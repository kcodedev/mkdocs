# Secondary Storage

Secondary storage provides permanent storage that the CPU accesses indirectly:

## 💽 Magnetic Hard Disk

<iframe width="560" height="315" src="https://www.youtube.com/embed/wteUW2sL7bc" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

> How in the hell did anyone ever come up with this technology and then create it!? The engineering, timing, and precision required is staggering. Amazing video, thank you.


### Structure of a HDD

- A HDD has one or more **platters** made of aluminium coated with magnetised metal grains
- The platters/disks **rotate** around a central spindle at [high-speed](https://www.youtube.com/watch?v=3owqvmMf6No)
- **Read/write heads** are mounted on **actuator** arms and positioned over each platter surface
- Electronic circuits control the movement of the arm and heads
- The surface of the platter/disk is divided into concentric tracks, each divided into sectors
- The basic unit of storage is called a block, each block has data encoded as a magnetic pattern

### Reading and Writing

![Read Write Head](https://upload.wikimedia.org/wikipedia/commons/thumb/7/74/Hard_disk_read_write_head_and_data_connector.jpg/330px-Hard_disk_read_write_head_and_data_connector.jpg)

The read/write head is an **electromagnet** and is positioned very close to the disk surface (a few nanometres). 

When writing, a change in the current in the head produces a variation in the magnetic field on the disk, aligning magnetic grains to represent binary 1s (one magnetic direction) or 0s (opposite direction). 

When reading, a change in the magnetic field on the disk produces a variation in current through the head, allowing detection of the binary value based on the magnetic orientation.

### 1950s Hard Disk Drive

![old hdd](https://i.insider.com/4dfb8533ccd1d5cb200d0000?width=700&format=jpeg&auto=webp)

> This is a picture of an IBM hard drive being loaded onto an airplane in 1956. According to @HistoricalPics, which tweeted the picture, it's a 5 mega-byte drive, and it weighed more than 2,000 pounds.

## 💿 Optical Storage

<iframe width="560" height="315" src="https://www.youtube.com/embed/H-jxTzFrnpg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

💿 **Lasers** create **pits** (low areas) and **lands** (high areas) on the disc <br>
💿 The disc features a **reflective metal layer** for laser interaction <br>
💿 Data is read by detecting differences in **light reflection** <br>
💿 Pits and lands produce distinct reflections, encoded as **binary bits** (0s and 1s) <br>
💿 Examples: **CD**, **DVD**, **Blu-ray** <br>
💿 Tracks are typically **spiral**, but **DVD-RAM** uses **concentric tracks** for random access <br>

### Variants:

- **ROM** (read-only)<br>
- **R** (recordable once)<br>
- **RW** (rewritable)<br>
- **RAM** (random access rewritable) <br>


## ⚡Solid-State Storage (Flash Memory)

![ssd](https://upload.wikimedia.org/wikipedia/commons/thumb/7/75/Samsung_980_PRO_PCIe_4.0_NVMe_SSD_1TB-top_PNr%C2%B00915.jpg/960px-Samsung_980_PRO_PCIe_4.0_NVMe_SSD_1TB-top_PNr%C2%B00915.jpg)

## Key Information

⚡Solid state memory (aka flash memory) is a type of non-volatile memory that stores data in an array of memory cells <br>
⚡It can be volatile(RAM) or non-volatile(SSD) <br>
⚡It uses semiconductor technology and has no moving parts <br>
⚡Arrays of transistors act as memory cells <br>
⚡Most circuitry resembles that of a NAND logic gates <br>
⚡Data is “flashed” onto chips <br>
