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
