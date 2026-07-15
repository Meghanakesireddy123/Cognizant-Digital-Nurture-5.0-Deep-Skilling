# Hands-On 11: React Event Handling and Currency Converter

## Objective

The objective of this hands-on exercise is to understand React Event Handling by implementing button click events, multiple event handlers, passing arguments to event handlers, synthetic events, and a simple Currency Converter component.

---

# Learning Objectives

After completing this exercise, you will be able to:

- Understand React Events.
- Implement Event Handling in React.
- Understand Event Handlers.
- Use the `this` keyword in Class Components.
- Understand Synthetic Events.
- Pass arguments to event handlers.
- Invoke multiple methods from a single event.
- Develop a Currency Converter component.

---

# Software Requirements

- Node.js
- npm
- Visual Studio Code
- ReactJS

---

# Project Name

eventexamplesapp

---

# Scenario

Develop a React application demonstrating different Event Handling concepts.

The application should provide:

- Increment Counter
- Decrement Counter
- Say Hello Button
- Say Welcome Button
- Synthetic Event Button
- Currency Converter

---

# Step 1: Create React Project

Open Terminal.

Execute:

```bash
npx create-react-app eventexamplesapp
```

---

# Step 2: Navigate into Project

```bash
cd eventexamplesapp
```

---

# Step 3: Open Project

```bash
code .
```

---

# Project Structure

```text
eventexamplesapp
│
├── src
│
├── Components
│      ├── Counter.js
│      ├── CurrencyConverter.js
│
├── App.js
│
└── package.json
```

---

# Counter.js

```javascript
import React, { Component } from "react";

class Counter extends Component {

    constructor(props) {

        super(props);

        this.state = {

            count: 0

        };

    }

    increment = () => {

        this.setState({

            count: this.state.count + 1

        });

    }

    decrement = () => {

        this.setState({

            count: this.state.count - 1

        });

    }

    sayHello = () => {

        alert("Hello! Welcome to React Event Handling.");

    }

    handleIncrement = () => {

        this.increment();

        this.sayHello();

    }

    sayWelcome = (message) => {

        alert(message);

    }

    handleClick = () => {

        alert("I was clicked");

    }

    render() {

        return (

            <div>

                <h2>Counter : {this.state.count}</h2>

                <button onClick={this.handleIncrement}>

                    Increment

                </button>

                <button onClick={this.decrement}>

                    Decrement

                </button>

                <br/><br/>

                <button

                    onClick={() => this.sayWelcome("Welcome")}

                >

                    Say Welcome

                </button>

                <br/><br/>

                <button onClick={this.handleClick}>

                    OnPress

                </button>

            </div>

        );

    }

}

export default Counter;
```

---

# CurrencyConverter.js

```javascript
import React, { Component } from "react";

class CurrencyConverter extends Component {

    constructor(props){

        super(props);

        this.state={

            rupees:1000,

            euro:0

        };

    }

    handleSubmit=()=>{

        const euroValue=

        (this.state.rupees/90).toFixed(2);

        this.setState({

            euro:euroValue

        });

    }

    render(){

        return(

            <div>

                <h2>Currency Converter</h2>

                <p>

                    Indian Rupees :

                    {this.state.rupees}

                </p>

                <button

                    onClick={this.handleSubmit}

                >

                    Convert

                </button>

                <h3>

                    Euro :

                    {this.state.euro}

                </h3>

            </div>

        );

    }

}

export default CurrencyConverter;
```

---

# App.js

```javascript
import React from "react";

import Counter from "./Components/Counter";

import CurrencyConverter
from "./Components/CurrencyConverter";

function App(){

    return(

        <div>

            <Counter/>

            <hr/>

            <CurrencyConverter/>

        </div>

    );

}

export default App;
```

---

# Run the Application

Execute:

```bash
npm start
```

---

# Browser URL

```
http://localhost:3000
```

---

# Expected Output

### Counter Section

```
Counter : 0

[Increment]

[Decrement]

[Say Welcome]

[OnPress]
```

- Clicking **Increment** increases the counter and displays:

```
Hello! Welcome to React Event Handling.
```

- Clicking **Decrement** decreases the counter.

- Clicking **Say Welcome** displays:

```
Welcome
```

- Clicking **OnPress** displays:

```
I was clicked
```

---

### Currency Converter

```
Indian Rupees : 1000

[Convert]

Euro : 11.11
```

---

# Explanation

## React Events

React Events allow components to respond to user actions such as mouse clicks, keyboard input, and form submissions.

---

## Event Handler

An Event Handler is a function executed when an event occurs.

Example:

```javascript
<button onClick={this.handleIncrement}>
```

---

## Multiple Methods on One Event

One button click can invoke multiple methods.

Example:

```javascript
handleIncrement(){

    this.increment();

    this.sayHello();

}
```

---

## Passing Arguments

Arguments are passed using Arrow Functions.

Example:

```javascript
onClick={() => this.sayWelcome("Welcome")}
```

---

## Synthetic Event

React wraps browser events inside Synthetic Events for consistent behavior across different browsers.

Example:

```javascript
onClick={this.handleClick}
```

---

## this Keyword

The `this` keyword refers to the current component instance and allows access to state and methods.

Example:

```javascript
this.state.count
```

---

# React Event Naming Convention

| HTML | React |
|------|-------|
| onclick | onClick |
| onchange | onChange |
| onsubmit | onSubmit |
| onkeypress | onKeyPress |

---

# Benefits of React Events

- Cross-browser compatibility
- Better performance
- Easy event handling
- Cleaner code
- Supports Synthetic Events

---

# Learning Outcome

- Implemented React Event Handling.
- Used Event Handlers.
- Passed Arguments to Functions.
- Invoked Multiple Methods.
- Used Synthetic Events.
- Implemented Currency Conversion.

---

# Result

Successfully implemented React Event Handling concepts by developing an Event Examples application featuring counter operations, multiple event handlers, argument passing, synthetic events, and a Currency Converter component using React Class Components.
