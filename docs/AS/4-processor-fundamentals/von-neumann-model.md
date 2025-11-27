# Von Neumann Model

![ENIAC](https://upload.wikimedia.org/wikipedia/commons/thumb/a/aa/Reprogramming_ENIAC.png/960px-Reprogramming_ENIAC.png)
>The ENIAC completed in 1945. Operators had to manually rewire the machine using plugboards, set thousands of switches, and adjust patch cables to connect different components in order to change the program. This made programming extremely time-consuming.

## Before Von Neumann:

- **Hardwired Computers**: Computers were built with specific hardware for each task
- **No Separation of Data and Instructions**: Data and instructions were physically separate
- **No Memory**: No memory to store programs or data
- **No Program Counter**: No way to keep track of the next instruction to execute

## After Von Neumann

The Von Neumann architecture is the fundamental model for modern computer systems, named after mathematician and physicist John von Neumann.

![Von Neumann Architecture](https://upload.wikimedia.org/wikipedia/commons/thumb/8/88/CPT-Von_neumann_architecture.svg/960px-CPT-Von_neumann_architecture.svg.png)

The model consists of five main components:

- **Central Processing Unit (CPU)**: Executes instructions and performs calculations
- **Memory (RAM)**: Stores both data and instructions
- **Input Devices**: Allow data entry into the system
- **Output Devices**: Display or output processed information
- **Control Unit**: Coordinates the flow of data between components

## Stored Program Concept

The stored program concept means that:

- Both instructions and data are stored in the same memory
- Instructions are fetched from memory and executed sequentially
- Programs can be modified by changing the contents of memory
- The same hardware can run different programs by loading different instruction sets

### Examples of Stored Program Concept

- **Photo Editing Software**: The software (program/instructions) is stored in memory, and the photos (data) are also stored in the same memory. The CPU executes the instructions to manipulate the data, such as applying filters, cropping, or adjusting brightness.
- **Integrated Development Environment (IDE)**: The IDE software (program/instructions) is stored in memory, and the source code files (data) being edited are also stored in memory. The CPU executes the IDE's instructions to process and modify the code data, such as syntax highlighting, compiling, or debugging.

## Key Principles

- **Sequential Execution**: Instructions are executed one after another
- **Unified Memory**: Single memory space for both programs and data
- **Program Counter**: Keeps track of the next instruction to execute
- **Modifiability**: Programs can be changed without hardware modifications
