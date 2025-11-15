module forwarding_unit_tb;

    logic [4:0] id_ex_rs1, id_ex_rs2;
    logic [4:0] ex_mem_rd, mem_wb_rd;
    logic       ex_mem_rw, mem_wb_rw;

    logic [1:0] forward_a, forward_b;

    forwarding_unit dut(
        .id_ex_rs1(id_ex_rs1),
        .id_ex_rs2(id_ex_rs2),
        .ex_mem_rd(ex_mem_rd),
        .mem_wb_rd(mem_wb_rd),
        .ex_mem_rw(ex_mem_rw),
        .mem_wb_rw(mem_wb_rw),
        .forward_a(forward_a),
        .forward_b(forward_b)
    );

    initial begin
    id_ex_rs1 = 5'd1;
    id_ex_rs2 = 5'd2;
    ex_mem_rd = 5'd7;
    mem_wb_rd = 5'd8;
    ex_mem_rw = 0;
    mem_wb_rw = 0;
    #10;
        // ------------------------------
        // 1) RS1 EX HAZARD (ForwardA = 10)
        // ------------------------------
        id_ex_rs1 = 5'd5;  
        id_ex_rs2 = 5'd0;  
        ex_mem_rd = 5'd5;  
        mem_wb_rd = 5'd0;
        ex_mem_rw = 1;     
        mem_wb_rw = 0;
        #10;

        // ------------------------------
        // 2) RS1 MEM HAZARD (ForwardA = 01)
        // ------------------------------
        id_ex_rs1 = 5'd7;
        id_ex_rs2 = 5'd0;
        ex_mem_rd = 5'd0;
        mem_wb_rd = 5'd7;
        ex_mem_rw = 0;
        mem_wb_rw = 1;
        #10;

        // ------------------------------
        // 3) RS2 EX HAZARD (ForwardB = 10)
        // ------------------------------
        id_ex_rs1 = 5'd0;
        id_ex_rs2 = 5'd8;
        ex_mem_rd = 5'd8;
        mem_wb_rd = 5'd0;
        ex_mem_rw = 1;
        mem_wb_rw = 0;
        #10;

        // ------------------------------
        // 4) RS2 MEM HAZARD (ForwardB = 01)
        // ------------------------------
        id_ex_rs1 = 5'd0;
        id_ex_rs2 = 5'd3;
        ex_mem_rd = 5'd0;
        mem_wb_rd = 5'd3;
        ex_mem_rw = 0;
        mem_wb_rw = 1;
        #10;

        $finish;

    end

endmodule
