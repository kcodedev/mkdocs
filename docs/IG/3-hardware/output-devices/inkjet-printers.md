# 💧 Inkjet printers

<iframe width="560" height="315" src="https://www.youtube.com/embed/0PKFQciUWBU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

---

## Inkjet Printing Process

💻 The data from the document is sent to a **printer driver**.<br>
⚙️ The printer driver makes sure that the printer is available (not busy, offline, out of ink etc)<br>
📄 The data is then stored temporarily in memory known as a **printer buffer**.<br>
📜 A sheet of paper is then given into the main body of the printer.<br> 
💧 The **print head** moves from side to side across the paper, printing the text or image.<br>
🎨 The four ink colours provided are sprayed exact amounts to produce the required colour. <br>
💧 The paper is moved forward by the **stepper motor** to allow the next line to be printed. <br>
📜 This continues repeatedly until the whole page has been printed. <br>

---

## Thermal Bubble vs Piezoelectric

| Thermal Bubble | Piezoelectric |
|----------------|---------------|
| Tiny resistors create heat & vaporises ink to create a bubble. When the bubble pops the ink is forced onto the page. | There is a piezo crystal vibrates when it receives an electric charge. Ink is forced out of the nozzle by the vibration. |


<img src="https://www.researchgate.net/profile/Alessia-Sambri/publication/259426490/figure/fig2/AS:671526395338780@1537115777555/Principle-of-a-a-thermal-bubble-jet-print-head-and-b-a-piezoelectrically-actuated.png" alt="Inkjet Print Head Principle">