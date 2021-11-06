
# Async JavaScript 



## cheatsheet

### Normal way 
1. request = new XMLHttmpRequest();
2. request.addEventListener("readystatechange", () => {})
2.1 if(request.readyState === 4 && request.status === 200) else if(request.readyState === 4)
3. request.open("GET", url);
4. request.send();

```javascript 
/* https://jsonplaceholder.typicode.com/todos/1
*/


const request = new XMLHttpRequest();
request.addEventListener("readystatechange", () => {
	if(request.readyState === 4 && request.status === 200)
console.log(request.responseText);
else if(request.readyState === 4){

}

})

request.open("GET","https://jsonplaceholder.typicode.com/todos/");
request.send();

```
### Callback Function way 

```javascript 

const CallBackFunction = (callbackfunction) => {
const request = new XMLHttpRequest();
request.addEventListener("readystatechange", () => {
	if(request.readyState === 4 && request.status === 200){
callbackfunction(undefined,"this is going great! success");
}

else if(request.readyState === 4){
callbackfunction("ERROR!!! BOOM", undefined);

}

})

request.open("GET","https://jsonplaceholder.typicode.com/todos/");
request.send();


}

CallBackFunction((err,data) =>{

console.log("this is callback");
if(err){
console.log(err);

}else{
console.log(data);
}


} )

```


### JSON.parse(request.responseText)



### CallbackFunction('json url').then(data => {}).then(err = > {})
### return new Promise((resolve, reject) = {})


### CallbackFunction((url)).then((data) => {}).catch((err) => {})


```javascript 
const CallbackFunction = (resource) => {

return new Promise((resolve, reject) => {

const request = new XMLHttpRequest();
request.addEventListener("readystatechange", () => {
if(request.readyState === 4 && request.status === 200){
resolve(JSON.parse(request.responseText));


}else if(request.readyState === 4){
reject("error here!! BOOM");
}

});

request.open("GET",resource);
request.send();
});


}

CallbackFunction("https://jsonplaceholder.typicode.com/todos/").then((data) => {console.log("promise resolved", data);}).catch((err) => { console.log("got error",err);})


```

### second request : CallbackFunction((url1)).then((data) => { return CallbackFunction(url2)}).then(data => { console.log("second");})catch((err) => {})

```javascript
CallbackFunction("https://jsonplaceholder.typicode.com/todos/").then((data) => {console.log("promise resolved", data);
return CallbackFunction("https://jsonplaceholder.typicode.com/todos/");
}).then((data) => {console.log("good news!",data); }).catch((err) => { console.log("got error",err);})

```


### fetch("url").then((response) => {console.log(response.json());}).catch((err) => {})


```javascript 
fetch("https://jsonplaceholder.typicode.com/todos/1").then( (response) => {console.log(response.json());}).catch((err) => {console.log(err);})

```


### nonblocking code starts now and finish later, let javascript carry on with the rest of the code async() => { const request = await fetch('url.json'); const data = await response.json(); }
```javascript 

const callBackFunction = async() => {const response = await fetch("https://jsonplaceholder.typicode.com/todos/");
const data = await response.json();
return data;
 }

callBackFunction().then((data) => {console.log("resolved", data);})

```


### if(response.status !== 200) {throw new Error()}


```javascript 
const callBackFunction = async() => {const response = await fetch("https://jsonplaceholder.typicode.com/todos/");
if(response.status !== 200){
throw new Error("this is the new error here");

}
const data = await response.json();
return data;
 }

callBackFunction().then((data) => {console.log("resolved", data);}).catch((err) => { console.log("hahaha, error:",err);})

```


climbing a mountain with no peak and you kept on slipping up along the way as well, perservere 



it governs how we perofrm tasks which take some time to complete. e.g requesting data from a database or from an API 



you will be using it at some point to do these kinds of things 


in a very simplistic nutshell, asynchronous code is code that can start now and finish later 


understand its counterpart - synchronous code. JavaScript, by its very nature, is a synchronous language, an that basically means that JavaScript can execute one statement at a time from top to bottom, run in term. 


JavaScript is being called a single threaded language and that essentially means the same thing 
a thread is like an audit sequence of statements and only one of those statements can run at a time. this is a crux of synchronos code. one statement being executed at a time after one another 


with this image of synchronous code in mind, a single thread and only one statement executing 



requesting data could take 2 or 3 secs to complete, maybe less, maybe more so in a synchronous programming, this fetching data is known as blocking code because it blocks the next line of code from running until it gets the back. so this is a downfall of synchronous code and this is where asynchrnous code comes into play to help 
so we know that running our function synchronously when it comes to a task that takes some time to complete is probably not the best way to complete 

I gave asynchrous code starting now and finishes later. this is the pattern we generally want to follow when boring tasks that take some time to do like network request for database or API 

instead of this being some synchronous function to request data, we use aysnchronous function instead. this means it starts now and come back later where we get it from 

sincely this function is finishing later, what we typically do is pass this function or this statement some kind of callback function as a parameter, and then that callback function is the thing that runs and finishes later on once the request is complete and the data comes back 

remember at all times, javascript can only execute one thing at a time 
but this time when we get to the request function here we are using an asynchronosu function to request the external data. what this means is that the browser takes that request and it handles it outside of the scope of this single thread in anothe part of the browser 

it also takes a callback function and puts it to one side too, so that it knows how to execute this later on when the data comes back 

so because this network request has been taken out of this thread, and now is running in different part of the browser, javascript can carry on down the queue and the remaining functions all the while, this is still going on the request for data. so it contineus through these functions and then when it receives the data back from the network request, and wants the rest of the functions have been executed, then we are allowed to call this callback function and finish this original function, this is the crux of asynchrnous programming.


and it makes our code nonblocking because the rest of the functiosn here, they can run while the request has been made. this explanation is a very simplistic one, and there are other things at play, such as the event loop and call stack. to delve into that would be a bit overwhelming

## Asynchronosu code in action 


setTimeout(() => {}); that function fires after a certain amount of time that we specify 


this is going to take 2 secs to do, then when it comes back, it is going to fire a callback function, we are emulating that request and fire this  


```javascript 

console.log(1);
console.log(2);
 
setTimeout(() => {
	console.log(3);
	conosle.log("this callback function is not blocked");
	},2000);

console.log(4);
console.log(5);


```

this is asynchronous, so it does not block the code 
the actions which take some time to complete 

in the future, we will be using the real http network request for data. this sets the scene how it works, we know the general princile behind asynchronous code 


## http requests 

1. make http requests to get data from another server 
2. we make these request to API endpoints 

we would make what is known as an http request to reach out to that external server on that database to get that data and then do something with it 

these are just like your URLs that a particular API or server expose to us so that we can use them 

the API might have an endpoint which 


browser -- http request -->
                             other server
          <----response --


and each API is going to have its own set of endpoints that we make requests for daa 

we could even make your own API using a service side language. but anyways, once we make a request to an endpoint from the browser, we typically get back a selection of data in a format called json 

a completely free service allows us to play around with API endpoints and to get back json data: https://jsonplaceholder.typicode.com/

chrome -> network -> headers 


## Make HTTP requests 


```javascript 

const request = new XMLHttpRequest();

```


this creates a request object, this xml part represents an old data format we used to work with much before json arrived 
this will send request from the browser, this thing is built into the javascript language 

we take the request variable we just created and now this comes loaded with different properties and methods we use 




```javascript 

const request = new XMLHttpRequest();
request.open('method', url);

```
the first is the open method, when we get some data, we make a get request 

there are other types of requests we can make like post, send data, or ports to update , 
the first argument, the type of request we make 
the second argument is where we want to make th request to what is the end point we want to get data from: https://jsonplaceholder.typicode.com/todos/



at a minute, the request has not actually been made. this is just kind of setting up the request 
to send the request we need:
request.send(); to send the request 

in our code, we can track the progress of a request using an event listener and a specific event called ready state change 
we attach this to the request object itself so we can say request.AddEventListener('readystatechange', ()=>()); 
this fires every time when there is a state change in the request 

a state change jsut means that the request is going through these different phases of the request 

```javascript 

const request = new XMLHttpRequest();
request.addEventListener('readystatechange', () => (console.log(request,request.readyState);));

request.open('GET','https://jsonplaceholder.typicode.com/todos/');

request.send();

```
we will send this request and every time there is some kind of ready state change then it is going to log the conosle 


XMLHttpRequest 1
XMLHttpRequest 2
XMLHttpRequest 3
XMLHttpRequest 4
1 means open
2 means header receives 
3 loading 
4 done 

the most crucial part, this is when we want to take that data and do something with it, we can receive and do something 

we can see this response text and this response text contains the actual data we receive 

if request.readyState === 4, this is when we can do something with the response, the data not in zero one, two or three 
we can call request.responseText, that is the property which contains the response data 


```javascript 
const request = new XMLHttpRequest();
request.addEventListener('readystatechange', () => { 

if(request.readyState === 4){
     console.log(request.responseText);
}

 });
request.open('GET','https://jsonplaceholder.typicode.com/todos/');
request.send();

```

it looks like a gigantic array of javascript objects 




## Response Status 

request.readState === 4, that is not enough, because if there was some kind of error with the request. if we made error, which is not valid, it still trie to make this request and it still goes through the motions of going through each phase or sate and will reach state 4 

```javascript 

const request = new XMLHttpRequest();
request.addEventListener('readystatechange', () => { 

if(request.readyState === 4){
     console.log(request, request.responseText);
}

 });
request.open('GET','https://jsonplaceholder.typicode.com/todossss/');
request.send();


```
now it is 404 error, we do not get the responseText, we still getting this bad status 404 and also no response, how we overcome this is to check the status while response text comes back 

status 200 means the data comes back correctly, the 404 request means it cannot find the resource that we are trying to send it because it did not exist 

100 means information responses 

200 means ok successful 

300 is redirection 

400 range is client error responses 

500 is the server error so it is not our fault 



we have made the correct type of request, but there is some kind of error on the server which prevents us from getting the data so that a different kinds of response codes 


what we want to do is to make sure that we have this response status 

checking for ready state for over here, we can also check for the status right here to 
so we've seen how to do logical and double ampersand and we say request.status is equal to 200 

```javascript 


const request = new XMLHttpRequest();
request.addEventListener("readystatechange", () => {
if(request.readyState === 4 && request.status === 200){

console.log(request,request.responseText);
}

});
request.open('GET','https://jsonplaceholder.typicode.com/todossss/');
request.send();

//VM1744:10 GET https://jsonplaceholder.typicode.com/todossss/ 404

```

this is only going to fire when we get an OK response and readState === 4


```javascript 


const request = new XMLHttpRequest();
request.addEventListener("readystatechange", () => {
if(request.readyState === 4 && request.status === 200){

console.log(request,request.responseText);
}else if(request.readyState === 4){
	console.log("could not fetch the data");
}

});
request.open('GET','https://jsonplaceholder.typicode.com/todossss/');
request.send();

//VM1744:10 GET https://jsonplaceholder.typicode.com/todossss/ 404

```


## Callback Function
we could wrap up all of this code inside a function that makes it more reusable 

```javascript 
const toDo = () =>{ 

const request = new XMLHttpRequest();
request.addEventListener("readystatechange", () => {
if(request.readyState === 4 && request.status === 200){

console.log(request,request.responseText);
}else if(request.readyState === 4){

console.log("could not fetch the data");

}

});
request.open('GET','https://jsonplaceholder.typicode.com/todos/');
request.send();
    
}
toDo();

```

we are making this more reusable I can call this multiple times, it would be nice if I could instead putting a callback function to this, which we then fire over here so we could specify how we want to react in that callback function 

then every time we get to this, we could specify a different callback function to do something 


obviously to this this inside a function, we pass in a parameter and jsut going to call this callback, but you can call it what you want 

when we have either some kind of successful response or a bad respoonse, we can instead of log in this to the console just called the callback 


```javascript 


const toDo = (callback) =>{ 

const request = new XMLHttpRequest();
request.addEventListener("readystatechange", () => {
if(request.readyState === 4 && request.status === 200){

console.log(request,request.responseText);
callback();
}else if(request.readyState === 4){

console.log("could not fetch the data");
callback();
}

});
request.open('GET','https://jsonplaceholder.typicode.com/todos/');
request.send();
    
}
toDo(() => {
console.log("callback fired");
});

```

it would be nice instead if we could pass through the data and error 
we can take in error and data, the convention is when we do callbacks like this from a network request we alwasy do error first and data second 


```javascript 

const toDo = (callback) =>{ 

const request = new XMLHttpRequest();
request.addEventListener("readystatechange", () => {
if(request.readyState === 4 && request.status === 200){


callback(undefined,request.responseText);
}else if(request.readyState === 4){

console.log("could not fetch the data");
callback("could not fetch data",request.responseText);
}

});
request.open('GET','https://jsonplaceholder.typicode.com/todos/');
request.send();
    
}
toDo((err,data) => {
console.log(err,data);
});


```

the err is only define if we define the callback function this way 

```javascript 


const toDo = (callback) =>{ 

const request = new XMLHttpRequest();
request.addEventListener("readystatechange", () => {
if(request.readyState === 4 && request.status === 200){


callback(undefined,request.responseText);
}else if(request.readyState === 4){

console.log("could not fetch the data");
callback("connection error",undefined);
}

});
request.open('GET','https://jsonplaceholder.typicode.com/todos/');
request.send();
    
}
toDo((err,data) => {
if(err){
console.log(err, "this connection is wrong");
}else{
console.log(data);

}
});

```


tie this into the whole idea of asynchronosu code, it can start now and finish later 


this is going to pass this off to another part of the browser so that we can carry on with these statements in the queue 

```javascript 
const toDo = (callback) =>{ 

const request = new XMLHttpRequest();
request.addEventListener("readystatechange", () => {
if(request.readyState === 4 && request.status === 200){


callback(undefined,request.responseText);
}else if(request.readyState === 4){

console.log("could not fetch the data");
callback(request.responseText,undefined);
}

});
request.open('GET','https://jsonplaceholder.typicode.com/todos/');
request.send();
    
}

console.log(1);
console.log(2);
toDo((err,data) => {
if(err){
console.log(err, "this connection is wrong");
}else{
console.log(data);

}
});
console.log(3);
console.log(4);

```

then at the end, we fire this callback function and the rest of statements should be fired 

## JSON data 

#### json looks like an array with loads of js objects inside it, but it is not. it is just a string, which looks like javascript object. and it has to be a string because when a brwoser exchanges data with the server, it has to be done in text format 
that is the format of data transfer and that is why we use this format 


we turn it into a real javascript object so we can access all of the different properties 

now fortunately, there is an object that is built into the js language which we can use to do this 


JSON, stands for javascript object notation 

JSON.parse() this methos takes in a json string, and what it does is convert that json string into javascript objects that we can use easily in the code 


```javascript 

const toDo = (callback) =>{ 

const request = new XMLHttpRequest();
request.addEventListener("readystatechange", () => {
if(request.readyState === 4 && request.status === 200){
const jsonToJSObject = JSON.parse(request.responseText);

callback(undefined,jsonToJSObject);
}else if(request.readyState === 4){

console.log("could not fetch the data");
callback("error here", undefined);
}

});
request.open('GET','https://jsonplaceholder.typicode.com/todos/');
request.send();
    
}


toDo((err,data) => {
if(err){
console.log(err, "this connection is wrong");
}else{
console.log(data);

}
});


```

inside we can see loads of objects we can cycle through and access, we are not going to do that yet 

we can also create our own json as well 

##### when we make a json file, it has to have a .json extension. we have an array, and inside will be different things that look like objects, the difference between when we are writing json objects and javascript obejcts is that all keys have to go in double quotes!!!!  
these are comma separated 

```json

[
{"name1":"value1"}, 
{"name2":"value2"}, 
{"name3":"value3"}, 


]

```




### callback hell 
what if we want to get several file that we want to call one after the other, what if we want to go out and get each one in turn and combine into it??

so this idea of waiting until one request is done to go out and do another request is quite common 



when you are making requests to different apis, often you might eed to make a request to one API to get some data, and use data to get next 




```javascript 

const toDo = (resource,callback) =>{ 

const request = new XMLHttpRequest();
request.addEventListener("readystatechange", () => {
if(request.readyState === 4 && request.status === 200){
const jsonToJSObject = JSON.parse(request.responseText);

callback(undefined,jsonToJSObject);
}else if(request.readyState === 4){

console.log("could not fetch the data");
callback(undefined,request.responseText);
}

});
request.open('GET',resource);
request.send();
    
}


toDo('first.json',(err,data) => {
if(err){
console.log(err, "this connection is wrong");
}else{
console.log(data);
toDo('second.json',(err,data) ={
	if(err){
console.log(err, "this connection is wrong");
}else{
console.log(data);
toDo('second.json',(err,data) ={
	if(err){
console.log(err, "this connection is wrong");
}else{
	console.log(data);
}


}

}
});


```


this is called callback hell, nesting callback within callback within callback 

it would start very soon, get very hard to maintain and read

we will use something called promises 

## promises 

we have seen now how to request data from different sources, one after another sequentially, we did that by testing the requests inside callback functions, inside callback functions ... 

in promise, we either resolve it when we get the data, when it is a success or we reject it when we get some kind of error 




```javascript 

const functionToCall = (resource,callback) => {

const request = new XMLHttpRequest();
request.addEventListener("readystatechange", () => {

if(request.readyState === 4 & request.status === 200){
const jsonObject = JSON.parse(request.responseText);
callback(undefined,jsonObject);
}else if(request.readyState === 4){

callback("error here", undefined);
}


});

request.open("GET",resource);
request.send();

}


functionToCall('https://jsonplaceholder.typicode.com/todos/',(err,data) =>{
if(err){
console.log(err);

}else{

console.log("data here");


functionToCall('https://jsonplaceholder.typicode.com/todos/',(err,data) =>{

if(err){
console.log(err);

}else{

console.log("data here");
}


} )



}


} );



```





when we use promises, the first thing we do is return a new promise like so: return new Promise(); 

a promise is basically something which is going to take some time to do so a promise is ultimately going to lead to one of two outcomes:
1 a promise is going to be resolved, meaning we get the data we want and it is resolved or it is going to be rejected, meaning we get an error at some point and we reject the promise 


so in a promise, we automatically get access to two parameters inside this function 



```javascript 

return new Promise((resolve,reject) => {
	
})



```


these two are functions and they are built into the Promise API 
so in here we typically fetch some data, make a network request, and then if we get some kind of data back and it is success, we would call the resolve function and we would pass the data through in here 


if there is a resolve, then it is true, if not, then we would reject 

```javascript 
const promiseFunction = () => {
return new Promise((resolve,reject) => {
	resolve('this is some data');
	reject('we reject this but we do not have an error because we have not made this request');
})


}

promiseFunction();


```


so we returned a promise right here and a promise is basically saying it will either resolve or reject at some point 

now when we get a promise back from a function like this, we can take on a dot then method and a promise says if you pass a function here it will pass down that function when we resolve promise 

so when we resolve something in a promise, it fires the callback funciton inside the then method and that callabck function takes the data that we pass through to the resolve function 



```javascript 
const promiseFunction = () => {
return new Promise((resolve,reject) => {
	resolve('this is some data');
	
})


}

promiseFunction().then((data) => {
	console.log(data);

	});


```

if we set reject function, it will pass err in the function as a second argument inside the method 



```javascript 
const promiseFunction = () => {
return new Promise((resolve,reject) => {
	
	reject('we reject this but we do not have an error because we have not made this request');
})


}

promiseFunction().then((data) => {
	console.log(data);

	},(err) => {
		console.log(err);
		});


```


now sometimes when we are adding two functions as arguments into then method, it can get a little bit confusing and look a bit messy. and this looks a bit neater than that. specially when it comes to chaining promises together 

```javascript 
promiseFunction().then(data => {

console.log(data);


	}).catch(err => {
		console.log(err);
		});


```
and what this does is catch an error 



```javascript 

const promiseFunction = () => {

return new Promise((resolve, reject) => {
resolve("this is resolved, data presented");
reject("error presented");

});


}

promiseFunction().then(data => {

console.log(data);

}).catch(err => {

console.log(err);

})

```


it might seem pointless before we actually do something improper with it 



```javascript 

const promiseFunction = (resource) => {

return new Promise((resolve, reject) => {
 const request = new XMLHttpRequest();
request.addEventListener("readystatechange", (err,data) => {

if(request.readyState === 4 && request.status === 200){

resolve(data);


}else if (request.readyState === 4){

reject("error getting data, connection might be wrong");
}


});

request.open("GET",resource);
request.send();



}); 


}

promiseFunction("https://jsonplaceholder.typicode.com/todos/").then(data => {
console.log(data);
}).catch(err => {console.log(err);})



```

so this is another way other than using callbacks to work with asynchronosu code. this is really come in handy when we try to sequentially get data one after another because we are going to be able to change promises together 


callback function resulted in messy unmaintainable code 


## chaining promises 
one of the best things about promises is that we can chain them together so we can perform one asychronous task after another in order should we need to 

using callbacks, which results in messy, deeply nested code chaining promises gives us a much cleaner and easier way to do it 

remember we want to get data sequentiall so we know we find this function in the method that we have already got the first lot of data. if we want to do this sequentially to go out and try and get the next lot of data 


```javascript 


promiseFunction("https://jsonplaceholder.typicode.com/todos/").then(data => {
console.log(data);
promiseFunction("").then(data => {

	}).catch(err => {

		})
}).catch(err => {console.log(err);})



```


we do not defeat the whole point of promise chaining 



```javascript 
const magicalFunction = (resource) => {

return new Promise((resolve,reject) => {


const request = new XMLHttpRequest();
request.addEventListener("readystatechange", (err,data) => {
if(request.readyState === 4 && request.status === 200){
const data = JSON.parse(request.responseText);

resolve(data);
}else if(request.readyState === 4){

reject("error here");

}


});
request.open("GET",resource);
request.send();


});


};


magicalFunction("https://jsonplaceholder.typicode.com/todos/").then((data) =>{
console.log(data);
}).catch((err) => {

console.log(err);

})
```


instead this we return the promise, what that means is that the parents of this thing, the whole hting now has a return value of a promise 


so since this returns a promise now I can take on the dot then method again at the end 


we are getting the first lot of, and we are getting this callback function which runs when we are turning this request 


```javascript 
promiseFunction('json-data).then(data => {
console.log("promise 1 resolved", data);
return promiseFunction('json-data');

}).then(data =>{

	console.log("promise 2 resolve",data);
	}).catch(err => {console.log(err);})






```

###### the good thing about the catch is it catches any error!!! so we do not have to rewrite the catch because it just catches all errors at the end and one function that runs for any error!!!




```javascript 
promiseFunction('json-data1').then(data => {
console.log("promise 1 resolved", data);
return promiseFunction('json-data2');

}).then(data =>{

	console.log("promise 2 resolve",data);

	return promiseFunction('json-data3'); 
	}).then(data => {
		console.log("promise 2 resolve",data);

		}).catch(err => {console.log(err);})






```

that takes the data from that request
and notice now we do not have that big triangle etched in our code 

we do not get callbacks and this looks a lot more logical one after another so that is one of the really nice things about promise is the way we can chain them together like this. if we have the error anywhere, this is still gonna fire the error. this works for any requeset if we have a catch method on the end and we have a function which takes that error. it is going to fire for any error in any one of these request 




## The Fetch API 

so far when we have been making HTTP request, we have been using new XMLHttpRequest(); to do that and that is completely fine to do 

however, there is a newer and quicker way to make these request using the native fetch API, which is now built right into the language 

this is a fairly modern addition to the language and it is going to require us to write much less code than old way using the XMLHttpRequest object, and it is also going to implement the promised API under the hood, which is going to make handling success and error cases easy 

you might be sitting there asking yourself why we have put you through all the misery of learning the old way when there is a newer and easier way to work 


it is not to annoy you is you have a great understanding of what is actually happening when we make these requests and to learn all about how callbacks with requests and promises, understanding different moving pieces 

I can show you a more simplified approach to getting data which implements all of these things 

```javascript 

fetch(json);
```

we pass in an argument which is the resource that we want to fetch. now, that could be some endpoint to an API like json or it could just be a local resource 

now this returns as a promise, a promise is basically at some point either resolve it or reject it 


```javascript 
fetch('.json').then((response) =>{

	}).catch((err) => {

		});

```








```javascript 
fetch('.json').then((response) =>{
 console.log('resolved', response);
	}).catch((err) => {
		console.log('rejected',err);

		});

```

I would like to show you how the errors worth with the fetch api 

```javascript 

fetch('https://jsonplaceholder.typicode.com/todos/').then(response => {console.log(response)}).catch(err => {console.log(err);});



```



we cannot see any data inside this body 


response.json(); method gets us the data and it passes and gets us the response data and it passes it so we can use it inside our code easily 


const data = response.json(); wont work and the reason is because response.json() righ here, this returns a promise. a promise is something that typically takes a little to do, it can be rejected or resolved 


```javascript 

fetch('https://jsonplaceholder.typicode.com/todos/').then(response => {
console.log(response);
return response.json();
}).then(data => {
console.log(data);
}).catch(err => {console.log(err);})

``` 

so in the future, when we are making some kind of network request and we are probably gonna be using this way to get some kind of json, rather than the old way of using http request object because this is much less code to write and much easier to maintain 


three steps: 
1 fetch the data 
2 take the response 
3 return response 



## aysnc & await 

they basically allow us to do is change promises together in a clean and much more readable way. so previously, when we use the fetch API, we changed a couple of promises together and we got a promise right here and we find a function when that promise resolved 

this way of promise chaining and it still looks a lot better than callback function but when we start to change a lot of different promises together then it still can start to look a bit messy 

so using async and await what we can do is setting off all of our asynchronosu code into a single function, an asynchronous function, and then use the await key word inside two chain promises together in a much more readable and logical way 


all of the stuff that actually goes out to get data from somewhere 

```javascript 

const functionName = () => {

};

```
but to make it an asynchronous function using these keywords, we jsut pop async right here in front of the parentheses, now this is known as an asynchronous function 


and whenever we call an asynchrnous function, that always returns a promise regardless what is inside here 


async always returns the promise function 


```javascript 

const functionName = async () => {
console.log("this is async");
}
const test = functionName();
console.log(test);


```

inside this function, we want to go out and grab data 

```javascript 

const functionName = async () => {
const response = await fetch('.json');
};
const test = functionName();
console.log(test);

```
so what this does is thi fetch and this returns a promise 

this await keyword stops it from assigning a value to this variable until the promise has resolved 


once the promise has resolved, we can take the value from the result, function and response and assign it to this variable 

then take it on then and take it in the response inthe callback function inside then method 


you might think this is blocking the code, we are adding all of this inside an asynchronous function and this asynchronous function in itself is non blocking 


so when we call this function out here somewhere, that is not going to block the rest of the code. this is returning a promise 


```javascript 
// this is wrong
/* 
VM972:3 Uncaught (in promise) TypeError: response.json is not a function
    at functionName (<anonymous>:3:29)
    at <anonymous>:6:1

*/
const functionName = async () => {
const response = fetch("https://jsonplaceholder.typicode.com/todos/");
console.log(response);

};
functionName();

```



```javascript 
const functionName = async () => {
const response = await fetch("https://jsonplaceholder.typicode.com/todos/");
const data = await response.json();
console.log(data);
};
functionName();



fetch("https://jsonplaceholder.typicode.com/todos/").then(response => {
return response.json();
​
}).then(data => {
console.log(data);
})


```

the power of these await keyword is if we want to use them, we could change together many of these different things obviously the variables something different but we change together many different things that we turn promise and then we would be doing them sequentially 

we would be waiting for one promise to resolve before sigining it to this, then another before siging it 


so it does each step in turn, that is really nice 

so in a sense, it is blocking inside this because we are waiting until these tasks are done, but because this whole function is asynchronous and it returns a promise when we use in our code it would like the code to carry on
```javascript 
const functionName = async () => {
const response = await fetch("https://jsonplaceholder.typicode.com/todos/");
const data = response.json();
return data;

}
functionName().then(data => {console.log(data);}).catch(err => {console.log(err);} )

```

we demo it this is nonblocking 


```javascript 
console.log(1);
console.log(2);
functionName().then(data => {console.log(data);}).catch(err => {console.log(err);} )
console.log(3);
console.log(4);

```

this is an asynchronous function, starts now, finishes later and lets javascript carry on with the rest of the code while it is doing things 

what does it achieve for us? firstly, it is bundled up all of asynchronous code inside the function, and secondly it is an asynchronous function, so it is not going to block the rest of the code in our application 

and thirdly, it gives us a much cleaner way to chain promises together much more readable 


and the beauty of this is that we could chain as many as promises together as we want 

we just follow the same pattern of using await before each call 

before we finish up the async and await are not supported in all the browsers like IE, but all modern browsers do support it at this moment in time 

## Throwing & Catching errors 


how to throw our own custom erros inside the asynchronos function if we want to reject the promise that this returns 


so currently, there is some kind of error when we use this json method if json is not valid json, then this is goin to reject the promise and it is going to return that rejection so that we can catch it down here 


```javascript 
const functionName = async () => {
const response = await fetch("https://jsonplaceholder.typicode.com/todosss/");
return response.json();

}
functionName().then(data => {
console.log(data);}).catch(err => {
console.log("this is wrong",err);})



```


this is an error object
```javascript 
const functionName = async () => {
const response = await fetch("https://jsonplaceholder.typicode.com/todosss/");
return response.json();

}
functionName().then(data => {
console.log(data);}).catch(err => {
console.log("this is wrong",err.message);})

```



err.message property therefore in the catch method we can catch the error and we can log it to the console 

when we use the fetch method, if there is a problem with the resource, we spell incorrectly 

if the response is not being found, then it is throwing some kind of error instead and it is reject this promise 


so to combat this, we are going to have to manually check if the resonse has a status of 200 or rather check that it does not have one because it does not have a status of 200 then we can throw our own error 


throw new Error("msg");
```javascript 

const functionName = async () => {
const response = await fetch("https://jsonplaceholder.typicode.com/todosss/");

if(response.status !== 200){
throw new Error("the connection is not valid");
}

return response.json();

}
functionName().then(data => {
console.log(data);}).catch(err => {
console.log("this is wrong",err.message);})



```




this syntax is creating a new error object so this throws a new error 

when we throw a new error inside an asynchronous function, the promise returned by this asynchronous function is reject. therefore we can catch this error that we have just throw in .catch() that we have just thrown 



as far as asynchronous javascript goes, we are now pretty well equipped to go out and start fetching data from external sources so that we can use that data in our applications 


we are going to put this newfound knowldge to very good use 

this idea will sink in 








