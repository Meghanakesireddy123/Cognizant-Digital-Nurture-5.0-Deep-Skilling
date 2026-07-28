# Hands-On 17: React Fetch User REST API

## Objective

The objective of this hands-on exercise is to understand how React applications consume REST APIs using the Fetch API. The application retrieves random user details from a public REST API and displays the user's title, first name, last name, email, country, and profile picture.

---

# Learning Objectives

After completing this exercise, you will be able to:

- Understand REST APIs.
- Consume REST APIs using Fetch API.
- Use React Lifecycle Methods.
- Retrieve JSON data.
- Store API responses in Component State.
- Display API data dynamically.

---

# Software Requirements

- Node.js
- npm
- Visual Studio Code
- ReactJS
- Internet Connection

---

# Project Name

fetchuserapp

---

# REST API Used

```
https://api.randomuser.me/
```

---

# Scenario

Develop a React application that retrieves user information from the Random User REST API.

The application should display:

- Profile Picture
- Title
- First Name
- Last Name
- Email
- Country

The API should be invoked inside the **componentDidMount()** lifecycle method.

---

# Step 1: Create React Project

```bash
npx create-react-app fetchuserapp
```

---

# Step 2: Navigate to Project

```bash
cd fetchuserapp
```

---

# Step 3: Open in VS Code

```bash
code .
```

---

# Project Structure

```text
fetchuserapp
│
├── src
│
├── Components
│      └── GetUser.js
│
├── App.js
│
└── package.json
```

---

# GetUser.js

```javascript
import React, { Component } from "react";

class GetUser extends Component {

    constructor() {

        super();

        this.state = {

            user: null

        };

    }

    async componentDidMount() {

        try {

            const response = await fetch(

                "https://api.randomuser.me/"

            );

            const data = await response.json();

            this.setState({

                user: data.results[0]

            });

        }

        catch(error){

            console.log(error);

        }

    }

    render() {

        const { user } = this.state;

        if(user===null){

            return <h2>Loading User Details...</h2>;

        }

        return(

            <div
                style={{

                    width:"400px",

                    margin:"30px auto",

                    border:"1px solid gray",

                    borderRadius:"10px",

                    padding:"20px",

                    textAlign:"center"

                }}
            >

                <h2>User Details</h2>

                <img

                    src={user.picture.large}

                    alt="User"

                    style={{

                        borderRadius:"50%"

                    }}

                />

                <h3>

                    {user.name.title}

                    {" "}

                    {user.name.first}

                    {" "}

                    {user.name.last}

                </h3>

                <p>

                    <b>Email :</b>

                    {user.email}

                </p>

                <p>

                    <b>Country :</b>

                    {user.location.country}

                </p>

            </div>

        );

    }

}

export default GetUser;
```

---

# App.js

```javascript
import React from "react";

import GetUser from "./Components/GetUser";

function App(){

    return(

        <GetUser/>

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
User Details

(Profile Image)

Mr John Smith

Email:
john.smith@example.com

Country:
United States
```

> The displayed user changes every time the application is refreshed because the API returns a random user.

---

# Explanation

## What is a REST API?

A REST API (Representational State Transfer API) allows applications to communicate over HTTP and exchange data, usually in JSON format.

---

## Fetch API

The Fetch API is used to send HTTP requests and retrieve data from a server.

Example:

```javascript
fetch("https://api.randomuser.me/")
```

---

## componentDidMount()

`componentDidMount()` is a React lifecycle method that executes automatically after the component is rendered.

It is commonly used for:

- Fetching data from APIs
- Loading external resources
- Initializing application data

Example:

```javascript
async componentDidMount(){

    const response = await fetch(...);

}
```

---

## State Management

The retrieved user data is stored in the component state.

```javascript
this.setState({

user:data.results[0]

});
```

---

## Conditional Rendering

Before the API response is received:

```javascript
Loading User Details...
```

After the response:

```javascript
User information is displayed.
```

---

## JSON Response Structure

```json
{
  "results": [
    {
      "name": {
        "title": "Mr",
        "first": "John",
        "last": "Smith"
      },
      "email": "john@example.com",
      "picture": {
        "large": "image-url"
      },
      "location": {
        "country": "United States"
      }
    }
  ]
}
```

---

# React Concepts Used

| Concept | Purpose |
|---------|---------|
| Component | Create UI |
| State | Store User Data |
| Fetch API | Consume REST API |
| componentDidMount() | Load API Data |
| Conditional Rendering | Display Loading Message |

---

# Advantages of Fetch API

- Easy HTTP Requests
- Promise-based API
- Supports Async/Await
- Lightweight
- Built into Modern Browsers
- Easy Integration with React

---

# Learning Outcome

- Created a React application.
- Consumed a REST API.
- Used Fetch API.
- Used `componentDidMount()`.
- Stored API response in state.
- Displayed user information dynamically.

---

# Result

Successfully developed a React application that consumes a public REST API using the Fetch API. The application retrieves random user details, stores the response in the component state, and dynamically displays the user's profile picture, name, email, and country using React lifecycle methods.
