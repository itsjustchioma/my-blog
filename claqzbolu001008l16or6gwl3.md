---
title: "Demystifying JavaScript Equality Operators: = vs == vs ==="
seoTitle: "= vs == vs === in javascript"
seoDescription: "= vs == vs === in javascript
javascript assignment operator
javascript equality operator
javascript strict equality operator 
difference between = == ==="
datePublished: Mon Nov 21 2022 16:05:21 GMT+0000 (Coordinated Universal Time)
cuid: claqzbolu001008l16or6gwl3
slug: demystifying-javascript-equality-operators-vs-vs
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689771500833/e7f97a78-0fdb-4610-96dd-919abb568acc.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1689771321570/62c04ba5-f471-492a-90d8-39b5d6bd5306.png
tags: javascript, equality-operator-in-javascript, strict-equality-operator, assignment-operator

---

Javascript developers are faced with this question more often than not and can’t answer it. In this article, I’ll explain the differences between each of them.

## What is “=”? 

It is called an ***assignment operator*** because it is used to ***assign*** a value to a variable. That’s easy to remember.

> It’s an assignment operator because it is used to assign/give a value to a variable.

### “=” example

Let’s create a variable, ```x```. If we want to give ```x``` a value of ```10```, we would do the following: 

```let x = 10;```
That’s it! 

Let’s try to assign a value ```y``` to the ```x``` variable we created above:

```let y = x;```

The output is ```10```. 

It’s as easy as that! 

## What is “==”? 

1.	This is the ***equality operator***. It determines whether two operands are equal, and yields a Boolean result.

2.	It tries to convert operands of different types, unlike the strict equality operator (===). After converting the arguments to numbers, the equality operator evaluates them.

### “==” example

Take a look at the following example:

``` console.log("4" == 4); ```

This returns ```true``` because ```”4”``` is converted to a number, making it,

``` console.log(4 == 4); ```, which is true.

Examine the following and without scrolling, identify which is true and false:
1.	``` console.log("1" == 1); ```
2.	```console.log("0" == 0); ```
3.	```console.log(1 == 1); ```
4.	```console.log(0 == false);```
5.	```console.log("NaN" == NaN); ```
6.	```console.log(NaN == NaN); ``` 

Here are the answers: 
1.	True 
2.	True
3.	True
4.	True => The string zero "0" is converted to the Number data type, and the boolean false is converted to the Number data type.
5.	False 
6.	False

## What is “===”?

This is the ***strict equality operator**.* Similar to the equality operator, it checks whether two operands are equal and yields a Boolean result. It does not convert the data types of operands, therefore returns false for values that are not of a similar data type.

#### Note:
If operand(s): 

•	are different types => return false

•	are both objects => return true (only if both operands are objects and both refer to the same object)

•	are null or undefined => return true

•	is either NaN => return false

### “===” example.


![smallerimg.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1669045503567/LV4-xv_xR.png align="left")

## Differences between =, == & ===.

<table>
  <tr>
    <td>** Parameters **</td>
    <td>** = **</td>
    <td>** == **</td>
    <td>** === **</td>
  </tr>
<tr>
    <td>1. Name</td>
    <td>Assignment operator</td>
    <td>Equality operator</td>
    <td>Strict equality operator</td>
  </tr>
<tr>
    <td>2. Function</td>
    <td>Assigns a value to a variable.</td>
    <td>Checks if two operands are equal, but ignore the data type of the variable. </td>
    <td>Checks if two operands are equal, but checks the data type of the variable.</td>
  </tr>
<tr>
    <td>3. Return Value</td>
    <td>It doesn’t return true or false</td>
    <td>Returns true if the two operands are equal, and false if they are not.</td>
    <td>Returns true only if data types and operands are equal.</td>
  </tr>
</table>

### Glossary: 

#### 1.	Variable: 

It is the name of a storage location. It can also be defined as a container for storing values. For example, 

```x = 5```; 

```x``` is the variable.

#### 2.	Operand: 

This is something that is operated on (such as a quantity or data). For example, 

```5 == 5```; 

```5```  is the operand.

#### 3.	Boolean: 
It represents one of two values: ```true``` or ```false```.

## Thanks for reading!

Thank you for reading my blog. Please give it a like if you learned anything. If you would like to connect, feel free to find me on [Twitter](https://twitter.com/itsjustchioma), [GitHub](https://github.com/itsjustchioma), [Medium](https://medium.com/@itsjustchioma), and [Hashnode](https://itsjustchioma.hashnode.dev/). 

*** Ciao! ***


