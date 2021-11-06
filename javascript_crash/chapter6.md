
# Chapter6 The Document Object Model Part2 Form Events 

introduce the idea of node relations by that I mean relationships between different nodes or different elements in a node tree 


a node tree is a visual representation of the DOM and it represents our html page 


## cheatsheet 
Array.from(element.child);

```javascript 
childrenNode.forEach((elem) => {elem.textContent = "what's up"; } )
childrenNode.forEach((elem) => {elem.classList.add('success'); } )

```


button.addEventListener('event','callback function');
element.parentElement
element.parentElement.parentElement
element.nextElementSibling 
element.previousElementSibling 

e and e.target 
e.target.style.AttributeName = "";
element.remove() or e.target.remove() to remove element

### document.createElement('li');  

### element.append('element');

### element.prepend('element');



## parents, children & siblings 



one type of relationship between different noes or elements on a tree is the sibiling relationship 

another type of relationship is the parent child relationship 


we use these to traverse the DOM between different elements and get bigger selections of elements 


```javascript 

<html lang="eng">

<head>

	<title> javascript </title>



</head>


<body>


<h1> page title </h1>
	

<div>
<h2> article title </h2>
<p> hello </p>
<p> hello </p>
<p> hello </p>
<p> hello </p>
<p> hello </p>


</div>


</body>
</html>


```
imagine at some point what we wanted to do is make a selection of all of the elements inside the elements. these can be three separate queries, but we are writing much more code than we actually need to do here, how do we combat these problems? 


we use a query to the parent, then we can use the child property to go out an d give us all of the children in a single collection 



### element.child


```javascript 
const parentNode = document.querySelector('div');
console.log(parentNode.children);

```


when we use the querySelectorAll and we can use a foreach on an array, this is an html collection and w can use forEach on this 

so how do you cycle through this? we take this and convert it into an array, then when we have that, we can use forEach on it


### Array.from(element.child);

this now is no longer html collection, it is an array we can see right there, this is actually returning a new value. this does not alter the original value of this thing 

```javascript 
const parentNode = document.querySelector('div');
const childrenNode = Array.from(parentNode.children);

```


now we pass a callback function into this. just do a single arrow function first of all 


```javascript 
childrenNode.forEach((elem) => {elem.textContent = "what's up"; } )
childrenNode.forEach((elem) => {elem.classList.add('success'); } )

```

if we know how to make a selection for a certain element and want to find the path to all of its different parents, we can do that here 


### element.parentElement 

```javascript 
const element = document.querySelector('h2');
console.log(element.parentElement);

```

### element.parentElement.parentElement


```javascript 
const element = document.querySelector('h2');

console.log(element.parentElement.parentElement);
```

### element.nextElementSibling 


```javascript 
const element = document.querySelector('h2');
console.log(element.nextElementSibling);

```
### element.previousElementSibling 

```javascript 
const element = document.querySelector('h2');
console.log(element.previousElementSibling);

```

this is long and convoluted, you might never need to do this, but it is possible we can use all of these different properties to traverse the domain and get selections of things 


### event basics -- click events 


we will take one step back, a lot of the time, the manipulation and changes we make are in reaction to a user's action on a web page, if a user clicks on a button, we might show some kind of pop up menu 


the idea ultimately is that we are going to creat very simplistic to do list 


```javascript 
<html lang="eng">

<head>

	<title> todo list </title>


	<style>

li{
	list-style-type:none;
	max-width: 200px;
	padding:8px;
	margin:8px auto;
	background: #eee;
	border: 1px dotted #ddd;
}
</style>

</head>
<body>




<h1> Todos </h1>

<ul>

<li> to do 1: laver votre mains </li>
<li> to do 2: rinser votre visage </li>
<li> to do 3: doucher votre corp </li>
<li> to do 4: brosser votre dents </li>


	</ul>


	<button> cliquer moi</button>
 

</body>
</html>


``` 

there is three setps involved to set this up 

first of all, we need to query the DOM to get the lement where we expect the event to happen
the second thing to do is add what is called an event listener to the element and an event listener actively listens for user events and a specific element 


and the third step is to write a callback function, which will fire when the event happens, when users clicks a button 


### button.addEventListener('event','callback function');

this method here actively listens to certain events on this button



```javascript 
// option1 
const butt = document.querySelector('button');
butt.addEventListener('click', ()=>{ console.log('butt is clicked, fired'); });

// option2 
const butt = document.querySelector('button');
butt.addEventListener('click', functionOne);

const functionOne = () => {console.log('fire in the hole'); }

```


now we want to attach eventListener to each of the li so when a user click on that tag, eventually we are going to delete that from the to do list 





```javascript 

const lists = document.querySelectorAll('li');
lists.forEach((elem) => {elem.addEventListener('click', e =>{ console.log(elem.textContent); })})


```

### e and e.target 

inside the browser automatically gives us a parameter called E or events 

```javascript 
const lists = document.querySelectorAll('li');
lists.forEach((elem) => {elem.addEventListener('click', e =>{ console.log(e);
console.log(e.target); })})

```


another thing is the item, we cycle through all of the text in the colleciton of the node, rather and we have access to each individual item at the time 


e.target will help us with event delegation

```javascript 

const lists = document.querySelectorAll('li');
lists.forEach((elem) => {elem.addEventListener('click', e =>{ console.log(e.target); })})

```

### e.target.style.AttributeName = "";
then we can change the style in the target 


```javascript 
const lists = document.querySelectorAll('li');
lists.forEach((elem) => {elem.addEventListener('click', e =>{  e.target.style.textDecoration = "line-through"; })})

```


## creating & removing elements



### element.remove() or e.target.remove() to remove element


if I am at any point want to remove this from the DOM then I can jsut say element.remove(), so this takes that element out of the webpage 
and that is going to get the lights out 


```javascript 
const lists = document.querySelectorAll('li');
lists.forEach((elem) => {elem.addEventListener('click', e =>{  e.target.remove(); })})

```

### innerHTML += "<tag> </tag>" to append element to the html 


```javascript 

const ul = document.querySelector('ul');
const button = document.querySelector('button');
button.addEventListener('click', () => {ul.innerHTML += "<li> add new item</li>"; });

```


what we could also do is say we are going to create a new element, 



### document.createElement('li');  

### element.append('element');

### element.prepend('element');

we have actually inserted it into the webpage, so we just have a reference to it, we need to set the text content of this empty tag with no text in it 


the first way is to append this to a parent, the second way is to prepend it to the parent 


```javascript 

const ul = document.querySelector('ul');
const button = document.querySelector('button');
button.addEventListener('click', (e) => {
const li = document.createElement('li');
li.textContent = "this is a new element";
ul.append(li);
});

```
prepend will take the element we put inside, and prepend it to the top 


```javascript 

const ul = document.querySelector('ul');
const button = document.querySelector('button');
button.addEventListener('click', (e) => {
const li = document.createElement('li');
li.textContent = "this is a new element";
ul.prepend(li);
});


li.forEach((elem) => {
elem.addEventListener('click',(e) => {
e.target.remove();
})

})

```
for people do not like to use template to do stuff, this would be a way to do 

##### watch out, if we try to click on the new appended list, it does not work. that is because we already attach the events at the start before we added new lists, we can combat this 




## event bubbling and delegation 


this is one of those things that you could quite easily turn a blind eye to when you are learning, it will trip you up along the way 

when an event occurs like a click or whatever element we click, that element becomes the event target. e.target, so it finds that callback function for that element if there is an event lsitener attached to it 


that event then bubbles up the dot from the event target to its parent, which will fire the callback function of that listener 


if we do, then the event bubbles up and it goes to the next parent and so forth 


this is called event bubbling, the event starts at the event target, then it bubbles up to parents to see if there is any eventListener attached to those. and if there is, then it is going to fire the callback function for those event listeners as well 


```javascript 

const ul_element = document.querySelector('ul');
const li_element = document.querySelectorAll('li');
ul_element.addEventListener('click',e => {console.log("ul is fired")} );
li_element.forEach((li_ele) => {li_ele.addEventListener('click',e =>{ console.log("li is fired");} )})

```


at this point, if we want to stop the event, we can do via a method called stop propagation on the event object 




### e.stopPropagation(); 

```javascript 

const ul_element = document.querySelector('ul');
const li_element = document.querySelectorAll('li');
ul_element.addEventListener('click',e => {console.log("ul is fired")} );
li_element.forEach((li_ele) => {li_ele.addEventListener('click',e =>{ console.log("li is fired");
e.stopPropagation();
} )})
```

when the callback function fires, we reach the stopPropagation method and it stops the event bubbling up anymore to the parent, otherwise you might eget some unexpected behaviour when you are working with eventListeners 



it is not a good pratice, because it is a costly thing to attach an event like this, so we also have to attach a new event listenres to these new element every time we add a new one to it. so there is a better way to do this so we are not attaching an event listenre to loads of different elements, and also it is going to work when we add new element to the DOM as well 


inside this event listener, inside this callback function, try to find out what thing was initially clicked 


so we do not have anymomore have an event listener attached to those tags, so no callback function is fired
however, the event is then going to bubble up to that 


we are not attaching event listener to individual tag. and wha we want to do is take that tag.target and we want to remove it 


### e.target.tagName 

```javascript 

const ul = document.querySelector('ul');
const button = document.querySelector('button');
button.addEventListener('click', e => { const new_li = document.createElement('li');
new_li.textContent = "voici l'articile nouvelle";
ul.prepend(new_li);


}

);
ul.addEventListener('click', e => {
if(e.target.tagName === 'LI'){
 e.target.remove();
}
}


 )

```




we have got basics under the wraps 


### document.addEventListener('copy',callback_function);

```javascript 


<html lang="eng">

<head>

	<title> todo list </title>


	<style>

</style>

</head>
<body>




<p>Le Lorem Ipsum est simplement du faux texte employé dans la composition et la mise en page avant impression. Le Lorem Ipsum est le faux texte standard de l'imprimerie depuis les années 1500, quand un imprimeur anonyme assembla ensemble des morceaux de texte pour réaliser un livre spécimen de polices de texte. Il n'a pas fait que survivre cinq siècles, mais s'est aussi adapté à la bureautique informatique, sans que son contenu n'en soit modifié. Il a été popularisé dans les années 1960 grâce à la vente de feuilles Letraset contenant des passages du Lorem Ipsum, et, plus récemment, par son inclusion dans des applications de mise en page de texte, comme Aldus PageMaker.

</p>


 
</body>
</html>

p_tag = document.querySelector('p');
<p>​…​</p>​

p_tag.addEventListener('copy', e => {

alert("this is a copy right, please do not copy");
})

```

### document.addEventListener('mousemove',callback_function);

## e.offsetX, e.offsetY

```javascript 

p_tag.addEventListener('mousemove', e => {
console.log(e);
})

```




### document.addEventListener('wheel',callback_function);

### e.pageX, e.pageY

```javascript 

p_tag.addEventListener('wheel', e => {
console.log(e);
})
```

we can build a popup using this 





## event inside forms 


web forms exist to capture some kind of data or information from a user -- e.g. a username & password 

so either way, we are capturing data or info from a user 

in particular we use a event to click the submit button at the bottom of the form once they filled in, so we could set up an event listener to react to this submit event 

### submit event 


```javascript 

<html lang="eng">

<head>

	<title> form </title>


	<style>

</style>

</head>
<body>

<form class = "signup-form">
<input type = "text" id="username" placeholder="username">


<input type = "submit" value = "submit">


</form>



 
</body>
</html>


``` 





so when we are listening for a submit event, we attach the event listener to the form itself and not the submit button 


### form.addEventListener(submit, callback_functions);

### e.preventDefault();

to submit the default action of a particular event, that prevents the default function of a particular event 

we must have a form and a submit input entry here !!!!

```html


                <form class = ".signup-form">

                <input type = "text" id = "username" placeholder="username" >
  

        		<input type = "submit" class ="what"> 

```


```javascript 

const form = document.querySelector('.signup-form');
form.addEventListener('submit', e => {
e.preventDefault();
console.log(e);});

```


now we need to get the form field of that form, we need a reference to the field 

the first way: using const element = document.querySelector('#id'); then element.value
we need to get the value of that particular input field from the user name input field 

```javascript 

const form = document.querySelector('.signup-form');
form.addEventListener('submit', e => {
e.preventDefault();
console.log(username.value);});
```



another way is form.id_name because that gets the form that we have already had 

```javascript 
const form = document.querySelector('.signup-form');
form.addEventListener('submit', e => {
e.preventDefault();
console.log(form.username.value);});

```




## regular expression 

when we create forms and we expect to use that type data into those forms, we normally want the user to enter values that match a certain pattern, to do this, we are going to be using matching patterns called regular expressions or regex for short 



what this allow us to do is type out character patterns to represent certain values 


```javascript 
/^[a-zA-Z0-9][n,m]
/^.[n,m] // this means any character 
```

regular expression contains one forward slashes 


$ means this word must end with the pattern 

^ means this word mus start with the this pattern 

```javascript 
const pattern = /[a-z]{n,}/;
// at least n

let result = pattern.test(string); 
// to test if the resutl passes the etst 


const name = 'eddie';
let pattern = /[a-z]{6,}/;
let result = pattern.test(name);
console.log(result);    
```



```javascript 

let pattern = /^[a-zA-Z0-9]{6,}/;
const form = document.querySelector('.signup-form');
form.addEventListener('submit', e => {
if(pattern.test(form.username.value)){
const p = document.createElement('p');
p.textContent = "this is correct";
form.append(p);
}else{
const p = document.createElement('p');
p.textContent = "please follow the right format";
form.append(p);
}
}
)

```

## keyboard event 


so now we are able to lsiten to some events and we are able to validate a user's data, real time checking. how can we implement this real time validation behaviour into our form? 

### form.attribute.addEventListener('keyup',callback_function);
the keyup event basically means when I press a key down and then lift it back up, that is the key up event 

so not the push down, but the letting go the up, let's pass that through 


```javascript 

const form = document.querySelector('.signup-form');
form.addEventListener('keyup', e => {console.log(form.username.value, e.target.value);});
```



what we do is to test the value inside the code block , inside its function 

```javascript 

<html lang="eng">

<head>

	<title> form </title>


	<style>

</style>

</head>
<body>

<form class = "signup-form">
<input type = "text" id="username" placeholder="username">


<input type = "submit" value = "submit">
<p id = "toggle"> </p>

</form>



 
</body>
</html>




let pattern = /^[a-zA-Z0-9]{6,}/;
const form = document.querySelector('.signup-form');
form.addEventListener('keyup', e => {if(pattern.test(form.username.value)){
const p = document.createElement('p');
p.textContent = "this is correct";
form.append(p);
}else{
const p = document.createElement('p');
p.textContent = "please follow the right format";
form.append(p);
}});


let pattern = /^[a-zA-Z0-9]{6,}/;
const toggle_text = document.querySelector("#toggle");
const form = document.querySelector('.signup-form');
form.addEventListener('keyup', e => {if(pattern.test(form.username.value)){
toggle_text.textContent = "this is correct";
}else{

toggle_text.textContent = "please follow the right format";

}});

```
#### we can see all the keys being pressed 









