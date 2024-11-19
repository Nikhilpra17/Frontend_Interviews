<h1>Understanding <script>, <script async>, and <script defer></h1>

In HTML, the <script> tag is used to include JavaScript files in your web page. However, the behavior of how and **when** the script is loaded and executed can vary depending on the attributes async and defer. Let's break it down step by step.


----
**1\. <script> (Default)**

-  **How it works**:

Without any attributes, the browser will:

1.  **Stop rendering** the HTML when it encounters the <script> tag.

2.  Fetch the script file.

3.  Execute the script immediately **before continuing to render the rest of the HTML**.


```ruby
<html>
  <head>
    <script src="script.js"></script>
  </head>
  <body>
    <h1>Hello World</h1>
  </body>
</html>

```

```
Parsing stops → Fetch script → Execute script → Resume parsing
```


----

**2\. <script async>**

-  **How it works**:

1.  The script is fetched in parallel (asynchronously) with the rest of the HTML.

2.  The script is executed **as soon as it is downloaded**, potentially before the HTML is fully parsed.

-  **When to use**:

Use this when the script is **independent** of the HTML (e.g., analytics scripts or advertisements) and doesn't rely on DOM elements.



```ruby
<html>
  <head>
    <script async src="analytics.js"></script>
  </head>
  <body>
    <h1>Hello World</h1>
  </body>
</html>
```

```
Fetch HTML and script in parallel → Execute script as soon as it loads
```
----

**3\. <script defer>**

-  **How it works**:

1.  The script is fetched in parallel (like async).

2.  The script is executed **only after the HTML is fully parsed**.

-  **When to use**:

Use this for scripts that depend on the complete DOM structure (e.g., manipulating or interacting with HTML elements).

-  **Upside**:

Scripts are executed in the order they appear in the document, ensuring proper dependencies.


```ruby
<html>
  <head>
    <script defer src="dom-helper.js"></script>
    <script defer src="main.js"></script>
  </head>
  <body>
    <h1>Hello World</h1>
  </body>
</html>
```

```
Fetch HTML and script in parallel → Parse HTML completely → Execute script
```
