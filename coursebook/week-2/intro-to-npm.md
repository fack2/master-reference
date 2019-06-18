# An introduction to npm



npm is Node's package manager. It's a repository of hundreds of thousands of useful pieces of code that you may want to integrate with your Node project.

npm also has a command line tool that lets us easily install, manage and run projects.

### to use npm 
the first step is to run
``` 
npm init -y
```
this creates a package.json which is the file that manages all your packages.

then to install a package you can do either:
``` 
npm install <package> -S
```
or 
``` 
npm install <package> -D
```

you use -S to save it as a dependency. A dependency is a package that your application needs to run (i.e. things that need to be installed on the server delivering your application).


you use -D to save as a development-dependency. A dev-dependency is a package that your project doesn't need in production (e.g. testing frameworks are generally only used in development — you don't need it on your live server).



### `.gitignore`

A `.gitignore` file is a way to tell Git to leave certain things alone.

This is a good time to mention that you want to keep your `node_modules` folder off Github. There can be hundreds of thousands of files in this directory, which can make for some ugly commits. It can also take up a huge amount of space on something like Github as this folder can easily exceed 100MB for applications with lots of dependencies.

If you are creating a repository on Github then you can use the 'Add .gitignore file' dropdown to automatically generate a variety of `.gitignore` files for different kinds of projects. You'll want to choose 'Node' here.

If you're working locally you can create a file called `.gitignore` at the root of your project and add `node_modules`.


### npm scripts

You may have noticed that npm created a section called "scripts" in your `package.json`. These are handy shortcuts you can create to run dependencies you install. Think of them as per project command line aliases.


```json
{
  "scripts": {
    "greeting": "cowsay hello"
  }
}
```

and run it with `npm run greeting`, and this would be exactly the same as running `cowsay hello` in the terminal. This is useful when the commands become long we can call them with a small script. 

## Tasks

1. Create a new directory
2. Inside the new directory, initialise the project with `npm init -y`
3. Install Cowsay `npm install cowsay -D`
4. Have a look at the `package.json` file
5. Open `node_modules` and see if you can find Cowsay
6. Run `node_modules/.bin/cowsay hello`
7. Add `"greeting": "cowsay hello"` to your npm scripts
8. Run `npm run greeting`
