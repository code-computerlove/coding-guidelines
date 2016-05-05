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
