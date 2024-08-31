**The time when human learned how to communicate with a computer, they had set a journey that will never be the same.**
# The essence of computer programming
#compiler #interpreter #programming-language #assembly #programming 

## But what is a computer program?

It is something that runs in a computer. Yes. That's what a program means.
(***Warning**: Historical Content*) The word "program" goes back centuries, with its origin in Latin "programma" which means "a proclamation" or "public notice". In English, it came to mean a plan of action or a course of study. This meaning fits well with the modern definition of a computer program - a detailed plan, or, **a set of instructions for the computer to follow**.

## Computers can speak Assembly, but human can't (SAD!)

We know that modern computers can run a set of basic instructions to perform the a complex task. We used the example of assembly code, which directly translates to machine code instructions, telling exactly how to CPU should work step-by-step:

```assembly
_start:
    MOV eax, 5      ; Move 5 into the eax register
    MOV ebx, 3      ; Move 3 into the ebx register
    ADD eax, ebx    ; Add ebx to eax, storing the result in eax
    ; eax now contains the sum (8)
    
    ; Exit the program
    MOV eax, 1      ; System call number for exit
    XOR ebx, ebx    ; Exit status 0
    INT 0x80        ; Call the kernel to exit
```

But we call know they are not very comfortable to read. Instead, you might prefer:
```Javascript
let a = 5; let b = 3; a = a + b // a now should be 8
```

or even let computer output some shit:
```Some-custom-programming-language
say hello world!
```

But sadly, computers does not have the superpower of directly run these English-like commands. These are called #high-level-language, and you need a **translator** to convert such commands to assembly code, which can be understood by the CPU. Assembly code is called a #low-level-language because it involve direct CPU instructions and memory operations. 

p.s. If you're a computer father who speaks Assembly as your first language, you may not need such translators.

## Let's start with C, the OG programming language

Compared to Assembly, C is much more readable:

```c
#include <stdio.h>

int main(){
	int a = 6;
	int b = 9;
	printf("%d", a + b); // Outputs 15 at console
}
```

Oh! But what is console? This shit opens another whole chapter, but it's not really that important now. If you're really interested, just refer to [[Operating System Overview]]. For now, you only need to know that this code wants to show you the result of adding 6 to 9.

Anyways, C is indeed much more readable. It is concise and clean, even more efficient than human language (in which case, you need to say "There are 2 numbers, each called a and b, and a is 6, and b is 9; computer-san, tell me what's the result of adding a to b.")

As we mentioned, CPU can only understand a fixed set of basic instructions (Assembly). You now would dream of translating those C code into Assembly:

```Assembly
section .data        ; Data section
    fmt: db "%d", 10, 0  ; Format string for printf

section .text        ; Code section
global main          ; main function needs to be globally visible

main:
    mov     eax, 6   ; Load value 6 into %eax (represents variable 'a')
    mov     ebx, 9   ; Load value 9 into %ebx (represents variable 'b')
    add     eax, ebx ; Add contents of %ebx to %eax (result of a + b)
    push    rax      ; Push the result onto the stack 
    push    fmt      ; Push the format string onto the stack
    call    printf   ; Call printf (exists in a standalone library)
    add     esp, 8   ; Clean up the stack (8 bytes for two pushed dwords) 
    mov     eax, 0   ; Return value 0 
    ret              ; Return from main
```

If you can't comprehend this, it means you're human. To do this translation work, the C language uses a separate program called a #compiler. Not too much magic here, because the compiler is really just about translating C into Assembly. The full compilation system involves more, like locating the code of the printf function, but this gives you a general idea and startup. For more information, you can refer to the book [Computer Systems: A Programmers' Perspective](C:\Users\xingw\Desktop\拡張　かくちょう\【1】深入理解计算机系统(中文版).pdf) Section 1.2.

## Compiled Languages vs Interpreted Languages: Translators with Different Approaches

Ok, so we figured out C needs a compiler to be translated into Assembly for the CPU to understand. This means it's a #compiled-language. The main characteristic of compiled languages is that they have **separate files** for source code (written in C) and executable programs (assembly).
But there's another way to get the job done: directly execute the source code.

**Interpreted Languages: The On-the-Fly Translators**

Think of an #interpreter  like a simultaneous translator at a United Nations meeting. They listen to the original language and immediately convert it to a different language for the audience. Interpreted programming languages work similarly. For example, with Python:

```
# main.py
print("Hello, world!")
```

The **Python Interpreter** does the following: 
1. **Reads the Line:** It grabs the instruction `print("Hello, world!")`
2. **Understands the Intent:** "Ah, the human wants to display some text!"
3. **Converts to Internal Actions:** The interpreter figures out the necessary low-level assembly code to make the text appear on the screen.
4. **Executes:** The interpreter tells the computer to do those actions.
5. **Go to the Next Line**: If the file is not ended, the interpreter goes to the next line to perform the same read-and-execute process.

#interpreted-language  doesn't have a separate executable file; instead, the interpreter executes the raw python script, going through and translate each line one by one. Interpreted languages are also called **scripting languages**.

### Why do we need interpreted languages?
- **Better debugging**. When the program goes wrong, the interpreter can identify the line that's being executed when it goes wrong and can be easily traced.
- Every time you change the code, compiled languages **recompile the whole file**, even for the part you don't necessarily execute every time. This can make interpreted languages a little faster for development. Oh, not to mention you don't need to click 2 separate buttons: "compile" and "run".

### Can't We Have The Best of Both Worlds?
Some languages like #Java and #C-sharp use clever tricks. They have a compiler to translate the code into an intermediate form called "bytecode". Then, a separate program called a "**virtual machine**" ( #JVM) acts as a **super-fast interpreter for this bytecode**. It's a compromise between speed and flexibility.

## Summing Up

- A program is a set of instructions for the computer to follow.
- High-level languages which looks like English need to be translated into low-level language (i.e. assembly).
	- **Compiled Languages:** Translate your code into machine language _before_ running it, like preparing a whole translated book in advance.
	- **Interpreters:** Translate your code line-by-line as it runs, like a real-time language interpreter.

## Index of Programming Languages
Java: [[1. Welcome Page to Java]]
