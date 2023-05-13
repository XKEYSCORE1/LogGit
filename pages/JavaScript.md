- React JS Frontend Web Development
	- Javascript w/ new features added by ES6
	- ES6 is vital to understand React
- Creating variables with `var`, `const`, and `let`
  collapsed:: true
	- create a folder
		- create `index.html`
		  collapsed:: true
			- ```html
			  <!DOCTYPE html>
			  <html lang="en">
			   <head>
			     <meta charset="UTF-8">
			     <title>Document</title>
			  </head>
			  <body>
			    <script src="index.js"></script>
			  </body>
			  </html>
			  ```
		- create `index.js`
			- `var`
				- ```javascript
				  // old school way
				  var name = "Samuel";
				  name = "Sam"; // var "name" value can be changed over time 
				  
				  alert(name);
				  ```
					- variables can hold many different kinds of data
						- `strings` | `integer` | `functions` | `objects` | `arrays`
						-
				- ```javascript
				  // conditional 
				  if (true) {
				    var name = "Ryan";
				    // alert(name); both work since var is global scope 
				  }
				  
				  alert(name);
				  
				  // var "name" value is part of the window object
				  ```
				- Variables made with the `var` method become a property of the window object
					-
					- ``` console
					  input > window.name
					  output < "Ryan"
					  ```
					-
			- `const` - the `const` keyword allows you to declare a constant (a JS variable with a constant value)
				- similar to let variables, except value cannot be changed
				- ```javascript
				  // static variable
				  const name = "Ryan";
				  alert(name);
				  // const "name" values can not be changed
				  ```
			- `let` - the `let` keyword allows you to declare a variable with block scope
				-
				- What if you don't want to reference outside of the function? -> `let`
					- prevents conflicts between variable names
					- stays within it's surrounding scope
				- ``` javascript
				  if(true) {
				  	let name = "Ryan";
				    // value subject to change 
				    	name = "Ryan_is_so_cool"
				    	alert(name)
				  }
				  // variable "name" stays in scope when defined with `let` method
				  ```
- Template Strings
	- Better alternative to string concatenation
	- ```  javascript
	  let fname = 'Ryan';
	  let lname = 'd'
	  let age = prompt('Guess Ryan`s age...')
	  
	  // old way
	  let result = 'Your guess:  ' + fname + ' ' + lname + ' ' + age + ' years old'
	  
	  //using template string 
	  let result = `${fname} ${lname} is ${age} years old`
	  
	  ```
- Default parameters
	- ```  javascript
	  
	  ~~
	  //pre-defined variables 
	  function welcome(user, message){
	   	alert(`Hello ${user}, ${message}`); 
	  }
	  
	  welcome("Ryan", "Good morning!") //defined variables 
	  -------------------------------------
	  // Hello Ryan, Good morning! 
	  -------------------------------------
	  
	    
	  ~~
	  //undefined variables
	  function welcome(user, message){
	   	alert(`Hello ${user}, ${message}`); 
	  }
	  
	  welcome() //undefined variables
	  -------------------------------------
	  // Hello undefined, undefined
	  -------------------------------------
	   
	    
	  ~~
	  //default values 
	   function welcome(user="FBI agent", message ="G'day"){ //default parameters 
	  	alert(`Hello ${user}, ${message}`)
	  }
	  
	  welcome()
	  -------------------------------------
	  // Hello FBI agent, G'day
	  -------------------------------------
	  ```
- Arrow functions
	- Slightly different than regular functions
	- `Regular function`
		- ```  javascript
		  function greeting(message){
		    return allert(`${message} everyone!`);
		  }
		  
		  greeting('Good morning')
		  ```
	-
	- `Arrow function`
		- ```  javascript
		  let greeting = message => alert(`${message} everyone!`)
		  		// 		^	>1 argument = ()
		  // 1 statement being returned -> no return keyword
		  greeting('Good morning')
		  ```
		- ```  javascript
		  let createBlog = (title, body) => {
		    if (!title) {
		      throw new Error ('A title is required.')
		    }
		    
		    if (!body) {
		      throw new Error('Body cannot be empty.')
		    }
		    return alert(`${title} - ${body}`);
		  } 
		  
		  createBlog('Blog title', 'Blog body')
		  ```
		- ES5 vs ES6
			- ``` javascript
			  // ES5
			  // variable "x" = function (args "x", "y"); return "x" * "y"
			  var x = function(x,y) {
			    return x * y;
			  }
			  
			  //ES6
			  //constant 'x' = args ('x', 'y') => x times y
			  const x = (x, y) => x * y; 
			  ```
- Arrow functions and `this` keyword
  collapsed:: true
	- Normal function using `this`
		- ``` javascript
		  let nepal = {
		    
		    // add property
		    mountains: ['Everest', 'Fish Tail', 'Annapurna'],
		    
		    //add method
		    printWithDash: function(){
		      // console.log('inside printWithDash',this); -> points to property 
		      setTimeout(function(){
		        //console.log('inside setTimeout', this); -> points to window object
		        console.log(this.mountains.join(" - "))
		      }, 3000);
		    }
		  };
		  nepal.printWithDash();
		  ```
			- `this` -> local scope
			- function -> global window object (global scope)
			- method inside function -> points to function object
			- benefit from using arrow functions -> arrow functions don't have their own enclosing context
				- If used within another function -> will point to the enclosing our outer function context
	- Arrow function using `this`
		- ``` javascript
		  let nepal = {
		    
		    //add property
		    mountains: ['Everest', 'Fish Tail', 'Annapurna'],
		    
		    //add method 
		    printWithDash: function() {
		      setTimeout(() => console.log(this.mountains.join(' - ')), 3000);
		    }
		    
		  };
		  
		  nepal.printWithDash();
		  ```
- The Spread `(...)` Operator
  collapsed:: true
	- The `...` operator expands an iterable (like an array) into more elements
		- ``` javascript
		  const q1 = ["Jan","Feb","Mar"];
		  const q2 = ["Apr","May","Jun"];
		  const q3 = ["Jul","Aug","Sep"];
		  const q4 = ["Oct","Nov","Dec"];
		  
		  const year = [...q1, ...q2, ...q3, ...q4];
		  
		  -----------------------------------------------------------
		  Jan, Feb, Mar, Apr, May, Jun, Jul, Aug, Sep, Oct, Nov, Dec
		  -----------------------------------------------------------
		  ```
	- The `...` operator can be used to expand an iterable into more arguments for function calls
		- ``` javascript
		  const numbers = [23, 55, 21, 87, 56];
		  let maxValue = Math.max(...numbers); // returns highest number
		  
		  
		  ----
		   87
		  ----
		  
		  ```
- The For/Of Loop
  collapsed:: true
	- The `for/of` statement loops through the values of an iterable object
	- `for/of` lets you loop over data structures such as:
		- `Arrays`, `Strings`, `Maps`, `NodeLists`, and more
	- The `for/of` loop has the following syntax:
		- ``` javascript
		  for (variable of iterable) {
		  	// code block to be executed
		  }
		  ```
		- variable - for every iteration the value of the next property is assigned to the variable
			- declared with `const`, `let`, or `var`
		- Iterable - object with iterable properties
- Looping over Arrays and Strings
	- Looping over an Array
		- ``` javascript
		  const cars = ['BMW', 'Volvo', 'Mini'];
		  let text = '';
		  
		  for (let x of cars) {
		    text += x + '';
		  }
		  
		  -----------------------
		  BMW
		  Volvo
		  Mini
		  -----------------------
		  ```
	- Looping over a String
		- ``` javascript
		  let language = "JavaScript";
		  let text = "";
		  for (let x of language) {
		  	text += x + "";
		  }
		  
		  ----------------------
		  J
		  a
		  v
		  a
		  S
		  c
		  r
		  i
		  p
		  t
		  ----------------------
		  ```
- JavaScript Maps
	- Being able to use an Object as a key is an important Map feature
		- a Map holds key-value pairs where the keys can be any datatype
		- A map rembers the original insertion order of the keys
		- A map has a property that represents the size of the map
-