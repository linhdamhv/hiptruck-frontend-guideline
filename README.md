# HipTruck Frontend Guideline

* This guideline represents bullet points in descending order of their importance.

* This guideline is just a summary of the well-known styleguides, [GitHub (CSS, HTML)](https://github.com/styleguide) and [CSSguidelin.es](http://cssguidelin.es/).

* HTML and CSS are not painful. They only are when you make them so.



## Constitution (The Three CSS Pillars)
### 1. Never create unnecessary elements

- There must not be any HTML element without attributes:

``` html
<!-- Illegal elements -->
<a href='/'>
  <span>Home Page</span>
</a>


<!-- Legal element -->
<a href'/'>Home Page</a>

```

- Combine elements as much as possible when they don't have conflict CSS styles:

``` html
<!-- Illegal elements -->
<div class='container'>
  <div class='another-container-style'>
  	<div class='js-selector-for-javscript'>
      Illegal
    </div>
  </div>
</div>


<!-- Legal element -->
<div class='container another-container-style js-selector-for-javscript'>
  Legal
</div>
```

### 2. Never nest CSS selectors unnecessarily
``` html
<header class="page-header">
  <div class="page-header-wrapper">
    <h1 class="page-title">
      Some Title
    </h1>
  </div>
</header>

<style>
/* Illegal nesting */
.page-header .page-header-wrapper .page-title {
}

/* Legal nesting */
.page-header .page-title {
}

/* Also legal nesting if you're sure you want to apply the styles to all page-title */
.page-title {
}
</style>
```
### 3. Always name HTML class and id meaningfully and unambiguously
``` html
<!-- Illegal naming: There may be other titles (e.g. product title, collection title) -->
<h1 class='title'>Home Page</h1>

<!-- Legal naming -->
<h1 class='page-title'>Home Page</h1>



<!-- Illegal naming: Container of what? -->
<div class='container'>...</div>

<!-- Legal naming -->
<div class='entire-page-container'>...</div>
```

## Law
* [Nesting CSS as little as possible](http://cssguidelin.es/#keep-it-low-at-all-times)
* Prepend `js-` to a class selector if you intent to use them in JavaScript:
``` html
<input type="submit" class="btn js-btn" value="Follow" />
``` 

* Prepend `is-` to a class selector if it is shared between CSS and JavaScript
* Do not select by tag names in CSS:
```html
<ul class='sidebar-nav'>
  <li class='sidebar-nav__link'>Link 1</li>
  <li class='sidebar-nav__link'>Link 2</li>
</ul>

<style>
/* Wrong */
.sidebar-nav li {
}

/* Right */
.sidebar-nav .sidebar-nav__link {
}
</style>
```

* Do not use `!important` unless you really have to
* [Prefer class selector to id selector](http://cssguidelin.es/#ids-in-css) in CSS to increase reusability.


## Ethic (optional but recommended)
* Follow [BEM-like Naming](http://cssguidelin.es/#bem-like-naming).
  + Naming for a block (a parent): `.user-dropdown`
  + Naming for children of the parent: `.user-dropdown__profile-image`, `.user-dropdown__username`
  + Naming for a modifier of the parent: `.user-dropdown--disabled`

  ``` html
  <section class='user-dropdown'>
    <img class='user-dropdown__profile-image'>
    <span class='user-dropdown__username'>...</span>
  </section>
  ```
  
* Add [meaningful whitespaces](http://cssguidelin.es/#meaningful-whitespace):
  * One (1) empty line between closely related rulesets.
  * Five (5) empty lines between entirely new sections.
``` scss
.page-header {
  .page-title {
  }

  .page-logo {
  }
}





.main-page-wrapper {
}
```

* No trailing whitespace.
* End files with a single newline character.
