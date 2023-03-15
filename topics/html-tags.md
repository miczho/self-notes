# Hypertext Markup Language: Tags & Elements

![](../img/html-element.png)

## Block-level Elements

Starts on a *new line*.

```html
<address>       <article>       <aside>         <blockquote>    <canvas>        <dd>             <div>
<dl>            <dt>            <fieldset>      <figcaption>    <figure>        <footer>         <form>
<h1>-<h6>       <header>        <hr>            <li>            <main>          <nav>            <noscript>
<ol>            <p>             <pre>           <section>       <table>         <tfoot>          <ul>
<video>
```

## Inline Elements

Continues on the *same line*.

```html
<a>             <abbr>          <acronym>       <b>             <bdo>           <big>            <br>
<button>        <cite>          <code>          <dfn>           <em>            <i>              <img>
<input>         <kbd>           <label>         <map>           <object>        <output>         <q>
<samp>          <select>        <small>         <span>          <strong>        <sub>            <sup>
<textarea>      <time>          <tt>            <var>           <script>
```

## Tags

### Default Structure (html5):

```html
<!DOCTYPE html>
<html>
<head>
    <title> <!-- This is the browser tab name --> </title>
    <!-- Other stuff that has nothing to do with output -->
</head>
<body>
    <!-- Output stuff goes in here -->
</body>
</html>
```

### Headers

```html
<h1>Heading One</h1>
<h2>Heading Two</h2>
<h3>Heading Three</h3>
<h4>Heading Four</h4>
<h5>Heading Five</h5>
<h6>Heading Six</h6>
```

### Paragraphs

```html
<p>
    <!-- Text -->
    <a href="http://google.com" target="_blank">Link in new tab</a>
    <strong>Bold font</strong>
    <em>Italicized font</em>
</p>
```

### Lists

```html
<!-- Bullets -->
<ul>
    <li>List Item 1</li>
    <li>List Item 2</li>
    <li>List Item 3</li>
</ul>

<!-- Numbers -->
<ol>
    <li>List Item 1</li>
    <li>List Item 2</li>
    <li>List Item 3</li>
</ol>
```

### Tables

```html
<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Email</th>
            <th>Age</th>
        </tr>
    </thead>


    <tbody>
        <tr>
            <td>John Doe</td>
            <td>jdoe@something.com</td>
            <td>45</td>
        </tr>
        <tr>
            <td>Sara Williams</td>
            <td>sara@something.com</td>
            <td>25</td>
        </tr>
    </tbody>
</table>
```

### Forms

The layout of the form can be made, but the server stuff is done by programming.

```html
<form action="process.php" method="POST">
    <div>
        <label>Name</label>
        <input type="text" name="name" placeholder="Enter name">
    </div>

    <div>
        <label>Email</label>
        <input type="email" name="email">
    </div>

    <div>
        <label>Message</label>
        <textarea name="message"></textarea>
    </div>

    <div>
        <label>Gender</label>
        <select name="gender">
            <option value="male">Male</option>
            <option value="female">Female</option>
            <option value="other">Other</option>
        </select>
    </div>

    <div>
        <label>Age:</label>
        <input type="number" name="age" value="30">
    </div>

    <div>
        <label>Birthday:</label>
        <input type="date" name="birthday">
    </div>

    <input type="submit" name="submit" value="Submit">
</form>
```

### Buttons

```html
<button>Click Me</button>
```

### Images

### Quotes