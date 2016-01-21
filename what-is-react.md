# What is React?

React is a JavaScript tool that makes it easy to reason about, construct, and maintain stateful user interfaces. It provides the means to divided a UI into  components (aka React components) made up of HTML like elements (aka React elements). These components live in a tree, called the virtual DOM that is similar to the DOM tree created when HTML documents are parsed by browsers.

I could ramble on trying to express in words exact what React is, but I think it is best to just show you. Don't try and figure out all the details as I describe React using code. Just follow along grabbing a hold of the gist of it for now. The details will come in later chapters.

## React Components

Below is a an HTML `<select>` element that encapsulates child HTML `<option>` elements.

[source code](https://jsfiddle.net/s2pxp36L/#tabs=html,results)

When a browser parses this tree of elements it will of course produce a UI containing a textual list of items that can be selected (click on results, to see what the browser produces). The browser and the DOM (aka shadow DOM) are working behind the scenes to turn the HTML into a UI component. Note that the select component allows the user to make a selection and thus storing the state of that selection (i.e. click on "Volvo", and you have selected it).

Using React we can essentially do the same exact thing but instead of using HTML elements and the DOM we use React elements and the virtual DOM.

```javascript

```


[source code](https://jsfiddle.net/zp86ez31/#tabs=javascript,hmlt,results)


















