---
title: "Rust Operators : The Four Pillars of Empire"
excerpt: "Learn about Rust operators, including arithmetic, comparison, logical, and compound assignment operators. This guide covers the essential operators in Rust with examples to help you understand how they work."
date: Sept 13, 2024
layout: post
author: neha
categories:
    - rust
image: assets/techalgospotlight-rust-banner.webp
keywords: rust operators, rust arithmetic operators, rust comparison operators, rust logical operators, rust bitwise operators 
published: true
---

As we know, **Operators** are **Key Pillars** of every programming language, Instead of talking about other things, Let’s talk about only **Rust Operators the four pillars of empire**. Sounds weird? I know because you are in **TechAlgoSpotlight**. We only do weird things 😅

Basically, operators are nothing. They used to do various types of **operations in values or maybe variables**. So, Rust also came with this type of common functionality in four parts. **Arithmetic Operators, Logical Operators, Comparison Operators and Compound Assignment Operators**.

Are you ready to see each of them? Let’s get started with wasting a lot of time. 😉

!Rust Operators Okay TechAlgoSpotlight

* * *

1\. Rust with Arithmetic Operators
----------------------------------

As we know everywhere arithmetic operators are only used for **addition, subtraction, multiplication and division. Rust did the same things without any fear.**

Let’s think about two variables, the First **X** and the Second **Y**. Let me show you something in table form. I know, you know these things, But as a responsible admin, I have to show you, How many types of arithmetic operators are available in Rust.


|Operators         |Using What We Can Do|
|------------------|--------------------|
|+ (Addition)      |X + Y               |
|- (Subtraction)   |X – Y               |
|* (Multiplication)|X * Y               |
|/ (Division)      |X / Y               |
|% (Remainder)     |X % Y               |


### Rust with Addition, Subtraction and Multiplication Operators

We will see the Division operator after some time. **The longer you wait, The more you get**. 😂

```rs
fn main() {
    let a = 18;
    let b = 2;

    // add two variables using + operator
    let x = a + b;
    println!("{} + {} = {}", a, b, x);

    // subtract two variables using - operator
    let y = a - b;
    println!("{} - {} = {}", a, b, y);

    // multiply two variables using * operator
    let z = a * b;
    println!("{} * {} = {}", a, b, z);
}
```


#### Output (Result)

```rs
18 + 2 = 20
18 - 2 = 16
18 * 2 = 36
```


Have seen magic? Rust just did with giving us the output. Let’s see some more magical things with Division Operators.

* * *

### Rust with Division Operator

```rs
fn main() {
    let dividend = 21;
    let divisor = 8;

    // arithmetic division using / operator with integers
    let division = dividend / divisor;

    println!("{} / {} = {}", dividend, divisor, division);
}
```


#### Output

As per the code, you can understand. We did just a simple division with **/** Operators. But wait here is the twist come.

Regular calculation gives us **2.625**. But in Rust, When we use division operators for operation. Instead of a floating value, they give us an **Int value** (2). I don’t know why Rust acts like this But maybe internally they like JavaSciprt.

Anyway, What if we want float values with a division operator? So, silently Rust introduced a trick to achieve floating values by passing **floating integers**.

> **Spotlight**: Floating Integer is like x = 2 works as an integer but x = 2.0 works as an floating integer.

Let’s take a small example while closing our eyes.

```rs
fn main() {
    let dividend = 21.0;
    let divisor = 8.0;

    // arithmetic division using / operator with floating point values
    let division = dividend / divisor;

    println!("{} / {} = {}", dividend, divisor, division);
}
```


As we discussed in Spotlight. **Floating Integer is nothing but a copycat of Float**.

#### Output

By assigning **dividend** and **divisor** as a float value. We got a float value, Simple. Now, we have to learn the **remainder**. So let’s see how **remainder operators** work.

* * *

### Rust with Remainder Operator

```rs
fn main() {
    let dividend = 21;
    let divisor = 8;

    // arithmetic remainder using % operator
    let remainder = dividend % divisor;
  
    println!("{} % {} = {}", dividend, divisor, remainder);
}
```


#### Output:

As we don’t know the remainder, So, let’s understand the code first. Instead of using other arithmetic operators, They used **%**. It works like the operator name. **Just give us reminders**. Nothing Else. Finish!!!

I don’t think so any other arithmetic operators remaining. 🤔 **Let’s see Assignment Operators with a cup of tea.**

* * *

2\. Rust with Assignment Operator
---------------------------------

**Assignment operator used for assigning values. That’s it!!!** 🤣

Here we are using **=** for assigning 007 to bobbyDeol. Maybe in the future bobbyDeol become 007. But as syntax vice, it’s 007. Assignment operators are like I am giving you something, Hold it until you die.😂

Do you have questions like, What if we have to change the value of a variable? Let’s see how we can do by putting the small keyword **mut** (Mutable).

As we discussed bobbyDeol example of assigning 007. Sowe can not change. But after using **mut** keyword, We can change bobbyDeol to 700.

Now **mut** keyword is introduced and I would like to tell you more about this. let me share one example with you.

* * *

### Rust Compound Assignment Operators

The simplest definition of this operator is we can do some operations with shorter syntax. Let me show you How we can do in Rust.

```rs
let mut x = 1;

// compound assignment operators
x += 3;
```


#### Output

Rust has some fancy terms. Looks like, they use almost JavaScript Syntax. 😆 Let me share some of this fancy operators list with you.


|Operator                      |Example|Equivalent To|
|------------------------------|-------|-------------|
|+= (addition assignment)      |a += b |a = a + b    |
|-= (subtraction assignment)   |a -= b |a = a – b    |
|*= (multiplication assignment)|a *= b |a = a * b    |
|/= (division assignment)      |a /= b |a = a / b    |
|%= (remainder assignment)     |a %= b |a = a % b    |


Let’s wrap this operator with our cup of tea. Because you need coffee to understand the next operator.

* * *

3\. Rust Comparison Operators
-----------------------------

The heading says everything. Explanation is not required here.

This is called **>** (greater than). This operator is only required when you have to compare something. After comparison, the Output will be either **true** or **false**. You can this operator as a **relational operator**.

*   **TRUE** : If Condition Satisfied.
*   **FALSE** : If Condition Not Satisfied.

Let’s list out some of the comparison operators


|Operator                     |Example|Description                            |
|-----------------------------|-------|---------------------------------------|
|> (Greater than)             |a > b  |true if a is greater than b            |
|< (Less than)                |a < b  |true if a is less than b               |
|>= (Greater than or equal to)|a >= b |true if a is greater than or equal to b|
|<= (Less than or equal to)   |a <= b |true if a is less than or equal to b   |
|== (Equal to)                |a == b |true if a is equal to b                |
|!= (Not equal to)            |a != b |true if a is not equal to b            |


Oh, We forgot the example of comparison operators. Let me share 😅

### Rust Comparison Operators Example

```rs
fn main() {
    let a = 7;
    let b = 3;
    
    // use of comparison operators
    let c = a > b;
    let d = a < b;
    let e = a == b;
    
    println!("{} >= {} is {}", a, b, c);
    println!("{} <= {} is {}", a, b, d);
    println!("{} == {} is {}", a, b, e);
}
```


#### Output:

```rs
7 > 3 is true
7 < 3 is false
7 == 3 is false
```

As we know if the condition is satisfied then **TRUE**, Otherwise **FALSE**. That’s all about comparison operators. Actually, I don’t know much about this operator because I don’t like it. Simple 🫠🫠

I think we have to conclude with our last operator. The logic killer operator. It’s called **Logical Operator**.

* * *

4\. Rust Logical Operators
--------------------------

Find a second coffee, Because this operator required energy to understand. As you know words say everything. But the tricky part is, It’s not about logical things. It’s all about logical plus comparison. Let me show you how this works.

**It’s like comparing two logic.** **&&** This is an AND operator. AND Operator returns **TRUE** If both conditions are satisfied.

I know only three logical conditions 😅, Let me share them one by one quickly via table

* Operator: && (Logical AND)
  * Example: exp1 && exp2
  * Description: returns true if both exp1 and exp2 are true
* Operator: || (Logical OR)
  * Example: exp1 || exp2
  * Description: returns true if any one of the expressions is true
* Operator: ! (Logical NOT)
  * Example: !exp
  * Description: returns true if the expression is false and returns false, if it is true


### Rust Logical Operators Example

```rs
fn main() {
    let a = true;
    let b = false;
    
    // logical AND operation
    let c = a && b;

    // logical OR operation
    let d = a || b;

    // logical NOT operation
    let e = !a;
    
    println!("{} && {} = {}", a, b, c);
    println!("{} || {} = {}", a, b, d);
    println!("!{} = {}", a, e);
}
```


#### Output:

```rs
true && false = false
true || false = true
!true = false
```


Basically, **&&** Operater Works If both condition is **TRUE**, **||** Operartor works if one or more condition is **TRUE** and **!** Operartor used for when we don’t want to satisify condition forcefully.

**That’s It!!** 🙌🙌

* * *

Conclustion
-----------

**Today we show four pillars of Operators.**

*   Arithmetic Operators
*   Compound Assignment Operators
*   Logical Operators
*   Comparison Operators (Relational Operators)

**We show the each of the operators examples with 2 cup of Coffee and 1 Cup of Tea.** Why i am telling you because reading is easy but make content more readble and understandable is little difficult.🥲 Insted of sharing my childhood troma let’s wrap up now!!. We will see **Rust conditions** in upcomming articles.