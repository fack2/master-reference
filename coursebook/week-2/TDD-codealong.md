# myGame Code Along
Explain what a codealong is.

We’re going to re create the rock paper scissors game from week 0, but we are going to write it using TDD.

We’re going to start with an empty directory we’ll call myGame, cd into it and run npm init.

`mkdir myGame` and `cd myGame`, `npm init -y`

We’re then going to run `npm install -D tape tap-sec`. Tape is our test framework and tap-spec is a formatter for the output of tape. I’ll show you the difference between them in a sec. 

/Navigate to package.json./ You can see the dev dependancies in the package.json.

Add a npm script for the test command. 

`”test”: "tape myGame.test.js"`

/Create the myGame.test.js file./ Import the tape library. 

`const test = require(‘tape’)`  so we have tape in the test variable.

Describe what we’re testing and a callback. In this case we’ll just test if tape is working. 

```javascript
test(‘Tape is working’, function(t) {
	t.equal(1, 1, 'One should equal one')
	t.end() // tells tape that we're done with our tests
})
```

Now if we run `npm test` you get the results that the test pass correctly. This isn’t good to look at to see at a glance what’s going on so we’ll use tap-spec to make it look a bit better. 

We’ll use the pipe command that takes the output of the first section and sends it into what comes after the symbol. /run it/ You can see it looks a lot better - colour and ticks. 

`”test”: "tape myGame.test.js | tap-spec"`

We’re going to be using test driven development today - meaning we’re going to be writing tests before we write any code. So we need to think about what our function to do, what it should take in, what it should output. We want this function to take in a number and we want it to output a string.  So for our first test we can say 

```javascript
test(‘myGame output’, function(t) {
	const actual = myGame("paper", "scissors")
	const expected = 'you lose'
	t.equal(actual, expected, 'scissors beats paper')
	t.end()
})
```

This is isn’t going to run yet because we don’t have myGame imported. 

`const myGame = require(‘./myGame.js’) // ./ means the folder we're in` 

/create myGame.js/ In this file we want a function called myGame which takes in two strings and doesn’t do anything.

```javascript
function myGame(myChoice, opponentsChoice) {
	return;
}
```

In order for our test file to import it we need our myGame file to export it. 

`module.exports = myGame`

Now hopefully when we run our test  we should get back a failing test. If you see how it expected 'you lose' but got undefined because we’re not returning anything from our function right now. 

The way TDD works is now we have a failing test we want to write some code to make our tests pass in the simplest way possible. Let’s say for now the function returns 'you lose'. 

```javascript
function myGame(myChoice, opponentsChoice) {
	return 'you lose';
}
```

There you go, we have two passing tests. This seems a bit counterintitituve because this code isn’t going to keep working as as soon as we right more tests it’s going to be failing again but the idea with TDD is you keep writing as little code as you need to pass the current failing test and build and build on that until you reach your final solution. So we’re going to try to keep relatively strictly to that. Now we’ll test to see what happens when we give myGame('paper', 'paper'). 

```javascript
test('myGame returns the correct result', function(t) {
  const actual = myGame('paper', 'paper');
  const expected = 'tie';
  t.equal(actual, expected, 'both chosing paper should return tie');
  t.end();
});  
```

Now this test should be failing. 'paper, paper' should return 'tie' but our function only returns 'you lose'. The simplest way I can think of to solve that is to 

```javascript
function myGame(myChoice, opponentsChoice) {
  if (myChoice === 'paper' && opponentsChoice ==='paper') return 'tie';
  return 'you lose';
}
```

The test should now pass. Just a quick aside here, getting slightly annoying with running npm test over and over again. We can use a module called nodemon  which is a demon that watches the files and then reruns everything when it notices the file changes. 

`npm install -D nodemon`

We then tell our test script to use nodemon instead of tape.

`”test”: "nodemon myGame.test.js | tap-spec"`

It should watch our test file for us and update every time we save it.

```javascript
test('myGame returns the correct result', function(t) {
  const actual = myGame('paper', 'rock');
  const expected = 'you win';
  t.equal(actual, expected, 'paper wins over rock');
  t.end();
});  
```


```javascript
function myGame(myChoice, opponentsChoice) {
  if (myChoice === 'paper' && opponentsChoice === 'paper'){
              return 'tie';
  }
  if (myChoice === 'paper' && opponentsChoice === 'rock') {
              return 'you win'
}
  return 'you lose';
}
```



So let’s keep on going with the TDD process and see where it takes us next. We’re going to check 4 now. 4 should equal V. Again this is going to fail which is what we want. The simplest way to do this is to add

```javascript
test('myGame returns the correct result', function(t) {
  const actual = myGame('rock', 'rock');
  const expected = 'tie';
  t.equal(actual, expected, 'rock and rock should tie');
  t.end();
});  
```

we could add another condition that says
```javascript
if (myChoice === 'rock' && opponentsChoice === 'rock') {
	return 'tie'
}
```
but we can see that we can avoid extra code by instead writing

```javascript

  if (myChoice === opponentsChoice ){
              return 'tie';
  }

```


```javascript
test('myGame returns the correct result', function(t) {
  const actual = myGame('rock', 'scissors');
  const expected = 'you win';
  t.equal(actual, expected, 'rock wins over scissors');
  t.end();
});  
```

then we can add 

```javascript
  if (myChoice === 'rock' && opponentsChoice === 'scissors') {
              return 'you win'
}
```

next test 

```javascript
test('myGame returns the correct result', function(t) {
  const actual = myGame('rock', 'paper');
  const expected = 'you lose';
  t.equal(actual, expected, 'rock loses over paper');
  t.end();
});  
```

this test passes because the deafult is to return 'you lose', so we dont need to add any code to make this pass. 


```javascript
test('myGame returns the correct result', function(t) {
  const actual = myGame('scissors', 'scissors');
  const expected = 'tie';
  t.equal(actual, expected, 'scissors and scissors should tie');
  t.end();
});  
```

again, this passes so we dont need to add any code. the next test is

```javascript
test('myGame returns the correct result', function(t) {
  const actual = myGame('scissors', 'paper');
  const expected = 'you win';
  t.equal(actual, expected, 'scissors should win over paper');
  t.end();
});  
```

we can add this

```javascript
  if (myChoice === 'scissors' && opponentsChoice === 'paper') {
              return 'you win'
}
```
final test 
```javascript
test('myGame returns the correct result', function(t) {
  const actual = myGame('scissors', 'rock');
  const expected = 'you lose';
  t.equal(actual, expected, 'scissors should lose over rock');
  t.end();
});  
```

this passes because the default return is 'you lose'

the final function is: 

```javascript
function myGame(myChoice, opponentsChoice) {
  if (myChoice === 'paper' && opponentsChoice === 'paper'){
              return 'tie';
  }
  
  
  if (myChoice === 'paper' && opponentsChoice === 'rock') {
              return 'you win'
}
  if (myChoice === 'scissors' && opponentsChoice === 'paper') {
              return 'you win'
}
  if (myChoice === 'rock' && opponentsChoice === 'scissors') {
              return 'you win'
}
  return 'you lose';
}
```

could refactor to


```javascript
function myGame(myChoice, opponentsChoice) {
 const winConditionOne= myChoice === 'paper' && opponentsChoice === 'rock'
 const winConditionTwo= myChoice === 'scissors' && opponentsChoice === 'paper'
 const winConditionThree= myChoice === 'rock' && opponentsChoice === 'scissors'
 
 if (myChoice === 'paper' && opponentsChoice === 'paper'){
              return 'tie';
  }
  if(winConditionOne || winConditionTwo || winConditionThree) {
              return 'you win'
}
  return 'you lose';
}
```

