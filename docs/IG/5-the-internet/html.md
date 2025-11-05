# Introduction to HTML

HTML (HyperText Markup Language) is the standard language used to create web pages. It provides the structure and presentation of content on the internet. This guide offers a basic introduction to HTML, focusing on its key concepts for beginners.

## Structure

HTML organizes web content into a structured format. The main elements include:

### Head

Contains metadata about the document, such as the title, character encoding, and links to external resources like stylesheets or scripts.

  ```html
  <head>
      <title>Page Title</title>
  </head>
  ```
### Body

Holds the main content of the web page that users see and interact with.

  ```html
  <body>
      <p>This is the body content.</p>
  </body>
  ```
### Table

Used to display data in rows and columns, making it easy to organize information like schedules or comparisons.

  ```html
  <table>
      <tr>
          <th>Name</th>
          <th>Age</th>
      </tr>
      <tr>
          <td>John</td>
          <td>25</td>
      </tr>
  </table>
  ```
### Heading

Defines the main titles or sections of a page, typically using tags like `<h1>` for the most important heading down to `<h6>` for subheadings.

  ```html
  <h1>Main Title</h1>
  ```
### Subheading

Smaller headings under main headings, helping to break down content into manageable sections.

  ```html
  <h2>Subheading</h2>
  ```
### Paragraph

Groups text into blocks, allowing for better readability and separation of ideas.

  ```html
  <p>This is a paragraph.</p>
  ```

## Presentation

Presentation in HTML controls how content looks visually. This is often enhanced with CSS (Cascading Style Sheets), but basic HTML tags can also influence appearance:

### Colour

Sets the color of text, backgrounds, or borders using names, hex codes, or RGB values.

  ```html
  <p style="color: red;">Red text</p>
  ```
### Font Size

Determines the size of text, from small to large, to emphasize importance or improve readability.

  ```html
  <p style="font-size: 24px;">Large font</p>
  ```
### Font Style

Changes the appearance of text, such as making it bold, italic, or underlined.

  ```html
  <p style="font-weight: bold;">Bold text</p>
  <p style="font-style: italic;">Italic text</p>
  ```
### Border Style

Defines the look of borders around elements, including solid, dashed, dotted, or none.

  ```html
  <div style="border: 2px dotted blue;">Dotted border</div>
  ```