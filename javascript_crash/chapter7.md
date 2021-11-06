
# Chapter7 The Array Methods

we have seen the forEach method which we can use in arrays to fire a callback function 



## cheatsheet 

filter: 
```javascript 
list_elements.filter((each) => {

return each > 2;
})

```


map: 
```javascript 

list_dict.map((each) => {
return {name1: each.name1 * 2, name2: each.name2 * 3}

})

```

reduce():  

```javascript 
const list = [1,2,3,4,5,6,]
undefined
list.reduce((accumulator,current) => {

return accumulator + current;


},0)


```

find():

```javascript 

list.find((each) => {
return each > 3;

}) 

```


sort() 

```javascript 

const list = [3,7,1,5,4,]
list.sort()

const list = [3,7,1,5,4,]
list.sort((a,b) => {
return a - b;

})
(5) [1, 3, 4, 5, 7]
const list = [3,7,1,5,4,]
list.sort((a,b) => {
return b - a;

})
(5) [7, 5, 4, 3, 1]

```

chained method: 

```javascript 
const list = [3,7,1,5,4,]
list.filter((elem) => { return elem > 3;} ).map((elem) => {return elem *2;})

```



## filter((element) => {callback_function}) method 


filter method iterates an array and it performs a check on each item in the array inside a callback function. and if that check passes, then it is going to keep the item inside the filtered array 

```javascript 

const array = [213,123,1123,2131,412];
array.filter(()=>{return true;});
const array = [213,123,1123,2131,412];
array.filter(()=>{return false;});

const array = [213,123,1123,2131,412];
array.filter((elem)=>{return elem < 1000;});

```


if this is not correct, we are gonna filter that out. if it returns true, we are gonna keep the item in the array 


come down underneath and create some data 

```javascript 
const dictionary = [{name1:'value1',flag:true},
{name2:'value2',flag:false},
{name3:'value3',flag:true},
{name4:'value4',flag:true}
]
const true_results = dictionary.filter(element => {return element.flag;} );
console.log(true_results);

```



## map((element) => {callback_function}) method 


the map method takes an array and then it maps that into a completely new array. iterate an array and it returns an updated value for each item in the array and it pushes that updated value into a new array 


```javascript 

const array = [213,123,1123,2131,412];
array.map((element) => {return element * 2; } );
```



we return a new object: 

```javascript 
const dictionary = [{name:'value1',value:100},
{name:'value2',value:200},
{name:'value3',value:300},
{name:'value4',value:400}
]
dictionary.map((element) => {return {name:element.name,value:element.value*2}});

```




## array.reduce((accumulator,current) => {callback_function}) method 
the reduce method works a bit differently than map and filter methods in method it does not erturn necessarily a new array. instead it returns a new value. any value that you want based on the values in the array that we itearte over 

so for each item in this array were firing this callback function and each time around we have access to this accumulator and the value of this accumulator is remember through teach item as we fire 


for each accumulation, we can edit that value 

```javascript 

const array = [1,2,3,4,5,6];
let result = array.reduce((accumulator,current) => {

if(current < 4){
accumulator += current;
}
return accumulator;
},0);
console.log(result);


const dictionary = [{name:'value1',value:100},
{name:'value2',value:200},
{name:'value3',value:300},
{name:'value4',value:400}
]
dictionary.reduce((accumulator,current) => {

if(current.name === 'value1' ||  current.name === 'value2'){
  accumulator += current.value;
}

return accumulator;
},0);
```


## find((element) => {return condition}) method

what the find method is going to do is iterate an array and find a callback function for each item. as soon as it passes a certain condition. it will return that value right there and it won't carry on through the rest of the values in the array 


```javascript 

const array = [10,20,30,40,50,60,70,80];
const firstOccurrence = array.find((element) => {return element > 30;})
console.log(firstOccurrence);
```



## sort() method 

in javascript, a lot of the time when we have some kind of array of data, we might want to sort that data or rearrange it in a particular way 


the sort() method has a simple algorithm which automatically sort strings alphabetically 


this is destructive because it changes the original array 


```javascript 
const array = ['b','c','a','d'];
array.sort();

```



we cannot overcome this 


```javascript 

const array = [10,20,30,4,40,5,50];
array.sort();

```

## reverse() 
this reverse the order and turn sort() around make 180 degrees 

```javascript 
const array = ['b','c','a','d'];
array.reverse();

```


dictionary.sort() is not going to work, the inbuilt sorting array algorithm won't work because it does not automatically know what to sort by, for more complex sorting like this we have to provide a function as an argument to sort 


```javascript 

const dictionary = [{name:'value4',value:300},
{name:'value2',value:200},
{name:'value3',value:100},
{name:'value1',value:500}
]
dictionary.sort((a,b) => {
if(a.value < b.value){
   return -1;
}else if(a.value > b.value){
  return 1;
}else{
  return 0;
}

});

``` 


this does exactly the same thing, because if that is greater than, we will get a positive number 

```javascript 

const dictionary = [{name:'value4',value:300},
{name:'value2',value:200},
{name:'value3',value:100},
{name:'value1',value:500}
]
dictionary.sort((a,b) => {return a.value - b.value;});
```


to reverse() it 

```javascript 
const dictionary = [{name:'value4',value:300},
{name:'value2',value:200},
{name:'value3',value:100},
{name:'value1',value:500}
]
dictionary.sort((a,b) => {return b.value - a.value;});

```


## chaining array method 

```javascript 

const dictionary = [{name:'value4',value:30},
{name:'value2',value:2},
{name:'value3',value:10},
{name:'value1',value:50},
{name:'value5',value:3},
]
const filtered = dictionary.filter((element) => {return element.value < 30} );
const result = filtered.map((element) => { console.log(`${element.name} | ${element.value}`);});

```

when we do method chaining, we go to next line and idents just so it is easy to read like this 


```javascript 
const dictionary = [{name:'value4',value:30},
{name:'value2',value:2},
{name:'value3',value:10},
{name:'value1',value:50},
{name:'value5',value:3},
]
dictionary.filter((element) => {return element.value < 30;})
           .map((element) => {console.log(`${element.name} " ${element.value}`);});

```


