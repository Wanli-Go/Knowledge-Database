# But what is a computer?
#computer #software #hardware #instructions #programming

## Compute means calculation

If compute means calculation, then what is calculation? Well, there are some basic calculations that you must know: like addition, subtraction, multiplication. Maybe you know calculus. The key here is that **it takes a set of inputs and form an output**. In other words, you need some startup conditions like the numbers that need to be added, and you want someone to calculate the result of the addition operation for you. 

That someone that calculate the result for you, then, should be called "calculator". It can be a human, or it can be a machine.

## Computers are machines that does calculation for you

Human is both **smart and lazy**. That is the key reason of technology's development. Instead of doing the whole shit using their mind, they would rather find someone, or better, some automatic tools to calculate things for them. The introduction of steam engine, and later electricity, made people aware that such automatic tools are possible. They gave such automatic tools a nice name: **Machines**. 

Machines can be used in many fields like production, but mathematicians also needed machine calculators. *And such, the evolution of **computers** has begun*. If you're interested in its development, ask ChatGPT. Now you can understand that **computers are machines that does calculation for you**. But...

## Modern computers does more, but it start from calculations

We all know modern computers are capable of much more than just basic arithmetic operations. We can takes notes, play games, and even chat with people. However, this doesn't make a computer deviate from its original concept: a machine designed to perform calculations. 

In fact, the core #instructions of a modern CPU (Central Processing Unit, the heart of a modern computer) is still addition, subtraction, multiplication, division operations, together with some bitwise logical operations (0 AND 0 = 0, 0 AND 1 = 0, 0 OR 1 = 1).

The CPU communicates with input/output devices through I/O instructions. But under the #Von-Neumann architecture, CPUs have evolved to include a wide range of instructions beyond basic arithmetic operations, most notably the **interaction with memory**. Here's some example instructions (if you can't understand them all, don't worry):

| Instruction | Description                                                                             |
| ----------- | --------------------------------------------------------------------------------------- |
| MOV         | Move data between registers (the area in CPU that temporarily stores results) or memory |
| ADD         | Add two operands and store the result                                                   |
| SUB         | Subtract one operand from another and store the result                                  |
| JMP         | Unconditional jump to a specified address                                               |
| CMP         | Compare two operands                                                                    |
| JE          | Jump if equal (after comparison)                                                        |
| CALL        | Call a subroutine                                                                       |
| RET         | Return from a subroutine                                                                |

## Programs are a set of basic computer instructions

In a antique computer architecture (mid 20-century), you need to use punch cards and insert them into the computer to perform an instruction; you might need multiple instructions to get a result of a complex calculation (like numerical methods of solving equations). **Thinking of the right sequence of computer instructions to get your shit done are called programming**, because programming, in is original meaning, is planning.

But this manual punching work becomes extremely tedious. What if you can use a human-like language to talk to a computer? What if you can use digital information to store the instructions you created?

The genius Von Neumann thought of an idea: (Refer to [[Von Neumann Architecture]])
```markdown
Von Neumann's Solutions Overview

**Stored Program Concept:** Von Neumann proposed storing programs in the same memory as data. This meant a computer could be programmed to perform different tasks by simply changing the contents of its memory, eliminating the need for rewiring.
**Unified Memory:** He proposed a single, addressable memory to store **both data and instructions**. This eliminated the need for physically separating them, streamlining operation.
**The Central Processing Unit (CPU):** His design included a central processing unit responsible for fetching instructions from memory, decoding them, and performing computations.
**Input/Output (I/O)**: His model included mechanisms for inputting data into the machine and outputting the results, simplifying interaction with the computer.
```

With such architecture, you can store a sequence of instructions as a digital format. The **digital format of program, are called** #code. And with this architecture, we can finally separate software from hardware. Here's an example assembly code (x86 syntax) of adding two numbers, using the instructions we mentioned:

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

The code we just showed is an example of Assembly code, the very fundamental format of modern computer programs, and is designed for Von Neumann architecture computers. For more information, please go inside the [[Von Neumann Architecture]].

(p.s. There maybe something that is confusing: "system call", "kernel", etc.? That's OK, because these are some work that are done by the #operating-system, and operating systems itself are programs that can work closely with CPUs to do some trivial task for you. You can refer to [[Operating System Overview]] for more information, but it's OK to not understand these right now.)


## Summing up

- Computers evolved from the human desire to automate calculations. Originally just calculators, they've grown into powerful machines that still rely on basic arithmetic and logic instructions at their core.

- The Von Neumann architecture revolutionized computers, allowing stored programs (code) to modify their own behavior. 

- Under the background of modern computers, **programs, code, software are fundamentally the same thing**. "Programs" are more emphasized on the "set of instructions" nature; "code" are more focused on the digital representation; "software" are more oriented on its relativity to hardware (CPU, Memory, Hard Drives, I/O devices, etc.)

- Modern computers run complex programs, but their fundamental building blocks remain the simple operations that define their computational nature.