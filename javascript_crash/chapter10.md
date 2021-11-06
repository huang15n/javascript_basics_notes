

# Object Oriented Programming 


an object in js is very much like an object in real life, it can have property and methods 

```javascript 
const objectName = {
name1: 'value1',
name2: 'value2',
name3: 'value3'

}
objectList.forEach((element) => {
console.log(element.name1);
})

const anObject = {
variable : 100,
functionName : () => {
console.log("this is a function");
}

}
```
```python
>>> dictionary = {  
... 'name' : 'value',
... 'function' : lambda x : x * 2,
... }
>>> dictionary['function']
<function <lambda> at 0x10d2d2af0>
>>> dictionary['function'](2)
4


```

array is a type of object in javascript and this array will have a length property and also methods 


but just know for now that any methods a particular object has access to are listed inside its property 

```javascript 
array = ['a','b'];
2) ['a', 'b']0: "a"1: "b"length: 2[[Prototype]]: Array(0)

```

know for now that any methods that a particular object has access to are listed inside its Prototype property 


another way to create an Array is to use array constructor

```javascript 
const array = new Array(1,2,3,4,5,5)

```
whenever you see a new keyword there we know we are creating some kind of object, this is a constructor function and that is going to make that kind of object 

square brakcets are easiser to use 


we can create an empty object 

```javascript
const emptyObject = {}

```

it does not have any properties because we did not give it any properties 


we can also make an object litereal using the object constructor 


```javascript 
const emptyObject = new Object();

```


we use the Object constructor to do this, this constructs a new Object 

in general, you might hear the phrase everything in js is object, that is not technically true because we see many data types in js which are not object, string, numbers, booleans, they do not fall into object types. they are not objects 




what happens is that when we try to access a property, javascript takes that primitive type value and and wrap it temporarily in a wrapper object, and that object will be the thing that actually has the methods and properties on it has that has been used so it wraps primitive values into a wrapper object and then uses different properties or methods on the object once we have done that method or use that property, javascript unwraps the primitive values from that object and give it back to us and it does all of this under the hood without us seeing it 



let's create an object which wraps a string, which is a primitive value and this thing has all the properties and methods 

```javascript 
const stringObject = new String("object is here");

```
then when we are done ,it wraps them again and give back the value and we can do the same thing 


we also know that though not everything in javascript is an object, pretty much everything can behave like an object. this knowledge will be a good foundation for you to understand objects 


we will do a quick object recap and why this is a good way to create an object when we are creating the objects of hte same kind of data 

```javascript 
const newObject1 = {

username: 'Eddie',
age : 18,
functionLog(){
console.log("you are logged in");

}

}


const newObject2 = {

username: 'Jason',
age : 32,
functionLog(){
console.log("you are logged in");

}

}

```

this is not making our code maintainable, we are rewriting a lot of the same code, we are repeating ourselves, if we want to create a lot of user objects, it get even more messages

```javascript 
const userOne = new User("name", 18 );

```


and all it does for us is to create a new object and it uses this constructor to create that object with all of those methods and properties, it is going to help us to easily create objects for different types of data 

## Classes 

we know object dot notion is not always the best to create different objects by copying and pasting these objects over and object 

we can do this in a couple of different ways 


one way is to use prototype model direclty, which is the original way we do this in javascript, but with release of ES6, which is a newever javascript specification, we can now do this using the class keyword as well 

now classes are just a bit of syntactic sugar, meaning that under the hood it still uses the same original prototype model that we used before classes came about to do this kind of thing 

but classes aimed to make our code a little bit cleaner and easiser to understand the inner happening under the hood 

classes are just syntatic sugar to make objects a little bit easiser, but to begin with, gently introduce the idea of classes until we get a basic grasp of what class is and object oriented programming is all about and then dive deeper into the prototype model under the hood 


#### a class is like a blueprint for an object(it describes how one should be made), it describes how to create one with all of its base properties and functionality. that is not to say that everyone should be completely identical 
in java script we use a class to describe the type of object istead of a blueprint. once we have a class defined and stored somewhere, we can then call upon it from anywhere in our application code to create a new use object 


```javacript 
class SomeClass{

}

```


### Class Constructor 
now we need to create a constructor function 

a constructor function is the thing that actually constructs our object and sets the properties on it 

```javacript 
class SomeClass{

}

const classOne = new SomeClass();

```




what this does is call the constructor function inside this class to set all the proeprties on that new object 



```javacript 
class SomeClass{
	constructor(){

	}

}

const classOne = new SomeClass();

```
this constructor() name is important, this is the same shorthand syntax for a function that we used inside objects 


so inside this constructor, this is where we set up properties on the object 


whenever we use the 'new' keyword 
1. it creates a new empty object {}
2. it binds the value of this to the new empty object 
3. it calls the construction to build the object 


then we use 'this' keyword now to refer to this object we just creating 


```javascript 

class SomeClass{
	constructor(){
		this.instanceVariable = 'value';
	}
}

const object1 = new SomeClass();
const object2 = new SomeClass();
```
these objects are identical, it would be nice if instead we could pass in a value into this user constructor when we call it right here


```javascript 

class SomeClass{
	constructor(parameter1,parameter2){
		this.instanceVariable = parameter1;
	}
}

const object1 = new SomeClass('value1','value2');
const object2 = new SomeClass('value3','value4');
```

now if we launch these out, we should see these properties in the objects 
so now we are creating unique objects using this constructor and passing in values.

##### and once again, whenever we create an object like this, we say that we are creating an instance of that class. the instance refers to the individual object that we are actually creating using the class 


```javascript 

class BaseClass{
	constructor(parameter1){
		this.variable1 = parameter1;
	}
	method1(){
		console.log(`$this.variable1}`);
		return this;
	}
}

```

### Class Methods & Method chaining 

when we create our new user objects, we are attaching properties to those objects 

it would be nice to give different obejcts methods so it has access to these methods 

notice this is a regular function using shorthand notation and arrow functions do nto buy the value to the "this " keyword when they called 

##### if we use an arrow function here, this is the function itself would refer to the window object!!!
instead by using a regular shorthand function like this, that this keyword will create object instance. that is the new object that we create when we say new. 

```javascript 

 

class SomeClass{
	constructor(parameter1){
		this.instanceVariable = parameter1;
	}
    method1(){

    console.log(this.instanceVariable);
console.log("this is method 1");
    }
    method2(){
 console.log("this is method 2");
    }
}

const object1 = new SomeClass('value1');
object1.method1();
object1.method2();

```
now we are essentially encapsulating everythign means to be inside this class, if we expand this, we have seen different methods have been attached to the user, and the same goes for this one up here 

if we want to run two consecutive methods on a single obejct, we'd have to run them in separate statements 

it would be nice if we could chain these together so we can do some one line in a single statement rather than having to go onto a second statement. now this does not work because those two methods are not returning any values. when a method does not explcitly return a value automatically, javascript assigns the return value to be undefined. so because this is now undefined, when return it, something undefined in the return statement which is obviously not going to work 

we will see how to combat this 

```javascript 
class SomeClass{
	constructor(parameter1){
		this.instanceVariable = parameter1;
   this.counter = 0;
	}
    method1(){

    console.log(`${this.instanceVariable}`);
console.log("this is method 1");
    }
   method2(){
 console.log(`${this.instanceVariable} has ${this.counter}`);
this.counter ++;

   } 
 

}

const object1 = new SomeClass('value1');
object1.method1();
object1.method2();
object1.method2();
const object2 = new SomeClass('value2');
object2.method2();
 

```



so we need to return a value in order for this to work 

what we want to do is return the value are attached to the obejct instance 
what we return is the object instance 'this'


```javascript 
class SomeClass{
	constructor(parameter1){
		this.instanceVariable = parameter1;
   this.counter = 0;
	}
    method1(){

    console.log(`${this.instanceVariable}`);
console.log("this is method 1");
return this;
    }
   method2(){
 console.log(`${this.instanceVariable} has ${this.counter}`);
this.counter ++;
return this;

   } 
 

}

const object1 = new SomeClass('value1');
object1.method1().method1();
object1.method2().method2();



class NewClass{
constructor(parameter){
this.variable = parameter;

}
method(){
console.log(`${this.variable}`);
this.variable ++;
return this;
}




}
let someObject = new NewClass(1);
someObject.method().method().method();

```


this method chaining now works because we are explicitly returning the instance at the end of each one of these methods 


now you do not have to do this if you do not want your methods to be changeable 

## Class Inheritance 

hopefully now you are getting the hang of what a class is and how we can use them to create new types of objects 

class inheritance otherwise known as subclasses 

we have all of the same properties and methods that others would have so it inherits all the stuff in the class. we can also define the extra methods or properties on it, which only it will have and we utimately have 


```javascript 

class BaseClass{
	constructor(parameter1){
		this.variable1 = parameter1;
	}
	method1(){
		this.variable1 ++;
		console.log(`${this.variable1}`);
		return this;
	}
}

class SubClass extends BaseClass{

}

const subObject = new SubClass(0);

subObject.method1().method1().method1();


```

it will call constructor of that, now we can define methods over here 




```javascript 
class BaseClass{
	constructor(username){
		this.username = username;
	}

}

class SubClass extends BaseClass{
	method1(user){
		 users = users.filter((u => {return u.username !== user.username;}))
	}

}





const subObject1 = new SubClass("eddie");
const subObject2 = new SubClass("jason");
const subObject3 = new SubClass("bin");
let users = [subObject1, subObject2, subObject3]
subObject3.method1(subObject2);

```



lets neat this, it has all the properties that it has brought 


## super() 



we have seen now how to create a subclass which inherits from or extends another class. so it inherits all of these properties and all of these methods but also we have to define extra methods which subclass will have 

```javascript 
// forgot to extend and new 
class SuperClass{

constructor(parameter1,parameter2){
this.variable1 = parameter1;
this.variable2 = parameter2;

}
method1(){
console.log(`${this.variable1}`);
console.log(`${this.variable2}`);
}

}


class SubClass{
constructor(parameter1,parameter2,parameter3){
super(parameter1,parameter2);
this.variable3 = parameter3;

}
method2(){
super.method1();
console.log(`${this.variable3}`);

}

}


const subObject1 = SubClass("Eddie","Wong","19");


```

what if we want to create properties only subclasses have. to use super, you must use subclass to extend a superclass and new it!!

to add any other properties, we have to call super


```javascript 
class SuperClass{

constructor(parameter1,parameter2){
this.variable1 = parameter1;
this.variable2 = parameter2;

}
method1(){
console.log(`${this.variable1}`);
console.log(`${this.variable2}`);
}

}


class SubClass extends SuperClass{
constructor(parameter1,parameter2,parameter3){
super(parameter1,parameter2);
this.variable3 = parameter3;

}
method2(){
super.method1();
console.log(`${this.variable3}`);

}

}


const subObject1 = new SubClass("Eddie","Wong","19");

```

## Constructor under the hood 

classes in javascript is syntatic sugar because javascript does not actually ahve classes built into it 
instead, it uses a prototype model to implement the same kind of behavior 

now, the class keyword was just introduced more recently into the lnaguage as a way to emulate the object oriented programming 


but the class syntax here is just a think layer of abstraction over the prototype model, which is being used under the hood to create these objects when we write classes 


the constructor is responsible for setting up the object, applying the properties to it and setting the values of those variables 


now if we do not use constructors to create objects, we still need constructors to do this to set up new objects 


and it is the old way that we created objects using functions before the class syntax came 

```javascript 

function ClassSimulator(parameter1,parameter2){
	this.variable1 = parameter1;
	this.variable2=  parameter2;
	this.method = function(){
		console.log(`${this.variable1}`);
		console.log(`${this.variable2}`);
	}
}
let object1 = new ClassSimulator(12,23)

```
we can do this because this refers to the obejct instane inside this constructor 


but there is a better way to add methods to our objects, not inside the constructor, and that is via prototype 


## Prototype Model

we could create a constructive function and call then by saying new SuperClass() and passing different values, then we attach values as properties 


but defining methods inside the constructor like this is not the best way to add them. instead, it is better to add them onto the prototype 

if we create any kind of object in javascript, then all of the methods that we can use on that object will be inside our prototype property. and no matter what object we use, the methods should be inside this prototype property 

javascript automatically proxies all of the methods that we can use up onto the root level of the objects 

```javascript 
// this is not how we do it 

const num = [1,2,3,4,5]
num.__proto__.filter((item) => {
return item > 2;
})

```

when we define methods in a class, javascript automatically took those methods and added them onto the __proto__ properties 


### Prototypes 
1. every object in javascript has a prototype 
2. prototypes contain all the methods for that object type 

even every custom object type that we create have a prototype 


Array prototype share exactly the same methods: sort(), filter() etc ... so all the array methods are stored once in the central palce on the array prototype. so the proto property for an array object will point to the array prototype 

so this approach of storing the methods on a prototype instead of we create every object has two main benefit
1. it will be more efficient since we are storing them in one single place once 
2. it will help us with prototype inheritance 


#### remember it must new the object otherwise it will report the error:
VM4578:1 Uncaught TypeError: Cannot read properties of undefined (reading 'method')
    at <anonymous>:1:7


```javascript 
ClassName.prototype.method = function (){
	
}
```

```javacript 

function ClassSimulator(parameter1,parameter2){
	this.variable1 = parameter1;
	this.variable2=  parameter2;
	this.method = function(){
		console.log(`${this.variable1}`);
		console.log(`${this.variable2}`);
	}
}

ClassSimulator.prototype.method = function(){
		console.log(`${this.variable1}`);
		console.log(`${this.variable2}`);
	}
ClassSimulator.prototype.method2 = function() {
console.log("this is method 2");

}
ƒ (){
		console.log(`${this.variable1}`);
		console.log(`${this.variable2}`);
	}
```

when we use class syntax, the syntax just looks different on the surface. and it aimed to make this kind of thigns easiser ,especially to programmer coming from different languages 

```javascript 
function User(username, email){
this.username = username;
this.email = email;

}
User.prototype.method = function(){

console.log(`${this.username}`);

}

```
before the class keyword came about in javascript, this is how we had to emulate the idea of classes 



### prototypal inheritance 

```javascript 

function SuperClass(parameter1, parameter2){
	this.variable1 = parameter1;
	this.variable2 = parameter2;
}

SuperClass.prototype.method1 = function(){
	console.log(`${this.variabel1}`);
 
}
SuperClass.prototype.method2 = function(){
	console.log(`${this.variabel2}`);
}


function SubClass(parameter1, prameter2){
	SuperClass.call(this,parameter1,this.parameter2);

}


/*subObject.method2();
VM4910:1 Uncaught TypeError: subObject.method2 is not a function
    at <anonymous>:1:11
    */


```

but subclass at the minute they do not have any methods 

it has its own prototype, so essentially what we need to do is copy the Superclass prototype to the Subclass prototype 

```javascript 
SubClass.prototype = Object.create(Superclass.prototype);
SubClass.prototype.method1 = function(){

}
let object1 = new SubClass(1,2);

```

we are two levels deep in Prototype 

so that prototype inheritace, the inner workings of how classes are made and extended in javascript 

a lot of the time you won't be using this type of work and you might just opt to use javascript class instead, but i think understadning this concept of what is actually happening when we create classes is very useful especially when it comes to writing more complex specifications evevn working with all the developers code 

### Built in Objects 

we can see them in a new light because we understand what the prototype model is and what that little __proto__ property is 

we are storing all of these methods on the Array prototype inheriting methods from the object prototype, an if we expand that, we can see all different methods we inherit from the object prototype 
every object type in javascript is going to inherit from object. this is like the base type with basic methods attached to its prototype 

ultimately everything inherits from object and along the way this one as inherited from quite a few different thigns 













































