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
                console.log(a)
            };
            the position of the constant a in our function named test gives us an idea on when and where it is going to be available ( scoping). And if not available inside of that function test, it rolls back to the outer lexical environment and so on till it finds the constant a .
        Execution Context - 
            Imagine a js file that actually does something meaningful. It most probably have multiple functions and/or variables. The execution context gets created whenever we run our js file and kindof manages the lexical environments and more called the golbal exectuion context. Their are 2 types of execution context, the first one is global and the second one is function execution context and basically is called and created when a function runs.

            The Global EC(execution context) contains two things by default. rather javascript create them for us. It is the global object and the 'this' keyword. The global object (key vale pairs) being anything not inside a function, be it a variable or a function decalration like our test function above. The this keyword is a variable that denotes the actual EC we are into.
        Hoisting and EC- 
            Hoisting is the process whereby the JS engine allocates space in memory for all variables and functions that is declared and created in the entire EC, so it can access them when the code is executed. All of this happens during the creation phase of the EC.
            During the exection phase is when for example variables are assigned values.
            const a = 10
            Before being executed, JS allocates an undefined type to all variables values. So, const a, before execution phase would be undefined.
            So you've guessed it, a fat function like below
            
            function test(){
                const a = 10;
                console.log(a)
            };

            is stored in memory as such in the creation phase.
            while the new arrow function like below

            const test = () => {
                const a = 10;
                console.log(a)
            }
            would return undefined in the creation phase, since it is at the end of the day, a variable assignation.

            so the below piece of code would return 10 and undefined respectively.
            test()
            console.log(b)
            const b = "hey there"
            function test(){
                const a = 10;
                console.log(a)
            };

            while the below piece of code would return the true value of b, since it has now had the time to be executed and assigned
            test()
            const b = "hey there"
            function test(){
                const a = 10;
                console.log(a)
            };
            console.log(b)

        So to sum it up, the creation phase creates and allocates space in memory for your functions and variables. and during the execution phase is when the JS engine goes line by line and excutes your code
    
    Single Threaded, Synchronous Execution
        Single threaded means only one piece of code is executed at a time.
        while Synchronous also means signle threaded but with the addition of executing in order.

    Function Invocation and Execution Stack
        So, as discussed above, every funtion invoked creates a new EC on top of the already existing global EC . It stacks up and kindof follow the LIFO prinnciple. The last EC created is the the one that is currently being executed.