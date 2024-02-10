#computing
[[Computing]]

# 7 HTML and CSS

# 7.0 Internet

The internet is a global system of interconnected computer networks.

## 7.0.1 TCP/IP

*not important*

## 7.0.2 World Wide Web

*not important*

## 7.0.3 Hypertext Transfer Protocol

> [!info] HTTP
> An application-layer protocol for transmitting hypermedia documents, such as HTML

- Made for communication between web browsers and web servers
- Follows client-server model where client opening a connection makes a request to the server and waits for a response

There are many types of HTTP requests but the two important ones are:
- `GET` → Used to request data only. (should not contain data within request)
- `POST` → Used to send data to the server

`index.html` is usually the default file sent to the client when a website address is first opened.

# 7.1 Hypertext Markup Language

> [!info] HTML
> A **markup language** that tells web browsers how to structure the web page

HTML consists of a series of elements that is used to wrap content

![[anatomy-of-an-html-element.png]]

The **attributes** extend an element, in order to change its behaviour or provide metadata.

Syntax for attributes: `name="value"`

## 7.1.1 Basic Structure of HTML document

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>Example</title>
	</head>
	<body>
		Example Body
	</body>
</html>
```

## 7.1.2 Basic Formatting Elements in HTML

- `<p>` paragraph
- `<b>` bold
- `<em>` italics
- `<a>` anchor element. Makes text it encloses into a hyperlink. Attributes:
	- `href` specifies web address for the link
	- `title` extra information about the link
	- `target` specifies where to open the linked document. 
- `<img>` image element. Attributes:
	- `src` path to the image
	- `alt` alternate text for the image (important for accessibility)
	- `width`/`height` determines the size of the image
- `<h1></h1>`...`<h6></h6>` headings, sizes 1 to 6, with 1 being the largest
- Special Characters
	- & → `&amp;`
	- < → `&lt;`
	- > → `&gt;`
	- " → `&quot;`
- `<!-- -->` wrap comments
- `<ul></ul>` Unordered List, with each item wrapped in `<li></li>`
- `<ol></ol>` Ordered List, with each item wrapped in `<li></li`
- Table
```html
<table>
	<tr>
		<th></th>
	</tr>
	<tr>
		<td></td>
	</tr>
</table>
```

## 7.1.3 Navigation Section Element

*not important*

# 7.2 Cascading Style Sheets

> [!info] CSS
> A declarative language that controls how websites look in the browser

```css
element {
	propertyName: value;
	/* comment */
	...
}
```

## 7.2.1 CSS Properties for A-Level

- `display`
- `background`
- `color`
- `font-family`
- `font-size`
- `font-style`
- `font-weight`
- `font-align`
- `font-decorration`
- Box Model (refer to 7.2.4)

Note:
- Some properties (like `border`) can take multiple values separated by whitespace
- American Spelling is used: `center`, `color`
- Units can be as follows:
	- `%` percentage of parent container
	- `px` pixels
	- `em` relative to font size of parent

CSS is can be added to your element in 3 ways:
- Inline - using `style` attribute
```html
<element style="property: value;" />
```
- Internal - using `<style>` element in `<head>`
```html
<style>
	element {
		property: value;
	}
</style>
```
- External - using an external `.css` file and importing it with `link`

**css**:
```css
element {
	property: value;
}
```
**html**:
```html
<link rel="stylesheet" href="file.css">
```

## 7.2.2 `div` Element

- The `div` element is a generic container for flow content.
- It has no effect on the content or layout until it is styled in some way by CSS

## 7.2.3 `id` and `class` attributes

A selector is a pattern of element and other terms that tell the browser which elements should be selected to have the CSS property values. 

There are 3 types of selector
- Type, i.e. the element type
- `class` attribute
- `id` attribute

To access the element with those selectors, the following syntax should be employed:
```html
<head>
	<style>
		element {
			property: value;
		}
		.class1 {
			property: value;
		}
		#id1 {
			property: value;
		}
	</style>
</head>
<body>
	<element class="class1" id="id1"></element>
<body>
```

## 7.2.4 CSS Box Model

The CSS Box Model is a box that wraps around every HTML element, it consists of:

- **Margins**: The CSS margin properties are used to create space around elements, outside of any defined borders
- **Borders**: CSS border properties allow you to specify the style, width and colour of an element's border
- **Padding**: CSS padding is used to create space around an element's content, inside of any defined borders.

![[box-model.png]]

# 7.3 Usability Principles in Web Applications

- 7.3.1 Visual Hierarchy
- 7.3.2 Consistency (Mental Models)
- 7.3.3 Affordance
- 7.3.4 Responsiveness

*Theres literally no further information about this in the notes*

# 7.4 Flexbox Layout Module

The Flexible Box Layout Module is used to make it easier to design a flexible responsive layout structure.

This can be achieved by adding `display: flex;` to the css

# 7.5 Web Forms

A web form is used to get inputs from the user and submitted to be processed by the web application.

| Elements                   | Attributes           | Values                                                           |
| -------------------------- | -------------------- | ---------------------------------------------------------------- |
| `<form>` `</form>`         | `action`             | URL to submit(identify the server)                               |
|                            | `method` (optional)  | `GET` or `POST`                                                  |
|                            | `enctype` (optional) | Upload a file using `multiplart/form-data`                       |
| `<input>`                  | `name`               | Similar to a variable name but different from `id`               |
|                            | `type`               | text, submit, file ( radio, checkbox, date,... )                 |
|                            | `value`              | Values that will be submitted. Use for specifying default values |
| `<textarea>` `</textarea>` | `name`               | Multi-line textbox                                               |
| `<label>` `</label>`       | `for`                | `id` of the input elements that the label refers to              |

![[web-form.png]]

- The `for` attribute of `<label>` must be equal to the `id` attribute of the related element to bind them together.
- `<label>` element also increases the hit area of the form element.

# 7.6 Web Server

## 7.6.1 Software, Server and Applications

- **Software** → set of instructions that make computer hardware usable.
- **Server** → a computer on a network that provides a resource to the other machines on the network.
- **Web Server** → accepts requests via HTTP, to distribute web pages.
- **Web Browser** → software that enables the access to the material requested from the web server.
- **Application** → set of instructions designed to make the computer do something for the user.
- **Web Application** → Application that runs on a web server
- **Native Application** → Application that is runs locally on a device's operating system
- **Web Framework** → Software framework (code library) that is designed to support the development of web applications and it provide a standard way to build and deploy web applications.

## 7.6.2 Flask

> [!info] Flask
> Flask is a web framework written in python

To install:
```
$ pip install flask
```

Flask version for A-levels is 0.12.2

**Basic Flask syntax**:

```python
from flask import Flask # import the Flask module

app = Flask(__name__) # create the Flask object

@app.route("/") # Decorator that denotes that it will respond to web requests for the '/' path
def index():
	return "hello, world!"
	# the text 'hello, world!' will be displayed on the browser

if __name__ == "__main__":
	app.run()
```

When this code is run, the webpage will be displayed at the url `http://127.0.0.1:5000` by default. The port number can be changed by specifying the `port` parameter in `app.run()`.

**Templates**:
In order to serve `.html` files to the client, we can use the `render_template` method.

```python
from flask import Flask, render_template # note the inclusion of the new method
...
@app.route("/")
def index():
	return render_template("index.html")
	# the .html file should be saved in the templates folder
...
```

The usual file hierarchy for flask apps is as follows:

```
|app.py
|templates
	|index.html
|static
	|image.jpg
	|index.css
```

The static folder can be accessed using the `url_for()` method from flask:
```python
from Flask import url_for

url_for('static', filename="name of file")
```

```html
<!--e.g.-->
<link rel="stylesheet" href="{{url_for('static', filename='index.css')}}" />
```

HTML response errors can be handled using the following decorator:
```python
@app.errorhandler(404)
def pagenotfound(e):
	return render_template('404.html'), 404
```

Examples of HTML responses include:
- `404 NOT FOUND`
- `403 FORBIDDEN`
- `410 GONE`
- `418 I'M A TEAPOT`
- `500 INTERNAL SERVER ERROR`

## 7.6.3* HTTP Methods GET and POST

- HTTP Methods `GET` and `POST` are used to send information to the server.
- Usually when you input a URL into your browser, it sends a `GET` request to request for the webpage.
- We can use parameters in our `GET` request to send information to the server. However this is not very secure as information is displayed in the URL.
- Instead, we can use a `POST` request to send data discretely to the server.
- We need the `request` object to do this with Flask:

```python
#app.py

from flask import Flask, render_template, request, redirect

@app.route("/", methods=["GET", "POST"])
def index():
	if request.method == "GET":
		return render_template('index.html')
	elif request.method == "POST":
		data = request.form.get('data')
		...
		return redirect('/')

if __name__ = "__main__":
	app.run(debug=True)
```

```html
<!--index.html-->

...
	<body>
		<form method="post" action="/">
		<input name="data" placeholder="data"/>
		<button type="submit">Submit</button>
	<body>
...
```

# 7.7 Jinja Expressions

Jinja is a web template engine.

Jinja supports the following:
- basic arithmetic and comparison operators
- inserting of variables → `{{ var }}`
- control structures `for` and `if` using:
	- `{% for element in iterable %}...{% endfor %}`
	- `{% if condition %} ...{% elif %}...{% else %}... {% endif %}`
- template inheritance via:
	- `{% extends NAME_OF_FILE.html %}` denotes that the html file is to be inserted into another html file
	- `{% block SOME_NAME %}...{% endblock %}`, `SOME_NAME` is usually `content`, `footer`

Pass variables into Jinja by specifying them when rendering:
```python
return render_template("index.html", var=value)
```

_Last edited 16/09/2023 by Joshua Lim NJC_