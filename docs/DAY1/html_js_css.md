## 1. Learning Outcomes

#### 1.1 Understanding Reactivity in a Web App
   - **Explanation:**
     - Define reactivity in the context of a web application.
     - Discuss the concept of data-binding and how it enables automatic UI updates.
     - Explore the reactivity system in VueJS, including the reactivity caveats.

   - **Activities:**
     - Create a simple Vue component to demonstrate reactivity.
     - Modify data properties and observe how the UI updates reactively.

#### 1.2 Ability to develop a frontend application using HTML, CSS, JavaScript
   - **Explanation:**
     - Emphasize the role of VueJS as a progressive framework, allowing integration into existing projects.
     - Discuss the HTML template syntax, styling with CSS, and enhancing functionality with JavaScript within Vue components.

   - **Activities:**
     - Build a basic VueJS application incorporating HTML, CSS, and JavaScript.
     - Customize the styling of components using scoped CSS.

#### 1.3 Understanding how routing works, and how to use it
   - **Explanation:**
     - Introduce Vue Router and its significance in single-page applications.
     - Explain the concept of routing, navigation guards, and nested routes.

   - **Activities:**
     - Set up Vue Router in a project.
     - Create multiple pages and link them using router links.
     - Implement navigation guards for authentication or data validation.

#### 1.4 Making API Requests with Fetch API (replacing state management)
   - **Explanation:**
     - Introduce the Fetch API for making asynchronous HTTP requests.
     - Discuss the basics of making GET, POST, and other types of requests.
     - Explain how to handle responses and errors.

   - **Activities:**
     - Integrate the Fetch API into a VueJS application to retrieve data from a mock API.
     - Implement data binding to display the fetched data in the UI.

### General Tips for Day 1 Facilitation:

- **Hands-On Exercises:** Continue to incorporate hands-on exercises for each learning outcome, focusing on using the Fetch API.

- **Real-world Examples:** Utilize real-world examples to illustrate the practical applications of VueJS and API integration.

- **Peer Collaboration:** Encourage participants to collaborate and discuss their solutions during the activities.

- **Q&A Sessions:** Allocate time for questions and answers to address any confusion or concerns related to API integration.

- **Resources for Further Learning:** Provide additional resources and references for participants interested in diving deeper into VueJS and API interactions.

- **Feedback Loop:** Maintain a feedback loop for participants to share their thoughts on the learning materials and session structure.

# HTML And CSS Refresher

## HTML

### What is HTML?

HTML stands for HyperText Markup Language. It is the standard markup language for creating web pages. It describes the structure of a web page. 
HTML consists of a series of elements, which are the building blocks of HTML pages. 

HTML elements are represented by tags. HTML tags label pieces of content such as "heading", "paragraph", "table", and so on. Browsers do not display the HTML tags, but use them to render the content of the page.

Type this into a text-editor and save this as .html

```html
<!DOCTYPE html>
<html>
<head>
<title>Page Title</title>
     
</head>
<body>
<h1>This is a Heading</h1>
<p>This is a paragraph.</p>
</body>
</html> 
```



Html texts are display from top to bottom. The first line is the doctype, which tells the browser what type of document it is. The second line is the html tag, which tells the browser that this is an html document. The third line is the head tag, which contains the title of the page. The fourth line is the body tag, which contains the content of the page. The fifth line is the h1 tag, which is a heading. The sixth line is the p tag, which is a paragraph.

### HTML Tags (the important ones)

#### Headings

Headings are defined with the h1 to h6 tags. h1 defines the most important heading. h6 defines the least important heading.

```html

<h1>This is heading 1</h1>
<h2>This is heading 2</h2>
<h3>This is heading 3</h3>

```
<h1>This is heading 1</h1>
<h2>This is heading 2</h2>
<h3>This is heading 3</h3>

### Headers, Paragraphs, and Lists

a standard html website has a header, a footer, and a main content. The header contains the title of the page, and the navigation bar. The footer contains the contact information, and the social media links. The main content contains the main content of the page.

```html

<header>
  <h1>Company Name</h1>
  <nav>
    <a href="#">Home</a>
    <a href="#">About</a>
    <a href="#">Contact</a>
  </nav>
</header>

<main>
  <h1>Page Title</h1>
  <p>Page content goes here.</p>
</main>

<footer>
  <p>Company Name</p>
  <p>123 Street Name</p>
  <p>City, State, Country</p>
</footer>

```
<header>
  <h1>Company Name</h1>
  <nav>
    <a href="#">Home</a>
    <a href="#">About</a>
    <a href="#">Contact</a>
  </nav>
</header>

<main>
  <h1>Page Title</h1>
  <p>Page content goes here.</p>
</main>

<footer>
  <p>Company Name</p>
  <p>123 Street Name</p>
  <p>City, State, Country</p>
</footer>

### Lists

There are two types of list in html, ordered lists and unordered lists. Ordered lists are numbered lists, while unordered lists are bulleted lists.

```html

<ul>
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ul>

<ol>
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ol>

```
<ul>
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ul>

<ol>
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ol>

### HTML Attributes
_(I copied this from Mozilla Developer Network)_

Elements in HTML have **attributes** 

These are additional values that configure the elements or adjust their behavior in various ways to meet the criteria the users want.

The most common attributes are :

| Attribute Name<br> | Elements                                                                                   | Description<br>                                                                                 |
| ------------------ | ------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------- |
| `id`               | Global Attribute                                                                           | Often used with CSS to style a specific element. The value of this attribute must be unique.    |
| `class`            | Global attribute                                                                           | Often used with CSS to style elements with common properties.                                   |
| `style`            | Global attribute                                                                           | Defines CSS styles which will override styles previously set.                                   |
| `hidden`           | Global attribute                                                                           | Prevents rendering of given element, while keeping child elements, e.g. script elements, active |
| `disabled`         | `<button>`,`<fieldset>`,`<input>`,`<optgroup>`,`<option>`,`<select>`,`<textarea>`          | Indicates whether the user can interact with the element.                                       |
| `src`              | `<audio>`,`<embed>`,`<iframe>`,`<img>`,`<input>`,`<script>`,`<source>`,`<track>`,`<video>` | The URL of the embeddable content                                                               |
| `href`             | `<a>`, `<area>`, `<base>`, `<link>`                                                        | The URL of a linked resource.                                                                   |


### Links

Links are defined with the `<a>` (anchor) tag. The `*href*` attribute specifies the URL of the page the link goes to.

```html

<a href="www.google.com" target="_blank">Click Me</a>
```

<a href="www.google.com" target="_blank">Click Me</a>

The target attribute specifies where to open the linked document. The *target="_blank"* attribute specifies to open the linked document in a new tab.

### Images

Images are defined with the *img* tag. The *src* attribute specifies the URL of the image.

```html

<img src="image.jpg" alt="Image">

```
<img src="image.jpg" alt="Image">

### Tables

Tables are defined with the *table* tag. The *tr* tag defines a row in the table. The *td* tag defines a cell in the table. The *th* tag defines a header cell in the table.

```html
<table>
    <tr>
        <th>Firstname</th>
        <th>Lastname</th>
        <th>Age</th>
    </tr>
    <tr>
        <td>Jill</td>
        <td>Smith</td>
        <td>50</td>
    </tr>
    <tr>
        <td>Eve</td>
        <td>Jackson</td>
        <td>94</td>
    </tr>
</table>

```

<table>
    <tr>
        <th>Firstname</th>
        <th>Lastname</th>
        <th>Age</th>
    </tr>
    <tr>
        <td>Jill</td>
        <td>Smith</td>
        <td>50</td>
    </tr>
    <tr>
        <td>Eve</td>
        <td>Jackson</td>
        <td>94</td>
    </tr>
</table>

### Forms

Standard HTML forms are defined with the *form* tag. The *input* tag defines an input field where the user can enter data. The *label* tag defines a label for an input field. The *textarea* tag defines a multi-line input field. The *select* tag defines a drop-down list. The *option* tag defines an option in a drop-down list. The *button* tag defines a clickable button.

```html

<form>
    <label for="fname">First name:</label><br>
    <input type="text" id="fname" name="fname"><br>
    <label for="lname">Last name:</label><br>
    <input type="text" id="lname" name="lname">
    <input type="submit" value="Submit Form">
</form>

```
<form>
    <label for="fname">First name:</label><br>
    <input type="text" id="fname" name="fname"><br>
    <label for="lname">Last name:</label><br>
    <input type="text" id="lname" name="lname">
    <input type="submit" value="Submit Form">
</form>

### Events

Think of events like things that "happen" while your program is running - similar to events in real life. Just like how you might react when your phone rings (the event) by answering it (your response), computer programs can react to different events.

You can program what to do as an event happens.

Here are some common examples:

Mouse events:
1. Clicking a button
2. Moving the mouse cursor
3. Double-clicking

Keyboard events:
1. Pressing a key
2. Releasing a key
3. Typing a character


Form events:

1. Submitting a form
2. Selecting from a dropdown menu
3. Checking a checkbox

Window events:

1. Loading a webpage
2. Resizing the browser window
3. Scrolling up or down

Here's a  table of common HTML events:

| Event | Description | Example Use Case |
|-------|-------------|-----------------|
| `onclick` | Triggered when element is clicked | Button click actions |
| `onsubmit` | Triggered when a form is submitted | Form validation before sending |
| `onchange` | Triggered when input value changes | Update UI when dropdown selection changes |
| `onmouseover` | Triggered when mouse hovers over element | Show tooltips or highlight items |
| `onmouseout` | Triggered when mouse leaves element | Remove highlights or hide tooltips |
| `onkeydown` | Triggered when keyboard key is pressed | Keyboard shortcuts |
| `onkeyup` | Triggered when keyboard key is released | Form validation as user types |
| `onload` | Triggered when page or image finishes loading | Initialize page components |
| `onfocus` | Triggered when element receives focus | Highlight input field |
| `onblur` | Triggered when element loses focus | Validate input field |
| `ondblclick` | Triggered on double click | Open editor or expand item |
| `oninput` | Triggered immediately when input value changes | Real-time search filtering |
| `onscroll` | Triggered when scrolling | Infinite scroll or sticky headers |
| `onresize` | Triggered when window is resized | Responsive layout adjustments |
| `ondrag` | Triggered when element is dragged | Drag and drop interfaces |
| `ontouchstart` | Triggered when touch screen is first touched | Mobile interface interactions |

#### Sample implementation in JavaScript
```html
<!-- Key events -->
<input type="text" 
        placeholder="Press keys here..."
        onkeydown="document.getElementById('keyPress').textContent = 'Key pressed: ' + event.key">
<p id="keyPress"></p>
```

## CSS

Cascading Style Sheets (CSS) is a style sheet language used for describing the presentation of a document written in a markup language such as HTML. CSS is a cornerstone technology of the World Wide Web, alongside HTML and JavaScript.

Create a file called style.css and save it in the same folder as your html file. Add this code to your html file

```css

body {
  background-color: lightblue;
}

h1 {
  color: white;
  text-align: center;
}

```

```html
<head>
     <link rel="stylesheet" href="style.css">
</head>
<body>
        <h1>Hello World</h1>
</body>

```

### Inline styles

You can also put styles directly in your html file. This is called inline styles. Add this code to your html file

```html
<body style="background-color:lightblue;">
        <h1 style="color:white;text-align:center;">Hello World</h1>
</body>
```

### CSS Selectors

CSS selectors are used to "find" (or select) the HTML elements you want to style. We can divide CSS selectors into five categories: simple selectors, pseudo-class selectors, attribute selectors, pseudo-element selectors, and combinators.

#### Simple Selectors

Simple selectors select elements based on name, id, class, attribute, and pseudo-class.

```css

/* Selects all <p> elements */
p {
  text-align: center;
  color: red;
}

/* Selects the element with id="demo" */

#demo {
  text-align: center;
  color: red;
}

/* Selects all elements with class="intro" */

.intro {
  text-align: center;
  color: red;
}

/* Selects all <a> elements with a target attribute */

a[target] {
  background-color: yellow;
}

/* Selects all <a> elements with a target="_blank" attribute */

a[target="_blank"] {
  background-color: yellow;
}

/* Selects every <p> element that is the first child of its parent */

p:first-child {
  color: red;
}

/* Selects every <p> element that is the last child of its parent */

p:last-child {
  color: red;
}

/* Selects every <p> element that is the first <p> element of its parent */

p:nth-child(1) {
  color: red;
}

/* Selects every <p> element that is the second <p> element of its parent */

p:nth-child(2) {
  color: red;
}

/* Selects every <p> element that is the last <p> element of its parent */

p:nth-child(3) {
  color: red;
}

/* Selects every <p> element that is the second child of its parent */

p:nth-of-type(2) {
  color: red;
}

/* Selects every <p> element that is the last child of its parent */

p:last-of-type {
  color: red;
}

/* Selects every <p> element that is the only child of its parent */

p:only-child {
  color: red;
}

/* Selects every <p> element that is the only <p> element of its parent */

p:only-of-type {
  color: red;
}

/* Selects every <p> element that is the first <p> element of its parent, if <p> is the first child of its parent */

p:first-child:first-of-type {
  color: red;
}

```

And many more. CSS is a very powerful tool for styling your web pages. And can be very difficult to understand at first. But with practice, you will be able to master it.

#### Tailwind CSS

Tailwind CSS is a utility-first CSS framework for rapidly building custom user interfaces. It is a highly customizable, low-level CSS framework that gives you all of the building blocks you need to build bespoke designs without any annoying opinionated styles you have to fight to override.

Tailwind CSS is a great tool to have in your web development arsenal as it allows you to build beatiful and responsive websites in a short amount of time.

For this workshop, we will be using Tailwind CSS generously. You can learn more about Tailwind CSS at https://tailwindcss.com/