# Hands-On 2: React Components and Class Components

## Objective

The objective of this hands-on exercise is to understand React Components by creating multiple class components and rendering them inside the main application.

---

# Learning Objectives

After completing this exercise, you will be able to:

- Understand React Components
- Differentiate Components and JavaScript Functions
- Identify Functional and Class Components
- Understand Component Constructor
- Understand render() Method
- Create Multiple Components
- Render Components inside App.js

---

# Software Requirements

- Node.js
- npm
- Visual Studio Code
- ReactJS

---

# Project Name

StudentApp

---

# Scenario

Develop a Student Management Portal using React.

The application contains three components:

- Home
- About
- Contact

Each component displays a welcome message.

---

# Step 1: Create React Project

Open Terminal.

Execute

```bash
npx create-react-app StudentApp
```

---

# Step 2: Navigate into Project

```bash
cd StudentApp
```

---

# Step 3: Open Project

```bash
code .
```

---

# Step 4: Project Structure

```text
StudentApp
│
├── src
│   │
│   ├── Components
│   │      ├── Home.js
│   │      ├── About.js
│   │      └── Contact.js
│   │
│   ├── App.js
│   └── index.js
│
└── package.json
```

---

# Home.js

```javascript
import React, { Component } from 'react';

class Home extends Component {

    render() {

        return (

            <h1>
                Welcome to the Home page of Student Management Portal
            </h1>

        );
    }

}

export default Home;
```

---

# About.js

```javascript
import React, { Component } from 'react';

class About extends Component {

    render() {

        return (

            <h1>
                Welcome to the About page of the Student Management Portal
            </h1>

        );
    }

}

export default About;
```

---

# Contact.js

```javascript
import React, { Component } from 'react';

class Contact extends Component {

    render() {

        return (

            <h1>
                Welcome to the Contact page of the Student Management Portal
            </h1>

        );
    }

}

export default Contact;
```

---

# App.js

```javascript
import React from 'react';

import Home from './Components/Home';
import About from './Components/About';
import Contact from './Components/Contact';

function App() {

    return (

        <div>

            <Home />

            <About />

            <Contact />

        </div>

    );

}

export default App;
```

---

# Run the Application

Execute

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

```
Welcome to the Home page of Student Management Portal

Welcome to the About page of the Student Management Portal

Welcome to the Contact page of the Student Management Portal
```

---

# Explanation

## React Component

A React Component is an independent and reusable piece of UI.

---

## Class Component

A Class Component extends the React Component class and must contain a render() method.

Example

```javascript
class Home extends Component
```

---

## render() Method

The render() method returns JSX that is displayed in the browser.

---

## Constructor

A constructor initializes the state and properties of a class component.

Example

```javascript
constructor(props){

    super(props);

}
```

---

# Difference Between JavaScript Function and React Component

| JavaScript Function | React Component |
|---------------------|-----------------|
| Returns value | Returns JSX |
| Independent function | UI building block |
| No lifecycle methods | Supports lifecycle methods |

---

# Types of Components

### Functional Component

Simple JavaScript function returning JSX.

### Class Component

JavaScript class extending React.Component.

Supports lifecycle methods.

---

# Learning Outcome

- Created a React Application.
- Developed multiple Class Components.
- Rendered components using App.js.
- Understood render() method.
- Learned the difference between Functional and Class Components.

---

# Result

Successfully created a Student Management Portal using React by implementing Home, About, and Contact class components and rendering them within the main application.
