# What is React?

React is a JavaScript tool that makes it easy to reason about, construct, and maintain stateless and stateful user interfaces. It provides the means to declaratively define and divide a UI into components (aka React components) made up of HTML like elements (aka React elements). 

I could ramble on trying to express in words what React is, but I think it is best just to show you. Don't try and figure out all the details as I describe React using code in this section. Just follow along grabbing a hold of the gist of it for now. The fine details will come later.

### A whirl wind tour of React components

Below is a an HTML `<select>` element that encapsulates child HTML `<option>` elements.

[source code](https://jsfiddle.net/s2pxp36L/#tabs=html,result)

When a browser parses this tree of elements it will produce a UI containing a textual list of items that can be selected. Click on the "Result" tab, to see what the browser produces.

The browser and the DOM (i.e. the shadow DOM) are working together behind the scenes to turn the `<select>` HTML into a UI component. Note that the `<select>` component allows the user to make a selection thus storing the state of that selection (i.e. click on "Volvo", and you have selected it instead of "Mercedes").

Using React we can essentially do the same exact thing but instead of using HTML elements directly we use React elements and the virtual DOM than in turn will create real HTML elements and DOM structures.

##### Defining a component

Below I am creating a `<MySelect>` React component by invoking the `React.createClass` function in order to create a `<MySelect>` class. 

As you can see the `<MySelect>` component is made up of an empty styled React `<div>` element.

```javascript
var MySelect = React.createClass({ //define MySelect component
    render: function(){
        var mySelectStyle = {
            border: '1px solid #999',
            display: 'inline-block',
            padding: '5px'
        };
        return <div style={mySelectStyle}></div>; //react div element, via JSX
    }
});
```

That `<div>` is an HTML like tag, yes in JavaScript, called JSX. JSX is a custom JavaScript syntax used by React to express React elements that map to HTML elements. This syntax must be transformed from JSX to real JavaScript by a JavaScript transformer called [Babel](http://babeljs.io/).

After Babel transforms the JSX into real JavaScript, it will look like this:

```javascript
return React.createElement('div', { style: mySelectStyle });
```

instead of this:

```javascript
return <div style={mySelectStyle}></div>;
```

For now, just keep in mind that the HTML elements that you see in React JavaScript code are being transformed into actual JavaScript/React code by Babel along with ES6 syntax (i.e. `class`, `extends`, etc...).

My `<MySelect>` component at this point consist of an empty React `<div>` element. Let's change that. 

I'm going to define another component called `<MyOption>` and then use the `<MyOption>` component within the `<MySelect>` component (aka composition). Examine the changes in the code below.

```javascript
var MySelect = React.createClass({
    render: function(){
        var mySelectStyle = {
            border: '1px solid #999',
            display: 'inline-block',
            padding: '5px'
        };
        return ( //react div element, via JSX, containing <MyOption> component
            <div style={mySelectStyle}>
                <MyOption value="Volvo"></MyOption>
                <MyOption value="Saab"></MyOption>
                <MyOption value="Mercedes"></MyOption>
                <MyOption value="Audi"></MyOption>
            </div>
        );
    }
});

var MyOption = React.createClass({  //define MyOption component
    render: function(){
        return <div>{this.props.value}</div>; //react div element, via JSX
    }
});
```


##### React props

The first thing you should notice is that the `<MyOption>` component is made up of one `<div>` containing the expression `{this.props.value}`. The `{}` brackets indicate to JSX that a JavaScript expression is being used. Inside of the `{}` brackets JavaScript is used to gain access (i.e. `this.props.value`) to the properties or attributes passed by the `<MyOption>` component. In other words when the `<MyOption>` component is rendered the value passed, via what looks like an HTML attribute (i.e. `value="Volvo"`) will be placed into the `<div>`. These HTML looking attributes are consider React props. React uses them to pass stateless/immutable options into components.

##### Rendering a component to the Virtual DOM, then HTML DOM

At this point our JavaScript only defines two React Components. We have yet to actually render these components to the Virtual DOM and HTML DOM.

Before we do that I'd like to mention that up to this point all we have done is define a UI component. In theory, the file is just the definition of a UI component. This same definition could also be used to render this component to a [native mobile platform](https://github.com/facebook/react-native) or an [HTML canvas](https://github.com/Flipboard/react-canvas). But we're not going to do that, even though one do could that. Just be aware that React is a pattern for organizing a UI that can transcends HTML pages.

Let's now render the `<MyOption>` component to the virtual DOM which in turn will render it to the actual DOM inside of an HTML page.

In the JavaScript below notice I added a call to the `ReactDOM.render()` function on the last line. Here I am passing the `ReactDOM.render()`  function the component we want to render (i.e. `<MyOption>`) and a reference to the HTML element already in the DOM (i.e. `<div id="app"></div>`) where I want to render my React `<MyOption>` component. Click on the "Result" tab and you will see our custom React `<MyOption>` component rendered to the HTML DOM.

[source code](https://jsfiddle.net/zp86ez31/#tabs=js,result,html,resources)

Hold up, you might be thinking. We haven't actually re-created a select at all. All we have is a static/stateless list of text.

Before I move on I want to point out that no implicit DOM interactions we're written to get the `<MyOption>` component into the real DOM. In other words, no jQuery invoke in the creation of this component. The dealings with the actual DOM have all been abstracted. That's pretty neat. Right? Don't answer yet, there is more to come.

##### React state

In order for our `<MyOption>` component to mimic a native `<select>` element we are going to have to add state. State typically gets involved when a component contains snapshots of information. In regards to our custom `<MyOption>` component, it's state is the currently selected text or the fact that no text is selected at all. Note that state will typically involved user or network events.

[source code](https://jsfiddle.net/L1z9za23/#tabs=js,result,html,resources)

1. When can we talk about React and NG2 components
2. Talk about React
3. Talk about NG2
4. Talk about ES6, Babel, and webpack/systemJS,rollup
5. Talk about how to use Kendo UI with React/NG2 ...ideal way until real thing happens
6. 




























