---
title: "A Dummies Guide To Mastering Modules in Javascript"
seoTitle: "Master Modules in JS: A Beginner's Guide"
seoDescription: "Learn how to simplify your JavaScript codebase using modules. Modules are reusable units of code that encapsulate related code into one file."
datePublished: Thu May 11 2023 09:30:39 GMT+0000 (Coordinated Universal Time)
cuid: clhixirbx00vvpjnvdlr68brr
slug: a-dummies-guide-to-mastering-modules-in-javascript
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683788716071/5f409c8f-6efc-4538-8f57-0167e9f95f49.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1683788800739/1f22390b-f1e1-4c3b-9b11-c64f32bb061f.jpeg
tags: javascript-modules

---

Timi is moving to a new apartment. The movers are instructed to take his belongings, including his bed, couch, kitchen utensils, and other furniture, to his new apartment. After arriving at his new apartment, Timi discovers that everything is piled up in the living room, and he needs to separate each item by room. To avoid all code being written in one file, we must separate particular codes in Javascript and organize them appropriately into their respective files.

Rather than having the different dependencies layered together, we should separate them into different groups and organize them. This is what modules do. This article will provide an in-depth look at modules.

## What are modules in Javascript?

Modules are independent, reusable units of code.

Using modules, you can encapsulate related code into one unit. All functions related to a single module are contained in a file.

This allows us to build uncomplicated applications by simplifying our codebase. This is one of the major reasons frameworks and libraries leverage the module feature. Our large applications can be broken down into reusable chunks of code that carry out a few specific tasks.

## Properties of modules

* They are reusable. Modules need to be specific; they should perform a single or a group of tasks. That is the essence of creating them. Imagine we want to create a simplified banking application. With this application, users can do the following: deposit money, withdraw money, and check their account balances.
    

As a general rule, we would create this application in our `script.js` file as follows:

```javascript
// script.js
function depositMoney() {
	//code goes here
}

function withdrawMoney() {
	//code goes here
}

function checkBalance() {
	//code goes here
}

function bankingApp() {
	// code goes here
	depositMoney();
	withdrawMoney();
	checkBalance();
}
bankingApp();
```

While there are only four functions here, what happens when we need hundreds of functions in a large application? A module comes to the rescue here. The code above has been simplified using modules as shown below:

```javascript
// script.js
import depositMoney from "./depositMoney.js";
import withdrawMoney from "./withdrawMoney.js";
import checkBalance from "./checkBalance.js";
function bankingApp() {
	depositMoney();
	withdrawMoney();
	checkBalance();
}
bankingApp();
```

Each module is separated into its file as follows:

```javascript
// depositMoney.js
function depositMoney() {
	//code goes here
}
export default depositMoney;
```

```javascript
// withdrawMoney.js
function withdrawMoney() {
	//code goes here
}
export default withdrawMoney;
```

```javascript
// checkBalance.js
function checkBalance() {
	//code goes here
}
export default checkBalance;
```

As seen above, each function is placed in a separate file. To apply each function to the main function, the modules are imported into the main file (`script.js`). In the unlikely scenario that you need to check the balance in another code base, you can simply import the module instead of copying and pasting it.

* They need to be top-level items. For example, you can’t export inside a function.
    
* In a module, `this` is undefined. This is because modules use strict mode by default. In strict mode, `this` is not allowed to default to the global object like it does in non-strict mode. Instead, it remains undefined unless explicitly set by the developer. Therefore, if you need to use `this` in a module, you will need to set it explicitly or use a different approach.
    
* Modules only work with the HTTP(S) protocol.
    
* A web page opened via the file `://` protocol cannot use import or export.
    

## Export in modules

The `export` statement is used to export values (functions, objects, and primitives) to be used in other programs. The `import` keyword can then be used to import exported values into other programs.

The runtime must interpret the file as a module before it can be exported. It can be accomplished by adding `type="module"` to the `<script>` tag in HTML.

```HTML
// index.html
script type="module" src="script.js"></script>
```

It can also be accomplished by importing the script into another module. If we fail to do so, we may run into an `Uncaught SyntaxError: Unexpected Identifier` error. Additionally, note that anything exported from a module is called a public API.

There are two ways modules can be exported:

* Default export
    
* Named export
    

### Default export

You can have one default export per module, but you can have multiple named exports per module. If you have duplicate export names or you are using more than one default export, a `SyntaxError` will occur.

To demonstrate default exports, let's create a script called `greeting.js`:

```javascript
// greeting.js
const greeting = function (name) {
	console.log(`Hello, ${name}!`);
};

export default greeting;
```

In this example, the greeting function is being exported as the default export from the `greeting.js` module.

Then, in another module or file, you can import the default export by using the import statement without curly braces around the imported variable name:

```javascript
// main.js
import greeting from './greeting.js';
greeting('Alice'); // outputs "Hello, Alice!"
```

This will import the greeting function from the `greeting.js` module as the default export.

### Named export

For named exports, there are two ways to create them:

* in-line individually
    
* all at once at the bottom.
    

To demonstrate both, let’s create an `animal.js`:

* In-line individually
    

```javascript
// animal.js
export const animalName = "Giraffe";
export const binomialName = "Giraffa camelopardalis";
export const animalClass = "Mammalia";
```

* All at once at the bottom
    

```javascript
// animal.js
const animalName = "Giraffe";
const binomialName = "Giraffa camelopardalis";
const animalClass = "Mammalia";
export {animalName, binomialName, animalClass};
```

Modules can export values before the value itself is declared. For example:

```javascript
export {y} 
const y = 5;
```

This works because `export` is only a declaration and doesn't utilize the value of `y`.

## Import in modules

Importing functionality from other modules is possible with the `import` statement. Similar to the `export` statement, the runtime must interpret the file as a module before it can be exported.

There are two ways modules can be imported:

* Default import
    
* Named import
    

### Default import

This is the syntax for importing from a default export.

```javascript
import defaultExport from "./module.js";
```

Let’s take a look at the following example:

```javascript
// animalInfo.js
export default {
	animalName: 'Lion',
	binomialName: 'Panthera leo',
	animalClass: 'Mammalia'
}
```

```javascript
// main.js
import animalInfo.js from "./animalInfo.js"
let animalText = `Animal Information: ${animalInfo.animalName}; ${animalInfo.binomialName}; ${animalInfo.animalClass}`;
```

In this example, `animalInfo.js` exports a default object that contains information about a lion. The `main.js` file imports this object using the import statement and assigns it to the `animalInfo` variable.

Note that when importing a default export, you don't need to use curly braces around the imported name. Instead, you can give it any name you want (in this case, `animalInfo`), and the exported object will be assigned to it.

### Named import

For a named import, this is the syntax for importing from a named export.

```Javascript
import { namedExport1, namedExport2 } from './module.js';
```

`{ namedExport1, namedExport2 }` is an object destructuring syntax used to extract specifically named exports from the `module.js` module?

Always remember that if you have many named exports from a module, you can use the `*` operator to import all named exports as a single object:

```javascript
import * as moduleExports from './module.js';
```

Let's take a look at the following example:

```javascript
// animalInfo.js
export const animalName = 'Lion';
export const binomialName = 'Panthera leo';
export const animalClass = 'Mammalia';
```

Let’s import two named exports from `animalInfo.js`:

```javascript
// animalInfo.js
import {
	animalName,
	binomialName
} from "./animalInfo.js"
let animalText = `Animal Information: ${animalName}; ${binomialName};`
```

The import statement uses the named import syntax to selectively import only the `animalName` and `binomialName` variables from the `./animalInfo.js` module.

## Renaming imports and exports

Modules can rename imports and exports. Renaming them to anything we want is completely up to us. Here are ways we can accomplish this.

* Renaming module imports Suppose we have a module named `myModule.js` that contains the following function:
    

```javascript
// myModule.js
export function greet(name) {
	console.log(`Hello, ${name}!`);
}
```

Now, let's say we want to import this function into another module called `main.js`, but we want to give it a different name. We can use the `as` keyword to rename the import:

```javascript
// main.js
import { greet as sayHello } from './myModule.js';
sayHello('John'); // Outputs: "Hello, John!"
```

In this example, we renamed the imported `greet` function to `sayHello` using the `as` keyword.

* Renaming module exports Suppose we have a module named `myModule.js` that exports an object with a `greet` function:
    

```javascript
// myModule.js
function greet(name) {
  console.log(`Hello, ${name}!`);
}

export default {
  greet
};
```

Now, let's say we want to export the `greet` function directly from `myModule.js`, but we want to give it a different name. We can use the `as` keyword to rename the export:

```javascript
function sayHello(name) {
  console.log(`Hello, ${name}!`);
}

export { sayHello as greet };
```

In this example, we renamed the exported `sayHello` function to `greet` using the `as` keyword. Now, when another module imports greet from `myModule.js`, it will actually receive the `sayHello` function.

Next, we'll explore how the modules can be used.

## Application of modules

To better understand everything we have learned so far, let's take a look at the following example.

### Displaying animal information using modules

For this animal example, we will create two modules: `animal.js` and `animalInfo.js`.

`animal.js` will hold the information about the animal and `animalInfo.js` displays the information about the animal in a single sentence.

Let's start with our HTML file, `index.html`.

```HTML
// index.html
<!DOCTYPE html>
<html lang="en">

<head>
	<meta charset="UTF-8" />
	<meta http-equiv="X-UA-Compatible" content="IE=edge" />
	<meta name="viewport" content="width=device-width, initial-scale=1.0" />
	<title>Example of Modules: Animal</title>
</head>

<body>
	<h1>Example Of Modules: Animals</h1>
	<p id="demo"></p>
	<script type="module" src="./script.js"></script>
</body>

</html>
```

As seen above, the `script` type is set to `module` as discussed earlier to avoid `Uncaught SyntaxError: Unexpected Identifier` error.

Moving to the modules, create a module folder and place all your modules in that folder as follows:

```plaintext
index.html
script.js
modules/
    animal.js
    animalInfo.js
```

`animal.js` holds the animal's information as shown below:

```javascript
// animal.js
export const animalName = "Lizard";
export const binomialName = " Lacertilia";
export const animalClass = "Reptilia";
```

Let's move on to the `animalInfo.js` module:

```javascript
// animalInfo.js
import {
	animalClass,
	animalName,
	binomialName
} from "./animal.js";

const animalInfo = function () {
	const message = `Animal name: ${animalName}. Binomial name: ${binomialName}. Class: ${animalClass}`;
	document.getElementById("demo").innerHTML = message;
};
export default animalInfo;
```

The `animalInfo` is exported using default export. The `animalName`, `binomialName` and `animalClass` variables will be imported by `animalInfo.js` because without the import (which is named import in the `animalInfo.js`), the variables remain private to `animal.js`.

For `script.js`, `animalInfo` is imported using the default import:

```javascript
// script.js
import animalInfo from "./modules/animalInfo.js";
animalInfo();
```

This is the output:

![](https://i.imgur.com/3YVFzL3.png align="left")

## Summary

Modules play a vital role in JavaScript development. In addition to making it easier to maintain complex applications, they organize and reuse code logically. We explored what modules are, how to create and use them, and the different types available in this article. By using modules in your code, you can improve code structure, reduce duplication, and make your code more maintainable. The more you work with modules, the more efficient and reliable your code will be.

## Glossary

* Dependency: A dependency is a relationship between modules. A module is said to depend on another module when it needs a piece from it.