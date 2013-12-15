fragment.js
========

Asynchronous loading of html fragments.  This small loader will also process nested fragments via annotated html with mjs-fragment.<br>
Fragment.js depends on <a href="https://github.com/MiguelCastillo/resource.js">resource.js</a> for loading and caching the html fragments.<br>


1) Load simple html fragment sample.html
``` javascript
fragment("sample.html").done(function(tmpl) {
  console.log(tmpl);
});
```

``` html
<div>
Hello world!
</div>
```

2) Load nested fragment nested.html.  Once nested.html is loaded, child-fragment.html will be loaded and inserted into the div.<br>
The call to load nested.html will not return until all nested fragments are loaded.  The depth of nested fragments isn't limited either.  E.g. child-fragment.html can have other nested fragments and those fragments can have n levels deep of nested fragments.
``` javascript
fragment("nested.html").done(function(tmpl) {
  console.log(tmpl);
});
```

``` html
<div mjs-fragment="child-fragment.html">
</div>
```

3) You can configure the selector used for processing nested fragments by changing fragments.selector
``` javascript
fragment.selector = "data-fragment";
```

Or by passing in a selector parameter.
``` javascript
fragment("nested.html", "data-fragment").done(function(tmpl) {
  console.log(tmpl);
});
```
