# Hands-On 16: React Forms Validation and Registration

## Objective

The objective of this hands-on exercise is to understand React Forms Validation by implementing a user registration form using Controlled Components. The application validates user inputs before form submission and displays appropriate validation messages.

---

# Learning Objectives

After completing this exercise, you will be able to:

- Understand React Forms Validation.
- Differentiate between React Forms and HTML Forms.
- Implement Controlled Components.
- Handle Textbox, Email, and Password input controls.
- Perform validation using event handlers.
- Submit forms using the `onSubmit` event.
- Display validation messages dynamically.

---

# Software Requirements

- Node.js
- npm
- Visual Studio Code
- ReactJS

---

# Project Name

mailregisterapp

---

# Scenario

The HR department requires a simple employee registration portal.

The application should:

- Accept Employee Name.
- Accept Email Address.
- Accept Password.
- Validate all input fields.
- Display error messages if validation fails.
- Display a success message after successful registration.

---

# Step 1: Create React Project

```bash
npx create-react-app mailregisterapp
```

---

# Step 2: Navigate to Project

```bash
cd mailregisterapp
```

---

# Step 3: Open in VS Code

```bash
code .
```

---

# Project Structure

```text
mailregisterapp
│
├── src
│
├── Components
│      └── Register.js
│
├── App.js
│
└── package.json
```

---

# Register.js

```javascript
import React, { useState } from "react";

function Register() {

    const [name, setName] = useState("");

    const [email, setEmail] = useState("");

    const [password, setPassword] = useState("");

    const [errors, setErrors] = useState({});

    const validateForm = () => {

        let validationErrors = {};

        if (name.trim().length < 5) {

            validationErrors.name =
                "Name must contain at least 5 characters.";

        }

        if (!email.includes("@") || !email.includes(".")) {

            validationErrors.email =
                "Enter a valid email address.";

        }

        if (password.length < 8) {

            validationErrors.password =
                "Password must contain at least 8 characters.";

        }

        setErrors(validationErrors);

        return Object.keys(validationErrors).length === 0;

    };

    const handleSubmit = (event) => {

        event.preventDefault();

        if (validateForm()) {

            alert("Registration Successful!");

            setName("");

            setEmail("");

            setPassword("");

            setErrors({});

        }

    };

    return (

        <div
            style={{
                width: "450px",
                margin: "30px auto",
                padding: "20px",
                border: "1px solid gray",
                borderRadius: "10px"
            }}
        >

            <h2>Employee Registration</h2>

            <form onSubmit={handleSubmit}>

                <label>Name</label>

                <br/><br/>

                <input

                    type="text"

                    value={name}

                    onChange={(e)=>setName(e.target.value)}

                    placeholder="Enter Name"

                />

                <br/>

                <span style={{color:"red"}}>

                    {errors.name}

                </span>

                <br/><br/>

                <label>Email</label>

                <br/><br/>

                <input

                    type="email"

                    value={email}

                    onChange={(e)=>setEmail(e.target.value)}

                    placeholder="Enter Email"

                />

                <br/>

                <span style={{color:"red"}}>

                    {errors.email}

                </span>

                <br/><br/>

                <label>Password</label>

                <br/><br/>

                <input

                    type="password"

                    value={password}

                    onChange={(e)=>setPassword(e.target.value)}

                    placeholder="Enter Password"

                />

                <br/>

                <span style={{color:"red"}}>

                    {errors.password}

                </span>

                <br/><br/>

                <button type="submit">

                    Register

                </button>

            </form>

        </div>

    );

}

export default Register;
```

---

# App.js

```javascript
import React from "react";

import Register from "./Components/Register";

function App() {

    return <Register />;

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

# Validation Rules

| Field | Validation |
|--------|------------|
| Name | Minimum 5 characters |
| Email | Must contain **@** and **.** |
| Password | Minimum 8 characters |

---

# Sample Input

### Invalid Data

```
Name

Ram

Email

ramgmail.com

Password

12345
```

### Output

```
Name must contain at least 5 characters.

Enter a valid email address.

Password must contain at least 8 characters.
```

---

### Valid Data

```
Name

Meghana Kesireddy

Email

meghana@gmail.com

Password

Welcome123
```

### Output

```
Registration Successful!
```

---

# Explanation

## React Forms

React Forms allow user input to be managed using React state.

---

## Controlled Components

The values of form fields are controlled using `useState()`.

Example

```javascript
const [name, setName] = useState("");
```

---

## Form Validation

Validation is performed inside the `validateForm()` function before the form is submitted.

---

## Event Handling

### onChange()

Updates the state whenever the user types into an input field.

```javascript
onChange={(e)=>setName(e.target.value)}
```

### onSubmit()

Prevents page refresh and validates the form before submission.

```javascript
<form onSubmit={handleSubmit}>
```

---

## Validation Logic

```javascript
if(name.trim().length < 5)

if(!email.includes("@") || !email.includes("."))

if(password.length < 8)
```

---

# React Form vs HTML Form

| React Form | HTML Form |
|------------|-----------|
| Controlled using React State | Controlled by Browser |
| Uses `useState()` | Uses HTML elements only |
| Dynamic validation | Basic HTML validation |
| Better user experience | Limited interactivity |

---

# React Hooks Used

| Hook | Purpose |
|------|---------|
| useState() | Stores form field values |
| useState() | Stores validation error messages |

---

# Advantages of React Form Validation

- Immediate feedback to users.
- Prevents invalid submissions.
- Better user experience.
- Easy form management.
- Improved application reliability.

---

# Learning Outcome

- Created a React Registration Form.
- Implemented Controlled Components.
- Validated Name, Email, and Password.
- Used `onChange()` and `onSubmit()` events.
- Displayed dynamic validation messages.
- Managed form state using React Hooks.

---

# Result

Successfully developed a Mail Registration Application using React Forms and Controlled Components. The application validates user input for Name, Email, and Password, displays appropriate validation messages, and allows registration only after all validation rules are satisfied.
