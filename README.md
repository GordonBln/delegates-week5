# delegates-week5

## delegates this week: Jessica and Marek

---

### React

- **React** is an open-source, front end JavaScript library built / maintained by Facebook as well as a community of individual developers and companies. The first version dates back from 2013
  It's purpose is to build user interfaces or UI components.
  React can be used as a base in the development of single-page applications.

## It's used by:

- Facebook
- Netflix
- airbnb
- Instagram

### **Components**

## What is a Component?

- They are essentially building blocks to our applications.
- The term "component" is used to mean an element or section of a page as shown in the image below.
- They divide and isolate elements within the UI for both visual and behavioural purposes.
- A component can be broken down further and contain other components to make up pages such as in the image below.
- The image contains multiple components which would make up a page component e.g Homepage.

![alt text](https://codippa.com/wp-content/uploads/2019/02/react-component-2.png)

## Component Hierarchy

A component can contain multiple components (children) so we end up with a component hierarchy.

- Within React there is a Hierarchy which occurs when building and scaling our applications.
- Typically in most apps we have a Root Component called App this is where all other components end up reaching through the component tree.
- As we can see inside the App Component there is a child component called Contacts.
- Contacts contains the following child components AddContact, ContactList & SearchBar.
- AddContact contains a child component AddContactForm.
- ContactList also contains a child component ContactCard.

![alt text](https://storage.googleapis.com/quest_editor_uploads/CywzyRPJDjWtsAQLfXHVQnK7mktTGNwc.png)

[More info here](https://reactjs.org/docs/thinking-in-react.html#step-1-break-the-ui-into-a-component-hierarchy)

## Types of Components

### Class Component

```javascript
import React, { Component } from "react";
import HelloWild from "./HelloWild";
import "./App.css";

class App extends Component {
  render() {
    return (
      <div className="App">
        <header className="App-header">
          <HelloWild />
        </header>
        <p className="App-intro">Hello World!</p>
      </div>
    );
  }
}

export default App;
```

- class inherits from React.Component

- the render() method must return JSX or null

### Class components MUST have a render method!

### functional component

```javascript
import React from "react";

const HelloWild = () => (
  <div className="hello-wild">
    <h1>Hello Wild</h1>
  </div>
);

export default HelloWild;
```

- It’s a regular JS function

- the name must start with a capital letter

### The function must return JSX or null

## JSX

### What is JSX?

It is a syntax extension to JavaScript. It is used with React to describe what the UI should look like. JSX may remind you of a template language, but it comes with the full power of JavaScript. It looks like HTML but in essence it combines HTML and JavaScript together.

- JSX = Javascript + XML

- JSX is neither HTML nor a string

```javascript
// HelloWild component
const HelloWild = () => {
return(

<div>
<h1>Hello Wild</h1>
  </div>
)
}

// calling HelloWild component on React App
<HelloWild />

// DOM

<div><h1>Hello Wild</h1></div>
```

## Tooling

### A common React app requires some third party tools to run, namely:

- Webpack - Webpack is a bundler. Among other things. It mashes all your .js files and .css files into one .js and one .css

- Babel - Babel is a Javascript transpiler. It allows you to use the newest, sexiest JS features and still be compatible with all (most) browsers.

## Create React App

Create React App configures all the necessary tools for us.
It’s easier and faster to get started.

### You can find ih here --> [https://github.com/facebook/create-react-app](https://github.com/facebook/create-react-app)

# React - Props

### What are Props?

“Props” is a special keyword in React, which stands for properties and they are used for passing data from one component to another. Furthermore, props data is read-only, which means that data coming from the Parent should not be changed by Child components.

Props are passed from Parent components to Child components.

In this example, only one property is passed to the Welcome component, in the form of a key-value pair. The key is name, the value is the string "Sara". But just like with HTML attributes, you can pass several key-value pairs, i.e. grouping props within the same object and passing them to the component. To make it a little more visual:

![alt text](https://images.innoveduc.fr/react/02-component/react-props-1.svg)

-Below we show how the Child component will receive the props object and display the name prop.

```javascript
import React from "react";

function Welcome(props) {
  return (
    <div>
      <p>{props.name}</p>
    </div>
  );
}

export default Welcome;
```

## Access props

### Props are accessible in the child component (read only):

- via this.props in a class component
- via props in a functional component

## Boolean props

In the case of Boolean props, it is not necessary to pass a true/false value , you only have to pass the prop name.

```javascript
// App.js
const App = () => (
  <div>
    <Person name="Homer" food="donuts" />
    <Person name="Lisa" food="vegetables" hasFood />
  </div>
);

// Person.js
const Person = (props) => {
  if (props.hasFood) {
    return <div>Gonna eat {props.food}!</div>;
  }
  return <div>No more {props.food} :/</div>;
};
```

- For Lisa, props.hasFood equals true. For Homer, props.hasFood equals undefined, which is a “falsy” value (considered as false in a Boolean expression assessment).

## Destructing props

It is good practice to destructure props, in order to make your JSX more readable.

```javascript
// class component
class User extends Component {
  render() {
    const { name, avatar } = this.props;
    return (
      <div>
        <h3>{name}</h3>
        <img src={avatar} />
      </div>
    );
  }
}

// functional component
const User = ({ name, avatar }) => (
  <div>
    <h3>{name}</h3>
    <img src={avatar} />
  </div>
);
```

## Using the spread operator

The spread operator is used to pass all key/values of an object as individual props (spread them).

```javascript
// App.js
const article = {
  title: "Panic in Springfield",
  text: "Homer blew the nuclear plant",
};

const App = () => <Article {...article} />;

// Article.js
const Article = ({ title, text }) => (
  <div>
    <h2>{title}</h2>
    <p>{text}</p>
  </div>
);
```

- In the example, the Article component receives a title and a text as individual props.

## API

- What's an **API**?

An API (Application Programming Interface) serves as a middleware that lets you channel data between software products.
It is a server that exposes data and functions through the HTTP protocol.

You can use it to define requests that have been made, handle business logic, the and manage data formats that should be used and the conventions to adhere to when building software products.

- Why do we need **API's** ?

APIs make it easier to access to a variety of resources. They also allow cross-platform communication which solves certain business logic.

As webservices usually respond with raw data (formatted in JSON), the API client is free to display the data however he wants.

An API can provide data you need without requiring extra research or manipulation which speeds up the development process.
They also provide user-friendly endpoints specific to certain use cases.

- API Tools:
  **POSTMAN**
  A collaboration platform for API development.
  Simplify each step of building an API and streamline collaboration so you can create better APIs—faster.

**REST**
This tool simplifies testing API endpoints in Java – yes JAVA. It tests and validates responses, making it seamless for Java devs to test APIs.

## Express

../\* **Express** is a framework for Node.js that gives us access to a lot of powerful and simple tools that we can use to create and configure our server quickly.

It allows rapid development of Webservices as it provides straightforward ways to handle HTTP requests.

- Avantages Perks of Express.js:
  Well documented
  Big community
  Performant
  Lightweight
  Unopinionated

- How to install it?
  Step 1
  $ mkdir my-api
  $ cd my-api
  $ touch index.js

Step 2
$ npm init && git init

Step 3
$ npm install express

- Why we use **Nodemon**?
  Reloading your server all the time can be quite annoying, to avoid that, you can use a Node package called Nodemon.
  Nodemon will listen for changes in your files and will automatically reload the server.

- How to install **Nodemon**?
  Step 1
  $ npm install nodemon --save-dev

Step 2
"scripts": {
"start": "nodemon index.js"
}

Step 3
<img src="https://i.imgur.com/vkF1kBZ.png">

- How to create a route?

const express = require("express");
const app = express();

const port = 3000;

app.get("/", (request, response) => {
console.log(request);
response.send("Welcome to Express");
});

app.listen(port, () => {
console.log(`Server is runing on ${port}`);
});

- What's a **Request** ?
  The request object represents the HTTP request. It contains information such as:
  HTTP header,
  The request body (what is sent with the request),
  Form data,
  Url params and query string, ...

- What's a **Query String** ?
  The query property is an object that will contain a property for each query string passed in the URL.

Example:
// GET /search?name=tobi+ferret
res.send(request.query.name)
// => 'tobi ferret'

// GET /shoes?order=desc&color=blue
res.send(req.query.color)
// => 'blue'

- What's a **Response** ?
  The response object represents the HTTP response that the server sends to the client. It can contain data, messages (validation, error), or simply a status corresponding to the state of the request processed by the server.
