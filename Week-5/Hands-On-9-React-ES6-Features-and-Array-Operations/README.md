# Hands-On 9: React ES6 Features and Array Operations

## Objective

The objective of this hands-on exercise is to understand the important features of ES6 in React applications by implementing array operations, arrow functions, destructuring, and the spread operator. The application demonstrates player management for a cricket team.

---

# Learning Objectives

After completing this exercise, you will be able to:

- Understand ES6 features used in React.
- Differentiate between `var`, `let`, and `const`.
- Use Arrow Functions.
- Apply `map()` for rendering data.
- Use `filter()` with arrow functions.
- Implement Array Destructuring.
- Merge arrays using the Spread Operator.

---

# Software Requirements

- Node.js
- npm
- Visual Studio Code
- ReactJS

---

# Project Name

cricketapp

---

# Scenario

Develop a Cricket Management application.

The application should:

- Display a list of cricket players.
- Filter players scoring below 70.
- Display Odd Team and Even Team players using Destructuring.
- Merge T20 and Ranji Trophy player lists.
- Display components using a simple if-else condition.

---

# Step 1: Create React Project

Open Terminal.

Execute:

```bash
npx create-react-app cricketapp
```

---

# Step 2: Navigate to Project

```bash
cd cricketapp
```

---

# Step 3: Open Project

```bash
code .
```

---

# Project Structure

```text
cricketapp
│
├── src
│
├── Components
│      ├── ListOfPlayers.js
│      ├── IndianPlayers.js
│
├── App.js
│
└── package.json
```

---

# ListOfPlayers.js

```javascript
import React from "react";

function ListOfPlayers() {

    const players = [

        {name:"Virat Kohli",score:95},
        {name:"Rohit Sharma",score:88},
        {name:"Shubman Gill",score:75},
        {name:"KL Rahul",score:65},
        {name:"Hardik Pandya",score:72},
        {name:"Ravindra Jadeja",score:60},
        {name:"Surya Kumar",score:91},
        {name:"Rishabh Pant",score:68},
        {name:"Bumrah",score:80},
        {name:"Siraj",score:55},
        {name:"Shami",score:78}

    ];

    const filteredPlayers =
    players.filter(player=>player.score<70);

    return(

        <div>

            <h2>List of Players</h2>

            {

                players.map((player,index)=>

                    <p key={index}>

                        {player.name} - {player.score}

                    </p>

                )

            }

            <h2>Players with Score Below 70</h2>

            {

                filteredPlayers.map((player,index)=>

                    <p key={index}>

                        {player.name} - {player.score}

                    </p>

                )

            }

        </div>

    );

}

export default ListOfPlayers;
```

---

# IndianPlayers.js

```javascript
import React from "react";

function IndianPlayers(){

    const players=[
        "Virat",
        "Rohit",
        "Gill",
        "Rahul",
        "Pant",
        "Jadeja"
    ];

    const [
        odd1,
        even1,
        odd2,
        even2,
        odd3,
        even3
    ]=players;

    const t20Players=[
        "Virat",
        "Rohit",
        "Surya"
    ];

    const ranjiPlayers=[
        "Sarfaraz",
        "Jaiswal",
        "Patidar"
    ];

    const mergedPlayers=[
        ...t20Players,
        ...ranjiPlayers
    ];

    return(

        <div>

            <h2>Odd Team Players</h2>

            <p>{odd1}</p>
            <p>{odd2}</p>
            <p>{odd3}</p>

            <h2>Even Team Players</h2>

            <p>{even1}</p>
            <p>{even2}</p>
            <p>{even3}</p>

            <h2>Merged Players</h2>

            {

                mergedPlayers.map((player,index)=>

                    <p key={index}>{player}</p>

                )

            }

        </div>

    );

}

export default IndianPlayers;
```

---

# App.js

```javascript
import React from "react";

import ListOfPlayers from "./Components/ListOfPlayers";
import IndianPlayers from "./Components/IndianPlayers";

function App(){

    const flag=true;

    if(flag){

        return <ListOfPlayers/>;

    }

    else{

        return <IndianPlayers/>;

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

### When `flag = true`

- List of all 11 cricket players.
- List of players with scores below 70.

### When `flag = false`

- Odd Team Players.
- Even Team Players.
- Merged T20 and Ranji Trophy players.

---

# Explanation

## ES6 Features Used

### let

Used to declare block-scoped variables.

### const

Used to declare variables whose reference should not change.

### Arrow Function

Example:

```javascript
player => player.score < 70
```

Used for concise function expressions.

### map()

Used to iterate through arrays and render JSX.

```javascript
players.map(player => ...)
```

### filter()

Returns elements matching a condition.

```javascript
players.filter(player => player.score < 70)
```

### Destructuring

Extracts array elements into variables.

```javascript
const [odd1, even1, odd2, even2] = players;
```

### Spread Operator

Merges arrays.

```javascript
const mergedPlayers = [...t20Players, ...ranjiPlayers];
```

---

# Difference Between var, let and const

| var | let | const |
|------|------|-------|
| Function Scoped | Block Scoped | Block Scoped |
| Can be Redeclared | Cannot be Redeclared | Cannot be Reassigned |
| Older JavaScript | ES6 | ES6 |

---

# Benefits of ES6

- Cleaner syntax
- Better readability
- Improved performance
- Easier array manipulation
- Enhanced code reusability

---

# Learning Outcome

- Used ES6 features in React.
- Implemented Arrow Functions.
- Used map() and filter().
- Applied Array Destructuring.
- Merged arrays using Spread Operator.
- Displayed components conditionally.

---

# Result

Successfully developed a React Cricket Management application using modern ES6 features including Arrow Functions, `map()`, `filter()`, Destructuring, and the Spread Operator to manage and display cricket player information efficiently.
