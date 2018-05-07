
# Arrow functions
Arrow functions are very similiar to regular functions in behavior,but are quite deifferent syntactically. 

## Convert a function to an arrow function

``` 
const upperrizedNames = ['Farrin', 'Kagure', 'Asser'].map(function(name){
	return name.toUpperCase();
});
```
To convert into an arrow function

- remove the ```function``` keyword;
- remove the parentheses;
- remove the opening and closing curly braces;
- remove the ```return``` keyword
- remove the semicolon;
-add an arrow ```=>``` between the parameter list and the function body.  

## Using Arrow Function
One confusing syntax is when an arrow function is stored in a variable.
```
const greet = name => `Hello ${name}!`;

greet('Asser');
Returns: Hello Asser!
```
## Parentheses and arrow function parameteres

If there's only one parameter in the list, then you can write it just like the example above. But, if there are two or more items in the parameter list, or if there are zero items in the list, then you need to wrap the list in parentheses:

```
// empty parameter list requires parentheses
const sayHi = () => console.log('Hello Udacity Student!');
sayHi();
Prints: Hello Udacity Student!
```
```
// multiple parameters requires parentheses
const orderIceCream = (flavor, cone) => console.log(`Here's your ${flavor} ice cream in a ${cone} cone.`);
orderIceCream('chocolate', 'waffle');
Prints: Here's your chocolate ice cream in a waffle cone.
```

## Concise and block body syntax
The concise syntax:

- has no curly braces surrounding the function body
- and automatically returns the expression.

If you need more than just a single line of code in your arrow function's body, then you can use the "block body syntax".
```
const upperizedNames = ['Farrin', 'Kagure', 'Asser'].map( name => {
  name = name.toUpperCase();
  return `${name} has ${name.length} characters in their name`;
});
```
Important things to keep in mind with the block syntax:

- it uses curly braces to wrap the function body
- and a return statement needs to be used to actually return something from the function.

## "this" and Regular Functions

The value of the this keyword is based completely on how its function (or method) is called. this could be any of the following:

1. A new object
If the function is called with new:
```
const mySundae = new Sundae('Chocolate', ['Sprinkles', 'Hot Fudge']);
```
In the code above, the value of this inside the Sundae constructor function is a new object because it was called with new.

2. A specified object
If the function is invoked with ```call/apply```:
```
const result = obj1.printName.call(obj2);
```
In the code above, the value of this inside ```printName()``` will refer to ```obj2``` since the first parameter of ```call()``` is to explicitly set what this refers to.

3. A context object
If the function is a method of an object:
```
data.teleport();
```
In the code above, the value of ```this``` inside ```teleport()``` will refer to ```data```.

4. The global object or undefined
If the function is called with no context:

```teleport();```
In the code above, the value of this inside ```teleport()``` is either the global object or, if in strict mode, it's undefined.

TIP: ```this``` in JavaScript is a complicated topic. We just did a quick overview, but for an in-depth look at how ```this``` is determined, check out {this All Makes Sense Now!] (https://github.com/getify/You-Dont-Know-JS/blob/master/this%20%26%20object%20prototypes/ch2.md) from Kyle Simpson's book series [You Don't Know JS] (https://github.com/getify/You-Dont-Know-JS/blob/master/README.md).