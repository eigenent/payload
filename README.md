
##### Introduction

This document contains a guide through the second major redesign of AcubeSAT's payload. We begin with an overview of the key functions facilitated by the payload, establishing the challenges that need to be overcome to achieve them. We take a look at the previous designs and their shortcomings as well as the design ideas that were implemented to address them. Finally we will briefly look at the final redesign that happened afterwards.

----------

##### Contents
1. AcubeSAT
   1.1 Experiment hosted
   1.2 Design challenges  
2. Previous designs
   2.1 Original
   2.2 Boupan's redesign  
3. 2nd redesign (my work)
   3.1 Container
   3.2 Unibody assembly
   3.3 Chip holder
   3.4 Alternative design
4. Newest version
5. Further reading

-----

##### AcubeSAT 

The AcubeSAT is Aristotle University of Thessaloniki's cubesat project under the umbrella of the "Fly Your Satellite! 3" program by the educational office of the European Space Agency. The aim of the mission is to study the effects of the conditions in orbit, namely increased radiation load and microgravity on the cultivation and gene expression of yeast cells. 

The satellite is a 3U+ cubesat. The top 1/3 is occupied by the PCB stack containing critical PCBs such as the on board computer or the communications board, as well as the deployment antenna, whereas the rest of the satellite houses the payload. Originally the design was 3U but it was changed during the 2nd redesign in order to enable the usage of the check valve without disassembling the entire satellite (more on that later).

![satellite inner view](https://github.com/user-attachments/assets/bf3f3843-63ce-41a5-9cff-08247c7160d7)

In terms of attachment points, the cubesat frame procured from Endurosat comes with fixed mounting holes and ribs that support the interior components as well as the solar panels. Originally the Payload was designed to be mounted with the aid of two of these ribs that were then mounted on the exterior walls of the container. The distances between the PCBs is maintained using spacers.

###### Experiment hosted

The experiment hosted in the mission can be simply described as taking photographs of an active yeast cell cultivation. There are two parts in it, cultivating the cells and then taking photographs of them. 

The yeast cells are placed inside chambers of a PDMS microfluidics chip. This chip has a total of 4 arrays of chambers made of 3 arrays for the experiments and one for testing the operation of the chip. The initial dimensions were about 30mm (length) x 20mm (width) x 10mm (height). In the picture below a smaller cut PDMS chip can be seen, containing only one (of 3) experimental chamber arrays. The design of outside the scope of this document, the only thing that is relevant is the physical architecture as well as the fact that the chip is connected with tubes via needles inserted to it's chambers. 

![pdms chip bad quality (1)](https://github.com/user-attachments/assets/48545d4e-7c1e-47c0-8dfa-e93410364cf3)

The other part of the experiment is the imaging system. In short, a camera is used to take pictures of the cultivation. Attached to the camera is a zooming lens whereas, initially there was a LED excitation PCB to excite the cells so the camera captures their fluorescence as a measure of their growth. From a mechanical standpoint it is absolutely imperative that the distances between the key components, the camera-lens, the LED PCB and the chip remain unchanged during launch and operation, as even a slight change would alter the focus and would harm the legibility of the results. In the picture below the distance measuring 25.87 mm is what is most important.

![distances](https://github.com/user-attachments/assets/98b55b40-f1ac-4cbc-95ca-156641964bb9)


###### Design challenges

Putting all being written until now in order, there are three major design challenges faced in this mission from a structural/mechanical design standpoint. These are, placed in order of what the team was faced with first, the following:

- Making sure everything fits inside the payload vessel and the payload fits with the rest of the satellite
- Making sure it can withstand the loads (vibrations) of the launch conditions
- Making sure it is leak proof
  
There are further design challenges within each one of those, as well as challenges regarding the heating of the yeast cells to make sure their temperature is in a viable range, as well as a host of different electrical challenges that are outside the scope of this document.

Diving deeper in each one of them, the question of fit entails more than just fitting everything inside a vessel, it also includes maintaining camera focus as well as an unobstruced view for the camera. Additionally there are dimensional constraints to the exterior dimensions -and therefore to the interior dimensions- put in place by the fact that the available 3U cubesat space is shared with a stack of PCBs, as can been seen in the picture above. 

Furthermore, this assembly must survive the launch conditions with zero relative motion of the components. This is achieved by an effective and reliable elimination of the degrees of freedom of each part, both translational and rotational. The vibration loads applied to the cubesat during launch can be modelled, according to the ECSS standard as this (add proper reference and load). More information regarding the analysis performed can be found in 1 (add link)

When it comes to the leak rate, it is specified such that the pressure inside the container will not be reduced below 0.8 atm by the end of the 3rd experiment. The container is pressurized using the check valve in the beginning of the mission to 1.2 atm. 

------

##### Previous designs

Before looking at anything and discussing the various designs it is crucial to establish that some of the older designs were made in earlier phases of the design process and thus some of their eventual shortcomings where not visible from the onset. In early design stages it was more a question of "could this potentially work?", rather than "what is the best way to do it?". As the project grew closer to reality, through phases B, C, and D, the focus was more on the interior of the payload architecture and the functionality rather than it's structural properties. Thus great progress was made on one front while other aspects were partially overlooked due, in part, to a lack of people availability. A different situation was faced later in the design process, when we started to create detailed mock ups of the assembly we found out that even though stuff worked on paper, in reality problems were faced. Lastly, some simplifications in the experiment design resulted in the elimination of some components or the reductions of dimensions in other components, allowing for some major improvements in the mechanical design.

###### Original

Let us first look at how the team approached the design at a conceptual level, in the first stages of the project, before being accepted into the "FYS!3" program. At this conceptual stage, the fundamental design philosophy was established and subsequent redesigns were only modifications on this and did not attempt a major rethink of this philosophy.

Realizing the major engineering challenges described above the team decided that the best way to tackle them was to create an enclosure, a container that hosted an interior assembly supporting the components that made the experiment possible. This container is sealed tight using a PTFE sealing gasket being pressed using 16 M3 bolts. The proper distances, that allow for the focus to be maintained are kept with the aid of the unibody assembly, the chassis into which all other components are mounted on. 

![initial paylaod](https://github.com/user-attachments/assets/22f42a0e-ec72-4804-bd6c-a3f28780f87b)

As seen in the above image (everything is inverted, so the SU board is in the -Z direction), the PEEK unibody assembly is made of two almost identical parts which the team called "unibody halfs", one part on which these two were connected on, which housed the two pumps for the fluidics system, and two "unibody sides" connecting all three together. Inside and closer to -Z, there is the chip holder housing the PDMS chip, some microtubes and sensors necessary for controlling the system. Further along on the -Z direction there is the SU PCB assembly consisted of the manifold, its' valves and the SU PCB all mounted on the Unibody assembly using bolts. 

This assembly was then inserted into the container, the aluminium vessel holding everything together, through an opening on its' -Z face. The picture above with the proper distances between parts includes the depiction of the container, however also includes an even older version of the payload interior without the manifold for instance. The interior assembly was restricted in the XY plane through the use of the rails seen in the picture below. Initially there were two sets of rails both a and b, however the team soon realized that only the rails "a" were necessary and removing "b" would maximize the space for the SU PCB and the manifold. 

![initial XY plane fixation 2](https://github.com/user-attachments/assets/7e4cbb6d-2b90-4e3d-ad23-41487231c858)


In summary then this design established that:
- The PDMS chip is to be held inside a chip holder
- The chip holder is to be supported along with the rest of the parts inside the payload, the optical subsystem, the fludics and the SU PCB, by the unibody assembly
- Everything is housed inside the container, sealed with a PTFE gasket
- The container is mounted using ribs to the cubesat's frame

This design was assessed by ESA's team of experts during the critical design review (CDR), shortly after acceptance to the program. It had however some shortcomings. For once, the question of assembly procedures was further down the line at this point and most components were also in an early stage meaning that the design was more a theoretical one that a practical one. Mounting points, tubes and cables, fluid bags inside were also for the most part left out of the discussion. 

Summary of open points:
- Restriction of movement not properly defined along Z axis
- Tubes and cables inside not taken into account
- Interior parts mounting not properly defined

###### 1st redesign

Those are the holes that the first major redesign attempted to fill. Between the early designs and this one, other modifications were made in order to fix problems that crept up left and right, that left the design somewhat inconsistent with design elements sometimes clashing, with some of the details about tubes, mounting points and cables still not entirely defined. This redesign then aimed to unify the design, adress some more practical open points and add detail on the areas discussed above.

![payload boupan](https://github.com/user-attachments/assets/8e24358b-a086-4ed4-9c93-c33725e0a339)

Before this first redesign, some design changes were made, such as the introduction of a second opening to the container enclosure, enabling an assembly process but doubling the lids and gaskets required to leak proof it, as well as increasing the bolt count from 16 to 32 for the lids and having the weight go up as well. 

![pre boupan 3](https://github.com/user-attachments/assets/f9aba805-eebd-4b3d-a499-81df3bf2bb25)

During the redesign the focus turned to adding more detail in specific areas of the design, such as the chip holder assembly, containing sensors, heaters, inserts and other smaller components absent from previous designs. Also space was made for the bags, doing away with the complex camera mounting. 

![adding significant detail](https://github.com/user-attachments/assets/f9d0533b-a934-4f67-8efe-a7825d7c0f7b)

![boupan old vs new](https://github.com/user-attachments/assets/911298d8-ee74-498c-a5f6-0191f1eb99b5)

Although much detail was added in some aspects and solutions were provided for some of the previous open points, these solutions had some shortcomings themselves, particularly when it comes to the mechanical interfaces of the components. These can be summed up as:
- Restriction of degrees of freedom clashing with leak proofing
- Inadequate or improper fixation of interior components, specifically the camera assembly
- Very complicated difficult to manufacture parts

More specifically some of the major problems that require a change are the following:

1. First of all there is the problem of now properly restricting the Z axis movement of the internal parts. In the previous design this was completely lacking, but here the provided solution does not allow for the PTFE gasket to be pressed using the bolt connections (b, b2). What happens is that there are stand offs on the top and bottom of the unibody assembly directly in contact with the two lids of the container (a, a2). As is pressure and tension of the exterior bolts is transfered to the stand offs and the interior assembly rather than the lids. 

![exlplain improper fixation](https://github.com/user-attachments/assets/33844513-7805-409e-948b-bc8429cbe640)

2. A second major problem is the attachement of interior parts to the unibody assembly, the chassis of the design. An obvious, but not the only example, is the fixation of the optical system. The previous geometrical restriction was replaced with a bolt connection one. However it not being properly designed left the main part of the bolts vunerable to tangent stresses making the connection inadequate to restrict the Z axis movement as well as various rotational movements. 

![bad bolts](https://github.com/user-attachments/assets/5bc7c5d6-c30f-4aca-9490-a909f3b37aae)

3. Another problem is the general unessecary complexity in the design of parts. Some examples include the chip holder whose geometry is chaotic or the curvature found on various other components. Indicatively, c and e are way too thin to be manufactured, d and f serve absolutely no purpose. A

![bad ch](https://github.com/user-attachments/assets/142bbf1e-952c-4f69-b272-920e509e0af9)

![curvature](https://github.com/user-attachments/assets/1d33df49-700f-43f5-8787-0b0b0a6896af)

5. Here are that there are way too many parts in this assembly. There are the 3 main unibody components, the two "halfs" (2 is the visible one) and the lid (1), but additionally there is an extra part holding all three together (3) and 12 fasteners to fasten all the unibody assembly together (only 2 are visible). 

![too many parts 1](https://github.com/user-attachments/assets/3d5edbed-baa8-4e1b-b473-f9c6752fbd40)

6. Additionally carried through from the initial design and the intermidiete redesigns there are a number of exterior problems. For once, there is too much complexity with unesseccary ribs and fasteners acting as a middle man between the container and the frame. Then there is the second lid introduced to ease assembly, which when the bolt heads are added contributes significantly to the total height and weight of the payload. The edges are not smooth which is also adding weight. Lastly the check valve, which is the only way to pressurize the payload once closed, is still in the +Z face of the payload, facing the interior of the satellite, making the repressurization impossible without the complete dissasembly of the satellite. This is not only a problem because of the inconvenience but adds a major system risk since after the system level acceptance test, when the satellite is given a clearance from the launch provider, there may be a significant waiting period, during which the interior pressure could fall below the 1.2 atm design level, making it nessecary for the repressurization to occur. However taking the satellite apart could possibly nullify the acceptance test.
   
![general exterior problems](https://github.com/user-attachments/assets/3af9dcba-e9b2-44bb-81f2-fb8cfdb5f782)

------------
##### 2nd redesign (My work)

Although this redesign was initiated by some specific circumstances, the problems identified above really necessitated a major eventual redesign. That being said, two specific necessities triggered it. On the one hand a different, bigger battery pack was opted for due to the previous one becoming unavailable which necessitated the reduction in the height of the container in order for the entire PCB stack to fit. On the other hand the scientific team requested another camera, again bigger overall but crucially taller and with it's cable exiting on it's +z face and needing 20mm of space before it can bend. Thankfully the removal of the control level in the fluidics/microfluidics system reduced the number of tubes as well as the height of the PDMS chip by 7mm. In doing this redesign the primary target was accomodate these changes while at the same time adress some of the shortcomings of the previous designs discussed above. 

###### Chip holder

First of all a redesign of all internal components was underway to ensure simplicity and manufacturability. For instance, it can be seen in the chip holder bottom half illustrated bellow that the previous shortcomings are solved. The design is much more substancial, wall thickness of 4mm in some areas. There are also some details, such as the smooth inserts that allow for both stress relief and the accomodation of the orthogonal angle of the metal sheet on which the inserts were based, all the while without compromising on the manufacturability. 

![smooth and beefy](https://github.com/user-attachments/assets/b1add1b0-68f5-4f41-b481-16bb693a1e5c)

###### Interior

Then the number of interior parts was significantly reduced along with a major simplification in their interface. Gone are the bolt connections everywhere, replaced with a simple geoemtrical connection (the shape of the parts is keeping them together). The camera is mounted with a proper bolt connections where the two bodies are in direct contact, with the bolt taking only axial stresses while sheer stresses are absorbed by the friction of the bodies. The main body of the bolt is not subject to bending forces. What is more, even if it is not necessary and it was eventually dropped from the latest design, there are further geometrical supports for the optical system. These do not introduce a problem similar to no. 1 from the previous design since the bolts are not fastened in the Z direction but rather in the Y.

![simplified unibody assembly](https://github.com/user-attachments/assets/6b0c2fbf-bab7-433b-90ba-78d1e7179e88)

![simplified connections 2](https://github.com/user-attachments/assets/0a897af9-2202-4efb-960d-4f11ebf0ff29)

This iteration was the first properly defining a solution for the restriction of the Z axis movement of the interior assembly. This connection, in keeping with the theme of this design philosophy is based on form connections, where the shape of the parts introduces the restriction. Here the internal payload assembly, consisting of the unibody assembly, the manifold and the SU PCB are holded together using bolts and spacers. Then it is slided into place from above into the container, stopping at the end of the guiding rail shaped into the container's walls (b). After that a safety piece is added above to restrict the movement in the Z axis. This part is then safely fastened to the unibody lid (a). As can be seen, there is no component of the interior assembly touching the container lid (d circle) and thus all the pressure created by the tension of the botls holding the lid is transfered to the PTFE gasket ensuring leak proofing. 


![Z fixation explained](https://github.com/user-attachments/assets/7f0ca1b1-456c-4887-bae9-68a50086f007)

Additionally, in the bottom of the container main body floor 4 "L"s were formed, put in place to restrict the rocking motion of the interior assembly. More specifically, they kept the heads of the bolts used to keep the interior parts together. Having 4 of these, one in every corner ensured that all rocking degrees of freedom are restricted. 

![idea no rocking](https://github.com/user-attachments/assets/c3f5676e-6632-4c1e-aa2a-b7095502da59)

Further, the picture is complete by adding the actual reagent bags procured and tested by this point in the project, as well as the removal of the control layer in the PDMS chip microfluidics system which resulted in the removal of one pump. The other pump was rotated around to make way for the cable exiting on the top of the camera, rather than the side as with the previous design. The interior shapes have no curvature (apart from the fillets to ease stresses).

![interior nent](https://github.com/user-attachments/assets/9504629c-9a69-4839-b745-f57157993367)


###### Exterior

Due to the introduction of the new battery pack, the aim was to reduce the overall space, height-wise that the payload covered inside the 3U cubesat. The tallest component on the +Z container lid was the check valve. Initially a plan was drafted to have it lie on it's side rather than having it be vertical. The thinking was that this would also enable the refilling with only a solar panel taken out and not the entire satellite taken apart as before. However, it turned out that due to the size of the valve operating tool this was impossible given the extremely limited space as the tool would not fit between the bolts securing the container lid. What is more, an additional constraint imposed by the introduction of an bigger camera, meant that whatever space was saved inside due to inner simplifications was taken by the new camera and the giant (relatively speaking) cable coming out it's +Z face. The next solution attempted was to move to a single opening in the design, doing away with the two openings of the previous configuration, making the assembly process more challenging. Despite the significant height reduction (5mm), the space was still not adequate. By this time it was inevitable to go against the original 3U cubesat design and into a 3U+. After a detailed trade off it was decided to move the check valve to the -Z face of the payload, with it protruding on the -Z face of the satellite. This bought us the necessary space for the new battery pack and enabled the repressurization of the payload without removing anything. The only required sacrifice was the removal of the solar panel on the -Z face, which however, with the alteration of the pointing strategy of the cubesat only resulted in insignificant loss in energy production capacity. 

![trade off for tuna can](https://github.com/user-attachments/assets/f5035c53-577b-45d1-a9bb-f4c474a27a1c)


Another aspect of the design we were keen to fix was the many parts present on the outside. The elimination of one of the openings already resulted in a major reduction, however more parts could be eliminated if the ribs in between the payload and the frame were removed. Removing them meant that their openings should be created on the outside of the container itself. Thus the extrusions of the container were enlarged to make way for these. Lastly large radious fillets were introduced to the corners of the container body in part to smooth the edges and in part to further reduce it's mass. 

![exterior changes](https://github.com/user-attachments/assets/94c4b385-72e5-4f19-8f6a-477b30be9e97)


###### Sum up

This design iteration solves all of the previous problems. 
- The interior components are restricted in the Z axis (as well as the XY plain as before)
- The interior parts are properly fastened to the chassis (unibody assembly)
- The parts are greatly simplified, a lot of bolts are taken out, weight is reduced
- The valve can be operated without the disassembly of the entire satellite
- Proper leak proofing since all the pressure goes to the PTFE gasket and not any interior parts

However, even though we did receive an initial confirmation that the design was manufacturable from Xometry (a intermidiate company between manufacturers and clients), and the Finite Element Analysis performed returned promising results, the team was later informed that the container was not manufacturable due to the height of the interior container walls. 

**This design can be found as a .STEP file in this repository.**


----------
##### Newest version

To counter this problem, the team opted to move the opening of the container to the middle of it rather than the top side, eliminating the container lid and splitting the main body into two halves. As can be seen this necessitated the rethinking of the interior fixation for the Z axis movement. Now 4 rods attached to the lower half of the container run all the way to the top of the unibody lid with spacers separating the parts inbetween. Then simple nuts are inserted on top of the rods to fix the entire assembly in place. Both container halves don't have stoppers on their rails anymore to avoid problem no.1 from the 1st redesign iteration. The rest remain pretty much unchanged. This iteration of the payload was constructed and has been succesfully qualified to survive the vibrations during launch. The testing took place in ESA's CSF facility.

![proper mounting new payload](https://github.com/user-attachments/assets/3064699d-42a7-4595-a501-c0f1a2051c0b)

![container](https://github.com/user-attachments/assets/bd83cf10-482b-4207-8e0a-66f29188335d)


----------
##### Further reading

For further reading into the nitty gritty of the design as well as other aspects of the mission head to [AcubeSAT gitlab](https://gitlab.com/acubesat). There you can find public documents containing mechanical drawings, CADs, FEM models, as well as analysis and test results, reports and more. 
