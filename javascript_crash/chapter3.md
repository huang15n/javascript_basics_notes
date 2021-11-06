


# Functions & Methods


functions allow us to define a block of code which we can call and execute whenever we want. you could think of functions as a bit like a box with some code inside it that does a particular thing 


we define it once and run it multiple times whenever we want 

we could also pass values into functions so that the function could take those values and do something, so this is the power of funcitons to create little blocks of code that become reusable 

## function declaration & expression 


```javascript 

function functionName(){
	statements;
}

// to call the function , invoking the function
functionName();

```



```javascript 

function functionName(){
	console.log("hello there");
}

// to call the function , invoking the function
functionName();
functionName();
functionName();

```

## function expression 

if I do not want to overwrite the function later on, I am storing this in a constant 
basically, any time you get a variable and set equal to something, wehther it is a function or a string that is known as an expression, we should always have semicolons 


```javascript 

const myFunction = function (){
	statements;
};

// to call the function , invoking the function
functionName();
```



```javascript 
const functionName = function(){
   console.log("this is a function expression");
};


functionName();


```


most of the time, these are two different eways of creating functions, they behave the same way 

#### but there is a subtle difference when it comes to something called hoisting in JavaScript, hoisting is a term that loosely describes how our functions are hoisted on the top of a file before the rest of our JavaScript actually runs 
so what that means is that we could potentially declare a function using a function declaration down at the botton of the file and we could still run these things over here. it just seems jumbled up and it does not enforce a good code in practice when you are declaring things 


```javascript 

//function hoisting, define the function below its invocation 

functionName();
functionName();
functionName();
function functionName(){
	console.log("hello there");
}



```
javascript hoists function essentially at the top of the file. that is a gross oversimplication, but essentially this is what the effect is 

#### javascript does not hoisting function expression, only function declaration. you should declare something first and then use it to keep a logical flow to your code. and if you do not do that, you could end up with a mismatch of functions and calls all over the place 


```javascript 

//function hoisting, define the function above its invocation 
const functionName = function (){
	console.log("hello there");
}

functionName();
functionName();
functionName();

```


## Arguments & Parameters

we first declared what we want to receive some kind of value inside the function and do that inside the paretheses 

```javascript 

const functionName = function(argument){
    statement;
}


functionName(parameter);

```

it is taken this value and assigned it to the local variable. arguments and parameters are interchangeable and a lot of people get them mixed up 





```javascript 

const functionName = function(argument){
    console.log(`we are gonna call this function ${argument}`);
}
functionName('parameter');


const functionName1 = function(argument1, argument2){
    console.log(`we are gonna call this function ${argument1} and ${argument2}`);
}
functionName1('parameter','parameter');


```


to combat this just in case a function is invoked without passing anything in, what we could do is give these parameters some default values 



```javascript 

const functionName = function(argument=value,arguemnt2=value){
    statement;
}


functionName();

```
but at the moment that i pass in some arguments, these value are going to overwrite default values 




```javascript 

const functionName = function(argument1='value1',argument2='value2'){
    console.log(argument1,argument2);
}


functionName();

functionName('value3');

```


## return values 


we might want to instad have the function return of values to us, we do not want to log each thing in the function 


instead, what we want to do is receive the area of value back so that we can do something with it later 



```javascript 

const functionName = function(argument){
   return value;
}


const result = functionName(parameter);

```

this set equal to this new constant which has global scope 


```javascript 

const functionName = function(argument){
   return argument + 1;
}


const result = functionName(2);
console.log(result);

```

the beneift of this is that we can now take the result and do something with it 

so we are able to reuse a value that a function brings back to us 


## arrow functions 

if there is not parameters, we still annot take brackets away because that would not be an arraow function 

```javascript 

const functionName = (parameters) => {
 statement;
 return value;
};

const functionName = () => {
 statement;
};

```


this is an arrow function version of this regular function and it is just a bit shorter 

```javascript 
const functionName = (parameter) => {
	return parameter * 2;
};

functionName(4);
```


### single arrow function
even if we do not write out a return keyword, it still returns a value:


```javascript 


const functionName = parameter => one_return_statement;

```


it only works when we have one simple return statemetn !!! we use arrow functions as we go forward 


```javascript 


const functionName = parameter =>  parameter * 2 ;

console.log(functionName(2));

```


if we do not have parameters 

```javascript 


const functionName = () => one_return_statement;

```



```javascript 


const functionName = () =>  'something' ;

console.log(functionName());

```


## functions versus methods 

you are going to be quite clued up as to what a function is 

I want you to cast your mind back to methods on data types 

functions and methods are kind synonomous to them because they kinda do the same thing 

if we just have a regular function or an arrow function and in fact 


```javascript
const functionName = () => `hello`;
let result = functionName(); 

```
when we invoke this funciton, we invoke the name and paretheses 

when we use a method, the method is invoked using dot notation 

the only difference in how we are calling them is that we are calling a method on the back of something using dot notation 




## Foreach method & callbacks 

### callback function 

```javascript 

const functionName = (callbackFunction) => {
	let variable = value;
	callbackFunction(variable);
};

functionName(function(variable){
	console.log(variable)

	});


```



when we call the callback function, what we are doing is calling that callback function and passing that value as an argument 



```javascript 

const functionName = (callbackFunction) => {
	let variable = 50;
	callbackFunction(variable);
};

functionName(function(variable){
	console.log(variable)

	});


```
that callback function will proably be caleld and maybe pass value, which we can take in 


that is the general prmsise 


we convert this into an arrow function 



```javascript 

const regularFunction = (callBackFunction) => {
    let variable = 100;
	return callBackFunction(variable);

};

let result = regularFunction( parameter => parameter * 2 );

console.log(result);


```

### forEach() method 



each method expects an argument in a call function 

```javacript 

let array1 = ["eddie", "jack", "ron", "rick"];

array1.forEach((item,index) => { console.log(index, item)});

```


we essentially put this arow function into foreach method is doing exactly the same thing 



```javacript 

let array1 = ["eddie", "jack", "ron", "rick"];

const functionName = (item,index) => { console.log(index, item);
};


array1.forEach(functionName);

```


we use callback function directly especially when they are just small functions 

but sometimes if we have a large funciton, then we are going to externalize them , create them somewhere else, and then pass them in as a callback function 


hopefully you know callback function is just one function passed into another function or another method as an argument 


remember there is no way to modify the value of the array through regular return statement in the forEach loop 

```javascript 

const funcA = (variable) => {

return variable + 1;
}
a.forEach(funcA);

const funcA = (variable) => {

console.log(`${variable+1}`);
}

a.forEach(funcA);

```

the callback function is passed the element, the index, and the array itself 


```javascript 
const result = document.querySelector(".something");
const array = [1,2,3,4];
let html = '';
array.forEach((each_element) => {
html += `<li>${each_element} hahahaha</li>`;
})
result.innerHTML = html;
"<li>1 hahahaha</li><li>2 hahahaha</li><li>3 hahahaha</li><li>4 hahahaha</li>"

```




