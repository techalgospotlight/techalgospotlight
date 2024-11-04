---
title: "All You Need to Know Comments in Rust"
excerpt: In any programming language, Comments are lines of text used to describe information in code. Let's take one example...
date: June 23, 2024
layout: post
author: neha
categories:
    - rust
image: assets/techalgospotlight-rust-banner.webp
keywords: rust, rust comments
published: true
---


In any programming language, **Comments** are lines of text used to describe information in code. Let’s take one example.

```rs
// entry point
fn main() {
    // printing text on the screen
    println!("TechAlgoSpotlight!");
}
```

Here **// entry point** and **// printing text on the screen** are the comments.

While the code is executing, comments are completely ignored by the **compiler or interpreter**. So, comments are ideally for **reading** purposes only.

## Types of Comments in Rust

There are **two** main types of comments available in Rust.

- **//** – Line Comment
- **/*<em>…*</em>/** – Blocked Comment

### Line Comments in Rust

For **Line comments**, we have two used two forward slashes like this **//**.

```rs
fn main () {
    // declare your variable name here.
    let x = 10;
    println!("x = {}", x);
}
```

##### Output

```
x = 10
```

Here, **// declare your variable name here.** is a line comment, Also known as a **single-line** comment.

---

### Block Comments in Rust

For **Block comments**, we used symbols like **/*....*/**. to denote the comments. It starts with / and ends with */ symbols.

```rs
fn main() {
    /*
    declare a variable
    and assign value here
    */
    let x = 10;
    println!("x = {}", x);
}
```

##### Output

```
x = 10
```

Here,

```rs
/*
declare a variable
and assign value here
*/
```

is a block comment, You can see block comments using multiple lines and we can write a complete brief in these comments. Hence, it is known as a block comment.

---

We can also create multiple lines of comments by just using line comments. Here is a small example.

```rs
fn main() {
    // declare a variable
    // assign value here
    let x = 10;
    println!("x = {}", x);
}
```

> **Note**: In the Rust ecosystem, line comments are preferred over block comments.

We can also disable part of the code using line or block comments.

```rs
fn main() {
    // declare a variable
    // assign value here
    // let x = 10;
    println!("x = {}", x);
}
```

In the above code, we just commented variable x. So that **println!** couldn’t get the value of **X**.

Instead of printing X in the program will give you an error.

---

So, this is all we need to know about comments in Rust. Will see more articles about Rust in upcoming articles.