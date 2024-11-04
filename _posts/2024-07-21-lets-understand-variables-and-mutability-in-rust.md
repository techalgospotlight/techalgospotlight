---
title: "Let’s Understand Variables and Mutability in Rust"
excerpt: "Learn how to declare variables and use mutability in Rust. This guide covers the essential concepts and code examples to help you understand Rust variables and mutability."
date: July 21, 2024
layout: post
author: neha
categories:
    - rust
image: assets/techalgospotlight-rust-banner.webp
keywords: rust, variables, mutability, rust programming language, rust tutorial, rust for beginners
published: true
---

In every programming language, We used variables for storing data. Let’s see one example.

In the above code, x is the name of the variable that stores the value **1**.

We can think of variables that can hold information.

* * *

How can we declare a variable in Rust?
--------------------------------------

We use the **let** keyword to declare a variable in Rust.

In the above code, we have created a variable named **age** with a value of **30**.

### Example: Rust Variables

```rs
fn main() {
    // variable to store integer value
    let age = 30;
    println!("Age: {}", age);

    // variable to store floating-point value
    let salary = 342523.23;
    println!("Salary: {}", salary);

    // variable to store string
    let name = "TechAlgoSpotlight";
    println!("Name: {}", name);
}
```


#### Output

```txt
Age: 30
Salary: 342523.23
Name: TechAlgoSpotlight
```


In the above coding example, we have created three variables:

*   age – to store an integer value
*   salary – to store floating-point data
*   name – to store a string

**Also, We have used the println! macro for printing variables.**

To learn more about **println!** ?, visit Rust Print Output.

* * *

Let’s Change The Value of a Variable
------------------------------------

Variables are immutable in Rust, Which means we cannot change the value of a variable once it’s defined. Let’s see an example,

```rs
fn main() {
    // declare a variable with value 1
    let x = 0;
    println!("x = {}", x);

    // change the value of variable x
    x = 10;
    println!("x = {}", x);
}
```


When we run this code, we will get an error. This is because we are trying to change the value of the x variable from **0** to **10**.

```rs
error[E0384]: cannot assign twice to immutable variable `x`
 --> main.rs:7:5
  |
3 |     let x = 0;
  |         -
  |         |
  |         first assignment to `x`
  |         help: consider making this binding mutable: `mut x`
...
7 |     x = 10;
  |     ^^^^^ cannot assign twice to immutable variable
```


To solve this problem, Rust allows us to create mutable variables.

* * *

Create Mutable Variable in Rust
-------------------------------

To make variables mutable, We use the **mut** keyword in rust before the variable name. Let’s take an example.

Here, x is a mutable variable. Now we can change the value of x.

### Example: Mutable Variables

```rs
fn main() {
    // declare a mutable variable with value 1
    let mut x = 1;
    println!("Value of x = {}", x);

    // change the value of variable x
    x = 2;
    println!("Updated value of x = {}", x);
}
```


#### Output

```txt
Value of x = 1
Updated value of x = 2
```


* * *

How to Naming Variables in Rust
-------------------------------

Rust is a case-sensitive language. Hence, lowercase variables and uppercase variables are different. For example,

*   age is different from the AGE.
*   _**name**_ is different from the Name.

Rust Variables must start with either a letter or an underscore.

```rs
let age = 30;     	// valid and good practice
let _age = 30;    	// valid variable 
let 1age = 30;    // inavlid variable
```


Rust Variable names can only contain letters, digits and an underscore character.

```rs
let age1 = 31;        // valid variable
let age_num = 31;     // valid variable
let s@lary = 52352;   // invalid variable
```


Use underscore if we need to use two words as variable names.

```rs
let first name = "TechAlgoSpotlight";    // invalid variable
let first_name = "TechAlgoSpotlight";    // valid variable
let first-name = "TechAlgoSpotlight";    // invalid variable
```


* * *

All about Rust Constants
------------------------

Constant is a special type of variable, Whose value cannot be changed. We use the const to create constants in Rust.

```rs
fn main() {
    // declare a float constant
    const PI: f32 = 3.14;

    println!("Value of PI = {}", PI);
}
```


#### Output:

In the above coding example, We declared a constant PI with a value of 3.14. Now, the value of PI can’t be changed throughout the program.

Let’s see what happens if we try to change the value of a constant.

```rs
fn main() {
    // declare a constant
    const PI:f32 = 3.14;
    println!("Initial Value of PI: {}", PI);

    // change value of PI
    PI = 202.2;
    println!("Update Value of PI: {}", PI);
}
```


When we run this code, we will get an error because PI is a constant.

```rs
error[E0070]: invalid left-hand side of assignment
 --> main.rs:7:8
  |
7 |     PI = 202.2;
  |     -- ^
  |     |
  |     cannot assign to this expression
```

* * *

Conclusion
----------

In the upcoming article, We will deep dive into Rust Data Types. Meanwhile, You can check the previous Rust article on Printing anything in RUST.