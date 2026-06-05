# cal
#include <iostream>
#include <iomanip>  // For better number formatting
#include <limits>   // For input validation
using namespace std;

void clearInput() {
    cin.clear();
    cin.ignore(numeric_limits<streamsize>::max(), '\n');
}

int main() {
    double num1, num2;
    char op;
    char choice;

    cout <<"::::::::Hi There:::::::\n";
    cout << "============================\n";
    cout << "      SMART CALCULATOR      \n";
    cout << "============================\n";
    cout << "Perform basic calculations!\n";

    do {
        cout << "\nEnter first number: ";
        while (!(cin >> num1)) {
            cout << "Invalid input! Please enter a number: ";
            clearInput();
        }

        cout << "Enter operator (+, -, *, /, % for modulo): ";
        cin >> op;

        cout << "Enter second number: ";
        while (!(cin >> num2)) {
            cout << "Invalid input! Please enter a number: ";
            clearInput();
        }

        cout << "\n----------------------------\n";

        cout << fixed << setprecision(2);  // Format output to 2 decimal places

        switch(op) {
            case '+':
                cout << "Result: " << num1 << " + " << num2 
                     << " = " << num1 + num2 << endl;
                break;

            case '-':
                cout << "Result: " << num1 << " - " << num2 
                     << " = " << num1 - num2 << endl;
                break;

            case '*':
                cout << "Result: " << num1 << " * " << num2 
                     << " = " << num1 * num2 << endl;
                break;

            case '/':
                if (num2 != 0)
                    cout << "Result: " << num1 << " / " << num2 
                         << " = " << num1 / num2 << endl;
                else
                    cout << "Error: Division by zero is not allowed! 🚫" << endl;
                break;

            case '%':
                if (num2 != 0 && num1 == static_cast<int>(num1) && num2 == static_cast<int>(num2))
                    cout << "Result: " << static_cast<int>(num1) << " % " << static_cast<int>(num2) 
                         << " = " << static_cast<int>(num1) % static_cast<int>(num2) << endl;
                else
                    cout << "Error: Modulo requires non-zero integers! 🔢" << endl;
                break;

            default:
                cout << "Invalid operator! Please use +, -, *, /, or % 😕" << endl;
        }

        cout << "\nDo you want to calculate again? (y/n): ";
        cin >> choice;
        clearInput(); 

    } while(choice == 'y' || choice == 'Y');

    cout << "\nThank you for using Smart Calculator! 👋\n";

    return 0;
}
