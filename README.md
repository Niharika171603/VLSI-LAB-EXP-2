SIMULATION AND IMPLEMENTATION OF  COMBINATIONAL LOGIC CIRCUITS

AIM: 

   To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using Xilinx ISE.

APPARATUS REQUIRED:

            vivado 2023.2

**LOGIC DIAGRAM**

ENCODER

 ![image](https://github.com/Niharika171603/VLSI-LAB-EXP-2/assets/161016278/371705fd-5ab2-4c67-a04e-55dae52e4a7d)

DECODER

 ![image](https://github.com/Niharika171603/VLSI-LAB-EXP-2/assets/161016278/d9e4a1bb-d8b2-463c-bca5-694600c8b58c)

MULTIPLEXER

 ![image](https://github.com/Niharika171603/VLSI-LAB-EXP-2/assets/161016278/21c884a0-2ada-4648-be94-3d858f398295)

DEMULTIPLEXER

 ![image](https://github.com/Niharika171603/VLSI-LAB-EXP-2/assets/161016278/cd680ced-41bf-46c9-b58b-8dced05ff67e)

MAGNITUDE COMPARATOR

 
![image](https://github.com/Niharika171603/VLSI-LAB-EXP-2/assets/161016278/ed974ebc-7781-4eb1-a3b9-0221474ab1e8)


  
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

   
   8-3 ENCODER:

module encoder(d,a,b,c);

input [7:0]d; output a,b,c;

or (a,d[4],d[5],d[6],d[7]);

or (b,d[2],d[3],d[6],d[7]);

or (c,d[1],d[3],d[5],d[7]);

endmodule

3-8 DECODER:

module decoder(A,E,Y);

input [1:0]A;

input E;

output [3:0]Y;

assign Y[0]=~A[1]&~A[0]&E;

assign Y[1]=~A[1]&A[0]&E;

assign Y[2]=A[1]&~A[0]&E;

assign Y[3]=A[1]&A[0]&E;

endmodule

module decoder(A,Y);

input[2:0]A;

output[7:0]Y;

decoder_2_4 d1(A[1:0],~A[2],Y[3:0]);

decoder_2_4 d2(A[1:0],~A[2],Y[7:4]);

endmodule

8-1 MULTIPLEXER:

module multi(i,s,y);

input[7:0]i;

input[2:0]s;

output reg y;

always@(*)

begin

case({s[2],s[1],s[0]})

3'b000:y=i[0];

3'b001:y=i[1];

3'b010:y=i[2];

3'b011:y=i[3];

3'b100:y=i[4];

3'b101:y=i[5];

3'b110:y=i[6];

3'b111:y=i[7];

endcase

end

endmodule

1-8 DEMULTIPLEXER:

module demultiplexer(d1,d2,d3,d4,d5,d6,d7,d8,i,s0,s1,s2);

input i,s0,s1,s2;

output d1,d2,d3,d4,d5,d6,d7,d8;

wire w1,w2,w3;

not g1(w1,s0);

not g2(w2,s1);

not g3(w3,s2);

and g4(d1,w1,w2,w3,i);

and g5(d2,w1,w2,s2,i);

and g6(d3,w1,s1,w3,i);

and g7(d4,w1,s1,s2,i);

and g8(d5,s0,w2,w3,i);

and g9(d6,s0,w2,s2,i);

and g10(d7,s0,s1,w3,i);

and g11(d8,s0,s1,s2,i);

endmodule

2 BIT MAGNITUDE COMPARATOR :

module mag_com(a,b,gt,it,eq);

input [3:0]a,b;

output reg gt,it,eq;

always @(a,b)

begin

if(a>b)

begin

gt = 1'b1;

it = 1'b0;

eq = 1'b0;

end

else if(a<b)

begin

gt = 1'b0;

it = 1'b1;

eq = 1'b0;

end

else

begin

gt = 1'b0;

it = 1'b0;

eq = 1'b1;

end

end

endmodule


OUTPUT WAVEFORM


  ENCODER:
 
 ![image](https://github.com/Niharika171603/VLSI-LAB-EXP-2/assets/161016278/388ce3b4-fefa-43b3-b301-39498f6174d5)

 DECODER:

 ![image](https://github.com/Niharika171603/VLSI-LAB-EXP-2/assets/161016278/aa86bb71-8e41-4600-a075-daa78cd6b501)

 MULTIPLEXER:

 ![image](https://github.com/Niharika171603/VLSI-LAB-EXP-2/assets/161016278/f163520e-db2f-44d3-9d50-84aaa6bac082)

 DEMULTIPLEXER:

 ![image](https://github.com/Niharika171603/VLSI-LAB-EXP-2/assets/161016278/ffb55a1a-9616-4580-80e5-6b973a018bae)

 2 BIT MAGNITUDE COMPARATOR:

 ![image](https://github.com/Niharika171603/VLSI-LAB-EXP-2/assets/161016278/b9e5ff64-b6cb-426d-bfdd-d2ba436ed78f)




RESULT

Thus the simulation and synthesis of ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, 2bit MAGNITUDE COMPARATOR using vivado is successfully completed and executed.


