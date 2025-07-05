
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

This assembly was then inserted into the container, the aluminium vessel holding everything together, through an opening on its' -Z face. The picture above with the proper distances between parts includes the depiction of the container, however also includes an even older version of the payload interior without the manifold for instance. 


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

During the redesign the focus turned to adding more detail in specific areas of the design, such as the chip holder assembly, containing sensors, heaters, inserts and other smaller components absent from previous designs.

![adding significant detail](https://github.com/user-attachments/assets/f9d0533b-a934-4f67-8efe-a7825d7c0f7b)

![boupan old vs new](https://github.com/user-attachments/assets/911298d8-ee74-498c-a5f6-0191f1eb99b5)

Although much detail was added in some aspects and solutions were provided for some of the previous open points, these solutions had some shortcomings themselves, particularly when it comes to the mechanical interfaces of the components. These can be summed up as:
- Restriction of degrees of freedom clashing with leak proofing
- Inadequate or improper fixation of interior components, specifically the camera assembly
- Very complicated difficult to manufacture parts

More specifically:




------------
##### 2nd redesign (My work)

Although this redesign was initiated by some specific circumstances, the problems identified above really necessitated a major eventual redesign. That being said, two specific necessities triggered it. On the one hand a different, bigger battery pack was opted for due to the previous one becoming unavailable. This necessitated the reduction in the height of the container in order for the entire PCB stack to fit. On the other hand the scientific team requested another camera, again bigger overall but crucially taller and with it's cable exiting on it's +z face and needing 20mm of space before it can bend. Thankfully the removal of the control level in the fluidics/microfluidics system reduced the number of tubes as well as the height of the PDMS chip by 7mm. 

In doing this redesign the primary target was accomodate these changes while at the same time adress some of the shortcomings of the previous designs discussed above, as well as enabling the repressurazation of the payload without the need to completely disassemble the cubesat.

###### Chip holder

###### Unibody assembly

###### Container



###### Comparisons

For comparison here is the 1st redesign vs 2nd redesign for the paylaod, both exterior and interior. The component reduction is obvious.

![old vs new exterior](https://github.com/user-attachments/assets/8120807d-5b86-46c7-b619-13f6497e0069)

![old vs new interior](https://github.com/user-attachments/assets/195a003c-d701-43dc-9906-31d8d5306111)

----------
##### Newest version

The one actually implemented

----------
##### Further reading

For further reading into the nitty gritty of the design as well as other aspects of the mission head to [insert spacedot gitlab link]. There you can find public documents containing mechanical drawings, CADs, FEM models, as well as analysis and test results, reports and more. 
