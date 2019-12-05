---
layout: post
title:      "Ruby Variables"
date:       2019-12-05 18:48:44 +0000
permalink:  ruby_variables
---



This is a short, general post about Ruby variables.

Variables are important because they allow us to encapsulate data. A variable is a reference to a value. 

```
first_number = 10
second_number = 5 

sum = first_number + second_number

puts sum 
```


The above code will print ‘15’.

```first_number```, ```second_number```, and ```sum``` are all variables. Variables are words or characters that hold values. In other words, variables allow us to store information. They refer to a specific object located in computer memory. In Ruby, a variable can point to almost any type of value including numbers, strings, arrays, and hashes.

Variables can be written in different ways but in Ruby there is a strong convention to use what is known as snake case. ```first_number``` and ```second_number```, above, are examples of *snake case*, words separated by underscores. If you're trying to remember snake case just imagine that a snake has eaten your variable name. The underscore(s) as the flat body of the snake and the bare words as food that the snake is digesting.

![](https://66.media.tumblr.com/1c664f3cb13395b5ea20e6c550da8c55/tumblr_neooslzYnY1tyhayao1_500.gif)

##Ruby Naming Variable Conventions

Variable names should start with an undercase alphanumeric character or the underscore _ character. A variable that begins with an uppercase letter is known as a [constant](https://www.rubyguides.com/2017/07/ruby-constants/) and has different characteristics. It is considered good practice to choose *meaningful* variable names. Programs are more readable when variable names are short and descriptive.

There are a couple ways you shouldn’t write variable names: 

```
2nd Place 
begin
my.email
```

A ruby variable cannot start with a number, be a [Ruby reserved word,](https://ruby-doc.org/docs/ruby-doc-bundle/Manual/man-1.4/syntax.html#resword) or have punctuation or space characters.

##Variable Type

A variable has a type, and a variable’s type is the type of value it holds. Ruby is a dynamically typed language, meaning the value of a variable can change its type and does not need to be permanently defined. Variables are assigned using ```=``` (equal sign), called the assignment operator.The above variable, ```sum```, has a value of 15 which is a type of 'number'. You could change that value to a type ‘string’, easily.

```
sum = ‘fifteen’
```

Ruby is also a strongly typed language meaning a variable will never be automatically coerced to another type without you explicitly changing the type. Adding two numbers will return a number, adding two string will return a string, but adding a number and a string will raise a [TypeError](https://ruby-doc.org/core-2.2.0/TypeError.html).


Ruby variables can be classified in different ways, including local, global, instance, class, and more. I'll dive deeper into specific kinds of variables in future posts.

Follow me on [twitter](http://twitter.com/drkjc_)!


