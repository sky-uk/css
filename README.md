# Sky CSS Style Guide

Our approach to CSS

## Contents

### Writing CSS

* [Architecture](#architecture)
* [Template](#template)
* [Selectors](#selectors)
* [Properties](#properties)
* [Formatting](#formatting)
* [Extending and Modifying](#extending-and-moidfying)
* [Resources](#resources)

### Linter

* [Installation](#installation)
* [Versioning](#versioning)
* [Champions](#champions)

---

## Writing CSS

### Architecture

* Style vs. Structure
* DRY


#### Project Structure

Project styles should be structured following closely to the principles of [ITCSS](https://medium.com/@jordankoschei/how-i-shrank-my-css-by-84kb-by-refactoring-with-itcss-2e8dafee123a#.7gdzbrk1m), imported in the following order for greater control over specificity:

0. Settings
0. Tools
0. Generic
0. Base
0. Objects
0. Components
0. ~~Trumps~~ Utilities


### Selectors

It's important we keep code transparent and self-documented when it comes to naming our selectors. 

:x: **Don't**

* **Don't** use `html` tags in selectors.
* **Don't** use IDs (`#`) in selectors.
* **Don't** uncessarily nest selectors.
  * Try to keep selectors flat, at the same level of specificity.
  * Avoid going more than 2 levels deep. 

:white_check_mark: **Do**

* **Do** use classes.

#### Specificity

By following the steps above (specifically by using classes and limited nesting) conflicts with specificity shouldn't be a problem.

:warning: **Never** use `!important`

If you're struggling to ovverride styles, battling specificty, the safest option is to [chain the selector to itself](http://csswizardry.com/2014/07/hacks-for-dealing-with-specificity/#safely-increasing-specificity). In SCSS we can achieve this by:

```css
/**
 * Doubling up a selector's specificity in SCSS.
 *
 * 1. Outputs as `.c-example.c-example`
 *
 */

.c-example {
  color: #4a4a4a;

  &#{&} { /* [1] */
    text-decoration: none;
  }
}
```

#### BEM

TODO

#### States

* `is-`
* `has-` 

State prefixes signify that the piece of UI in question is currently styled a certain way because of a state or condition (SMACSS). It tells us that the DOM currently has a temporary, optional, or short-lived style applied to it due to a certain state being invoked.

#### Namespacing

Following a prefix convention provides better insight into a class' purpose for other developers to work with.

* `o-` signifies that this class is an **Object**, and that it may be used in any number of unrelated contexts to the one you can currently see it in. :warning: Making modifications to these types of class could potentially have knock-on effects in a lot of other unrelated places.
* `c-` signifies that this class is a **Component**. This is a concrete, implementation-specific piece of UI. All of the changes you make to its styles should be detectable in the context you're currently looking at. Modifying on top of these styles should be safe and have no side effects.
* `u-` signifies that this class is a **Utility** class. It has a very specific role (often providing only one declaration) and should not be bound onto or changed. It can be reused and is not tied to any specific piece of UI. You will probably recognise this namespace from libraries and methodologies like SUIT.
* `t-` signifies that a class is responsible for adding a **Theme** to a view. It lets us know that UI Components' current cosmetic appearance may be due to the presence of a theme.
* `js-` signifies that this piece of the DOM has some **behaviour** acting upon it, and that JavaScript binds onto it to provide that behaviour. If you're not a developer working with JavaScript, leave these well alone.
* `qa-` signifies that a **QA or Test Engineering** team is running an automated UI test which needs to find or bind onto these parts of the DOM. Like the JavaScript namespace, this reserves hooks in the DOM for non-CSS purposes.



### Properties

#### Ordering

Properties should be ordered in the following manner (a style similar to [Dropbox](https://github.com/dropbox/css-style-guide#rule-ordering)) to promote readability:

0. Structure
  * `display`, `position`, `margin`, `padding`, `width`, `height`, `box-sizing`, `overflow` etc.
0. Typography
  * `font-*`, `line-height`, `text-*`, `letter-spacing` etc.
0. Stylistic
  * `color`, `background-*`, `border-*`, `animation`, `transition` etc.
0. Native interaction
  * `appearance`, `cursor`, `user-select`, `pointer-events` etc.
0. [@-rules](https://www.sitepoint.com/sass-basics-rules-directives/)
  * `@include` use your previously-defined mixins here.
0. Pseudo-elements
  * `::before`, `::after` etc.
0. Pseudo-classes
  * `:hover`, `:focus`, `:active` etc.
0. Nested elements

Definining separately:

0. [State classes](#states)
0. [Modifier classes](#bem)

##### Example

```css

.c-example {
}

.c-example.is-active {
}

.c-example--large {
}

```

### Formatting

TODO

### Extending and Modifying

:warning: **Never** use `@extend`.

### Resources

#### Readings

* [CSS Guidelines](http://cssguidelin.es/)
* [idiomatic-css](https://github.com/necolas/idiomatic-css)
* [OOCSS](https://www.smashingmagazine.com/2011/12/an-introduction-to-object-oriented-css-oocss/)

#### Other CSS Style Guides

* [Airbnb](https://github.com/airbnb/css)
* [Dropbox](https://github.com/dropbox/css-style-guide)
* [Primer (GitHub)](http://primercss.io/guidelines/)

---

## Linter

### Installation

Our CSS linter runs on [Stylelint](https://github.com/stylelint/stylelint), you can install the conguration by running:

```
$ npm install github:sky-uk/css --save
```

After installing, we recommend creating a symbolic link in the route of your project to reference the Style Guide's configuration:

```
$ ln -s node_modules/sky-css-lint/.stylelintrc .stylelintrc
```

### Versioning

The CSS Style Guide follows [Semantic Versioning](http://semver.org) to help manage the impact of releasing new library versions.

### Champions

The CSS Style Guide is maintained by the [Toolkit Champions](https://github.com/sky-uk/toolkit#champions).
