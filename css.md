[Back](https://github.com/digiti/styleguides)
# CSS

### Editor configuration

```
Soft Tabs:      NO
Spaces per tab: 4
````

### File structure

A CSS file follows the flow of the page (or pages) it applies to. It starts with general styles (eg. reset, body,...), and continues with the header, content and footer (if there are any), in that order.

Third-party styles (eg. plugin styles), are placed in the bottom of the CSS file, unless they apply to a distinct part of the page.

Each distinct part of the page is marked with a comment in caps, and is separated from other parts of the page with **2 spaces**.

```CSS
/** COMMON **/
@import url('reset.css');

body {}


/** HEADER **/
#header {}


/** CONTENT **/
#content {}


/** FOOTER **/
#footer {}


/** PLUGIN **/
.plugin {}
```


### File organization

Put all CSS styles in one file, except for reset.css and print.css.

```
..
main.css
reset.css
print.css
```

CSS styles must be divided in several files if this helps make the structure more clear. An application or larger website will likely have a CSS file for every page.

```
..
reset.css
common.css
users.css
todos.css
entries.css
```

Don't divide the CSS in several files bases on lay-out properties (eg. typography.css, colors.css,...). Since CSS properties will be scattered among several files, this makes it harder to perform updates in the future.