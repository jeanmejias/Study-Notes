
# Sets
## How to Create a Set
```
const games = new Set();
console.log(games);
```
If you want to create a Set from a list of values, you use an array:
```
const games = new Set(['Super Mario Bros.', 'Banjo-Kazooie', 'Mario Kart', 'Super Mario Bros.']);
console.log(games);
Set {'Super Mario Bros.', 'Banjo-Kazooie', 'Mario Kart'}
```
# Exercise
```
/*
 * Programming Quiz: Using Sets (3-1)
 *
 * Create a Set object and store it in a variable named `myFavoriteFlavors`. Add the following strings to the set:
 *     - chocolate chip
 *     - cookies and cream
 *     - strawberry
 *     - vanilla
 *
 * Then use the `.delete()` method to remove "strawberry" from the set.
 */
<!--  -->
 const myFavoriteFlavors = new Set();

 myFavoriteFlavors.add('chocolate chip');
 myFavoriteFlavors.add('cookies and cream');
 myFavoriteFlavors.add('strawberry');
 myFavoriteFlavors.add('vanilla');
 myFavoriteFlavors.delete('strawberry');
 console.log(myFavoriteFlavors);
 ```


## Modifying Sets
You use the appropriately named, ```.add()``` and ```.delete()``` methods:
```
const games = new Set(['Super Mario Bros.', 'Banjo-Kazooie', 'Mario Kart', 'Super Mario Bros.']);

games.add('Banjo-Tooie');
games.add('Age of Empires');
games.delete('Super Mario Bros.');

console.log(games);
Set {'Banjo-Kazooie', 'Mario Kart', 'Banjo-Tooie', 'Age of Empires'}
```

On the other hand, if you want to delete all the items from a Set, you can use the ```.clear()``` method.

```
games.clear()
console.log(games);
Set {}
```

```.add()``` returns the ```Set``` if an item is successfully added. On the other hand, ```.delete()``` returns a ```Boolean (true or false)``` depending on successful deletion.

# Working With Sets
## Checking The Length

Use the ```.size``` property to return the number of items in a Set:
```
const months = new Set(['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December']);
console.log(months.size);
12
```
 **Remember**, Sets can’t be accessed by their index like an array, so you use the ```.size``` property instead of ```.length``` property to get the size of the Set.

# Checking If An Item Exists

Use the ```.has()``` method to check if an item exists in a Set. If the item is in the Set, then ```.has()``` will return true. If the item doesn’t exist in the Set, then ```.has()``` will return false.
```
console.log(months.has('September'));
true
```
# Retrieving All Values
Finally, use the ```.values()``` method to return the values in a Set. The return value of the .values() method is a ```SetIterator object```.
```
console.log(months.values());
```

# Using the SetIterator
Because the ```.values()``` method returns a new iterator object (called ```SetIterator```), you can store that iterator object in a variable and loop through each item in the Set using ```.next()```.
```
const iterator = months.values();
iterator.next();
Object {value: 'January', done: false}
```
And if you run ```.next()``` again?
```
iterator.next();
Object {value: 'February', done: false}
```
And so on until done equals true which marks the end of the Set.

## Using a for...of Loop
An easier method to loop through the items in a Set is the ```for...of loop```.
```
const colors = new Set(['red', 'orange', 'yellow', 'green', 'blue', 'violet', 'brown', 'black']);
for (const color of colors) {
  console.log(color);
}
red 
orange 
yellow 
green 
blue 
violet 
brown 
black
```

#What is a WeakSet?

1. a WeakSet can only contain objects
2. a WeakSet is not iterable which means it can’t be looped over
3. a WeakSet does not have a ```.clear()``` method

You can create a WeakSet just like you would a normal Set, except that you use the WeakSet constructor.
```
let student1 = { name: 'James', age: 26, gender: 'male' };
let student2 = { name: 'Julia', age: 27, gender: 'female' };
let student3 = { name: 'Richard', age: 31, gender: 'male' };

const roster = new WeakSet([student1, student2, student3]);
console.log(roster);
```
**What makes this so useful is you don’t have to worry about deleting references to deleted objects in your WeakSets, JavaScript does it for you! When an object is deleted, the object will also be deleted from the WeakSet when garbage collection runs. This makes WeakSets useful in situations where you want an efficient, lightweight solution for creating groups of objects.**

# Creating & Modifying Maps
## How to Create a Map
```
const employees = new Map();
console.log(employees);
```

# Modifying Maps
Unlike Sets, you can’t create Maps from a list of values; instead, you add key-values by using the Map’s ```.set()``` method.
```
const employees = new Map();

employees.set('james.parkes@udacity.com', { 
    firstName: 'James',
    lastName: 'Parkes',
    role: 'Content Developer' 
});
employees.set('julia@udacity.com', {
    firstName: 'Julia',
    lastName: 'Van Cleve',
    role: 'Content Developer'
});
employees.set('richard@udacity.com', {
    firstName: 'Richard',
    lastName: 'Kalehoff',
    role: 'Content Developer'
});

console.log(employees);
Map {'james.parkes@udacity.com' => Object {...}, 'julia@udacity.com' => Object {...}, 'richard@udacity.com' => Object {...}}
```
```.has()``` method to check if a key-value pair exists in your Map by passing it a key.
And you can also retrieve values from a Map, by passing a key to the ```.get()``` method.

# Looping Through Maps
1. Step through each key or value using the Map’s default iterator
2. Loop through each key-value pair using the new for...of loop
3. Loop through each key-value pair using the Map’s .forEach() method

1. 
```
let iteratorObjForKeys = members.keys();
iteratorObjForKeys.next();
Object {value: 'Evelyn', done: false}
```
```
let iteratorObjForValues = members.values();
iteratorObjForValues.next();
```
and so on

2. 
```
const members = new Map();

members.set('Evelyn', 75.68);
members.set('Liam', 20.16);
members.set('Sophia', 0);
members.set('Marcus', 10.25);

for (let [key, value] of members) {
    console.log(key, value);
}
```

3. 
```
members.forEach((value, key) => console.log(key, value));
```

# What is a WeakMap?
A WeakMap is just like a normal Map with a few key differences:

1. a WeakMap can only contain objects as keys,
2. a WeakMap is not iterable which means it can’t be looped and
3. a WeakMap does not have a .clear() method.

# Promises 

```
const myFirstPromise = new Promise((resolve, reject) => {
  // do something asynchronous which eventually calls either:
  //
  //   resolve(someValue); // fulfilled
  // or
  //   reject("failure reason"); // rejected
});
```

resolve
```
new Promise(function (resolve, reject) {
    window.setTimeout(function createSundae(flavor = 'chocolate') {
        const sundae = {};
        // request ice cream
        // get cone
        // warm up ice cream scoop
        // scoop generous portion into cone!
        resolve(sundae);
    }, Math.random() * 2000);
});
```

reject
```
new Promise(function (resolve, reject) {
    window.setTimeout(function createSundae(flavor = 'chocolate') {
        const sundae = {};
        // request ice cream
        // get cone
        // warm up ice cream scoop
        // scoop generous portion into cone!
        if ( /* iceCreamConeIsEmpty(flavor) */ ) {
            reject(`Sorry, we're out of that flavor :-(`);
        }
        resolve(sundae);
    }, Math.random() * 2000);
});
```
**The first thing to understand is that a Promise will immediately return an object.**

That object has a ```.then()``` method on it that we can use to have it notify us if the request we made in the promise was either successful or failed. The ```.then()``` method takes two functions:

1. the function to run if the request completed successfully
2. the function to run if the request failed to complete

```
mySundae.then(function(sundae) {
    console.log(`Time to eat my delicious ${sundae}`);
}, function(msg) {
    console.log(msg);
    self.goCry(); // not a real method
});
```

[Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise). 

[Promises course](https://eu.udacity.com/course/javascript-promises--ud898). 

# Proxies 

To create a proxy object, we use the Proxy constructor - ```new Proxy();```.

## ```.Get()``` Trap 

```
const richard = {status: 'looking for work'};
const handler = {
    get(target, propName) {
        console.log(target);
        console.log(propName);
        return target[propName];
    }
};
const agent = new Proxy(richard, handler);
agent.status; // (1)logs the richard object, (2)logs the property being accessed, (3)returns the text in richard.status
```

** Notice we added the ```return target[propName];``` as the last line of the get trap. This will access the property on the target object and will return it.**

The ```set``` trap is used for intercepting code that will change a property. The set trap receives: the object it proxies the property that is being set the new value for the proxy
```
const richard = {status: 'looking for work'};
const handler = {
    set(target, propName, value) {
        if (propName === 'payRate') { // if the pay is being set, take 15% as commission
            value = value * 0.85;
        }
        target[propName] = value;
    }
};
const agent = new Proxy(richard, handler);
agent.payRate = 1000; // set the actor's pay to $1,000
agent.payRate; // $850 the actor's actual pay
```

## Other Traps
So we've looked at the get and set traps (which are probably the ones you'll use most often), but there are actually a total of 13 different traps that can be used in a handler!

[the get trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/get) - lets the proxy handle calls to property access
[the set trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/set) - lets the proxy handle setting the property to a new value
[the apply trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/apply) - lets the proxy handle being invoked (the object being proxied is a function)
[the has trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/has) - lets the proxy handle the using in operator
[the deleteProperty trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/deleteProperty) - lets the proxy handle if a property is deleted
[the ownKeys trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/ownKeys) - lets the proxy handle when all keys are requested
[the construct trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/construct) - lets the proxy handle when the proxy is used with the new keyword as a constructor
[the defineProperty trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/defineProperty) - lets the proxy handle when defineProperty is used to create a new property on the object
[the getOwnPropertyDescriptor trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/getOwnPropertyDescriptor) - lets the proxy handle getting the property's descriptors
[the preventExtenions trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/preventExtensions) - lets the proxy handle calls to Object.preventExtensions() on the proxy object
[the isExtensible trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/isExtensible) - lets the proxy handle calls to Object.isExtensible on the proxy object
[the getPrototypeOf trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/getPrototypeOf) - lets the proxy handle calls to Object.getPrototypeOf on the proxy object
[the setPrototypeOf trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/getPrototypeOf) - lets the proxy handle calls to Object.setPrototypeOf on the proxy object

As you can see, there are a lot of traps that let the proxy manage how it handles calls back and forth to the proxied object.

## With ES6 Proxies, we do not need to know the properties beforehand:
```
const proxyObj = new Proxy({age: 5, height: 4}, {
    get(targetObj, property) {
        console.log(`getting the ${property} property`);
        console.log(targetObj[property]);
    }
});

proxyObj.age; // logs 'getting the age property' & 5
proxyObj.height; // logs 'getting the height property' & 4
All well and good, just like the ES5 code, but look what happens when we add a new property:

proxyObj.weight = 120; // set a new property on the object
proxyObj.weight; // logs 'getting the weight property' & 120
```

# Generators
## Pausable Functions

```
function* getEmployee() {
    console.log('the function has started');

    const names = ['Amanda', 'Diego', 'Farrin', 'James', 'Kagure', 'Kavita', 'Orit', 'Richard'];

    for (const name of names) {
        console.log( name );
    }

    console.log('the function has ended');
}

getEmployee();

// this is the response I get in Chrome:
getEmployee {[[GeneratorStatus]]: "suspended", [[GeneratorReceiver]]: Window}
```
Notice the asterisk ```(i.e. *)``` right after the ```function``` keyword? That asterisk indicates that this function is actually a generator!
```
(i.e. function* name() { … })
```

## how do we get this magical, pausing functionality?

The ```yield``` keyword is new and was introduced with ES6. It can only be used inside generator functions. ```yield``` is what causes the generator to pause. Let's add ```yield``` to our generator and give it a try:
```
function* getEmployee() {
    console.log('the function has started');

    const names = ['Amanda', 'Diego', 'Farrin', 'James', 'Kagure', 'Kavita', 'Orit', 'Richard'];

    for (const name of names) {
        console.log(name);
        yield;
    }

    console.log('the function has ended');
}
const generatorIterator = getEmployee();
generatorIterator.next();

the function has started
Amanda

generatorIterator.next();
Diego
```

So we can get data out of a generator by using the yield keyword. We can also send data back into the generator, too. We do this using the ```.next()``` method:
```
function* displayResponse() {
    const response = yield;
    console.log(`Your response is "${response}"!`);
}

const iterator = displayResponse();

iterator.next(); // starts running the generator function
iterator.next('Hello Udacity Student'); // send data into the generator
// the line above logs to the console: Your response is "Hello Udacity Student"!
```


