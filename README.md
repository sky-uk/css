# Sky CSS Style Guide

Our approach to CSS

## Contents

### Writing CSS
* [Architecture](#architecture)
* [Selectors](#selectors)
* [Formatting](#formatting)
* [Extending](#extending)
* [Readings](#readings)

### Linter
* [Installation](#installation)
* [Versioning](#versioning)
* [Champions](#champions)

---

## Writing CSS

### Architecture

Style vs. Structure

### Selectors
It's important we keep code transparent and self-documented when it comes to naming our selectors. 

#### BEM
TODO

#### States
- `is-`
- `has-` 

State prefixes signify that the piece of UI in question is currently styled a certain way because of a state or condition (SMACSS). It tells us that the DOM currently has a temporary, optional, or short-lived style applied to it due to a certain state being invoked.

#### Namespacing
Following a prefix convention provides better insight into a class' purpose for other developers to work with.

For more information, read [Harry Roberts'](https://github.com/csswizardry/) article [More Transparent UI Code with Namespaces](http://csswizardry.com/2015/03/more-transparent-ui-code-with-namespaces/).

* `o-` signifies that this class is an **Object**, and that it may be used in any number of unrelated contexts to the one you can currently see it in. :warning: Making modifications to these types of class could potentially have knock-on effects in a lot of other unrelated places.
* `c-` signifies that this class is a **Component**. This is a concrete, implementation-specific piece of UI. All of the changes you make to its styles should be detectable in the context you're currently looking at. Modifying on top of these styles should be safe and have no side effects.
* `u-` signifies that this class is a **Utility** class. It has a very specific role (often providing only one declaration) and should not be bound onto or changed. It can be reused and is not tied to any specific piece of UI. You will probably recognise this namespace from libraries and methodologies like SUIT.
* `t-` signifies that a class is responsible for adding a **Theme** to a view. It lets us know that UI Components' current cosmetic appearance may be due to the presence of a theme.
* `js-` signifies that this piece of the DOM has some **behaviour** acting upon it, and that JavaScript binds onto it to provide that behaviour. If you're not a developer working with JavaScript, leave these well alone.
* `qa-` signifies that a **QA or Test Engineering** team is running an automated UI test which needs to find or bind onto these parts of the DOM. Like the JavaScript namespace, this reserves hooks in the DOM for non-CSS purposes.

### Formatting
TODO

### Readings
- [CSS Guidelines](http://cssguidelin.es/)
- [idiomatic-css](https://github.com/necolas/idiomatic-css)
- [OOCSS](https://www.smashingmagazine.com/2011/12/an-introduction-to-object-oriented-css-oocss/)

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
