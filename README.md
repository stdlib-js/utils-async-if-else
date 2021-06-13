<!--

@license Apache-2.0

Copyright (c) 2018 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->

# ifelseAsync

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] [![dependencies][dependencies-image]][dependencies-url]

> If a predicate function returns a truthy value, return `x`; otherwise, return `y`.

<!-- Section to include introductory text. Make sure to keep an empty line after the intro `section` element and another before the `/section` close. -->

<section class="intro">

</section>

<!-- /.intro -->

<!-- Package usage documentation. -->

<section class="installation">

## Installation

```bash
npm install @stdlib/utils-async-if-else
```

</section>

<section class="usage">

## Usage

```javascript
var ifelseAsync = require( '@stdlib/utils-async-if-else' );
```

#### ifelseAsync( predicate, x, y, done )

If a `predicate` function returns a truthy value, returns `x`; otherwise, returns `y`.

```javascript
var randu = require( '@stdlib/random-base-randu' );

function predicate( clbk ) {
    setTimeout( onTimeout, 0 );
    function onTimeout() {
        clbk( null, randu() > 0.5 );
    }
}

function done( error, result ) {
    if ( error ) {
        throw error;
    }
    console.log( result );
}

ifelseAsync( predicate, 1.0, -1.0, done );
```

The `predicate` function is provided a single argument:

-   `clbk`: callback to invoke upon `predicate` function completion

The callback accepts two arguments:

-   `error`: error object
-   `bool`: condition used to determine whether to return `x` or `y`

The `done` callback is invoked upon function completion and is provided at most two arguments:

-   `error`: error object
-   `result`: either `x` or `y`

</section>

<!-- /.usage -->

<!-- Package usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

## Notes

-   Execution is **not** guaranteed to be asynchronous. To guarantee asynchrony, wrap the `done` callback in a function which either executes at the end of the current stack (e.g., `nextTick`) or during a subsequent turn of the event loop (e.g., `setImmediate`, `setTimeout`).

</section>

<!-- /.notes -->

<!-- Package usage examples. -->

<section class="examples">

## Examples

<!-- eslint-disable callback-return -->

<!-- eslint no-undef: "error" -->

```javascript
var randu = require( '@stdlib/random-base-randu' );
var ifelseAsync = require( '@stdlib/utils-async-if-else' );

var i;

function next() {
    ifelseAsync( predicate, 'BOOP', 'beep', done );
}

function predicate( clbk ) {
    setTimeout( onTimeout, 0 );
    function onTimeout() {
        clbk( null, randu() > 0.9 );
    }
}

function done( error, result ) {
    if ( error ) {
        throw error;
    }
    i += 1;
    console.log( result );
    if ( i < 100 ) {
        return next();
    }
}

i = 0;
next();
```

</section>

<!-- /.examples -->

<!-- Section to include cited references. If references are included, add a horizontal rule *before* the section. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="references">

</section>

<!-- /.references -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2021. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/utils-async-if-else.svg
[npm-url]: https://npmjs.org/package/@stdlib/utils-async-if-else

[test-image]: https://github.com/stdlib-js/utils-async-if-else/actions/workflows/test.yml/badge.svg
[test-url]: https://github.com/stdlib-js/utils-async-if-else/actions/workflows/test.yml

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/utils-async-if-else/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/utils-async-if-else?branch=main

[dependencies-image]: https://img.shields.io/david/stdlib-js/utils-async-if-else
[dependencies-url]: https://david-dm.org/stdlib-js/utils-async-if-else/main

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/utils-async-if-else/main/LICENSE

</section>

<!-- /.links -->
