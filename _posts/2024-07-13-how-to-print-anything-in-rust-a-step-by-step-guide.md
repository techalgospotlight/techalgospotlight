---
title: "How to Print Anything in Rust: A Step-by-Step Guide"
excerpt: Let’s understand how to print things like numbers, strings or variables in Rust. So, for printing anything in Rust, We use print! macro....
date: July 13, 2024
layout: post
author: neha
categories:
    - rust
image: assets/techalgospotlight-rust-banner.webp
keywords: rust print
published: true
---

Let’s understand how to print things like numbers, strings or variables in Rust. So, for printing anything in Rust, We use **print!** macro.

```rs
fn main() {
    print!("Hello, TechAlgoSpotlight!");
}
```


#### Output

```txt
Hello, TechAlgoSpotlight!
```

In the above code, **print!** is a macro that prints the text inside double quotes. To learn more about macros, visit [_Rust Macro_](https://programiz.com/rust/macro).

In Rust, there are two variations of the print:

*   **print!()**
*   **println!()**

* * *

**print!** Macro in Rust
----------------------

As we discussed earlier, the **print!** prints the text inside **double quotes**. Let’s take an example,

```rs
fn main() {
    print!("Let's learn rust from TechAlgoSpotlight! ");
    print!("I love TechAlgoSpotlight.");
}
```

#### Output

```txt
Let's learn rust from TechAlgoSpotlight! I love TechAlgoSpotlight.
```

Have you seen that, we used two **print!** to print two different strings? However, both strings are printed on the same line. Because print! macro always **prints in a single line**.

To separate the print strings into different lines, we can use the **println!** macro.

* * *

**println!** Macro in Rust
------------------------

```rs
fn main() {
    println!("Let's learn rust from TechAlgoSpotlight! ");
    println!("I love TechAlgoSpotlight.");
}
```

#### Output

```txt
Let's learn rust from TechAlgoSpotlight!
I love TechAlgoSpotlight.
```

Have you seen that, our output is printed in two separate lines?

Because **println!** Add a **new line** at the end. So the second text will print in the **next line**.

* * *

Printing Variable in Rust
-------------------------

Let’s use the same **print!** and **println!** macros to print variables in Rust. For example,

```rs
fn main() {
    let age = 20;
  
    // print the variable using println!
    println!("{}", age);

    // print the variable using print!
    print!("{}", age);
}
```

#### Output

In the above code, **{}** is a placeholder that is replaced by the variable after the comma. That’s why we get **20** as output.

We can add a placeholder to format our output. For example,

```rs
fn main() {
    let age = 20;
    println!("Age = {}", age);
}
```

#### Output

* * *

Printing Multiple Variable in Rust
----------------------------------

Let’s use a single **println!** macro to **print multiple** variables. For example,

```rs
fn main() {
    let age = 26;
    let name = "TechAlgoSpotlight";
  
    // print the variables using println!
    println!("Name = {}, Age = {}", name, age);
}
```

#### Output

```txt
Name = TechAlgoSpotlight, Age = 26
```

Have you seen variables are printed sequentially? Yes, the first variable name replaces the first placeholder and the second variable age replaces the second placeholder.

We can specify the **numbering for placeholders** to print variables in different order. Let’s see.

```rs
fn main() {
    let age = 26;
    let name = "TechAlgoSpotlight";
  
    // print the variables using println!
    println!("Name = {0}, Age = {1}", name, age);
}
```

#### Output

```txt
Name = TechAlgoSpotlight, Age = 26
```

Here, the placeholder

*   **{0}** will be replace by the variable name.
*   **{1}** will be replace by the variable age.

We can also use the **variable names** directly inside the placeholder. Let’s see.

```rs
fn main() {
    let age = 26;
    let name = "TechAlgoSpotlight";
  
    // print the variables using println!
    println!("Name = {name}, Age = {age}");
}
```

#### Output

```txt
Name = TechAlgoSpotlight, Age = 26
```

Here, instead of using variables separately after **comma**, we have directly provided them inside the placeholder.

*   **{name}** – prints the value of the name variable
*   **{age}** – prints the value of the age variable

* * *

Printing Newline Character in Rust
----------------------------------

Let’s see, How we can print newline using **\n** character(s) for **escaping sequence**.

```rs
fn main() {
    print!("TechAlgoSpotlight!\nI love TechAlgoSpotlight.");
}
```

#### Output

```txt
TechAlgoSpotlight!
I love TechAlgoSpotlight.
```

Here, **\n** is an escape sequence that adds a new line character. The text after **\n** will print in a new line.

* * *

Conclusion
----------

So, this is all about printing anything in rust. We seen most of the common methods for printing anything. In upcoming tutorial, We will deep dive into **variables and mutability** in Rust.