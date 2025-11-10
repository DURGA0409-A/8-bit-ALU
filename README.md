# 8-bit-ALU
## AIM
To design and implement an 8-bit Arithmetic Logic Unit (ALU) using Verilog HDL.

## TOOLS REQUIRED
Vivado

## THEORY
An ALU performs arithmetic and logical operations.
Common operations include addition, subtraction, AND, OR, XOR, NOT, and comparison.

## Procedure 
Open Vivado and create a new Verilog project.
Write the Verilog code for 2:1 MUX and use it hierarchically to build an 8:1 MUX.
Develop a testbench to apply different input and select combinations.
Compile and simulate the design using ModelSim/Quartus II simulator.
Verify outputs with expected results and save waveform observations.

## Verilog 
```
module alu_8bit(
    input [7:0] A, B,
    input [2:0] sel,
    output reg [7:0] Y
);
    always @(*) begin
        case(sel)
            3'b000: Y = A + B;       // Addition
            3'b001: Y = A - B;       // Subtraction
            3'b010: Y = A & B;       // AND
            3'b011: Y = A | B;       // OR
            3'b100: Y = A ^ B;       // XOR
            3'b101: Y = ~A;          // NOT
            3'b110: Y = A << 1;      // Shift Left
            3'b111: Y = A >> 1;      // Shift Right
            default: Y = 8'b00000000;
        endcase
    end
endmodule
```
 ## TestBench
 ```
timescale 1ns/1ps
module tb_alu_8bit;
    reg [7:0] A, B;
    reg [2:0] sel;
    wire [7:0] Y;

    alu_8bit uut (.A(A), .B(B), .sel(sel), .Y(Y));

    initial begin
        A = 8'b00001111; B = 8'b00000101;
        for(sel = 0; sel < 8; sel = sel + 1)
            #10;
        $finish;
    end
endmodule
```
## OUTPUT

## RESULT
8-bit ALU designed and simulated successfully performing arithmetic and logic operations.
