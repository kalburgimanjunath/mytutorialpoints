# ECMAScript 6 reached feature complete status in 2015 and was formally dubbed “ECMAScript 2015.” 

In this chapter we learn about Block Bindings,Strings and Regular Expressions,Functions,Expanded Object Functionality,Destructuring,Symbols and Symbol Properties,Set, WeakSet, Map, and WeakMap,Iterators and Generators,JavaScript Classes,Improved Array Capabilities,Promises,Proxies and the Reflection API,Modules.

# Let and Const and Var
When you declare a variable using var it will get hosted on top and you can use that variable from anywhere access it.
`
function testing(){
    var abc = 10;
    function testingInside(){
        console.log(abc) // abc = 10
    }
}
`
when you defind the variable using let the variable will be block scoped you cannt access the variable outside the block.
function testing(){
    console.log(abc); // reference error
    function testingInside(){
        let abc = 20;
    }
}

when you use const instead of let/var the value what you initialize will not change forever.
function testing(){
    const abc = 10;
    function testingInside(){
        abc = 20; // error 
    }
}

## Temporal Dead zone
TDZ is where you try to access or assign value to variable which you cannt refer and change.In this example when you are trying to access the abc from testingInside() function using let will create a new variable which has difference reference so you cannt access abc which is defined from var inside testingInside() function this situation is called TDZ.

function testing(){
    var abc = 10;
    function testingInside(){
        let abc = 20; // abc is block scoped
    }
}

## Immediate Invocation function (IIFE)

var funcs = [];

for (let i = 0; i < 10; i++) {
    funcs.push(function() {
        console.log(i);
    });
}

funcs.forEach(function(func) {
    func();     // outputs 0, then 1, then 2, up to 9
})

this can be solved with IIFE or using let instead of var in loop.

var funcs = [];

for (var i = 0; i < 10; i++) {
    funcs.push((function(value) {
        return function() {
            console.log(value);
        }
    }(i)));
}

funcs.forEach(function(func) {
    func();     // outputs 0, then 1, then 2, up to 9
});