# What is React?

React is a JavaScript tool that makes it easy to reason about, construct, and maintain stateful user interfaces. It provides the means to divided the UI into React components made up of HTML like elements (aka React Elements). These components live in a tree, called the virtual DOM that is similar to the DOM tree created when HTML documents are parsed by browsers.

I could ramble on trying to express in words exact what React is, but I think it is best to just show you.

Below is a an HTML select element that encapsulates child HTML option elements.

```html
<select size="4">
  <option>Volvo</option>
  <option>Saab</option>
  <option selected>Mercedes</option>
  <option>Audi</option>
</select>
```

When a browser parses this tree of elements it produces the following UI.

[source code](https://jsfiddle.net/s2pxp36L/#tabs=[result,html])













