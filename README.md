# ES6-Introduction

## Requirements
- node.js
- npm
- any preferred IDE (VS Code Recommended)

## let & const

**Before ES6**
```js
i = "This is i variable"
console.log(i)
j = "This is variable j"
console.log(j)

function test(){
    k = "This is the k variable"
    j = "I changed the j variable"
    console.log(i)
    console.log(j)
}

var i,j,k
test()

/*
Output:
This is i variable
This is variable j
This is i variable
This is variable j
*/

```
*```var``` supports hoisitng, i.e. moving all declarations to the begining of the code.*

**After ES6**
```js
const i = "This is i variable"
console.log(i)
let j = "This is variable j"
console.log(j)

function test(){
    const k = "This is the k variable"
    j = "I changed the j variable"
    // k = "Does this work" (This will cause error)
    console.log(k)
    console.log(j)
}

test()
/*
Output:
This is i variable
This is variable j
This is the k variable
I changed the j variable
*/
```
*```let``` & ```const``` doesn't support hoisitng. ```let``` variable can be reassigned where as ```const``` cannot be. It is however possible to mutate the properties of the ```const``` variable.*


## Template Literals
*Template literals are string literals which allow embedded expressions and multiline strings. Intead of ( ' ' ) or ( " " ) template literals use ( ``` ` ` ``` ) or backticks*

**Before ES6**
```js
var fName = "Ryad"
var lName = "Ahmed"
console.log("Hello " + fName + " " +lName)
var age = 23
console.log(fName + " is " + age + " years old")
/*
Output:
Hello Ryad Ahmed
Ryad is 23 years old
*/
```
**After ES6**
```js
const fName = "Ryad"
const lName = "Ahmed"
const bYear = 1996
const cYear = 2019
const age = cYear - bYear

console.log(`Hello ${fName} ${lName}
${fName} is ${cYear-bYear} years old ${ age<=30 ? 'young man':'old man' }`)
/*
Output:
Hello Ryad Ahmed
Ryad is 23 years old
*/
```

## Destructuring

**Before ES6**
```js
var fullName = ["John", "Smith"];
var firstName = fullName[0];
var lastName = fullName[1];

console.log(firstName, lastName);
/*
Output:
John Smith
*/ 
```
###### In case of objects:
```js
const fullName = { first: "John", last: "Smith"};

console.log(fullName.first, fullName.last);

Output:
John Smith
*/
```
**After ES6**
```js
const fullName = ["John", "Smith"];
const [firstName, lastName] = fullName;

console.log(firstName, lastName);
/*
Output:
John Smith
*/
```
###### In case of objects:
*NOTE: Make sure the properties for the objects exist otherwise it wouldn't work*
```js
const fullName = { first: "John", last: "Smith"};
const {first, last} = fullName;

console.log(first, last);
/*
Output:
John Smith
*/
```

## Spread Operator
*It allows us to spread the contents of a literal.*

```js
const person = {
    fName: "Ryad",
    lName: "Ahmed",
    age: 23,
    status: {
        gender: "man",
        marital: "single"
    }
}

const newPerson = {
    ...person
}

console.log(person == newPerson)

newPerson.fName = "Omer"
newPerson.lName = "Sayeem"

console.log(person)
console.log(newPerson)

const people = [{...person},{...newPerson}]

console.log(people)

const numbers = [1,2,3]

const moreNumbers = [...numbers,4,5,6]

console.log(numbers)
console.log(moreNumbers)

/*
false
{ fName: 'Ryad',
  lName: 'Ahmed',
  age: 23,
  status: { gender: 'man', marital: 'single' } }
{ fName: 'Omer',
  lName: 'Sayeem',
  age: 23,
  status: { gender: 'man', marital: 'single' } }
[ { fName: 'Ryad',
    lName: 'Ahmed',
    age: 23,
    status: { gender: 'man', marital: 'single' } },
  { fName: 'Omer',
    lName: 'Sayeem',
    age: 23,
    status: { gender: 'man', marital: 'single' } } ]
[ 1, 2, 3 ]
[ 1, 2, 3, 4, 5, 6 ]
*/
```
