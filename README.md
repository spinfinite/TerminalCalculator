# TerminalCalculator
// Create a calculator program that prompts the user to enter an operation and 2 operands.  The program determines correct input and performs the operation.  It    // makes use of recursion as well as promptly end the program if the user does not wish to perform additional operations.

// The program uses mac's terminal to compile. 

#!/usr/bin/swift

//Initiate Values

var firstNumber: Double = 0.0
var secondNumber: Double = 0.0
var operand: String = ""

//Function to calculate the operation
func calculate(operand: String, firstNumber: Double, secondNumber: Double) -> Double {
    switch operand {
    case "/":
        return firstNumber / secondNumber
    case "*":
        return firstNumber * secondNumber
    case "-":
        return firstNumber - secondNumber
    case "+":
        return firstNumber + secondNumber
    default:
        return 0
    }
}

//Function to ensure a proper operand is chosen
func checkOperation(operand: String) ->Bool {
    switch operand {
    case "/","*","-","+":
        return true
    default:
        return false
        
    }
    
}

//Function to obtain the first operand and check to see if it is a correct type.
func getFirstNumber() {
    print("Please enter the first number")
    if let first = readLine() {
        if let num1 = Double(first) {
            firstNumber = num1
            getSecondNumber()
        } else {
            print("Please enter a proper number")
            getFirstNumber()
        }
    }
}

//Function to obtain the second operand and check to see if it is a correct type.  The call to continue is also made.
func getSecondNumber() {
    print("please enter the second number")
    if let second = readLine() {
        if let num2 = Double(second) {
            secondNumber = num2
            let result = calculate(operand: operand, firstNumber: firstNumber, secondNumber: secondNumber)
            print("Here is your result: \(firstNumber) \(operand) \(secondNumber) = \(result)\n")
            getResponseToContinue()
        } else {
            print("Please enter a proper number)")
            getSecondNumber()
        }
    }
}
 
//Function to get the operation
func getOperation() {
    print("What operation would you like to perform? /, *, -, +")
    if let operation = readLine() {
        if checkOperation(operand: operation) {
            operand = operation
            getFirstNumber()
        } else {
            print("You have entered an invalid operation.  Please enter /, *, -, +")
            getOperation()
        }
    }
}

//Function to continue or end program
func getResponseToContinue() {
    print("Would you like to continue? y for yes or n for no")
    if let response = readLine() {
        if response == "y" {
            getOperation()
        } else {
            print("Thank you for completing a calculation")
        }
    }
}

getOperation()
