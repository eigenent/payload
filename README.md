
##### Introduction

This document contains a guide through the second major redesign of AcubeSAT's payload. We begin with an overview of the key functions facilitated by the payload, establishing the challenges that need to be overcome to achieve them. We take a look at the previous designs and their shortcomings as well as the design ideas that were implemented to address them. Finally we will briefly look at the final redesign that happened afterwards.

-----

##### AcubeSAT 

The AcubeSAT project is Aristotle University of Thessaloniki's cubesat project under the umbrella of the "Fly Your Satellite! 3" program by the educational office of the European Space Agency. 

The project aims to 

###### Experiment hosted

The experiment hosted in the mission can be simply described as taking photographs of an active yeast cell cultivation. There are two parts in it, cultivating the cells and then taking photographs of them. 

The cells are placed in a PDMS chip. 

% add picture

###### Design challenges

There are three major design challenges faced in this mission from a structural/mechanical design standpoint. These are, in order of being in earth and being in space, the following
- Making sure everything fits inside the payload vessel and the payload fits with the rest of the satellite
- Making sure it can withstand the loads (vibrations) of the launch conditions
- Making sure it is leak proof
There are further design challenges within each one of those, as well as challenges regarding the heating of the yeast cells to make sure their temperature is in a viable range, as well as a host of different electrical challenges that are outside the scope of this document.

The question of fit entails more than just fitting everything inside a vessel. In order for the photographs to be legible it is absolutely crucial that the focus of the camera is maintained throughout the launch and into orbit. More than that it is minimizing the required space while keeping in line with th


------

##### Previous designs

Before looking at anything and discussing the various designs it is crucial to establish that some of the older designs were made in earlier phases of the design process and thus some of their eventual shortcomings where not visible from the onset. In early design stages it was more a question of "could this potentially work?", rather than "what is the best way to do it?". As the project grew closer to reality, through phases B, C, and D, the focus was more on the interior of the payload architecture and the functionality rather than it's structural properties. Thus great progress was made on one front while other aspects were partially overlooked due, in part, to a lack of people availability. A different situation was faced later in the design process, when we started to create detailed mock ups of the assembly we found out that even though stuff worked on paper, in reality problems were faced. Lastly, some simplifications in the experiment design resulted in the elimination of some components or the reductions of dimensions in other components, allowing for some major improvements in the mechanical design.

###### Original

Let us first look at how the team approached the design at a conceptual level, at the first stages of the project, before being accepted into the program. At this conceptual stage, the fundamental design philosophy was established and subsequent redesigns were only modifications on this and did not attempt a major rethink of this philosophy.

Realizing the major engineering challenges described above the team decided that the best way was to create an enclosure, a container that hosted an interior assembly inside supporting the components that made the experiment possible. This container is sealed tight using a PTFE sealing ring that is being pressed using 16 M3 bolts. 

The proper distances, that allow for the focus to be maintained are kept with the aid of the unibody assembly


###### Boupan's work


------------
##### 2nd redesign (My work)

My work

----------
##### Newest version

The one actually implemented

----------
##### Further reading

For further reading into the nitty gritty of the design as well as other aspects of the mission head to [insert spacedot gitlab link]. There you can find public documents containing mechanical drawings, CADs, FEM models, as well as analysis and test results, reports and more. 
