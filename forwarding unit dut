`timescale 1ns / 1ps
//////////////////////////////////////////////////////////////////////////////////
// Company: 
// Engineer: 
// 
// Create Date: 15.11.2025 19:56:37
// Design Name: 
// Module Name: forwarding_unit
// Project Name: 
// Tool Versions: 
// Description: 
// 
// Dependencies: 
// 
// Revision:
// Revision 0.01 - File Created
// Additional Comments:
// 
//////////////////////////////////////////////////////////////////////////////////


module forwarding_unit(id_ex_rs1, 
    id_ex_rs2,
    ex_mem_rw,
    mem_wb_rw,
    ex_mem_rd,
    mem_wb_rd, 
    forward_a, 
    forward_b);
    
input logic ex_mem_rw, mem_wb_rw;
input logic [4:0] id_ex_rs1, id_ex_rs2, ex_mem_rd, mem_wb_rd;
output logic [1:0] forward_a, forward_b;
always_comb begin
if (ex_mem_rw && (ex_mem_rd != '0) && (ex_mem_rd == id_ex_rs1))
forward_a = 2'b10;
else if (mem_wb_rw && (mem_wb_rd != '0) && !(ex_mem_rw && (ex_mem_rd != '0) && (ex_mem_rd == id_ex_rs1)) && (mem_wb_rd == id_ex_rs1))
forward_a = 2'b01;
else
forward_a = 2'b00;
if (ex_mem_rw && (ex_mem_rd != '0) && (ex_mem_rd == id_ex_rs2))
forward_b = 2'b10;
else if (mem_wb_rw && (mem_wb_rd != '0) && !(ex_mem_rw && (ex_mem_rd != '0) && (ex_mem_rd == id_ex_rs2)) && (mem_wb_rd == id_ex_rs2))
forward_b = 2'b01;
else
forward_b = 2'b00;

end
endmodule
