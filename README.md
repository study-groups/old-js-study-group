# JavaScript Study Group

Three legs of JS development:

1. **DevOps** (linux commandline, Babel, Webpack, Postman, HTTP, JWT, OAuth)
2. **Language** (syntax, symantics, single threaded model, DOM interface)
3. **Architecture** (backend frameworks, network, frontend frameworks)

JavaScript is used in software engineering (aka, full-stack web development) to compose autonomous functions which 
create a seamless user experience. In contrast, Python is used in data science to create software products that run one time, are specialized and are fragile with respect to distribution and re-use.

# DevOps
In contrast to DevOps for data science (which is geared toward training models used for future inference), DevOps
software engineering is about creating continuous integreation / continous deployment piplelines according to 
the [12 Factor App Methodology](https://12factor.net/) first documented by Heroku. 

## Tools
- [neovim](https://neovim.io/): New take on vim, classic command line editor.
- [VS Code](https://code.visualstudio.com/): popular, free open-source code editor.
- [curl](https://curl.haxx.se/): Command line tool for transferring data with URLs.
- [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools)
- [Firefox DevTools](https://developer.mozilla.org/en-US/docs/Tools)
- [NPM](https://www.npmjs.com/) Node Package Manager. It creates and manages package.json.

## Other players in the JS DevOps ecosystem:
- Databases: MongoDB,RedisDB, FireBase
- Hosting: Digital Ocean
- JAM stack hosting: Netlify, Zeit, Heroku
- Code storage and CI/CD: GitLab

# Language Syntax and Symantics
Syntax refers to symbols and the rules for writing them. Symantics refers to what the symbols mean.
Mozilla Developer Network is a strong starting point for understanding JS as a language.

## Intro
- [JavaScript at MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
- [JavaScript Guide at MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide)
- [Documnet Object Model](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model): Best DOM reference.
- [Manipulating the Document Object Model](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Client-side_web_APIs/Manipulating_documents)

## Intermediate
- [What the heck is the event loop anyway? | Philip Roberts | JSConf EU](https://www.youtube.com/watch?v=8aGhZQkoFbQ): true in 2014, true now. Great explaination of event loop and the function stack maintained by every tab in a browser.
- [Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [ES Lint](https://eslint.org/docs/user-guide/getting-started): ESLint is a tool for identifying and reporting on patterns found in ECMAScript/JavaScript code, with the goal of making code more consistent and avoiding bugs.

# Architecture
## Frontend
### Foundation
- [MDN: Getting started with the web](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web)
- [MDN: JS First Steps](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps)
### Frameworks
- [React](https://reactjs.org/): A JavaScript library for building user interfaces.
- [React: Main Concepts](https://reactjs.org/docs/hello-world.html). Start here. Return here.
### Testing
- [Jest](https://jestjs.io/): Jest is a JavaScript Testing Framework with a focus on simplicity.
- [MochaJS](https://mochajs.org/): Mocha is a feature-rich JavaScript test framework running on Node.js and in the browser
for asynchronous testing.
- [Chai assertion library](https://www.chaijs.com/): Chai is a BDD / TDD assertion library for node and the browser that can be delightfully paired with any javascript testing framework.

## Network
- [Web APIs](https://developer.mozilla.org/en-US/docs/Web/Guide/API)
- [Fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)
- [JWT](https://jwt.io/): JSON Web Tokens are an open, industry standard RFC 7519 method for representing claims securely between two parties. JWT.IO allows you to decode, verify and generate JWT.
- [Websockets](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API/Writing_WebSocket_client_applications)
WebSocket client applications use the WebSocket API to communicate with WebSocket servers using the WebSocket protocol.
- [Webworkers](https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API): Web Workers makes it possible to run a script operation in a background thread separate from the main execution thread of a web application. The advantage of this is that laborious processing can be performed in a separate thread, allowing the main (usually the UI) thread to run without being blocked/slowed down.


## Backend 
- [NodeJs](https://nodejs.org/en/)
- [Bable](https://babeljs.io/)
- [ExpressJS](https://expressjs.com/)
- [WebPack](https://webpack.js.org/)
- [MongoDb](https://www.mongodb.com/)


## Possible projects
- Make ES6 Module with subset of [gauss.js](https://github.com/fredrick/gauss)

## References

## Version references
- [ECMA-262 version ES6, aka
ES2015](https://www.ecma-international.org/ecma-262/7.0/#):
the nominal reference suitable for use in 2019.

- [ECMA-262 version ES2016+ ](https://tc39.github.io/ecma262/): Start here for documentation for language reference.

- [JavaScript Version Guide](
https://flaviocopes.com/ecmascript/) - good site reminding that 
ES6 is same as ES2015.

- [Kangax JS/Browser Compatibility](http://kangax.github.io/compat-table/es2016plus/): We can use ES2016+ features

- [Can I use?](https://caniuse.com/)

- [ES6-features.org](http://es6-features.org): Shows the
changes from old ES5 (2014) to new ES6 (2015. This marks a
significant change and is a good point of study.

## Best practices
- [12factor app](https://12factor.net/): The twelve-factor methodology can be applied to apps written in any programming language, and which use any combination of backing services (database, queue, memory cache, etc).

- [Node Best Practices](https://github.com/goldbergyoni/nodebestpractices)
- [Testing with Kent C Dodds](https://testingjavascript.com/)


