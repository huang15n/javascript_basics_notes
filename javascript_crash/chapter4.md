

# Object Literals 

## overview 

objects in real life have properties & method(things they can do)


the way we create an object using object literal notation is by using curly braces, each object we will have key value pair 


```javascript 

let object = {
   name1 : 'value1',
   name2 : 'value2',
};
console.log(object);


``` 


now this way of formatting where each key value pair of each property is on a new line is just for readability 

two ways to access the property 
1 .dot notation 
2 [] square bracket in string format

```javascript 

let object = {
   name1 : 'value1',
   name2 : 'value2',
};
console.log(object);
console.log(object.name1);
console.log(object.name2);

console.log(object);
console.log(object["name1"]);
console.log(object["name2"]);

object.name1 = 'value3';
console.log(object.name1);
object['name2'] = 'value4';
console.log(object['name2']);

``` 


typeof() shows the type of the object, we should see object because it is of object type 




## object methods 
a regular function is not defined inside an object. a method is 

wrong example: 
```
objectSomething = {
key:'value',
function func(){
console.log("haha");
}


}

//Uncaught SyntaxError: Unexpected identifier

//wrong example 

objectSomething = {
key:'value',
func : function (){
console.log(key);
}


}
{key: "value", func: ƒ}
objectSomething.func();
//VM734:4 Uncaught ReferenceError: key is not defined
    at Object.func (<anonymous>:4:13)
    at <anonymous>:1:17


//right example 
objectSomething = {
key:'value',
func : function (){
console.log("haha");
}
objectSomething.func();


```

```javascript 

let object = {
   name1 : 'value1',
   name2 : 'value2',
   method_name1 : function(){
   	console.log("hello");
   }
   /* you can not use it like this 
   function_name2: () => {console.log("world");};
   */
};

console.log(object.function_name1());


``` 



## this keyword 

this keyword is a context object, and it represents the context in which the current code is executed 

if we use this inside the root of the document, then it is going to refer to the global context, which is called window object 

when we call a method, javascript sets the value of this keyword to be the object 

```javascript 

let object = {
   name1 : 'value1',
   name2 : 'value2',
   // this will cause an error when you try to access it : VM73:6 Uncaught ReferenceError: name1 is not defined
    at Object.method_name1 (<anonymous>:6:17)
    at <anonymous>:13:20
   method_name1 : function(){
   	console.log(name1);
   }
   /* you can not use it like this 
   function_name2: () => {console.log("world");};
   */
};

console.log(object.method_name1());

```


if we use "this" keyword, it refers to the object. 


```javascript 

let object = {
   name1 : 'value1',
   name2 : 'value2',
   method_name1 : function(){
   	console.log(this.name1);
   	console.log(this.name2);

   	},
};

console.log(object.method_name1());

```

we can also use callback function inside the method 


when we use a normal function as a method and invoke that method, javascript sets the value of this method, javascript setes the value of this keyword to the object that method was used on 

therefore, we can use that this keyword to refer to the object itself when we use an arrow function here instead to create the method 
and in fact I'll just change this to be in our function

so parentheses an arrow, then the code block javascript now will not set the value of this keyword to be the object when this is an arrow function, when we use our functions, the value of this does not change from the value 

it was at the point in the code that the arrow function was invoked right here 

now in this case, it was called a point when the value of this is the global window object. so if we try to use this inside here when it is in our function, i will be the same value, the global window object and obviously we cannot use a property on the window object 

when we use it on an object, it just atkes what it currently is in the current context, which passes that into the function 


```javascript 

let object = {
   name1 : 'value1',
   name2 : 'value2',
   list_name : ['a is good','b is bad', 'c is awful', 'd is excellent'],
   method_name1 : function(){
    this.list_name.forEach(item =>{ console.log(item);
    })

   	},
};


object.method_name1();

```


##### so in order to use this inside a method to refer to the actual object that the method is on, we need to use a regular function and not an arrow function, and that is just to take away the function keyword and take away the colon and just have our parenthese directly after the name 


```javascript 

let object = {
   name1 : 'value1',
   name2 : 'value2',
   
   method_name1(){

   }
};
let obj = {
    name : 'value',
    method(param){
        console.log(param,this.name);
    }
}


object.method_name1();



```



## objects in array 
we can also store objects inside arrays. 

```javascript 

const objs =[
 {
    name : 'value',
    method(param){
        console.log(param,this.name);
    }
},{
    name : 'value',
    method(param){
        console.log(param,this.name);
    }
}
]

for(const item of objs){
    console.log(item);
}

for(const item of objs){
    console.log(item.method(1));
}

objs.forEach((obj) => {console.log(obj);} )

```


## math object 
javascript has a whole bunch of ready made objects built into the language which we can use out of the box, method objects are things bundled into it 


```javascript 
console.log(Math.PI);
console.log(Math.E);
console.log(Math.round(1.1));
console.log(Math.floor(1.1));
console.log(Math.ceil(1.1)); // represents the top
Math.trunc(1.1));

```


## primitive & reference types 

when we create a primitive value, that value is stored in a stack 

#### primitive types
- numbers
- strings 
- Booleans 
- null
- undefined 
- symbols 


when we create a reference type like an object literal or an array that is not stored on the stack. but on what is known as the heap, heap has more space available so we can holder bigger and more complex types like objects and arrays but it is a bit slower too 

it adds a pointer to that reference in the stack and then it unlocks this variable name to the pointer 
and it does have ramifications and it will affect the way that we code 





#### reference types 
- all type of objects 
- objec literals 
- arrays 
- functions 
- dates 
- etc 



when we make a copy of the primitive type, we make a copy of the stack 

when we try to make a copy of a reference type, we only make a copy of the pointer on the stack, which points to the same data on the heap 

```javascript 
const obj1 = {name1:'value', name2:'value2'};
const obj2 = obj1;


console.log(obj1,obj2);
obj1.name1 = 'value3';
console.log(obj1,obj2);


```
watch out for references type stores pointer in one with several places 




