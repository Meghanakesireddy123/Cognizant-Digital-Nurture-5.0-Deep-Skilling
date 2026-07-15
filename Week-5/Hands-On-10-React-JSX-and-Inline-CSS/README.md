# Hands-On 10: React JSX and Inline CSS

## Objective

The objective of this hands-on exercise is to understand React JSX by creating elements, attributes, JavaScript expressions, and rendering office rental information dynamically. The application also demonstrates the use of inline CSS to apply conditional styling based on office rent.

---

# Learning Objectives

After completing this exercise, you will be able to:

- Understand JSX syntax.
- Understand ECMAScript (ES6) features used in React.
- Explain React.createElement().
- Create React elements using JSX.
- Render JSX elements to the DOM.
- Use JavaScript expressions inside JSX.
- Apply Inline CSS in React.
- Display dynamic data using arrays and objects.

---

# Software Requirements

- Node.js
- npm
- Visual Studio Code
- ReactJS

---

# Project Name

officespacerentalapp

---

# Scenario

Develop an Office Space Rental application using React JSX.

The application should:

- Display a heading.
- Display an office image.
- Display office details such as Name, Rent, and Address.
- Display multiple office records.
- Apply conditional colors to Rent:
  - Red → Rent below 60000
  - Green → Rent 60000 or above

---

# Step 1: Create React Project

Open Terminal and execute:

```bash
npx create-react-app officespacerentalapp
```

---

# Step 2: Navigate into Project

```bash
cd officespacerentalapp
```

---

# Step 3: Open Project

```bash
code .
```

---

# Project Structure

```text
officespacerentalapp
│
├── public
│
├── src
│   │
│   ├── App.js
│   ├── index.js
│   └── office.jpg
│
└── package.json
```

---

# App.js

```javascript
import React from "react";

import officeImage from "./office.jpg";

function App() {

    const offices = [

        {
            name: "Tech Park",
            rent: 55000,
            address: "Hyderabad"
        },

        {
            name: "Cyber Towers",
            rent: 72000,
            address: "Bangalore"
        },

        {
            name: "Innovation Hub",
            rent: 48000,
            address: "Chennai"
        }

    ];

    return (

        <div>

            <h1>Office Space Rental Application</h1>

            <img
                src={officeImage}
                alt="Office Space"
                width="500"
            />

            {

                offices.map((office,index)=>(

                    <div key={index}>

                        <h2>{office.name}</h2>

                        <h3
                            style={{
                                color:
                                office.rent < 60000
                                ? "red"
                                : "green"
                            }}
                        >

                            Rent : ₹{office.rent}

                        </h3>

                        <p>

                            Address : {office.address}

                        </p>

                        <hr/>

                    </div>

                ))

            }

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

```
Office Space Rental Application

[Office Image]

Tech Park

Rent : ₹55000

Address : Hyderabad

----------------------------

Cyber Towers

Rent : ₹72000

Address : Bangalore

----------------------------

Innovation Hub

Rent : ₹48000

Address : Chennai
```

### Styling

- Rent below ₹60000 → **Red**
- Rent ₹60000 or above → **Green**

---

# Explanation

## JSX

JSX (JavaScript XML) is a syntax extension that allows HTML-like code to be written inside JavaScript.

Example:

```javascript
<h1>Office Space Rental Application</h1>
```

---

## React.createElement()

JSX is converted internally into `React.createElement()` calls.

Example:

```javascript
<h1>Hello</h1>
```

is transformed into:

```javascript
React.createElement("h1", null, "Hello");
```

---

## JavaScript Expressions in JSX

Expressions are written inside curly braces `{}`.

Example:

```javascript
<h2>{office.name}</h2>
```

---

## Rendering Lists

The `map()` method is used to render multiple office objects.

```javascript
offices.map((office,index)=>...)
```

---

## Inline CSS

Inline styles are applied using the `style` attribute.

Example:

```javascript
style={{ color: "green" }}
```

---

## Conditional Styling

Rent color changes dynamically.

```javascript
style={{

color:

office.rent<60000

?"red"

:"green"

}}
```

---

# ECMAScript (ES6) Features Used

- const
- Arrow Functions
- Objects
- Arrays
- map()
- Template Literals
- Import & Export

---

# Benefits of JSX

- Easy to read
- HTML-like syntax
- Supports JavaScript expressions
- Better performance with Virtual DOM
- Improves code maintainability

---

# Learning Outcome

- Created React elements using JSX.
- Displayed objects and arrays.
- Rendered lists using map().
- Applied Inline CSS.
- Used JavaScript expressions inside JSX.
- Implemented Conditional Rendering.

---

# Result

Successfully developed an Office Space Rental application using React JSX. The application dynamically displayed office details, rendered multiple office records, and applied conditional inline styling to the rent values based on predefined business rules.
