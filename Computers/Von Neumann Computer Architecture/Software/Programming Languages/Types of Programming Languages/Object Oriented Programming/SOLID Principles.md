The SOLID principles are a set of five design principles aimed at making software designs more understandable, flexible, and maintainable. The principles are a subset of many principles promoted by American software engineer and instructor Robert C. Martin, also known as Uncle Bob. Here's a brief overview of each:

### 1. **Single Responsibility Principle (SRP)**
- **Definition**: A class should have one, and only one, reason to change.
- **Purpose**: This principle aims to reduce complexity by ensuring that a class is focused on doing one thing only. It helps in making the system easier to understand and maintain because changes to one responsibility should not affect those classes that have other responsibilities.
- Incorrect Example:
```java
public class User {
    private String name;
    private String email;

    public void saveUser() {
        // Code to save user to a database
    }

    public void sendEmail(String message) {
        // Code to send an email to the user
    }
    // getters and setters
}
```
The `User` class is responsible for both user attributes and actions that could be considered separate concerns: user data management and communication management.
- Correct Example:
```java
public class User {
    private String name;
    private String email;
    // getters and setters
}

public class UserRepository {
    public void saveUser(User user) {
        // Code to save user to a database
    }
}

public class EmailService {
    public void sendEmail(User user, String message) {
        // Code to send an email to the user
    }
}
```
### 2. **Open/Closed Principle (OCP)**
- **Definition**: Software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification.
- **Purpose**: The idea is to allow classes to be easily extended to accommodate new functionality but to be closed against modifications to existing code, which could introduce new defects. This is typically achieved through the use of interfaces or abstract classes.
- Incorrect Example:
```java
public class DiscountCalculator {
    public double calculateDiscount(String type, double price) {
        if (type.equals("STANDARD")) {
            return price * 0.1;
        } else if (type.equals("PREMIUM")) {
            return price * 0.2;
        }
        return 0;
    }
}
```
- Correct Example:
```java
interface Discount {
    double calculate(double price);
}

class StandardDiscount implements Discount {
    public double calculate(double price) {
        return price * 0.1;
    }
}

class PremiumDiscount implements Discount {
    public double calculate(double price) {
        return price * 0.2;
    }
}

public class DiscountCalculator {
    public double calculateDiscount(Discount discount, double price) {
        return discount.calculate(price);
    }
}
```
### 3. **Liskov Substitution Principle (LSP)**
- **Definition**: Objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program.
- **Purpose**: This principle ensures that a subclass can stand in for its superclass. The principle is crucial for achieving polymorphic behavior in object-oriented systems.
- Incorrect Example:
```java
public class Rectangle {
    protected int width;
    protected int height;

    public void setWidth(int width) {
        this.width = width;
    }

    public void setHeight(int height) {
        this.height = height;
    }

    public int getArea() {
        return width * height;
    }
}

public class Square extends Rectangle {
    public void setWidth(int width) { // Different Behaviour from Parent class
        this.width = this.height = width;
    }

    public void setHeight(int height) { // Different Behaviour from Parent class
        this.height = this.width = height;
    }
}
```
- Correct Example:
```java
public interface Shape {
    int getArea();
}

public class Rectangle implements Shape {
    protected int width;
    protected int height;

    public Rectangle(int width, int height) {
        this.width = width;
        this.height = height;
    }

    public int getArea() {
        return width * height;
    }
}

public class Square implements Shape {
    private int side;

    public Square(int side) {
        this.side = side;
    }

    public int getArea() {
        return side * side;
    }
}
```
### 4. **Interface Segregation Principle (ISP)**
- **Definition**: No client should be forced to depend on methods it does not use.
- **Purpose**: This principle aims at splitting a set of actions into smaller interfaces so that a class doesn’t need to implement interfaces it doesn’t use. It encourages finer-grained interfaces that are client-specific, rather than one large, general-purpose interface.
- Incorrect Example:
```java
public interface MediaPlayer {
    void playAudio();
    void playVideo();
}

// A class that only needs to play audio might still have to implement the `playVideo` method, which violates ISP.
public class AudioPlayer implements MediaPlayer {
    public void playAudio() {
        // Play audio
    }

    public void playVideo() {
        throw new UnsupportedOperationException();
    }
}
```
- Correct Example:
```java
public interface AudioPlayer {
    void playAudio();
}

public interface VideoPlayer {
    void playVideo();
}

public class OnlyAudioPlayer implements AudioPlayer {
    public void playAudio() {
        // Play audio
    }
}
```
### 5. **Dependency Inversion Principle (DIP)**
- **Definition**: High-level modules should not depend on low-level modules. Both should depend on **abstractions**. Additionally, abstractions should not depend on details; details should depend on abstractions.
- **Purpose**: This principle aims at reducing dependencies among the code modules. The main idea is to decouple high-level components from low-level components to make the system more reusable and robust.
- Incorrect Example:
```java
class Disk {
    String read() {
        // Reads data from the disk
        return "data from disk";
    }
}

class FileReader {
    Disk disk = new Disk();

    String fetchData() {
        return disk.read();
    }
}
```
- Correct Example:
```java
interface DataSource {
    String read();
}

class Disk implements DataSource {
    public String read() {
        // Reads data from the disk
        return "data from disk";
    }
}

class Network implements DataSource {
    public String read() {
        // Fetches data from a network location
        return "data from network";
    }
}

class FileReader {
    private DataSource dataSource;

    public FileReader(DataSource dataSource) {
        this.dataSource = dataSource;
    }

    String fetchData() {
        return dataSource.read();
    }
}
```

Applying the SOLID principles can lead to better software design that is easier to understand, modify, and extend. However, it's also important to apply these principles judin a way that is appropriate to the context of the project. Over-application can lead to unnecessary complexity.