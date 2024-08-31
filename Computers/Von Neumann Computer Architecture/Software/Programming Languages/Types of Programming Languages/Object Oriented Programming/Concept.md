# Objected Oriented Programming (OOP)

#OOP #programming-language 

You must have heard of this shit about objected oriented programming, which is called "encapsulation", "inheritance", and "polymorphism". But learning these won't tell you why you need Object-Oriented Programming.

Consider this example in C that calculates the area and perimeter of a shape:
```c
#include <stdio.h>

// Functions for square
int is_tangible_square_shape(){
	return 1;
}

float calculate_square_shape_area(float side) {
    return side * side;
}

float calculate_square_shape_perimeter(float side) {
    return 4 * side;
}

// Functions for rectangle
int is_tangible_rectangle_shape(){
	return 1;
}

float calculate_rectangle_shape_area(float length, float width) {
    return length * width;
}

float calculate_rectangle_shape_perimeter(float length, float width) {
    return 2 * (length + width);
}

int main() {
    char shapeType;
    float side, length, width;

    printf("Enter shape type (s for square, r for rectangle): ");
    scanf("%c", &shapeType);

    if (shapeType == 's') {
        printf("Enter side: ");
        scanf("%f", &side);
        printf("Area: %.2f\n", calculate_square_shape_area(side));
        printf("Perimeter: %.2f\n", calculate_square_shape_perimeter(side));
    } else if (shapeType == 'r') {
        printf("Enter length and width: ");
        scanf("%f %f", &length, &width);
        printf("Area: %.2f\n", calculate_rectangle_shape_area(length, width));
        printf("Perimeter: %.2f\n", calculate_rectangle_shape_perimeter(length, width));
    } else {
        printf("Invalid shape type.\n");
    }

    return 0;
}
```
C does not have any namespace, which means every function you write have to **not collide** with other function names. This sucks, because if the project grows large, you may have to write very-very long function names, and write a ton of "if shapeType = 'xxx'".

What OOP encourages is that you **put the operation to the object (such as the shapes) within the object itself**, and when there are **common methods** for different class objects, you can **put it in a parent class or an interface**: 

```java
// Shape.java (Abstract base class)
abstract class Shape {
	private bool tangible;

	public Shape(bool tangible){
		this.tangible = tangible;
	}
	
	public bool is_tangible(){
		return tangible;
	}
    public abstract float calculateArea();
    public abstract float calculatePerimeter();
}

// Square.java
class Square extends Shape {
    private float side;

    public Square(float side) {
	    super(true); // is a tangible shape
        this.side = side;
    }

    @Override
    public float calculateArea() {
        return side * side;
    }

    @Override
    public float calculatePerimeter() {
        return 4 * side;
    }
}

// Rectangle.java (similar to Square.java)

// EntryPoint.java
public class EntryPoint {
    public static void main(String[] args) {
        // ... (input code similar to C)
        Shape shape;

        if (shapeType == 's') {
            shape = new Square(side);
        } else if (shapeType == 'r') {
            shape = new Rectangle(length, width);
        } else {
           // ...
        }

        System.out.println("Area: " + shape.calculateArea());
        System.out.println("Perimeter: " + shape.calculatePerimeter());
        // Notice you don't have to call separate function names
    }
}

```


## Modularity, Code Reusability, Abstraction
Forget the last 2 features (Code Reusability and Abstraction) because it is also the feature of **functions**. The key thing OOP promotes is **modularity**, and it is the natural way of human thinking and is easier to understand. Many #design-pattern s facilitate this modularity such as Mediator, Facade, etc.; The #SOLID principles provides further specification for this modularity. Please refer to


## Summing Up

- Object-Oriented Programming (OOP) brings powerful concepts like inheritance, encapsulation, and polymorphism to structure code for large, complex problems.  
- Inheritance promotes code reusability, encapsulation protects data integrity, and polymorphism allows for adaptable functions that work seamlessly with different object types. These concepts make code cleaner, easier to maintain, and better able to handle real-world scenarios with flexibility.