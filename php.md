[Back](https://github.com/digiti/styleguides)
# PHP

## File structure

A PHP file starts with `<?php` at the top, followed by empty line. The first level of PHP code is not indented.

```PHP
<?php

$foo = 'bar';
```

A PHP file does not have a closing PHP tag (`?>`). A block of PHP embedded in an HTML page however does.

```PHP
<?php

$foo = 'bar';

?>
<!DOCTYPE html>
<html>
```


## Quotes
Use single quotes where possible. Use double quotes when embedding variables in strings.
```PHP
$foo = 'bar';
$foo = "{$bar}";
$foo = "Let's not unnecessarily escape single quotes";
```


## Comments

Document your code with comments as much as possible, but don't be verbose. Use single or multiline comments where appropriate.

**Wrong:**
```PHP
// Checks if the form was posted
$form_was_posted = true;

/**
 * Checks if the form was posted
 */
function isFormPosted ()
{
	
}
```

**Right:**
```PHP
// Holds a unique hash for identifying the template
$template_hash = 'qs54kio4kds';

/**
 * Gets a list of users
 *
 * Returns an array of user objects, or false if no users
 * were found
 */
function getUsers ()
{
	
}
```


## Variable names

Variable names are written in lowercase, use underscores for spaces ( _snake case_ ) and **[correctly describe their meaning](http://37signals.com/svn/posts/3250-clarity-over-brevity-in-variable-and-method-names)**. Do **not** use [Hungarian notation](http://en.wikipedia.org/wiki/Hungarian_notation).

Variable declarations are followed by a space, an equals sign, a space, the variable value and a semicolon.

**WRONG:**
```PHP
$FOO = 'bar';
$txtTitle = 'My title';
$foo='bar';
$foo=bar
$thisIsAnotherVariable = 'test';
```

**RIGHT:**
```PHP
$foo = 'bar';
$foo = true;
$foo = array();
```


## Classes

Class names are written in camel case, and start with a capital letter. They are on a separate line, and the opening and closing curly braces are written on a separate line as well.

```PHP
class Users
{
	
}
```


## Functions

Function names are written in camel case. They are on a separate line, and the opening and closing curly braces are written on a separate line as well.

The parentheses which contain the function arguments are preceded by a single space. The arguments are separated with commas, with a space between each item.

It is preferred to initialize the parameters in the argument list.

Functions are **always** preceded by a comment describing their functionality.

```PHP
// Fetches a sorted list of users
function getUsers ($foo = 'test', $bar = true)
{
	
}
```