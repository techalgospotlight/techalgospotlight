---
title: "Type Casting in Rust"
excerpt: "Learn how to perform type casting in Rust using the as keyword. This guide covers type casting examples for different data types, including int to float, float to double, int to char, char to int, and bool to int."
date: Sept 10, 2024
layout: post
author: neha
categories:
    - rust
image: assets/techalgospotlight-rust-banner.webp
keywords: rust type casting, rust as keyword, rust type conversion, rust type casting examples 
published: true
tags: featured
---

In Rust or any other programming language, Type Casting plays an important role. But today we will deep dive into type casting in rust. Mostly In one datatype to another datatype and vice versa. Maybe you have to convert **Int to Float** or **Float to Double**. But here in the rust, type-casting works a little differently. they introduced **as** keyword.

Let me take a small example.

```rs
// create a floating-point variable
let decimal: f64 = 43.210;

// convert floating point type to integer type
let integer = decimal as u16;
```


In the above example, The **f64** type converts to **u16** and we used **as** keyword for type conversion. This example is a little small, Let me share a complete coding example.

* * *

Rust Type Casting: Example
--------------------------

```rs
fn main() {
    // assign a floating point f64 value to decimal variable
    let decimal: f32 = 55.31;

    // convert decimal variable to u16 integer type using as keyword
    let integer = decimal as u16;

    println!("decimal = {}", decimal);
    println!("integer = {}", integer);
}
```


What do you think, What would be our output? 🤔🤔

### Output

```rs
decimal = 55.31
integer = 55
```


Here, We are converting decimal f32 floating values to u16 integer values. And one more thing, We are doing this explicitly, So, we are considered as **Explicit Type Casting**. 🤟

* * *

Rust Int to Char Type Casting
-----------------------------

As you know now, in Rust we are using **as** keyword for typecasting. But We can use **as** keyword for the **Int to char** type conversion.

```rs
fn main() {
    // only u8 integer data type can be converted into char
    let integer: u8 = 66;
  
    // convert integer to char using the as keyword
    let character = integer as char;

    println!("integer : {}" , integer);
    println!("character : {}", character);
}
```


### Output

```rs
integer : 66
character : B
```


Every char has a Unicode in the programming language. So, When we convert int to char, This was converted into Unicode format because **int 66** has **Unicode B**. And we got out as **B**.

Do you think, In every scenario int to char will work? **NO**. Let’s see why.

### Error While Int to Char Type Casting

The reason behind this is we are only allowed to use **u8** integers for type casting from **int to char**. But when we use other integers for type casting by default error will show up. Let’s see how this happens.

```rs
fn main() {
    let integer: i32 = 66;
  
    // convert integer to char using the as keyword
    let character = integer as char;

    println!("integer : {}" , integer);
    println!("character : {}", character);
}
```

#### Type Casting Error:

```rs
error[E0604]: only `u8` can be cast as `char`, not `i32`
 --> main.rs:5:19
  |
5 |   let character = integer as char;
  |                   ^^^^^^^^^^^^^^^ invalid cast
```


Why we are getting errors? Because Unicode values are **smaller integers** and its not fit in the range of **u8**. And we used **i32 datatypes**. Hope you got my point. 😁😁

We tried to convert **int to char**, So do this reverse by **char to int** 😁

* * *

Rust Char to Int Type Casting
-----------------------------

```rs
fn main() {
    let character: char = 'B';

    // convert char type to u8 integer type
    let integer = char as u8;

    println!("character : {}", character);
    println!("integer : {}", integer);
}
```

### Output:

```rs
character : B
integer : 66
```


This time it is working fine! Why, Because Unicodes are standards (code points) and Internally they store numeric values. So, that **char to int** works smoothly.

**Are you ready for a little heavy type casting?** 😎😎

* * *

Rust Bool to Int Type Casting
-----------------------------

It looks weird Because in day-to-day life we never do this type of casting. Let’s see if this how this is happening in Rust.

```rs
fn main() {
    let bool1: bool = false;
    let bool2: bool = true;
  
    // convert boolean type to integer
    let int1 = boolean1 as i32;
    let int2 = boolean2 as i32;

    println!("bool1 = {}", boolean1);
    println!("bool1 = {}", boolean2);
    println!("int1 = {}", integer1);
    println!("int2 = {}", integer2);
}
```

### **Output:**

```rs
bool1 = false
bool1 = false
int1 = 0
int2 = 1
```

As expected, Booleans only support **true** and **false**. So, they respectively convert in **0** or **1**.

* * *

As of now, we have seen three types of casting in rust. But remember souls, **Rust have some limitations in type casting.**

Rust Type Casting Limitations
-----------------------------

There are some limitations to rust. some datatypes are not able to cast. For example, **float to char**. Let’s try to cast. 😁

```rs
fn main() {
    let decimal: f32 = 54.321;
  
    // convert float to char data type
    let character = decimal as char;

    println!("decimal : {}", decimal);
    println!("character : {}", character);
}
```


### Error:

```rs
error[E0604]: only `u8` can be cast as `char`, not `f32`
 --> main.rs:5:19
  |
5 |   let character = decimal as char;
  |                   ^^^^^^^^^^^^^^^ invalid cast
```


So, this is what it is. It is not casting. **Don’t try!** 😅

> **Note**: By default **Rust does not support implecit type casting** between primitive and scalar data types. So, use **as** keyword for casting.

* * *

Conclusion
----------

*   Rust only supports **explicit typecasting**.
*   Rust Supports **decimal to int, int to char and char to int** type casting.

In the end, you and I both know that no one will remember this.😂 People always find tutorials or resources to check if this is working or not. That’s why I wrote this post.😂😂. Anyway, We will see the operators in Rust in the upcoming article.