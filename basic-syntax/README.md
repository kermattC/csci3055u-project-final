# CSCI3055U-Final-Swift

Matt Chan
matthew.chan5@uoit.net

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


