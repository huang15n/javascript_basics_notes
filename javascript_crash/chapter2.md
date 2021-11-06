

# Chapter2 Control Flow 

sometimes we need to either make some kind of decision on what to do next or maybe execute a piece of code over and over, make a cycle through and check if certain condition is met 

either that be using a loop to repeat a section of code or to conditionally run a section of code based on a certain condition 






## For loop

at the end of the day, the job of a for loop is to loop through a portion of code over and over again, it is just a section of code we section off 



```javascript 

for(initialization; condition; update){

}



```

we do not add semicolon at the end of braces 


you may hear cylcing through the array as iteration, each iteration is one cycle through 


```javascript 

for(let i = 0; i < 10; i ++){
	console.log(i);
}


let array1 = ["hello", "world", "this is me"];

// we do not have to know the exact length when using this syntax 
for(let i = 0; i < array1.length; i++){
	console.log(`${array1[i]} !`);
}


```


## while loop 

it does exactly the same thing, they loop through some code a certain amount of times 


```javascript 

let counter = 0;

while(counter < number){
	statements;
}

```



```javascript 

let variable = 0;


while(variable < 10){
	console.log(`<h1>${variable}</h1>`);
	variable ++;
}




let array1 = ["hello", "world", "this is me"];

// we do not have to know the exact length when using this syntax
let i = 0; 
while(i < array1.length){
	console.log(`${array1[i]} !`);
	i++;
}


```


## Do while 

do while loop is just an exception of while loop, sometimes you just want to run the statement at least even this condition is not true 


```javascript 

do{
	statements;
}while(condition);

```

regardless of whether condition is true or false 


## if statement 

a condition check and if statement in paretheses what we want to evaluate 

```javascript 


if(conditional statement){
	
}
}


```

sometimes we might want to feedback some information if this code does not execute 


```javascript 


if(conditional statement){
	
}else if(condition statement){

}
}else{
	
}


```


## logical operator &&, ||, !  

| Operator      | Name         |
| ------------- | ------------ |
| !           | NOT !a return true if it is false or vice versa     |
| &&           | AND  a && b  returns true if both a and b are true; otherwise false   |
| ||           |   OR returns true if either a or b or both are true; otherwise false   |


we can get really amibtious 

```javascript 

if(a == b || a == c){ // or 
	statments;
}
}else{
	statments;
}

if(a == b && a == c){ // and 
	statments;
}
}else{
	statments;
}

if(!a){
	statments;
}



```

## switch statement


```javascript 

const label= "";

switch(label){
	case '1':
	statement;
	break;
	case '2':
	statement;
	break;
	default:
	statement;
	break;

}


```
note: swtich statements, you strict equality to check 






## break & continue 




```javacscript 

for(let i = 0; i < 1000, i++){
	console.log(i);
	if(i == 50){
		break;
	}
}


let j = 0;

while(j < 1000){
	console.log(j);
	if( j == 40){
		continue;
	}


	j++;
}


```



## Variable & Block scope 

globalScope means it can be accessed anywhere in the file if I want to use it 

```javascript 

let globalScope;


if(true){
	let localScope;
}

```


if we are giving something a local scope , eaning the scope of this variabel is only valid inside this code block!

```javascript 

let sameName;


if(true){
	let sameName;//only use this inside the scope
	if(true){
	let sameName; //only use this inside the scope
}

}

```

