---
title: "Hello World Program in Rust"
excerpt: Let’s start with the world’s simplest program “Hello World! in Rust”. Since it’s a very easy program, it’s often used to learn a new programming language quickly.
date: June 21, 2024
layout: post
author: neha
categories: 
    - rust
image: assets/techalgospotlight-rust-banner.webp
keywords: rust, hello world
published: true
---

Let’s start with the world’s simplest program “**Hello World!** in Rust”. Since it’s a very easy program, it’s often used to learn a new programming language quickly.

Let’s see how we can run **Hello World!** program in **Rust**.

## Rust “Hello, World!” Program

```rs
fn main() {
    println!("Hello, World!");
}
```

##### Output

```
Hello, World!
```

we have successfully printed the text **Hello, World!** on the screen.

## BTS of “Hello, World!” Program in Rust

Here are the different things in the below programs

#### 1. main() function

```rs
fn main() {
  // Code
}
```

**main()** function is the entry point of every program in Rust. It is always the first code that runs every Rust program.

The body is wrapped with **{}** brackets. We will learn more about this in upcoming articles.

#### 2. Print statement

```rs
println!("Hello, World!");
```

In this program we used **println!** for print text in Rust. Basically, **println!** is macro for printing any text in Rust. In this program **Hello World!** is an argument of **println!()** , Also we have to specify **;** At the end of the line which indicates the program is complete.

We will learn more about macros in upcoming articles.