# calculator


import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        char operator;
        Double number1 = 0.0, number2 = 0.0, result;

        Scanner input = new Scanner(System.in);

        System.out.println("Choose an operator: +, -, *, /, %, ^, !, p (for pi), e (for e), or P (for pi calculation)");
        operator = input.next().charAt(0);

        if (operator != 'p' && operator != 'e' && operator != 'P' && operator != '!') {
            System.out.println("Enter first number");
            number1 = input.nextDouble();
            System.out.println("Enter second number");
            number2 = input.nextDouble();
        }

        switch (operator) {
            case '+':
                result = number1 + number2;
                System.out.println(number1 + " + " + number2 + " = " + result);
                break;
            case '-':
                result = number1 - number2;
                System.out.println(number1 + " - " + number2 + " = " + result);
                break;
            case '*':
                result = number1 * number2;
                System.out.println(number1 + " * " + number2 + " = " + result);
                break;
            case '/':
                if (number2 != 0) {
                    result = number1 / number2;
                    System.out.println(number1 + " / " + number2 + " = " + result);
                } else {
                    System.out.println("Error! Division by zero is not allowed.");
                }
                break;
            case '%':
                result = number1 % number2;
                System.out.println(number1 + " % " + number2 + " = " + result);
                break;
            case '^':
                result = Math.pow(number1, number2);
                System.out.println(number1 + " ^ " + number2 + " = " + result);
                break;
            case '!':
                if (number1 == Math.floor(number1) && number1 >= 0) { // check if number1 is a non-negative integer
                    int fact = 1;
                    for (int i = 1; i <= number1; i++) {
                        fact *= i;
                    }
                    result = (double) fact;
                    System.out.println(number1 + " ! = " + result);
                } else {
                    System.out.println("Error! Factorial is only defined for non-negative integers.");
                }
                break;
            case 'p':
                double pi = Math.PI;
                System.out.println("The value of pi is: " + pi);
                break;
            case 'e':
                double e = Math.E;
                System.out.println("The value of e is: " + e);
                break;
            case 'P':
                System.out.println("Enter the number of terms for pi calculation:");
                int n = input.nextInt();
                double piCalc = 0;
                for (int i = 0; i < n; i++) {
                    piCalc += 4 * ((i % 2 == 0) ? 1 : -1) / (2 * i + 1);
                }
                System.out.println("The calculated value of pi is: " + piCalc);
                break;
            default:
                System.out.println("Invalid operator!");
                break;
        }

        input.close();
    }
}

