# Hands-On 3: React Function Component and Styling

## Objective

The objective of this hands-on exercise is to create a React Functional Component that calculates a student's average score and displays the student details with CSS styling.

---

# Learning Objectives

After completing this exercise, you will be able to:

- Understand React Functional Components
- Differentiate Class Components and Functional Components
- Apply CSS Styling in React
- Pass data using Props
- Calculate and display student average score
- Render Functional Components

---

# Software Requirements

- Node.js
- npm
- Visual Studio Code
- ReactJS

---

# Project Name

scorecalculatorapp

---

# Scenario

Develop a Student Score Calculator application.

The application accepts:

- Student Name
- School Name
- Total Marks
- Goal

It calculates the average score and displays the student information using a Functional Component with CSS styling.

---

# Step 1: Create React Project

Open Terminal and execute:

```bash
npx create-react-app scorecalculatorapp
```

---

# Step 2: Navigate to Project

```bash
cd scorecalculatorapp
```

---

# Step 3: Open Project in Visual Studio Code

```bash
code .
```

---

# Project Structure

```text
scorecalculatorapp
│
├── src
│   │
│   ├── Components
│   │      └── CalculateScore.js
│   │
│   ├── Stylesheets
│   │      └── mystyle.css
│   │
│   ├── App.js
│   └── index.js
│
└── package.json
```

---

# CalculateScore.js

```javascript
import React from "react";
import "../Stylesheets/mystyle.css";

function CalculateScore(props) {

    const average = props.total / props.goal;

    return (

        <div className="container">

            <h1>Student Score Calculator</h1>

            <h3>Name : {props.name}</h3>

            <h3>School : {props.school}</h3>

            <h3>Total Marks : {props.total}</h3>

            <h3>Goal : {props.goal}</h3>

            <h2>Average Score : {average}</h2>

        </div>

    );

}

export default CalculateScore;
```

---

# mystyle.css

```css
.container{

    width:500px;

    margin:auto;

    text-align:center;

    background-color:#f2f2f2;

    padding:20px;

    border-radius:10px;

    font-family:Arial;

}

h1{

    color:blue;

}

h2{

    color:green;

}

h3{

    color:#444;

}
```

---

# App.js

```javascript
import React from "react";

import CalculateScore from "./Components/CalculateScore";

function App() {

    return (

        <div>

            <CalculateScore

                name="Rahul"

                school="ABC Public School"

                total={500}

                goal={5}

            />

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
Student Score Calculator

Name : Rahul

School : ABC Public School

Total Marks : 500

Goal : 5

Average Score : 100
```

---

# Explanation

## Functional Component

A Functional Component is a JavaScript function that returns JSX.

Example:

```javascript
function CalculateScore(props)
```

---

## Props

Props are used to pass data from the parent component to the child component.

Example:

```javascript
<CalculateScore

name="Rahul"

school="ABC Public School"

total={500}

goal={5}

/>
```

---

## CSS Styling

External CSS is imported into the component using:

```javascript
import "../Stylesheets/mystyle.css";
```

---

## Average Calculation

```javascript
const average = props.total / props.goal;
```

Calculates the student's average score.

---

# Difference Between Functional and Class Components

| Functional Component | Class Component |
|----------------------|-----------------|
| JavaScript Function | JavaScript Class |
| Simpler Syntax | More Complex |
| Uses Props | Uses State and Props |
| No render() Method | Uses render() Method |

---

# Learning Outcome

- Created a Functional Component.
- Applied CSS Styling.
- Used Props to pass data.
- Calculated Average Score.
- Rendered Functional Component.

---

# Result

Successfully developed a React Student Score Calculator application using a Functional Component, CSS styling, and Props to display student information and average score.
