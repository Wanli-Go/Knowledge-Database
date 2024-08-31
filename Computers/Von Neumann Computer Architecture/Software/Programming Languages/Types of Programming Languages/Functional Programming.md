# Functional Programming

#FP #programming-language 

Functional programming is a different way of thinking about problems. It is a way of approaching problems by treating computation **as applying functions to data**. Unlike traditional programming that focuses on changing state, functional programming emphasizes **pure functions and immutability**.
## Example: Swift
Here are some key concepts in Swift's functional programming world:

1. **Pure Functions:** These are the building blocks. A pure function always produces the same output for the same input, with no side effects like modifying global variables or printing to the console. This makes them predictable and easy to test.
``` Swift
func add(x: Int, y: Int) -> Int {
  return x + y
}

let result = add(x: 5, y: 3) // result will always be 8
```

2. **Immutability:** Functional programming prefers working with data that doesn't change after creation. Swift uses `let` constants instead of `var` variables **whenever possible** to enforce this. You create a new version of the data with the changes, rather than modifying the original.
```swift
struct Person {
    let name: String
    let age: Int
}

var john = Person(name: "John", age: 30)

// Attempting to directly change a property will fail (good!):
// john.age = 31  // Error: Cannot assign to 'age' in 'john'

// To represent a change, create a new instance:
let updatedJohn = Person(name: "John", age: 31) 
```
    
3. **Higher-Order Functions:** These functions take other functions as arguments or return functions as results. This allows you to write more generic and reusable code.
```swift
func apply(operation: (Int) -> Int, to value: Int) -> Int {
  return operation(value)
}

let doubled = apply(operation: { $0 * 2 }, to: 10) // doubled will be 20
```

4. **Closures:** Closures are anonymous functions that can capture variables from their surrounding context. They are a powerful tool for expressing concise and flexible functionality.
```swift
let numbers = [2, 4, 6, 8]

let evenNumbers = numbers.filter { mynum in 
    mynum % 2 == 0
} // [2, 4, 6, 8]

// The closure is: { mynum in mynum % 2 == 0 }
```
The `filter` method takes a closure as an argument. The closure captures the idea of an "even number" from within the filter function. It has access to the external variable `number`.
    
5. **Functional Collection Operations:** Swift provides functions like `map`, `filter`, and `reduce` to operate on collections without explicitly using loops. These functions make your code more declarative, focusing on what you want to achieve rather than how.
    

By incorporating these concepts, you can write cleaner, more concise, and easier-to-reason-about Swift code. Functional programming offers advantages like:

- **Improved Testability:** Pure functions are deterministic, making them simpler to test with predictable inputs and outputs.
- **Reduced Errors:** Immutability helps prevent unexpected side effects that can lead to bugs.
- **Parallelization Potential:** Functional code can often be easily parallelized for improved performance.

## Functional Programming vs OOP

1. **Focus on Data vs. Behavior**
    
    - **OOP:** OOP is about bundling data (class attributes) together with behavior (methods). Objects encapsulate the state and operations that can be **performed on their data**. This means the internal states can change over time; methods often exist to modify this state explicitly.
        
    - **FP:** Functional programming **puts data at the forefront**. It models **problems as transformations of data**, using functions as the primary units of computation. Functional programming favors immutability. Instead of modifying objects in-place, functions **create new data structures to represent transformations**.
        
2. **Organization**
    
    - **OOP:** Code organization revolves around classes and objects. These act as templates, and objects are the actual instances during program execution. Relationships are modeled through inheritance and interactions between objects.
        
    - **FP:** Functions are the primary building blocks. Complex logic is built by composing smaller functions, often using higher-order functions that manipulate other functions.
        

**Illustrative Example (Conceptual)**

Imagine representing a 'car' in a program:

- **OOP:** You might have a `Car` class with properties like `color`, `speed`, and methods like `accelerate()`, `brake()`, and `turn()`. The `accelerate()` method likely modifies the car object's speed.
```swift
class Car {
  var color: String
  var speed: Int

  init(color: String, speed: Int) {
    self.color = color
    self.speed = speed
  }

  func accelerate(by amount: Int) {
    speed += amount 
  }

  func brake(by amount: Int) {
    speed -= amount
    if speed < 0 { speed = 0 } // Ensure speed doesn't go negative
  }
}

// Usage
let myCar = Car(color: "Red", speed: 0)
myCar.accelerate(by: 20)
print(myCar.speed) // Output: 20
```
    
- **FP:** You might have a `Car` data structure representing the car's properties. Functions like `accelerateCar(car, accelerationAmount)` would take a `car` and return a _new_ `car` data structure with the updated speed, leaving the original unchanged.
```swift
struct Car {
  let color: String
  let speed: Int
}

func accelerate(car: Car, by amount: Int) -> Car {
  return Car(color: car.color, speed: car.speed + amount) 
}

func brake(car: Car, by amount: Int) -> Car {
  let newSpeed = car.speed - amount
  return Car(color: car.color, speed: max(0, newSpeed)) // No negative speed
}

// Usage
let myCar = Car(color: "Red", speed: 0)
let acceleratedCar = accelerate(car: myCar, by: 20)
print(acceleratedCar.speed) // Output: 20 

```

## Summing Up

- OOP centers around the idea of **mutable objects** with encapsulated behavior.
- FP emphasizes **data flows, immutability**, and the composition of functions.