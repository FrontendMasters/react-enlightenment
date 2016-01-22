# What is React?

React is a JavaScript tool that makes it easy to reason about, construct, and maintain stateless and stateful user interfaces. It provides the means to declaratively define and divide a UI into components (aka React components) made up of HTML like elements (aka React elements). 

I could ramble on trying to express in words what React is, but I think it is best just to show you. Don't try and figure out all the details as I describe React using code in this section. Just follow along grabbing a hold of the gist of it for now. The fine details will come later.

### A whirl wind tour of React components

Below is a an HTML `<select>` element that encapsulates child HTML `<option>` elements.

[source code](https://jsfiddle.net/s2pxp36L/#tabs=html,result)

When a browser parses this tree of elements it will produce a UI containing a textual list of items that can be selected. Click on the "Result" tab, to see what the browser produces.

The browser, the DOM, and the shadow DOM are working together behind the scenes to turn the `<select>` HTML into a UI component. Note that the `<select>` component allows the user to make a selection thus storing the state of that selection (i.e. click on "Volvo", and you have selected it instead of "Mercedes").

Using React we can essentially do the same exact thing but instead of using HTML elements directly we use React elements and the virtual DOM that in turn will create real HTML elements in an HTML DOM.

##### Defining a component

Below I am creating a `<MySelect>` React component by invoking the `React.createClass` function in order to create a `MySelect` class. 

As you can see the `MySelect` component is made up of an empty styled React `<div>` element.

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

That `<div>` is an HTML like tag, yes in JavaScript, called [JSX](https://facebook.github.io/jsx/). JSX is a custom JavaScript syntax used by React to express React elements that map to real HTML elements. React elements, defined using JSX should not be considered a one to one match to HTML elements. There are [differences](https://facebook.github.io/react/docs/dom-differences.html) and some [gotchas](https://facebook.github.io/react/docs/jsx-gotchas.html). 

JSX syntax must be transformed from JSX to real JavaScript in order to be parsed by ES5 browsers. The tool used to transform JSX is called [Babel](http://babeljs.io/).

After Babel transforms the JSX into real JavaScript, it will look like this:

```javascript
return React.createElement('div', { style: mySelectStyle });
```

instead of this:

```javascript
return <div style={mySelectStyle}></div>;
```

For now, just keep in mind that the HTML elements that you see in React JavaScript code are being transformed into actual JavaScript/React code by Babel along with ES6 syntax.

The `<MySelect>` component at this point consist of an empty React `<div>` element. That seems rather pointless, so let's change that. 

I'm going to define another component called `<MyOption>` and then use the `<MyOption>` component within the `<MySelect>` component (aka composition).

Examine updated JavaScrip code below which defines both the `<MySelect>` and `<MyOption>` component.

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

The first thing you should notice in the update code is that the `<MyOption>` component is made up of one `<div>` containing the expression `{this.props.value}`. The `{}` brackets indicate to JSX that a JavaScript expression is being used. Inside of the `{}` brackets JavaScript is used to gain access (i.e. `this.props.value`) to the properties or attributes passed by the `<MyOption>` component. In other words when the `<MyOption>` component is rendering the value passed, via what looks like an HTML attribute (i.e. `value="Volvo"`) and that value will be placed into the `<div>`. These HTML looking attributes are consider React props. React uses them to pass stateless/immutable options into components.

##### Rendering a component to the Virtual DOM, then HTML DOM

At this point our JavaScript only defines two React Components. We have yet to actually render these components to the Virtual DOM and thus HTML DOM.

Before we do that I'd like to mention that up to this point all we have done is define a UI component made up of two React components. In theory, the JavaScript we have so far is just the definition of a UI component. This same definition, in theory, could also be used to render this component to a [native mobile platform](https://github.com/facebook/react-native) or an [HTML canvas](https://github.com/Flipboard/react-canvas). But we're not going to do that, even though one could do that. Just be aware that React is a pattern for organizing a UI that can transcend the DOM.

Let's now render the `<MyOption>` component to the virtual DOM which in turn will render it to the actual DOM inside of an HTML page.

In the JavaScript below notice I added a call to the `ReactDOM.render()` function on the last line. Here I am passing the `ReactDOM.render()`  function the component we want to render (i.e. `<MyOption>`) and a reference to the HTML element already in the DOM (i.e. `<div id="app"></div>`) where I want to render my React `<MyOption>` component. Click on the "Result" tab and you will see our custom React `<MyOption>` component rendered to the HTML DOM.

[source code](https://jsfiddle.net/zp86ez31/#tabs=js,result,html,resources)

Hold up, you might be thinking. We haven't actually re-created a `<select>`` at all and you'd be right. All we have is a static/stateless list of text. We'll fix that next.

Before I move on I want to point out that no implicit DOM interactions we're written to get the `<MyOption>` component into the real DOM. In other words, no jQuery code was invoke during the creation of this component. The dealings with the actual DOM have all been abstracted. That's pretty neat. Right?

##### React state

In order for our `<MyOption>` component to mimic a native `<select>` element we are going to have to add state. State typically gets involved when a component contains snapshots of information. In regards to our custom `<MyOption>` component, it's state is the currently selected text or the fact that no text is selected at all. Note that state will typically involved user or network events.

State is typically found on the top most component which makes up a UI component. Using the `getInitialState` function we can set the default state of our component to `false` by returning a state object (i.e. `return {selected: false};`) when `getInitialState` is invoked.

```javascript
var MySelect = React.createClass({
    getInitialState: function(){ //add selected state
        return {selected: false};
    },
    render: function(){
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
});

var MyOption = React.createClass({
    render: function(){
        return <div>{this.props.value}</div>;
    }
});
```

With the state setup next we'll add a callback function called `select` that gets called when a user clicks on an option. Inside of this function we get the text of the option that was selected and use that to determine how to set the current state of the component. 

```javascript
var MySelect = React.createClass({
    getInitialState: function(){
        return {selected: false};
    },
    select:function(event){// added select function
        if(event.target.textContent === this.state.selected){//remove selection
            this.setState({selected: false});
        }else{//add selection
            this.setState({selected: event.target.textContent});
        }   
    },
    render: function(){
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
});

var MyOption = React.createClass({
    render: function(){
        return <div>{this.props.value}</div>;
    }
});
```

In order for our `<MyOption>` components to gain access to the `select` function we'll have to pass a reference to it, via props, from the `<MySelect>` component to the `<MyOption>` component. To do this we add `select={this.select}` to the `<MyOption>` components. With that in place we can add `onClick={this.props.select}` to the `<MyOption>` component JSX.

```javascript
var MySelect = React.createClass({
    getInitialState: function(){
        return {selected: false};
    },
    select:function(event){
        if(event.target.textContent === this.state.selected){
            this.setState({selected: false});
        }else{
            this.setState({selected: event.target.textContent});
        }   
    },
    render: function(){
        var mySelectStyle = {
            border: '1px solid #999',
            display: 'inline-block',
            padding: '5px'
        };
        return (//pass reference, using props, to select callback to <MyOption>
            <div style={mySelectStyle}>
                <MyOption select={this.select} value="Volvo"></MyOption>
                <MyOption select={this.select} value="Saab"></MyOption>
                <MyOption select={this.select} value="Mercedes"></MyOption>
                <MyOption select={this.select} value="Audi"></MyOption>
            </div>
        );
    }
});

var MyOption = React.createClass({
    render: function(){//add event handler that will invoke select callback
        return <div onClick={this.props.select}>{this.props.value}</div>;
    }
});
```

By doing all this we can now set the state by clicking on one of the options.However, the UI user of the component has no idea this is being done because all we have done is update our code so that state is managed by the component.

The next thing we will need to do is also pass the current state down to the `<MyOption>` component so that it can respond visually to the state of the component.

Using props, again, we will pass the state in the `<MySelect>` down to an option component by placing the property `state={this.state.selected}` on all of the `<MyOption>` components. Now that we know the state (i.e. `this.props.state`) and the current `value` (i.e. `this.props.value`) of the option we can verify if the state matches the value. If it does, we then know that this option should be selected. And we'll write a simple if statement add a styled state to the option if the state matches the value of the current option.

```javascript
var MySelect = React.createClass({
    getInitialState: function(){
        return {selected: false};
    },
    select:function(event){
        if(event.target.textContent === this.state.selected){
            this.setState({selected: false});
        }else{
            this.setState({selected: event.target.textContent});
        }   
    },
    render: function(){
        var mySelectStyle = {
            border: '1px solid #999',
            display: 'inline-block',
            padding: '5px'
        };
        return (//pass state, using props, to <MyOption>
            <div style={mySelectStyle}>
                <MyOption state={this.state.selected}  select={this.select} value="Volvo"></MyOption>
                <MyOption state={this.state.selected}  select={this.select} value="Saab"></MyOption>
                <MyOption state={this.state.selected}  select={this.select} value="Mercedes"></MyOption>
                <MyOption state={this.state.selected}  select={this.select} value="Audi"></MyOption>
            </div>
        );
    }
});

var MyOption = React.createClass({
    render: function(){
        var selectedStyle = {backgroundColor:'red', color:'#fff',cursor:'pointer'};
        var unSelectedStyle = {cursor:'pointer'};
        if(this.props.value === this.props.state){
            return <div style={selectedStyle} onClick={this.props.select}>{this.props.value}</div>;
        }else{
            return <div style={unSelectedStyle} onClick={this.props.select}>{this.props.value}</div>;
        }
    }
});
```

[source code](https://jsfiddle.net/L1z9za23/#tabs=js,result,html,resources)






























