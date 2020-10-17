# Hello_world
#Test

public class Exercise5 {

    public static void main(String[] args) {
        Scanner userInput = new Scanner(System.in);

        // Read first integer value
        System.out.println("Input first integer number");
        int a = userInput.nextInt();

        // Read second integer value
        System.out.println("Input second integer number");
        int b = userInput.nextInt();

        // addition
        double addition_result = a + b;
        System.out.println("a = " + a + ", b = " + b + ", result is  " + addition_result);

        // subtraction
        double subtraction_result = a - b;
        System.out.println("a = " + a + ", b = " + b + ", result is " + subtraction_result);

        // multiplication
        double multiplication_result = a * b;
        System.out.println("a = " + a + ", b = " + b + ", result is " + multiplication_result);

        // division
        double division_result = a / b;
        System.out.println("a = " + a + ", b = " + b + ", result is " + division_result);

        // raising to a power
        double power_result = Math.pow(a, b);
        System.out.println("a = " + a + ", raised to power " + b + ", gives us " + power_result);
    }
}
