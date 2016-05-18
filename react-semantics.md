# React Semantics

Before I enlighten anyone with the mechanics of React I'd first like to define a few terms so as to grease the learning process.

Below I list the most common terms, and their definitions, used when talking about React.

#### Babel
Babel transforms JavaScript ES\* (i.e. JS 2016, 2016, 2017) to ES5. Babel is the tool of choice from the React team for writing future ES* and transforming JSX to ES5 code.

***

#### Babel Cli
Babel comes with a CLI tool, called Babel CLI, that can be used to compile files from the command line.

***

#### Component configuration options (aka "component specifications")

The configuration arguments passed (as an object) to the `React.createClass()` function resulting in an instance of a statefull React component.

***

#### Component life cycle methods

A sub group, semantically called out, from all of the component configuration options (i.e. `componentWillUnmount`, `componentDidUpdate`, `componentWillUpdate`, `shouldComponentUpdate`, `componentWillReceiveProps`, `componentDidMount`, `componentWillMount`). These various methods are executed at specific points in a component's lifecycle.

***

#### Document Object Model (aka DOM)

"The Document Object Model (DOM) is a programming interface for HTML, XML and SVG documents. It provides a structured representation of the document as a tree. The DOM defines methods that allow access to the tree, so that they can change the document structure, style and content. The DOM provides a representation of the document as a structured group of nodes and objects, possessing various properties and methods. Nodes can also have event handlers attached to them, and once an event is triggered, the event handlers get executed. Essentially, it connects web pages to scripts or programming languages." - [MSD](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model)

***

#### ES5
The 5th edition of the ECMAScript standard. The ECMAScript 5.1 edition was finalized on June 2011.

***

#### ES6/ES 2015
The 6th edition of the ECMAScript standard. AKA JavaScript 2015. The ECMAScript 6th edition was finalized on June 2015.

***

#### ECMAScript 2016 (aka ES7)
Name of the specification that will provide updates to the JavaScript language in 2016.

***

#### ES\*
Used to represent the current version of JavaScript as well as potential future versions that can written today using tools like Babel. When you see "ES*" it more than likely means you'll find uses of ES5, ES6, and ES7 together.

***

#### JSX
JSX is an optional XML-like syntax extension to ECMAScript that can be used to define an HTML-like tree structure in a JavaScript file. The JSX expressions in a JavaScript file must be transformed to JavaScript syntax before a JavaScript engine can parse the file. Babel is typically used, and recommended for transforming JSX expressions.

***

#### Node.js
An open-source, cross-platform runtime environment for writing JavaScript. The runtime environment interprets JavaScript using Google's V8 JavaScript engine.

***

#### npm
The package manager for JavaScript born from the Node.js community.

***

#### React attributes/props

In one sense you can think of props as the configuration options for React nodes and in another sense you can think of them as HTML attributes.

Props take on several roles:

1. Props can become HTML attributes.
2. Props become values stored in a `prop` object as a property of `React.createElement()` instances (i.e. `this.props.[NAME OF PROP]`).
3. A few special props have side effects (e.g. [`key`](https://facebook.github.io/react/docs/multiple-components.html#dynamic-children), [`ref`](https://facebook.github.io/react/docs/more-about-refs.html), and [`dangerouslySetInnerHTML`](https://facebook.github.io/react/tips/dangerously-set-inner-html.html))

***

#### React component

A React component is created by calling `React.createClass()` (or, `React.Component` if using ES6 classes). This function takes an object of options that is used to configure and create a React component. The most common configuration open is a `render` function that returns React nodes/JSX. Thus, you can think of a React component as an abstraction containing one or more React nodes/components.

***

#### React node factories

A function that generates a React element node with a particular type property.

***

#### React stateless function component



***

#### React element nodes (aka `ReactElement`)

An HTML or custom HTML element node representation in the Virtual DOM created using `React.createElement();`.

***

#### React text nodes (aka `ReactText`)
A text node representation in the Virtual DOM created using `React.createElement('div',null,'a text node');`.

***

#### React nodes
React nodes (i.e. element and text nodes) are the primary object type in React and can be created using `React.createElement('div');`. In other words React nodes are objects that represent DOM nodes and children DOM nodes. They are a light, stateless, immutable, virtual representation of a DOM node.

***

#### React
An open source JavaScript library for writing declarative, efficient, and flexible user interfaces.

***

#### Virtual DOM
A JavaScript tree of React elements/components that is used for efficient re-rendering (i.e. diffing via JavaScript) of the browser DOM.

***

#### Webpack

A module loader and bundler that takes modules (.js, .css, .txt, etc...) with dependencies and generates static assets representing those modules.
