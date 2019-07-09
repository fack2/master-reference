# Let's get linting!

## Intro
Linters are really useful as they detect and flag errors in your code. This readme is going to walk through how to set up `eslint` on your projects. This is useful because it:

- helps find small errors like typos!
- gives fixed formatting rules for your code eg indentation, spacing ect
- allows you to share a config file between your team to avoid merge conflicts


## Let's do the thing

### Setup eslint config
The following instructions need to be followed by **one person on your team** . Everyone else can get the packages by running `npm i`

`cd [project-name]` - cd into your project

`npm i -D eslint` - locally install eslint as a dev-dependency

`./node_modules/.bin/eslint --init` - initialises eslint
After this pick the following inputs:
- [How would you like to use ESLint?] `To check syntax and find problems`
- [What type of modules does your project use?] `JavaScript modules`
- [Which framework does your project use?] `None of these`
- [Where does your code run?] `select Browser and Node`
- [What format do . you want your config file to be in?] `JavaScript`


:boom: BOOM :boom: you've set up your linting configuration! you will now have a .eslintrc.js file with the config you have set up (you can change it if you made any mistakes)

Yay. Wait. Now what?!

### Lint your files!

So you can run your linter on all the files (in your directory) using the following command in your terminal:

`./node_modules/.bin/eslint [yourfile.js]`

Hopefully you should see something like this:

![linter running in the terminal](https://user-images.githubusercontent.com/14337958/33136597-85ef40f8-cf9d-11e7-8a77-aea69053bd60.png)

You can even set up a linting script in your package.json if you want. 

```
"lint": "eslint"
```

Cool huh? :ice_cream: 

**note** : scripts in the package json already know to look in the .bin folder in node_modules folder so you dont need to write`./node_modules/.bin/eslint ` you can just write `eslint`

But wait, this isn't actually that useful when it comes to writing code - I have to run this and manually compare it to my editor to fix things... :confused: 

Well, what if you could live see your linting errors as you go, in your editor? 

You can! :tada: 

### Setup your editor
To get your linter configuration working with your editor you need to install the following extentions:

**Atom** - `linter`, `linter-eslint`, `linter-ui-default`  
**VS Code** - `eslint`  
**VIM** - `¯\_(ツ)_/¯`

Restart your editor and you should now see errors underlined with a red line 

:heart:
