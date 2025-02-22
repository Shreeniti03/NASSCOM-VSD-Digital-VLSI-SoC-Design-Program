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

**• UTILIZATION FACTOR AND ASPECT RATIO**

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

•Inverter layout is modified using grid command with metal info (x, y coords & spacing). 

•Contacts are placed at grid line intersections. 

•Cell dimensions are odd multiples of metal height/width, within grid boundaries.

![1000013659](https://github.com/user-attachments/assets/4b821d99-41d9-43f8-80be-19601dc3f7cd)
The track info is shown below:
![1000013660](https://github.com/user-attachments/assets/193e14d2-6a93-46fc-99c3-42c891b45cf0)

**• Steps to convert magic layout to std cell lef**

The lef file of std cell of inverter is obtained by doing write lef in tickon window
![1000013661](https://github.com/user-attachments/assets/fc2d9cc7-713e-43fe-aa73-8599be1c21fa)

**• Steps to configure synthesis settings to fix slack and include vsdinv**

• After synthesizing Picorv32a, slack issues arose despite successful floorplanning and placement.

• To address this, MAX_CAP_FANOUT was set to 4, but slack issues persisted. 

•The sky130_vsdinv.lef file was then inserted as a LEF input to help resolve the slack issues.

re-Synthesis
![1000013662](https://github.com/user-attachments/assets/1daf3999-423b-4623-aba2-50d6284ef0b8)

re-Floorplan
![1000013663](https://github.com/user-attachments/assets/1f087063-ab38-441d-8452-215a50b19e03)

re-Placement
![1000013667](https://github.com/user-attachments/assets/85ddd028-4fd5-4b4d-9e3c-592d98bcf575)

**• Post synthesis timing analysis**

• A pre_sta_config.tcl file was created to analyze the synthesized netlist.
![1000013672](https://github.com/user-attachments/assets/a0c08da1-6266-4df4-89c5-606dd79c7edf)

• Delayed cells were replaced with larger cells, reducing slack from -26.64 to -21.85. 
![1000013668](https://github.com/user-attachments/assets/ed03bf82-0a71-496b-a5b7-571cd78f4629)

• The updated netlist was then overwritten in the synthesis results.

• Re-floorplanning and re-placement with updated netlist, followed by CTS, still resulted in slack violation of -7.63.

**• Timing analysis with openSTA**

• OpenROAD performs STA after CTS, reading necessary files, linking with Picorv32a, setting propagated clock, and checking timing reports.
![1000013678](https://github.com/user-attachments/assets/f6b27948-1282-4a38-a2a7-769481c4869c)
•for min and max libraries the slack is 4.28

•for typical library the slack is -5.22

•after removing sky130_fd_sc_hd_clkbuffer1 for typical library the slack is -5.15

•after removing sky130_fd_sc_hd_clkbuffer1 for min max libraries the slack is 3.6395 for setup and for hold is 1.9582
![1000013658](https://github.com/user-attachments/assets/fb160056-cf68-4bf5-bcd1-7e78d201e704)

# Day 5 - Final steps for RTL2GDS using tritonRoute and openSTA

•first step is to build the power distribution network by follwing command :
    gen_pdn
![1000013679](https://github.com/user-attachments/assets/7d41a874-d92f-4121-96a3-e10e3a3b947b)
![1000013680](https://github.com/user-attachments/assets/f87f4d08-6eaf-4061-a13a-8dbe4a8150c9)
•To check PDN, open Magic tool go to /tmp/floorplan/ indside the run folder in openlane directory by using below command :

magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read 14-pdn.def &
 
![1000013681](https://github.com/user-attachments/assets/6151356d-8a9d-490e-b8a1-85996f71b29c)
![1000013682](https://github.com/user-attachments/assets/731577e2-d0a2-4e19-bad2-cf728bfbd751)

•Final step is routing to run routing use below command :
     run_routing
![1000013680](https://github.com/user-attachments/assets/2a684f67-09dc-4ab6-b012-f8fa5e79947e)

•To view the final design with routing in Magic tool , go to the results/routing/ in the runs folder of openlane directory by using below command :

magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.def &

![1000013683](https://github.com/user-attachments/assets/7cbb875b-10ae-483f-abdf-4ac75ef3a162)
The power distribution network layout is shown below
![1000013693](https://github.com/user-attachments/assets/ce30ec0c-df9c-4502-b898-c4f5e65fd44a)

**• Detailed routing using Triton-route**

The current def file should be in pdn stage and set the ROUTING_STRATEGY should be 0 and then run the command run_routing.
![1000013723](https://github.com/user-attachments/assets/8f4dc156-a4f5-4bff-8371-9d39d7e1c0a3)
![1000013742](https://github.com/user-attachments/assets/c1c6ed0a-ad46-41ba-af8f-adb3adb1e713)

The spef file is extracted using following command shown below :
![1000013724](https://github.com/user-attachments/assets/70282dac-d008-4a42-9493-7dd9b21d5d73)
![1000013728](https://github.com/user-attachments/assets/7381b04c-03e9-4cf0-a86e-94c16baa50da)


**• Post-route STA analysis**

Commands used to get min/max slacks for hold and setup analysis:
![1000013729](https://github.com/user-attachments/assets/16ce5fad-0819-40e7-be8d-4334cf5c2559)


• Hold slack is Met
![1000013730](https://github.com/user-attachments/assets/8ec12859-fe95-4c38-8490-073b80d27f26)


• Setup slack is Met
![1000013731](https://github.com/user-attachments/assets/582b9726-6600-4669-b09d-c05d5b339c81)

# Acknowledgement 

I'd like to thank Mr. Kunal Ghosh and Mr. Nickson Jose for their amazing guidance during the DIGITAL-VLSI-SOC-DESIGN-AND-PLANNING workshop. Their expertise in chip design was incredibly helpful and I'm grateful for their support.
