# CSCI3055U-Final-Swift

Matt Chan
matthew.chan5@uoit.net

## About the language
Swift made its first appearance during June 2, 2014, starting off as a propietary language. Several upgrades were made over the years such as becoming a open-rsource software and more source stability, which leads us to Swift 4.0 in the modern day. 
Swift is a general purpose compiled programming language developed by Apple and is used for their products' operating systems such as iOS, macOS and watchOS. Also Linux is based on Swift as well. The library used by Swift is Objective-C runtime library, and this allows C code to run in one program such as C, C++ and Objective-C. The syntax is similar to C and similar in many ways as it is built to be friendly to new programmers. Additionally, Swift comes with large classes of programming patterns to help fix common programming errors. These include initialized variables before use, out of bound error checks for arrays, checking integer overflow and automatic memory handling.


## About the syntax

import Foundation

var str = "2 + 3 is"
var a:Int = 2   
var b:Int = 3   // same as assigning to integer, but this will restrict the data type to integer
var result = String(a+b)    // type cast. In this case it'll type cast to string
var pi = 3.14159



print(str , result )
print("Pi short form:" , Int(round(pi)))    // example use of the "round" function

var intResult = Int(result) // result can be type casted to any other data type on the go 
if (intResult == 5){   // if statements
    print("Result is equal to 5")
}else{
    print("Result is not 5")
}

for i in 1...100{   // for loop
    print(i, "", terminator:"") // swift's print command automatically prints with a new line. to print on the same line, use terminator:""
}
print()
var foo = 5
var bar = 10 


// declaring functions
func addNumbers(arg num1:Int, arg2 num2:Int) -> Int{
    return num1 + num2
} 
print("5 + 10 [via function call] =" ,addNumbers(arg: foo, arg2: bar))



## About the tools
Swift source code is translated into executable machine code by their own compiler, Swift compiler. It also has an additional number of tools at its disposal, such as IDE integration which comes along with syntax colouring, code completion and many more. The Swift compiler's major components include parsing, which generates an Abstract Syntax Tree (AST) without type information. There is also the semantic analysis which transforms the AST from the parser into a fully-type-checked version of the AST. Both the parser and semantic analysis tells the user errors or warning messages with the input source such as grammar errors. The Clang importer maps C or Objective-C APIs to the corresponding Swift APIs and the Swift Intermediate Language (SIL) has 3 components. SIL Generation lowers the AST into a "raw" SIL, SIL guaranteed transformations performs diagnostics which affectst the correctness of the program and SIL optimizations basically optmizes the program. Lastly the LLVM IR Generation continues to optimize the code and finally generates it into machine code. 

## About the standard library
The Swift standard library contains various data types such as the fundamental data types such as Int, String & Double and collections such as Array, Set and Dictionary. 

// Array:
let numbers = [1, 2, 3, 4]
print(numbers[0])
// Set:
let numbers: Set = ["one", "two", "three", "four"]
if (numbers.contains("one")){
    print ("One exists")
}
// Dictionary:
var numberAndMessage = [1: "first message", 2: "second message", 3: "third message"]
print(messages[1])  // prints "first message"

There are many global functions, primarily print which comes in the format: print(_:separator:terminator)
print ("one two three") // prints one two three
print (1...3)    // prints 1...3
// using separator:
print(1, 2, 3 separator:"..") // prints  1..2..3
// using terminator:
print(1, 2, 3 terminator:"") // prints 123


It also includes protocols that describe thoes data types algorithms which operate on them, such as Collection and Equatable and OptionSet. The implementation is located in the stdlib/public subdirectory
// Collection -> printing the first word in a string
let text = "a b c d"
if let firstWord = text.firstIndex(of:" "){
    print(text[..<firstWord])
}
// OptionSet
let oneOption: rewards = .gold
let bundle: rewards = [.gold .platinum .diamond]
let noOptions: []

var bonus = []
let purchase = 49.50
if (purchase > 65){
    bonus.insert(.gold)
    print("You've earned gold rewards"!)
}else{
    print("Add more to upgrade your membership rank!")
}


## About open source library

> _Describe at least one contribution by the open source
community written in the language._
One open source library I found interesting is called "Hero", which is a supercharged transition engine designed for iOS. It changes or adds transitioning when selecting different things on the screen. I enjoyed looking at it since it gives me the feeling of "smoothness", which is one thing many customers value when looking into buying a new phone. Hero is still being up to date, as it is currently supporting Swift 4.2. 

Another open source library is called "Vapor", which is a web framework and server for Swift which is designed for both macOS and Ubuntu. This allows users to host their own servers on their computers running either of the operating systems, which can be useful for hosting and allowing users to connect. Just like Hero, Vapor is also being up to date and is still supporting macOS and Ubuntu. 

# Analysis of the language
1. There have been claims of Swift being procedural programming and some saying it is functional, but in the end it is known to be procedural. However there are tools that can bring Swift over to the functional programming side, but not to the full "power" of functional programming. 

2. When it comes to boilerplate code, Swift has the ability to automate such code to make things more efficient. For example, take a look at this snippet of code, which compares one instance of the Dog struct with another 

struct Dog{
    let breed: String
    let age: Int
}
// to compare the Dog struc to other parts of code, we can use the Equatable protocol
extension Dog : Equatable{
    func ==(lhs: Dog, rhs: Dog) -> Bool {
        return lhs.breed == rhs.breed && lhs.age == rhs.age
    } 
}
This requires some copy and pasting and when taken to a larger scale, the repetitiveness can result in runtime bugs. 
This is where Sourcery comes in which takes in source code then applies templates determined by the user and generates Swift code, saving time and space. Sourcery is a binary tool and has 3 components: The Source, which is the path to the folder containing the source files as the input. The Template, the path to the template file and the Output, where the new generated code will be in. Templates are written in Stencil syntax.
For example, here is a Equatable template written by Or Ron from Medium.com (more details here https://medium.com/@orron)

{% for type in types.structs %}
extension {{ type.name }} : Equatable {}
func ==(lhs: {{ type.name }}, rhs: {{ type.name }}) -> Bool
{
	{% for var in type.variables %}
	guard lhs.{{ var.name }} == rhs.{{ var.name }} else { return false }
	{% endfor %}
	return true
}

{% endfor %}
 

This will loop through all struts as the input while Stencil copies all contents, but the result does the same thing as the snippet above. Applying it to the Dog struct will result in this:

extension Dog : Equatable {}
func == (lhs: Car, rhs: Car) -> Bool
{
    guard lhs.breed = rhs.breed else {return false}
    guard lhs.age = rhs.age else {return false}
    return true}
}
As you can see creating templates on Swift can ease up many repetitive tasks and thus saving a lot of time and space. 

3. Swift's closure expressions aim to be as optimized as possible, having features such as shorthand argument names and trailing closure syntax. Swift also supports Nested Functions, allowing self-contained blocks of code to be part of a larger function. Part of the standard library contains methods such as the sorted(by:) method, which sorts an array of values with some known type. The method would require a function to be passed as an argument. For example to sort numbers from least to greatest:

func ascending (_s1: int, _s2: int) -> Bool {	// note that the data types are int since this is used for numbers, which is 
	return s1 < s2				// because the te method and functions need to be the same data type. 
}
let numbers = [5, 1, 3, 7, 2]	// here is the array to be sorted
var result = numbers.sorted(by:ascending)	// call the function and the sorted(by:) closure method 
						// will output [1,2,3,5,7]
Additionally there are also filters which can take an array as a parameter and return a new array that satisfies the predicate. The filter can be declared like this:
public func filter (_isIncluded: (Element) throws -> Bool) rethrows -> [Element]

4. Swift supports lexical scoping. Here is an example of calculating the square, and will divide by 2 
func square (x: Double) -> Double {
    let result = x * x
    func divide () -> Double{
        return result / 2
    }
    return divide() 
}
print(square (x: 5.0))

5. As stated before Swift is a procedural programming language but there are tools that can turn Swift to the functional programming side. 
For example, taking only the even numbers from an array through functional programming:
let numbers = [23, 52, 10, 6, 99].filter {(numbers) -> Bool in 	// apply the filter via closure 
	if numbers % 2 == 0 {
		return true
	}else{
		return false
	}
}

6. Swift is a static type language, as all information about classes and functions must be provided once it the program is compiled. 

7. Some of Swift's biggest strengths is its open source compatability, as well as being a safe language since it provides safeguards for the user to prevent errors. As well as being built for performance, it is said to be 2.6 times faster than Objective-C and 8.4 times faster than Python. Although Swift is very new compared to the well-known languages such as Objective-C and Python which came during the 1980's, Swift came out in 2014 and yet is already one of the most popular programming languages. Being a "clean" language, Swift is easy to read and write. Additioanlly Swift is easy to scale so then products that run Swift are guaranteed to be future-proof. Dynamic libraries are included as well to decrease memory footprint and the language is compatible with Objective-C 
As it was mentioned that Swift is still new, that also stands as one of the cons of the language as there are still many issues that will come up as the language matures. It also has a limited amount of native branches and has poor backward compatibility with the older versions, meaning developers will need to rewrite projects once a new version of Swift is released. There is XCode however to help do most of the changes. With the frequent updates that come to Swift and the lack of backwards compatability, it can be difficult finding the right tools to complete a task. Additionally the Apple IDE and XCode is "slow" on supporting tools for Swift. 
