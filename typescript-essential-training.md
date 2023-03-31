> ### Introduction <p>

#### Why TypeScript? <br>

- Typescript vs. JavaScript - JavaScript is Dynamic - It allows everything and has a forgiving nature, but also allows mistakes
- TypeScript is designed to catch problems in JavaScript code
- It has Strong Static Typing on top of JavaScript 
- It adds compile time that will catch common issues and help you write better code - with inline documentation and guidance 
- It extends JavaScript and is a Superset of it 
- It complies down to JavaScript 
- It is built for large applications, but a good size for applications of any size

#### Adding TypeScript to Your Application <p>

#### Install Typescript

- Need to compile TypeScript to run it, Need to install TypeScript Compiler 
- Recommended to install at the project level so each project can run on a different version and one version doesn’t break another

> ### Adding TypeScript to an Existing Solution 

- Add TypeScript configuration file to the root of your Application’s code base called `tsconfig.json`
- Run the TypeScript Complier with `tsc` in CLI when making changes to `tsconfig`
- Supply parameters of paths to files you would like to include 
- TypeScript files have `.ts` extension and can use JavaScript

#### Example Configuration File


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

#### Adding Type Checking to JavaScript 

- To enable checking of existing JavaScript file add two additional setting to `tsconfig` under `complierOptions`  -  `“allowJS”: true`  and  `“checkJS:: true`

#### Importing Third-Party Types

- At some point you will come across a library that doesn’t offer TypeScript support
- If the library is open source you can install types that people have created online - These can be found in the Definitely Typed Github Repository, although it easier to install via npm
- You can search @types on npm and find the types for the library you need
- `.d.ts` is the TypeScript Declaration Files

> ### Questions <p>

#### JavaScript is Dynamically Typed - What Does That Mean? 

- Dynamically typed means that the variable is assigned a type at runtime, as opposed to during compile/build

#### What is Strong Static Typing? 

- Strong Typing means that variables and other data structures can be declared to be a specific type, like a string or boolean, by the programmer and TypeScript will check the validity of their values
- Static Typing means that all checks with performed during the compile/build time before we actually execute the program. The opposite is Dynamic Typing which is checked at run time. 

#### TypeScript is a Superset of JavaScript - What Does that Mean? 

- TypeScript understands all of JavaScript’s syntax and capability, while adding additional features, such as Static Typing

#### What is a Complier? 

- A Complier is a special program that translates a programming language’s source code into machine code or another programming language

#### What is Type Checking in TypeScript?

- Type Checking is used to validate the type of any variable. With Typescript, it checked at compile time to check any errors in the code. 

#### What are TypeScript Declaration Files? 

- TypeScript Declaration Files are files that describe the shape of an existing JavaScript codebase to TypeScript 
- `.d.ts`  and only include type information. They don't produce `.js` outputs, and are only used for typechecking
- Meanwhile `.ts` files are Implementation files that contain types and executable code. These produce `.js` outputs.

> ### Resources <p>

[TS Config Reference](https://www.typescriptlang.org/tsconfig)




