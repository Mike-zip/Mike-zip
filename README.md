# Michael Marquis

**Digital hardware: RTL design & verification (Verilog) | Bare-metal embedded (ARM Cortex-A9)**

B.S. Electrical Engineering, Washington State University, expected May 2028. Currently interning at Schweitzer Engineering Laboratories, doing hands-on hardware failure analysis on protection relays: tracing circuits through schematics, chasing failures to root cause with DMMs, oscilloscopes, and X-ray inspection then reworking the boards and testing until they work again, all in a NERC CIP environment.

Relevant Coursework: Digital Logic Design, Combinational and Sequential Circuits, Microprocessors.

## Projects

### [axi-uart](https://github.com/Mike-zip/axi-uart)

Parameterizable UART core with independent transmit and receive datapaths and an AXI4-Lite register interface for runtime configuration and status.

**Design decisions**
- Synchronous FIFO with binary read/write pointers for data buffering between the AXI interface and UART logic
- 2-flop input synchronizer and 16x oversampling receiver for asynchronous bit recovery on the RX line


**Verification**
- Self-checking Verilog testbench that loops 256 bytes through the core and gates PASS / FAIL on an error counter
- Verilog testbenches verifying the AXI4-Lite VALID / READY handshake

**Status:** transmit path complete and verified. Receive-path loopback verification in progress.

### [zynq-interrupt-handlers](https://github.com/Mike-zip/zynq-interrupt-handlers) · Bare-metal C on ARM Cortex-A9
 
Interrupt-driven peripheral drivers on the Zynq-7000 with no RTOS and no vendor BSP drivers: every peripheral is brought up by writing its memory-mapped registers directly and routed through the ARM Generic Interrupt Controller.
 
- Shared driver layer (UART1, MIO GPIO, 64-bit global timer, thin GIC header) with a single dispatch ISR that demultiplexes by interrupt ID
- **bounce-meter**: measures mechanical switch contact bounce in nanoseconds using dual-edge interrupts, with the 333.33 MHz global timer as a free-running timebase
- **blink-controller**: coordinates three concurrent interrupt sources; UART input sets the blink count, pushbuttons start and stop the sequence, and a periodic timer interrupt drives the RGB LED only while a sequence is active

## Contact

- LinkedIn: [linkedin.com/in/michael-d-marquis](https://www.linkedin.com/in/michael-d-marquis)
- Email: michaelmarquis43@gmail.com
