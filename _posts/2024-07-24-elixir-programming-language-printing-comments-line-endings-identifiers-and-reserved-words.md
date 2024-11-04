---
title: "Elixir Programming Language: Printing, Comments, Line Endings, Identifiers, and Reserved Words"
excerpt: "Learn about Elixir programming language basics, including printing, comments, line endings, identifiers, and reserved words. This guide provides an introduction to Elixir syntax and conventions for beginners."
date: July 24, 2024
layout: post
author: neha
categories:
    - elixir
image: assets/techalgospotlight-elixir-banner.webp
keywords: elixir, elixir programming language, elixir tutorial, elixir for beginners, functional programming, fault-tolerant programming, reserved words, identifiers, line endings, comments, printing
published: true
---

In this article delves into the fundamental aspects of Elixir, including printing, comments, line endings, identifiers, and reserved words, providing practical coding examples for a hands-on understanding.

Printing in Elixir is straightforward, primarily using the **IO.puts** function. This function prints a string to the standard output followed by a new line.

### Example

```elixir
IO.puts("Hello, Elixir!")
```


For more control over output, Elixir also provides **IO.write**, which does not append a newline at the end.

```elixir
IO.write("Hello, ")
IO.write("Elixir!")
```


* * *

Comments in Elixir
------------------

Comments are essential for making code understandable. Elixir supports single-line comments, which start with the **#** symbol.

### Example

```elixir
# This is a single-line comment in Elixir
IO.puts("Hello, Elixir!") # This prints a message
```


Elixir does not have built-in syntax for multi-line comments, but multiple single-line comments can be used to achieve the same effect.

```elixir
# This is a multi-line comment
# in Elixir
IO.puts("Hello, Elixir!")
```


* * *

Line Endings
------------

Elixir uses newline characters to signify the end of a line. It does not require semicolons or any special character to terminate statements.

### Example

```elixir
IO.puts("Hello")
IO.puts("Elixir")
```


Semicolons can be used to separate multiple statements on a single line if desired.

```elixir
IO.puts("Hello"); IO.puts("Elixir")
```


* * *

Identifiers
-----------

Identifiers in Elixir are names given to variables, functions, and modules. They must start with a lowercase letter or an underscore and can contain alphanumeric characters and underscores.

### Example

```elixir
variable_name = "Elixir"
another_variable = 42
```


Identifiers starting with uppercase letters are reserved for module names.

```elixir
defmodule MyModule do
  def greet do
    IO.puts("Hello from MyModule!")
  end
end
```


* * *

Reserved Words
--------------

Elixir has a set of reserved words that cannot be used as identifiers. These include:

**after,case,catch,do,else,end,false**,**fn,for,if,import,in,nil,quote,receive,require,rescue,true,try,when**

### Example

```elixir
# Incorrect usage
defmodule try do
  def example do
    IO.puts("This is not allowed")
  end
end
```


#### Correct usage:

```elixir
defmodule ExampleModule do
  def try_example do
    IO.puts("This is allowed")
  end
end
```


* * *

Conclusion
----------

In the upcoming article, We will discuss more about the data types of the Elixir Programming Language. Meanwhile, you can check out **Elixir Programming Language: Functional, Scalable, and Fault-Tolerant** Aritcle.