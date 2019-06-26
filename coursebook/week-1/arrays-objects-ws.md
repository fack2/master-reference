# arrays 
```
const colorsArray = ["yellow", "red", "turquoise", "green", "blue"]
```
1. use the **filter** method to create an array with all colors from colorsArray that are longer than 5 letters long. expected answer is [ 'yellow', 'turquoise']

2.
    a) use the **forEach** method to create an array that has each color from colorsArray in capital letters. expected answer is [ 'YELLOW',  'RED', 'TURQUOISE', 'GREEN', 'BLUE' ]
    
    b) create the same array using the **map** method


3. use the **reduce** method to find the color with the most amount of letters in colorsArray.
expected answer is 'turquoise' (as a string, not in an array)







# objects
```
const myDog = {
  name: "Clyde", 
  breed: "boxer",
  age: 3, 
}
```
1. create an object called anotherDog with the properties "name", "breed" and "age" (you can choose the values for these properties)

2. without touching the variable add the information gender:female to myDog 
3. without touching the variable add the information gender:male to anotherDog using a different method to the one you used for question 2.

4. change the age of myDog from 3 to 7

5. without touching the variable create a method on the myDog object called 'playFetch' that, when called console.logs 'i am playing fetch'

6. create a method on myDog called "myName" that uses the 'this' keyword so that when called it console.logs 'my name is Clyde' . 

7. delete the property 'breed' from anotherDog 

8. create a function called hasBreed that takes an object and checks if it has the property 'breed'. hasBreed(myDog) should return true, hasBreed(anotherDog) should return false.

9. calculate how many key value pairs myDog contains

10. create a copy of myDog object so that if you change the name of the copy it does not change the name of the original. 

