# NASSCOM-VSD-Digital-VLSI-SoC-Design-Program
# Day 1 : Inception of open-source EDA, OpenLANE and Sky130 PDK
°How to talk to computers.

°SoC design and openLANE

°get familiar to open source EDA tools 

●VLSI technology is crucial for integrating numerous tiny transistors onto chips, making electronics faster, smaller, and more cost-effective.

●The Arduino board relies on a microcontroller unit (MCU) to perform essential tasks like reading sensors and controlling lights.

●Chip manufacturing facilities, or foundries, are vital in determining the performance of chips used in devices like Arduino boards.

●Key components of a chip include the core, pads, and die, which are essential for logic implementation and signal transmission.

●The Sky130_fd_sc_hd variant from SkyWater foundry provides necessary technology files for chip design, with tools like OPENLANE requiring specific commands for design processes.
![411302519-3759afb9-445a-4140-832a-3ae61331d831](https://github.com/user-attachments/assets/08370fd4-78a3-4213-9b5e-46ec560fafd7)
![411303043-311a83b9-1db0-4206-b8f2-ff87eb4b17fa](https://github.com/user-attachments/assets/5a019dbf-5e0d-4372-b726-45c6ec3e4072)
![415284160-cd5d598f-6e4c-420a-9270-6fc1f7dd1bbc](https://github.com/user-attachments/assets/050df1ed-a8d2-438e-b891-9ec87e12a31c)

# DAY 2: Good floorplan vs bad floorplan and introduction to library cells

°Chip Floorplanning Considerations

°Library winding and placement

°Cell design and characterization flows

°General timing characterization parameters

![1000013490](https://github.com/user-attachments/assets/d471fe0f-8377-4840-85e3-da51cfbefcd9)
![1000013491](https://github.com/user-attachments/assets/79011030-e1b0-41bb-9730-9d58d6de3037)
![1000013492](https://github.com/user-attachments/assets/bd2e8d99-0f07-44ab-85d9-cda0b26496b7)
![1000013493](https://github.com/user-attachments/assets/eb57f139-6c95-4b43-b02a-59be120fb927)

**UTILIZATION FACTOR AND ASPECT RATIO**

In order to calculate the Utilization Factor and Aspect Ratio, we must know the height and width of core and die areas. Formula is given by:

•Utilization Factor = area occupied by the netlist / Total area occupied by the core

-If the utilization factor is 1 then it denotes 100 % utilization. --> We never go for 100 % utilization, we go for 50 % or 60 % factor.

•Aspect Ratio = height of the core / width of the core

-When aspect ratio is 1 , then its a square chip.

Once synthesis is sucessful,next step is floorplan. we use command:
    run_floorplan
    
This will create a folder inside runs folder of picorv32a directory. It will take a while to execute and once done we will get PDN GENERATION IS SUCESSFUL as shown in below image. 
![1000013494](https://github.com/user-attachments/assets/04659d29-4e4b-4b5d-86a1-5a512d844bc7)
![1000013495](https://github.com/user-attachments/assets/41a0f228-1690-4035-b48e-e58cf437ced5)

To see the actual layout after the floorplan ,go the folders as shown below:
![1000013497](https://github.com/user-attachments/assets/16709bf0-44f3-44e8-8721-987e1d3074c6)

• openlane/designs/picorv32a/runs/08-02_06-43/results/floorplan

now we need to open the magic file by the following command

• magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
![1000013499](https://github.com/user-attachments/assets/9976b0b6-2746-42a5-8336-67c8e200a6e9)
![1000013500](https://github.com/user-attachments/assets/e2cea230-ad72-4b96-9240-f3896b11dcc0)
![1000013502](https://github.com/user-attachments/assets/5c0613ad-1264-44ec-84bc-93f3b7d11cc6)

Once the Floorplanning is done sucessfully , the next step in the process is Placement. To run the placement use the command:
     run_placement 
     
![1000013503](https://github.com/user-attachments/assets/4d245e9e-bbf5-47bf-bbbe-ee9a7c31242a)

Once Placement process is done , next step is to check whether the cells are placed correctly or not.by using magic tool.

The command to view the standerd cells placement. image is shown below:

• magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
![1000013504](https://github.com/user-attachments/assets/a66a556e-481c-41a1-afc0-28b7e066197c)
![de13d2ee8d7e09a155319010cd7ff4a897e730d316964b462793586e51710da6~2](https://github.com/user-attachments/assets/76d93afa-a4e4-4a12-960b-08a2a75e5977)
![1000013617](https://github.com/user-attachments/assets/8765979e-8f27-4623-89bd-007ad4911fe7)

# Day 3: Design library cell using Magic layout and ngspice characterization

Commands to open inverter layout in magic:

•magic -T sky130A.tech sky130_inv.mag &

![1000013508](https://github.com/user-attachments/assets/0a0aeaa4-8a57-476e-a9b4-db0c4efe082d)
CMOS inverter layout 
![1000013509](https://github.com/user-attachments/assets/80d85222-759a-4646-bd69-be4898511be6)
NMOS 
![1000013510](https://github.com/user-attachments/assets/43273864-9ae3-4210-be83-f4e59e0c728c)
PMOS 
![1000013511](https://github.com/user-attachments/assets/c1cb2016-2511-404f-bfa6-20ccab999647)
Output 
![1000013512](https://github.com/user-attachments/assets/40d3d94a-f3e2-40a7-8930-53d925dc90f9)

![1000013624](https://github.com/user-attachments/assets/c2a0a59f-e3e2-4f57-9961-be0487a21e82)
![1000013631](https://github.com/user-attachments/assets/e6d84ef0-6900-4cbc-a33a-2f2c33a1202b)
![1000013622](https://github.com/user-attachments/assets/aa4f4962-5108-493d-9799-77e3e638facd)
![1000013623](https://github.com/user-attachments/assets/2f70f951-86ea-4ef4-b41f-e457bddf80b4)
![1000013635](https://github.com/user-attachments/assets/73e2c916-a08a-4b74-811e-10c042f6eb76)
![1000013636](https://github.com/user-attachments/assets/c7d11319-0e9e-42e1-a816-d9453c6ccf55)
![1000013638](https://github.com/user-attachments/assets/c037f27d-754b-4dca-816f-cc0790200b2f)
![1000013639](https://github.com/user-attachments/assets/d01340c5-df4a-4aff-b871-9ea7908efb51)
![1000013641](https://github.com/user-attachments/assets/0ecee08c-5741-4ca6-a7f1-9494d441e2bb)
![1000013642](https://github.com/user-attachments/assets/e1293913-84cf-4e87-a76a-1b3525778632)

# Day 4: PRELAYOUT TIMING ANALYSIS AND CLOCK TREE SYNTHESIS
Get the .lef file from the inverter design using command:
•openlane_working_dir/pdk/sky130/libs.tech /openlane/sky130_fd_sc_hd/track.info
Get the .lef file from the inverter design using command:
![1000013643](https://github.com/user-attachments/assets/a87fb93a-3d95-4df2-8c12-a73d9377007e)


