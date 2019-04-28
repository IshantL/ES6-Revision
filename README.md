"# ES6-Revision" 

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
