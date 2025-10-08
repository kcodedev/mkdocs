# HTML & CSS Introduction Course

## Table of Contents
- [HTML Fundamentals](#html-fundamentals)
  - [Basic Structure and Elements](#basic-structure-and-elements)
  - [Headings, Paragraphs, and Lists](#headings-paragraphs-and-lists)
  - [Links and Images](#links-and-images)
  - [Forms and Inputs](#forms-and-inputs)
  - [Semantic HTML Elements](#semantic-html-elements)
- [CSS Fundamentals](#css-fundamentals)
  - [Selectors (Element, Class, ID)](#selectors-element-class-id)
  - [Box Model](#box-model)
  - [Colors and Backgrounds](#colors-and-backgrounds)
  - [Typography](#typography)
  - [Layout (Display, Position, Flexbox)](#layout-display-position-flexbox)
- [Practical Examples](#practical-examples)
  - [Complete Webpage Example](#complete-webpage-example)
  - [Styling Examples for Each Concept](#styling-examples-for-each-concept)
  - [Code Snippets to Copy and Modify](#code-snippets-to-copy-and-modify)
- [Best Practices](#best-practices)
  - [Clean, Readable Code Structure](#clean-readable-code-structure)
  - [Progressive Enhancement](#progressive-enhancement)
  - [Responsive Design Basics](#responsive-design-basics)

---

## HTML Fundamentals

### Basic Structure and Elements

HTML (HyperText Markup Language) is the standard markup language for creating web pages. It provides the basic structure of sites, which is later enhanced and modified by CSS and JavaScript.

**Basic HTML Document Structure:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Your Page Title</title>
</head>
<body>
    <!-- Your content goes here -->
</body>
</html>
```

**Key HTML Elements:**

- `<!DOCTYPE html>` - Declares the document type and version of HTML
- `<html>` - Root element that wraps all content
- `<head>` - Contains meta information about the document
- `<body>` - Contains the visible page content

### Headings, Paragraphs, and Lists

**Headings** create a hierarchical structure for your content:

```html
<h1>Main Title</h1>
<h2>Section Title</h2>
<h3>Subsection Title</h3>
<h4>Sub-subsection Title</h4>
<h5>Minor Heading</h5>
<h6>Smallest Heading</h6>
```

**Paragraphs** contain blocks of text:

```html
<p>This is a paragraph of text. It can contain multiple sentences and will be displayed as a block of content.</p>
<p>This is another paragraph, separate from the first one.</p>
```

**Lists** organize information:

**Unordered List (bullets):**
```html
<ul>
    <li>First item</li>
    <li>Second item</li>
    <li>Third item</li>
</ul>
```

**Ordered List (numbers):**
```html
<ol>
    <li>First step</li>
    <li>Second step</li>
    <li>Third step</li>
</ol>
```

### Links and Images

**Links** connect to other pages or resources:

```html
<!-- External link -->
<a href="https://www.example.com">Visit Example.com</a>

<!-- Internal link -->
<a href="about.html">About Us</a>

<!-- Link that opens in new tab -->
<a href="https://www.example.com" target="_blank" rel="noopener noreferrer">Open in New Tab</a>

<!-- Email link -->
<a href="mailto:contact@example.com">Send Email</a>
```

**Images** add visual content:

```html
<!-- Basic image -->
<img src="image.jpg" alt="Description of image">

<!-- Image with specific dimensions -->
<img src="image.jpg" alt="Description" width="300" height="200">

<!-- Responsive image -->
<img src="image.jpg" alt="Description" style="max-width: 100%; height: auto;">
```

### Forms and Inputs

**Forms** collect user input:

```html
<form action="/submit" method="post">
    <!-- Text input -->
    <label for="username">Username:</label>
    <input type="text" id="username" name="username" required>

    <!-- Email input -->
    <label for="email">Email:</label>
    <input type="email" id="email" name="email" required>

    <!-- Password input -->
    <label for="password">Password:</label>
    <input type="password" id="password" name="password" required>

    <!-- Radio buttons -->
    <fieldset>
        <legend>Choose your favorite color:</legend>
        <input type="radio" id="red" name="color" value="red">
        <label for="red">Red</label><br>
        <input type="radio" id="blue" name="color" value="blue">
        <label for="blue">Blue</label><br>
    </fieldset>

    <!-- Checkbox -->
    <input type="checkbox" id="newsletter" name="newsletter" value="yes">
    <label for="newsletter">Subscribe to newsletter</label><br>

    <!-- Select dropdown -->
    <label for="country">Country:</label>
    <select id="country" name="country">
        <option value="us">United States</option>
        <option value="ca">Canada</option>
        <option value="uk">United Kingdom</option>
    </select>

    <!-- Textarea -->
    <label for="message">Message:</label>
    <textarea id="message" name="message" rows="4" cols="50"></textarea>

    <!-- Submit button -->
    <button type="submit">Submit</button>
</form>
```

### Semantic HTML Elements

**Semantic elements** are HTML tags that clearly describe their meaning, purpose, and the type of content they contain, making web pages more accessible, understandable, and better structured for both humans and machines. The example below demonstrates common semantic elements including `<header>`, `<main>`, `<nav>`, `<article>`, `<aside>`, and `<footer>`:

```html
<!-- Header section -->
<header>
    <h1>Website Title</h1>
    <nav>
        <ul>
            <li><a href="/">Home</a></li>
            <li><a href="/about">About</a></li>
            <li><a href="/contact">Contact</a></li>
        </ul>
    </nav>
</header>

<!-- Main content area -->
<main>
    <article>
        <h2>Article Title</h2>
        <p>Article content goes here...</p>
    </article>

    <aside>
        <h3>Related Information</h3>
        <p>Sidebar content...</p>
    </aside>
</main>

<!-- Footer -->
<footer>
    <p>&copy; 2024 Your Website. All rights reserved.</p>
</footer>
```

---

## CSS Fundamentals

### Selectors (Element, Class, ID)

**CSS selectors** target HTML elements to apply styles:

```css
/* Element selector - targets all instances of an element */
p {
    color: blue;
    font-size: 16px;
}

/* Class selector - targets elements with a specific class */
.highlight {
    background-color: yellow;
    padding: 10px;
}

/* ID selector - targets a single element with a specific ID */
#header {
    background-color: #333;
    color: white;
}

/* Multiple selectors */
h1, h2, h3 {
    font-family: Arial, sans-serif;
}

/* Descendant selector */
article p {
    line-height: 1.6;
}

/* Pseudo-class selector */
a:hover {
    color: red;
}

button:disabled {
    opacity: 0.5;
    cursor: not-allowed;
}
```

### Box Model

**The CSS Box Model** describes the rectangular boxes generated for elements:

```css
.box {
    /* Content area */
    width: 200px;
    height: 100px;
    padding: 20px;        /* Space between content and border */
    border: 5px solid black;  /* Border around padding */
    margin: 10px;         /* Space outside the border */

    /* Total width = width + padding-left + padding-right + border-left + border-right + margin-left + margin-right */
    /* Total height = height + padding-top + padding-bottom + border-top + border-bottom + margin-top + margin-bottom */
}

/* Box-sizing can change how width and height are calculated */
.content-box {
    box-sizing: content-box; /* Default - width/height = content only */
}

.border-box {
    box-sizing: border-box;  /* Width/height includes padding and border */
}
```

### Colors and Backgrounds

**Color in CSS** can be specified in multiple ways:

```css
/* Named colors */
color: red;
background-color: blue;

/* Hexadecimal */
color: #ff0000;           /* Red */
background-color: #0000ff; /* Blue */

/* RGB */
color: rgb(255, 0, 0);    /* Red */
background-color: rgb(0, 0, 255); /* Blue */

/* RGBA (with transparency) */
color: rgba(255, 0, 0, 0.5); /* Semi-transparent red */

/* HSL */
color: hsl(0, 100%, 50%); /* Red */
background-color: hsl(240, 100%, 50%); /* Blue */

/* Background properties */
.background-example {
    background-color: lightgray;
    background-image: url('pattern.png');
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
    background-attachment: fixed;
}
```

### Typography

**Text styling** controls how text appears:

```css
/* Font properties */
body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    font-size: 16px;
    font-weight: normal; /* normal, bold, 100-900 */
    font-style: normal;  /* normal, italic, oblique */
    line-height: 1.5;    /* Space between lines */
    letter-spacing: 0.5px; /* Space between characters */
    word-spacing: 2px;   /* Space between words */
    text-align: left;    /* left, right, center, justify */
    text-decoration: none; /* none, underline, overline, line-through */
    text-transform: uppercase; /* none, uppercase, lowercase, capitalize */
    color: #333;
}

/* Web fonts */
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;700&display=swap');

.font-example {
    font-family: 'Roboto', sans-serif;
}
```

### Layout (Display, Position, Flexbox)

**Display property** controls how elements are rendered:

```css
/* Block elements take full width */
div {
    display: block;
}

/* Inline elements flow with text */
span {
    display: inline;
}

/* Inline-block elements flow with text but respect width/height */
.inline-block-example {
    display: inline-block;
    width: 100px;
    height: 50px;
}

/* None removes element from layout */
.hidden {
    display: none;
}
```

**Position property** controls element positioning:

```css
/* Static positioning (default) */
.static {
    position: static;
    top: 20px; /* Ignored */
}

/* Relative positioning */
.relative {
    position: relative;
    top: 20px;   /* Moves 20px down from normal position */
    left: 10px;  /* Moves 10px right from normal position */
}

/* Absolute positioning */
.absolute {
    position: absolute;
    top: 50px;   /* 50px from positioned ancestor or viewport */
    right: 0;    /* 0px from right edge */
}

/* Fixed positioning */
.fixed {
    position: fixed;
    top: 0;      /* Always at top of viewport */
    right: 0;    /* Always at right of viewport */
}

/* Sticky positioning */
.sticky {
    position: sticky;
    top: 0;      /* Sticks when scrolling reaches this point */
}
```

**Flexbox** provides powerful layout capabilities:

```css
/* Flex container */
.flex-container {
    display: flex;
    flex-direction: row;        /* row, row-reverse, column, column-reverse */
    flex-wrap: nowrap;          /* nowrap, wrap, wrap-reverse */
    justify-content: flex-start; /* flex-start, flex-end, center, space-between, space-around, space-evenly */
    align-items: stretch;       /* stretch, flex-start, flex-end, center, baseline */
    gap: 10px;                  /* Space between items */
}

/* Flex items */
.flex-item {
    flex: 1;           /* Grow to fill space */
    flex-shrink: 0;    /* Don't shrink */
    flex-basis: 200px; /* Base size */
    align-self: auto;  /* Override align-items for individual item */
}

/* Alternative shorthand */
.flex-item-short {
    flex: 1 0 200px;   /* flex-grow flex-shrink flex-basis */
}
```

---

## Practical Examples

### Complete Webpage Example

**HTML Structure:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Personal Website</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Welcome to My Website</h1>
        <nav>
            <ul>
                <li><a href="#home">Home</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#portfolio">Portfolio</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <section id="home">
            <h2>Home</h2>
            <p>Welcome to my personal website! I'm a web developer passionate about creating beautiful and functional websites.</p>
            <img src="hero-image.jpg" alt="Hero image" class="hero-image">
        </section>

        <section id="about">
            <h2>About Me</h2>
            <div class="about-content">
                <p>I started learning web development 3 years ago and have been creating websites ever since.</p>
                <p>My skills include HTML, CSS, JavaScript, and various frameworks.</p>
            </div>
        </section>

        <section id="portfolio">
            <h2>My Portfolio</h2>
            <div class="portfolio-grid">
                <div class="portfolio-item">
                    <h3>Project 1</h3>
                    <p>A responsive e-commerce website</p>
                    <a href="#" class="portfolio-link">View Project</a>
                </div>
                <div class="portfolio-item">
                    <h3>Project 2</h3>
                    <p>An interactive dashboard application</p>
                    <a href="#" class="portfolio-link">View Project</a>
                </div>
            </div>
        </section>

        <section id="contact">
            <h2>Contact Me</h2>
            <form class="contact-form">
                <div class="form-group">
                    <label for="name">Name:</label>
                    <input type="text" id="name" name="name" required>
                </div>
                <div class="form-group">
                    <label for="email">Email:</label>
                    <input type="email" id="email" name="email" required>
                </div>
                <div class="form-group">
                    <label for="message">Message:</label>
                    <textarea id="message" name="message" rows="5" required></textarea>
                </div>
                <button type="submit" class="submit-btn">Send Message</button>
            </form>
        </section>
    </main>

    <footer>
        <p>&copy; 2024 My Personal Website. All rights reserved.</p>
        <div class="social-links">
            <a href="#" aria-label="Twitter">🐦</a>
            <a href="#" aria-label="LinkedIn">💼</a>
            <a href="#" aria-label="GitHub">🐱</a>
        </div>
    </footer>
</body>
</html>
```

**CSS Styling:**

```css
/* Reset and base styles */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    line-height: 1.6;
    color: #333;
    background-color: #f5f5f5;
}

/* Header */
header {
    background-color: #2c3e50;
    color: white;
    padding: 1rem 0;
    position: sticky;
    top: 0;
    z-index: 100;
}

header h1 {
    text-align: center;
    margin-bottom: 1rem;
}

nav ul {
    display: flex;
    justify-content: center;
    list-style: none;
}

nav li {
    margin: 0 1rem;
}

nav a {
    color: white;
    text-decoration: none;
    padding: 0.5rem 1rem;
    border-radius: 4px;
    transition: background-color 0.3s;
}

nav a:hover {
    background-color: #34495e;
}

/* Main content */
main {
    max-width: 1200px;
    margin: 0 auto;
    padding: 2rem;
}

section {
    margin-bottom: 3rem;
    background-color: white;
    padding: 2rem;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

section h2 {
    color: #2c3e50;
    margin-bottom: 1rem;
    border-bottom: 2px solid #3498db;
    padding-bottom: 0.5rem;
}

/* Hero image */
.hero-image {
    max-width: 100%;
    height: auto;
    border-radius: 8px;
    margin-top: 1rem;
}

/* About section */
.about-content {
    display: flex;
    gap: 2rem;
}

.about-content p {
    flex: 1;
}

/* Portfolio grid */
.portfolio-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
}

.portfolio-item {
    border: 1px solid #ddd;
    padding: 1.5rem;
    border-radius: 8px;
    text-align: center;
    transition: transform 0.3s, box-shadow 0.3s;
}

.portfolio-item:hover {
    transform: translateY(-5px);
    box-shadow: 0 5px 20px rgba(0, 0, 0, 0.15);
}

.portfolio-link {
    display: inline-block;
    background-color: #3498db;
    color: white;
    padding: 0.5rem 1rem;
    text-decoration: none;
    border-radius: 4px;
    margin-top: 1rem;
    transition: background-color 0.3s;
}

.portfolio-link:hover {
    background-color: #2980b9;
}

/* Contact form */
.contact-form {
    max-width: 600px;
}

.form-group {
    margin-bottom: 1.5rem;
}

label {
    display: block;
    margin-bottom: 0.5rem;
    font-weight: bold;
    color: #2c3e50;
}

input[type="text"],
input[type="email"],
textarea {
    width: 100%;
    padding: 0.75rem;
    border: 2px solid #ddd;
    border-radius: 4px;
    font-size: 1rem;
    transition: border-color 0.3s;
}

input[type="text"]:focus,
input[type="email"]:focus,
textarea:focus {
    outline: none;
    border-color: #3498db;
}

.submit-btn {
    background-color: #2ecc71;
    color: white;
    padding: 0.75rem 2rem;
    border: none;
    border-radius: 4px;
    font-size: 1rem;
    cursor: pointer;
    transition: background-color 0.3s;
}

.submit-btn:hover {
    background-color: #27ae60;
}

/* Footer */
footer {
    background-color: #2c3e50;
    color: white;
    text-align: center;
    padding: 2rem 0;
    margin-top: 3rem;
}

.social-links {
    margin-top: 1rem;
}

.social-links a {
    color: white;
    text-decoration: none;
    margin: 0 0.5rem;
    font-size: 1.5rem;
    transition: transform 0.3s;
}

.social-links a:hover {
    transform: scale(1.2);
}

/* Responsive design */
@media (max-width: 768px) {
    nav ul {
        flex-direction: column;
        text-align: center;
    }

    nav li {
        margin: 0.5rem 0;
    }

    .about-content {
        flex-direction: column;
    }

    .portfolio-grid {
        grid-template-columns: 1fr;
    }
}
```

### Styling Examples for Each Concept {#styling-examples-for-each-concept}

**Button Styling Variations:**

```css
/* Basic button */
.btn-basic {
    background-color: #3498db;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 16px;
}

/* Hover effect */
.btn-basic:hover {
    background-color: #2980b9;
}

/* Gradient button */
.btn-gradient {
    background: linear-gradient(45deg, #3498db, #2ecc71);
    color: white;
    padding: 12px 24px;
    border: none;
    border-radius: 6px;
    cursor: pointer;
    font-size: 16px;
    transition: transform 0.3s;
}

.btn-gradient:hover {
    transform: translateY(-2px);
}

/* Outline button */
.btn-outline {
    background-color: transparent;
    color: #3498db;
    padding: 10px 20px;
    border: 2px solid #3498db;
    border-radius: 4px;
    cursor: pointer;
    font-size: 16px;
    transition: all 0.3s;
}

.btn-outline:hover {
    background-color: #3498db;
    color: white;
}
```

**Card Component Styling:**

```css
.card {
    background-color: white;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    overflow: hidden;
    transition: transform 0.3s, box-shadow 0.3s;
}

.card:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
}

.card-header {
    background-color: #2c3e50;
    color: white;
    padding: 1rem;
}

.card-body {
    padding: 1.5rem;
}

.card-footer {
    background-color: #f8f9fa;
    padding: 1rem;
    border-top: 1px solid #dee2e6;
}
```

### Code Snippets to Copy and Modify

**Navigation Bar:**

```html
<nav class="navbar">
    <div class="navbar-brand">
        <a href="/">MySite</a>
    </div>
    <ul class="navbar-nav">
        <li><a href="/">Home</a></li>
        <li><a href="/about">About</a></li>
        <li><a href="/services">Services</a></li>
        <li><a href="/contact">Contact</a></li>
    </ul>
</nav>
```

```css
.navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #2c3e50;
    padding: 1rem 2rem;
}

.navbar-brand a {
    color: white;
    text-decoration: none;
    font-size: 1.5rem;
    font-weight: bold;
}

.navbar-nav {
    display: flex;
    list-style: none;
}

.navbar-nav li {
    margin-left: 2rem;
}

.navbar-nav a {
    color: white;
    text-decoration: none;
    transition: color 0.3s;
}

.navbar-nav a:hover {
    color: #3498db;
}
```

**Responsive Grid Layout:**

```css
.grid-container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 2rem;
    padding: 2rem;
}

.grid-item {
    background-color: white;
    padding: 1.5rem;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    text-align: center;
}
```

**Modal/Dialog Box:**

```css
.modal {
    display: none;
    position: fixed;
    z-index: 1000;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
}

.modal-content {
    background-color: white;
    margin: 10% auto;
    padding: 2rem;
    border-radius: 8px;
    width: 80%;
    max-width: 500px;
    position: relative;
}

.close {
    position: absolute;
    top: 1rem;
    right: 1rem;
    font-size: 1.5rem;
    cursor: pointer;
}

.close:hover {
    opacity: 0.7;
}
```

---

## Best Practices

### Clean, Readable Code Structure

**HTML Best Practices:**

1. **Use semantic HTML elements** to clearly describe content
2. **Proper indentation** for nested elements
3. **Meaningful class and ID names** that describe purpose
4. **Alt attributes** for all images
5. **Proper heading hierarchy** (h1 → h2 → h3, don't skip levels)

**CSS Best Practices:**

1. **Organize CSS logically** (base styles → layout → components → utilities)
2. **Use consistent naming conventions** (BEM, kebab-case, camelCase)
3. **Group related properties** together
4. **Use CSS custom properties** (variables) for consistent values
5. **Comment complex sections** of code

**Example of well-structured CSS:**

```css
/* ===== CSS CUSTOM PROPERTIES (VARIABLES) ===== */
:root {
    --primary-color: #3498db;
    --secondary-color: #2ecc71;
    --text-color: #333;
    --background-color: #f5f5f5;
    --border-radius: 8px;
    --box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

/* ===== BASE STYLES ===== */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    line-height: 1.6;
    color: var(--text-color);
    background-color: var(--background-color);
}

/* ===== LAYOUT ===== */
.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 2rem;
}

.grid {
    display: grid;
    gap: 2rem;
}

/* ===== COMPONENTS ===== */
.card {
    background-color: white;
    border-radius: var(--border-radius);
    box-shadow: var(--box-shadow);
    padding: 2rem;
    transition: transform 0.3s, box-shadow 0.3s;
}

.card:hover {
    transform: translateY(-5px);
    box-shadow: 0 5px 20px rgba(0, 0, 0, 0.15);
}

.btn {
    display: inline-block;
    padding: 0.75rem 1.5rem;
    border: none;
    border-radius: var(--border-radius);
    background-color: var(--primary-color);
    color: white;
    text-decoration: none;
    cursor: pointer;
    transition: background-color 0.3s;
}

.btn:hover {
    background-color: #2980b9;
}

/* ===== UTILITIES ===== */
.text-center { text-align: center; }
.text-left { text-align: left; }
.text-right { text-align: right; }

.mb-1 { margin-bottom: 1rem; }
.mb-2 { margin-bottom: 2rem; }
.mb-3 { margin-bottom: 3rem; }

.visually-hidden {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    border: 0;
}
```

### Progressive Enhancement

**Progressive enhancement** is a strategy that starts with a basic, functional experience and then adds enhancements for capable browsers and devices.

**Implementation approach:**

1. **Start with semantic HTML** that works without CSS
2. **Add basic CSS** for visual enhancement
3. **Add advanced CSS** for layout and interactions
4. **Add JavaScript** for enhanced functionality

**Example progressive enhancement:**

```html
<!-- Basic HTML (works everywhere) -->
<a href="/contact">Contact Us</a>

<!-- Enhanced with ARIA (better accessibility) -->
<a href="/contact" aria-label="Contact our customer service team">Contact Us</a>
```

```css
/* Basic styling (works in all browsers) */
.contact-link {
    color: blue;
    text-decoration: underline;
}

/* Enhanced styling (modern browsers) */
@supports (display: grid) {
    .contact-link {
        display: inline-grid;
        grid-template-columns: 1fr auto;
        gap: 0.5rem;
        align-items: center;
    }

    .contact-link::after {
        content: '→';
        transition: transform 0.3s;
    }

    .contact-link:hover::after {
        transform: translateX(0.25rem);
    }
}
```

### Responsive Design Basics

**Responsive design** ensures websites work well on all devices and screen sizes.

**Key techniques:**

1. **Flexible Grid Systems** using percentages or grid/flexbox
2. **Flexible Images** that scale with their containers
3. **Media Queries** for different screen sizes
4. **Mobile-First Approach** starting with mobile styles

**Responsive CSS example:**

```css
/* Mobile-first approach */
/* Base styles for mobile */
.container {
    width: 100%;
    padding: 1rem;
}

.grid {
    display: block;
}

.grid-item {
    margin-bottom: 1rem;
}

/* Tablet styles */
@media (min-width: 768px) {
    .container {
        max-width: 750px;
        margin: 0 auto;
    }

    .grid {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 2rem;
    }

    .grid-item {
        margin-bottom: 0;
    }
}

/* Desktop styles */
@media (min-width: 1024px) {
    .container {
        max-width: 1200px;
    }

    .grid {
        grid-template-columns: repeat(3, 1fr);
    }
}

/* Large screens */
@media (min-width: 1440px) {
    .container {
        max-width: 1400px;
    }
}
```

**Responsive images:**

```css
/* Make images responsive */
img {
    max-width: 100%;
    height: auto;
}

/* Different images for different screen sizes */
.responsive-image {
    background-image: url('mobile-image.jpg');
    background-size: cover;
    background-position: center;
    height: 200px;
}

@media (min-width: 768px) {
    .responsive-image {
        background-image: url('desktop-image.jpg');
        height: 400px;
    }
}
```

**Viewport meta tag (essential for mobile):**

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```