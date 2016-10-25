# [redux-elm](http://salsita.github.io/redux-elm)

[![NPM version][npm-image]][npm-url]
[![Dependencies][dependencies]][npm-url]
[![devDependency Status][dev-dependencies]][dev-dependencies-url]
[![Build status][travis-image]][travis-url]
[![Downloads][downloads-image]][downloads-url]
[![Join the chat at https://gitter.im/salsita/redux-elm](https://badges.gitter.im/salsita/redux-elm.svg)](https://gitter.im/salsita/redux-elm?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

> [The Elm Architecture](https://github.com/evancz/elm-architecture-tutorial) in JavaScript for building really scalable applications.

`redux-elm` is framework specifically tailored for solving difficult problems that people have to face in modern front-end application development, it is heavily based on [Composition](http://salsita.github.io/redux-elm/composition/).

Goal of this project is to solve hard problems **by defining patterns, not implementation**. Library is very lightweight and you should be able to fully understand the codebase. Main building block is **[redux](http://github.com/reactjs/redux)** which serves as predictable state container and because `redux-elm` is built on top of that, you will be able to benefit from all of its tooling:


* [DevTools](https://github.com/zalmoxisus/redux-devtools-extension)
* Time Travel
* Immutable application snapshots
* Easy unit testing

Because `redux-elm` is about Patterns, we have really [thorough documentation](http://salsita.github.io/redux-elm) which guides you to utilize all the ideas that `redux-elm` provides.

See [why the Elm Architecture matters](http://salsita.github.io/redux-elm/).

## How does it look?

`redux-elm` is about Components and every Component must define two pieces `Updater` and `View` where `Updater` is very similar to Redux [`reducer`](http://redux.js.org/docs/basics/Reducers.html) and `View` is simple [`React`](https://facebook.github.io/react/) Component, of course you can use your own View library.

### Counter Updater

```javascript
import { Updater } from 'redux-elm';

const initialModel = 0;

export default new Updater(initialModel)
  .case('Increment', model => model + 1)
  .case('Decrement', model => model - 1)
  .toReducer();
```

### Counter View

```javascript
import React from 'react';
import { view } from 'redux-elm';

export default view(({ model, dispatch }) => (
  <div>
    <button onClick={() => dispatch({ type: 'Decrement' })}>-</button>
    <div>{model}</div>
    <button onClick={() => dispatch({ type: 'Increment' })}>+</button>
  </div>
));

```

### Installation & Usage
You can install `redux-elm` via npm.

```
npm install redux-elm --save
```

**We didn't want to keep all the boilerplate in `redux-elm` repo therefore we've prepared simple [`redux-elm-skeleton`](http://github.com/salsita/redux-elm-skeleton) repositiory which will serve as easiest way to start using `redux-elm`**.

```
git clone git@github.com:salsita/redux-elm-skeleton.git
cd redux-elm-skeleton
npm install
npm start
open http://localhost:3000
```

You will see Hello World so that you can immediately open your favorite Text Editor and start writing your own application. Skeleton repo integrates [`redux-devtools` Chrome extension](https://github.com/zalmoxisus/redux-devtools-extension), so we strongly recommend installing the extension.

### Boilerplate

Are you looking for more feature complete boilerplate? There are two boilerplates which works well with `redux-elm`:

1. https://github.com/jmarceli/redux-elm-boilerplate based on `react-boilerplate` 
2. https://github.com/salsita/redux-boilerplate from `redux-elm` authors but soon to be deprecated

## Documentation

Goal of documentation is explaining basic principle of `redux-elm` and this is Composition, it's divided into few chapters to gradually increase amount of complexity. 

1. [Getting Started Tutorial](http://salsita.github.io/redux-elm/getting-started/)
2. [GifViewer Tutorial](http://salsita.github.io/redux-elm/gif-viewer/)
3. [Composition](http://salsita.github.io/redux-elm/composition/)

First two chapters describes basic principles, while Composition part is the most important part explaining how `redux-elm` helps you building really scalable application. There's also Chapter which explains how to properly [Unit test](http://salsita.github.io/redux-elm/gif-viewer/unit-tests.html) your application.

## Examples

You will find original Elm Architecture examples written in JavaScript using `redux-elm`:

1. [Counter](./examples/counter)
2. [Counters Pair](./examples/pair-of-counters)
2. [Dynamic List of Counters](./examples/dynamic-list-of-counters)
2. [Random GIF Viewer](./examples/random-gif-viewer)
2. [Random GIF Viewers Pair](./examples/gif-viewers-pair)
2. [Dynamic List of Random GIF Viewers](./examples/gif-viewers-dynamic-list)

## Static Typing
Definitely one of the most important features of Elm programming language is its type system. Elm is statically typed language and fully supports type inference, unfortunately this is not same for JavaScript, however you can still use [flowtype](http://flowtype.org/) because `redux-elm` provides type definitions for everything that's publicly exposed. We strongly encourage you to do so, because Flow is a great help for spotting subtle bugs before they actually appear. Using Flow in your `redux-elm` [project is seemless and does not require any additional effort except installing flow as your project's dependency](https://github.com/salsita/redux-elm-skeleton/commit/cd6d370a4dcc999779ebd0eb3f67dff1ac1bfb1d).

Flow checks:

* correct model shape
* Matchers
* and many more...

## Discussion
Join the [discussion on gitter](https://gitter.im/salsita/redux-elm)

[npm-image]: https://img.shields.io/npm/v/redux-elm.svg?style=flat-square
[npm-url]: https://npmjs.org/package/redux-elm
[travis-image]: https://img.shields.io/travis/salsita/redux-elm.svg?style=flat-square
[travis-url]: https://travis-ci.org/salsita/redux-elm
[downloads-image]: http://img.shields.io/npm/dm/redux-elm.svg?style=flat-square
[downloads-url]: https://npmjs.org/package/redux-elm
[dependencies]: https://david-dm.org/salsita/redux-elm.svg
[dev-dependencies]: https://david-dm.org/salsita/redux-elm/dev-status.svg
[dev-dependencies-url]: https://david-dm.org/salsita/redux-elm#info=devDependencies
