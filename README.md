Exp-No: 02 - Write and simulate seven segment display using Verilog HDL and verify with testbench
Aim:

  To design and simulate a Seven Segment using Verilog HDL and verify its functionality through a testbench using the Vivado 2023.1 simulation environment.
Apparatus Required:

  Vivado 2023.1

Procedure:


Launch Vivado Open Vivado 2023.1 by double-clicking the Vivado icon or searching for it in the Start menu.
Create a New Project Click on "Create Project" from the Vivado Quick Start window. In the New Project Wizard: Project Name: Enter a name for the project (e.g., Mux4_to_1). Project Location: Select the folder where the project will be saved. Click Next. Project Type: Select RTL Project, then click Next. Add Sources: Click on "Add Files" to add the Verilog files (e.g., mux4_to_1_gate.v, mux4_to_1_dataflow.v, etc.). Make sure to check the box "Copy sources into project" to avoid any external file dependencies. Click Next. Add Constraints: Skip this step by clicking Next (since no constraints are needed for simulation). Default Part Selection: You can choose a part based on the FPGA board you are using (if any). If no board is used, you can choose any part, for example, xc7a35ticsg324-1L (Artix-7). Click Next, then Finish.
Add Verilog Source Files In the "Sources" window, right-click on "Design Sources" and select Add Sources if you didn't add all files earlier. Add the Verilog files (mux4_to_1_gate.v, mux4_to_1_dataflow.v, etc.) and the testbench (mux4_to_1_tb.v).
Check Syntax Expand the "Flow Navigator" on the left side of the Vivado interface. Under "Synthesis", click "Run Synthesis". Vivado will check your design for syntax errors. If any errors or warnings appear, correct them in the respective Verilog files and re-run the synthesis.
Simulate the Design In the Flow Navigator, under "Simulation", click on "Run Simulation" → "Run Behavioral Simulation". Vivado will open the Simulations Window, and the waveform window will show the signals defined in the testbench.
View and Analyze Simulation Results 
Adjust Simulation Time To run a longer simulation or adjust timing, go to the Simulation Settings by clicking "Simulation" → "Simulation Settings". Under "Simulation", modify the Run Time (e.g., set to 1000ns).
Generate Simulation Report Once the simulation is complete, you can generate a simulation report by right-clicking on the simulation results window and selecting "Export Simulation Results". Save the report for reference in your lab records.
Save and Document Results Save your project by clicking File → Save Project. Take screenshots of the waveform window and include them in your lab report to document your results. You can include the timing diagram from the simulation window showing the correct functionality of the Seven Segment across different select inputs and data inputs.
Close the Simulation Once done, by going to Simulation → "Close Simulation

Input/Output Signal Diagram:


<img width="640" height="400" alt="image" src="https://github.com/user-attachments/assets/01c96bc9-69d3-4988-8b32-8743b39818c7" />


RTL Code:
   
    module SEVENSEG(bcd,seg);
        input[3:0]bcd;
        output reg[6:0]seg;
        always @ (bcd)
        begin
            case(bcd)
            4'd0 : seg = 7'b0111111;
            4'd1 : seg = 7'b0000110;
            4'd2 : seg = 7'b1011011;
            4'd3 : seg = 7'b1001111;
            4'd4 : seg = 7'b1100110;
            4'd5 : seg = 7'b1101101;
            4'd6 : seg = 7'b1111101;
            4'd7 : seg = 7'b00001111;
            4'd8 : seg = 7'b1111111;
            4'd9 : seg = 7'b1101111;
            default : seg = 7'b0000000;
            endcase
         end
     endmodule


TestBench:

      module sevensed_tb;
          reg[3:0]bcd_tb;
          wire[6:0]seg_t;
          SEVENSEG dut(.bcd(bcd_tb),.seg(seg_t));
          initial
              begin
                  bcd_tb = 4'd0;
              #100
                  bcd_tb = 4'd1;
              #100
                  bcd_tb = 4'd2;
              #100
                  bcd_tb = 4'd3;
              #100
                  bcd_tb = 4'd4;
              #100
                  bcd_tb = 4'd5;
              #100
                  bcd_tb = 4'd6;
              #100
                  bcd_tb = 4'd7;
              #100
                  bcd_tb = 4'd8;
              #100
                  bcd_tb = 4'd9;
              end        
      endmodule

Output waveform:


![WhatsApp Image 2025-09-03 at 10 19 32_d571f62a](https://github.com/user-attachments/assets/b3c2d5dd-d055-4b6c-8228-69f4b3d14edc)

Conclusion:

The designed Seven Segment display using Verilog HDL was successfully simulated and verified using a testbench in Vivado 2022.1, demonstrating correct output for each BCD input as per the aim of the experiment. The output waveform confirms that the display accurately lights up the segments corresponding to decimal values 0–9, validating the functionality.
