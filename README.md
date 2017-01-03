# Sky CSS Style Guide

Our approach to CSS

## Contents

### Writing CSS
* [Architecture](#architecture)
* [Selectors](#selectors)
* [Namespacing](#namespacing)
* [Formatting](#formatting)
* [Extending](#extending)
* [Readings](#readings)

### Linter
* [Installation](#installation)
* [Versioning](#versioning)
* [Champions](#champions)

---

## Writing CSS

TODO

### Architecture



### Formatting

TODO

### Namespacing

TODO

### Readings

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
