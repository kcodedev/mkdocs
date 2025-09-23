# Memory Management

## Understanding Memory Management

Memory management is a critical OS function that allocates and deallocates memory space among various processes. It ensures efficient use of RAM and secondary storage, preventing conflicts and optimizing performance. Key techniques include virtual memory, paging, and segmentation.

## Virtual Memory

Virtual memory is a memory management technique that provides an "idealized abstraction of the storage resources that are actually available on a given machine" (Wikipedia). It allows processes to use more memory than physically available by using disk space as an extension of RAM.

- **Benefits**: Enables larger programs to run, improves multitasking, and provides memory protection.
- **Implementation**: Uses a combination of hardware and software to map virtual addresses to physical addresses.

## Paging

Paging divides physical memory into fixed-size blocks called frames and logical memory into blocks of the same size called pages. When a process needs memory, pages are loaded into available frames.

- **Page Table**: Maintains mappings between virtual pages and physical frames.
- **Advantages**: Eliminates external fragmentation, simplifies allocation.
- **Disadvantages**: Can lead to internal fragmentation if page size doesn't match process needs.

## Segmentation

Segmentation divides memory into variable-sized segments based on logical divisions of a program (e.g., code, data, stack). Each segment has its own base address and limit.

- **Segment Table**: Stores base address and length for each segment.
- **Advantages**: Reflects logical program structure, reduces internal fragmentation.
- **Disadvantages**: Can cause external fragmentation, more complex management.

## Differences Between Paging and Segmentation

| Aspect | Paging | Segmentation |
|--------|--------|--------------|
| Division | Fixed-size pages | Variable-size segments |
| Address Translation | Page number + offset | Segment number + offset |
| Fragmentation | Internal fragmentation possible | External fragmentation possible |
| Logical View | Flat address space | Structured address space |
| Complexity | Simpler implementation | More complex due to variable sizes |

## Page Replacement

When memory is full and a new page needs to be loaded, the OS must replace an existing page. Common algorithms include:

- **FIFO (First In, First Out)**: Replaces the oldest page. Simple but may not be optimal.
- **LRU (Least Recently Used)**: Replaces the page not used for the longest time. Better performance but requires tracking usage.
- **Optimal**: Replaces the page that will not be used for the longest time. Theoretical best but impractical to implement.

Page replacement aims to minimize page faults (when a required page is not in memory).

## Disk Thrashing

Disk thrashing occurs when the system spends more time swapping pages between RAM and disk than executing processes. This happens when:

- Too many processes compete for limited memory.
- The working set (pages actively used by a process) exceeds available RAM.
- Poor page replacement algorithms cause frequent faults.

Thrashing leads to severe performance degradation, as the CPU waits for I/O operations. Solutions include increasing RAM, reducing multiprogramming level, or using better scheduling algorithms.