# How Computers Understand and Process Binary 💻

Computers use **binary**, a system of only two digits (0 and 1), to represent all data because their internal circuits are fundamentally **on** or **off** switches. Think of a light switch: it's either on (1) or off (0). A computer's processor is made of millions of tiny transistors that act as these switches. This two-state system is the foundation for all computer operations.

---

## Data Conversion to Binary 🔄

Every piece of data—text, images, sound, and numbers—must be converted into this binary format for a computer to understand and process it.

* **Numbers:** Decimal numbers are converted to their binary equivalents. For example, the number 5 is represented as 101 in binary. This conversion is done using a process of repeated division by 2.
* **Text:** Characters are assigned a specific binary code. A widely used system is **ASCII** (American Standard Code for Information Interchange) or **Unicode**, which assigns a unique binary number to each letter, number, and symbol. For example, the capital letter 'A' is represented as `01000001` in ASCII.
* **Images and Sound:**
    * Images are broken down into tiny dots called **pixels**. Each pixel's color is assigned a unique binary code.  For instance, in a simple black-and-white image, a black pixel might be 1 and a white pixel might be 0.
    * Sound is converted by sampling the sound wave at regular intervals and assigning a binary value to the amplitude (height) of the wave at each point. The more samples taken, the higher the quality.

---

## Data Processing and Storage 🧠

Once data is in binary form, the computer processes it using **logic gates** and stores it in **registers**.

* **Logic Gates:** These are the building blocks of the computer's processor. They take one or more binary inputs (0s and 1s) and produce a single binary output based on a specific logical rule. Common gates include **AND**, **OR**, and **NOT**. For example, an AND gate only outputs a 1 if both of its inputs are 1. These gates are used to perform all calculations and data manipulations.
* **Registers:** These are small, high-speed memory locations within the CPU (Central Processing Unit). They temporarily hold the binary data that the processor is currently working on. Think of a register as a small scratchpad for the CPU, allowing for quick access and manipulation of data as it's processed by the logic gates. Data is constantly moved in and out of registers during every operation.