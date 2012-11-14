[Back](https://github.com/digiti/styleguides)
# Ruby

### Indentation

```
Soft Tabs:      YES
Spaces per tab: 2
````

### Formatting

```
Class names:  CamelCase
Functions:    snake_case
Properties:   snake_case
Variables:    snake_case
Constants:    ALL_CAPS
```

**Try to keep lines of code to a maximum of 80-100 characters in width, but split them up where it makes sense.**  
An answer on StackOverflow summarizes the reason to do this pretty well:

> I think the practice of keeping code to 80 (or 79) columns was originally created to support people 
editing code on 80-column dumb terminals or on 80-column printouts. 
Those requirement have mostly gone away now, but there are still valid reasons to keep the 80 column rule:

>  * To avoid wrapping when copying code into email, web pages, and books.
>  * To view multiple source windows side-by-side or using a side-by-side diff viewer.
>  * To improve readability. Narrow code can be read quickly without having to scan your eyes from side to side.

> I think the last point is the most important. 
> Though displays have grown in size and resolution in the last few years, eyes haven't.