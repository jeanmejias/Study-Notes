# CLASSES AND OBJECTS

**Creating an object:**
const Car = {
	model: 'Polo',
	brand: 'wokswagen',
	type: 'petrol',
	use: function() {
	console.log (this.model + 'is for driving')
}
}

## Constructor Functions 

```new SoftwareDeveloper();```

What does make SoftwwareDeveloper() a constructor function are:
- The use of the ```new``` operator to invoke the function
-How the function is coded internally.

## Constructor Functions: Structure and Syntax
This is what the internals of a constructor function looks like:

```function SoftwareDeveloper() {
  this.favoriteLanguage = 'JavaScript';
}```
 
 **this** refers to the new object that was created by using the **new** keyword in front of the constructor function. 

 - ** Constructor functions in JavaScript should not have an explicit return value (i.e., there should not be ```return``` statement).**

## Creating a New Object

```function SoftwareDeveloper() {
  this.favoriteLanguage = 'JavaScript';
} 

let developer = new SoftwareDeveloper();

console.log(developer);
SoftwareDeveloper {favoriteLanguage: 'JavaScript'.```

## Constructor Functions Can Have Parameters

```function SoftwareDeveloper(name) {
  this.favoriteLanguage = 'JavaScript';
  this.name = name;
}```

In the updated ```SoftwareDeveloper()``` function, whatever value is passed into the function will be the value of the object's name property. Let's check it out:

```let instructor = new SoftwareDeveloper('Andrew');

console.log(instructor);
// SoftwareDeveloper { favoriteLanguage: 'JavaScript', name: 'Andrew' } ```

Great! And as we've seen above, we can create different objects using the same constructor. Let's call the same constructor function but pass a different argument this time:

```let teacher = new SoftwareDeveloper('Richard');
console.log(teacher);
// SoftwareDeveloper { favoriteLanguage: 'JavaScript', name: 'Richard' }```

## exercise 

```/*

Now it's your turn to create a constructor function. Declare a
`Sandwich` constructor function that takes three parameters:

1. `bread` (string) - the type of bread for the sandwich (e.g. "Wheat")
2. `meat` (array) - the meats to put on the sandwich
   (e.g. `[]` for a vegetarian sandwich!)
3. `vegetables` (array) - the vegetables to include in the sandwich

*/

function Sandwich (bread, meat, vegetables) {
    this.bread = bread;
    this.meat = meat;
    this.vegetables = vegetables;
   }
   
   const ingredientes = new Sandwich('wheat',['beef','chicken','pork'],['tomato','onion','cucumber']);
   
   
   console.log(ingredientes);```
   
   ## Further Research 
   
   [The new operator] (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new).
   [The instanceOf operator] (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/instanceof).
