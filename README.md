# Blitzing Digital Electronics: A Rough Curriculum
### Inspired and Slightly Modified Version of the TinyVision.AI Course

## Section 1: Introduction to digital electronics, FPGA’s and environment setup:

### Material:

- [x]  [Shawn Hymel FPGA Part 1: Introduction](https://www.digikey.com/en/maker/projects/introduction-to-fpga-part-1-what-is-an-fpga/3ee5f6c8fa594161a655a9f960060893)
- [x]  [Shawn Hymel FPGA Part 2: environment setup](https://www.digikey.com/en/maker/projects/introduction-to-fpga-part-2-toolchain-setup/563a9518cd11466fb6a75cf3cb684d6d)
- [x]  [Converting Decimal → Binary (Khan Academy)](https://www.khanacademy.org/math/algebra-home/alg-intro-to-algebra/algebra-alternate-number-bases/v/decimal-to-binary)
- [x]  [Addition in Binary (Khan Academy)](https://www.khanacademy.org/math/algebra-home/alg-intro-to-algebra/algebra-alternate-number-bases/v/binary-addition)
- [x]  Read Harris 1.5 (Logic Gates)
- [x]  Read Harris 2.1 - 2.2 (Boolean Equations)
- [x]  [Making Sense of Boolean Algebra Theorems](https://youtu.be/kjoN5pl-m4s)
- [x]  [DeMorgan’s theorem and bubble pushing](https://youtu.be/Ezl9CpDQvK4)
- [x]  [Simplifying a sum-of-products expression](https://youtu.be/p6EyMNmVf-8)
- [x]  [Truth tables to Boolean equations: sum of products](https://youtu.be/13HCv91RGOE)
- [x]  [Truth tables to Boolean equations: product of sums](https://youtu.be/BiSxQjPZ-jA)
- [x]  Harris 2.6-2.7
- [x]  [Intro to Karnaugh Maps](https://youtu.be/pPHxpiJfyS8)
- [x]  [Rules for Making K Map Rect.](https://youtu.be/68e6eOKs8Gg)
- [x]  [K Maps and don’t-cares](https://youtu.be/U92OiiAT854)
- [x]  [4x4 K-Maps](https://youtu.be/GLSdMlzngsY)
- [ ]  Breadboarding
    - [ ]  [Lab 1 of Tufts Digital Electronics Course](https://www.ece.tufts.edu/es/4/labs/lab1_getting_started.pdf)
    - [ ]  [Building a circuit on a breadboard from a schematic](https://youtu.be/gPnP_tuey6s&t=378)

### Suggested Setup:

- [ ]  TerosHDL Plugin Setup on VS Code
- [ ]  Set Up ICE Studio

### Challenge:

1. Write code to get various colors on the 3 color LED and program the board with it. Try out the [UPduino FPGA](https://blog.idorobots.org/entries/upduino-fpga-tutorial.html) tutorial to get your hands wet.
2. Advanced challenge: Setup a command line compile using a [Simple Makefile](https://github.com/tinyvision-ai-inc/UPduino-v3.0/blob/master/RTL/blink_led/Makefile) or a more [Complex Makefile](https://github.com/XarkLabs/upduino-video/blob/master/Makefile) as an example. Go through the makefile and understand what it does.

## Section 2: **Getting started with logic design, Verilog simulations**

### Material:

- [ ]  [Shawn Hymel 3](https://www.youtube.com/watch?v=A4VfBoP4Hdk&list=PLEBQazB0HUyT1WmMONxRZn9NmQ_9CIKhb&index=3&pp=iAQB)
- [ ]  HDL Bits
    - [ ]  Basics
    - [ ]  Vectors
    - [ ]  Modules: Hierarchy
    - [ ]  Procedure
    - [ ]  More Verilog Features
- [ ]  [Preface for ZipCPU Resource](https://zipcpu.com/tutorial/lsn-00-preface.pdf)
- [ ]  Setup Verilator
- [ ]  [ZipCPU Wires and Combinatorial logic](http://zipcpu.com/tutorial/lsn-01-wires.pdf)
- [ ]  [Circuitverse Digital Logic Course](https://learn.circuitverse.org/)
    - [ ]  Binary Representation
    - [ ]  Binary Algebra
    - [ ]  Combinational SSI
    - [ ]  Logic Design
    - [ ]  Combinational MSI (Extra: Harris 2.9)
        - [ ]  [What are multiplexers good for? (10:10)](https://youtu.be/XQ4NVl9lBJA)
        - [ ]  [Implementing logic with multiplexers (11:48)](https://youtu.be/yR4qEI4h1z0)
    - [ ]  Combination LSI
- [ ]  HDL Bits
    - [ ]  Basic Gates
    - [ ]  MUX
    - [ ]  Arithmetic Circuits
    - [ ]  K Maps to Circuits

### Challenge:

- Create a System Verilog design that combines what you learnt today. You can use the [EDA Playground Example](https://www.edaplayground.com/x/9) as a starting point and modify it:
    - An `adder` module
        - Inputs: Two 8 bit unsigned numbers to be added
        - Output: The sum of the 2 numbers.
    - Testbench to exercise the block and print the output to the console
    - Bitwidth analysis is an important part of designing a hardware system as well as algorithms, especially for digital processing. We will do some bitwidth analysis as part of this question. Note that these dont require simulations to be done and can be solved by analysis):
        - What is the range of unsigned numbers that can be represented by a variable with 2 bits? 3 bits? 8 bits? 16 bits?
        - What pattern do you see here?
        - What is the minimum number of bits it takes to represent the sum of the 2 numbers? eg. if two numbers are repesented by 2 bits each, how many bits does it take to represent their sum? What if the inputs are now 3 bits instead of 2 bits? What pattern do you see?
        - What if one of the above numbers is represented by 2 bits and the other by 3 bits?
        - What if the operation were the difference of the two numbers?
        - What if the operation were a multiplication of the 2 numbers?
    
    ### Advanced Challenges/Thought experiments:
    
    - What happens if there are too few bits to represent the result of the operation? eg. if you have the sum of 2 numbers, each represented by 2 bits and the output is represented by a 2 bit number. This is known as an overflow and is a common bug/feature.
        - Can you try simulating this with your Verilog design?
    - Signed and floating point numbers can also be represented in binary.
        - Look up how to represent signed numbers in Verilog (Two's complement).
            - Harris 1.4
            - [Integer Exposed](https://integer.exposed/#0x82) visualization of signed numbers
            - [Three ways to represent negative numbers (Computerphile)](https://youtu.be/lKTsv6iVxV4)
            - [Examples of two’s complement (Ben Eater)](https://youtu.be/4qH4unVtJkE)
        - Change your adder to use signed arithmetic.
        - What is the minimum number of bits needed for the above operations if the numbers are signed instead of unsigned or a combination. What happens if a signed number overflows?
        - How to implement more complex arithmetic functions like: divide, square root, sine, cosine etc.

## Section 3: **Getting started with logic design, Verilog simulations Pt. 2**

### Material:

- [ ]  [Shawn Hymel Video Part 4](https://www.digikey.com/en/maker/projects/introduction-to-fpga-part-4-clocks-and-procedural-assignments/356e12284daf48b5bd9b80af8a6ac5b8)
- [ ]  [ZipCPU Registers](http://zipcpu.com/tutorial/lsn-02-regs.pdf)
- [ ]  Advanced reading: [Asynchronous design using Micropipelines](http://web.cse.msu.edu/~cse820/readings/sutherlandMicropipelinesTuring.pdf)
- [ ]  Complete the following Chapters from [Circuitverse Digital Logic Course](https://learn.circuitverse.org/):
    - [ ]  [Sequential SSI Components](https://learn.circuitverse.org/docs/seq-ssi/)
- [ ]  Harris 3.1-3.3
- [ ]  [Intro to sequential logic / What are flip-flops good for?](https://youtu.be/FSKUjpUpkZA)
- [ ]  [Behavior of the SR latch](https://youtu.be/YM1trTlRaSo)
- [ ]  [SR latch demo](http://www.falstad.com/circuit/circuitjs.html?ctz=CQAgjCAMB0l3BWcMBMcUHYMGZIA4UA2ATmIxARQosgoFMBaMMAKABkQUAWWsQ34lT60RIAGYBDADYBnOtUjtOPTnjzhBq9aMmz5SRWATZlvDIRDZK4c1E52ELIye61MVK1Xd2qSRwHdLazBbLi51EItFQM8bC1i0bRYY60TOblMoZPSuTJQMlAQo7PzcwotXTiKslK8MKjD1b2iguo9UlRaElVLOfBqcvqaMsE0W3tGvFUmsgA9wNHArPogwbHUy3IBlOgAXAB0ZAAotgEoWeeIXQjLIa-JNkAAlOjkD46fz+bDeBFouBARYwgCq5ACKFxAXGwxCq-wQ5EKJkeEIAslDwnEocQLJEfNBHOjGpx6tiKqS3ASWAB7Ow3OxcMB3BSweBkQhFQo+OzYGngEG5f5MkwGVlwdmcgz2CC82mw+lC5mi+CQCWELluECw3lAA)
- [ ]  [Building a D latch](https://youtu.be/4H39-fhjZrU)
- [ ]  [D latch demo](https://circuitverse.org/users/71561/projects/d-latch-5b732dfe-fd65-4848-b47e-115838a15f17)
- [ ]  [Building a D flip-flop](https://youtu.be/41-ukztBY4s)
- [ ]  [D flip-flop demo](https://circuitverse.org/users/71561/projects/d-flip-flop-4a47d9ee-8c72-4fc1-ab8d-2a0502aa6894)
- [ ]  Extra:
    - [ ]  [SR latch (Ben Eater)](https://www.youtube.com/watch?v=KM0DdEaY5sY)
    - [ ]  [D latch (Ben Eater)](https://youtu.be/peCh_859q7Q)
    - [ ]  [From D-latch to D-flip-flop (Ben Eater)](https://youtu.be/YW-_GkUguMM) (This is a different way to build a D flip-flop than what the book describes, which might help you better understand what it does.)
    - [ ]  [Latch and flip-flop operation (Intermation)](https://youtu.be/lVXjI8Mpu4w)
    - [ ]  [Timing diagrams of flip-flops and latches (Intermation)](https://youtu.be/moxMU86NeVI)
- [ ]  First Half: [PS/2 Keyboard](https://www.youtube.com/watch?v=7aXbh9VUB3U) // Cool Use of Shift Register
- [ ]  HDL Bits
    - [ ]  Latches and Flip Flops
    - [ ]  Counters
    - [ ]  Shift Registers
    - [ ]  More Circuits

### Challenge:

Challenge: Use Circuitverse or preferably SystemVerilog to create a 4-bit binary counter. This should count the following sequence: 0000, 0001, 0010 …, 1110, 1111, 0000

1. Make the counter count up or down
2. Can you make it so the counter will stop at a particular count?
3. Try to make it count on negative edges
4. What if you didn’t have a reset condition? Can you see what happens?

[Solution in EDA playground](https://www.edaplayground.com/x/9PwL)

### Advanced Challenges/Thought experiments:

1. Can you create a clock signal from plain logic gates? What is the minimum number of gates you need to create a clock? What determines the frequency of the clock?
2. How can you create a clock circuit from a NAND gate, resistor and a capacitor?

## Section 4: State Machines

### Material:

- [ ]  Harris 3.4 - 3.5
- [ ]  [Introduction to finite state machines](https://youtu.be/xIQXNzUgguU)
- [ ]  [Introduction to state machines (Intermation)](https://youtu.be/gv5fQrD8XUo) Detailed explanation of what “state” is, with a walkthrough of the traffic light example from start to finish.
- [ ]  [Breaking down the Moore machine (Intermation)](https://youtu.be/SZwLuDUsX3A)
- [ ]  [Building an FSM to detect binary patterns (Intermation)](https://youtu.be/2u46bjN50Xg)
- [ ]  [FSM example: passcode lock](https://youtu.be/a3Ldvpiz8WU)
- [ ]  [Shawn Hymmel Pt 5](https://www.youtube.com/watch?v=pK6XN7sFosI&list=PLEBQazB0HUyT1WmMONxRZn9NmQ_9CIKhb&index=5&t=61s&pp=iAQB)
- [ ]  [Sunburst paper on State Machines](http://www.sunburst-design.com/papers/CummingsSNUG2019SV_FSM1.pdf)
- [ ]  [ZipCPU Finite State Machines](http://zipcpu.com/tutorial/lsn-03-fsm.pdf)
- [ ]  HDL Bits
    - [ ]  FSM
    - [ ]  Building Larger Circuits

### Challenge:

Code up a state machine for a traffic light. Here are the specifications:

- Shall have 3 states: Red, Yellow and Green.
- Start in the Red state on reset
- When the Red timer expires, go to the Green state.
- When the Green timer expires, go to the Yellow state.
- When the Yellow timer expires, go to this Red state.
- In case of roadwork, blink the Red light.
- Identify the various inputs to the state machine
- Identify the various outputs from the state machine
- Identify what causes the system to change state.
- Draw up the state transition diagram using [diagrams.net](https://www.diagrams.net/) or [Graphviz](https://edotor.net/)
- Pick a specific way to implement the state machine and code it up on [EDA Playground](https://www.edaplayground.com/) or other tool.
- Simulate the state machine and check whether this works.

### Advanced Challenges/Thought experiments:

- Practical systems often consist of nested simple state machines rather than a single large one. Larger state machines get harder to verify and corner cases can be tough to test. Extend your state machine so you have lights at all 4 roads at an intersection.
    - What does a single state machine for a 4 road intersection look like? How does this extend to cases where you may have intersections with 2, 3 or 5 roads as well as road crossing signals?
    - What if you used the same state machine at each intersection instead of a single large one? What information does one state machine need to communicate wiht the others so that the intersection is safe for traffic?

## Section 5: **Memories: RAM, ROM**

### Material:

- [ ]  [Shawn Hymmel Pt 6](https://www.youtube.com/watch?v=0BKyiY8R5NU&list=PLEBQazB0HUyT1WmMONxRZn9NmQ_9CIKhb&index=6&t=77s&pp=iAQB)
- [ ]  [Shawn Hymmel Pt 7](https://www.youtube.com/watch?v=ykBi2H2NGyA&list=PLEBQazB0HUyT1WmMONxRZn9NmQ_9CIKhb&index=7&pp=iAQB)
- [ ]  HDL Bits
    - [ ]  Verification: Reading Simulations
    - [ ]  Verification: Writing Test Benches
- [ ]  Skim Harris Ch 4.
- [ ]  Skim Harris 5.1 - 5.4 Harris
- [ ]  Harris 5.5
- [ ]  [Shawn Hymmel Pt 8](https://www.youtube.com/watch?v=CJVMFjonx_s&list=PLEBQazB0HUyT1WmMONxRZn9NmQ_9CIKhb&index=8&t=73s&pp=iAQB)
- [ ]  [ZipCPU Using Block RAM](http://zipcpu.com/tutorial/lsn-08-memory.pdf)

### Challenge: Digital Clock

- Create a ROM module that maps hex digits to a 7 segment LED display. The module should take as input a 4 bit input and output a 7 bit vector.
- Create a counter module with a programmable value at which it rolls over and also generates a carry output. Cascade multiple of these to create a seconds, minutes and hours counter.
- Connect each of these modules to the ROM.
- Add an oscillator and clock divider that generates a pulse every second as the input to the clock.
- Add an alarm output that goes active when the clock reaches a particular time. Hint: See [here](https://www.fpga4fun.com/Opto.html) for a nice introduction to how 7 segment displays work as well as how to drive a few of these critters.

### Advanced Challenges/Thought experiments:

- How can you use a small memory to build a bigger one? eg. if you want to build an 8kB memory from two 4kB memories.
- What if you wanted double the bitwidth? How would you restructure the smaller memories?

## Section 6: Blitz Wrap-Up

### Material:

- [ ]  [Shawn Hymel Pt 9](https://www.youtube.com/watch?v=A4VfBoP4Hdk&list=PLEBQazB0HUyT1WmMONxRZn9NmQ_9CIKhb&index=3&pp=iAQB)
- [ ]  [Shawn Hymel Pt 10](https://www.youtube.com/watch?v=dXU1py-Od1g&list=PLEBQazB0HUyT1WmMONxRZn9NmQ_9CIKhb&index=10&t=1s&pp=iAQB)
- [ ]  [Shawn Hymel Pt 11](https://www.youtube.com/watch?v=gJno9TloDj8&list=PLEBQazB0HUyT1WmMONxRZn9NmQ_9CIKhb&index=11&t=4s&pp=iAQB)
- [ ]  [Shawn Hymel Pt 12](https://www.youtube.com/watch?v=DtAwbKqLA5Y&list=PLEBQazB0HUyT1WmMONxRZn9NmQ_9CIKhb&index=12&t=150s&pp=iAQB)
- [ ]  [Digital to FPGA 101](https://youtu.be/FcFbFTbngrw)
