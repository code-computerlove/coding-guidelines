# coding-guidelines
Code's coding guidelines to consistent development

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
