# VLSI-LAB-EXPERIMENTS
AIM: To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

APPARATUS REQUIRED: Xilinx 14.7 Spartan6 FPGA

PROCEDURE: STEP:1 Start the Xilinx navigator, Select and Name the New project. STEP:2 Select the device family, device, package and speed. STEP:3 Select new source in the New Project and select Verilog Module as the Source type. STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it. STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax. STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table. STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window. STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu. STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here. STEP:12 Load the Bit file into the SPARTAN 6 FPGA STEP:11 On the board, by giving required input, the LEDs starts to glow light, indicating the output.

Logic Diagram :

Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)


Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)


Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)


Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)



Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)



8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)



VERILOG CODE:
# Program
# Logic Gates:
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
# Half Adder:
```
module halfadder(a,b,sum,carry);
input a,b;
output sum,carry;
xor g1(sum,a,b);
and g2(carry,a,b);
endmodule
```
# Half Subractor:
```
module halfsubtractor(a,b,diff,borrow);
input a,b;
output diff,borrow;
xor g1(diff,a,b);
and g2(borrow,~a,b);
endmodule
```
# Full Adder:
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
# Full Subtractor:
```
module fs(a,b,bin,d,bout);
input a,b,bin; 
output d,bout;
wire w1,w2,w3;
xor g1(w1,b,bin; 
xor g2(d,w1,a);
and g3(w2,a,~w1);
and g4(w3,~b,bin);
or g5(bout,w2,w3);
endmodule
```
# 4 bit ripple carry adder:
```

module rippe_adder(S,Cout,X,Y,Cin);
input [3:0] X,Y;
input Cin;
output [3:0] S;
output Cout;
wire w1,w2,w3;
fulladder u1(S[0],w1,X[0],Y[0],Cin);
fulladder u2(S[1],w2,X[1],Y[1],w1);
fulladder u3(S[2],w3,X[2],Y[2],w2);
fulladder u4(S[3],Cout,X[3],Y[3],w3);
endmodule

module fulladder(S,CO,X,Y,Ci);
input X,Y,Ci;
output S,CO;
wire w1,w2,w3;
xor G1(w1,X,Y);
xor G2(S,w1,Ci);
and G3(w2,X,Ci);
and G4(w3,X,Y);
or G5(CO,w3,w3);
endmodule
```

# 8 bit ripple carry adder:
```
module rippe_adder(S,Cout,X,Y,Cin);
input [7:0] X,Y;
input Cin;
output [7:0] S;
output Cout;
wire w1,w2,w3,w4,w5,w6,w7;
fulladder u1(S[0],w1,X[0],Y[0],Cin);
fulladder u2(S[1],w2,X[1],Y[1],w1);
fulladder u3(S[2],w3,X[2],Y[2],w2);
fulladder u4(S[3],w4,X[3],Y[3],w3);
fulladder u5(S[4],w5,X[4],Y[4],w4);
fulladder u6(S[5],w6,X[5],Y[5],w5);
fulladder u7(S[6],w7,X[6],Y[6],w6);
fulladder u8(S[7],Cout,X[7],Y[7],w7);
endmodule

module fulladder(S,CO,X,Y,Ci);
input X,Y,Ci;
output S,CO;
wire w1,w2,w3;
xor G1(w1,X,Y);
xor G2(S,w1,Ci);
and G3(w2,X,Ci);
and G4(w3,X,Y);
or G5(CO,w3,w3);
endmodule
```

# OUTPUT:
# OR gate:
![image](https://github.com/j-gugan/VLSI-LAB-EXP-1/assets/163828735/d4f22570-81cb-4327-b927-a85013f19b52)
# NOT gate:
![image](https://github.com/j-gugan/VLSI-LAB-EXP-1/assets/163828735/9d7200da-8b41-4233-aa11-6ce79ca2494d)
# AND gate:
![image](https://github.com/j-gugan/VLSI-LAB-EXP-1/assets/163828735/44466d73-5ff4-4162-b00e-3d5d1bc84b00)
# NAND gate: 
![image](https://github.com/j-gugan/VLSI-LAB-EXP-1/assets/163828735/149fe8ad-e949-40ba-a485-8b5128aa62cd)
# NOR gate:
![image](https://github.com/j-gugan/VLSI-LAB-EXP-1/assets/163828735/fd15907b-313f-4e65-b18d-71e5062dd93c)
# XNOR gate:
![image](https://github.com/j-gugan/VLSI-LAB-EXP-1/assets/163828735/ca3715cd-212c-4fd8-9359-b6bd05b20c88)
# XOR gate:
![image](https://github.com/j-gugan/VLSI-LAB-EXP-1/assets/163828735/03fee7a7-7fd1-4a14-8d6c-8c5628bf848d)
# Half Adder:
![half adder1](https://github.com/j-gugan/VLSI-LAB-EXP-1/assets/163828735/22c46686-7646-45d2-80b8-478b7576ca00)
# Half Subtracter: 
![image](https://github.com/j-gugan/VLSI-LAB-EXP-1/assets/163828735/c01f422e-c424-43a5-ab56-ca8d1a873f4e)
# Full Adder:
![full adder](https://github.com/j-gugan/VLSI-LAB-EXP-1/assets/163828735/0023fb24-70a5-478c-acf9-506e965188a3)
# Full Subtracter:
![full subtracter](https://github.com/j-gugan/VLSI-LAB-EXP-1/assets/163828735/79dc011d-c0b9-4422-88f5-e61a8379488c)
# 4 Bit Ripple Carry Adder:
![rip 4bit](https://github.com/j-gugan/VLSI-LAB-EXP-1/assets/163828735/42c5b397-05d8-4607-a491-165ea8a67711)

# 8 Bit Ripple Carry Adder:
![rip 8 bit](https://github.com/j-gugan/VLSI-LAB-EXP-1/assets/163828735/efa076f1-4429-4f9e-a368-f7be4d2685fb)



# RESULT:
Hence Logic Gates,Adders and Subtractor are simulated and synthesised using Xilinx ISE.

