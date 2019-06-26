# Brief intro to Arrow Functions and Template strings

## ARROW FUNCTIONS

bar written in ES5 :

```
function bar(){
  return "hello"
}
```
bar written in ES6 :
```
const bar = () => {
 return "hello"
 }
```

--------------------------------------
1. write newFunc in ES6

```

function newFunc(a, b) {
  return a
}
```


2. convert the anonymous function to be written in ES6 

```
const arr = [1,2,3]

const double = arr.map(function(e, i){
  return e * 2
})

```

## TEMPLATE STRING
```
const str = "it"
const str2 = "is"
const str3 = "sunny"

const sentence = str + " " + str2 + " " + str3
// output will be "it is sunny"
```
the same thing written with template strings is:
```
const sentence2 = 
`${str} ${str2} ${str3}`
```
--------------------------------------
1. console.log a sentence that says 'i love bananas' using the fruit variable
```
const fruit = "bananas"
```

2. for each fruit in the array console log 'i love <fruit>'
```
const fruits = ['apples', 'cherries', 'bananas']
```

