1.0.1 (2022-05-02)
------------------

- fix package not actually containing any files :)

1.0.0 (2022-05-02)
------------------

- (no changes compared to alpha releases)

1.0.0-alpha4 (2022-05-02)
------------------

- fix major bugs introduced in last release
- **breaking:** rename more functions to avoid collisions with built-ins

1.0.0-alpha3 (2022-05-02)
------------------

- **breaking:** remove `math` module
- **breaking:** combine everything into a single module called `index`
- **breaking:** remove `pf-` prefix from functions

1.0.0-alpha1 (2022-05-02)
------------------

- **breaking:** drop compatibility with LibSass
- **breaking:** remove `clearfix` and `grid` modules
- **breaking:** rename this fork to `@johv/sass-labmix`
- fix deprecation warnings when using Dart Sass
- ignore `$steps` argument to most functions in `math` module

0.6.0 (2018-04-08)
------------------

- math: rename `ln()` to `log()` and `log()` to `log10()`
- color: interpret unitless angles (hues) as `deg` instead of `rad`
- contrast: `contrast-check()` return second argument instead of `null`

0.5.0 (2017-12-05)
------------------

- contrast: avoid cases with too little contrast in `contrast-stretch()`
- color: add support for HSLab and HSLuv color spaces
- color: change behavior of chroma/saturation in HSL color space

0.4.2 (2017-07-21)
------------------

- contrast: refine `pow()` approximation that was introduced in 0.4.0
- contrast: add new function `contrast-stretch()`

0.4.1 (2017-07-12)
------------------

- limit the files that go into npm package

0.4.0 (2017-06-02)
------------------

- change license from GPL-2+ to MIT
- color: reduce chroma to avoid clipping
- contrast: no longer requires a `pow()` function
- contrast: WCAG compliance levels can be used as thresholds

0.3.1 (2016-07-13)
------------------

- fix a typo in clearfix mixin

0.3.0 (2016-07-07)
------------------

- add feature: grid
- add feature: clearfix
- contrast: `luma()` is deprecated. Use `pf-lightness($color, 'lab')` from the
  color module instead.
- contrast: `alpha-blend()` is deprecated.
- add eyeglass support

0.2.1 (2016-04-23)
------------------

- math: Fix angles as input to `cos()` and `tan()`
- color: make default colorspace configurable
- color: add YUV colorspace

0.2.0 (2016-04-01)
------------------

- `$pi` has been converted to a function `pi()` for better compass
  compatibility.
- Add inverse trigonometric functions, including `atan2()`.
- Allow angles as input to trig functions.
- Add a generic bezier interpolation.
- Add CIELAB/CIELUV based color functions.

0.1.2 (2016-03-10)
------------------

- Improved test coverage for math module.
- Fix `pow(0, $exp)` if `$exp` is a float.
- Fix `sin($x)` for negativ `$x`.
- Fix `cos()`.
- Fix syntax error in `tan()`.

0.1.1 (2016-03-06)
------------------

- Fix an undefined variable in `contrast-check()`
- `contrast-check()` could not be called because it did not return a value. It
  now always returns `null`.

0.1.0 (2016-03-05)
------------------

The algorithm for calculating contrasts of transparent colors has been
overhauled completely:

- The old algorithm ignored the fact that gamma correction is non-linear.
- In order to simplify the API, `contrast()` now uses an approximation that
  does not care about the order of inputs. The exact algorithm is available as
  `contrast-min()`. Another effect of this change is that the `$bg` parameter
  of `contrast-color()` has been removed.

0.0.0 (2016-03-03)
------------------

initial release
