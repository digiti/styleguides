[Back](https://github.com/digiti/styleguides)
# HTML

## Conventions
1. Tags are written in lowercase, and are closed properly if you are using XHTML
2. Attributes are written in lowercase
3. Attribute values are written in lowercase (if applicable), are quoted with **double quotes**, and are repeated only when you are using XHTML (checked="checked")
4. Classes and ID's are written in lowercase, use underscores for spaces ( _snake case_ ) and **describe their meaning properly**
5. The common rules for writing valid, semantic and well-formed HTML always apply. Validation is however not a requirement, because it's sometimes near to impossible
6. Use XML formatting where possible (`<link />`, `<img />`,...)


## Indenting
Always indent HTML tags with a single tab, and follow the flow of the document. This also applies to HTML newsletters. It's not because we're writing for Outlook, that we have to write sloppy HTML.
```HTML
	<body>
		<div id="container">
			<header>
				<h1>Site title</h1>
			</header>
			<section>
				<article>
					<h1>My article</h1>
				</article>
			</section>
			<footer>
				<p>&copy; 2012</p>
			</footer>
		</div>
	</body>
```


## Documentation/commenting
Use comments for documentation appropriatly. Don't write verbose comments.

**WRONG:**
```HTML
<!-- This is the content div -->
<div id="content">

</div>
```

**RIGHT:**
```HTML
<!-- BEGIN CONTENT !-->
<div id="content">

</div>
<!-- END CONTENT -->
```

Use comments to mark the beginning and the end of large sections of HTML. This is very useful when creating areas in HTML newsletter templates.


## Including assets (CSS, JavaScript,...)

Use the `<link>` tag for including CSS files. It is proven to be faster then using @import. Don't put CSS in your `<head>` tag, unless it's necessary.

XHTML:
```HTML
<link rel="stylesheet" type="text/css" href="css/main.css" />
```

HTML5:
```HTML
<link href="css/main.css" rel="stylesheet" />
```

Use the `<script>`tag for including JavaScript files. It is encouraged to place JavaScript files at the bottom of the page, or use an AMD (eg. [RequireJS](http://requirejs.org/)).

XHTML:
```HTML
<script type="text/javascript" src="js/jquery.js"></script>
```

HTML5:
```HTML
<script src="js/jquery.js"></script>
```


## DOCTYPE

Use the DOCTYPE which is appropriate for the project you are working, but use the DOCTYPE consistenly throughout the project. Don't mix different DOCTYPE's.

### Websites and applications

```HTML
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
```

```HTML
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
	"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
```

```HTML
<!DOCTYPE html>
<html>
```

### HTML newsletters (eg. Pigeon)

```HTML
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
	"http://www.w3.org/TR/html4/loose.dtd">
<html>
```


## Encoding

Always define the **UTF-8** character set for your page. This also applies to HTML newsletters (eg. Pigeon).

XHTML:
```HTML
<meta http-equiv="content-type" content="text/html; charset=utf-8" />
```

HTML5:
```
<meta charset="utf-8" />
```


## Pigeon

Always define a DOCTYPE and UTF-8 character set!

```HTML
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
	"http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
	<meta http-equiv="content-type" content="text/html; charset=utf-8" />
```

Use XHTML closing tags for every element (eg. `<img />`).

Put CSS in the head tag, and avoid inline CSS as much as possible. Lay-out corrections are almost inevitable, and this makes it much easier to make adjustments later on.

**WRONG:**
```HTML
<h1 style="font-family: Verdana; font-size: 18px;"><span class="title"></span></h1>
```

**RIGHT:**
```HTML
<head>
<style type="text/css" media="all">
	h1 {
		font-family: Verdana, Geneva, sans-serif;
		font-size: 18px;
	}
</style>
</head>
<body>
	<h1><span class="title"></span></h1>
</body>
```

When centering a page, use a table with `align="center"`, not a `<center>` tag.

**WRONG:**
```HTML
<center>
<table>
</table>
</center>
```

**RIGHT:**
```HTML
<table align="center">
</table>
```

Set the dimensions of table cells as much as possible. This prevents awkward lay-out rendering.

```HTML
<td width="600" height="40"></td>
```

Avoid spacer GIF's or spaces (`&#160;`) for creating margins. If you set both the **width** and **height** of an empty table cell, it will create the correct space.

**WRONG:**
```HTML
<td><img src="spacer.gif" width="600" height="20" /></td>
<td>&#160;</td>
```

**RIGHT:**
```HTML
<td width="600" height="20"></td>
```