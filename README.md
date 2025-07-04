
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

The AcubeSAT project is Aristotle University of Thessaloniki's cubesat project under the umbrella of the "Fly Your Satellite! 3" program by the educational office of the European Space Agency. The aim of the mission is to study the effects of the conditions in orbit, namely increased radiation load and microgravity on the cultivation and gene expression of yeast cells. 

The satellite is a 3U+ cubesat. The top 1/3 is occupied by the PCB stack containing critical PCBs such as the on board computer or the communications board, as well as the deployment antena, whereas the rest of the satellite houses the payload. Originally the design was 3U but it was changed during the 2nd redesign in order to enable the usage of the check valve without disassembling the entire satellite (more on that later).


###### Experiment hosted

The experiment hosted in the mission can be simply described as taking photographs of an active yeast cell cultivation. There are two parts in it, cultivating the cells and then taking photographs of them. 

The cells are placed inside the channels of a PDMS chip about 30mm x 20mm x 10mm. 


###### Design challenges

There are three major design challenges faced in this mission from a structural/mechanical design standpoint. These are, in order of being in earth and being in space, the following
- Making sure everything fits inside the payload vessel and the payload fits with the rest of the satellite
- Making sure it can withstand the loads (vibrations) of the launch conditions
- Making sure it is leak proof
There are further design challenges within each one of those, as well as challenges regarding the heating of the yeast cells to make sure their temperature is in a viable range, as well as a host of different electrical challenges that are outside the scope of this document.

Diving deeper in each one of them, the question of fit entails more than just fitting everything inside a vessel. In order for the photographs to be legible it is absolutely crucial that the focus of the camera is maintained throughout the launch and into orbit. Additionally there are dimensional constraints to the exterior dimensions -and therefore to the interior dimensions- put in place by the fact that the available 3U cubesat space is shared with a stack of PCBs, as can been seen in the picture above. 

Furthermore, all this assembly must survive the launch conditions with zero relative motion of the components. This is achieved by an effective and reliable elimination of the degrees of freedom of each part, both translational and rotational. The vibration loads applied to the cubesat during launch can be modelled, according to the ECSS standard as this (add proper reference and load). More information regarding the analysis performed can be found in 1 (add link)

When it comes to the leak rate, it is specified such that the pressure inside the container will not be reduced below 0.8 atm by the end of the 3rd experiment. The container is pressurized using the check valve in the beginning of the mission to 1.2 atm. 

------

##### Previous designs

Before looking at anything and discussing the various designs it is crucial to establish that some of the older designs were made in earlier phases of the design process and thus some of their eventual shortcomings where not visible from the onset. In early design stages it was more a question of "could this potentially work?", rather than "what is the best way to do it?". As the project grew closer to reality, through phases B, C, and D, the focus was more on the interior of the payload architecture and the functionality rather than it's structural properties. Thus great progress was made on one front while other aspects were partially overlooked due, in part, to a lack of people availability. A different situation was faced later in the design process, when we started to create detailed mock ups of the assembly we found out that even though stuff worked on paper, in reality problems were faced. Lastly, some simplifications in the experiment design resulted in the elimination of some components or the reductions of dimensions in other components, allowing for some major improvements in the mechanical design.

###### Original

Let us first look at how the team approached the design at a conceptual level, at the first stages of the project, before being accepted into the program. At this conceptual stage, the fundamental design philosophy was established and subsequent redesigns were only modifications on this and did not attempt a major rethink of this philosophy.

Realizing the major engineering challenges described above the team decided that the best way was to create an enclosure, a container that hosted an interior assembly inside supporting the components that made the experiment possible. This container is sealed tight using a PTFE sealing ring that is being pressed using 16 M3 bolts. 

The proper distances, that allow for the focus to be maintained are kept with the aid of the unibody assembly


###### Boupan's work

Recaping, the version circa 2022 was this one

Problems that needed adressing

------------
##### 2nd redesign (My work)

My work

###### Container

###### Unibody assembly

###### Chip holder

###### Comparisons

----------
##### Newest version

The one actually implemented

----------
##### Further reading

For further reading into the nitty gritty of the design as well as other aspects of the mission head to [insert spacedot gitlab link]. There you can find public documents containing mechanical drawings, CADs, FEM models, as well as analysis and test results, reports and more. 
