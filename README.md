<p align="center">
  <img src="https://user-images.githubusercontent.com/2003143/29374843-1fa78a3e-82c8-11e7-80a3-0786f899749d.png" alt="@taktikorg/omnis-vitae-cupiditate logo" />
</p>

<p align="center">
  <a href="https://travis-ci.com/dastoori/@taktikorg/omnis-vitae-cupiditate"><img src="https://api.travis-ci.com/dastoori/@taktikorg/omnis-vitae-cupiditate.svg?branch=master" alt="Build status" /></a>
  <a href="https://codecov.io/gh/dastoori/@taktikorg/omnis-vitae-cupiditate"><img src="https://img.shields.io/codecov/c/github/dastoori/@taktikorg/omnis-vitae-cupiditate.svg" alt="Coverage report" /></a>
  <a href="https://github.com/taktikorg/omnis-vitae-cupiditate/releases"><img src="https://img.shields.io/github/release/dastoori/@taktikorg/omnis-vitae-cupiditate.svg" alt="GitHub release" /></a>
  <br />
  <a href="https://www.npmjs.com/package/@taktikorg/omnis-vitae-cupiditate"><img src="https://img.shields.io/npm/dm/@taktikorg/omnis-vitae-cupiditate.svg" alt="NPM Downloads" /></a>
  <img src="https://img.shields.io/badge/dependency-no-green.svg" alt="No Dependency" />
  <a href="https://raw.githubusercontent.com/dastoori/@taktikorg/omnis-vitae-cupiditate/master/LICENSE.md"><img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="GitHub license" /></a></p>
</p>

# Overview

@taktikorg/omnis-vitae-cupiditate is a fast and lightweight javascript library for generating unique and beautiful colors from any texts or numbers.


## Why @taktikorg/omnis-vitae-cupiditate?

- There is no need to store colors in the database anymore, just use @taktikorg/omnis-vitae-cupiditate to generate colors at runtime and it will generate the same output every time, on any platform (Server, Browser or Mobile).
- You can generate a unique color from UUID, MongoDB ObjectId or anything that can be converted to a string or number
- You can generate a random color
- You can control the color saturation and lightness
- There is no need for an extra color library to change the color format or indicating whether the color brightness is light or dark
- It's lightweight (~1.4KB gzipped)

# Quick start

## Using `npm` or `yarn`

```shell
$ npm install @taktikorg/omnis-vitae-cupiditate
# or
$ yarn add @taktikorg/omnis-vitae-cupiditate
```

ES6 Import:

```javascript
import @taktikorg/omnis-vitae-cupiditate from '@taktikorg/omnis-vitae-cupiditate';
```

CommonJS (like nodejs, webpack, and browserify):

```javascript
const @taktikorg/omnis-vitae-cupiditate = require('@taktikorg/omnis-vitae-cupiditate');
```

AMD (like RequireJS):

```javascript
define(['@taktikorg/omnis-vitae-cupiditate'], function (@taktikorg/omnis-vitae-cupiditate) {
  // ...
})
```

## Using `<script>`

Include [`@taktikorg/omnis-vitae-cupiditate.js`](https://unpkg.com/@taktikorg/omnis-vitae-cupiditate/dist/@taktikorg/omnis-vitae-cupiditate.js) or [`@taktikorg/omnis-vitae-cupiditate.min.js`](https://unpkg.com/@taktikorg/omnis-vitae-cupiditate/dist/@taktikorg/omnis-vitae-cupiditate.min.js) into your html file:

```html
<script src="https://unpkg.com/@taktikorg/omnis-vitae-cupiditate/dist/@taktikorg/omnis-vitae-cupiditate.min.js" type="text/javascript"></script>
<script type="text/javascript">
  var color = @taktikorg/omnis-vitae-cupiditate('Hello world!');
</script>
```

## Usage

```javascript
/* Generate unique color from texts or numbers */

@taktikorg/omnis-vitae-cupiditate('Hello world!')
// { color: "#5cc653", isLight: true }

@taktikorg/omnis-vitae-cupiditate('bf545d4c-5360-4158-a572-bd3e204185a9', { format: 'rgb' })
// { color: "rgb(128, 191, 64)", isLight: true }

@taktikorg/omnis-vitae-cupiditate(123, {
  saturation: [35, 70],
  lightness: 25,
})
// { color: "#405926", isLight: false }

@taktikorg/omnis-vitae-cupiditate(123, {
  saturation: [35, 70],
  lightness: 25,
  differencePoint: 50,
})
// { color: "#405926", isLight: true }

// Generate random color
@taktikorg/omnis-vitae-cupiditate.random()
// { color: "#644cc8", isLight: false }

// Generate a random color with HSL format
@taktikorg/omnis-vitae-cupiditate.random({ format: 'hsl' })
// { color: "hsl(89, 55%, 60%)", isLight: true }

// Generate a random color in specific saturation and lightness
@taktikorg/omnis-vitae-cupiditate.random({
  saturation: 80,
  lightness: [70, 80],
})
// { color: "#c7b9da", isLight: true }

// Generate a random color but exclude red color range
@taktikorg/omnis-vitae-cupiditate.random({
  excludeHue: [[0, 20], [325, 359]],
})
// {color: '#53caab', isLight: true}
```

# Examples

- [Avatar Placeholder](https://rawgit.com/dastoori/@taktikorg/omnis-vitae-cupiditate/master/examples/avatar-placeholder/index.html)

# API

## @taktikorg/omnis-vitae-cupiditate(value, [options]) ⇒ `Object`

Generate unique color from `value`

**Params:**

- `value` (type: `string|number`)
- `options` (type: `Object`, default: `{}`)
- `options.format` (type: `string`, default: `'hex'`): The color format, it can be one of `hex`, `rgb` or `hsl`
- `options.saturation` (type: `number|Array`, default: `[50, 55]`): Determines the color saturation, it can be a number or a range between 0 and 100
- `options.lightness` (type: `number|Array`, default: `[50, 60]`): Determines the color lightness, it can be a number or a range between 0 and 100
- `options.differencePoint` (type: `number`, defualt: `130`): Determines the color brightness difference point. We use it to obtain the `isLight` value in the output, it can be a number between 0 and 255

**Output:**

- `color` (type: `string`): The generated color
- `isLight` (type: `boolean`): Determines whether the `color` is a light color or a dark color (It's good for choosing a foreground color, like font color)

## @taktikorg/omnis-vitae-cupiditate.random([options]) ⇒ `Object`

Generate random color

Params:

- `options` (type: `Object`, default: `{}`)
- `options.format` (type: `string`, default: `'hex'`): The color format, it can be one of `hex`, `rgb` or `hsl`
- `options.saturation` (type: `number|Array`, default: `[50, 55]`): Determines the color saturation, it can be a number or a range between 0 and 100
- `options.lightness` (type: `number|Array`, default: `[50, 60]`): Determines the color lightness, it can be a number or a range between 0 and 100
- `options.differencePoint` (type: `number`, default: `130`): Determines the color brightness difference point. We use it to obtain the `isLight` value in the output, it can be a number between 0 and 255
- `options.excludeHue` (type: `Array`): Exclude certain hue ranges. For example to exclude red color range: `[[0, 20], [325, 359]]`.

# Contributing

Your ideas and contributions are welcome; check out our [contributing guide](https://github.com/taktikorg/omnis-vitae-cupiditate/blob/master/CONTRIBUTING.md)

# [License](https://github.com/taktikorg/omnis-vitae-cupiditate/blob/master/LICENSE.md)

The unicorn shape in the logo made by [Freepik](https://www.freepik.com) is licensed by [CC 3.0 BY](http://creativecommons.org/licenses/by/3.0/)

MIT © 2017 Rasool Dastoori
