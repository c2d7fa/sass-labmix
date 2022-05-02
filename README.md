# `@johv/sass-labmix`

This pure-Sass library provides an alternative to some of the features that will be added in [CSS Color Module Level 5](https://www.w3.org/TR/css-color-5/), namely `mix` as an alternative to `color-mix()` and support for Lab and LCh color spaces through the `lab` and `lch` functions.

When these functions become commonly available through CSS, this library will be deprecated. See the *Alternatives* section below for more information.

The library is a fork of Tobias Bengfort's [sass-planifolia](https://github.com/xi/sass-planifolia/). The aim of this fork is to strip it down to just the color-manipulation functions and bring it up to date with the current version of Sass. Read [this pull request](https://github.com/xi/sass-planifolia/pull/6) to understand why this fork exists.

See the [full documentation](https://c2d7fa.github.io/sass-labmix/) for more details.

## Quick start

Install the library:

    npm install --save-dev @johv/sass-labmix

Import it in your Sass files (most bundlers support the tilde-syntax; otherwise use `node_modules/@johv/sass-labmix` explicitly):

```scss
@use "~@johv/sass-labmix" as labmix;

.test {
    background-color: red;

    // pick between two colors (default: black and white) to get good contrast
    color: labmix.contrast-color(red);

    // mix orange with black or white to get good contrast to red
    border-color: labmix.contrast-stretch(red, orange);

    // mix red with black in a perceptually uniform color space
    box-shadow: 0 0 1em labmix.shade(red, 0.5, 'lab');
}
```

## Alternatives

- [CSS Color Module Level 5](https://www.w3.org/TR/css-color-5/) will provide native support for Lab and related color spaces and will support color mixing with `colox-mix()`. However, as of May 2022, it is not yet widely available.
- [Parcel's CSS transformer](https://github.com/parcel-bundler/parcel-css) implements some of the functionality of CSS Color Module Level 5, including `color-mix()` and `lch()`. If you're already using Parcel, just use that instead!
- [PostCSS](https://postcss.org/) supports Lab and related color spaces through [postcss-preset-env](https://github.com/csstools/postcss-plugins/tree/main/plugin-packs/postcss-preset-env), but [as of May 2022, it does not support `color-mix()`](https://github.com/csstools/postcss-plugins/issues/177).
- This library is a fork of [sass-planifolia](https://github.com/xi/sass-planifolia/). This fork has less functionality, but aims to be compatible with Dart Sass (without triggering any deprecation warnings). Changes made here may or may not be upstreamed into Planifolia in the future.
- [oddbird/blend](https://github.com/oddbird/blend) also provides early access to some of the functionality of the CSS Color Module Level 5 features, but unless I'm missing something, there is no equivalent of `mix`.
