# JavaScript Questions

## What is a primitive value?
It's data that's not an object and has no methods.

## What are the JavaScript Primitive Types?
There are 6 primitive data types: string, number, bigint, boolean, undefined, and symbol.


## Are Primitive Data Types Immutable?
**All primitives are immutable**, which means that they cannot be altered. It's important to remember that there is a difference between re-assigning a new value to a variable and mutating the existing value.

## What are Structural Types?
- Objects (Array, Map, Set, WeakMap, WeakSet)
- Function

## undefined vs null
In the structural meaning:
- `null` is for something that exists but it's empty
- `undefined` is for somehting that does not exist yet or that doesn't exist anymore

## What is an Object?
It's a collection of properties. Where aditional properties can be added or removed after the creation of the object. Property values can be of any kind, including other objects. Properties are identified using key values. A key value is either a String or a Symbol.

## What are properties?
Objects can be seen as a collection of properties.
Properties are identified using `key values`. A key value is either a String or a Symbol.

There are two types of object properties which have certain attributes: The data property and the accessor property.


## What is Dynamic typing?
Variables in JavaScript are not associated with a particular type (like in Java). Variables can be re-assigned to other types different to their initial one.
The following code would work without a problem:
```javascript
let foo = 42;
foo = 'bar';
foo = true;
```

## What is type coercion?
Is the automatic or implicit conversion of values from one data type to another.

## What is the difference between “=”, “==” and “===”?
***
### `=` Single Equal Sign
is for assigning values.

### `==` Double Equal Sign
is for comparing two values. It uses type inference, meaning that the statement
```javascript
'2' == 2
```
it would return a true value

### `=== Tripe Equal Sign`
is for comparing two values. But it does not use type inference, meaning that if I compare
```javascript
'2' === 2
```
it would return a false value

## What is the difference between `var`, `let` and `const`?

### `var`
- When it's outside of a function it's globally scoped
- When declared inside a function it's scoped within the function
- You can redefine a variable that already exists, which can be buggy

### `let`
- let is block scoped, even if we declare it outisde of a function it will onlt be accesible within its block
- let can be updated, but no re-declared (it can be done in a different scope because essentially it's not the same variable)

### `const`
- as it names states, these variables will maintain a constant value
- const cannot be updated or re-declared
- objects declared with const can have their properties updated

## Passing something by value vs passing it by reference?
- When you change a primitive value, you never change the underlying primitive, it just points the variable to a new primitive or object.
- Changing a property of an object referenced by a variable, does change the underlying object.
