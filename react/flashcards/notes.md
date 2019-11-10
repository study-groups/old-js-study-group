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