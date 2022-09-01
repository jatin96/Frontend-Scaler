# Frontend-Scaler

Javascript is an interpreted language.

# Types in Javascript 

 - Number 
 - String
 - boolean
 - null
 - undefined

 > Everything in Javascript is an object.

 > You can see the type of a variable by using typeof()

 > typeof(typeof(undefined)) --> string

 > typeof(NaN) --> number

## Type Coercion

In Javascript if you put a plus in front of a string then that turns into a number

```js
console.log(typeof(+"1")); // output : number
console.log(+"abc"); // output: NaN
console.log(8 + "8") // output: 88
console.log(1 + 2 + "hello world") // output: 3hello world
```

## Equality in Javascript

```js
var a = 10;
var b = "10";

console.log(a == b) // true
console.log(a === b) // false. // compares the type also
console.log(10.0 === 10) // true. round off happening here

var a = null;
var b = undefined;

console.log(a == b) // true since they signify the same thing
console.log(a === b) // false


var a = NaN
var b = NaN

console.log(a === b) // false because not a number means anything. This can also be used as a check
```

## Arrays in javascript

var a = new Array();
 > Javascript uses constructor functions to create objects.
```js
var a = [];
var b = [1, 2, 3, "hello"]; // this is possible because everything in js is an object. This is a key value pair with indices.

console.log(b.length);


var a = [1,2,3,4,5]
var b = a;
a = []

console.log(a); // []
console.log(b);// [1,2,3,4,5]
```

```js
var a = [1,2,3,4,5]
var b = a;
a.length = 0

console.log(a);// []
console.log(b);// []
```

## Functions in Javascript

In Javascript you can assign functions to variables, return functions and pass functions as parameters.

```js
function test() {
    var a = 10;
    console.log(a);
    return function() {
        console.log('yes');
    }
}

var a = function() {
    var d = 10;
    console.log(d);
}

// calling a function in variable : a()
```


