# React Semantics

Before I enlighten anyone with the mechanics of React I'd first like to define a few terms so as to grease the learning process.

Below I list the most common terms, and their definitions, used when talking about React.

#### Babel
Babel is a generic multi-purpose compiler for JavaScript. Using Babel you can use (and create) the next generation of JavaScript, as well as the next generation of JavaScript tooling. Babel is the tool of choice from the React team for writing future ES* and transforming JSX to ES5 code.

***

#### ES5
he 5th edition of the ECMAScript standard. The ECMAScript 5.1 edition was finalized on June 2011.

***

#### ES6
The 6th edition of the ECMAScript standard. AKA JavaScript 2015. The ECMAScript 6th edition was finalized on June 2015.

***

#### ECMAScript 2016
Name of the specification that will provide updates to the JavaScript language in 2016. This edition of ECMAScript is still working towards being finalization.

***

#### ES\*
Used to represent the current version of JavaScript as well as potential future versions that can written today using tools like Babel. When you see "ES*" it more than likely means you'll find uses of ES5, ES6, and ES7 together.

***

#### Factories

A function that generates a React element node with a particular type property.

***

#### JSX
JSX is an optional XML-like syntax extension to ECMAScript that can be used to define an HTML-like tree structure in a JavaScript file. The JSX expressions in a JavaScript file must be transformed to JavaScript syntax before a JavaScript engine can parse the file. Babel is typically used, and recommended for transforming JSX expressions.

***

#### React attributes/props


***

#### React element nodes (aka `ReactElement`)

An HTML or custom HTML element node representation in the Virtual DOM created using `React.createElement('div');`.

***

#### React text nodes (aka `ReactText`)
A text node representation in the Virtual DOM created using `React.createElement('div',null,'a text node');`.

***

#### React nodes
React nodes (i.e. element and text nodes) are the primary object type in React and can be created using `React.createElement('div');`. In other words React nodes are objects that represent DOM nodes and children DOM nodes. They are a light, stateless, immutable, virtual representation of a DOM node.

***

#### Virtual DOM
A JavaScript tree of React elements/components that is used for efficient re-rendering (i.e. diffing via JavaScript) of the browser DOM.
