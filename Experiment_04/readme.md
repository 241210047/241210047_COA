8-bit Shift Register using Flip-Flops in Logisim

Aim:
To design and simulate an 8-bit shift register using flip-flops and observe the shifting of binary data using Logisim.

What it is:
An 8-bit shift register is a sequential circuit made up of eight flip-flops connected in series. Each flip-flop stores one bit of data. The output of one flip-flop is connected to the input of the next, allowing data to shift from one stage to another on each clock pulse. In Logisim, this circuit is simulated to understand how binary data moves sequentially through the register. It is mainly used in data storage, data transfer, and serial communication systems.

Apparatus / Components Required:
Logisim software
8 D Flip-Flops
Clock
Input pin
Output pins / LEDs
Connecting wires

Theory:
A shift register is a type of sequential logic circuit that is used to store and transfer data. It operates on clock pulses and shifts data either to the left or right depending on the design. In an 8-bit shift register, eight flip-flops are connected in such a way that the output of one becomes the input of the next. On every clock pulse, the data stored in each flip-flop moves one position forward. This type of register is known as Serial-In Serial-Out (SISO) when data is given and taken out serially.

Procedure:
First, open Logisim and create a new circuit project. From the memory section, select and place eight D flip-flops on the workspace in a straight line. Then add a clock component and connect it to all the flip-flops so that they receive the same clock signal. Next, place an input pin to provide serial data and connect it to the input of the first flip-flop. After that, connect the output of each flip-flop to the input of the next flip-flop in sequence. Attach LEDs or output pins to each flip-flop output to observe the shifting process. Finally, enable the clock and run the simulation. Apply input values and observe how the data shifts from one flip-flop to the next with each clock pulse.

Observation:

Clock Pulse    Output (Q7–Q0)
Initial        00000000
1              00000001
2              00000010
3              00000100
...            ...

Result:
The 8-bit shift register was successfully designed, implemented, and simulated using Logisim. The circuit functioned correctly as expected. It was observed that the input data shifted sequentially from one flip-flop to the next with each clock pulse. The movement of data across all eight stages confirmed the proper working of the Serial-In Serial-Out shift register. The experimental results were in accordance with the theoretical concept of shift registers, demonstrating accurate data storage and transfer using flip-flops.
