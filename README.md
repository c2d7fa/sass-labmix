# `@johv/sass-labmix`

This pure-Sass library provides an alternative to some of the features that will be added in [CSS Color Module Level 5](https://www.w3.org/TR/css-color-5/), namely `pf-mix` as an alternative to `color-mix()` and support for Lab and LCh color spaces through the `lab` and `lch` functions.

When these functions become commonly available through CSS, this library will be deprecated. See the *Alternatives* section below for more information.

The library is a fork of Tobias Bengfort's [sass-planifolia](https://github.com/xi/sass-planifolia/). The aim of this fork is to strip it down to just the color-manipulation functions and bring it up to date with the current version of Sass. Read [this pull request](https://github.com/xi/sass-planifolia/pull/6) to understand why this fork exists.

Currently, the following modules are included:

-   **math** for high performance math functions
-   **contrast** for WCAG compatible [color
    contrast](https://www.w3.org/TR/WCAG20/#contrast-ratiodef) functions
-   **color** for CIELAB/CIELUV based color functions (with support for
    [HSLuv](http://www.hsluv.org/))

These modules can be imported individually (color depends on math though).
Also note that these modules will only define mixins and variables. They will
not output any CSS. This means that importing them does not add a single byte
to your CSS.

See the [full documentation](https://c2d7fa.github.io/sass-labmix/) for more details.

## Quick start

Install the library:

    npm install --save-dev @johv/sass-labmix

Import it in your Sass files:

```scss
@import "node_modules/@johv/sass-labmix/sass/math";
@import "node_modules/@johv/sass-labmix/sass/contrast";
@import "node_modules/@johv/sass-labmix/sass/color";

.test {
    background-color: red;

    // pick between two colors (default: black and white) to get good contrast
    color: contrast-color(red);

    // mix orange with black or white to get good contrast to red
    border-color: contrast-stretch(red, orange);

    // mix red with black in a perceptually uniform color space
    box-shadow: 0 0 1em pf-shade(red, 0.5, 'lab');

    // calculate modular scale dynamically
    font-size: 16px * pow(1.5, 2);
}
```

## Alternatives

- [CSS Color Module Level 5](https://www.w3.org/TR/css-color-5/) will provide native support for Lab and related color spaces and will support color mixing with `colox-mix()`. However, as of May 2022, it is not yet widely available.
- [Parcel's CSS transformer](https://github.com/parcel-bundler/parcel-css) implements some of the functionality of CSS Color Module Level 5, including `color-mix()` and `lch()`. If you're already using Parcel, just use that instead!
- [PostCSS](https://postcss.org/) supports Lab and related color spaces through [postcss-preset-env](https://github.com/csstools/postcss-plugins/tree/main/plugin-packs/postcss-preset-env), but [as of May 2022, it does not support `color-mix()`](https://github.com/csstools/postcss-plugins/issues/177).
- This library is a fork of [sass-planifolia](https://github.com/xi/sass-planifolia/). This fork has less functionality, but aims to be compatible with Dart Sass (without triggering any deprecation warnings). Changes made here may or may not be upstreamed into Planifolia in the future.
- [oddbird/blend](https://github.com/oddbird/blend) also provides early access to some of the functionality of the CSS Color Module Level 5 features, but unless I'm missing something, there is no equivalent of `pf-mix`.
