

## ES6 features 

this modern does not naturally fit in the rest of the content 


### Rest Parameter 

this allows us to bundle up arguments in a single array parameter 


```javascript 
const result = (...parameter) =>{

}


```

the rest parameter looks like ...parameter, and what that does is take all the arguments that we put into the functoiin when we call it 

and it bundles them up into a single array parameter 

that is really useful when we do nto know how many diffferent aruments we are going to pass in and we want to bundle them up into a single array 


```javascript 
const restResult = (...parameters) => {

console.log(parameters);
parameters.forEach((item) =>{
console.log(item);

})



}

```


that is rest parameters, three dots in front of whatever you wanto call a parameter, which will be an array of arguments 


## spread with arrays 

put each element of one array into another array 
this will unpack you, spread an array to another 

```javascript 
const array1 = [1,2,3,4];
const array2 = [5,6,...array1]
console.log(array2);
```
## spread with objects 
objects are reference type and all this does is create a new pointer, which is pointing to the same object so this odes make a clone ofthe object 


I am just copying and make a new pointer and making a brand new object 


deeply copy of an object 


```javascript 
const dictionaryObject1 = {
'name': 'Eddie',
'age':20,

}
const dictionaryObject2 = {...dictionaryObject1}


```


so now I am actually making a full copy of the object, not just the copy of the pointer 


## Sets 


sets are new object of object category, which means there are eferene types and allow us to store a list of any kind of unique values 


by that I mean in any given set, a certain value can be present once 


so these are a bit like an array, but they do not allow duplicates whereas an array would allow duplicates 



there is no shorthand way of creating a set 


```javascript 
const setVariable = new Set();
const setVariable = new Set([array]);
let newSet = new Set([1,2,3,4,1,2,3,4,5]);
let array1 = [1,2,3,4,1,2,3,4]
setVariable = new Set(...array1)
/*

VM6005:2 Uncaught TypeError: number 1 is not iterable (cannot read property Symbol(Symbol.iterator))
    at new Set (<anonymous>)
    at <anonymous>:2:15
*/
let array1 = [1,2,3,4,1,2,3,4]
setVariable = new Set([...array1])
```


there was an oversimplication to say that  that only allows unique values 



convert a set to an array 

```javascript 

const array = [... new Set(namesOfArray)]

let array1 = [1,2,3,4,1,2,3,4]
let array2 = [new Set([...array1])]

```

we can also put a set of list of dictionaries
```javascript 

setVariable = new Set([
    {'name1':'value1',
 'name2':'value2',
'name3':'value3'}

])

```

###  set methods 
.add(value);
.delete(value); if it has the value, it returns true , false otherwise 
.clear(); which clears the set 



```javascript 
let setVariable = new Set([1,2,3,4,5,1,2,3,4])
setVariable.add(10).add(15);
setVariable.delete(3)
```


## Symbols 
we use the Symbol() to create a new symbol object which is reating a symbol and a symbol is a primitive type 


symbols can be used as keys or property names in objects 


```javascript 
const symbolOne = Symbol();
const symbolTwo = Symbol();
console.log(symbolOne,symbolTwo, typeof symbolOne);
console.log(symbolOne === symbolTwo);

```



we cannot give an object this way to properties which are essentially the same now with symbols 
```javascript 
let dictionary = {

}
dictionary['name'] = 'value';
```
with objects, we cannot overwrite the properties 
with symbols, this is not the matter 

```javascript 
dictionary[symbolOne] = 'value';
'value'
dictionary[symbolTwo] = 'value';
'value'

```

when we add keys to these objects, it does not matter that they look identical because technically they are nto the same thing  because no symbol is the same 



