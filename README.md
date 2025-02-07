# rion-shaw-nasscom-vsd-soc-design-program
The course consists of 5 chapters. In the first part better to say "DAY1 - Inception of open-source EDA, OpenLANE and Sky130 PDK" I learned about how application software or apps are connected to the hardware of the system via system software in a pictorial view. I heard lots of new terms like Macros, Foundary IPs etc. Here I understand ASIC design is a output of RTL IPs, EDA tools and PDK data jointly. 
# DAY1 - Inception of open-source EDA, OpenLANE and Sky130 PDK
The aim is calculate the flop ratio -
![image alt](https://github.com/Rionshaw/rion-shaw-nasscom-vsd-soc-design-program/blob/0d8db12d8863e95843c649e06470677b2d646a55/Screenshot%20from%202025-02-06%2019-11-09.png)
now synthesis is started
![image alt](https://github.com/Rionshaw/rion-shaw-nasscom-vsd-soc-design-program/blob/4c0255b7745d76fe0a57730ab852577c1589317c/Screenshot%20from%202025-02-06%2019-24-44.png)
after successful completion of the synthesis we go to the reports folder of the specific run (in my case it is 06-02_13-40) and see the Yosys stat report file 
![image alt](https://github.com/Rionshaw/rion-shaw-nasscom-vsd-soc-design-program/blob/9921efa62ed347648ad249ad095eb402c1deef19/Screenshot%20from%202025-02-06%2019-36-44.png)
The count of flip-flops is given by 'sky130_fd_sc_hd_dfxtp_2'
![image alt](https://github.com/Rionshaw/rion-shaw-nasscom-vsd-soc-design-program/blob/ce9332ca06e94433ab6b249540bf6f0fe9578a9f/Screenshot%20from%202025-02-06%2019-34-55.png)
count of flip-flops - 1613 <br>
number of cells - 14876 <br>
flop ratio = 1613/14876 = 0.108429685 or 10.84%
# DAY 2 - Good floorplan VS bad floorplan and introduction to library cells

### 1. Define the floorplan using the floorplan utility from OpenLANE
we run the floorplan
![image alt](https://github.com/Rionshaw/rion-shaw-nasscom-vsd-soc-design-program/blob/e17f58ad8d10afbd5358c077651d91fdf2e08333/Screenshot%20from%202025-02-06%2020-15-15.png)

### 2. Review the floorplan output files and calculate the die area
![image alt](https://github.com/Rionshaw/rion-shaw-nasscom-vsd-soc-design-program/blob/bce02997aa3ef5e1662ed201fb1fab188eda43ad/Screenshot%20from%202025-02-06%2020-22-50.png)
![image alt](https://github.com/Rionshaw/rion-shaw-nasscom-vsd-soc-design-program/blob/98c6d8ffc27016e02906493f9e8c792289e19abb/Screenshot%20from%202025-02-06%2020-22-28.png)
The width and height of the die are given (in distance units) by the 'DIEAREA' line. The number of distance units per micron is given by the 'UNITS DISTANCE MICRONS'. The current setting is 1000 distance units per micron. <br>
Die width: 660685 d.u. ---> 660.685 microns <br>
Die height: 671405 d.u. ---> 671.405 microns <br>
Die area = 660.685x671.405 = 443587.212425 square microns

### 3. Review the floorplan in Magic
![image alt](https://github.com/Rionshaw/rion-shaw-nasscom-vsd-soc-design-program/blob/9a716f0a1a43bb21452e949434aee09a837ce557/Screenshot%20from%202025-02-06%2020-35-08.png)
![image altt](https://github.com/Rionshaw/rion-shaw-nasscom-vsd-soc-design-program/blob/4ba0e5fb80482ee92d4bc3993e3f3a6574d35c18/Screenshot%20from%202025-02-06%2020-37-50.png)
once Magic opens, press s for select the entire object and press v for allign in centre and z for zoom in.
![image alt](https://github.com/Rionshaw/rion-shaw-nasscom-vsd-soc-design-program/blob/35fad4895c4c996758a0eb3582fbdb704c4f0911/Screenshot%20from%202025-02-06%2020-46-38.png)
### 4. Perform congestion-aware placement using RePlAcE
now we run the placement 
![image alt](https://github.com/Rionshaw/rion-shaw-nasscom-vsd-soc-design-program/blob/aff8885ade47a6f254cdb217d956a4eefc61d27a/Screenshot%20from%202025-02-06%2020-56-41.png)
### 5. Review the placement in Magic
![image alt](https://github.com/Rionshaw/rion-shaw-nasscom-vsd-soc-design-program/blob/58be598611d875a07c39018d1594e2d7f4d538be/Screenshot%20from%202025-02-06%2021-06-10.png)
The standard cells have been legally placed and we can observe also the power and GND lines.
![image alt](https://github.com/Rionshaw/rion-shaw-nasscom-vsd-soc-design-program/blob/1a6c6ab30d068be15b299592f97256669d35e1d6/Screenshot%20from%202025-02-06%2021-04-08.png)
![image alt](https://github.com/Rionshaw/rion-shaw-nasscom-vsd-soc-design-program/blob/896711445f89a371fe6eef0f53d5e378df266d44/Screenshot%20from%202025-02-06%2021-05-25.png)

# DAY 3 - Design library cell using Magic Layout and ngspice characterization
### 1. Observe different placement modes with Magic
The placement mode can be controlled through the value of FP_IO_MODE. We set it to 2, run floorplan again and observe it with Magic.
![image alt](https://github.com/Rionshaw/rion-shaw-nasscom-vsd-soc-design-program/blob/d496cc211cc55925aa7c8a52d1dcdf3470ebf23b/Screenshot%20from%202025-02-06%2021-27-23.png)
![image alt](https://github.com/Rionshaw/rion-shaw-nasscom-vsd-soc-design-program/blob/6eed6342e7381905aac81f5ab0b70725413c2988/Screenshot%20from%202025-02-06%2021-30-24.png)
The IO pins have been placed around the bottom left-hand corner.
### 2. Clone CMOS inverter standard cell design from repository
Change directory to the OpenLANE flow directory within the OpenLANE working directoryand then Clone the repository(git clone https://github.com/nickson-jose/vsdstdcelldesign.git) and give command ls -ltr
![image alt](https://github.com/Rionshaw/rion-shaw-nasscom-vsd-soc-design-program/blob/074901206d31d5ce7c6c4b6e21cf2cacd4fd1032/Screenshot%20from%202025-02-06%2021-38-40.png)
### 3. Explore the inverter layout in Magic
![image alt](https://github.com/Rionshaw/rion-shaw-nasscom-vsd-soc-design-program/blob/949830aa54e6981b7ce02876c80625fe90ff8b02/Screenshot%20from%202025-02-06%2021-50-36.png)
![image alt](https://github.com/Rionshaw/rion-shaw-nasscom-vsd-soc-design-program/blob/5954833f4acec0037ad5995d8b5d78461308955c/Screenshot%20from%202025-02-06%2021-57-00.png)
![image alt](https://github.com/Rionshaw/rion-shaw-nasscom-vsd-soc-design-program/blob/523017d4e5603ff816ac5da39c08ac4f80c18679/Screenshot%20from%202025-02-07%2019-38-29.png)
Connectivity of the drains of both p-channel and n-channel MOSFETs to the output Y
![image alt](https://github.com/Rionshaw/rion-shaw-nasscom-vsd-soc-design-program/blob/75d69b80ea08b8d40c9a1ea2a6f341bea9ed6b4d/Screenshot%20from%202025-02-07%2019-42-07.png)
Connectivity of the source of the n-channel MOSFET to VGND
![image alt](https://github.com/Rionshaw/rion-shaw-nasscom-vsd-soc-design-program/blob/21dc819a9efb8c217d59378e67eecf51b5917f28/Screenshot%20from%202025-02-07%2019-46-08.png)
