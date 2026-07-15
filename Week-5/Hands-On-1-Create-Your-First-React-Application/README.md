# Hands-On 1: Create Your First React Application

## Objective

The objective of this hands-on exercise is to set up a React development environment, create a React application using **Create React App**, understand the basic project structure, and display a simple welcome message in the browser.

---

# Learning Objectives

After completing this exercise, you will be able to:

* Understand Single Page Applications (SPA).
* Explain the benefits of SPA.
* Understand the basics of React.
* Differentiate between SPA and MPA.
* Explain the Virtual DOM.
* Identify the key features of React.
* Create a React application using Create React App.
* Run a React application locally.

---

# Prerequisites

The following software should be installed before starting this exercise:

* Node.js
* npm (Node Package Manager)
* Visual Studio Code
* Google Chrome or any modern web browser

---

# What is a Single Page Application (SPA)?

A Single Page Application (SPA) is a web application that loads a single HTML page and dynamically updates its content without refreshing the entire page.

### Benefits of SPA

* Faster page loading
* Better user experience
* Reduced server requests
* Smooth navigation
* Improved performance

---

# Difference Between SPA and MPA

| SPA                         | MPA                       |
| --------------------------- | ------------------------- |
| Loads one HTML page         | Loads multiple HTML pages |
| Faster navigation           | Slower navigation         |
| Uses JavaScript extensively | Server renders every page |
| Better user experience      | Frequent page reloads     |

---

# What is React?

React is an open-source JavaScript library developed by Facebook for building fast, interactive, and reusable user interfaces.

---

# Features of React

* Component-Based Architecture
* Virtual DOM
* One-Way Data Binding
* JSX Support
* High Performance
* Reusable Components
* Easy Integration

---

# What is Virtual DOM?

The Virtual DOM is a lightweight copy of the Real DOM maintained by React. Whenever the application state changes, React updates the Virtual DOM first, compares it with the previous version, and updates only the modified parts of the Real DOM, improving application performance.

---

# Software Requirements

* Node.js
* npm
* Visual Studio Code
* React
* Create React App

---

# Step 1: Install Node.js

Download and install Node.js from:

```text
https://nodejs.org/en/download/
```

Node.js installation also installs npm automatically.

---

# Step 2: Install Create React App

Open Command Prompt and execute:

```bash
npm install -g create-react-app
```

---

# Step 3: Create React Application

Execute the following command:

```bash
npx create-react-app myfirstreact
```

This creates a new React project named **myfirstreact**.

---

# Step 4: Navigate to the Project

```bash
cd myfirstreact
```

---

# Step 5: Open Project in Visual Studio Code

```bash
code .
```

---

# Step 6: Replace App.js

Open:

```text
src/App.js
```

Replace the existing code with:

```javascript
function App() {
    return (
        <div>
            <h1>Welcome to the First Session of React</h1>
        </div>
    );
}

export default App;
```

---

# Step 7: Run the Application

Execute the following command:

```bash
npm start
```

The React development server starts successfully.

---

# Project Structure

```text
myfirstreact
│
├── node_modules
├── public
├── src
│   ├── App.js
│   ├── index.js
│   └── index.css
│
├── package.json
└── README.md
```

---

# Browser URL

```text
http://localhost:3000
```

---

# Expected Output

```text
Welcome to the First Session of React
```

The browser displays the heading:

# Welcome to the First Session of React

---

# Explanation of App.js

### Function Component

```javascript
function App()
```

Creates a functional React component.

---

### JSX

```javascript
<h1>Welcome to the First Session of React</h1>
```

JSX allows HTML-like syntax to be written inside JavaScript.

---

### Export Statement

```javascript
export default App;
```

Exports the component so it can be rendered by `index.js`.

---

# Learning Outcome

After completing this exercise, you will be able to:

* Install Node.js and npm.
* Create a React application using Create React App.
* Understand the React project structure.
* Modify the App component.
* Execute a React application.
* Display content using JSX.
* Access the application through the browser.

---

# Result

Successfully created a React application named **myfirstreact**, configured the development environment, modified the `App.js` component, and displayed the message **"Welcome to the First Session of React"** in the browser.
