[Back](https://github.com/digiti/styleguides)
# CSS

## File structure

A CSS file follows the flow of the page (or pages) it applies to. It starts with general styles (eg. reset, body, @font-face,...), and continues with the header, content and footer (if there are any), in that order.

Third-party styles (eg. plugin styles), are placed in the bottom of the CSS file, unless they apply to a distinct part of the page.

Each distinct part of the page is marked with a comment in caps, and is separated from other parts of the page with **2 line breaks**.

```CSS
/** COMMON **/
@import url('reset.css');

@font-face {
	font-family: Gotham;
	src: url('Gotham.otf');
} 

body {
}


/** HEADER **/
#header {
}


/** CONTENT **/
#content {
}


/** FOOTER **/
#footer {
}


/** PLUGIN **/
.plugin {
}
```


## File organization

Put all CSS styles in one file, except for reset.css and print.css.

Give the CSS file a logical name (eg. the name of a page or controller).

```
..
main.css
print.css
reset.css
```

CSS styles must be divided in several files if this helps make the structure more clear. An application or larger website will likely have a CSS file for every page.

```
..
application.css
entries.css
reset.css
todos.css
users.css
```

Don't divide the CSS in several files bases on lay-out properties (eg. typography.css, colors.css,...). Since CSS properties will be scattered among several files, it will makes it harder to perform updates in the future.


## Documentation/commenting

Document every specific fix or hack in your file, so other developers now why specific properties were applied.

But don't overdo it. There's no need to explain every property.

```CSS
/**
 * Multi-line comment
 * http://nicolasgallagher.com/micro-clearfix-hack/
 */
cf:before,
.cf:after {
  content: ' ';
	display: table;
}

/** Single-line comment **/
.cf {
	*zoom: 1;
}
```


## Names & capitalization
Class names and ID's are written in **lowercase**, with **spaces separated by hyphens**. HTML elements are also written in lowercase.

```CSS
body {
}

.box-content {
}

#featured-content {
}
```


## Rules

Related rules are **grouped**, and always follow the same structure. This enables every developer to easily find specific properties.

```CSS
#content {
	/** Everything that is related to positioning **/
	float: left;
	position: relative;
	display: block;
	overflow: auto;
	/** Margin/border/padding **/
	margin: 0 0 40px 0;
	margin-left: 20px;
	border: 1px solid #333;
	padding: 20px 10px;
	/** Width/height, min-width/min-height, combined on a single rule if possible **/
	width: 400px; height: 300px;
	min-width: 400px; min-height: 300px;
	/** Typography **/
	font-family: Verdana, Helvetica, 'Trebuchet MS', sans-serif;
	font-size: 12px;
	line-height: 18px;
	font-weight: bold;
	font-style: italic;
	text-transform: uppercase;
	text-decoration: underline;
	/** Colors/backgrounds **/
	color: #333;
	background: url('content.png') no-repeat 0 0;
	/** Transforms/transitions **/
	transform: rotate(20deg);
	transition: height 1s;
	/** Box styles **/
	box-shadow: 5px 5px 5px #333;
	border-radius: 4px;
}
```

A rule starts with the selector (multiple selectors are divided among multiple lines), followed by a space, the opening curly brace on the same line, the properties and values, and ends with a curly brace on the beginning of a new line.

```CSS
.box h1,
.box h1 a {
	color: #333;
}
```

Rules always stick to the left side of the CSS file, and **can not be indented**. They are grouped based on their containers. Rules are **separated by a single line**.

```CSS
.box {
	width: 400px;
}

.box h1 {
	font-size: 18px;
}

.box h1 a {
	color: #333;
}
```

Properties are indented with a single tab, followed by a colon, a space, the value of the property, and a closing semicolon.

```CSS
	color: #333;
```

Property values are written in shorthand where possible.

```CSS
	margin: 0 0 0 20px;
	color: #333;
	background: url('content.png') repeat-x 0 0;
```

If the value of the width or height is 0, do not specify units.

**WRONG:**
```CSS
	margin: 0px 0px 10px 0px;
```

**RIGHT:**
```CSS
	margin: 0 0 10px 0;
```


## CSS preprocessors
Depending on the project, [SASS](http://sass-lang.com/) with **SCSS syntax** can be used. The same style conventions listed here should be used for SASS as well.

## Pixels vs. Ems
Use px for font-size, because it offers absolute control over text. 
Additionally, unit-less line-height is preferred because it does not inherit a percentage value of its parent element, 
but instead is based on a multiplier of the font-size.

## Nesting
As a rule of thumb, don't nest further than 3 levels deep. If you find yourself going further, 
think about reorganizing your rules (either the specificity needed, or the layout of the nesting).
