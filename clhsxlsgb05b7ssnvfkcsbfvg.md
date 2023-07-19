---
title: "The Importance of Using try-catch in JavaScript for Graceful Error Handling"
seoTitle: "The Importance of Using try-catch in JavaScript"
seoDescription: "Learn about the importance of try-catch for error handling in JavaScript, how to use it, and the benefits it offers. Get tips on writing more efficient and"
datePublished: Thu May 18 2023 09:30:42 GMT+0000 (Coordinated Universal Time)
cuid: clhsxlsgb05b7ssnvfkcsbfvg
slug: the-importance-of-using-try-catch-in-javascript-for-graceful-error-handling
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689770361343/02a2d95a-e796-4938-a95f-8ce0d9a5434f.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1683790310455/b575499e-2d39-4bfd-82d7-8b845faff589.jpeg
tags: javascript, trycatch

---

One thing in life is sure: Everything may only sometimes go according to plan. Before riding, every biker wears a helmet. It is imperative, not mandatory, that they wear helmets for their heads' safety. The same is true for Javascript. There is no way to predict an unexpected outcome of a code or program, so we must wear our "helmets" at all times. This article explores the “helmet” of Javascript, try-catch.

<iframe src="https://giphy.com/embed/13awhIC2CcDaHC" width="480" height="336" class="giphy-embed"></iframe>

## Errors in Javascript

Errors in programming refer to mistakes or issues in the code that result in incorrect behavior or prevent it from functioning as intended. Some common types of errors include:

* Exception handling errors
    
* Logical errors
    
* Run-time errors
    
* Semantic errors
    
* Syntax errors
    

There are several ways of handling errors, including:

* Try-catch blocks to handle exceptions
    
* Return error codes
    
* Check return values
    
* Assertions
    
* Input validation
    
* Exception safety
    

In this article, we will focus on handling errors using try-catch blocks. It is important to note that not all errors can be managed using the try-catch block.

Try-catch can handle the following types of errors:

* Exceptions
    
* Logical errors
    
* Run-time errors
    

Try-catch cannot handle:

* Syntax errors
    
* Semantic errors
    
* Compile-time errors
    

As listed above, the try-catch block is only effective in handling run-time errors that are thrown when the program encounters an abnormal or unexpected situation. By combining try-catch with error-handling methods, an integrated error-handling approach can be established.

## What is try-catch?

Imagine you want to get coffee but you’re not sure they have your favorite type of coffee, an espresso. You would ask the barista for an espresso; you would “try” to get an espresso. If perhaps they don’t have an espresso, you’ll have to choose another type of coffee, let’s say a cappuccino. That’s the "catch" part.

Try-catch in Javascript is used to handle errors in code. They come in pairs. Let’s talk about each block of the statement.

### try statement:

Try statements allow you to define a block of code that will be tested for errors during execution. If any error occurs, it passes it to the catch block to handle the errors. If there is no error, it executes the code within it.

### catch statement:

This block handles the error passed down from the try block. It contains either the user-defined exception handlers or a built-in handler. The catch block is only executed if there is an error. One try block can contain one or more multiple catch blocks.

Here is an example written in code based on the example above:

```plaintext
try {
	var coffee = getMyFavoriteCoffee("espresso");
} catch (error) {
	console.log("Oh no, they don't have my favorite coffee, espresso. I'll have to try a cappuccino.");
	var coffee = "cappuccino";
}
```

By calling `getMyFavoriteCoffee("espresso")`, we're trying to get our favorite coffee, an espresso. If that function fails, for example, because espresso is not available, the program jumps to the catch block and prints a message. Instead, a cappuccino will be selected.

## Syntax of try-catch

This is the syntax and try-catch:

```plaintext
try {
	tryCode;
} catch (error) {
	catchCode;
}
```

## Why should we use try-catch

It is recommended that you incorporate try-catch blocks into your code to improve error handling, even though they are not a mandatory aspect. Remember that a helmet is not mandatory if you're riding a bike, but it's a good idea to wear one for precaution.

Let’s examine five benefits they offer:

* Try-catch lets you handle errors in a way that keeps your program running even if part of it fails. This phenomenon is called "graceful failure."
    
* Try-catch offers a centralized way of handling errors. By reducing duplication, your code becomes easier to manage and more efficient.
    
* In addition to providing a higher user experience, try-catch handles errors so that users aren't unexpectedly confronted with messages.
    
* The catch block provides information about what went wrong, making debugging easier.
    
* Developers can better understand error messages with try-catch thanks to customizable error messages.
    

## The try-catch-finally trio

A try-catch statement formally consists of a try block and either a catch block, a `finally` block, or both. We discussed earlier that the code in the try block is executed first, and if it throws an exception (an error), the code in the catch block will be executed (only because it has an unhandled exception).

The `finally` block is an optional block of statements. They are executed after the try-catch statements have been executed. Exception or not, the code in the `finally` block will be executed regardless of the output.

Try-catch-finally has the following syntax:

```plaintext
try {
	tryCode - Code block to run.
} catch (error) {
	catchCode - Code block to handle errors.
} finally {
	finallyCode - Code block to be executed regardless of the
	try result.
}
```

## Applications of try-catch

These examples illustrate the use of try-catch statements in three different applications.

### Accessing an array element.

In the following example, you can see how to access an element of an array:

```plaintext
let scores = [1, 2, 3, 4, 5];
try {
	let index = prompt("Enter an index (1-5): ");
	if (index < 0 || index > 5) {
		throw new Error("The index is out of bounds!!!");
	}
	console.log(`The number at index ${index} is ${scores[index]}.`);
} catch (error) {
	console.error("Oh no!", error.message);
}
```

Using the prompt function in the try block, it gets user input, which is then compared against the bounds of the scores array to detect errors. In the event of out-of-bounds input, an error message is thrown. The catch block then catches the error and logs an error message to the console `"Oh no!"` along with the error message.

### Loading external data.

Consider the following example:

```plaintext
try {
	let info = fetch("https:api.example.com/userinfo")
		.then(response => response.json())
		.then(data => {
			console.log("User info: ", data);
			console.log("Process is complete!");
		});
} catch (error) {
	console.error("Failed to load user info: ", error.message);
}
```

The code attempts to load user information from an external API using the `fetch method`. The fetch method returns a Promise that resolves with a Response object, which is then converted to JSON using the `json()` method. The `then()` method is used to handle the JSON data returned from the API and log it to the console using console.log().

If there are no errors, `"Process is complete!"` is logged to the console after the user information has been logged. If there is an error, it will be caught by the catch block and an error message will be logged using `console.error()`.

### Validating user input.

Let us take a look at the last application of try-catch.

```plaintext
try {
	let age = parseInt(prompt("How old are you? "));
	if (isNaN(age) || age < 0) {
		throw new Error("Invalid age! Age must be a positive number.");
	}
	console.log("Your age is: ", age);
} catch (error) {
	console.error("Oops! ", error.message);
}
```

In this example, we use a try-catch statement to handle potential errors while parsing the user's age. The try block takes the user’s age and uses `parseInt` to convert it to a number. If the input is not a number or is negative, an error is thrown with the message `"Invalid age! Age must be a positive number."`. The catch block then catches the error and logs an error message `"Oops!"` along with the error message to the console.

## Summary

The try-catch statement is a basic building block of error handling. Let’s not forget bikers wearing helmets to better understand try-catch in Javascript. The try block contains code that may throw an exception, while the catch block handles the exception that may occur.

The optional finally block contains code that will be executed regardless of whether an exception is thrown or not. The main difference between the two statements is that try-catch only catches exceptions and handles them, while try-catch-finally does that and also ensures that the code in the `finally` block is executed.

In this way, program execution is less likely to be interrupted by unexpected errors, and the code becomes more robust.

## Glossary

* Error codes: In computing, an error code, also called a return code, is a numeric or alphanumeric code that indicates the problem, why it occurred, and the cause.
    
* Exception safety: This ensures the program state remains valid even if exceptions are thrown.
    
* Logging/reporting: Logging or reporting is the act of keeping a log of events that occur in a computer system, such as problems, errors, or just information on current operations
    
* Logical errors: This term describes an error that causes it to perform incorrectly but does not cause it to terminate (or crash) improperly.
    
* Run-time errors: The term "runtime error" refers to an error that occurs when a program runs after it has been successfully compiled.
    
* Semantic errors: A semantic error is a mistake in logic or behavior that results in unintended results even when the syntax is correct.
    
* Syntax errors: This is an error in the grammar or syntax of a programming language.