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
            Imagine a js file that actually does something meaningful. It most probably have multiple functions and/or variables. The execution context gets created whenever we run our js file and kindof manages the lexical environments and the golbal exectuion context. Their are 2 types of execution context, the first one is global and the second one is function execution context and basically is called and created when a function runs.

            The Global EC(execution context) contains two things by default. rather javascript create them for us. It is the global object and the 'this' keyword. The global object (key value pairs) being anything not inside a function, be it a variable or a function decalration like our test function above. The this keyword is a variable that denotes the actual EC we are into.
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
        So, as discussed above, every funtion invoked creates a new EC on top of the already existing global EC . It stacks up and kindof follow the LIFO prinnciple. The last EC created is the the one that is currently being executed. Once it has been processed, it gets popped out of the stack and then the one below it executes till the only thing left is the Global EC

    Variable Environment
        Basically where our variables are stored and relate to each other in memory

    Scope
        Where a variable at any given time is accesible and available in your code. So if we call a same function twice, that means two execution context, which creates two different spaces in memory.

        Scope Chain
            Links to the outer environment from it's lexical position
            for example if we have this piece of code

            function a(){
                console.log(myVar);
            }

            function b(){
                var myVar = 2
                a()
            }
            var myVar = 1
            b()

            The output would be 1 . Since it can't find myVar inside of the execution context it currently is in, it falls back to the outer scope, in this case the GEC.

            If function a was nested in function b, then the output would be 2 since it found the myVar in the outer scope, which in this case is the function b, as shown below


            function b(){
                function a(){
                    console.log(myVar);
                }
                var myVar = 2
                a()
            }
            var myVar = 1
            b()

            In that same sense if we didn't declare myVar in function b, it would fallback to the GEC and the output would be back to 1, as shown below.

            function b(){
                function a(){
                    console.log(myVar);
                }
                a()
            }
            var myVar = 1
            b()

        Scope and Let ES6
            let is block scoped instead of function scoped. During the execution phase the let variable is still created and assigned an undefined value

    This keyword
        this keyword is directly dependent on who is calling it. for eg : if you say I'm having a good time, the I refers to you and it's denoted by this keyword in js

    ASYNCHRONOUS REQUESTS
        If Javascript is single threaded and synchronous, how the hell does the browser does thing asynchronously?
            Turns out, the browser contains other elements than just the Javascript engine. It has a Rendering Engine which renders the page, styled and all, it has a HTTP Request engine of some kind to make these requests and other elements also.
            So when we say async requests, it's more delegating requests than anyhring else, the browser has hooks that just calls the engine responsible for that particular task you want to do and your JS just waits for it's completion to proceed further.

            So say for example we have a click event. These events are pushed inside of an event queue, which will be periodically looked at when the JS engine's execution stack is empty (ie after the execution context and global execution context have been completed)

            So, what appears asynchronous, is actually not the case, so long functions, or long exections on the exectuion stack will definitely alter the execution timing of all other async events happening.

Second Part
Types and Javascript
    Dynamic Typing
        You don't tell the engine what data type a variable holds, it will deduce it while running the code. So in reality, one variable can hold several data types.s
            The difference with static typing and dynamic typing is shown below.
            In c++
                bool isABool = 'jeff' // Error!
            In JS
                let/var isABool = 'jeff' // No Error!
                isABool = true // No Error!
                isABool = 21 // No Error!
    Primitive Type
        It is a type of data that represents a single value. So no objects(object is a collection of key/value pairs).
        In JS, we have six of them
            undefined - To represent nothingness, also the base type assigned by the JS engine if we don't assign a variable
            null - Also to represent nothingness. We use it when we want to assign nothingness to a variable instead of undefined to avoid confusion or unwanted errors
            boolean - true or false
            number - In js we only have floating point number, basically every number we assign has some decimals. That's why math is sometimes weird with js
            string - Any text in between single or double quotes
            symbol - They are used to represent unique and immutable values that can be used as identifiers or keys in objects.
    Operators
            It is a special function writtenly in a different syntatic manner.
            For example
            const a = 3 + 4
            is syntatic sugar for a pre-written function in JS that does addition. 
            function add(3, 4) (just an example, it's maybe not exactly as is)
            So the JS parser then converts what we write above to the weird function below and then it gets executed
            True for all other operators ( + , -, *, /, >, <, ==)
        
        Operator Precedence and Associativity
            Operator precedence
                Determines which operator function gets called first when there are multiple operators on a single line ( higher precedence wins)
            
            Associativity
                Basically, what order operators are exceuted or called left to right or right to left
                when functions have same precedence.
                find on this link the order preferences for js
                https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_precedence#table

                for example
                let a = 1, b = 2, c = 3
                a = b = c
                console.log(a,b,c)
                is going to return 3,3,3

                This is because equality operator '=' has right to left associativity, meaning b = c will be exceuted first which returns 3 and then a = b will be run.

                another example
                let a = 4 + 3 * 5
                    Since multiply has precedence level 13 and addition level 12, it means that 3 * 5 will be executed first and returned the value 15
                    and then 4 will be added to that 15 to return 19 total

                But if we did 
                let a = (4 + 3) * 5
                since (...) has higher precedence of level 19, 4 + 3 will be executed first then the multiplication will be carried out to give 35

                Crazy right!
            
            Coercion
                The process of converting a value from one type to another
                So we can also kindof use the concept of precedence to get a better understanding of this phenomenon.
                So JS will prioritise converting a NUMBER to a STRING.
                for example if we have the code below
                let a = 1 + '2'
                it will return us '12'
                JS will convert the 1 to a string '1' so as it can carry out the addition(well concatenation in that case to be more precise.)
                So the code below will also return '12'
                let b = '1' + 2

                Now for the weird part - 
                Say we have this statement
                const a = 1 < 2  < 3
                    Easy, this return true, since 2 is less than 1 and 3 is less than 2
                
                now if we have this one
                const b = 3 < 2 < 1
                    Should return false right?But it does not, it returns true again ?!?!?!
                    Actually, there's a very good explanation for this.
                
                The Associativity of comparison operators are from left to right.
                So for the case of const a = 1 < 2  < 3
                    1 is less than 2 evaluates to true.
                    So then true is then compared to 3 like so const a = true < 3
                    Now, we have a type incompatibility. So the true will be coerced by JS into a Number data type, using this built-in method called Number(expression)
                    So Number(true) will return 1.
                    Then finally const a will be equal to 1 < 3 , which evaluates to true.

                    So far so good.....
                In the case of const b = 3 < 2 < 1 , the same concept applies.
                    the comparison os from left to right accprding to it's respective associativity rule.
                    So, 3 < 2 is evaluated and the result is false. which makes sense
                    Then, that false values is compared to the 1 like so 
                    const b = false < 1
                    Again, type incompatibility.
                    So, false will be coerced to a number using the built-in method Number(false) which returns 0
                    Now const b = 0 < 1 which returns true.

                    JS does not make sense, but kindof does!

            Equality Operator
                We have three ways of doing equality operator. To keep it simple
                Two equals '==' is loose equality (ie without type comparison)
                so 2 == '2' will return true since it is coerced

                Three equals '===' is strict equality operator( No coercion takes place here)
                so 2 === '2' will return false

                We also have the not equal loose operator and not equal strict operator '!=' and '!=='
                
                The third one is Object.is to compare two types. ES6
                Object.is(2, 2) returns true
                Object.is('2',2) returns false

                More details here : https://developer.mozilla.org/en-US/docs/Web/JavaScript/Equality_comparisons_and_sameness

            Existence and Booleans
                So for example we have this snippet below.

                    const a ;
                    if(a){
                        console.log("a contains a value")
                    }
                This will output nothing since a is not defined and will be coerced to false
                On the otherhand, if const a = '1'
                it will return 'a contains a value', since '1' will be coerced to true using the built-in method Boolean('1')
                So we can use coercion and if statements to check and evaluate variables. Pretty handy
            
            Default Values
                Another handy trick is to use or operator over lenghty if/else statements.
                for example we have the function greet below

                const greet = (name) => {
                    console.log(`Hello ${name}`)
                }

                we could call greet() like so without an error, since name is allocated a value of undefined when the global execution is lauched.
                It will return us "Hello undefined" thanks or not thanks to coercion.
                What we could do is something like below

                const greet = (name) => {
                    name = name || 'stranger'
                    console.log(`Hello ${name}`)
                }
                In this case, name inside of the greet function will be evaluated to the first expression that coerces to true. So, if Boolean(undefined) evaluates to false, it goes to the second expression and Boolean('stranger') evaluates to true, so it will return the string 'stranger' and assign it to name. Since || has a higher precedence than = , || is executed first.
            
            Frameworks and the script tag
                So say that inside of an html body, we have this.
                <body>
                    <script src = './lib1.js'/>
                    <script src = './lib2.js'/>
                    <script src = './index.js'/>
                </body>

                It does not seperate the script code into several ECs, rather it stack and piles them up into a single JS file (ie our global execution context).
                So, we could have in lib1.js this snippet
                let mySpace = 'lib1'

                and have console.log(mySpace) in our index.js and it will execute fine returning us 'lib1'
                Then if in lib2.js we have mySpace = 'lib2'
                In our app.js the console.log(mySpace will evaluate to 'lib2')
                
Third Part - Object and Functions
    Objects - A collection of key/value pairs. It can be primitive, another nested object or method/functions
        const person = {
            firstName: "john",
            lastName: "wick",
            address: {
                state: "NY",
                addressLine1: "12, rue don't exist"
            },
            tellMeMyName: function() {
                return this.firstName + " " + this.lastName;
            }
        }
    
        or like so
            const person = new Object()
            person.firstName = "john"
            person.lastName = "wick"
            person.tellMeMyName = function() {
            return this.firstName + " " + this.lastName;
            }
        and both basically creates an object, just two different syntaxes, the first one is called object literal and the other is the dot syntax
    
    NameSpaces - 
        Namespace refers to the programming paradigm of providing scope to the identifiers (names of types, functions, variables, etc) to prevent collisions between them. For instance, the same variable name might be required in a program in different contexts.

        Js lacks default namespaces, however we can use objects to kindof create namespaces
        for example
            const english = {
                greet: "Hello!"
            }
            const spanish = {
                greet: "Hola!"
            }
        So if we were to call that same greet property but within the 2 different objects, we would get different results
            english.greet is going to return "Hello!"
            spanish.greet is going to return "Hola!"

    JSON vs Objects
        So, objects and Json does look quite alike right ? 
        True and also not true.
        Json is more strict than objects in term of writing it. You cannot pass a function to a json.
        And your Json has to be inside of a quoted string.
        Luckily we have helpers in JS that helps us to convery an object to JSON and vice versa.
            const person = {
                firstName: "john",
                lastName: "wick",
                address: {
                    state: "NY",
                    addressLine1: "12, rue don't exist"
                },
            }

        We can do JSON.stringify(person) and it will be converted to a JSON like below

        `{"firstName":"john","lastName":"wick","address":{"state":"NY","addressLine1":"12, rue don't exist"}}`

        const jsonVariable = `{"firstName":"john","lastName":"wick","address":{"state":"NY","addressLine1":"12, rue don't exist"}}`

        and to convert a JSON back to an object, we do JSON.parse(jsonVariable) and it's back to the OG object

    Functions are Objects
        First Class functions
            Everything you can do with other types(string, number, objects), you can do with functions. For example assign it to variables, pass them around, create them on the fly. So every function in JS is essentially a special type of first-class objects.

            So, as for objects, we can attach a primitive to it, another object or even a function. Mind Blown!!! and since it is a special type of object it also contains or may not contain a name(named and anonymous function) and also a code ( basically everything that sits inside of our function and that is executable using the () syntax)
            So for example : 
                function greet(){
                    console.log("Hello From this Crazy JS world")
                }
            So if we call greet(), we are executing the code inside of it.
            Now if we do greet.greetings = "Hello! it works too" and console.log it, it is going to return us "Hello! it works too"

            We can attach objects too like so 
                greet.meta = {
                    name: "function",
                    prop: "first class function"
                }
            
            And attach a function to a function
                greet.aFunction = () => {
                    console.log("I am an attached function")
                }
            
            Alright, that's enough Javascript for today!
        