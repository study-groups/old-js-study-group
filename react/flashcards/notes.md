# Tooling
## Reactstap v. react-bootstrap

Here is a good StackOverflow article on the ongoing discussion
about mainting **state** in an application's User Interface: [Reactstap v. react-bootstrap]( https://stackoverflow.com/questions/56061590/what-is-difference-between-reactstrap-and-react-bootstrap). 


In a nutshell, <code> reactstrap </code> uses this pointer and a state
variable on the Component where as react-bootstrap uses functions 
and Hooks. Comparing these two ways to interface with the Bootstrap 
UI CSS shows why [Hooks](https://reactjs.org/docs/hooks-intro.html)
are a popular solution to the task maintaining stateful logic
separately from it's view. — The alternative is to keep the state
in the UI component, thus tightly coupling the business logic
with it's visual representation. Such a tight coupling is
slightly easier to reason about but makes **testing** and 
**component sharing and reuse** more difficult.This is 
what they mean o the hooks-intro page when they say:

**Hooks allow you to reuse stateful logic without changing 
your component hierarchy. This makes it easy to share Hooks
among many components or with the community.**

## Imports

The history of of creating components in 
JavaScript is valuable for both learning the language
and reasoning about scope and composability of 
components.

- [JavaScript Modules: From IIFEs to CommonJS to ES6 Modules](https://tylermcginnis.com/javascript-modules-iifes-commonjs-esmodules/) by Tyler McGinnis. * 
 There’s good reason for that. Modules in JavaScript have a strange and erratic history. In this post we’ll walk through that history and you’ll learn modules of the past to better understand how JavaScript modules work today. *.

- [Learning JavaScript Design Patterns](https://addyosmani.com/resources/essentialjsdesignpatterns/book/#revealingmodulepatternjavascript) by Addy Osmani. 
*Design patterns also provide us a common vocabulary to describe 
solutions. This can be significantly simpler than describing syntax 
and semantics when we're attempting to convey a way of structuring 
a solution in code form to others.  In this book we will explore 
applying both classical and modern design patterns to the JavaScript 
programming language.* 

- [Crockford's Classless pattern](https://gist.github.com/mpj/17d8d73275bca303e8d2) Good breakdown of Douglas Crockford's version of the Revealing Module Pattern by [mpj](https://www.youtube.com/channel/UCO1cgjhGzsSYb1rsB4bFe4Q). Notice
no use of an IIFE in this example. This StackOverflow is good if 
ES6 syntax is not clear: [Understanding Crockford's Classless OOP]
](https://stackoverflow.com/questions/31615655/understanding-crockfords-classless-oop-implementation)

- [The Revealing Module Pattern in Javascript](https://gist.github.com/zcaceres/bb0eec99c02dda6aac0e041d0d4d7bf2) Another summary of the Revealing Module
Pattern by Zach Caceres. The point here is to return a object with 
specific variables and functions exposed. Until ES6, JavaScript did 
not have block scope, only function scope. So variables declared
with var keyword were local to the function they were declared in.
Variables declared without the <code>var</code> keyword are hoisted
to global scope (bad). 
