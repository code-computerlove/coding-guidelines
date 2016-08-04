# coding-guidelines
Code's coding guidelines to consistent development

## Inheritance vs Composition

Avoid using inheritance, prefer composition.

In classic OO you should prefer composition over inheritance. However, since JavaScript employs delegation over Object-orientation language, this is more of an anti-pattern. If in doubt, avoid this.

> @TODO add an example link

## DOM Selectors
Use data attributes instead of other selectors when querying the DOM. This is because you will have less brittle code.

```javascript
// bad 
var foo = document.querySelectorAll('.foo');

// good
var foo = document.querySelectorAll('[data-foo]');
```

## Variables
Use camelCase for variables and UPPER_CASE for constants. Define variables at top of scope with one variable per line.

```javascript
// bad
var foo, bar, baz;

foo = foo + 1;

var myMateJez = 'something';

// good
var foo = 'This may change';
var BAR = 'This is intended to be constant';
```

Variables containing a jQuery object should start with a dollar($)

```javascript
var $foo = $('.foo');
```

## Closures
Use them. This stops you polluting the global scope by having scoped variables and functions. 

If you need to use a global variable, attach it to `window` 

```javascript
(function(window, undefined){
	window.foo = 'globalVar';
	
	var scopedVar = 'Matt';
})(window);

console.log(window.foo); // globalVar
console.log(scopedVar); // undefined
```

## Strict Mode
Always use [strict mode](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode). ES2015 deprecates the use of non-strict mode.
```javascript
(function(){
	'use strict';
})();
```

## Quotes
Use single quotes, eg:
```javascript
var foo = 'bar';
```

## Naming functions
Always name functions. Every function should be named as if there is an error, this name will shown in the browser console. Naming over using anonymous functions in loops or callbacks also allows for re-use of functions.
```javascript
// bad
foo.each(function (element) {
	//do stuff
});

// good
function namedFunction (param) {
	// do stuff
}

foo.each(namedFunction);

// can also now re-use this function
namedFunction(param);

// good 
foo.each(function namedFunction (element) {
	// do stuff
});

```

## Equality

You should always use `===` when checking equality of two values. If using `==` the type of the values are coerced which can result in unexpected results.

```js
1 == true // true
1 === true // false
```
When explicitly looking for the state of a variable use `typeof` rather than `==`. For example to determine if a variable has had a value set yet use:

```js
// bad
if(foo) {
  // do stuff
}

// good
if(typeof foo !== 'undefined') {
  // do stuff
}
```

### Hanging Commas

Hanging commas should not be used for object, array etc. There should be no `,` on the last element / key of an array or object.

```js
// bad
var names = ['bob', 'james',]; //hanging comma at end

// good
var names = ['bob', 'james']; // no hanging comma at the end
```

### Testing

The default testing frameworks that should be used:

* [Mocha](https://mochajs.org/) as the test runner
* [Chai](http://chaijs.com/) as assertion, BDD
* [Karma](https://karma-runner.github.io/0.13/index.html) allows to run the above in a browser context.
* [Sinon](http://sinonjs.org/) Mocking framework

### Versioning

* Read up and use [SemVer](http://semver.org/)
* Ensure project dependencies are `.npmshrinkwrap`
