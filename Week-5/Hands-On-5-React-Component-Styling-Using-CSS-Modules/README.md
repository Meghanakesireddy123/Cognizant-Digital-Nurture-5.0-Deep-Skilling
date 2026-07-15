# Hands-On 5: React Component Styling Using CSS Modules

## Objective

The objective of this hands-on exercise is to understand different styling techniques in React by applying CSS Modules and inline styles. The application displays Cognizant Academy cohort details and styles each cohort card based on its status.

---

# Learning Objectives

After completing this exercise, you will be able to:

- Understand the need for styling React components.
- Apply styles using CSS Modules.
- Use the className property in React.
- Apply Inline Styling.
- Implement conditional styling based on component data.
- Improve the appearance of React applications.

---

# Software Requirements

- Node.js
- npm
- Visual Studio Code
- ReactJS

---

# Project Name

Academy Dashboard

---

# Scenario

The Cognizant Academy Team wants to develop a dashboard to display details of ongoing and completed cohorts.

Each cohort should be displayed inside a styled card.

The cohort status should determine the heading color:

- Green → Ongoing
- Blue → Completed

---

# Step 1: Restore Project Dependencies

Open Command Prompt.

Navigate to the project folder.

Execute:

```bash
npm install
```

---

# Step 2: Open Project

```bash
code .
```

---

# Project Structure

```text
academy-dashboard
│
├── src
│   │
│   ├── Components
│   │      └── CohortDetails.js
│   │
│   ├── Styles
│   │      └── CohortDetails.module.css
│   │
│   ├── App.js
│   └── index.js
│
└── package.json
```

---

# CohortDetails.module.css

```css
.box{

    width:300px;

    display:inline-block;

    margin:10px;

    padding:10px 20px;

    border:1px solid black;

    border-radius:10px;

}

dt{

    font-weight:500;

}
```

---

# CohortDetails.js

```javascript
import React from "react";

import styles from "./CohortDetails.module.css";

function CohortDetails(props){

    const headingStyle={

        color:props.status==="Ongoing"
                ?"green"
                :"blue"

    };

    return(

        <div className={styles.box}>

            <h3 style={headingStyle}>

                {props.cohortName}

            </h3>

            <dl>

                <dt>Coach</dt>

                <dd>{props.coach}</dd>

                <dt>Status</dt>

                <dd>{props.status}</dd>

                <dt>Technology</dt>

                <dd>{props.technology}</dd>

            </dl>

        </div>

    );

}

export default CohortDetails;
```

---

# App.js

```javascript
import React from "react";

import CohortDetails from "./Components/CohortDetails";

function App(){

    return(

        <div>

            <CohortDetails

                cohortName="React Batch"

                coach="John"

                status="Ongoing"

                technology="ReactJS"

            />

            <CohortDetails

                cohortName="Java Batch"

                coach="David"

                status="Completed"

                technology="Spring Boot"

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
React Batch

Coach : John

Status : Ongoing

Technology : ReactJS

----------------------------

Java Batch

Coach : David

Status : Completed

Technology : Spring Boot
```

### Styling

- Each cohort is displayed inside a bordered card.
- Cards have rounded corners.
- Cards have proper padding and spacing.
- **Ongoing** cohort heading is displayed in **Green**.
- **Completed** cohort heading is displayed in **Blue**.

---

# Explanation

## CSS Modules

CSS Modules provide locally scoped CSS, preventing style conflicts between components.

Import statement:

```javascript
import styles from "./CohortDetails.module.css";
```

---

## className

The `className` property applies CSS classes to React components.

Example:

```javascript
<div className={styles.box}>
```

---

## Inline Styling

Inline styles are applied directly using the `style` attribute.

Example:

```javascript
const headingStyle = {

    color:"green"

}
```

---

## Conditional Styling

The heading color changes dynamically based on the cohort status.

```javascript
const headingStyle={

    color:props.status==="Ongoing"

    ?"green"

    :"blue"

};
```

---

# CSS Module Benefits

- Scoped styles
- Prevents naming conflicts
- Easier maintenance
- Better component reusability

---

# Difference Between CSS Module and Inline Style

| CSS Module | Inline Style |
|------------|--------------|
| Reusable | Defined inside component |
| Supports pseudo selectors | No pseudo selectors |
| Better for large projects | Best for dynamic styling |
| Stored in separate file | Written inside JSX |

---

# Learning Outcome

- Styled React Components.
- Applied CSS Modules.
- Used className property.
- Applied Inline Styling.
- Implemented Conditional Styling.
- Improved UI using CSS.

---

# Result

Successfully styled the React Cohort Dashboard by implementing CSS Modules and Inline Styling. The application dynamically changes the heading color based on the cohort status while maintaining reusable and modular styling practices.
