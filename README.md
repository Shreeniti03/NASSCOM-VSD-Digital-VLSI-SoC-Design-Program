# NASSCOM-VSD-Digital-VLSI-SoC-Design-Program
# Day 1 : Inception of open-source EDA, OpenLANE and Sky130 PDK
-How to talk to computers.

-SoC design and openLANE

-get familiar to open source EDA tools 
●VLSI technology is crucial for integrating numerous tiny transistors onto chips, making electronics faster, smaller, and more cost-effective.

●The Arduino board relies on a microcontroller unit (MCU) to perform essential tasks like reading sensors and controlling lights.

●Chip manufacturing facilities, or foundries, are vital in determining the performance of chips used in devices like Arduino boards.

●Key components of a chip include the core, pads, and die, which are essential for logic implementation and signal transmission.

●The Sky130_fd_sc_hd variant from SkyWater foundry provides necessary technology files for chip design, with tools like OPENLANE requiring specific commands for design processes.
![411302519-3759afb9-445a-4140-832a-3ae61331d831](https://github.com/user-attachments/assets/08370fd4-78a3-4213-9b5e-46ec560fafd7)
![411303043-311a83b9-1db0-4206-b8f2-ff87eb4b17fa](https://github.com/user-attachments/assets/5a019dbf-5e0d-4372-b726-45c6ec3e4072)
![415284160-cd5d598f-6e4c-420a-9270-6fc1f7dd1bbc](https://github.com/user-attachments/assets/050df1ed-a8d2-438e-b891-9ec87e12a31c)

# DAY 2- Good floorplan vs bad floorplan and introduction to library cells
CHIP FLOOR PLANNING CONSIDERATION

UTILIZATION FACTOR AND ASPECT RATIO
In order to calculate the Utilization Factor and Aspect Ratio, we must know the height and width of core and die areas. formula is given by:

Utilization Factor = area occupied by the netlist / Total area occupied by the core

--> If the utilization factor is 1 then it denotes 100 % utilization. --> We never go for 100 % utilization, we go for 50 % or 60 % factor.

Aspect Ratio = height of the core / width of the core

--> When aspect ratio is 1 , then its a square chip.

STEPS TO RUN FLOORPLAN & REVIEW FLOORPLAN FILES
Once synthesis is sucessful,next step is floorplan. we use command

run_floorplan
This will create a folder inside runs folder of picorv32a directory. it will take a while to execute.once done we will get PDN GENERATION IS SUCESSFUL as shown in below image. To see the actual layout after the floorplan ,go the folders as shown below:

openlane/designs/picorv32a/runs/08-02_06-43/results/floorplan
now we need to open the magic file by the following command

magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &




Once the Floorplanning is done sucessfully , the next step in the process is Placement. To run the placement use the command

run_placement
Once Placement process is done , next step is to check whether the cells are placed correctly or not.by using magic tool.

use the below command to view the standerd cells placement. image is shown below

magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
