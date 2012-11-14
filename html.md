[Back](https://github.com/digiti/styleguides)
# HTML

## Conventions
1. Tags are written in lowercase, and are closed properly if you are using XHTML
2. Attributes are written in lowercase
3. Attribute values are written in lowercase (if applicable), are quoted with double quotes, and are repeated only when you are using XHTML (checked="checked")
4. Classes and ID's are written in lowercase, use underscores for spaces ( _snake case_ ) and describe their meaning properly
5. The common rules for writing valid, semantic and well-formed HTML always apply. Validation is however not a requirement, because it's sometimes near to impossible

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