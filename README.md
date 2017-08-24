# ZSS

## 📐 Sass for design systems.

ZSS is a Sass framework that helps you design and build UI components with several design scales.

---
- [Background](#background)
  - [What it does](#what-it-does)
  - [What it doesn’t do](#what-it-doesnt-do)
  - [Principles](#principles)
- [Setup](#setup)
- [Structure](#structure)
  - [Class names](#class-names)
  - [Source order](#source-order)
  - [Responsive](#responsive)
- [How to use](#how-to-use)
  - [Variables and configuration](#variables-and-configuration)
    - [Design scales](#design-scales)
    - [Other variables](#other-variables)
  - [Abstract objects](#abstract-objects)
  - [Utility classes](#utility-classes)
---

## Background

### What it does

- Provides a simple base for your typography.
- Provides abstractions of common UI patterns, so you can focus on the specific design details.
- Functional CSS: generates immutable and configurable utility classes.
- Provides a flexible and configurable flexbox grid, with an optional fallback for ancient browsers.

### What it doesn’t do

- No design. If you’re looking for a framework to quickly build a prototype that you can discard later, Bootstrap or a specific prototyping tool is a better choice.
- Unlike Bootstrap, ZSS does not contain pre-made components or JavaScript.

### Principles

ZSS is built on a few principles.

- **Composition over repetition**   
  The `class` attribute is perfect for composing your design with multiple classes. It leads to better re-usability of your design and smaller CSS stylesheets.
- **Configurable and optional**   
  In ZSS, generated utility classes have configurable values. Need an extra value, or don’t like the default values? Just override a variable in your project. Don’t need the button abstraction class? Just don’t import it.
- **Responsiveness**   
  All utility classes have responsive equivalents, so you can use different values on different screens.
- **Design scales**   
  ZSS uses scales to limit the number of available values for certain properties, like `color` and `margin`.

## Setup

Install:

```cli
npm install zss --save
```

After that, import the files you need into your Sass stylesheet.

```sass
@import "../node_modules/zss/src/utilities/background-color";
``` 

ℹ️ You can use the accompanying file [`zss.scss`](src/zss.scss) as a starting point for your project's stylesheet. It imports all files that are available in ZSS.

## Structure

### Class names

ZSS uses namespaces, similar to the system [CSS Wizardry](https://csswizardry.com/2015/03/more-transparent-ui-code-with-namespaces/) wrote about.

- `o-` suffix for abstract objects.
- `u-` suffix for utility classes.

### Source order

ZSS advocates importing sources files in the way [ITCSS](http://itcss.io/) prescribes, with an inverted specificity.

1. Settings and variables
2. Mixins and other Sass helpers
3. Generic: common resets
4. Base: unclassed HTML and page setup
5. Abstract objects
6. Components
7. Scopes
8. Theming
9. Visual classes
10. Utility classes

### Responsive

ZSS uses an `@breakpoint` suffix to indicate if a class only works on a certain breakpoint, e.g. `u-black@md`.

---

## How to use

### Configuration and variables

All ZSS variables are defined in [variables/_zss-defaults.scss](../src/variables/_zss-defaults.scss). Override them at will in your project.

```sass
@import '../node_modules/zss/src/variables/zss-defaults';
@import 'variables/zss-overrides';
```

#### Design scales

Variable     | Explanation
------------ | ----------
`$zss--opacity-scale` | Limited set of values for opacity utility classes.
`$zss--border-radius-scale` | Limited set of values for border-radius utility classes.
`$zss--border-width-scale` | Limited set of values for border-width classes.
`$zss--spacing-scale` | Limited set of values for margin and padding utility classes. 
`$zss--type-scale` | Limited set of values for font-size utility classes.
`$zss--line-height-scale` | Limited set of values for line-height utility classes.
`$zss--width--scale` | Limited set of values for width utility classes.
`$zss--width--percentage-scale` | Limited set of values for width utility classes, in percentages.
`$zss--max-width--scale` | Limited set of values for max-width utility classes.
`$zss--height--scale` | Limited set of values for height utility classes.
`$zss--height--percentage-scale` | Limited set of values for height utility classes, in percentages.

#### Other variables

Variable     | Explanation
------------ | ----------
`$zss--colors` | Sass map with color definitions for text, backgrounds and borders utility classes.
`$zss--grid-max-widths` | Sass map containing the max width of the grid on each breakpoint.
`$zss--grid-columns` | The number of columns a grid row can have.
`$zss--grid-gutter` | The amount of whitespace between grid column.
`$zss--grid-type` | Defines if the grid is generated with flexbox or floats.
`$zss--breakpoints` | Sass map containing breakpoint names and screen sizes.
`$zss--border-colors` | Sass map containing color definitions for border utility classes.
`$zss--base-font-size` | Font size that's used a base for `rem` values.
`$zss--base-line-height` | Base line-height that's applied to the BODY element.
`$zss--media-margin` | The margin between the image and text of media objects.

## Helpers

Helpers are mixins, functions, and similar programmatic constructs in Sass that help with code re-use. ZSS provides these helpers:

- [clear](helpers/clear): mixin that contains a clearfix.

### Abstract objects

Objects are classes that define the structure of a common UI pattern, like the popular media object. ZSS provides these objects:

- [button](docs/layout/button.md): a gathering of properties most used in buttons.
- [grid](docs/layout/grid.md): a grid structure to divide the page in rows and columns.
- [list-reset](docs/layout/list-reset.md): rests ordered and unordered lists.
- [media](docs/layout/media.md): image next to text.

### Utility classes

Utility classes have a single responsibility. In other words, they affect the value of just one single CSS property. (This
construct is also known as functional CSS.) The most common CSS properties are available in ZSS and are listed
in the [property index 📇](property-index.md).