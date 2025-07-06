##### Introduction

This document contains a guide through the second major redesign of AcubeSAT's payload. We begin with an overview of the key functions facilitated by the payload, establishing the challenges that need to be overcome to achieve them. We take a look at the previous designs and their shortcomings as well as the design ideas that were implemented to address them. Finally, we will briefly look at the final redesign that happened afterwards.

---

### ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ 

---


##### Contents

1. **AcubeSAT**  
   1.1 [Experiment hosted](#experiment-hosted)  
   1.2 [Design challenges](#design-challenges)  
2. **Previous designs**  
   2.1 [Original](#original)  
   2.2 [1st major redesign](#1st-major-redesign)  
3. **2nd redesign (my work)**  
   3.1 [Interior](#interior)  
   3.2 [Exterior](#exterior)  
   3.3 [Sum up](#sum-up)  
4. **Newest version**  
5. **Further reading**

---

### ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ 

---

##### AcubeSAT

AcubeSAT is the CubeSat project of the Aristotle University of Thessaloniki, developed under the European Space Agency's *Fly Your Satellite! 3* program. The mission's goal is to investigate the effects of space conditions—specifically increased radiation and microgravity—on the cultivation and gene expression of yeast cells.

The satellite is a 3U+ CubeSat. The top third houses a PCB stack containing essential boards such as the onboard computer and communication systems, along with the deployable antenna. The remaining two-thirds contain the payload. Originally designed as a 3U CubeSat, the format was extended to 3U+ during the second redesign to enable access to the check valve without requiring full disassembly as well as the accomodation of a larger battery pack (discussed in [3.2 Exterior](#32-exterior)).

![Satellite inner view](https://github.com/user-attachments/assets/bf3f3843-63ce-41a5-9cff-08247c7160d7)

The CubeSat frame, sourced from EnduroSat, includes fixed mounting holes and interior ribs for structural support and solar panel integration. Initially, the payload was mounted using two of these ribs, which were themselves attached to the container's outer walls. Vertical spacing between PCBs is maintained using spacers.
inally the Payload was designed to be mounted with the aid of two of these ribs that were then mounted on the exterior walls of the container. The distances between the PCBs is maintained using spacers.

###### 1.1 Experiment Hosted

The experiment hosted by AcubeSAT can be described, in simple terms, as imaging active yeast cell cultivation in microgravity. It consists of two main parts: cultivating the cells, and capturing images of them.

Yeast cells are placed in chambers within a PDMS (polydimethylsiloxane) microfluidics chip. This chip features four chamber arrays—three for scientific experimentation and one for functional validation. Its initial dimensions were approximately 30 mm (L) × 20 mm (W) × 10 mm (H). The image below shows a smaller, cut section of the PDMS chip, containing one of the three experimental chamber arrays. While the biological design is outside the scope of this document, it is important to note the chip’s physical architecture and its fluidic connectivity via tubes attached to needles inserted into each chamber.

![PDMS chip](https://github.com/user-attachments/assets/48545d4e-7c1e-47c0-8dfa-e93410364cf3)

The second part of the experiment is the imaging system. A camera, equipped with a zoom lens, captures images of the yeast cultivation process. Initially, an LED excitation PCB was also included to stimulate fluorescence in the cells, which acts as an indirect growth indicator.

From a mechanical standpoint, it is critical that the spatial relationship between key components—the camera, lens, LED PCB, and microfluidic chip—remains fixed throughout launch and operation. Even slight shifts can impact focus, compromising data integrity. In the figure below, the 25.87 mm dimension between components is especially critical.

![Component spacing](https://github.com/user-attachments/assets/98b55b40-f1ac-4cbc-95ca-156641964bb9)

---

###### 1.2 Design Challenges

Three major structural and mechanical challenges were encountered in the payload design, listed in the order they were addressed:

- **Volume integration**: Ensuring all payload components fit within the payload vessel and integrate with the rest of the satellite.
- **Mechanical survivability**: Guaranteeing the structure can withstand launch loads, especially vibrations.
- **Sealing and leak-proofing**: Maintaining internal pressure within mission-defined limits.

Additional challenges include maintaining thermal conditions suitable for cell viability and addressing numerous electrical integration constraints, which are beyond the scope of this document.

**1. Volume Integration**  
This goes beyond simply fitting components inside the housing. It involves ensuring:
- The camera maintains proper focus on the microfluidic chip,
- There is an unobstructed optical path for imaging, and
- The payload fits within the residual volume of the 3U CubeSat after accounting for the PCB stack (as shown previously in [AcubeSAT](#acubesat)).

**2. Mechanical Survivability**  
All components must endure launch loads without relative motion. This requires eliminating all translational and rotational degrees of freedom through robust mechanical constraints. Vibration loads are defined per ECSS standards (exact reference to be added). More details about the vibration analysis performed can be found in [Further Reading](#5-further-reading).

**3. Leak Rate Management**  
The internal pressure must not fall below 0.8 atm by the end of the third experiment. The container is initially pressurized to 1.2 atm using a check valve. Achieving and maintaining this seal integrity is a critical design constraint.

---

### ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ 

---

##### 2. Previous Designs

Before discussing the design iterations in detail, it's important to note that earlier versions were developed during preliminary phases of the mission. At those stages, the objective was to assess feasibility—*could this work in principle?*—rather than optimize implementation. As the project progressed through ESA's design phases B, C, and D, attention increasingly shifted to the internal payload architecture and experimental functionality, often at the expense of structural considerations. 

This imbalance was partly due to limited personnel availability and shifted later in the process as the team began building physical mockups. At that point, it became clear that certain elements which worked theoretically posed practical integration issues. Additionally, simplifications in the experimental design—such as removal of redundant components and size reductions—allowed for significant improvements in the mechanical layout during later stages.

---

###### 2.1 Original

The initial conceptual design, created prior to acceptance into ESA’s *Fly Your Satellite! 3* program, established the payload's core mechanical philosophy. All subsequent redesigns were modifications of this baseline rather than complete overhauls.

To address the key mechanical challenges, the team designed a sealed container that housed a rigid internal assembly responsible for supporting all experimental components. This container was closed with a PTFE gasket, compressed by 16 M3 bolts to maintain pressure integrity. Component spacing—critical for imaging focus—was maintained by a PEEK unibody chassis onto which all other parts were mounted.

![Initial payload](https://github.com/user-attachments/assets/22f42a0e-ec72-4804-bd6c-a3f28780f87b)

As shown above (noting that the orientation is inverted, with the SU board in the -Z direction), the PEEK unibody assembly consisted of:
- Two nearly identical “unibody halves”,
- A central connecting part housing two fluidic pumps,
- Two “unibody sides” that connected and reinforced the structure.

Inside the unibody assembly (closer to -Z), the chip holder secured the PDMS chip along with microtubes and sensors. Further along the -Z axis was the SU (Sample Unit) PCB assembly, which included the fluidic manifold, valves, and control PCB—all bolted directly onto the unibody chassis.

This complete assembly was inserted into the aluminum payload container via the -Z face. The earlier image showing the 25.87 mm spacing between optical components also includes this container, although it reflects an older interior version lacking certain components like the fluidic manifold.

To prevent lateral (XY-plane) movement, the internal assembly was constrained using guide rails. Initially, two sets of rails ("a" and "b") were implemented:

![XY plane fixation](https://github.com/user-attachments/assets/7e4cbb6d-2b90-4e3d-ad23-41487231c858)

However, the team soon realized that only rails "a" were necessary; removing rails "b" freed valuable space for the SU PCB and fluidic manifold.

**Design Summary:**
- The PDMS chip was housed in a dedicated chip holder.
- All subsystems (optical, fluidics, control PCB) were supported by a unified unibody structure.
- The assembly was enclosed in a sealed aluminum container with a PTFE gasket.
- The container was mounted to the CubeSat frame using external ribs.

This design was reviewed during ESA's Critical Design Review (CDR), shortly after project acceptance. While conceptually sound, the design had several unresolved issues due to its early-stage nature and focus on theoretical rather than practical integration.

**Identified Weaknesses:**
- Incomplete definition of Z-axis constraints and locking mechanisms.
- Absence of integrated routing for internal tubes and cables.
- Vague or undefined mounting strategies for internal subcomponents.

###### 2.2 1st Major Redesign

The first major redesign aimed to address the shortcomings of the original design. Between the conceptual design and this iteration, several ad-hoc modifications had been introduced to resolve emerging issues, but these led to inconsistencies. Some components clashed geometrically, and elements like tubing, mounting points, and cable routing remained ill-defined.

This redesign focused on unifying the architecture, resolving practical integration issues, and adding missing detail—particularly regarding fluidic and optical subassemblies.

![First redesign overview](https://github.com/user-attachments/assets/8e24358b-a086-4ed4-9c93-c33725e0a339)

### Key Changes

Before the formal redesign, an intermediate change introduced a second access opening on the container. This facilitated the assembly process but doubled the number of lids and gaskets, increased bolt count from 16 to 32, and significantly raised the total mass.

![Pre-redesign configuration](https://github.com/user-attachments/assets/f9aba805-eebd-4b3d-a499-81df3bf2bb25)

During the redesign, several targeted improvements were made:

- A more detailed chip holder assembly was introduced, including sensors, heaters, and other subcomponents.
- The optical system was simplified by eliminating the previous complex mounting.
- Space was allocated for fluid bags and internal routing.

![Detail improvements](https://github.com/user-attachments/assets/f9d0533b-a934-4f67-8efe-a7825d7c0f7b)
![Comparison of versions](https://github.com/user-attachments/assets/911298d8-ee74-498c-a5f6-0191f1eb99b5)

While this redesign improved granularity and resolved some critical issues, it introduced new problems—particularly in the mechanical interfaces of subcomponents.

---

### Identified Shortcomings

1. **Improper Load Path for Gasket Sealing**

   The attempt to constrain the Z-axis motion led to stand-offs on the unibody contacting both lids (a, a2). This unintentionally redirected bolt tension through the interior structure rather than compressing the PTFE gasket between the container lids.

   ![Improper load transfer](https://github.com/user-attachments/assets/33844513-7805-409e-948b-bc8429cbe640)

2. **Weak Attachment of Internal Subsystems**

   The new bolt-based fixation method for components like the optical system replaced earlier geometric constraints. However, it exposed bolts to tangential forces and failed to restrict Z-axis and rotational movements effectively.

   ![Inadequate fixation](https://github.com/user-attachments/assets/5bc7c5d6-c30f-4aca-9490-a909f3b37aae)

3. **Unnecessary Geometric Complexity**

   Several components exhibited overly complex or impractical shapes. The chip holder, for example, had chaotic geometry, while elements like parts *c* and *e* were too thin to manufacture reliably, and *d* and *f* served no functional purpose.

   ![Poor chip holder geometry](https://github.com/user-attachments/assets/142bbf1e-952c-4f69-b272-920e509e0af9)
   ![Excess curvature](https://github.com/user-attachments/assets/1d33df49-700f-43f5-8787-0b0b0a6896af)

4. **Excessive Part Count**

   The unibody structure comprised at least six components: the two main halves (only one is visible as part 2), the top lid (1), a central connector (3), and at least 12 fasteners. This increased both complexity and assembly time.

   ![Excessive part count](https://github.com/user-attachments/assets/3d5edbed-baa8-4e1b-b473-f9c6752fbd40)

5. **External Structural Issues**

   Several flaws persisted from earlier versions:
   - Overly complex exterior ribs and fasteners created indirect mounting paths to the CubeSat frame.
   - The second lid, while aiding assembly, significantly increased height and mass.
   - Sharp, unsmoothed edges added unnecessary mass.
   - Critically, the check valve remained on the +Z face, facing the interior of the satellite. This made repressurization impossible without disassembling the satellite—posing a serious risk. If interior pressure drops after the System Level Acceptance Test (SLAT), restoring it would require breaking system-level integrity, potentially invalidating test results.

   ![Exterior design problems](https://github.com/user-attachments/assets/3af9dcba-e9b2-44bb-81f2-fb8cfdb5f782)

Expanding on the last point, the check valve—the only interface for pressurizing the payload—is still located on the +Z face of the payload, which faces the interior of the satellite. This positioning makes repressurization impossible without fully disassembling the satellite structure. While inconvenient in itself, this design choice introduces a critical system-level risk.

After the System Level Acceptance Test (SLAT), the satellite receives formal clearance from the launch provider. Following this milestone, there is often a prolonged waiting period before launch. During this time, the pressure inside the payload may gradually drop below the nominal 1.2 atm level, potentially falling below the minimum acceptable threshold of 0.8 atm before the final experiment can be completed in orbit.

If repressurization becomes necessary at that stage, disassembly of the satellite would be required to access the check valve. However, this would invalidate the results of the SLAT, compromising the mission’s launch readiness and potentially requiring a full requalification process. This scenario presents a significant operational and schedule risk that must be mitigated through a redesign of the pressurization interface or access path.

---

### ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ 

---

##### 3. 2nd Redesign (My Work)

Although this redesign was prompted by specific external changes, the underlying issues identified in the previous designs made a complete overhaul both inevitable and necessary. Two key factors triggered the redesign:

- A new, larger battery pack was selected after the original became unavailable. To accommodate the full PCB stack, the payload container height had to be reduced.
- The scientific team requested the integration of a second, physically larger camera. In addition to its increased footprint, the new camera required 20 mm of clearance above it to allow for cable bending, as the cable exited from its +Z face.

Fortunately, some internal simplifications—namely the removal of the control layer from the microfluidics system—reduced the number of tubes and lowered the height of the PDMS chip by 7 mm. The objective of this redesign was to integrate these changes while resolving the mechanical and structural issues from previous iterations.

---

###### 3.1 Interior

**Chip Holder**

All internal components were redesigned with a focus on simplicity, manufacturability, and structural integrity. The chip holder, in particular, was significantly improved. The example below shows the lower half of the chip holder, now featuring thicker walls (up to 4 mm), clean geometry, and stress-relieving fillets. Smooth inserts accommodate the orthogonal metal sheet base without compromising on manufacturing feasibility.

![Redesigned chip holder](https://github.com/user-attachments/assets/b1add1b0-68f5-4f41-b481-16bb693a1e5c)

**Unibody and Mounting**

The internal assembly was dramatically simplified. The total number of parts was reduced, and their interfaces were redesigned. Instead of relying on numerous bolts, the system now uses form-fit (geometric) connections. Most internal components are held together through shape-based mating, reducing complexity and assembly time.

The camera is an exception: it is secured using a dedicated bolt connection designed to bear only axial loads. Shear forces are absorbed through friction between the contacting surfaces, ensuring the bolt is not subjected to bending—unlike in the previous design. Additional geometric supports for the optical system were explored (but ultimately dropped), and they did not interfere with sealing integrity since the bolts are oriented in the Y-direction, not Z.

![Simplified unibody assembly](https://github.com/user-attachments/assets/6b0c2fbf-bab7-433b-90ba-78d1e7179e88)
![Improved connections](https://github.com/user-attachments/assets/0a897af9-2202-4efb-960d-4f11ebf0ff29)

**Z-Axis Fixation**

This iteration introduced the first properly defined Z-axis restriction. Staying true to the form-fit design philosophy, Z-axis movement is restricted without compromising leak-proofing.

- The unibody assembly, manifold, and SU PCB are bolted together using spacers.
- This assembly slides vertically into the container, guided by rail features integrated into the container walls (label b).
- Once in place, a safety bracket is installed above it, securing the Z-axis and fastened to the unibody lid (label a).
- Importantly, no interior component contacts the top container lid (label d), ensuring that the compressive force from the lid bolts is transferred entirely to the PTFE gasket.

![Z-axis fixation concept](https://github.com/user-attachments/assets/7f0ca1b1-456c-4887-bae9-68a50086f007)

Additionally, four "L"-shaped features were added at the corners of the container floor. These lock in the heads of the bolts joining the internal assembly, preventing rocking or rotational movement.

![Anti-rocking supports](https://github.com/user-attachments/assets/c3f5676e-6632-4c1e-aa2a-b7095502da59)

**Other Internal Changes**

The interior layout was finalized with:
- Real reagent bags that had been tested and validated by this stage,
- The removal of one pump due to the simplified fluidics system,
- The rotation of the remaining pump to allow space for the new camera's top-exiting cable.

Interior geometries were fully rationalized—flat and functional, with fillets only where required for stress relief.

![Finalized interior](https://github.com/user-attachments/assets/9504629c-9a69-4839-b745-f57157993367)

---

###### 3.2 Exterior

The redesigned battery pack imposed strict constraints on the vertical space occupied by the payload. The tallest exterior feature was the check valve on the +Z lid.

**Initial Attempts**  
An early idea was to rotate the check valve sideways so that it could be accessed without removing the entire satellite structure—potentially requiring removal of only a solar panel. However, this proved unfeasible: the tool used to operate the valve was too large to fit between the bolts surrounding the lid in the tight available space.

Complicating things further, the larger camera and its rigid top-exiting cable consumed all of the internal volume gains made by removing the control layer. Despite reducing the container height by 5 mm and reverting to a single-opening container design (abandoning the dual-lid configuration), the space was still insufficient.

At this point, it became clear that a departure from the strict 3U CubeSat format was necessary. The team opted to move to a 3U+ configuration.

**Final Solution**  
After a detailed trade-off analysis, the check valve was relocated to the -Z face, where it now protrudes beyond the satellite structure. This change:
- Freed up space to accommodate the larger battery pack,
- Enabled repressurization of the payload post-integration without disassembling the satellite,
- Only required the removal of the -Z solar panel for valve access.

The resulting power loss from this panel was deemed negligible after modifying the satellite's pointing strategy.

![Check valve redesign and tradeoff](https://github.com/user-attachments/assets/f5035c53-577b-45d1-a9bb-f4c474a27a1c)

**Further Exterior Simplifications**

- Eliminating one container opening significantly reduced part count.
- The external ribs and intermediary fasteners used for frame attachment were removed.
- Mounting features were integrated directly into the container’s body via enlarged extrusions.
- Large-radius fillets were added to the container corners to reduce sharp edges and overall mass.

![Finalized exterior](https://github.com/user-attachments/assets/94c4b385-72e5-4f19-8f6a-477b30be9e97)

---

###### 3.3 Sum Up

This redesign successfully resolved all major structural issues present in previous iterations:

- **Z-axis and XY-plane motion are fully restricted** through form-fit interfaces.
- **Internal components are properly fastened** to the chassis using secure, well-aligned bolt connections.
- **Component complexity was significantly reduced**, lowering mass and assembly overhead.
- **The check valve is now accessible** post-assembly, enabling repressurization without compromising system integrity.
- **Proper leak sealing is ensured**, with all lid bolt tension transferred to the PTFE gasket rather than internal components.

Despite a preliminary confirmation of manufacturability from Xometry (a manufacturing broker), and promising results from finite element analysis (FEA), it was later discovered that the container body could not be manufactured due to the extreme height of the internal vertical walls.

**This design is available as a `.STEP` file in this repository.**



---

### ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ 

---

##### 4. Newest Version

To resolve the manufacturability issue identified in the previous redesign, the team reworked the container architecture by relocating the main opening from the top to the center of the payload body. This change eliminated the traditional container lid entirely and instead split the container into two interlocking halves—upper and lower.

As a result, the internal Z-axis fixation mechanism had to be reimagined. In this iteration, four structural rods are attached to the lower half of the container and run vertically through the entire payload assembly, terminating at the top of the unibody lid. Spacers are inserted between critical subcomponents along each rod to preserve precise distances. Once assembled, the entire structure is fixed in place by threading nuts onto the top ends of the rods.

![Payload rod fixation system](https://github.com/user-attachments/assets/3064699d-42a7-4595-a501-c0f1a2051c0b)

Unlike previous designs, this version does **not** use stopper features on the container rails. This avoids the Z-axis sealing interference issue described as problem no. 1 in the first major redesign, ensuring that lid tension is correctly applied to the sealing gasket and not transferred to the internal assembly.

Other structural and internal aspects remain largely unchanged from the second redesign.

This version of the payload was physically constructed and successfully passed vibration qualification testing at ESA’s CubeSat Support Facility (CSF), confirming its readiness for launch.

![Final payload container design](https://github.com/user-attachments/assets/bd83cf10-482b-4207-8e0a-66f29188335d)

---

### ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ ◆ 

---

##### Further reading

For further reading into the nitty gritty of the design as well as other aspects of the mission head to [AcubeSAT gitlab](https://gitlab.com/acubesat). There you can find public documents containing mechanical drawings, CADs, FEM models, as well as analysis and test results, reports and more. 
