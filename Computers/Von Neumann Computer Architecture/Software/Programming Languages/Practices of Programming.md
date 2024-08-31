# Think Like a Coder
#programming-language

## Common Practices of Programming
Before we get into the nitty-gritty of a specific programming language, we need to think of some common practices of all programming languages, including variables, control flows, arithmetic operations, etc., all of which are common in modern programming languages. The Youtube Series [Think Like A Coder](https://www.youtube.com/watch?v=KFVdHDMcepw&list=PLJicmE8fK0EgogMqDYMgcADT1j5b911or&index=2) is the perfect go-to to understand those common practices. These include:
- **Conditions**
- **Return Value**: a program needs to show the result to the user.
- **Loops**: go through a set of instructions again and again until a condition is met.
- **Variables**: containers to store data, such as numbers, words. you can replace it as often as you need.
- **Arithmetic Operations**: addition, multiplication, etc. to variables.
- **Functions/Procedures:** reusable blocks of code with a name, designed to perform specific tasks, such as "calculate_average()". Using functions provides #abstraction of a certain block of code, which promotes code organization, readability and makes complex problems easier to manage.
- #Data-Structures: a pre-defined combination of variables that simplifies calculation.
	- **Lists/Arrays:** Sequences of elements of the same data type, perfect for storing collections of information.
	- **Dictionaries/Maps:** Collections of key-value pairs. These are great for organizing data where you want to quickly look up information using its associated key.
### Example: C
- **Problem:** A school needs a program to calculate the average grade of a student and determine pass or fail status.
```c
#include <stdio.h>

// Function to calculate average grade
float calculateAverage(int grades[], int numSubjects) {
    int sum = 0;
    for (int i = 0; i < numSubjects; i++) {
        sum += grades[i];
    }
    return (float)sum / numSubjects;
}

int main() {
    int numSubjects;
    printf("Enter number of subjects: ");
    scanf("%d", &numSubjects);

    int grades[numSubjects]; // Array to store grades

    printf("Enter grades:\n");
    for (int i = 0; i < numSubjects; i++) {
        printf("Subject %d: ", i + 1);
        scanf("%d", &grades[i]);
    }

    float average = calculateAverage(grades, numSubjects);

    printf("\nAverage Grade: %.2f\n", average);

    // Condition to determine pass/fail
    if (average >= 60) {
        printf("Status: Pass\n");
    } else {
        printf("Status: Fail\n");
    }

    return 0;
}
```
- **Functions:** `calculateAverage` takes the grade array and number of subjects. It calculates and returns the average as a `float`; `#include <stdio.h>` provides necessary input/output functions (printf, scanf).
- **main Function:**
    - **Variables:** `numSubjects` stores the number of subjects, while the `grades` array stores the individual grades.
    - **Input:** The program gets the number of subjects and the grades from the user.
    - **Loops:** A `for` loop iterates to get the grades and another `for` loop inside `calculateAverage` is used to calculate the sum.
    - **Arithmetic operations:** The average is calculated.
    - **Conditions:** An `if-else` statement checks the average to determine pass or fail status.
    - **Output (Return values):** The average and the student's status are printed to the console.

### Same example using other languages
#### Python:
```python
def calculate_average(grades):
    return sum(grades) / len(grades)

grades = []
while True:
    grade = input("Enter grade (or type 'done'): ")
    if grade == 'done':
        break
    grades.append(int(grade))

average = calculate_average(grades)
print("\nAverage Grade:", average)

if average >= 60:
    print("Status: Pass")
else:
    print("Status: Fail")
```
#### Java:
```Java
import java.util.ArrayList;
import java.util.Scanner;

public class GradeCalculator {
    public float calculateAverage(ArrayList<Integer> grades) {
        int sum = 0;
        for (int grade : grades) {
            sum += grade;
        }   
        return (float) sum / grades.size();
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        ArrayList<Integer> grades = new ArrayList<>();

        while (true) {
            System.out.print("Enter grade (or type 'done'): ");
            String input = scanner.nextLine();
            if (input.equals("done")) {
                break;
            }
            try { grades.add(Integer.parseInt(input)); } catch (NumberFormatException e) { 
            System.out.println("Invalid Input: Please enter a whole number."); 
            }
        }

		GradeCalculator calculator = new GradeCalculator();

        float average = calculator.calculateAverage(grades);
        System.out.println("\nAverage Grade: " + average);

        if (average >= 60) {
            System.out.println("Status: Pass");
        } else {
            System.out.println("Status: Fail");
        }
    }
}
```
Note that we didn't ask user to input the number of subjects. In C, arrays must have a declared size at the time of creation, but in a more #high-level-language, the size of array can be adjusted dynamically, such as the ArrayList in Java.

## Beyond the Common Practices
(Generated by ChatGPT)
Absolutely! Let's delve into the world of programming languages and explore why we have such a diverse range.

**Beyond the Common Practices: Why So Many Programming Languages?**

While concepts like variables, loops, and functions form the backbone of programming, **the way we interact with computers has evolved tremendously**. Here's why we need a variety of programming languages:

- **Problem Domains:** Different problems require different approaches.
    - **Web Development:** Languages like JavaScript, HTML, and CSS specialize in creating dynamic and interactive websites.
    - **Scientific Computing:** Python shines with its libraries (NumPy, SciPy) for numerical analysis and data manipulation.
    - **Systems Programming:** C and C++ provide low-level control over hardware, crucial for operating systems and device drivers.

- **Programming Paradigms:** Languages are built on core philosophies that shape how we write code:
    - **Object-Oriented Programming ( #OOP):** Java, Python, C++ center around objects that encapsulate data and behavior, promoting modularity and code reuse.
    - **Functional Programming ( #FP):** Languages like Haskell and Lisp focus on pure functions and immutability (data cannot be changed once created), leading to more predictable and easier-to-reason-about code.
    - **Declarative Programming: ( #declarative)** Languages such as SQL and HTML let you describe _what_ you want, rather than explicitly specifying the steps to achieve it.

- **Level of Abstraction:** The degree to which a language distances itself from the nitty-gritty details of the computer.
    - #low-level-language :** Assembly. These provide direct control but can be more complex.
    - #high-level-language :** Python, Java, C++. They offer more human-readable syntax and handle tasks like memory management automatically, making development faster, often at the cost of some raw performance.

- **Performance vs. Ease of Use:** There's often a trade-off:
    - #compiled-language  (C, C++, Rust):** Code is translated into machine code before execution, leading to faster programs.
    - #interpreted-language (Python, JavaScript):** Code is translated on-the-fly, sacrificing some speed for greater flexibility and development speed.

**Categories of Programming Languages**

Let's outline some broad categories to help you get a sense of the landscape:

- **General-purpose:** Designed for a wide range of applications (Python, Java, C++)
- **Domain-Specific:** Focused on a particular niche (SQL for databases, R for statistics)
- **Scripting:** Used to automate tasks or within larger applications (JavaScript, Bash)
- **System Programming:** Building systems like operating systems (C, C++ Rust)
- **Web Development:** Specialize in creating websites and web applications (HTML, CSS, JavaScript, PHP, React)

**The Beauty of Choice**

The beauty of this diversity is that we can select the best tool for the job. Think of a carpenter's toolbox – a hammer is fantastic for some tasks, but you'll need a saw and other specialized tools for different purposes. The same principle applies to programming languages!

Let me know if you'd like a deeper dive into specific language categories or examples of how different languages tackle real-world problems.