---
layout: post
title: "Introduction to Java, The First Java Program"
excerpt: "Learn First program of java with printing simple hello world with java coding structure in class"
date: Octo 29, 2024
author: neha
categories:
    - java
image: assets/techalgospotlight-java-banner.jpg
keywords: java hello world program, techalgospotlight
published: true
tags: featured
---


From this tutorial, We are gone start new series of Java with their introduction and variables, datatypes, strings, arrays in java and many more things.

Are you excited ?. Because, We will deep dive into each concept with there coding example.

## First Java Program

Instead writing fancy defination, Let me show you first program.

```java
/**
 * A basic Java program that prints "Hello, world!" to the console.
 */
public class Hello {
  /**
   * The main entry point of the application.
   * 
   * @param args Command-line arguments (not used in this program)
   */
  public static void main(String[] args) {
    // Print "Hello, world!" to the console
    System.out.println("Hello, world!");
  }
}
```

Just see the program and try to understand code. I know, It’s look like little weird and funcky. But, this is our first program The **Hello World!**.

> **Note**: Java is **Object Oriented Programming**. That means we have write each line of code within class.

Let’s Discuss Key points of above program.

### Description of Hello World
- In Java, File Name should be same as Class Name.
- **main** method is the entry point of java program excution.
- **System.out.println** is for printing text like Hello World.
- In main method, We have to pass atleast single arguments in any form strictly. Because Its java.
- One more thing, We have to specifiy datatypes of every variables.

Core things are covered. For, Rest of the information and understanding, You can check program. I wroted comment for usage.

---
At this point everythings working fine. But we have one question. How can we run this code??. So, Let’s me show how can we run our first hello world java program.

## Run Java Program

### Output

```txt
Hello, World!
```

For this output we have follow below steps.

### Steps
- Save this code in a file named **Hello.java**.
- compile the program using **javac Hello.java**.
- If you get any error in compilation, Then we must correct first code. If you didn’t get any error then follow next step.
- Run binary code using **java Hello**. 

Java will generate class file when we compile the code. Then we have to run binary. One more thing, We don’t have to specify file extension when we are executing binary code. It’s optional.

> **Note**: **javac** for compile the java program.

In next article we will deep dive into the variables in java and defination.
