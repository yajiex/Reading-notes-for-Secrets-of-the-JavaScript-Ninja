# Chapter 9: Runtime code evaluation
* `ninja = 5`, this statement returns `undefined`
* For `eval()`, anything that isn't a simple variable, primitive, or assignment will need to be wrapped in parentheses in order for the correct value to be returned.
* The last argument of a variable argument list to the `Function` constructor is always the code that will become the body of the function. Any preceding arguments represent he names of the parameters for the function. No closures are created when functions are created via the `Function` constructor.
* Browsers will ignore any `script` type that it doesn't understand. We can force the browser to completely ignore a `script` block (and use it for whatever nefarious purposes we want) by using a type value that's not standard
* 
