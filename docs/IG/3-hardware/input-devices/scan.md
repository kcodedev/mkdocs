# 🖨 **Scanners**
## 📚**LO:** To understand what scanners are and their functions👨‍🏫
### 🤷‍♀️ **What are scanners?**
A scanner is a device that can capture information from a physical perspective and converts it into digital data that the computer can manipulate or store. 
### 📂 **Types of scanners:**
There are two major types of scanners; 2D and 3D, but they are split into may minor segments. Here are some of the common types of scanners we use:
<details>
<summary> 🔽Click Here To See The Types Of Scanners🔽</summary>

#### **2D Scanners**:
1. **Flatbed Scanners**
    * 📘Description: A Flatbed Scanner works by inserting a document facedown on a glass surface, which is then illuminated with a light source. Afterwards, a series of  lens and mirrors capture the light, changing it into electrical signals with a component called a CIS(Contact Image Sensor).
    * 🙌Pros and Cons:
        * Advantages:
            * High resolution and image quality
            * Can scan thick materials like books
            * Reliable color accuracy
        * Disadvantages:
            * Not very portable
            * Relatively slow
    * 📕Common Uses: Digitizing documents, photos, or artwork; used in offices, schools, and graphic design.
2. **Sheet Fed Scanners**
    * 📘Description: A Sheet Fed Scanner works similarly to a Flatbed Scanner; utilising stationary sensors and a light sources to capture information as documents roll across the scanner head. Many also include an ADF(Automatic Document Feeders) to make continuous scanning easier.
    * 🙌Pros and Cons:
        * Advantages:
            * Fast and efficient for multi-page scanning.
            * Compact size.
            * Supports duplex (both sides) scanning.
        * Disadvantages:
            * Cannot scan books or fragile materials.
            * Risk of paper jams.
    * 📕Common Uses: Office environments, digital archiving, document management systems.
3. **HandHeld Scanners**
    * 📘Description: A HandHeld Scanner is basically a small scanner you can manually glide over a page or object. It works with LEDs illuminating the surface and a sensor array capturing information line by line. Some models have an optical motion sensor to track movement and speed variations
    * 🙌Pros and Cons:
        * Advantages:
            * Lightweight and portable.
            * Can scan surfaces that don’t fit inside flatbeds.
        * Disadvantages:
            * Image quality depends on steady hand movement.
            * Lower resolution compared to flatbed scanners.
    * 📕Common Uses: Barcodes, receipts, quick document capture, translation pens or library scanning.
#### **3D Scanners**:
1. **Laser Triangulation Scanner**
    * 📘Description: A Laser Triangulation Scanner is 3D scanner that projects a laser beam onto an object and measures the angle of reflection using a camera or sensor to determine the object’s exact shape and surface geometry. It then builds a full 3D model.
    * 🙌Pros and Cons:
        * Advantages:
            * High accuracy and resolution.
            * Works well for small to medium objects.
            * Captures fine surface details.
        * Disadvantages:
            * Sensitive to shiny or transparent surfaces (light reflection issues).
            * Requires controlled lighting conditions.
    * 📕Common Uses: Reverse engineering, quality control, cultural heritage scanning.
2. **Structured Light Scanner**
    * 📘Description: A Structured Light Scanner is a 3D scanner that projects a series of light patterns, such as stripes or grids, onto an object and uses cameras to observe how the patterns deform over the surface. By analyzing these distortions, the scanner calculates the depth and shape of the object, creating a precise 3D model.
    * 🙌Pros and Cons:
        * Advantages:
            * Very fast and accurate.
            * Safe (non-laser, often infrared light).
            * Works well for human faces and organic shapes.
        * Disadvantages:
            * Sensitive to ambient light.
            * Limited range (best for small objects or people).
    * 📕Common Uses: 3D face scanning, AR/VR applications, body measurement, animation.
3. **Time-of-Flight (ToF) Scanner**
    * 📘Description: A Time-of-Flight Scanner is a 3D scanner that measures the time it takes for a pulse of light or laser to travel to an object and reflect back to the sensor. By calculating this travel time, the scanner determines the distance to each point on the object’s surface and builds a detailed 3D depth map or model.
    * 🙌Pros and Cons:
        * Advantages:
            * Works for large environments.
            * Real-time scanning capability.
            * Works well outdoors.
        * Disadvantages:
            * Lower accuracy than triangulation for small objects.
            * Reflective surfaces can cause noise.
    * 📕Common Uses: LIDAR systems, robotics, autonomous vehicles, 3D cameras (like in phones), and Range Finders.
</details>

### 📀 **How do they work?**
In simple steps, here is how most 2D and 3D scanners work:
* **2D Scanners**
    1. A light source (usually LED or fluorescent) shines across the document.
    2. The light reflects off the surface and passes through mirrors and lenses.
    3. A sensor (either a CIS or a CCD) detects the reflected light.
    4. The sensor converts light intensity and color into electrical signals.
    5. These signals are processed and stored as a digital image on a computer.
* **3D Scanners**\
3D Scanners are slightly different compared to 2D Scanners. There are many variations to how they work:
    * Laser Triangulation:
A laser beam is projected onto the object. A camera captures the reflection and, using geometry, calculates the distance and surface shape.
    * Structured Light:
A projector shines patterned light (grids or stripes) onto the object. Cameras record how the pattern deforms, and software converts that distortion into 3D depth data.
    * Time of Flight (ToF):
The scanner emits light pulses and measures how long they take to bounce back. The distance to each point is calculated from the travel time of the light.
    * Photogrammetry:
Many photos are taken from different angles, and computer software reconstructs the 3D shape by analyzing overlapping features.

    There are many ways how 3D Scanners work, and this is just a bare minimum. Next, we will talk about the components needed for these Scanners 🔽
### **👩‍🔧 Components of Scanners**
| Component                     | Function                             | Found In |
| ----------------------------- | ------------------------------------ | -------- |
| Light Source                  | Illuminates the object/document      | 2D & 3D  |
| Optical System                | Focuses light onto sensor            | 2D & 3D  |
| Image Sensor (CCD/CIS/Camera) | Captures reflected light             | 2D & 3D  |
| ADC                           | Converts signals to digital data     | 2D       |
| Stepper Motor                 | Moves scanning head                  | 2D       |
| Glass Plate                   | Holds document                       | 2D       |
| Laser Projector               | Projects light for shape measurement | 3D       |
| Positioning System            | Moves scanner or object              | 3D       |
| Processor/Control Unit        | Coordinates operations               | 2D & 3D  |
| Software Interface            | Builds and processes digital model   | 3D       |

### **🧠 Dictionary**
**CCD** – Charge-Coupled Device: A high-quality image sensor that captures light and converts it into electrical signals.

**CIS** – Contact Image Sensor: A compact image sensor that captures light directly from the scanned surface.

**ADC** – Analog-to-Digital Converter: Converts analog light signals from the sensor into digital data for the computer.

**LIDAR** – Light Detection and Ranging: A laser-based system that measures distances by timing light pulses to build 3D maps.

**ToF** – Time of Flight: A method that calculates object distance by measuring the time it takes for light to bounce back.

**CAD** – Computer-Aided Design: Software used to design, modify, or analyze 3D models, often using scanned data.

**3D Point Cloud**: A collection of millions of points in 3D space representing the surface of a scanned object.

**Laser Triangulation**: A 3D scanning method that calculates distances by measuring angles between a laser and a camera.
#### 📃***Disclaimer & Credit***
Tables and some information was provided by ChatGPT, including some details from parts:
* Dictionary
* Components of Scanners
* How do they work

Note that not all information was provided and some research was conducted and written. The only section fully created by ChatGPT was the Components of Scanners section, made with provided information.