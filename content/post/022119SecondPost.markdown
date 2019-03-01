---
title: Javascript Module Patterns
author: Daniel
date: '2018-07-01'
slug: JsModules
categories: []
tags: []
header:
  caption: ''
  image: ''
bibliography:
---

In this second post, I will explain several good reasons to use Javascript modules and how to incorporate them.

### Let’s begin.

There are a lot of good reasons why to use JS modules but here are a just few that, in my opinion, are most important. Modules are like chapters in a book. Modules that are well written, are also highly self-contained and only add distinct functionality. This allows them to be removed or added as need be and without disrupting the application or code base as a whole.

Maintainability: Code, specifically modules, that are written well should be maintainable. A module should aim not to depend on other parts of the codebase as much as possible. With this in mind, updating a modules should be easy. Going back to our book analogy above, if chapters in a book were interdependent it would be a hassle to change a chapter and not affect other chapters.

### Namespacing:
Avoiding namespace pollution includes creating a private space for our variables. In JavaScript, variables that are used outside the scope of a top level function are global variables. Namespace pollution occurs when completely unrelated code shares global variables. And sharing global variables is a huge NO in software development.

The Module Pattern: In JS, functions are the only way to create a new scope.
With this in mind, the module pattern approach is to store both public and private methods and variables in a single object. This approach allows us create ‘public’ methods that we would want to expose to the world.

### Examples on Incorporating Modules:
Below I will walk through two ways to incorporate modules into your development.

## 1. Anonymous Closure Example:
 {{< figure library="1" src="annoClosure.png" title="anonymousClosure" >}}

The example above demonstrates closure in our anonymous function. This hides our variables from our parent global scope and it is immediately evaluated. A detail to note are the parenthesis around the anonymous function. These are required because statements that start with the keyword function are considered function declarations.

## 2. Object Interface Example:
 {{< figure library="1" src="objectInterface.png" title="interfaceExample" >}}

The approach above creates a module and uses a self-contained object. This example lets us decide what variables or methods we want to keep private: the scores array. And, what methods, in this case, we want to expose: the double and sort functions.

These are just a two methods to incorporate module patterns into your codebase and a few good reasons to do so above. I hope this post gives a glimpse into JavaScript design patterns and that it gave you a better understanding of modules. In future posts, I will write more about JavaScrip design patterns.
