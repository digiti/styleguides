# JavaScript

### Indentation

```
Soft Tabs: NO
```

### Formatting

```
Functions:    camelCase
Variables:    camelCase
Constants:    ALL_CAPS
```

### jQuery

When you reuse jQuery object a lot then it's best to cache it in a variable.  
Also prefix the variable with `$` to indicate that it is a jQuery object.

```javascript
// BAD
$('.container .click-here').click(function(e) { /* ... */ });
$('.container .some-form').submit(function(e) { /* ... */ });

// GOOD
var $container = $('.container');
$container.find('.click-here').click(function(e) { /* ... */ });
$container.find('.some-form').submit(function(e) { /* ... */ });
```



### Coding Tips

* Don't use function statements. Instead, create anonymous functions and
assing them to vars for consistency with other vars.

    ```javascript
    // No
    function doThing(a, b) {return a * b;}

    // Yes
    var doThing = function(a, b) {return a * b;}; 
    ```

* Avoid global vars where you can. If you use them, specify it explicitly.

    ```javascript
    window.globalVar = ...;
    ```

* Use one `var` per variable.

    ```javascript
    var a = 5;
    var b = 6;
    var $this = $(this);
    // Exception.
    var a, b, c, d, $this;
    ```

* Use '_this' variable to push current context to the closures.

    ```javascript
    var a = {
     b: function() {
       var _this = this;
       $(some).click(function(event) {
         _this.c();
       });
     }
    };
    ```

* Do not use quotes in object keys.

    ```javascript
    // No
    {'a': 'testtest'}

    // Yes
    {a: 'testtest'}
    ```

* Use '===' for comparing instead of '=='. JavaScript is weakly typed
language, so 5 == '5'. This ambiguity could lead to hard-to-find bugs.

    ```javascript
    if (a === 5) {
      ...
    }
    if ($(this).val() === 'something') {
      ...
    }
    if (typeof a === 'undefined') {
      ...
    }

    // Exception: this compares both to 'null' and 'undefined'.
    if (item == null) {
  
    }
    ```

* Cache list length into a variable. You could afford 2x loop performance
increase with this on some browsers.

    ```javascript
    for (var i = 0, length = someList.length; i < length; i++) {
      doSomething(someList[i]);
    }
    ```

* Avoid bitwise operators if possible.
* Avoid `with` & implied typecasting.