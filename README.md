# ES6 basics and usage guide 

## Var, Let and Const 
1. Var have functional scope and can be accessible to global if it is created in global space.
2. Let is having block scope and hoisting is not there in Let, we cannot use undeclared variables before the initialization, after initialiaation we can use that variables.
3. In Var we can duplicate the declaration, reinitialize the variables with new value, while in Let we cannot, it throws error-"Already been declared".
```
let greet = "GM";
let greet = "GN"
//throws error...

var greet = "GM";
var greet = "GN"
//works fine
```

4. In let as we have block scope we can create 2 variables with same name, one in global and one in block.

```
let greet = "GM";

if(true){
let greet ="GN";
console.log(greet);
}
console.log(greet);

//output
//GN
//GM
```
5. If we initilize by let and then we can change the value, the value gets changed.
```
let greet = "GM";

if(true){
greet ="GN";
console.log(greet);
}
console.log(greet);
// GN
// GN
```
6. Example
for var it uses global variable and update the value of "i" i.e the same variable to 5 in 2 sec.
```
for(var i=0; i<5; i++){
	setTimeout(()=>{
     console.log(i);
    },2000);
}

//(5) 5
```
if we use let then
```
for(let i=0; i<5; i++){
	setTimeout(()=>{
     console.log(i);
    },2000);
}

 0
 1
 2
 3
 4
```
7. Const have the constabnt value. We can initialize two same const variable but both should be in differnt block, as it also have block scope.
```
const pi =3.14;
{
const pi =3.14555;
console.log(pi);
}
console.log(pi);
// 3.14555
// 3.14
```
8. In const, if we initialize the object then we can change its properties.
```
const per = {name: "Ishant"};
console.log(per);
per.name = "John";
console.log(per);
output:
{name: "Ishant"}
{name: "John"}
```
we cant replace the object , only we can change its properties
```
const per = {name: "Ishant"};
console.log(per);
per = {name: "john"};
console.log(per);
output:

 {name: "Ishant"}
 Uncaught TypeError: Assignment to constant variable.
    at <anonymous>:3:5
 ```
 
 ## Template Literal
 1. It simplifies the use of concatination by using the back tick "`".
 for example
 ```
 const per ={
name:"Ishant",
company: "Google",
role: "Software Developer"
}

var msg = "Hi, my name is" + per.name+ ". I works at " +per.company + ".";
console.log(msg);
Output: Hi, my name isIshant. I works at Google.


var tmsg = `Hi, my name is ${per.name}. I works at ${per.company }.`;
console.log(tmsg);
Output: Hi, my name is Ishant. I works at Google.
```
2. We can also do calculations in literal.

```
const pi = 3.14;
const r = 2;
let mgs = `The Area of circle is ${ pi *r*r}`;
console.log(mgs);
Output: The Area of circle is 12.56
```
3. Template literal remember the formatting also
```
const per ={
name:"Ishant",
company: "Google",
role: "Software Developer"
}



var tmsg = `
Hi, my name is ${per.name}. 
I works at ${per.company }.
`;

console.log(tmsg);
Output: 
 
Hi, my name is Ishant. 
I works at Google.


```
4. We can also write the HTML inside the template literal and assign to a variable. In react Jsx we have to use this template literal lot of time.

## Tagged Template

1. Here we can pass the template literal as a argument but without the brackets. The string is pass as first argument array, howvwer the rest is variables.

example:
```
const per ={
name:"Ishant",
company: "Google",
role: "Software Developer"
}

function bio(arr, arr1,arr2,arr3){
console.log(arr);
console.log(arr1);
console.log(arr2);
console.log(arr3);
}

const tmsg = bio `Hi, my name is ${per.name}. I works at ${per.company }. My role is ${per.role}`;

Output:
(4) ["Hi, my name is ", ". I works at ", ". My role is ", "", raw: Array(4)]0: "Hi, my name is "1: ". I works at "2: ". My role is "3: ""length: 4raw: Array(4)0: "Hi, my name is "1: ". I works at "2: ". My role is "3: ""length: 4__proto__: Array(0)__proto__: Array(0)

Ishant
Google
Software Developer
```
2. We can also use rest operator .
```
const per ={
name:"Ishant",
company: "Google",
role: "Software Developer"
}

function bio(arr, ...arg){
console.log(arr);
console.log(arg);

}

const tmsg = bio `Hi, my name is ${per.name}. I works at ${per.company }. My role is ${per.role}`;

Output:

(4) ["Hi, my name is ", ". I works at ", ". My role is ", "", raw: Array(4)]0: "Hi, my name is "1: ". I works at "2: ". My role is "3: ""length: 4raw: Array(4)0: "Hi, my name is "1: ". I works at "2: ". My role is "3: ""length: 4__proto__: Array(0)__proto__: Array(0)

[Ishant, Google, Software Developer]
```
## Arrow Functions

1.consize code
2.Implicit return
3. No 'this' Binding.
```
normal functions:

function square(a){
return a*a;
}

console.log(square(2));
output -> 4

const square = function(a){
return a*a;
}

console.log(square(2));
output -> 4
```
ES6
```
const square = a = a*a;

```
in case of multiple arguments
```
const square = (a,b) = a*b;

```

Program No 1:
To get the output in format {course: "java", Site: "google.com"}
```
const course = ["java","c","react"];


const site ="google.com";

const output = course.map( temp => ({"course" : `${temp}`, "Site": `${site}` }));
console.log(output);

output: 
(3) [{…}, {…}, {…}]
0: {course: "java", Site: "google.com"}
1: {course: "c", Site: "google.com"}
2: {course: "react", Site: "google.com"}
```
Program No 2:
To print the movies based on their rating descending.
```
const movies = [
{name:"A", rating:5.5},
{name:"B", rating:8.5},
{name:"C", rating:4.5}
]

movies.sort((a,b) => a.rating > b.rating ? -1 : 1 );

Output:
(3) [{…}, {…}, {…}]
0: {name: "B", rating: 8.5}
1: {name: "A", rating: 5.5}
2: {name: "C", rating: 4.5}
```
## Destructuring Object

```
const person = {
name: "Ishant",
profession: "Web Developer",
experience: "3+",
social:{
facebook:"www.facebook.com/Ishant"
}
}

const { name, profession, experience, social } = person;

```
We can also map object properies into different variable name of our choice

```
const { name: fname, profession: prof, experience, social } = person;

```
We can also give default value, It is used when value is undefined and object property is missing.
```
const { name: fname= "ABC", profession: prof ="XYZ", experience, social } = person;

```
## Classes & Inheritance

Before we starts with the Classes and Inheritance , we will see the Objects and prototypes in depth.

Object is basically a key value pair, collection onf multiple values.
Object can be created in multiple ways

```
var myObj ={};

to add the properties in object

myObj.foo = "Hello";

var myObj = {
    name: "Ishant",
    company:"Google",
    address:{
        city:"Hyd",
    }
}
```
First we will see normal object creation by function
```
function createEmployeeObject(fn,ln,gender) {
var obj ={};
obj.fn = fn;
obj.ln = ln;
obj.gender = gender;
return obj;
}

conct emp1 = createEmployeeObject("Atul","Verma","Male");

Using Constructor

When we use new keyword the JS put var this={}; 
```


In JavaScript, we already ave the concept of Inheritance and it is by using Protoypal Inheritance.
