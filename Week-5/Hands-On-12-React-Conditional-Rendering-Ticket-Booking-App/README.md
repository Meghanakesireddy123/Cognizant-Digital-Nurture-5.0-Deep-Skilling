# Hands-On 12: React Conditional Rendering – Ticket Booking Application

## Objective

The objective of this hands-on exercise is to understand Conditional Rendering in React by developing a Ticket Booking Application. The application displays different pages based on the user's login status using React components and conditional rendering techniques.

---

# Learning Objectives

After completing this exercise, you will be able to:

- Understand Conditional Rendering in React.
- Use Element Variables.
- Display components based on application state.
- Implement Login and Logout functionality.
- Prevent components from rendering when required.
- Improve user experience using conditional UI.

---

# Software Requirements

- Node.js
- npm
- Visual Studio Code
- ReactJS

---

# Project Name

ticketbookingapp

---

# Scenario

Develop a Ticket Booking Application.

The application has two users:

- Guest User
- Logged-in User

Guest users can only view flight details.

Logged-in users can:

- View available flights.
- Book flight tickets.
- Logout from the application.

The application should dynamically switch between Guest and User pages using Login and Logout buttons.

---

# Step 1: Create React Project

Open Terminal.

Execute:

```bash
npx create-react-app ticketbookingapp
```

---

# Step 2: Navigate to Project

```bash
cd ticketbookingapp
```

---

# Step 3: Open Project

```bash
code .
```

---

# Project Structure

```text
ticketbookingapp
│
├── src
│
├── Components
│      ├── GuestPage.js
│      ├── UserPage.js
│      ├── LoginButton.js
│      ├── LogoutButton.js
│
├── App.js
│
└── package.json
```

---

# GuestPage.js

```javascript
import React from "react";

function GuestPage(){

    return(

        <div>

            <h2>Welcome Guest</h2>

            <h3>Available Flights</h3>

            <ul>

                <li>Hyderabad → Delhi</li>

                <li>Bangalore → Mumbai</li>

                <li>Chennai → Kolkata</li>

            </ul>

            <p>

                Please Login to Book Tickets.

            </p>

        </div>

    );

}

export default GuestPage;
```

---

# UserPage.js

```javascript
import React from "react";

function UserPage(){

    return(

        <div>

            <h2>Welcome User</h2>

            <h3>Available Flights</h3>

            <ul>

                <li>Hyderabad → Delhi</li>

                <li>Bangalore → Mumbai</li>

                <li>Chennai → Kolkata</li>

            </ul>

            <button>

                Book Ticket

            </button>

        </div>

    );

}

export default UserPage;
```

---

# LoginButton.js

```javascript
import React from "react";

function LoginButton(props){

    return(

        <button

            onClick={props.onClick}

        >

            Login

        </button>

    );

}

export default LoginButton;
```

---

# LogoutButton.js

```javascript
import React from "react";

function LogoutButton(props){

    return(

        <button

            onClick={props.onClick}

        >

            Logout

        </button>

    );

}

export default LogoutButton;
```

---

# App.js

```javascript
import React,{Component} from "react";

import GuestPage from "./Components/GuestPage";
import UserPage from "./Components/UserPage";
import LoginButton from "./Components/LoginButton";
import LogoutButton from "./Components/LogoutButton";

class App extends Component{

    constructor(){

        super();

        this.state={

            isLoggedIn:false

        };

    }

    login=()=>{

        this.setState({

            isLoggedIn:true

        });

    }

    logout=()=>{

        this.setState({

            isLoggedIn:false

        });

    }

    render(){

        let page;

        let button;

        if(this.state.isLoggedIn){

            page=<UserPage/>;

            button=<LogoutButton

                onClick={this.logout}/>;

        }

        else{

            page=<GuestPage/>;

            button=<LoginButton

                onClick={this.login}/>;

        }

        return(

            <div>

                <h1>

                    Ticket Booking Application

                </h1>

                {button}

                <hr/>

                {page}

            </div>

        );

    }

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

### Initial Page (Guest)

```
Ticket Booking Application

[Login]

Welcome Guest

Available Flights

Hyderabad → Delhi

Bangalore → Mumbai

Chennai → Kolkata

Please Login to Book Tickets.
```

---

### After Clicking Login

```
Ticket Booking Application

[Logout]

Welcome User

Available Flights

Hyderabad → Delhi

Bangalore → Mumbai

Chennai → Kolkata

[Book Ticket]
```

---

### After Clicking Logout

Application returns to Guest Page.

---

# Explanation

## Conditional Rendering

Conditional Rendering displays different UI components based on specific conditions.

Example:

```javascript
if(this.state.isLoggedIn){

    page=<UserPage/>;

}

else{

    page=<GuestPage/>;

}
```

---

## Element Variables

Element Variables temporarily store React elements before rendering.

Example:

```javascript
let page;

let button;
```

---

## Login Function

```javascript
login=()=>{

this.setState({

isLoggedIn:true

});

}
```

Changes application state to Logged-in.

---

## Logout Function

```javascript
logout=()=>{

this.setState({

isLoggedIn:false

});

}
```

Returns application to Guest mode.

---

## Preventing Components from Rendering

React prevents unnecessary rendering by displaying only the component that satisfies the current condition.

---

# Advantages of Conditional Rendering

- Dynamic User Interface
- Better User Experience
- Easy Authentication Flow
- Efficient Component Rendering
- Cleaner Code Structure

---

# Learning Outcome

- Implemented Conditional Rendering.
- Used Element Variables.
- Managed Component State.
- Implemented Login and Logout.
- Switched between Guest and User views dynamically.

---

# Result

Successfully developed a Ticket Booking Application using React Conditional Rendering. The application dynamically displays Guest and User pages based on the login status, demonstrating effective use of state management, element variables, and conditional UI rendering.
