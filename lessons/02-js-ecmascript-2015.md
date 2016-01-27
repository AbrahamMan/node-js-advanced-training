# New in ECMAScript 2015 (ECMAScript 6)

## Constants

Support for constants (also known as "immutable variables"), i.e. variables which cannot be re-assigned new content.

```js
// Base const declaration
const CHUNK_SIZE = 1024;

// Try declarete one const twice
const MAX_SIZE = 10;
const MAX_SIZE = 20; // SyntaxError: Identifier 'MAX_SIZE' has already been declared

// Try rewrite const
const RETRY_COUNT = 10;
RETRY_COUNT = 100; // TypeError: Assignment to constant variable.

// Important: rewrite const as object
const USER_SETTINGS = { size: 1024 };
USER_SETTINGS.size = 1;
console.log(USER_SETTINGS); // { size: 1 }
```

#### Notes: 

 * Remember constants created using `const` keyword have function level scope like variables created with `var` keyword.

***


## Constant Objects

Creating a constant object in which new properties could not be added, modified or removed.

```js
// Freeze const as object
const USER_SETTINGS = { size: 1024 };
Object.freeze(USER_SETTINGS);
USER_SETTINGS.size = 1; // TypeError: Cannot assign to read only property 'size' of #<Object>

// Important: not freeze recursive
const REFERENCE_OBJECT = { a: { b: true } };
Object.freeze(REFERENCE_OBJECT);
REFERENCE_OBJECT.a.c = false;
console.log(REFERENCE_OBJECT); // { a: { b: true, c: false } }
```

#### Notes:

 * Note that `values that are objects can still be modified`, unless they are also frozen.

***


## Block-Scoped Variables
  
Block-scoped variables without hoisting.

```js
// ES6 
for (let i = 0; i < 10; i++) {
    let user = { index: i };
}

console.log(user); // ReferenceError: user is not defined

// ES5
for (var i = 0; i < 10; i++) {
    let var = { index: i };
}

console.log(user); // { index : 9 }
```

``` js
// ES6 
if (true) {
    let count = 1;
}
  
console.log(count); // ReferenceError: count is not defined

// ES5
if (true) {
    var count = 1;
}
  
console.log(count); // 1
```


