#strongly-typed #weakly-typed #programming-language 

# Strongly Typed Languages vs Weakly Typed Languages

(Generated by Gemini)
In programming, strong typing and weak typing refer to how strictly a language enforces data types for variables and expressions.

## Strongly Typed Languages

- **Meaning - Strict Type Rules:** These languages have a rigid type system. The data type of a variable must be declared explicitly and adhered to throughout the program. Or, the typed can be inferred from the right-side of "=", and it must be a concrete type.
- **Common Method - Compile-Time Type Checking:** The compiler performs rigorous checks **during compilation** to ensure type compatibility between operations and assignments. This helps catch potential errors early in the development process.
- **Aim - Type Safety:** Strongly typed languages aim for type safety, which guarantees that operations are performed only on compatible data types. This **reduces runtime errors and improves code reliability**.
- **Examples:** Java, C++, C#, Go, Dart, Rust.

## Weakly Typed Languages

- **Meaning - Flexible Type Conversions:** Weakly typed languages allow for more flexibility in data type manipulation. Implicit conversions between types might be possible, even if not ideal.
- **Common Method - Run-Time Type Checking:** Type checking often happens at runtime, which can lead to unexpected behavior if data types clash during program execution.
- **Examples:** JavaScript, Python, PHP.

## Choosing Between Strong and Weak Typing

- **Strong typing** is often preferred for large-scale, mission-critical systems where code reliability and maintainability are paramount. The stricter type system helps prevent errors and improves code clarity.
- **Weak typing** can be advantageous for **rapid prototyping**, scripting, and situations where flexibility and conciseness are valued. It allows for quicker development but requires more careful testing to ensure type compatibility.

## Static vs. Dynamic Typing

Static vs. Dynamic Typing is more well defined compared to strong & weak typing.

- **Dynamically typed** means that types are attached to values at run time, and an attempt to mix values of different types may cause a "run-time type error". For example, if in Scheme you attempt to add one to true by writing `(+ 1 #t)` this will cause an error. You encounter the error only if you attempt to execute the offending code.
    
- **Statically typed** means that types are checked at compile time, and a program that does not have a static type is rejected by the compiler. For example, if in ML you attempt to add one to true by writing `1 + true`, the program will be rejected with a (probably cryptic) error message. You always get the error even if the code might never be executed.

## Relationship between Compiled Languages vs Interpreted Languages

Well, you need a compiler for compile-time type checking, and that's one of compiler's job. Therefore, all statically-typed languages are compiled languages, and almost all dynamically-typed languages are interpreted languages.
## Blurred Lines

- **C**: C is statically-typed; however, it allows implicit type conversions, especially working with pointers (you can freely cast any pointer type to any other pointer type), and you can cast any type to any variables but with a warning. Therefore, it is weakly-typed language.
- **Hybrid languages:** Modern languages often blur the lines. Python, for instance, is dynamically typed but has added type hints for optional static type checking.
- **JIT Compilation:** Just-In-Time (JIT) compilation used in languages like Java and JavaScript can further complicate the traditional distinction between compiled and interpreted.
