# VLSI-LAB-EXPERIMENTS
 AIM: To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

apparatus required: Xilinx 14.7 Spartan6 FPGA

# PROCEDURE:
```
STEP:1 Start the Xilinx navigator, Select and Name the New project.
 STEP:2 Select the device family, device, package and speed.
 STEP:3 Select new source in the New Project and select Verilog Module as the Source type.
 STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it.
 STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax.
 STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.
STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window.
 STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained.
 STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.
  STEP:11 On the board, by giving required input, the LEDs starts to glow light, indicating the output.
STEP:12 Load the Bit file into the SPARTAN 6 FPGA
```
# Logic Diagram :

# Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)
# Verilog Code:
```
module logicgate (a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
input a,b;  
output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b);
xor(xorgate,a,b);
nand(nandgate,a,b); 
nor(norgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule
```
# Output:
![328125633-ceb0e2ab-9b30-4463-b11d-a57fde180035](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160302888/2ffbc783-48f4-43dc-87a5-4abe76fbeb5c)


Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)
# Verilog Code:
```
module halfadder(a,b,sum,carry);
input a,b;
output sum,carry;
xor g1(sum,a,b);
and g2(carry,a,b);
endmodule
```
# output:
![328125812-110b3da5-ccec-4ac8-a2a3-44c0d5b46d4c](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160302888/8103692c-6325-45b2-b7de-324857c2be22)


# Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)
# verilog code :
```
module fadd(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor g1(w1,a,b);
and g2(w2,a,b);
xor g3(sum,w1,c);
and g4(w3,w1,c);
or g5(carry,w3,w2);
endmodule
```
# output:
![image](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160302888/7d770a15-3ac5-4283-bddf-63fea2474004)



# Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)

# Verilog code:
```
module halfsubtractor(a,b,diff,borrow);
input a,b;
output diff,borrow;
xor g1(diff,a,b);
and g2(borrow,~a,b);
endmodule
```
# output :
![328126358-64f11318-01d1-4d15-b8d7-b34c3e6141ee](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160302888/2d855881-7549-42d6-84c3-4aad82173d84)




# Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)
# verilog code:
```
module fs(a,b,bi,d,bo);
input a,b,bi;
output d,bo;
wire w1,w2,w3,w4,w5;
not g1(w1,a);
xor g2(w2,a,b);
and g3(w3,w1,b);
not g4(w4,w2);
xor g5(d,w2,bi);
and g6(w5,w4,bi);
or g7(bo,w5,w3);
endmodule
```
# output :
![328126610-1dc8d314-9b4a-4dbb-b2de-310d8285531e](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160302888/721855f2-8105-47eb-9cd2-1f77fbfe57b5)



# 8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)

# verilog code :
```
module rippleCA(a, b, cin, sum, cout);
input [07:0] a;
input [07:0] b;
input cin;
output [7:0]sum;
output cout;
wire[6:0] c;
fulladd a1(a[0],b[0],cin,sum[0],c[0]);
fulladd a2(a[1],b[1],c[0],sum[1],c[1]);
fulladd a3(a[2],b[2],c[1],sum[2],c[2]);
fulladd a4(a[3],b[3],c[2],sum[3],c[3]);
fulladd a5(a[4],b[4],c[3],sum[4],c[4]);
fulladd a6(a[5],b[5],c[4],sum[5],c[5]);
fulladd a7(a[6],b[6],c[5],sum[6],c[6]);
fulladd a8(a[7],b[7],c[6],sum[7],cout);
endmodule
module fulladd(a, b, cin, sum, cout);
input a;
input b;
input cin;
output sum;
output cout;
assign sum=(a^b^cin);
assign cout=((a&b)|(b&cin)|(a&cin));
endmodule
```
# Output:
![328127045-c3f9f247-599e-42b2-b3ec-e63a563332bf](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160302888/906f5c9a-ea85-4af7-a4f9-db5f9d310a66)


# RESULT:
Hence the Logic Gates, Adders and Subtractors are simulated and synthesised using Xilinx ISE.

