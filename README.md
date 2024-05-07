# VLSI-LAB-EXP-4

# SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS

Date:


AIM: 
 To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Xilinx ISE.

APPARATUS REQUIRED:
Xilinx 14.7
Spartan6 FPGA

PROCEDURE:

STEP:1  Start  the Xilinx navigator, Select and Name the New project.

STEP:2  Select the device family, device, package and speed.       

STEP:3  Select new source in the New Project and select Verilog Module as the Source type.                       

STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it.

STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax.                       

STEP:6  Click the simulation to simulate the program and  give the inputs and verify the outputs as per the truth table.               

STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window.

STEP:8  Select Check Syntax from the Synthesize  XST Process. Double Click in the  FloorplanArea/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 

STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.

STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.

STEP:11  On the board, by giving required input, the LEDs starts to glow light, indicating the output.

SR FLIPFLOP

LOGIC DIAGRAM:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)

VERILOG CODE:

```
module srff(clk,rst,s,r,q);
input clk,rst,s,r;
output reg q;
always @(posedge clk)
begin
if(rst)
 q<=1'b0;
else
 begin
 case({s,r})
 2'b00:q<=q;
 2'b01:q<=1'b0;
 2'b10:q<=1'b1;
 2'b11:q<=1'bx;
 default:q<=1'bx;
 endcase
 end
end 
endmodule
```

Output:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/147235565/d2589f5d-1387-4a51-a34b-ad3ed09dd477)


JK FLIPFLOP

LOGIC DIAGRAM:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)

VERILOG CODE:

```
module jkff(clk,rst,j,k,q);
input clk,rst,j,k;
output reg q;
always @(posedge clk)
begin
if(rst)
q<=1'b0;
else
begin
case({j,k})
 2'b00:q<=q;
 2'b10:q<=1'b1;
 2'b11:q<=~q;
default:q<=1'bx;
endcase
end
end
endmodule
```
Output:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/147235565/65e5b169-de61-44f0-89e2-6ecdb03e2749)

T FLIPFLOP

LOGIC DIAGRAM:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)

VERILOG CODE:

```
module tff(clk,rst,t,q);
input clk,rst,t;
output reg q;
always @(posedge clk)
begin
if(rst)
q<=0;
else if(t)
q<=~q;
else
q<=q;
end
endmodule
```
Output:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/147235565/3a96986a-1d8a-4f8b-b4f2-47c9f2e7fb25)

D FLIPFLOP

LOGIC DIAGRAM:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)

VERILOG CODE:

```
module dff(d,clk,rst,q);
input d,clk,rst;
output reg q;
begin
if(rst)
q <=1'b0;
else
q <= d;
end
endmodule
```
Output:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/147235565/d81b6b6d-48fa-48f4-aa63-555383ab69ab)

COUNTER

LOGIC DIAGRAM:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)

VERILOG CODE:

```
module mod10counter(clk,rst,count);
input clk,rst;
output[3:0]count;
reg[3:0]count;
always@(posedge clk)
begin
if(rst|count==4'b1001)
count<=4'b0;
else
count<=count+1;
end
endmodule
```

Output:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/147235565/e22de50d-ec1f-4942-8ed1-a493ee5fc69c)


UP COUNTER:

LOGIC DIAGRAM:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/147235565/594840eb-45c6-4e56-80eb-a0757ab72b02)

VERILOG CODE:

```
module upcounter(clk,rst,count);
input clk,rst;
output[3:0]count;
always@(posedge clk)
begin
if(rst)
count<=4'b0;
else
count<=count+1;
end
endmodule
```

OUTPUT:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/147235565/10b3e098-e40a-4da8-842c-ef68742c74ef)

DOWN COUNTER

LOGIC DIAGRAM:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/147235565/16b90a3e-c2e7-435a-aa44-8bc0cf7871b9)

VERILOG CODE:

```

module downcounter(clk,rst,count);
input clk,rst;
output[3:0]count;
reg[3:0]count;
always@(posedge clk)
begin
if(rst)
 count<=4'b0;
else
 count <=count-1;
end
endmodule
```
OUTPUT:

![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/147235565/307fe185-c5f7-45b1-b04f-968fb79a89ad)

RESULT
Hence, the simulation and synthesis of SR, JK, T, D - FLIPFLOP, COUNTER DESIGN is verified using Xilinx ISE


