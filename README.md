# JsTheWeirdParts

A step by step approach to discover the JS world and all it's intricacies. 👻
Welcome to JS hell! 😈
There's no one to hoist you out of this loop!!


First Part
Execution Context and Lexical environments
        Syntax Parsers - 
            Ever gotten a compile error on your terminal, be it react, vue or a simple script you've written. Thank this guy for it.
            It's basically a set of rules and strict commands ( specificities of a particular language for eg: ()=>{} to denote an arrow function ) which is run and checks on whether it is correct or not based on the language you're using.

            One thing to remember is what you write in code form is not what the computer reads. It is compiled and/or interpreted by programs called the compiler and interpreter which are themselves a series of rules and command wirtten by someone ( Grace Hopper being the first person to create a compiler) and turn your code to 0s and 1s
        
        Lexical Environments - 
            The importance of the physical place that you write your code gives you an idea on where it will sit when compiled and turned to machine language.
            for eg : 
            function test(){
                const a = 10;
            };
            the position of the constant a in our function named test gives us an idea on when and where it is going to be available ( scoping).
        Execution Context - 
            Imagine a js file that actually does something meaningful. It most probably have multiple functions and/or variables. The execution context gets created whenever we run our js file and kindof manages the lexical environments and more called the golbal exectuion context. Their are 2 types of execution context, the first one is global and the second one is function execution context and basically is called and created when a function runs