# _Your project title_

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

> _Describe the compiler or interpreter needed_.

## About the standard library

> _Give some examples of the functions and data structures
> offered by the standard library_.

## About open source library

> _Describe at least one contribution by the open source
community written in the language._

# Analysis of the language

> _Organize your report according to the project description
document_.


