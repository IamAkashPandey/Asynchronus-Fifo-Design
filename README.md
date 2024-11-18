# Asynchronus-Fifo-Design
Purpose:
This Verilog module implements a parameterized First-In-First-Out (FIFO) buffer with separate read and write clock domains, commonly used for data buffering in digital systems.

Features:

Supports independent clock domains for read and write operations.
Handles asynchronous reset for both read and write logic.
Configurable data width (DSIZE) and address size (ASIZE) for flexibility in buffer size.
Provides full (wfull) and empty (rempty) flags for status monitoring.
Module Parameters:

DSIZE: Sets the width of the data bus (default: 8 bits).
ASIZE: Defines the number of address bits, controlling the FIFO depth as 
2
𝐴
𝑆
𝐼
𝑍
𝐸
2 
ASIZE
 .
Inputs:

wdata: Input data for writing.
winc: Write enable signal.
wclk: Write clock.
wrst_n: Asynchronous reset for the write logic (active low).
rinc: Read enable signal.
rclk: Read clock.
rrst_n: Asynchronous reset for the read logic (active low).
Outputs:

rdata: Data read from the FIFO.
wfull: Indicates if the FIFO is full, blocking further writes.
rempty: Indicates if the FIFO is empty, blocking further reads.
Internal Components:

Sync Modules (sync_r2w, sync_w2r): Synchronize pointers across clock domains.
Memory Block (fifomem): Holds the FIFO data with write and read access.
Control Modules (wptr_full, rptr_empty): Manage write and read pointers and flag generation.
Usage Instructions:

Instantiate the module and configure DSIZE and ASIZE as needed.
Drive the wclk and rclk with appropriate frequencies.
Use winc and rinc to control write and read operations, ensuring data synchronization.
Testbench:

A sample testbench is included to verify the module functionality.
Simulates reset, write, and read operations while monitoring outputs (rdata, wfull, rempty).
Can be run in any standard Verilog simulation tool
