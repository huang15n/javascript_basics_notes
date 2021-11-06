


# Chapter5 The Document Object Model



### cheat sheet 

```javascript 
document.querySelector(''); // class .  id#
document.querySelector(''); // class .  id#
document.getElementById();
document.getElementsByClassName();
Array.from(result.children).forEach(child => {
child.classList.add('child-class');});
tag.getAttribute('attribute');


element.parentElement;
element.parenetElement.parentElement;
element.nextElementSibling;
element.previous.ElementSibling;




document.createElement('li');
li.textContent = '';
ul.append(li);
ul.prepend(li);
element.target.remove();
e.target.stopPropgation();

element.classList.add('className'); 
element.classList.remove('className'); 

para.innerText = "value";
tag.setAttribute('style','class_attribute:value');


element.style.color = "yellow";
element.style.fontSize = "100px";
elements.forEach((elem) => {
elem.style.color = "red";
})


element.textContent.includes('');


element.classList.toggle('className');

element.addEventListener('click', () => {

	})


element.addEventListener('mouseover', () => {

	})

element.addEventListener('copy', () => {

	})


element.addEventListener('wheel', () => {

	})

const ulElement = document.querySelector('.something');
const buttonElement = document.querySelector('.what');
buttonElement.addEventListener('click', () => {
const newElement = document.createElement('li');
newElement.innerText = "something new";
ulElement.prepend(newElement);

});


const liElements = document.querySelectorAll('li');
liElements.forEach((elem) => {
elem.addEventListener('click', (e) => {
e.stopPropogation();
e.target.remove();

})
})



```


## interacting with the browser


kicking off this by learning and governed by object model 


- Document Object Model (DOM)
- Add, change & delete content 
- Make a cool effect in the web page 



- add content to the browser 
- change css style 
- react to user events 
- cool effects 



spin up a local development server so we can preview our webpages in it 


## Document Object Model 
- created by the browser 
- document object 


it is something created by the browser when an HTML document loads inside it 


once the document, html doc is loaded in the browser, the browser creates an object which models this document and this object is caleld the document object 




```javascript 

document
document.location 
document.URL

```

this document is created by the browser and it models the HTML page, we can use it to interact with the external pages using those different properties and methods 
the document object describes our html tree as nodes, it has all these different tags in it. we can use some different methods on that reference to change its content or change its style or remove it. that is the general premise 


html is the root node 




## the query selector 

this action of reaching in and selecting elements is known as querying the DOM, grab element from the DOM.  

### document.querySelector('') to get single element 

for javascript tag:
```javascript 
const para = document.querySelector('tag');


```

in css class we can say
```javascript 
const para1 = document.querySelector('.ClassName');
const para2 = document.querySelector('tag.ClassName'); // that gives a unique css 

const para3 = document.querySelector('tag1 > tag2'); // that gives the first tag2 child

```


```javascript 

<html lang="eng">

<head>

	<title> javascript </title>



</head>


<body>
	<h1> page title </h1>

	<p> this is a p tag </p>

	<p class = "something"> something in the p</p>


</body>
</html>





const para = document.querySelector('p');

console.log(para);
 
 
para.innerText = "hello";


const para_something = document.querySelector('p.something');

para_something.innerText = 'world';

const p_first = document.querySelector('body > p');

```

you always have the help of browser if you are not sure what the querySelector 


what if we want to grab all the elements? 


### document.querySelectorAll('') to get all elements 


it stored them in a single node list 

we can use forEach to cycle through the node list and for each individual node, we get access to that inside the callback function, it grabs multiple elements based on selectors 

```javascript 
const ps = document.querySelectorAll('p');
console.log(ps[0]);
console.log(ps[1]);

ps.forEach(para => {
	console.log(para);
	});

ps.forEach(para => {
	para.innerText = "hello world";
	});

```


## document.getElementById();



```javascript 
<html lang="eng">

<head>

	<title> javascript </title>



</head>


<body>
	<h1> page title </h1>

	<p> this is a p tag </p>

	<p class = "classSomething"> class is in the p</p>


	<p id = "idSomething"> id is in the p</p>




</body>
</html>


const idSelector = document.getElementById("idSomething");
idSelector.innerText = 'what';

```



## document.getElementsByClassName();
we do not need the dots as we would do in using query selectors! when we use querySelectorAll() we saw that we got a node list. now these things are similar but not identical like a node list 

like node list we can still use square bracket notaiton ot get a single element from that list or that collection, but we cannot use the forEach method on the collection: 
```javascript 
const classSelectors = document.getElementsByClassName('classSomething');
classSelectors.forEach(elem => {console.log(elem);});
Uncaught TypeError: classSelectors.forEach is not a function
    at <anonymous>:1:16
```





```javascript 
<html lang="eng">

<head>

	<title> javascript </title>



</head>


<body>
	<h1> page title </h1>

	<p> this is a p tag </p>

	<p class = "classSomething"> class is in the p1</p>
	<p class = "classSomething"> class is in the p2</p>
	<p class = "classSomething"> class is in the p3</p>


	<p id = "idSomething"> id is in the p</p>




</body>
</html>

const classSelectors = document.getElementsByClassName('classSomething');
console.log(classSelectors[1]);

```


## document.getElementByTagName()
they are quite easy to remeber and we are just putting the tag name as a string 
it grabs all tags and store them in a html collection inside this 

it does not much matter which methods you choose, but anything you can select with these methods, you can also select with the querySelector methods. So I tend to stick with using the querySelector or querySelectorAll. it is simple and flexible and you can query any element you need using them. 

also it is useful to be able to use for each directly on a node list which is returned by the query 



```javascript 
<html lang="eng">

<head>

	<title> javascript </title>



</head>


<body>
	<h1> page title </h1>

	<p> this is a p tag </p>

	<p class = "classSomething"> class is in the p1</p>
	<p class = "classSomething"> class is in the p2</p>
	<p class = "classSomething"> class is in the p3</p>


	<p id = "idSomething"> id is in the p</p>




</body>
</html>



```


## adding & changing page content 


```html


<html lang="eng">

<head>

	<title> javascript </title>



</head>


<body>
	<h1> page title </h1>

	<p> this is a p tag </p>

	<p class = "classSomething"> class is in the p1</p>
	<p class = "classSomething"> class is in the p2</p>
	<p class = "classSomething"> class is in the p3</p>


	<p id = "idSomething"> id is in the p</p>




</body>
</html>


```


get the inner text

```javascript 

const para = document.querySelector('p');

console.log(para.innerText);

```

change text inside the paragraph

```javascript 

const para = document.querySelector('p');

para.innerText = "value";

``` 


append text inside the paragraph

```javascript 

const para = document.querySelector('p');

para.innerText += "value";

``` 

cycle through the list 

```javascript 

const para = document.querySelectorAll('p');

para.forEach((p_individual) => {console.log(p_individual);} )


const para = document.querySelectorAll('p');

para.forEach((p_individual) => { p_individual.innerText += ' next text' ;} )

``` 


using innerHTML to change the whole tag 
change the tag, use += to append, = to overwrite it:

```javascript 
const para_class = document.querySelectorAll('.classSomething');

para_class.forEach((para) => { para.innerHTML = "<h1> hello </h1>"; });


``` 

html template to cycle through for each element we were firing his call back function 

```javascript 
const para_class = document.querySelector('.classSomething');

const list_items = ['one','two','three'];

list_items.forEach((item) => { 
	para_class.innerHTML = `<p>${item}</p>`; });


``` 


## getting & setting attribtues 

so in addition to changing the text of an element, we can also get and update attributes 


### tag.getAttribute('attribute');


```html

<html lang="eng">

<head>

	<title> javascript </title>



</head>


<body>
	<h1> page title </h1>

<a href = "https://www.google.ca"> google </a>

</body>
</html>


```

what actually we want to get as a string and we want the href attribute 

```javascript 
const attribute_something = document.querySelector("a");
attribute_something.getAttribute("href");

```
### tag.setAttribute('attribute','value');


```javascript 
const attribute_something = document.querySelector("a");
attribute_something.setAttribute("href", "https://www.amazon.ca");
attribute_something.innerText = "amazon";

```


### tag.setAttribute('class','className');

so far when we have been set in attriute here, we have been set in attribute using attribtues which already exist in the html 



```javascript 

<html lang="eng">

<head>

	<title> javascript </title>


<style>
.warning{
	color:red;
}
.success{
	color:blue;
}


</style>


</head>


<body>
	<h1> page title </h1>

<a href = "https://www.google.ca"> google </a>


<p class = "warning"> hello </p>

</body>
</html>


const para = document.querySelector("p");
para.setAttribute("class","success");

```


### tag.setAttribute('style','class_attribute:value');



```javascript 

const para = document.querySelector("p");
para.setAttribute("style","color:green");

```

## changing CSS style

there is one major drawback in setAttribute

if we got a new style, we come down, we have got a reference already that in here that is querySelector, we setAttribute(name,value); it just going to completely overwrite what is currently there 
```javacript 
console.log(name.style);
// this is the complete style of that element

```

I want to be able to add extra styles isntead of just completely overwriting them 


### element.style.attributeName = value;
if we want to get the specific attribute of the style 

```javascript 
const para = document.querySelector("p");
para.style.color = "yellow";
para.style.fontSize = "100px";
```
so most of the time that we are adding or removing just a single style are used this way of doing it rather than setAttribute. but a lot of the time, instead of just adding inline styles this ay, it can be easiser to predefine you css classes in a stylesheet somewhere and then use javascript to add, remove or change 

## adding & removing classes 


### element.classList.add('className'); 
### element.classList.remove('className'); 


you query this tag, and cycle through them inside the text using forEach 

```javascript 
<html lang="eng">

<head>

	<title> javascript </title>


<style>
.warning{
	padding: 10px;
	color:crimson;
	border : 1px dotted crimson;
}
.success{
	padding: 10px;
	color:limegreen;
	border: 1px dotted limegreen;
}


</style>


</head>


<body>
	<h1> page title </h1>
		<h1> page title </h1>
			<h1> page title </h1>




<p class = "warning"> hello </p>

</body>
</html>


const h1s = document.querySelectorAll('h1');
h1s.forEach((h) => {h.classList.add('warning');})
h1s.forEach((h) => {h.classList.remove('warning');})

```


### element.textContent vs. elementinnerText 

if we use innerText, then it will get us all the text that is visible. for example style = "display:none;"

if we use textContent, what that does is it get all of the text inside the tag, regardless of whether it is hidden or not 

```javascript 
const h1s = document.querySelectorAll('h1');
h1s.forEach((h) => { console.log(h.textContent);})

```

### element.textContent.includes('');

we can use this to see if it includes a certain word or phrase 

```javascript 
const h1s = document.querySelectorAll('h1');
h1s.forEach((h) => { if(h.textContent.includes('page')){
   h.textContent = 'what';
                        }})

```


### element.classList.toggle('className');

this is classList.toggle is equal to classList.add() and classList.remove() 
if it has a class and we use toggle again, then it is going to remove that class


```javascript 
const h1s = document.querySelectorAll('h1');
h1s.forEach((h) => { if(h.textContent.includes('page')){
   h.classList.toggle("success");
                        }})

```








