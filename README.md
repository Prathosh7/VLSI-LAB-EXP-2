SIMULATION AND IMPLEMENTATION OF  COMBINATIONAL LOGIC CIRCUITS

AIM: 
 To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Xilinx ISE.

APPARATUS REQUIRED:
Vivado
Spartan6 FPGA

**LOGIC DIAGRAM**

ENCODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/3cd1f95e-7531-4cad-9154-fdd397ac439e)


DECODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/45a5e6cf-bbe0-4fd5-ac84-e5ad4477483b)


MULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/427f75b2-8e67-44b9-ac45-a66651787436)


DEMULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/1c45a7fc-08ac-4f76-87f2-c084e7150557)


MAGNITUDE COMPARATOR

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/b2fe7a05-6bf7-4dcb-8f5d-28abbf7ea8c2)


  
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

VERILOG CODE

# ENCODER:
```
module encoder(d,a,b,c);
input [7:0]d;
output a,b,c;
or(a,d[4],d[5],d[6],d[7]);
or(b,d[2],d[3],d[6],d[7]);
or(c,d[1],d[3],d[5],d[7]);
endmodule
```
# DECODER:
```
module decoder_8(a,b,c,y);
input a,b,c; 
output[7:0]y; 
and gl(y[0],(~a),(~b),(~c)); 
and g2(y[1],(~a),(~b),(c)); 
and g3(y[2],(~a),(b),(~c));
and g4(y[3],(~a),(b),(c));
and g5(y[4],(a),(~b),(~c));
and g6(y[5],(a), (~b), (c));
and g7(y[6], (a), (b), (~c)); 
and g8(y[7], (a), (b), (c));
endmodule
```
# MULTIPLEXER:
```
module mux(a,b,c,d,s0,s1,y);
input a,b,c,d,s0,s1;
output y;
assign y=s1 ?(s0?d:c):(s0?b:a);
endmodule
```
# DEMULTIPLEXER:
```
module demux(in,s0,s1,s2,d0,d1,d2,d3,d4,d5,d6,d7);
input in,s0,s1,s2;
output d0,d1,d2,d3,d4,d5,d6,d7;
assign d0=(in & ~s2 & ~s1 &~s0),
d1=(in & ~s2 & ~s1 &s0),
d2=(in & ~s2 & s1 &~s0),
d3=(in & ~s2 & s1 &s0),
d4=(in & s2 & ~s1 &~s0),
d5=(in & s2 & ~s1 &s0),
d6=(in & s2 & s1 &~s0),
d7=(in & s2 & s1 &s0);
endmodule
```
# MAGNITUDE COMPARATOR:
```
module magcomp(a,b,l,g,e);
input [3:0]a,b;
output reg l,g,e;
always @(*)
begin
if(a>b)
begin
     l=1'b0;
     g=1'b1;
     e=1'b0;
end
else if(a<b)
begin
     l=1'b1;
     g=1'b0;
     e=1'b0;
end
else
begin
     l=1'b0;
     g=1'b0;
     e=1'b1;
end
end
endmodule
```
# OUTPUT WAVEFORM
# Encoder
![Encoder](https://github.com/Prathosh7/VLSI-LAB-EXP-2/assets/168956572/77f8e9f2-32f3-4f9b-ba74-1c9196739379)
# Elaborated Design
![ ](https://github.com/Prathosh7/VLSI-LAB-EXP-2/assets/168956572/3586d4f8-bc50-4926-af8d-cd737840df4a)
# Decoder
![Decoder](https://github.com/Prathosh7/VLSI-LAB-EXP-2/assets/168956572/17c0edc4-f7cc-4118-a6dc-1fe5aa06f30c)
# Elaborated design
![ ](https://github.com/Prathosh7/VLSI-LAB-EXP-2/assets/168956572/2bdcc3b8-4632-41b7-8f19-da04abb78dea)
# Multiplexer
![Multiplexer ](https://github.com/Prathosh7/VLSI-LAB-EXP-2/assets/168956572/2d0793b5-7308-4030-b28a-7996aef35bb7)
# Elaborated design
![ ](https://github.com/Prathosh7/VLSI-LAB-EXP-2/assets/168956572/24e2c35e-c9ac-48da-836f-e5b56f379f0e)
# Demultiplexer
![Demultiplexer ](https://github.com/Prathosh7/VLSI-LAB-EXP-2/assets/168956572/4f5c1c36-d62c-4faf-95eb-4ba318de799d)
# Elaborated design
![ ](https://github.com/Prathosh7/VLSI-LAB-EXP-2/assets/168956572/fc9133dc-bf07-4d5f-9b17-9b0c255193d3)
# MAGNITUDE COMPARATOR
![ MAGNITUDE COMPARATOR ](https://github.com/Prathosh7/VLSI-LAB-EXP-2/assets/168956572/9676197e-d8fb-411e-838d-efe52e837270)
# Elaborated design
![ ](https://github.com/Prathosh7/VLSI-LAB-EXP-2/assets/168956572/d8a5faff-687d-403e-9bd4-2a9ed21309d6)

# RESULT
Hence ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR is stimulated and synthesised using Vivado 2023.2.


