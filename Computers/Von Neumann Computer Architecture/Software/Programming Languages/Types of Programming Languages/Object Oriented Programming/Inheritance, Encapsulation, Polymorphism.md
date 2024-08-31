# Inheritance, Encapsulation, Polymorphism

## Inheritance

Inheritance is essentially saying "when there are **common methods** for different class objects, you can **put it in a parent class or an interface**". And why they would have common methods for different objects? Because they're in a same family, of course! Because square and circle both **are** shapes [[Concept]].



That is **Inheritance**.


## Encapsulation

And what is encapsulation? You put the functions related to the class objects in the class itself. Oh, because you put the functions that **modifies** the properties of the class object, you can hide the variable fields and keep them from being directly modified. 

Consider a simple banking scenario:

```c
#include <stdio.h>

struct Account {
    float balance; // Uh oh, balance is directly accessible
};

void deposit(struct Account *account, float amount) {
    account->balance += amount;
}

void withdraw(struct Account *account, float amount) {
    if (account->balance >= amount) {
        account->balance -= amount;
    } else {
        printf("Insufficient funds.\n");
    }
}

int main() {
    struct Account myAccount;
    myAccount.balance = 100.00; 

    deposit(&myAccount, 50.00); 

    myAccount.balance = -1000.00; // Negative balance? No problem!

    return 0;
}
```

When writing the main function, the line `myAccount.balance = -1000.00` is OK, which not OK! How can you just modify the bank account's balance? There should only be 2 ways to change its value: withdraw or deposit. Therefore, this code is unsafe. But in OOP languages, you can set those fields to *private* so only appropriate methods can modify them.



That is **encapsulation**.


## Polymorphism

Go back to the Shape.java and Square.java in [[Concept]]. See this word? `@Override`. That means you are rewriting the methods defined in the parent class. And because the parent class has some unimplemented methods (marked with the **abstract** keyword), you must implement (rewrite) them in the child class. 



That is **polymorphism**.



Actually that is **one** form of polymorphism called **method overriding**; another form of polymorphism is **method overloading**. It allows you to have multiple methods with the **same name**, but different "signatures" (different parameter lists). The magic is that the right method is chosen for you at compile time based on the number of arguments you provide.

```java
class Calculator {
    // Overloaded sum methods
    public int sum(int num1, int num2) { // the int version 
        return num1 + num2;
    }

    public double sum(double num1, double num2) { // the double version
        return num1 + num2;
    }

    public int sum(int num1, int num2, int num3) { // the three-argument version
        return num1 + num2 + num3;
    }
    
    public static void main(String[] args){
        Calculator calculator = new Calculator();
		System.out.println(calculator.sum(5, 10));        // calls the int version 
		System.out.println(calculator.sum(5.5, 2.3));    // calls the double version
		System.out.println(calculator.sum(2, 5, 8));      // calls the three-argument version
    }
}
```



There is actually another polymorphism called **parametric polymorphism**, meaning you can use a **generic type** (as long as they implement a certain interface of inherit a certain parent class) for a method or a class:

```java
import java.util.ArrayList;
import java.util.List;

public class ParametricExample {

    public static void main(String[] args) {
        // List of Strings
        List<String> names = new ArrayList<>();
        names.add("Alice");
        names.add("Bob");

        // List of Integers
        List<Integer> numbers = new ArrayList<>();
        numbers.add(10);
        numbers.add(20);

        printElements(names); 
        printElements(numbers); 
    }

    // Generic method that works with lists of any type. The generic type is denoted as "T", but it can be any other name.
    public static <T> void printElements(List<T> list) {
        for (T element : list) {
            System.out.println(element);
        }
    }
}
```

