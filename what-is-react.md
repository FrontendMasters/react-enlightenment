# What is React?

React is a JavaScript tool that makes it easy to reason about, construct, and maintain stateful user interfaces. It provides the means to declaratively define and divided a UI into components (aka React components) made up of HTML like elements (aka React elements).

I could ramble on trying to express in words exact what React is, but I think it is best to just show you. Don't try and figure out all the details as I describe React using code. Just follow along grabbing a hold of the gist of it for now. The details will come in later chapters and most of what we do here will run but should be consider pseudo code given I know you won't understand the details yet.

## A React Component Whirl Wind Tour

Below is a an HTML `<select>` element that encapsulates child HTML `<option>` elements.

[source code](https://jsfiddle.net/s2pxp36L/#tabs=html,result)

When a browser parses this tree of elements it will of course produce a UI containing a textual list of items that can be selected. Click on "Result" tab, to see what the browser produces. 

The browser and the DOM (i.e. the shadow DOM) are working behind the scenes to turn the HTML into a `<select>` UI component. Note that the `<select>` component allows the user to make a selection thus storing the state of that selection (i.e. click on "Volvo", and you have selected it).

Using React we can essentially do the same exact thing but instead of using HTML elements and the DOM we use React elements and the virtual DOM.

Below I am creating a `<MySelect>` React component by extending (i.e. child class) the `React.Component` function using ES6 class syntax. 

As you can see the `<MySelect>` component is made up of a styled React `<div>` element.

```javascript
class MySelect extends React.Component {
    render() {
        var mySelectStyle = {
            border: '1px solid #999',
            display: 'inline-block',
            padding: '5px'
        };
        return <div style={mySelectStyle}></div>;
    }
};
```

Yes, that `<div>` is an HTML like tag, yes in JavaScript, called JSX. JSX is a custom JavaScript syntax used by React to express React elements that map to HTML elements. This syntax must be transformed from JSX to real JavaScript by a JavaScript transformer called Babel.

After Babel transforms the JSX into an real JavaScript containing it will look like this:

```javascript
return React.createElement('div', { style: mySelectStyle });
```

For now, just keep in mind that the HTML elements that you see in JavaScript are being transformed into actual JavaScript/React code by Babel along with ES6 syntax (i.e. `class`, `extends`, etc...).

My `<MySelect>` component at this point consist of an empty React `<div>` element. Let's change that. 

Below I am going to define another component called `<MyOption>` and then use the `<MyOption>` component within the `<MySelect>` component (aka composition).

```javascript
class MySelect extends React.Component {
    render() {
        var mySelectStyle = {
            border: '1px solid #999',
            display: 'inline-block',
            padding: '5px'
        };
        return (
            <div style={mySelectStyle}>
                <MyOption value="Volvo"></MyOption>
                <MyOption value="Saab"></MyOption>
                <MyOption value="Mercedes"></MyOption>
                <MyOption value="Audi"></MyOption>
            </div>
        );
    }
};

class MyOption extends React.Component {
    render() {
        return <div>{this.props.value}</div>;
    }
};
```

The first thing you should notice is that the `<MyOption>` component is made up of one `<div>` containing the expression `{this.props.value}`. The `{}` brackets indicate to JSX that a JavaScript expression is being used. Inside of the `{}` brackets JavaScript is used to gain access (i.e. `this.props.value`) to the properties or attributes passed by the `<MyOption>` component. In other words when the `<MyOption>` component is rendered the value passed, via what looks like an HTML attribute (i.e. `value="Volvo"`) will be placed into the `<div>`. These HTML looking attributes are consider React props. React uses them to pass state-less/immutable options into components.

At this point our JavaScript only defines two React Components. We have yet to actually render these components to the Virtual Dom.

Before we do that I'd like to mention that up to this point all we have done is define a UI component. In theory, the file is just the definition of a UI component. This same definition could also be used to render this component to a [native mobile platform](https://github.com/facebook/react-native) or an [HTML canvas](https://github.com/Flipboard/react-canvas). But we're not going to do that, even though one do could that. 

Let's instead now render the `<MyOption>` component to the virtual DOM which in turn will render it to the actual DOM inside of an HTML page.

In the JavaScript below, specifically the last line, notice I added a call to the `ReactDOM.render()` function. Here I am passing the function the component we want to render (i.e. `<MyOption>`) and a reference to the HTML element already in the DOM (i.e. `<div id="app"></div>`) where I want to render my React `<MyOption>` component. Click on the "Result" tab and you will see our custom React `<MyOption>` component rendered to the HTML DOM.

[source code](https://jsfiddle.net/zp86ez31/#tabs=js,result,html,resources)

Hold up you might be thinking. We haven't actually re-created a select at all. All we have is a static list of text and we had to write a lot of JavaScript to get it.

Before I move on I want to point out that no implicit DOM interactions we're written to get the `<MyOption>` component into the real DOM. No jQuery was used. The dealings with the actual DOM have all been abstracted. That's pretty neat. Right? Don't answer yet, there is more to come.

In order for our `<MyOption>` component to mimic a native `<select>` element we are going to have to add some state. State typically gets involved when a component contains a serialize snapshot of information. In regards to our custom `<MyOption>` component, it must keep track of which of if a selection of text has been made and if so which one. Note that, state will typically involved user or network events.
























