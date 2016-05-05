# coding-guidelines
Code's coding guidelines to consistent development

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
