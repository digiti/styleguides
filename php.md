[Back](https://github.com/digiti/styleguides)
# PHP

## File structure

A PHP file starts with `<?php` at the top, followed by empty line. The first level of PHP code is not indented. Every subsequent level however is properly indented.

```PHP
<?php

$foo = 'bar';

if ($foo == 'bar') {
	echo 'Seems legit!';
}
```

A PHP file does not have a closing PHP tag (`?>`). A block of PHP _embedded_ in an HTML page however does.

```PHP
<?php

$foo = 'bar';

?>
<!DOCTYPE html>
<html>
```

Related blocks of PHP are grouped. An empty rule seperates grouped PHP code.

```PHP
// Fetches the users from the database
$query = "SELECT * FROM users";
$result = mysql_query($query);

// Loops through the users
while ($row = mysql_fetch_assoc($row)) {
	
}
```

**Redundant whitespace is to be avoided at all times.**


## One statement per line

Write a single statement per line.

**Wrong:**
```PHP
$foo = 'bar'; $bar = 1;
```

**Right:**
```PHP
$foo = 'bar';
$bar = 1;
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

**Wrong:**
```PHP
$FOO = 'bar';
$txtTitle = 'My title';
$foo='bar';
$foo=bar
$thisIsAnotherVariable = 'test';
```

**Right:**
```PHP
$foo = 'bar';
$foo = true;
$foo = array();
```


## Classes

Class names are written in _camel case_, and start with a capital letter. They are on a separate line, and the opening and closing curly braces are written on a separate line as well.

```PHP
class Users
{
	
}
```


## Functions

Function names are written in _camel case_. They are on a separate line, and the opening and closing curly braces are written on a separate line as well.

The only exception to this rule are controller methods in CodeIgniter, since they are related to the URL. Controller methods in CodeIgniter follow the same rules as variable names ( _snake case_ ). 

The parentheses which contain the function arguments are preceded by a single space. The arguments are separated with commas, with a space between each item.

It is preferred to initialize the parameters in the argument list.

Functions are **always** preceded by a comment describing their functionality.

```PHP
// Fetches a sorted list of users
function getUsers ($foo = 'test', $bar = true)
{
	
}
```


## Constants

Constants are written in uppercase, with underscores for spaces. Constant names describe their meaning like variables.

**Wrong:**
```PHP
myConstant = 'test';
$MYCONSTANT = 'test';
$MY_CONSTANT = 'test';
```

**Right:**
```PHP
USER = 'Bert';
MY_CONSTANT = 'test';
```


## Arrays

When defining arrays, they must be properly indented, and have a single space between the key, equals sign and value. 
Values are aligned using spaces.  
Always but a comma a the end so that new values can be easily added through copy paste.

```PHP
$users = array(
	1 => 'Bert',
	2 => 'Maarten',
	3 => 'Bert',
);
```


## Logical statements

Logical statements start with **if**, **else** or **elseif**, are followed by a single space, the logical operator(s) between parentheses, a single space and the opening curly brace on the same line. The closing curly brace is on seperate line.

The logical operators are separated from variables and values by a single space.

The use of &&, || and != is preferred over AND, OR and NOT.

Use === and !== when comparing or expecting boolean values.

**Wrong:**
```PHP
if($test=='test') {
	
} else {

}

if ($test=='test')
{
	
}
else
{

}

if ($test == 'test') {
	
}
else {

}
```

**Right:**
```PHP
if ($test == 'test') {
	
} else {

}
```


## Switch statements

Switch statements start with **switch**, are followed by a single space, the variable between parentheses, a single space, and the opening curly brace on the same line.

Cases are indented, and a seperate line. The colon immediately follows after the case value. The closing curly brace is on a separate line.

Switch statements are preferred over extensive if/else statements.

```PHP
switch ($i) {
	case 0:
		echo 'The value is zero';
		break;
	case 1:
		echo 'The value is one';
		break;
	default:
		echo 'The value could not be defined.';
		break;
}
```


## Loops

Loops follow the same style as logical statements. Always describe the meaning of counters and other variables used in loops.

```PHP
foreach ($users as $user) {
	echo $user['first_name'];
}


$number_of_users = count($users);

for ($current_user = 0; $current_user < $number_of_users; $i++) {
	echo "Currently looping through user {$current_user}.";
}


while ($row = mysql_fetch_assoc($result)) {
	echo $row['id'];
}
```


## Working with databases

### Escaping values

Each value which comes from user input (eg. forms) is considered dirty, and must be escaped at all times using **[mysql_real_escape_string](http://php.net/manual/en/function.mysql-real-escape-string.php)**.

The only exception is when the current framework used handles this automatically (eg. CodeIgniter Active Record).

**addslashes** is to be avoided.

```PHP
$first_name = mysql_real_escape_string($_POST['first_name']);
```


### Table names

Use a **plural** table name in lowercase, with underscores for spaces. The table name describes it's content as descriptive as possible.

**Wrong:**
```PHP
user
USER
User
usersTable
```

**Right:**
```PHP
users
registrations
```

The name of an associative table (a table which contains the foreign keys of two tables) is a combination of the name of the first and second table name, in alphabetical order. The name of the foreign keys is their **singular** respective table name, followed by **_id** (eg. user_id, project_id).

**Wrong:**
```PHP
projecttags
project_tags
tagsprojects
tags_projects
```

**Right:**
```PHP
projects_tags
```

### Database fields

Database fields are written in lowercase, and use underscores for spaces ( _snake case_ ).

**Wrong:**
```PHP
ID
firstname
firstName
```

**Right:**
```PHP
id
first_name
```

Always use **utf8_general_ci** as the character set for database fields, unless the field is case-sensitive (eg. hashes). In that case **utf8_bin** must be used as the character set for the database field.

The order of the database fields is determined by their importance. Primary and foreign keys come first, followed by an optional hash, the other fields, and an optional created date and updated date come last.

**Wrong:**
```PHP
title
created_on
updated_on
hash
project_id
id
```

**Right:**
```PHP
id
project_id
hash
title
created_on
updated_on
```

**Indexes** are applied to fields that are often used (eg. hashes).

### Connection encoding

Always set the database connection encoding to **UTF-8**.

```PHP
mysql_set_charset('utf8', $db_handle);
```


## Embedding PHP in HTML

Use **shorthand** when PHP is embedded in an HTML page. This greatly improves readability.

**Wrong:**
```PHP
<?php if ($user_id == 4) { ?>
<h1>Hello Bert!</h1>
<?php } else { ?>
<h1>Hello stranger!</h1>
<?php } ?>

<?php foreach ($users as $user) { ?>
<h1>Hello <?php echo $user['first_name']; ?>
<?php } ?>
```

**Right:**
```PHP
<?php if ($user_id == 4): ?>
<h1>Hello Bert!</h1>
<?php else: ?>
<h1>Hello stranger!</h1>
<?php endif; ?>

<?php foreach ($users as $user): ?>
<h1>Hello <?php echo $user['first_name']; ?>
<?php endforeach; ?>
```

Avoid the nesting of HTML in PHP as much as possible.

**Wrong:**
```PHP
<?php

	if ($user_id == 4) {
		echo '<h1>Hello Bert!</h1>';
	} else {
		echo '<h1>Hello stranger!</h1>';
	}

?>

<?php

foreach ($users as $user) {
	echo "<h1>Hello {$user['first_name']}";
}

?>
```

**Right:**
```PHP
<?php if ($user_id == 4): ?>
<h1>Hello Bert!</h1>
<?php else: ?>
<h1>Hello stranger!</h1>
<?php endif; ?>

<?php foreach ($users as $user): ?>
<h1>Hello <?php echo $user['first_name']; ?>
<?php endforeach; ?>
```

The usage of **short open tags** is never allowed.

**Wrong:**
```PHP
<? echo $test; ?>
```

**Right:**
```PHP
<?php echo $test; ?>
```


## require/require_once/include/include_once

**require/require_once** and **include/include_once** are placed at the top of a document, and don't use parentheses.

```PHP
<?php

require 'config.php';
include 'functions.php';
```