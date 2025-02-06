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

