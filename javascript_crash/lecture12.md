
# Projects 
## Let's build a Todo App


1. add html, css and bootstrap 

```html

<!doctype html>
<html lang="en">
  <head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">

    <title>Hello, world!</title>
  </head>
  <body>
    <h1>Hello, world!</h1>

   
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ka7Sk0Gln4gmtz2MlQnikT1wXgYsOg+OMhuP+IlRH9sENBO0LRn5q+8nbTov4+1p" crossorigin="anonymous"></script>

 
  </body>
</html>

```


2. add html and css elements 

```html

<!doctype html>
<html lang="en">
  <head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">

    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta2/css/all.min.css" integrity="sha512-YWzhKL2whUzgiheMoBFwW8CKV4qpHQAEuvilg9FAn5VJUDwKZZxkJNuGM4XkWuk94WCrrwslk8yWNGmY1EduTA==" crossorigin="anonymous" referrerpolicy="no-referrer" />
    <title>Todos </title>
 <style>
body{
  background:#352f5b;

}
.container{
  max-width : 400px;
}


input[type-text],
input[type-text]:focus{
  color:#fff;
  border:none;
  background:rbga(0,0,0,.23);
  max-width: 400px;
}
.todo li{
  background:#423a6f;
}
.delete{
  cursor: pointer;
}

</style>


  </head>
  <body>
    <div class = "container">

      <header class = "text-center text-light my-4">
   <h1 class = "mb-4"> Todo List</h1>

   <form class = "search">

 <input class = "form-control m-auto" type = "text" name = "search" placeholder = "search" >
   </form>

   </header>


   <ul class = "list-group todos mx-auto text-light">
   <li class = "list-group-item d-flex justify-content align-item-center"> 
    <span>item 1 </span>
    <i class ="far fa-trash-alt delete"></i>

   </li>
    <li class = "list-group-item d-flex justify-content align-item-center"> 
        <span>item 2 </span>
    <i class ="far fa-trash-alt delete"></i>
   </li>
    <li class = "list-group-item d-flex justify-content align-item-center"> 

        <span>item 3 </span>
    <i class ="far fa-trash-alt delete"></i>
   </li>


  </ul>

<form class = "add text-center my-4">
  <label class = "text-light"> new a new todo ...  </label>
<input class = "form-control m-auto" type = "text" name = "add">

</form>



    </div>




   
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ka7Sk0Gln4gmtz2MlQnikT1wXgYsOg+OMhuP+IlRH9sENBO0LRn5q+8nbTov4+1p" crossorigin="anonymous"></script>

 
  </body>
</html>

```


3. add javascript for add and delete 


```javascript 

const list = document.querySelector('.todos');

const template = (todo) => {

html = ` <li class = "list-group-item d-flex justify-content align-item-center">
        <span>${todo} </span>
    <i class ="far fa-trash-alt delete"></i>`;

list.innerHTML += html;

}
const addTodo = document.querySelector(".add");
addTodo.addEventListener("submit", (e) =>{
e.preventDefault();
const todo = addTodo.add.value.trim();
if(todo.length){
template(todo);}
addTodo.reset();

} );


```

there is a lot todos and it is a lot for js to add event listener 

this could affect performance 


we want to check if the thing we click has the "delete" class 

```javascript 
list.addEventListener("click", (e) => {
if(e.target.classList.contains("delete")){
e.target.parentElement.remove();

}


```

4. filter out things 

```javascript 
const search = document.querySelector('.search');
search.addEventListener('keyup', (e) => {
const word = search.value.trim();
filterToDos(word);


});

const filterToDos = (word) => {

Array.from(list.children)
  .filter((todo) => !todo.textContent.includes(term)).forEach((todo) => todo.classList.add('filtered'))

}
```



alternatively, we can use this html + css 



```javacript 
VM3119:3 Uncaught TypeError: Failed to execute 'addEventListener' on 'EventTarget': 2 arguments required, but only 1 present.
    at <anonymous>:3:3
    at NodeList.forEach (<anonymous>)
    at <anonymous>:2:11
(anonymous) @ VM3119:3
(anonymous) @ VM3119:2
let totalList = document.querySelectorAll('#myUL');
totalList.forEach((e) => {
e.addEventListener((item) => {
item.target.remove();

} )

})
VM3129:3 Uncaught TypeError: Failed to execute 'addEventListener' on 'EventTarget': 2 arguments required, but only 1 present.
    at <anonymous>:3:3
    at NodeList.forEach (<anonymous>)
    at <anonymous>:2:11
(anonymous) @ VM3129:3
(anonymous) @ VM3129:2


lis = document.getElementsByTagName("li");
for(let i = 0; i < lis.length; i++){
lis[i].addEventListener("click", (e) => {
e.target.remove();


})
}


lis = document.getElementsByTagName("li");
for(let i of lis){
i.addEventListener("click", (e) => {
e.target.remove();


})
}

uls = document.querySelector("#myUL");
uls.addEventListener('click', (e) => {

if(e.tagname == 'LI')
e.target.remove();
});

```


## in this case, we can use 

```javascript 
const list = document.querySelector("#myUL");
Array.from(list.children).filter().forEach();



```



