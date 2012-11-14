[Back](https://github.com/digiti/styleguides)
# CSS

### Indentation

```
Soft Tabs:      NO
Spaces per tab: 4
````

### File structure

A CSS file follows the flow of the page (or pages) it applies to.

It starts with general styles (eg. reset, body,...), continues with the header, content and footer, in that order.

Third-party styles (eg. plugin styles), are placed in the bottom of the CSS file.

Each distinct part of the page marked with a comment in caps.

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


### File organisation

