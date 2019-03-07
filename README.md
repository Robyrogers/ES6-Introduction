# ES6-Introduction

## Requirements
- node.js
- npm
- any preferred IDE (VS Code Recommended)

## let & const

**Before ES6**
```
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
```
const i = "This is i variable"
console.log(i)
let j = "This is variable j"
console.log(j)

function test(){
    const k = "This is the k variable"
    j = "I changed the j variable"
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
*```let``` & ```const``` doesn't support hoisitng. ```let``` varibale can be reassigned where as ```const``` cannot be. It is however possible to mutate the properties of the ```const``` variable.*
