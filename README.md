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


##Template Literals
*Template literals are string literals which allow embedded expressions and multiline strings. Intead of ( ' ' ) or ( " " ) template literals use ( ` ` ) or backticks*

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

console.log(`Hello ${fName} ${lName}
${fName} is ${cYear-bYear} years old`)
/*
Output:
Hello Ryad Ahmed
Ryad is 23 years old
*/
```
