# Hands-On 4: React Component Lifecycle Hooks

## Objective

The objective of this hands-on exercise is to understand the React Component Lifecycle by implementing lifecycle methods such as **componentDidMount()** and **componentDidCatch()**. The application fetches blog posts from an external REST API using the Fetch API and displays them in the browser.

---

# Learning Objectives

After completing this exercise, you will be able to:

- Understand the need for Component Lifecycle.
- Explain the benefits of Lifecycle Hooks.
- Identify various lifecycle methods.
- Understand rendering sequence.
- Fetch data using Fetch API.
- Handle runtime errors using componentDidCatch().
- Display API data dynamically.

---

# Software Requirements

- Node.js
- npm
- Visual Studio Code
- ReactJS

---

# Project Name

blogapp

---

# Scenario

Develop a Blog Application that retrieves blog posts from an external REST API and displays them using a React Class Component.

The application should:

- Fetch posts after component loading.
- Display the title and body of each post.
- Handle runtime errors gracefully.

---

# Step 1: Create React Project

Open Terminal.

Execute

```bash
npx create-react-app blogapp
```

---

# Step 2: Navigate into Project

```bash
cd blogapp
```

---

# Step 3: Open Project

```bash
code .
```

---

# Project Structure

```text
blogapp
│
├── src
│   │
│   ├── Post.js
│   ├── Posts.js
│   ├── App.js
│   └── index.js
│
└── package.json
```

---

# Post.js

```javascript
class Post {

    constructor(id,title,body){

        this.id=id;

        this.title=title;

        this.body=body;

    }

}

export default Post;
```

---

# Posts.js

```javascript
import React,{Component} from "react";

class Posts extends Component{

    constructor(props){

        super(props);

        this.state={

            posts:[]

        };

    }

    loadPosts(){

        fetch("https://jsonplaceholder.typicode.com/posts")

        .then(response=>response.json())

        .then(data=>{

            this.setState({

                posts:data

            });

        });

    }

    componentDidMount(){

        this.loadPosts();

    }

    componentDidCatch(error){

        alert(error);

    }

    render(){

        return(

            <div>

                {

                    this.state.posts.map(post=>

                        <div key={post.id}>

                            <h2>{post.title}</h2>

                            <p>{post.body}</p>

                        </div>

                    )

                }

            </div>

        );

    }

}

export default Posts;
```

---

# App.js

```javascript
import React from "react";

import Posts from "./Posts";

function App(){

    return(

        <Posts/>

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
Blog Posts

Title 1

Post Description...

Title 2

Post Description...

Title 3

Post Description...
```

The application displays multiple blog posts retrieved from the JSONPlaceholder API.

---

# Explanation

## Component Lifecycle

Lifecycle methods are special methods that execute automatically during different phases of a component.

---

## componentDidMount()

Executed immediately after the component is rendered.

Used for:

- Fetch API
- API Calls
- Database Calls

Example

```javascript
componentDidMount(){

    this.loadPosts();

}
```

---

## componentDidCatch()

Handles runtime errors occurring inside child components.

Example

```javascript
componentDidCatch(error){

    alert(error);

}
```

---

## Fetch API

Fetch retrieves JSON data from the server.

```javascript
fetch("https://jsonplaceholder.typicode.com/posts")
```

---

## render()

The render() method returns JSX to display UI.

React automatically re-renders whenever state changes.

---

# React Lifecycle Sequence

```
Constructor

↓

Render()

↓

componentDidMount()

↓

State Updated

↓

Render()

↓

componentDidCatch() (Only if Error Occurs)
```

---

# Advantages of Lifecycle Hooks

- Better code organization
- API integration
- Error handling
- Dynamic rendering
- Performance optimization

---

# Learning Outcome

- Created a React Blog Application.
- Used Constructor.
- Implemented componentDidMount().
- Implemented componentDidCatch().
- Loaded data using Fetch API.
- Rendered API response dynamically.

---

# Result

Successfully implemented React Component Lifecycle Hooks by loading blog posts from an external REST API using componentDidMount() and handling runtime errors using componentDidCatch().
