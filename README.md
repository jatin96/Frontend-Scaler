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

## Immediately invoked Function

In Javascript, a function can have no name. So, you can call a function immediately where you define it.

```js
(function() { console.log("immediately invoked function")})()
```


## Global namespace In Javascript

Anything you create in Javascript gets attached to the global namespace which is called **window**.

But a immediately invoked function is not attached to window because it is immediately called and it doesn't pollute the global namespace window.

## Objects in Javascript

```js
// creating a object in java.
var a = {};
var b = new Object();

var dog = {
    name: "Ramu",
    breed: "Desi",
    bark: function() {
        console.log("Bhaw Bhaw");
    }
}

console.log(dog.name);
console.log(dog["name"]); // this way of accessing is needed because if the key here was dynamic (stored in a variable) then you have to use this way to get the value from the object.
```

```js

function test() {
    console.log(arguments); // arguments will contain everything you pass to the function. You don't need to define the parameters.
}

test(1,2,3);
```

> Arguments is a array like structure(we cannot use common array functions in arguments). How to convert it into a typical array ?


## Hoisting

All variables in javascript are hoisted to the top of the function.
```js
var a = 10;
function abc() {
    // var a; hoisting will bring **only** the declaration to the top. Hence output here will be undefined.
    console.log(a);
    var a = 5; // a = 5;
}
```

## Implicit coersion

In javascript, toString is automatically applied to keys in an array due to coersion.

see the output for the below snipped

```js
var a = {}, b = {key: 'b'}, c = {key: 'c'}
a[b] = 123; // due to coersion, a[object Object]
a[c] = 456;// a[object Object] = 456

console.log(a[b]) // output : 456
```

## Constructor Functions

> In ES6 JS, you can use keywords like class etc.


> In javascript, classes are constructor functions.
```js
function Dog(name, breed) { // Constructor function name needs to start with capital character.
    this.name = name;
    this.breed = breed;
}

var d = new Dog('tommy', 'desi')
console.log(d.name);
```

## Proto 

In Javascript, inheritance happens using proto. Proto is an internal property of an object.

```js
var animal = {
        eats : true,
        walk: function() {
            console.log("walking...");
        }
}

var rabbit = {
    jumps: true,
    __proto__ : animal // this will include all properties of animal in rabbit.
}
```

## Prototype in Javascript

Every object in javascript has aa prototype property which is used to implement inheritance. Using prototype you can expose extra fields

```js
function Foo(y) {
    this.y = y;
}

Foo.prototype.x = 10; // this is useful when you want all the objects of Foo to have these properties.
Foo.prototype.calculate = function (z) {
    return this.x + this.y + z;
}

var a = new Foo(10);
console.log(a.calculate(20));
```

> Prototype internally uses Proto.

Prototype is useful because you declare all the generic functions and properties in one place and you make the objects point to that place. So memory is saved because prototype is a public property and it is not created again and again.


## Some tricky output questions

```js
0.1 + 0.2 === 0.3 // this is false in JS due to precision in storing numbers

function foo1() {
    return {
        bar: "hello"
    };
}d

function foo2() {
    return 
    {
        bar: "hello"
    };
}

foo1() --> returns {bar: "hellow"}
foo2() --> returns undefined // this is because JS adds semicolon after every statement that doesn't have a semi colon.
```


## Call, Bind and Apply


Call is used to change the context of this
```js
var pokemon = {
    firstname: 'pika';
    lastname: 'chu';
    pokeName: function() {
        return this.firstname + this.lastname;
    }  
}

var pokemonName = function(snack, hobby) {
    console.log(this.pokeName() + ' loves ' + snack + ' and ' + hobby);
};

pokemon.call(pokemon, 'food', 'jumping') // [context, parameters comma separated]
pokemon.apply(pokemon, ['food', 'jumping']) // [context, parameters in an array]
var a = [1,5,3,10];

pokemon.log(Math.max.apply(this, a));
var pokemonBinded = pokemonName.bind('food', 'jumping'); // bind helps you save the context.

```
> The only different between call and apply is the different in which parameters are passed.

## Closure

Closure is the retention of the value of variable after the function has returned.

```js
function makeWorker() {
    var name = "Pete";

    return function() {
        console.log(name);
    }
}

var name = "John";

var worker = makeWorker();;

worker(); // the value of name in the function is retained although it's not in scope.
```














