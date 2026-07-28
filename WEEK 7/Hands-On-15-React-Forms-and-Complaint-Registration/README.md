# Hands-On 15: React Forms and Complaint Registration

## Objective

The objective of this hands-on exercise is to understand React Forms by implementing Controlled Components. The application allows employees to register complaints using a form and generates a unique complaint reference number after successful submission.

---

# Learning Objectives

After completing this exercise, you will be able to:

- Understand React Forms.
- Implement Controlled Components.
- Handle Textbox and Textarea controls.
- Handle Form Submission.
- Generate unique Reference Numbers.
- Manage component state using React Hooks.

---

# Software Requirements

- Node.js
- npm
- Visual Studio Code
- ReactJS

---

# Project Name

ticketraisingapp

---

# Scenario

The HR department wants an application where employees can raise complaints.

The application should:

- Accept Employee Name.
- Accept Complaint Description.
- Validate user inputs.
- Generate a Complaint Reference Number.
- Display the reference number after successful submission.

---

# Step 1: Create React Project

```bash
npx create-react-app ticketraisingapp
```

---

# Step 2: Navigate to Project

```bash
cd ticketraisingapp
```

---

# Step 3: Open in VS Code

```bash
code .
```

---

# Project Structure

```text
ticketraisingapp
│
├── src
│
├── Components
│      └── ComplaintRegister.js
│
├── App.js
│
└── package.json
```

---

# ComplaintRegister.js

```javascript
import React, { useState } from "react";

function ComplaintRegister() {

    const [employeeName, setEmployeeName] = useState("");

    const [complaint, setComplaint] = useState("");

    const handleSubmit = (event) => {

        event.preventDefault();

        if (employeeName.trim() === "" || complaint.trim() === "") {

            alert("Please fill all the fields.");

            return;

        }

        const referenceNumber =

            "CMP" +

            Math.floor(100000 + Math.random() * 900000);

        alert(

            "Complaint Registered Successfully!\n\n" +

            "Reference Number : " +

            referenceNumber

        );

        setEmployeeName("");

        setComplaint("");

    };

    return (

        <div
            style={{
                width: "500px",
                margin: "30px auto",
                border: "1px solid gray",
                borderRadius: "10px",
                padding: "20px"
            }}
        >

            <h2>Ticket Raising Portal</h2>

            <form onSubmit={handleSubmit}>

                <label>

                    Employee Name

                </label>

                <br/><br/>

                <input

                    type="text"

                    value={employeeName}

                    placeholder="Enter Employee Name"

                    onChange={(e)=>setEmployeeName(e.target.value)}

                    style={{

                        width:"100%",

                        padding:"10px"

                    }}

                />

                <br/><br/>

                <label>

                    Complaint

                </label>

                <br/><br/>

                <textarea

                    rows="5"

                    value={complaint}

                    placeholder="Enter Complaint"

                    onChange={(e)=>setComplaint(e.target.value)}

                    style={{

                        width:"100%",

                        padding:"10px"

                    }}

                />

                <br/><br/>

                <button type="submit">

                    Raise Complaint

                </button>

            </form>

        </div>

    );

}

export default ComplaintRegister;
```

---

# App.js

```javascript
import React from "react";

import ComplaintRegister from "./Components/ComplaintRegister";

function App() {

    return (

        <ComplaintRegister/>

    );

}

export default App;
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
Ticket Raising Portal

Employee Name

______________________

Complaint

______________________

______________________

[Raise Complaint]
```

---

# Sample Execution

Employee Name

```
Meghana Kesireddy
```

Complaint

```
Unable to access internal HR portal.
```

After clicking **Raise Complaint**

```
Complaint Registered Successfully!

Reference Number : CMP582143
```

A new reference number is generated every time the form is submitted.

---

# Explanation

## React Forms

React Forms allow users to enter and submit information through input controls.

---

## Controlled Components

A Controlled Component is an input element whose value is managed by React state.

Example

```javascript
const [employeeName, setEmployeeName] = useState("");
```

---

## Textbox

The Employee Name is collected using an `<input>` element.

```javascript
<input
type="text"
value={employeeName}
onChange={(e)=>setEmployeeName(e.target.value)}
/>
```

---

## Textarea

The complaint description is collected using a `<textarea>` element.

```javascript
<textarea
value={complaint}
onChange={(e)=>setComplaint(e.target.value)}
/>
```

---

## Form Submission

The form uses the `onSubmit` event.

```javascript
<form onSubmit={handleSubmit}>
```

---

## handleSubmit()

The `handleSubmit()` method:

- Prevents page refresh.
- Validates user input.
- Generates a Complaint Reference Number.
- Displays a success alert.
- Clears the form.

---

## Complaint Reference Number

Reference numbers are generated dynamically.

Example

```javascript
const referenceNumber =

"CMP" +

Math.floor(100000 + Math.random() * 900000);
```

Sample Output

```
CMP582143
```

---

# React Hooks Used

| Hook | Purpose |
|------|---------|
| useState() | Stores Employee Name |
| useState() | Stores Complaint |

---

# Advantages of Controlled Components

- Better validation
- Easy state management
- Real-time updates
- Improved form handling
- Cleaner React code

---

# Learning Outcome

- Created a React Form.
- Implemented Controlled Components.
- Used Textbox and Textarea.
- Handled Form Submission.
- Generated Complaint Reference Numbers.
- Managed form data using React Hooks.

---

# Result

Successfully developed a Ticket Raising Application using React Forms and Controlled Components. The application allows employees to register complaints, validates the entered information, generates a unique complaint reference number, and demonstrates effective form handling using React Hooks.
