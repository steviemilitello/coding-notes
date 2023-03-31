<div align="center">
   <h1>:woman_technologist: Introducing TypeScript to Your Applications :woman_technologist:</h1>
</div>

<h1>Introduction</h1>

<h3>Why TypeScript?</h3>

- Typescript vs. JavaScript - JavaScript is Dynamic - It allows everything and has a forgiving nature, but also allows mistakes
- TypeScript is designed to catch problems in JavaScript code
- It has Strong Static Typing on top of JavaScript 
- It adds compile time that will catch common issues and help you write better code - with inline documentation and guidance 
- It extends JavaScript and is a Superset of it 
- It complies down to JavaScript 
- It is built for large applications, but a good size for applications of any size

<h3>Adding TypeScript to Your Application</h3>

<h4>Install Typescript</h4>

- Need to compile TypeScript to run it, Need to install TypeScript Compiler 
- Recommended to install at the project level so each project can run on a different version and one version doesn’t break another

<h4>Adding TypeScript to an Existing Solution</h4>

- Add TypeScript configuration file to the root of your Application’s code base called `tsconfig.json`
- Run the TypeScript Complier with `tsc` in CLI when making changes to `tsconfig`
- Supply parameters of paths to files you would like to include 
- TypeScript files have `.ts` extension and can use JavaScript

<h3>Example Configuration File</h3>

```
{
	“complierOptions”: {
		“target”: “ES6”
	},
	“include”: [“path/**/*”]
}
```
- Will know if the TypeScript Configuration works if there is an output file that complies to JavaScript after running `tsc`
- You can find more settings in [Complier Options](https://www.typescriptlang.org/tsconfig) in the TypeScript Documentation
- You can target ES6 (or the most current version of JavaScript)
- By default the JavaScript files render right next to the TypeScript files
	- If only using only the TypeScript, you can direct output to another folder by setting `outDir` to the folder where you want the files
	- use `“noEmit”: true` if only using TypeScript for Type Checking

<h3>Adding Type Checking to JavaScript</h3> 

- To enable checking of existing JavaScript file add two additional setting to `tsconfig` under `complierOptions`  -  `“allowJS”: true`  and  `“checkJS:: true`

<h3>Importing Third-Party Types</h3>

- At some point you will come across a library that doesn’t offer TypeScript support
- If the library is open source you can install types that people have created online - These can be found in the Definitely Typed Github Repository, although it easier to install via npm
- You can search @types on npm and find the types for the library you need
- `.d.ts` is the TypeScript Declaration Files

<h1>Questions</h1>

<h3>JavaScript is Dynamically Typed - What Does That Mean?</h3>

- Dynamically typed means that the variable is assigned a type at runtime, as opposed to during compile/build

<h3>What is Strong Static Typing?</h3>

- Strong Typing means that variables and other data structures can be declared to be a specific type, like a string or boolean, by the programmer and TypeScript will check the validity of their values
- Static Typing means that all checks with performed during the compile/build time before we actually execute the program. The opposite is Dynamic Typing which is checked at run time. 

<h3>TypeScript is a Superset of JavaScript - What Does that Mean?</h3> 

- TypeScript understands all of JavaScript’s syntax and capability, while adding additional features, such as Static Typing

<h3>What is a Complier?</h3> 

- A Complier is a special program that translates a programming language’s source code into machine code or another programming language

<h3>What is Type Checking in TypeScript?</h3>

- Type Checking is used to validate the type of any variable. With Typescript, it checked at compile time to check any errors in the code. 

<h3>What are TypeScript Declaration Files?</h3> 

- TypeScript Declaration Files are files that describe the shape of an existing JavaScript codebase to TypeScript 
- `.d.ts`  and only include type information. They don't produce `.js` outputs, and are only used for typechecking
- Meanwhile `.ts` files are Implementation files that contain types and executable code. These produce `.js` outputs.

<h1>Resources</h1>

<h3>TSConfig Reference</h3>

https://www.typescriptlang.org/tsconfig/

[<img src="https://i.imgur.com/nqYk01k.png" width="700">](https://www.typescriptlang.org/tsconfig/)

<h1>:computer: Technologies Used</h1>

![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-323330?style=for-the-badge&logo=javascript&logoColor=F7DF1E) 


