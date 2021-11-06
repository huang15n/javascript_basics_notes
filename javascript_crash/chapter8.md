

# Date & Time 


## cheatsheet 

```javascript 
console.log('timestamp',date.getTime());
const now = new Date();
console.log(now);
console.log(typeof(now));
console.log(now.getFullYear());
console.log(now.getMonth());
console.log(now.getDate());
console.log(now.getDay());
console.log(now.getSeconds());
console.log(date.toDateString());
console.log(date.toTimeString());
console.log(date.toLocaleString());

```


date in javascript are a type of data that fall under the object data type so that means that is also reference types and not primitive types 

now, dates can be really useful for many things in js from creating the date of a blog post or assign updates to an event date, and etc...

for now just know that a constructor is going to generally create a new object for us 

```javascript 

const now = new Date();
console.log(now);
console.log(typeof(now));

```
I will show you a handful of different methods 
```javascript 

const now = new Date();
console.log(now.getFullYear());
console.log(now.getMonth());
console.log(now.getDate());
console.log(now.getDay());
console.log(now.getSeconds());

```



time stamps, a time stamp is represented a date by the number of milliseconds since 1st of 1970




```javascript 
console.log('timestamp',date.getTime());

```

### toDateString() 

```javascript 

console.log(date.toDateString());
console.log(date.toTimeString());
console.log(date.toLocaleString());

```




## TimeStamp & Comparison 

a lot of time when working with dates in js, whether that be storing them in a database or maybe comparing dates together, it is a lot easier to ues timestap than using dates object directly 


if you want to use timestamp you can use 

```javascript 
date.getTime();

```
and this long number is the number of milliseconds since 1970/1/1 

we work out the different in time between them, the difference in milliseconds 


to create different dates with predefined format we can do 

```javascript 
const before = new Date('Mar 1 2021 9:30:20');
 
const now = new Date();

now.getTime();
before.getTime();
 
now - before
//16544353325
now.getDate();


const diff = now.getTime() - before.getTime();

```

we can convert the difference in milliseconds that we have and then we could display it on our web 


1000 millisecond is a second , 60 sec is a min, 60 mins is a hr

```javascript 
const mins = Math.round(diff / 1000/ 60);

const hours = Math.round(diff / 1000/ 60 / 60);

const days = Math.round(diff / 1000/ 60 / 60/ 24);


``` 

this is something we can potentially output in the browser, we can use the timestamp of a event and compare with timestamp of now 





## building a digital clock : setInterval(function, timeInterval);

```javascript 

<html lang="eng">

<head>

	<title> form </title>


	<style>

	body{
		background: grey;
	}


	span{
		border: 1px dotted red;

		padding:20px;
	}

	.clock{
		font-size:4em;
		text-align: center;
		margin:20px;
		font-family:arial;
		color:yellow;
	}

</style>

</head>
<body>

<div class = "clock">
 
</div>
</body>
</html>



const clock = document.querySelector('.clock');


const update = () => {
const now = new Date();
const hr = now.getHours();
const min = now.getMinutes();
const sec = now.getSeconds();

console.log(hr,min,sec);

}

setInterval(update,1000);


const clock = document.querySelector('.clock');

const update = () => {
const now = new Date();
const hr = now.getHours();
const min = now.getMinutes();
const sec = now.getSeconds();

clock.innerText = hr + ":" + min + ":" + sec;

}

setInterval(update,1000);



const clock = document.querySelector('.clock');

const update = () => {
const now = new Date();
const hr = now.getHours();
const min = now.getMinutes();
const sec = now.getSeconds();

clock.innerHTML = `<span>${hr}</span><span>${min}</span><span>${sec}</span>`;

}

setInterval(update,1000)

```




## Date-fns Library 

formatting dates and times in the right for your app can mean writing a fair amount of code 


there is a library that can help us just do that 


https://date-fns.org/





