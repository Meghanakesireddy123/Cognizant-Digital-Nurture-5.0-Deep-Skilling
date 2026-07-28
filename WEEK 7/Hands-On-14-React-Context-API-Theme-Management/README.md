# Hands-On 14: React Context API – Theme Management

## Objective

The objective of this hands-on exercise is to understand the React Context API by eliminating unnecessary prop drilling and sharing data efficiently between nested components. The application demonstrates how a theme (Light/Dark) can be shared across multiple components using `createContext()` and `useContext()`.

---

# Learning Objectives

After completing this exercise, you will be able to:

- Understand React Context API.
- Create Context using createContext().
- Use Context Provider.
- Use useContext() Hook.
- Avoid Prop Drilling.
- Share data among nested components.
- Apply dynamic themes using Context.

---

# Software Requirements

- Node.js
- npm
- Visual Studio Code
- ReactJS

---

# Project Name

employee-management-app

---

# Scenario

Apps Centric Solutions has developed an Employee Management Application.

Initially, the application passed the theme ("light" or "dark") from App → EmployeeList → EmployeeCard using props.

To improve maintainability and eliminate unnecessary prop passing, React Context API is implemented.

The selected theme is shared directly with nested child components.

---

# Step 1: Install Dependencies

```bash
npm install
```

---

# Step 2: Run Application

```bash
npm start
```

---

# Project Structure

```text
employee-management-app
│
├── src
│
├── Components
│      ├── EmployeeList.js
│      ├── EmployeeCard.js
│
├── Context
│      └── ThemeContext.js
│
├── App.js
│
└── index.js
```

---

# ThemeContext.js

```javascript
import { createContext } from "react";

const ThemeContext = createContext("light");

export default ThemeContext;
```

---

# App.js

```javascript
import React, { useState } from "react";

import EmployeeList from "./Components/EmployeeList";

import ThemeContext from "./Context/ThemeContext";

function App() {

    const [theme, setTheme] = useState("light");

    const toggleTheme = () => {

        setTheme(theme === "light" ? "dark" : "light");

    };

    return (

        <ThemeContext.Provider value={theme}>

            <div>

                <h1>Employee Management System</h1>

                <button onClick={toggleTheme}>

                    Change Theme

                </button>

                <EmployeeList />

            </div>

        </ThemeContext.Provider>

    );

}

export default App;
```

---

# EmployeeList.js

```javascript
import React from "react";

import EmployeeCard from "./EmployeeCard";

function EmployeeList() {

    const employees = [

        {

            id: 101,

            name: "Rahul Sharma",

            designation: "Software Engineer"

        },

        {

            id: 102,

            name: "Priya Reddy",

            designation: "Frontend Developer"

        },

        {

            id: 103,

            name: "Arjun Kumar",

            designation: "Backend Developer"

        }

    ];

    return (

        <div>

            {

                employees.map(employee => (

                    <EmployeeCard

                        key={employee.id}

                        employee={employee}

                    />

                ))

            }

        </div>

    );

}

export default EmployeeList;
```

---

# EmployeeCard.js

```javascript
import React, { useContext } from "react";

import ThemeContext from "../Context/ThemeContext";

function EmployeeCard({ employee }) {

    const theme = useContext(ThemeContext);

    return (

        <div
            style={{

                border: "1px solid gray",

                margin: "15px",

                padding: "15px",

                borderRadius: "10px"

            }}
        >

            <h2>{employee.name}</h2>

            <p>

                Designation :

                {employee.designation}

            </p>

            <button

                className={theme}

            >

                View Profile

            </button>

        </div>

    );

}

export default EmployeeCard;
```

---

# styles.css

```css
.light{

    background-color:white;

    color:black;

    border:1px solid black;

    padding:10px 18px;

}

.dark{

    background-color:#222;

    color:white;

    border:none;

    padding:10px 18px;

}
```

---

# Run the Application

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
Employee Management System

[Change Theme]

Rahul Sharma
Software Engineer
[View Profile]

Priya Reddy
Frontend Developer
[View Profile]

Arjun Kumar
Backend Developer
[View Profile]
```

When the **Change Theme** button is clicked:

- Light Theme → White buttons with black text.
- Dark Theme → Dark buttons with white text.

---

# Explanation

## React Context API

React Context API allows data to be shared across multiple components without passing props manually through every level.

---

## createContext()

Creates a Context object.

Example

```javascript
const ThemeContext = createContext("light");
```

---

## Provider

The Provider makes the context value available to all child components.

```javascript
<ThemeContext.Provider value={theme}>
```

---

## useContext()

Retrieves the current context value inside a child component.

```javascript
const theme = useContext(ThemeContext);
```

---

## Prop Drilling

Prop drilling occurs when data is passed through intermediate components that do not use it.

Before Context:

```
App

↓

EmployeeList

↓

EmployeeCard
```

Theme passed through every component.

After Context:

```
App

↓

ThemeContext

↓

EmployeeCard
```

EmployeeCard directly accesses the theme.

---

# Advantages of React Context API

- Eliminates Prop Drilling.
- Cleaner Component Structure.
- Better Code Reusability.
- Easier State Sharing.
- Improves Application Scalability.
- Simplifies Maintenance.

---

# Learning Outcome

- Created Context using createContext().
- Implemented Theme Provider.
- Used useContext() Hook.
- Eliminated unnecessary props.
- Applied dynamic Light and Dark themes.
- Shared data efficiently across nested components.

---

# Result

Successfully implemented React Context API in the Employee Management Application. The application efficiently shared the selected theme between nested components using Context Provider and useContext(), eliminating prop drilling and improving code maintainability.
