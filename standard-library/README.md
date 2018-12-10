# CSCI3055U-Final-Swift

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

// Globla Operators, such as print(_:separator:terminator)
print ("one two three") // prints one two three
print (1...3)    // prints 1...3
// using separator:
print(1, 2, 3 separator:"..") // prints  1..2..3
// using terminator:
print(1, 2, 3 terminator:"") // prints 123

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

