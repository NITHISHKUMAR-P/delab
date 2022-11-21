# DE_LAB _ EXPS
## <a href="https://github.com/Jovita08/Study-of-basic-digital-IC-s-and-verification-of-truth-tables-for-different-logic-gates-realization-" target="_blank">Exp - 1 - Study-of-basic-digital-IC-s-and-verification-of-truth-tables</a>
```
module gates(a,b,y1,y2,y3,y4,y5,y6,y7);
input a,b;
output y1,y2,y3,y4,y5,y6,y7;
and (y1,a,b);
or (y2,a,b);
not (y3,a);
xor (y4,a,b);
nand (y5,a,b);
nor (y6,a,b);
xnor (y7,a,b);
endmodule
```
## <a href="https://github.com/Mothesh-M127/Exp-02-Implementation-of-Half-Adder-and-Full-Adder-circuit.git" target="_blank">Exp-02-Implementation-of-Half-Adder-and-Full-Adder-Circuit</a>

### HALF ADDER
```
module HalfAdder(a,b,sum,carry);
input a,b;
output sum,carry;
xor(sum,a,b);
and(carry,a,b);
endmodule 
```
### FULL ADDER
```
module FullAdder(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
assign sum = ((a^b)^c);
assign carry = ((a&b)|(b&c)|(c&a));
endmodule
```
## <a href="https://github.com/NITHISHKUMAR-P/Experiment--03-Half-Subtractor-and-Full-subtractor.git" target="_blank">Exp--03-Half-Subtractor-and-Full-subtractor</a>
### HALF SUBTRACTOR
```
module HalfSubtractor(A,B,Diff,Borrow);
input A,B;
output Diff,Borrow;
wire x;
xor (Diff, A,B);
not(x,A);
and(Borrow,x,B);
endmodule
```
### FULL SUBTRACTOR
```
module FullSubtractor(A,B,C,Diff,Borrow);
input A,B,C;
output Diff,Borrow;
wire p;
assign Diff = ((A^B)^C);
not(p,A);
assign Borrow = ((p&B)|(p&C)|(B&C));
endmodule
```
## <a href="https://github.com/SanjayKumarAIML/Experiment--04-Implementation-of-combinational-logic-using-universal-gates" target="_blank">Exp 04-Implementation-of-combinational-logic-using-universal-gates</a>

### Using NAND Operation:
```
module combine1(A,B,C,D,F);
input A,B,C,D;
output F;
wire P,Q,R;
assign P = C&(~B)&(~A);
assign Q = D&(~C)&(~A);
assign R = (~C)&B&(~A);
assign F = (~P&~Q&~R);
endmodule
```
### Using NOR Operation:
```
module combine2(A,B,C,D,F);
input A,B,C,D;
output F;
wire P,Q,R,S;
assign P = C&(~B)&A;
assign Q = D&(~C)&A;
assign R = C&(~B)&A;
assign S = ~(P|Q|R);
assign F = ~S;
endmodule
```
## <a href="https://github.com/Shrruthilaya-Gangadaran/Experiment--05-Implementation-of-flipflops-using-verilog.git" target="_blank">Exp 05-Implementation-of-flipflops-using-verilog</a>
### SR FLIP FLOP:
```
module sr(s,r,clock,q,qbar);
input s,r,clock;
output q,qbar;
wire x,y;
nand(x,s,clock);
nand(y,r,clock);
nand(q,x,qbar);
nand(qbar,y,q);
endmodule
```
### D FLIP FLOP:
```
module dflp(D,Clock,Q,Qbar);
input D,Clock;
output Q,Qbar;
assign Dbar = ~D;
wire X,Y;
nand (X,D,Clock);
nand (Y,Dbar,Clock);
nand (Q,X,Qbar);
nand (Qbar,Y,Q);
endmodule
```

### JK FLIP FLOP:
```
module jkflp(J,K,Clock,Q,Qbar);
input J,Clock,K;
output Q,Qbar;
wire S,R;
nand (S,J,Clock,Qbar);
nand (R,K,Clock,Q);
nand (Q,S,Qbar);
nand (Qbar,R,Q);
endmodule
```
### T FLIP FLOP:
```
module tflp(T,Clock,Q,Qbar);
input T,Clock;
output Q,Qbar;
wire A,B;
nand (A,T,Clock,Qbar);
nand (B,T,Clock,Q);
nand (Q,A,Qbar);
nand (Qbar,B,Q);
endmodule
```

## <a href="https://github.com/Pradeesh333/Exp-7-Synchornous-counters-" target="_blank">Exp-6-Synchornous-counters-</a>
### UP-COUNTER:
```
module UC(input clk,input reset,output[0:3]counter);
reg[0:3] counter_up;
always@ (posedge clk or posedge reset)
begin
if(reset)
counter_up <= 4'd0;
else
counter_up <= counter_up + 4'd1;
end
assign counter = counter_up;
endmodule
```

### DOWN-COUNTER:
```
module DC(input clk,input reset,output[0:3]counter);
reg[0:3] counter_down;
always@(posedge clk or posedge reset)
begin
if(reset)
counter_down <= 4'd0;
else
counter_down <= counter_down - 4'd1;
end
assign counter = counter_down;
endmodule
```
## <a href="https://github.com/Kaushika-Anandh/Exercise-07-Multiplexer-and-De--multiplexer" target="_blank">Ex 07-Multiplexer-and-De--multiplexer</a>
### MULTIPLEXER:
```
module mux(I0,I1,I2,I3,S0,S1,Y);
input I0,I1,I2,I3,S0,S1;
output Y;
wire S0C,S1C;
not(S0C,S0);
not(S1C,S1);
wire P,Q,R,S;
and(P,S0C,S1C,I0);
and(Q,S0C,S1,I1);
and(R,S0,S1C,I2);
and(S,S0,S1,I3);
or(Y,P,Q,R,S);
endmodule
```

### DEMULTIPLEXER:
```
module demux(I,S0,S1,Y0,Y1,Y2,Y3);
input I,S0,S1;
output Y0,Y1,Y2,Y3;
wire S0C,S1C;
not(S0C,S0);
not(S1C,S1);
and(Y0,I,S0C,S1C);
and(Y1,I,S0C,S1);
and(Y2,I,S0,S1C);
and(Y3,I,S0,S1);
endmodule
```
## <a href="https://github.com/ezhilmathir/Experiment-08-Encoders-and-decoders-" target="_blank">Exp 08-Encoders-and-decoders</a>
### Encoder
```
module encod(d0,d1,d2,d3,d4,d5,d6,d7,a,b,c);
input d0,d1,d2,d3,d4,d5,d6,d7;
output a,b,c;
or(a,d4,d5,d6,d7);
or(b,d2,d3,d6,d7);
or(c,d1,d3,d5,d7);
endmodule
```
### DECODER:
```
input a,b,c;
output d0,d1,d2,d3,d4,d5,d6,d7;
assign d0 = (~a&~b&~c);
assign d1 = (~a&~b&c);
assign d2 = (~a&b&~c);
assign d3 = (~a&b&c);
assign d4 = (a&~b&~c);
assign d5 = (a&~b&c);
assign d6 = (a&b&~c);
assign d7 = (a&b&c);
endmodule 
```
## <a href="https://github.com/AshwinRaaj/Exercise-09-Shift-registers-using-verilog-" target="_blank">Exp 09-Shift-registers</a>
### i) PISO:
```
module piso(Clk, Parallel_In,load, Serial_Out);
input Clk,load;
input [3:0]Parallel_In;
output reg Serial_Out;
reg [3:0]tmp;
always @(posedge Clk)
begin
if(load)
tmp<=Parallel_In;
else
begin
Serial_Out<=tmp[3];
tmp<={tmp[2:0],1'b0};
end
end
endmodule
```

### ii) PIPO:
```
module pipo(PI,Clk,PO);
input Clk;
input [3:0] PI;
output reg [3:0] PO;
always @ (posedge Clk)
begin
PO=PI;
end 
endmodule 
```

### iii) SIPO:
```
module sipo(SI,Clk,Po);
input SI,Clk;
output [0:7]  Po;
reg [0:7]temp;
always @ (posedge Clk)
begin
temp={temp[0:6],SI};
end
assign Po=temp;
endmodule 
```
