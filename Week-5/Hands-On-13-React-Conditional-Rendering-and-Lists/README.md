# Hands-On 13: React Conditional Rendering and Lists

## Objective

The objective of this hands-on exercise is to understand different approaches to Conditional Rendering in React and learn how to render multiple components using lists, keys, and the `map()` function. The application displays Book Details, Blog Details, and Course Details using different conditional rendering techniques.

---

# Learning Objectives

After completing this exercise, you will be able to:

- Understand various Conditional Rendering techniques.
- Render multiple React Components.
- Understand List Components.
- Use Keys in React.
- Render collections using map().
- Extract reusable components with keys.
- Improve UI rendering using React Lists.

---

# Software Requirements

- Node.js
- npm
- Visual Studio Code
- ReactJS

---

# Project Name

bloggerapp

---

# Scenario

Develop a Blogger Application consisting of three components:

- Book Details
- Blog Details
- Course Details

The application should demonstrate multiple approaches to Conditional Rendering and dynamically render lists using the `map()` function.

---

# Step 1: Create React Project

Open Terminal.

Execute:

```bash
npx create-react-app bloggerapp
```

---

# Step 2: Navigate into Project

```bash
cd bloggerapp
```

---

# Step 3: Open Project

```bash
code .
```

---

# Project Structure

```text
bloggerapp
│
├── src
│
├── Components
│      ├── BookDetails.js
│      ├── BlogDetails.js
│      ├── CourseDetails.js
│
├── App.js
│
└── package.json
```

---

# BookDetails.js

```javascript
import React from "react";

function BookDetails(){

    const books=[

        {id:1,name:"React Guide",author:"Jordan Walke"},

        {id:2,name:"Java Programming",author:"James Gosling"}

    ];

    return(

        <div>

            <h2>Book Details</h2>

            {

                books.map(book=>

                    <div key={book.id}>

                        <p>

                            {book.name}

                            -

                            {book.author}

                        </p>

                    </div>

                )

            }

        </div>

    );

}

export default BookDetails;
```

---

# BlogDetails.js

```javascript
import React from "react";

function BlogDetails(){

    const blogs=[

        {id:1,title:"Introduction to React"},

        {id:2,title:"Understanding JSX"}

    ];

    return(

        <div>

            <h2>Blog Details</h2>

            {

                blogs.map(blog=>

                    <div key={blog.id}>

                        <p>{blog.title}</p>

                    </div>

                )

            }

        </div>

    );

}

export default BlogDetails;
```

---

# CourseDetails.js

```javascript
import React from "react";

function CourseDetails(){

    const courses=[

        {id:1,name:"ReactJS"},

        {id:2,name:"Spring Boot"},

        {id:3,name:"Microservices"}

    ];

    return(

        <div>

            <h2>Course Details</h2>

            {

                courses.map(course=>

                    <div key={course.id}>

                        <p>{course.name}</p>

                    </div>

                )

            }

        </div>

    );

}

export default CourseDetails;
```

---

# App.js

```javascript
import React from "react";

import BookDetails from "./Components/BookDetails";
import BlogDetails from "./Components/BlogDetails";
import CourseDetails from "./Components/CourseDetails";

function App(){

    const option="books";

    return(

        <div>

            <h1>Blogger Application</h1>

            {

                option==="books"

                ?<BookDetails/>

                :option==="blogs"

                ?<BlogDetails/>

                :<CourseDetails/>

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

### If `option = "books"`

```
Blogger Application

Book Details

React Guide - Jordan Walke

Java Programming - James Gosling
```

### If `option = "blogs"`

```
Blogger Application

Blog Details

Introduction to React

Understanding JSX
```

### If `option = "courses"`

```
Blogger Application

Course Details

ReactJS

Spring Boot

Microservices
```

---

# Explanation

## Conditional Rendering

Conditional Rendering allows different components to be displayed depending on application conditions.

Example:

```javascript
option==="books"

?<BookDetails/>

:<CourseDetails/>
```

---

## Rendering Multiple Components

React renders different components depending on the selected condition.

```javascript
<BookDetails/>

<BlogDetails/>

<CourseDetails/>
```

---

## List Rendering

React renders collections using the `map()` function.

Example:

```javascript
books.map(book=>...)
```

---

## Keys

Keys uniquely identify list elements.

Example:

```javascript
key={book.id}
```

Keys help React efficiently update and re-render list items.

---

## React map()

The `map()` function iterates over arrays and returns JSX elements for rendering.

Example:

```javascript
courses.map(course=>...)
```

---

## Extracting Components with Keys

Each list item should have a unique key to improve rendering performance and reduce unnecessary DOM updates.

---

# Various Ways of Conditional Rendering

### 1. if-else Statement

```javascript
if(condition){

return<Component1/>

}

else{

return<Component2/>

}
```

---

### 2. Ternary Operator

```javascript
condition

?<Component1/>

:<Component2/>
```

---

### 3. Logical AND Operator

```javascript
condition && <Component/>
```

---

### 4. Element Variables

```javascript
let content;

if(condition){

content=<Component/>;

}
```

---

# Benefits of List Rendering

- Faster Rendering
- Cleaner Code
- Easy Data Management
- Better Reusability
- Dynamic UI Updates

---

# Learning Outcome

- Implemented multiple Conditional Rendering techniques.
- Rendered multiple React Components.
- Used `map()` for List Rendering.
- Applied Keys in React.
- Displayed dynamic collections of data.
- Built a reusable React application structure.

---

# Result

Successfully developed a Blogger Application using React that demonstrates Conditional Rendering, List Rendering, Keys, and the `map()` function. The application dynamically displays Book Details, Blog Details, or Course Details based on the selected condition while following React best practices.
