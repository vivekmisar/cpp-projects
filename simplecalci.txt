#include <iostream>
#include <stdexcept>

// Calculator class definition
class Calculator {
public:
    // Method to add two numbers
    double add(double a, double b) {
        return a + b;
    }

    // Method to subtract two numbers
    double subtract(double a, double b) {
        return a - b;
    }

    // Method to multiply two numbers
    double multiply(double a, double b) {
        return a * b;
    }

    // Method to divide two numbers
    double divide(double a, double b) {
        if (b == 0) {
            throw std::invalid_argument("Cannot divide by zero");
        }
        return a / b;
    }
};

int main() {
    Calculator calc;  // Create a Calculator object
    double num1, num2; // Variables to hold user input
    char operation;   // Variable to hold chosen operation

    // Prompt user for input
    std::cout << "Enter the first number: ";
    std::cin >> num1;

    std::cout << "Enter the second number: ";
    std::cin >> num2;

    std::cout << "Enter an operation (+, -, *, /): ";
    std::cin >> operation;

    try {
        // Perform the selected operation
        double result;
        switch (operation) {
            case '+':
                result = calc.add(num1, num2);
                break;
            case '-':
                result = calc.subtract(num1, num2);
                break;
            case '*':
                result = calc.multiply(num1, num2);
                break;
            case '/':
                result = calc.divide(num1, num2);
                break;
            default:
                std::cerr << "Invalid operation!" << std::endl;
                return 1;
        }

        // Output the result
        std::cout << "The result is: " << result << std::endl;

    } catch (const std::invalid_argument& e) {
        // Handle errors such as division by zero
        std::cerr << "Error: " << e.what() << std::endl;
        return 1;
    }

    return 0; // Exit the program successfully
}
