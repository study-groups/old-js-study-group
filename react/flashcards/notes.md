# Flashcards Tech Notes

This Markdown file captures notes about building,
testing and deploying a create-react-app called
flashcards.

## High level requirements
Provide a means for storing and displaying collections of flashcards.

## What's included by `create-react-app`

See github docs for [what's included in create-react-app](https://github.com/facebook/create-react-app#whats-included):

- React, JSX, ES6, TypeScript and Flow syntax support.
- Language extras beyond ES6 like the object spread operator.
- Autoprefixed CSS, so you don’t need -webkit- or other prefixes.
- A fast interactive unit test runner with built-in support for coverage reporting.
- A live development server that warns about common mistakes.
- A build script to bundle JS, CSS, and images for production, with hashes and sourcemaps.
- An offline-first service worker and a web app manifest, meeting all the Progressive Web App criteria. (Note: Using the service worker is opt-in as of react-scripts@2.0.0 and higher)

- Hassle-free updates for the above tools with a single dependency.

## Learning create-react-app ecosystem

### Default files:

For the project to build, these files must exist with exact filenames:

- **public/index.html** is the page template;
- **src/index.js** is the JavaScript entry point.

### Webpack
- only files inside src are processed by Webpack
- You can, however, create more top-level directories.


See [cra_closer_look](https://github.com/nitishdayal/cra_closer_look) for info on:





## npm/yarn start

Yarn is used by default but npm should work.  Note that one starts a development session via `yarn start `
which in turn calls `node yarn.js react-scripts start`.

You can see this by running `strace yarn start` and finding this in the 
output (note I am using node version manager, aka, nvm, to maintain node environments): 

```
execve("/home/mricos/.nvm/versions/node/v12.13.0/bin/node", ["node", "/usr/share/yarn/bin/yarn.js", "react-scripts", "start"], [/* 73 vars */]) = 0
```

Which will cause this:
```
"cd packages/react-scripts && node bin/react-scripts.js start"
```

https://github.com/facebook/create-react-app#whats-included

### npm/yarn test

Create React App uses Jest as its test runner. 
While Jest provides browser globals such as window thanks to jsdom, they are only approximations of the real browser behavior. Jest is intended to be used for unit tests of your logic and your components rather than the DOM quirks.

### test files
- Files with .js suffix in __tests__ folders.
- Files with .test.js suffix.
- Files with .spec.js suffix.

From cra_closer_look:
We recommend to put the test files (or __tests__ folders) next to the code they are testing so that relative imports appear shorter. For example, if App.test.js and App.js are in the same folder, the test just needs to import App from './App' instead of a long relative path. Colocation also helps find tests more quickly in larger projects.


### react-scripts start

Hightlights of `node_modules/react-scripts/scripts/start.js`
```js
// Do this as the first thing so that any code reading it knows the right env.
process.env.BABEL_ENV = 'development';
process.env.NODE_ENV = 'development';

// Ensure environment variables are read.
require('../config/env');

    // Create a webpack compiler that is configured with custom messages.
    const compiler = createCompiler({
      appName,
      config,
      devSocket,
      urls,
      useYarn,
      useTypeScript,
      tscCompileOnError,
      webpack,
    });
    // Load proxy config

```

### Debugger
#### Node.js
- For server side, start with [getting started with debugging in node](https://nodejs.org/en/docs/guides/debugging-getting-started/)


### Component development

Create React App doesn't include any tools for this by default, but you can easily add React [Storybook](https://storybook.js.org/) to your project. It is a third-party tool that lets you develop components and see all their states in isolation from your app.
See more at [cra_closer_look](https://github.com/nitishdayal/cra_closer_look/tree/master/tic_tac_toe#developing-components-in-isolation)

## Deployment
`npm run build` creates a build directory with a production build of your app. Set up your favourite HTTP server so that a visitor to your site is served index.html, and requests to static paths like `/static/js/main.js` are served with the contents of the /static/js/main.<hash>.js file. For example, Python contains a built-in HTTP server that can serve static files:

```
cd build
python -m SimpleHTTPServer 9000
```

Or in node:
```
const express = require('express');
const path = require('path');
const app = express();

app.use(express.static('./build'));

app.get('/', function (req, res) {
  res.sendFile(path.join(__dirname, './build', 'index.html'));
});

app.listen(9000);
```

## Database Considerations
Two choices, firebase or mongodb.

### Firebase
1. create project, free terms are good
2. add app to project
3. Copy code from firebase:
```javascript
<!-- The core Firebase JS SDK is always required and must be listed first -->
<script src="https://www.gstatic.com/firebasejs/7.6.1/firebase-app.js"></script>

<!-- TODO: Add SDKs for Firebase products that you want to use
     https://firebase.google.com/docs/web/setup#available-libraries -->

<script>
  // Your web app's Firebase configuration
  var firebaseConfig = {
    apiKey: "XXXXXXXXXXXXXXXXXXXXXXXX",
    authDomain: "appname-2391a.firebaseapp.com",
    databaseURL: "https://appname-2391a.firebaseio.com",
    projectId: "appname-2391a",
    storageBucket: "appname-2391a.appspot.com",
    messagingSenderId: "291281952478",
    appId: "1:3333333333:web:44444444444444"
  };
  // Initialize Firebase
  firebase.initializeApp(firebaseConfig);
</script>
```

Refactor to read data in from a config file which is not stored in your repo:
```js
firebaseConfig=JSON.parse(readFileSync("./firebase-config.json")
```

Install CLI
```sh
npm install -g firebase-tools
```

Login ```$ firebase login```. This will prompt point-and-click web page login via Google

Initialize ```firebase init```

Put this in bottom of `<body>` tag:
```
<!-- The core Firebase JS SDK is always required and must be listed first -->
<script src="/__/firebase/7.6.1/firebase-app.js"></script>

<!-- TODO: Add SDKs for Firebase products that you want to use
     https://firebase.google.com/docs/web/setup#available-libraries -->

<!-- Initialize Firebase -->
<script src="/__/firebase/init.js"></script>

```

In addition, database needs to be 
initialized in the firebase web console.

When you’re ready, deploy your web app
Put your static files (e.g., HTML, CSS, JS) in your app’s deploy directory (the default is “public” but use "build"). Then, run this command from your app’s root directory: `firebase deploy`

A url like "https://flashcards-e027d.firebaseapp.com/" should appear on the command line and take you 
to the web page. 
### Mongodb



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
