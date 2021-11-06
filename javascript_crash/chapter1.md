
# Chapter1 Baiscs, Data Types, variables

## setup 

```html

<html lang="eng">

<head>

	<title> javascript </title>



</head>


<body>
	<h1> page title </h1>
<script type="text/javascript">
	alert('hello world!');
</script>

</body>
</html>

```


it is somehow nice to externalize that javascript and put it in a separate file, then just linked to that file from it 


most of time we will do:

```html

<html lang="eng">

<head>

	<title> javascript </title>



</head>


<body>
	<h1> page title </h1>
<script src = "xxxx.js">

</script>

</body>
</html>

```


```javascript 
alert("hello world");

```





in google chrome, open inspect and click on "Console" opens the javascript code, just play around with it and use building blocks to test our code. if you do not have chrome, shame on you. 


if we want to log something just say: 


```javascript
console.log(2);

```



## Variables, Constants & Comments 


let keyword 

```javascript 

let variable = value;
console.log(variable1,variable2);
```


```javascript 


let age = 10;
let year = 200;
console.log(age, year);

```


const keyword

```javascript 

const constant = value;
// you cannot override this value 
```


var keyword

before const and let, it works the same way but it is not modern javascript 

```javascript
var variable = 1;

console.log(variable);



```

we know what this wants to represent 

## comments 


```javascript 
// one line comment 

/*
multiline comments 
*/

```



## JavaScript Data Types 

it will come to you with nature 

| Tables        | Definition        |
| ------------- |:-------------:|  
| Number      |  Integer, Float |  
| String | "hello"     | 
| Boolean     |  true/false |  
| Null |   explicitly set a variable with no value    |  
| Undefined |  for variables that have not yet been defined      | 
| Object |  complex data structure, -- array, dates, literals, etc     | 
| Symbol |  used with objects       |


## Strings 

we use strings to store letters, numbers or other characters 


```javaScript

let stringVariable = "hello World";
console.log(stringVariable);

``` 

### String Concatenation 
we use a plus sign to concatenate one string to another string 

```javascript 
let str1 = "str1";
let str2 = "str2";
let str3 = str1 + str2;

```


### String indexing 
we can also extract a single characer from a string that we have stored using square bracket notation 

```javascript 
strVariable[number];

```


```javascript 
let str = "str here";
console.log(str[0]);

```


### String length 

```javascript 
strVariable.length;

```

```javascript 
let str = "str here";
console.log(str.length);
```

### String upper/lowercase 
```javascript 
strVariable.toUpperCase();
strVariable.toLowerCase();

```

note: these methods right here do not actually alter the variables themsleves, the original variable 


### String indexOf() 
find the index of one character inside the string 

```javascript 
let str = "hello";
console.log(str.indexOf('o'));

```

note methods are just functions that belong to a specific object or object type 


### String lastIndexOf()

find the instance of something at the end 
```javascript 
let str = "helloooooo";
console.log(str.lastIndexOf('o'));

```


### String slice(beginIndex, endIndex) 

and inside we put in two arguments. 

```javaScript 
let str = "helloooooo";
console.log(str.slice(1,3));

```


### String substr(beginIndex, length) 


substr is very much like a slice, but the two arguments represent something slightly different. the second argument is how many characters we want to go over 

```javaScript 
let str = "helloooooo";
console.log(str.substr(1,3));

```



### String replace(targetCharacter, FirstCharaterReplacedWithCharacter)

to replace the first character 

```javaScript 
let str = "helloooooo";
console.log(str.replace('o','i'));

```

### String replaceAll(targetCharacter, FirstCharaterReplacedWithCharacter)

```javascript
let str = "helloooooo";
console.log(str.replaceAll('o','i'));

```

### template string 

I want to take a sidestep and talk about a slight different version of a string, and that is a template string 


concatenation way: 

```javascript 
const str1 = '';
const str2 = '';
const str3 = '';

let result = 'one' + str1 + 'two' + str2 + 'three' + str3;

```
it just looks a bit messy and hard to maintain. the job of a template string is to allow us to inject variables directly into the string without coming out of it 


the standard way to create a template string is just like we create a normal string using tactics 

```javascript 
let result = `${variable1} xxx ${variable2}`;

```

when you have a lot of variables, it is definitely good to use template string, 


```javascript 

const str1 = 'str1';
const str2 = 'str2';
const str3 = 'str3';
let result = str1 + '|' + str2 + '|' + str3 + '|';
let result2 = `${str1}|${str2}|${str3}`
```


a good use case is to create html templates with that content embedded inside it and injecting this dynamic content 

```javascript 

let html = `
<h2> ${variable1} </h2>
<h2> ${variable2} </h2>
<h2> ${variable3} </h2>
`;

```





## Number 


shift our focus to numbers 

```javascript 
let variable1 = 1;
let variable2 = 1.1;
 

```


we can do all the typical math operations with numbers: +, -, *, /, **, %

| Operator      | Name                |
| ------------- | ------------------- |
| +             | addition  $a + $b   |
| -             | subtraction  $a-$b  |
| *             | multiplication $a*$b|
| /             | division $a / $b    |
| %             | modulus $a % $b     |



```javascript 
let number1 = 10;
let number2 = 20;
let result = number1 + number2; 
result = number1 - number2; 
result = number1 * number2; 
result = number1 / number2; 
result = number1 % number2; 

```

shorthand operation

| Operator      | Name         |
| ------------- | ------------ |
| +=            | $a += $b     |
| -=            | $a -= $b     |
| *=            |  $a *= $b    |
| /=            | $a /= $b     |
| %=            | $a %= $b     |
| .=            | $a .= $b     |

```javascript 

let number = 10;
number += 10;
number -= 10;
number *= 10;
number /= 10;
number %= 10;
```

similar operation like number += 1 or number -= 1 

```javascript 
let number = 1;
number += 1;
number -= 1;

```
note: if you do something wrong, you probably made some kind of error along the way that can not result in the number 


```javascript 
let number = 10;
console.log(3 * "hello");


```





## array 

array falls in the object data type 

array is used to store collections of things like strings and numbers using comma separate relate to each other 


```javascript 

let array = ['variable1','variable2','variable3'];

```


### array method join('delimiter');

```javascript 
let variable = strs.join('|');

```



```javascript 
let strs = ['hello','world','what','is','going',]
let result = strs.join(' ');
console.log(result);

```

### array method indexOf('')

```javascript 
let strs = ['hello','world','what','is','going',]
let result = strs.indexOf('is');
console.log(result);
```


### array method concat() 
join arrays together which pass through as an argument to this method 



```javascript 

let array1 = [1,2,3,4,5];
let array2 = [6,7,8,9,10];
let result = array1.concat(array2);
console.log(result);


```

### array pop() method 
we pop off the last element of the elemetn 

this method alteres the original value, which is called destructive method 
now we have taken it back off 

```javascript 

let array1 = [1,2,3,4,5];

console.log(array1.pop());

```

### array includes()

```javascript 
let array1 = [1,2,3,4,5];

console.log(array1.includes(1));


```


## Null & Undefined 
these are similar and they both represent lack of values 

the only difference is that null is an intentional lack of value, but undefined isn't 


undefined, because we have not given it a value yet 

```javascript 
let undefinedValue;
console.log(undefined,undefined + 3, `this value is ${undefinedValue}`);
//undefined NaN "this value is undefined"


```
Null is an intentional lack of value and by that I mean we explicitly say it 


```javascript 
let nullValue = null;

```

why would we ever really want to do this? we have a form on a websie which asks for title, when they select that, it has some values, if at some point the user goes through the rest of the form and then decides to clear the form, then reset it, we no longer to want to store that value, at that point we use the null as we go forward 




## Booleans & Comparison 

booleans represent true and false 


| Operator      | Name         |
| ------------- | ------------ |
| ==            | equals $a == $b     |
| ===            | identical $a=== $b     |
| !=            |  not equal $a != $b    |
| !==            | not identical $a !== $b     |
| >            |  greater than $a > $b     |
| <           |  less than $a < $b     |
| >=            |  greater than or equal to $a >= $b     |
| <=            |  less than or equal to $a <= $b     |




```javascript 

let array1 = [1,2,3,4,5];
console.log(array1.includes(2));
console.log(1 == 2);

```

if we compare strings 

```javascript 
console.log('shaun' == 'Shuan');
//false 
console.log('shaun' > 'christian');
//true, s comes before c 


```

### loose versus strict comparison 


== are known as abstract equality or loose equality which means that a value type is not considered when we perform the comparison, str is converted to a number 


```javascript 

1 == '1'
//true
1 != '1'
//false
1 != '2'
//true
1 != 2
//true
```

it is not always the most accurate way to check something 

=== is what we expected, so most of the time it is pretty strict comparison because it results in more predictable results and using it going forward 


```javascript 

1 === '1'
//false
1 !== '1'
true
1 !== '2'
// true 
1 !== 2
//true
```
## type conversion Number(), String(), Boolean()

Now I'd like to touch on someting called type conversion and that basically means turning one data to another data type 



```javascript 
// turn str to a number 

let str1 = '10';
str1 = Number(str1);
console.log(str1);

// we cannot convert


let number1 = 10;
let str2 = String(number1);
console.log(str2);

let number2 = 10;
let boolean1 = Boolean(number2);
console.log(boolean1);


```


### typeof()


how do we know what type is a variable?  we can know the type explicitly like this or inexplicitly behind the scene

```javascript 

console.log(result, typeof result);

```











