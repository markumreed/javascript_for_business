# HTML, CSS, and the DOM Tutorial

## Introduction

HTML (HyperText Markup Language) and CSS (Cascading Style Sheets) are the foundation of web development. HTML structures the content, while CSS styles it. The DOM (Document Object Model) allows JavaScript to interact with the HTML and CSS to create dynamic web pages. This tutorial will guide you through the basics of HTML, CSS, and DOM manipulation.

### Prerequisites
- Basic understanding of programming concepts

## 1. HTML Basics

HTML is the standard markup language used to create web pages. It consists of elements defined by tags.

### Step 1: HTML Document Structure

An HTML document has a specific structure. Create a new file named `index.html` and add the following code:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HTML, CSS, and DOM Tutorial</title>
</head>
<body>
    <h1>Welcome to HTML, CSS, and DOM Tutorial</h1>
    <p>This is a simple HTML document.</p>
</body>
</html>
```

**Discussion:**
1. **<!DOCTYPE html>**: Declares the document type and version of HTML.
2. **<html>**: Root element of an HTML document.
3. **<head>**: Contains meta-information about the document (e.g., title, character set).
4. **<body>**: Contains the content of the document, such as headings, paragraphs, images, links, etc.

### Step 2: Basic HTML Elements

Add more elements to `index.html`:

```html
<body>
    <h1>Welcome to HTML, CSS, and DOM Tutorial</h1>
    <p>This is a simple HTML document.</p>
    
    <h2>HTML Elements</h2>
    <ul>
        <li><strong>Heading:</strong> <h3>This is a heading</h3></li>
        <li><strong>Paragraph:</strong> <p>This is a paragraph.</p></li>
        <li><strong>Link:</strong> <a href="https://www.example.com">This is a link</a></li>
        <li><strong>Image:</strong> <img src="https://via.placeholder.com/150" alt="Placeholder Image"></li>
    </ul>
</body>
```

**Discussion:**
1. **<h1> to <h6>**: Defines HTML headings.
2. **<p>**: Defines a paragraph.
3. **<a>**: Defines a hyperlink.
4. **<img>**: Embeds an image.

## 2. CSS Basics

CSS is used to style and layout web pages. It can be applied inline, internally, or externally.

### Step 1: Inline CSS

Add inline styles directly to an HTML element:

```html
<h1 style="color: blue; text-align: center;">Welcome to HTML, CSS, and DOM Tutorial</h1>
```

### Step 2: Internal CSS

Add internal CSS within a `<style>` tag in the `<head>` section:

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HTML, CSS, and DOM Tutorial</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
        }
        h1 {
            color: blue;
            text-align: center;
        }
        p {
            color: #333;
        }
    </style>
</head>
```

### Step 3: External CSS

Create a new file named `styles.css` and add the following code:

```css
body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
}

h1 {
    color: blue;
    text-align: center;
}

p {
    color: #333;
}
```

Link the CSS file in `index.html`:

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HTML, CSS, and DOM Tutorial</title>
    <link rel="stylesheet" href="styles.css">
</head>
```

**Discussion:**
1. **Inline CSS**: Adds style directly to an element, useful for quick changes.
2. **Internal CSS**: Adds style within the `<head>` section, useful for single-page styles.
3. **External CSS**: Adds style through a separate CSS file, useful for multi-page styles.

## 3. DOM Manipulation with JavaScript

The DOM represents the HTML document as a tree structure where each node is an object representing a part of the document. JavaScript can interact with and manipulate the DOM to create dynamic content.

### Step 1: Adding JavaScript to HTML

Add a `<script>` tag before the closing `</body>` tag in `index.html`:

```html
<body>
    <!-- Existing content -->

    <script src="script.js"></script>
</body>
```

### Step 2: Basic DOM Manipulation

Create a new file named `script.js` and add the following code:

```javascript
// Change the text color of all paragraphs to green
const paragraphs = document.querySelectorAll('p');
paragraphs.forEach(p => p.style.color = 'green');

// Add a new list item to the unordered list
const ul = document.querySelector('ul');
const newItem = document.createElement('li');
newItem.innerHTML = '<strong>New Item:</strong> This is a new list item.';
ul.appendChild(newItem);

// Change the heading text
const heading = document.querySelector('h1');
heading.textContent = 'Welcome to DOM Manipulation Tutorial';
```

**Discussion:**
1. **Selecting Elements**: `document.querySelectorAll` selects all matching elements, and `document.querySelector` selects the first matching element.
2. **Changing Styles**: The `style` property allows changing the CSS properties of an element.
3. **Creating Elements**: `document.createElement` creates a new HTML element.
4. **Appending Elements**: `appendChild` adds a new child element to an existing element.
5. **Changing Content**: The `textContent` property changes the text content of an element.

## Conclusion

By following this tutorial, you've learned the basics of HTML, CSS, and DOM manipulation. You've created a simple HTML document, styled it with CSS, and added dynamic behavior using JavaScript. These skills form the foundation of web development and will allow you to create interactive and visually appealing web pages.

Happy coding!