[Back](https://github.com/digiti/styleguides)
# Ruby

##Line length
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


##Variables

Variable names are written in lowercase, use underscores for spaces ( _snake case_ ) and [correctly describe their meaning](http://37signals.com/svn/posts/3250-clarity-over-brevity-in-variable-and-method-names). Do **not** use [Hungarian notation](http://en.wikipedia.org/wiki/Hungarian_notation).

Variable declarations are followed by a space, an equals sign, a space and the variable value.

**WRONG:**
```Ruby
txtTitle = 'My title'
txt_title = 'My title'
mytitle = 'My title'
title='My title'
@title= 'My title'
```

**RIGHT:**
```Ruby
title = 'My title'
my_title = 'My title'
@title = 'My title'
```


