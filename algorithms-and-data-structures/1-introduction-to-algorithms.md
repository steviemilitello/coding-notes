<div align="center">
   <h1>:woman_technologist: Introduction to Algorithms :woman_technologist:</h1>
</div>

<h1>What is an Algorithm?</h1>


- A set of steps or instructions for completing a task
- More specifically a set of steps a program takes to finish a task
- Any code generally can be considered an Algorithm
- Given this, what do people mean when they say “You Should know about Algorithms?”
- Solutions to common problems that field of Computer Science has decided do the job well for the given task
- Established body of knowledge on how to solve particular problems well, and it’s important to know what these solutions are
- It is important b/c if you are unaware of a solution exists, you may try to come up with one yourself, and it’s likely your solution won’t be as efficient as one that has been thoroughly reviewed
- Not just knowing when it exists, but when to apply it.
- It is important because it gives you a deeper understanding of complexity and efficiency in programming
- Specificity of how something is defined

<h1>Defining an Algorithm</h1>


- Must have a clearly defined problem statement, input, and output
- Has a set of steps that solves the problem
- Definition must contain a specific set of instructions in a particular order
- Each step must be explicitly clear -> You shouldn’t be able to break down the steps into additional subtasks
- They should produce a result, if we didn’t we have no way of verifying that it worked correctly.
- However, the value can be nothing, which indicates it didn’t work.
- As long as it produces some result, we can understand it’s behavior
- Should actually complete and cannot take an infinite amount of time

<h1>Algorithmic Thinking</h1>


- Breaking down a problem in steps and determining which Algorithm or Data Structure is best for the job
- Establish bounds of the problem -> Clearly define what the problem set is and clarify
- With any given problem, there is no given one best solution, what we should try instead is what solution works better for current problem

<h1>Search Algorithms</h1>

<h2> Evaluating a Linear Search</h2>

- Also called Sequential Search or Simple Search
- Input - Series of values
- Output - Matching the value we are looking for

<h3>Steps</h3>


1. Start at Beginning
	- We start at beginning of a list or range of values
2. Compare Current Value to Target
	- Then we compare the current value to the target
3. Move Sequentially
	- If the current value is the target value, we’re done
	- If not, we move on to next value in the list and compare again
4. Reach End of List
	- If we reach the end of the list, then the target value is not in the list

<h3>Linear Search Example</h3>

```javascript
const linearSearch = (array, key) => {
  for(let i = 0; i < array.length; i++){
    if(array[i] === key) {
        return i;
    }
  }
  return -1;
}
```
<h2> Evaluating a Binary Search </h2>

