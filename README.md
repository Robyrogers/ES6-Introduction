# ES6-Introduction
- [let & const](#let--const)
- [Template Literals](#template-literals)
- [Tagged Templates](#tagged-templates)
- [Destructuring](#destructuring)
- [Spread Operator](#spread-operator)



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
*`var` supports hoisitng, i.e. moving all declarations to the begining of the code.*

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
*`let` & `const` doesn't support hoisitng. `let` variable can be reassigned where as `const` cannot be. It is however possible to mutate the properties of the `const` variable.*
[Top](#es6-introduction)

## Template Literals
*Template literals are string literals which allow embedded expressions and multiline strings. Intead of ( ' ' ) or ( " " ) template literals use ( \` \` ) or backticks*

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
[Top](#es6-introduction)

## Tagged Templates
*A sort of function that takes [Template Literals](#template-literals) as an arguement*

```js
const person = 'Mike';
const age = 28;

function myTag(strings, personExp, ageExp) {

//The first parameter always holds the string portion of the passed template literal arguement in an array of strings
//Every time there is a ${} inside the template literal the string is divided into different indexes of an array
//All the ${} are passed down as arguements for the parameters in the same order as they are present inside the template

  const str0 = strings[0] // "That "
  const str1 = strings[1] // " is a "

  // There is technically a string after
  // the final expression (in our example),
  // but it is empty (""), so disregard.
  // var str2 = strings[2]

  let ageStr
  if (ageExp > 99){
    ageStr = 'centenarian'
  } else {
    ageStr = 'youngster'
  }
  console.log(`${str0}${personExp}${str1}${ageStr}`)
}

myTag`That ${ person } is a ${ age }`

/*
That Mike is a youngster
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
[Top](#es6-introduction)

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
[Top](#es6-introduction)

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

console.log(person == newPerson)//false

newPerson.fName = "Omer"
newPerson.lName = "Sayeem"

console.log(person)
/*
{ fName: 'Ryad',
  lName: 'Ahmed',
  age: 23,
  status: { gender: 'man', marital: 'single' } }
*/

console.log(newPerson)
/*
{ fName: 'Omer',
  lName: 'Sayeem',
  age: 23,
  status: { gender: 'man', marital: 'single' } }
*/

const people = [{...person},{...newPerson}]

console.log(people)
/*
[ { fName: 'Ryad',
    lName: 'Ahmed',
    age: 23,
    status: { gender: 'man', marital: 'single' } },
  { fName: 'Omer',
    lName: 'Sayeem',
    age: 23,
    status: { gender: 'man', marital: 'single' } } ]
*/

const numbers = [1,2,3]

const moreNumbers = [...numbers,4,5,6]

console.log(numbers)
/*
[ 1, 2, 3 ]
*/
console.log(moreNumbers)
/*
[ 1, 2, 3, 4, 5, 6 ]
*/
```
[Top](#es6-introduction)

## Default Parameters
*ES6 allows us to have  default parameters for functions*

**Before ES6**
```js
function sum(a,b){
    if(a==undefined){
        a = 0
    }
    if(b==undefined){
        b = 0
    }
    
    return a+b  
}

console.log(sum())   //0
console.log(sum(2))  //2
console.log(2,5)     //7
```
**After ES6**
```js
function sum(a=0,b=0){
    return a+b  
}

console.log(sum())   //0
console.log(sum(2))  //2
console.log(2,5)     //7
```

