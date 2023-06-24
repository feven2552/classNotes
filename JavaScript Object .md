# JavaScript Object

# JavaScript Object

In JavaScript, an object is a collection of properties, where each property is a key-value pair. The key is always a string, and the value can be of any data type, such as a number, string, boolean, or even another object.

There are two ways to create an object in JavaScript - using object literal notation and using the object constructor.

## Object Literal Notation

To create an object using object literal notation, we use curly braces {} and define the properties and their values inside it, separated by a colon :

```
let person = {
  name: "John",
  age: 30,
  isMarried: true
};

```

In the above example, we have created an object named 'person' with three properties - name, age, and isMarried.

## Object Constructor

To create an object using the object constructor, we use the new keyword followed by the Object() constructor function.

```
let person = new Object();
person.name = "John";
person.age = 30;
person.isMarried = true;

```

In the above example, we have created the same 'person' object using the object constructor. We add properties to the object using dot notation.

### Accessing Object Properties

We can access the properties of an object using dot notation or bracket notation.

```
console.log(person.name); // John
console.log(person['age']); // 30

```

### Adding and Deleting Object Properties

We can add or delete properties to an object using dot notation or bracket notation.

```
person.job = "Developer"; // Adding a new property
delete person.isMarried; // Deleting a property

```

### Object Methods

We can also add methods to an object. A method is a function that belongs to an object.

```
let person = {
  name: "John",
  age: 30,
  isMarried: true,
  greet: function() {
    console.log("Hello!");
  }
};
person.greet(); // Hello!

```

In the above example, we have added a method named 'greet' to the 'person' object. We can call this method using dot notation.

```jsx
// Creating an object
var person = {
  name: "John Doe",
  age: 30,
  occupation: "Software Developer"
};

// Accessing object properties
console.log(person.name); // Output: John Doe
console.log(person.age); // Output: 30
console.log(person.occupation); // Output: Software Developer

// Modifying object properties
person.age = 32;
console.log(person.age); // Output: 32

// Adding new properties
person.location = "New York";
console.log(person.location); // Output: New York

// Deleting a property
delete person.occupation;
console.log(person); // Output: { name: 'John Doe', age: 32, location: 'New York' }
```

In the example above, we create an object called **`person`** using object literal notation, surrounded by curly braces **`{}`**. The object has three properties: **`name`**, **`age`**, and **`occupation`**. We can access and modify the properties using dot notation (**`object.property`**) or bracket notation (**`object['property']`**). We can also add new properties dynamically using dot notation or bracket notation. To delete a property, we use the **`delete`** operator followed by the object's property name.

Objects in JavaScript provide a flexible way to store and organize data, making them a powerful tool in web development and other JavaScript applications.

```jsx
//1. Find the person who has many skills in the users object:

javascript
Copy code
let maxSkills = 0;
let skillfulPerson = '';

for (let user in users) {
  const skillsCount = users[user].skills.length;
  if (skillsCount > maxSkills) {
    maxSkills = skillsCount;
    skillfulPerson = user;
  }
}

console.log(skillfulPerson); // Output: Asab
The above code iterates over each user in the users object and compares the length of their skills array. It keeps track of the person with the maximum number of skills (maxSkills) and assigns their name to the skillfulPerson variable.

//2. Count logged-in users and count users having greater than or equal to 50 points:

let loggedInCount = 0;
let highPointsCount = 0;

for (let user in users) {
  if (users[user].isLoggedIn) {
    loggedInCount++;
  }
  if (users[user].points >= 50) {
    highPointsCount++;
  }
}

console.log(loggedInCount); // Output: 2
console.log(highPointsCount); // Output: 4
The code above uses two separate counters (loggedInCount and highPointsCount) to keep track of the number of logged-in users and the number of users with points greater than or equal to 50.

//3. Find people who are MERN st noack developers from the users object:

let mernStackDevelopers = [];

for (let user in users) {
  const skills = users[user].skills;
  if (
    skills.includes('MongoDB') &&
    skills.includes('Express') &&
    skills.includes('React') &&
    skills.includes('Node')
  ) {
    mernStackDevelopers.push(user);
  }
}

console.log(mernStackDevelopers); // Output: ['Asab', 'Brook', 'Paul']
The code checks if each user's skills array includes the required skills for the MERN stack (MongoDB, Express, React, and Node). If all the skills are present, the user's name is added to the mernStackDevelopers array.

4. Set your name in the users object without modifying the original users object:

javascript
Copy code
const updatedUsers = { ...users, YourName: {} };

console.log(updatedUsers);
The above code creates a shallow copy of the users object using the spread operator (...). It then adds a new property to the copied object with your name as the key (YourName) and an empty object as its value.

5. Get all keys or properties of the users object:

const userProperties = Object.keys(users);

console.log(userProperties);
The Object.keys() method is used to extract all the keys (properties) of the users object and stores them in the userProperties array.

6. Get all the values of the users object:

const userValues = Object.values(users);

console.log(userValues);
The Object.values() method is used to extract all the values of the users object and stores them in the userValues array.
```