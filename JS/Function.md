
# Arrow functions
Arrow functions are very similiar to regular functions in behavior,but are quite different syntactically. 

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

TIP: ```this``` in JavaScript is a complicated topic. We just did a quick overview, but for an in-depth look at how ```this``` is determined, check out [this All Makes Sense Now!] (https://github.com/getify/You-Dont-Know-JS/blob/master/this%20%26%20object%20prototypes/ch2.md) from Kyle Simpson's book series [You Don't Know JS] (https://github.com/getify/You-Dont-Know-JS/blob/master/README.md).

# Default function parameters
- ES6 has introduced a new way to create defaults. It's called default function parameters.

```
function greet(name = 'Student', greeting = 'Welcome') {
  return `${greeting} ${name}!`;
}

greet(); // Welcome Student!
greet('James'); // Welcome James!
greet('Richard', 'Howdy'); // Howdy Richard!
```
To create a default parameter, you add an equal sign ( = ) and then whatever you want the parameter to default to if an argument is not provided.

```
Take a look at the following code:

function shippingLabel(name, address) {
  name = (typeof name !== 'undefined') ? name : 'Richard';
  address = (typeof address !== 'undefined') ?  address : 'Mountain View';
  return `To: ${name} In: ${address}`;
}
```

```
function ShippingLabel( name ='Richard', address = 'Mountain View') {
	return `To: ${name} In: ${address}`;
}
```

# Defaults and destructuring arrays
```
function createGrid([width = 5, height = 5]) {
  return `Generates a ${width} x ${height} grid`;
}

createGrid([]); // Generates a 5 x 5 grid
createGrid([2]); // Generates a 2 x 5 grid
createGrid([2, 3]); // Generates a 2 x 3 grid
createGrid([undefined, 3]); // Generates a 5 x 3 grid

createGrid(); // throws an error
```

```
function createGrid([width = 5, height = 5] = []) {
  return `Generates a ${width} x ${height} grid`;
}
createGrid(); // Generates a 5 x 5 grid
```

# ES5 "Class" Recap
```
function Plane(numEngines) {
  this.numEngines = numEngines;
  this.enginesActive = false;
}

// methods "inherited" by all instances
Plane.prototype.startEngines = function () {
  console.log('starting engines...');
  this.enginesActive = true;
};

const richardsPlane = new Plane(1);
richardsPlane.startEngines();

const jamesPlane = new Plane(4);
jamesPlane.startEngines();
```

# ES6 Classes
Here's what that same Plane class would look like if it were written using the new class syntax:
```
class Plane {
  constructor(numEngines) {
    this.numEngines = numEngines;
    this.enginesActive = false;
  }

  startEngines() {
    console.log('starting engines…');
    this.enginesActive = true;
  }
}
```
# Super and Extends
## Subclasses with ES6
Now that we've looked at creating classes in JavaScript. Let's use the new super and extends keywords to extend a class.

```
class Tree {
  constructor(size = '10', leaves = {spring: 'green', summer: 'green', fall: 'orange', winter: null}) {
    this.size = size;
    this.leaves = leaves;
    this.leafColor = null;
  }

  changeSeason(season) {
    this.leafColor = this.leaves[season];
    if (season === 'spring') {
      this.size += 1;
    }
  }
}

class Maple extends Tree {
  constructor(syrupQty = 15, size, leaves) {
    super(size, leaves);
    this.syrupQty = syrupQty;
  }

  changeSeason(season) {
    super.changeSeason(season);
    if (season === 'spring') {
      this.syrupQty += 1;
    }
  }

  gatherSyrup() {
    this.syrupQty -= 3;
  }
}

const myMaple = new Maple(15, 5);
myMaple.changeSeason('fall');
myMaple.gatherSyrup();
myMaple.changeSeason('spring');
```
Both ```Tree``` and ```Maple``` are JavaScript classes. The Maple class is a "subclass" of ```Tree``` and uses the ```extends``` keyword to set itself as a "subclass". To get from the "subclass" to the parent class, the ```super``` keyword is used. Did you notice that super was used in two different ways? In ```Maple```'s constructor method, ```super``` is used as a function. In ```Maple```'s ```changeSeason()``` method, ```super``` is used as an object!

#Exercise 
##Directions:
Create a Bicycle subclass that extends the Vehicle class. The Bicycle subclass should override Vehicle's constructor function by changing the default values for wheels from 4 to 2 and horn from 'beep beep' to 'honk honk'.
```
/*
 * Programming Quiz: Building Classes and Subclasses (2-3)
 */

class Vehicle {
	constructor(color = 'blue', wheels = 4, horn = 'beep beep') {
		this.color = color;
		this.wheels = wheels;
		this.horn = horn;
	}

	honkHorn() {
		console.log(this.horn);
	}
}

// your code goes here
class Bicycle extends Vehicle {
	constructor (color ='blue', wheels = 2, horn='honk honk') {
	    super (color,wheels,horn);
	    this.wheels = wheels;
	    this.horn = horn;
	   
	}
	}

const myVehicle = new Vehicle();
myVehicle.honkHorn(); // beep beep
const myBike = new Bicycle();
myBike.honkHorn(); // honk honk
```
