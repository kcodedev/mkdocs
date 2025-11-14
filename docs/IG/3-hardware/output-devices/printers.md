# 🖨Printers

> Printers are output devices that create hard copies

<img src="https://i2.pickpik.com/photos/758/52/946/printer-print-printing-paperwork-preview.jpg" alt="Alt Text" width="300">
<img src="https://images.pexels.com/photos/19149826/pexels-photo-19149826/free-photo-of-a-modern-3d-printing-station-setup.jpeg" alt="Alt Text" width="300">


## How do printers "Understand" data?
Software on the computer converts documents into **dot patterns** for inkjet and laser printers, while slicing software transforms 3D models into **G-code** for 3D printers, before sending the data to the respective printers.

**Dot Pattern**
![Microscope ink](https://upload.wikimedia.org/wikipedia/commons/8/86/Microscope_ink_05.jpg)

## 💧 Inkjet printers

Inkjet printers are the most common type of printer due to its affordability, high-quality color printing, and versatility. They use liquid ink catridges using colours CMYK (Cyan, Magneta, Yellow and Black). Below is more on how they work. The printer turns the electronic data it recieved using its printer driver, which turns the file into a dot pattern (bitmap) that the printer can understand.

Steps:

1. The data from the document is sent to a printer driver.
2. A check is then made by the printer driver to make sure that the printer is available to print the data. For instance, it might check if the printer is busy, offline, out of ink, and so on and so on.
3. The data is then sent to the printer and it is stored temporarily in memory known as a printer buffer.
4. A sheet of paper is then given into the main body of the printer where a sensor then detects whether paper is available or not in the paper feed tray. If it is out of paper or the paper is jammed or if there is an error, then an error message is sent back to the computer with the problem the printer recieved.
5. As the sheet of paper is going through the printer, the print head moves from side to side across the paper, printing the text or image. The four ink colours provided are sprayed exact amounts to produce the required colour. 
6. At the end of each full pass of the print head, the paper is moved very slightly to allow the next line to be printed. This continues repeatedly until the whole page has been printed.
7. If there is more data in the printer buffer, the temporary data in the printer, then the whole process continues from Step 5 until the buffer is finally empty.
8. Once the printer buffer is has been emptied, the printer sends an interrupt, a signal from the printer, to the CPU in the computer, requesting for more data to be sent to the printer. This whole process then continues until the whole of the document has been fully printed.

<br>

## ☄️ Laser printers

<iframe width="560" height="315" src="https://www.youtube.com/embed/WB0HnXcW8qQ" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

Laser printers are a type of printer that uses a laser beam to produce high-quality text and images on paper. Laser printers are known for their speed, precision, and efficiency, making them ideal for offices and high-volume printing tasks. Below is more on how they work.

Steps:

1. Printer driver checks printer is online and ready for use
2. Data is sent to the printer and stored in the printer buffer (temporary memory)
3. Printing drum given a positive charge, as the drum spins a laser beam moves across it removing positive charge in certain areas, leaving negatively charged areas
4. Drum is coated with positively charged toner which will only stick to the negatively charged parts of the drum
5. Negatively charged sheet of paper is rolled over the drum
6. Toner on the drum sticks to the paper to produce the image
7. The paper goes through a fuser where heat melts the ink to permanently fix it to the paper
8. A discharge lamp removes all electric charge from the drum.




<br>


## ⚙️ 3D printers

![alt text](https://html.scirp.org/file/3-7702864x3.png?20230309164023106)

3D printers create three-dimensional objects from digital designs by building them layer by layer using materials like plastic, resin, or metal.

Steps:

1. The digital design (3D model) is created using CAD software and saved in formats like STL or OBJ.
2. The model is sliced into thin horizontal layers using slicing software, which generates G-code instructions that the printer can understand and execute.
3. Material (e.g., plastic filament, resin, or metal powder) is loaded into the printer.
4. The printer follows the G-code to deposit or solidify the material layer by layer, with each new layer fusing to the previous one, building the object from the bottom up.







