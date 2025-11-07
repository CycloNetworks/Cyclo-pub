# Cyclo Programming Language

<div align="center">

**A modern, statically-typed programming language with clean syntax and LLVM-powered performance**

[![Version](https://img.shields.io/badge/version-7.1-blue.svg)](https://github.com/Cyclolysisss/CycloLLVM)
[![LLVM](https://img.shields.io/badge/LLVM-17+-orange.svg)](https://llvm.org)

[Quick Start](#quick-start) • [Documentation](#documentation) • [Examples](#examples) • [Contributing](#contributing)

</div>

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Quick Start](#quick-start)
- [Installation](#installation)
- [Language Basics](#language-basics)
    - [Data Types](#data-types)
    - [Variables](#variables)
    - [Operators](#operators)
    - [Control Flow](#control-flow)
    - [Functions](#functions)
    - [Classes](#classes)
- [Console I/O](#console-io)
- [Examples](#examples)
- [Compiler Usage](#compiler-usage)
- [Best Practices](#best-practices)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [License](#license)

---

## 🎯 Overview

**Cyclo** is a statically-typed, compiled programming language designed for clarity, performance, and developer productivity. Built on LLVM infrastructure, Cyclo combines modern language features with native execution speed.

### Why Cyclo?

- 🚀 **Fast Compilation** - Two-pass compilation with LLVM optimization
- 📝 **Clear Syntax** - Readable code that expresses intent
- 🔒 **Type Safety** - Static typing catches errors at compile time
- 🎯 **Zero-Cost Abstractions** - High-level features with no runtime overhead
- 🛠️ **Powerful Tooling** - Detailed error messages and debugging support

---

## ✨ Features

| Feature | Status | Description |
|---------|--------|-------------|
| Static Typing | ✅ | Compile-time type checking |
| LLVM Backend | ✅ | Native code generation |
| Object-Oriented | ✅ | Classes with inheritance |
| Functions | ✅ | First-class functions with recursion |
| Control Flow | ✅ | if/else, for, while loops |
| Console I/O | ✅ | Built-in input/output (Con.Read/print/println) |
| Error Handling | ✅ | Detailed compile-time diagnostics |
| Scope Management | ✅ | Block-level scoping |
| Type Inference | 🚧 | Partial support |
| Standard Library | 🚧 | In development |

---

## 🚀 Quick Start

### Hello World

Create `hello.cyc`:

```cyclo
pub stc empty main(str:[] args) {
    Con.println("Hello, Cyclo! 🚀");
}
```

Compile and run:

```bash
./CycloC-[YOUR_PLATRORM]-[YOUR_ARCH] hello.cyc
# or (Windows)
CycloC-Win-[YOUR_ARCH].exe hello.cyc

./hello 
# or (Windows)
hello.exe
```

**Output:**
```
Hello, Cyclo! 🚀
```

### Interactive Example

```cyclo
pub stc empty main(str:[] args) {
    int:age == 0;
    str:name == "";
    
    Con.println("What's your name?");
    Con.Read(str:name);
    
    Con.println("How old are you?");
    Con.Read(int:age);
    
    Con.print("Hello, ");
    Con.print(str:name);
    Con.print("! You are ");
    Con.print(int:age);
    Con.println(" years old.");
    
}
```

---

## 💿 Installation

### Prerequisites

- **A Computer** 
- **An Internet Connection** To Download the Compiler

### GNU/Linux (Ubuntu, Fedora, Arch, ...)

```bash

# Clone repository
git clone https://github.com/CycloNetworks/Cyclo-pub.git
cd Cyclo-pub

# Use the executable
./CycloC-Linux-[YOUR_ARCH]
```

### Apple macOS

```bash
# Clone repository
git clone https://github.com/CycloNetworks/Cyclo-pub.git
cd Cyclo-pub

# Use the executable
./CycloC-OSX-[YOUR_ARCH]
```

### Microsoft Windows

```bash
# 1. Download the file CycloC-Win-[YOUR_ARCH].exe on your favorite web browser
# 2. Open a CMD window and go to the folder using 
cd C:\Users\[YOUR_USERNAME]\Cyclo-pub\
# 3. Run the executable file with
CycloC-Win-[YOUR_ARCH]

```

---

## 📚 Language Basics

### Data Types

Cyclo supports six primitive types:

| Type | Keyword | Size | Range | Example |
|------|---------|------|-------|---------|
| **Integer** | `int` | 32-bit | -2³¹ to 2³¹-1 | `42`, `-10` |
| **Float** | `flt` | 32-bit | IEEE 754 | `3.14`, `-0.5` |
| **Double** | `dbl` | 64-bit | IEEE 754 | `3.14159265359` |
| **String** | `str` | Variable | UTF-8 | `"Hello"` |
| **Boolean** | `bln` | 1-bit | true/false | `true`, `false` |
| **Void** | `empty` | - | No value | Function returns |

#### Type Declaration Examples

```cyclo
int:count == 42;
flt:temperature == 98.6;
dbl:pi == 3.14159265359;
str:message == "Hello, World!";
bln:is_valid == true;
```

---

### Variables

#### Declaration and Initialization

**Syntax:** `type:name == value;`

```cyclo
// Basic declaration
int:age == 25;
str:name == "Alice";
flt:price == 19.99;

// Multiple variables
int:x == 10;
int:y == 20;
int:sum == x + y;
```

#### Assignment

After declaration, use `=` (single equals) for assignment:

```cyclo
int:counter == 0;    // Declaration with ==
counter = 5;         // Assignment with =
counter = counter + 1;
```

#### Scope Rules

```cyclo
pub stc empty main(str:[] args) {
    int:global_var == 100;    // Function scope
    
    if (global_var > 50) {
        int:local_var == 200;  // Block scope
        Con.println(int:local_var);
    }
    
    // ❌ local_var not accessible here
    
    for (int:i == 0; i < 5; i += 1) {
        int:loop_var == i * 2;  // Loop scope
    }
    
    // ❌ i and loop_var not accessible here
    
   
}
```

---

### Operators

#### Arithmetic Operators

| Operator | Operation | Example | Result |
|----------|-----------|---------|--------|
| `+` | Addition | `5 + 3` | `8` |
| `-` | Subtraction | `5 - 3` | `2` |
| `*` | Multiplication | `5 * 3` | `15` |
| `/` | Division | `15 / 3` | `5` |
| `%` | Modulo | `17 % 5` | `2` |

```cyclo
int:a == 10;
int:b == 3;

int:sum == a + b;         // 13
int:diff == a - b;        // 7
int:product == a * b;     // 30
int:quotient == a / b;    // 3
int:remainder == a % b;   // 1
```

#### Comparison Operators

| Operator | Meaning | Example | Result |
|----------|---------|---------|--------|
| `==` | Equal to | `5 == 5` | `true` |
| `!=` | Not equal | `5 != 3` | `true` |
| `<` | Less than | `3 < 5` | `true` |
| `>` | Greater than | `5 > 3` | `true` |
| `<=` | Less or equal | `5 <= 5` | `true` |
| `>=` | Greater or equal | `5 >= 3` | `true` |

```cyclo
int:x == 10;
int:y == 20;

if (x < y) {
    Con.println("x is less than y");
}

if (x != y) {
    Con.println("x is not equal to y");
}
```

#### Compound Assignment

| Operator | Equivalent | Example |
|----------|------------|---------|
| `+=` | `a = a + b` | `x += 5` |
| `-=` | `a = a - b` | `x -= 3` |
| `*=` | `a = a * b` | `x *= 2` |
| `/=` | `a = a / b` | `x /= 4` |
| `++` | `a = a + 1` | `x++` |
| `--` | `a = a - 1` | `x--` |

```cyclo
int:score == 100;
score += 50;     // score = 150
score -= 20;     // score = 130
score *= 2;      // score = 260
score /= 10;     // score = 26
score++;         // score = 27
score--;         // score = 26
```

---

### Control Flow

#### If-Else Statements

```cyclo
// Simple if
if (condition) {
    // code
}

// If-else
if (condition) {
    // true branch
} else {
    // false branch
}

// Nested if-else
if (score >= 90) {
    Con.println("Grade: A");
} else {
    if (score >= 80) {
        Con.println("Grade: B");
    } else {
        if (score >= 70) {
            Con.println("Grade: C");
        } else {
            Con.println("Grade: F");
        }
    }
}
```

#### While Loops

```cyclo
// Basic while loop
int:count == 0;
while (count < 5) {
    Con.println(int:count);
    count += 1;
}

// Countdown
int:timer == 10;
while (timer > 0) {
    Con.println(int:timer);
    timer -= 1;
}
Con.println("Blast off! 🚀");
```

#### For Loops

**Syntax:** `for (type:var == init; condition; increment) { }`

```cyclo
// Basic for loop
for (int:i == 0; i < 10; i += 1) {
    Con.println(int:i);
}

// Countdown
for (int:i == 10; i > 0; i -= 1) {
    Con.println(int:i);
}

// Step by custom increment
for (int:i == 0; i < 100; i += 10) {
    Con.println(int:i);
}

// Nested loops (multiplication table)
for (int:i == 1; i <= 5; i += 1) {
    for (int:j == 1; j <= 5; j += 1) {
        int:product == i * j;
        Con.print(int:product);
        Con.print("\t");
    }
    Con.println("");
}
```

---

### Functions

#### Function Declaration

**Syntax:**
```cyclo
[pub|prv|pro] [stc] fn return_type function_name(parameters) {
    // function body
    rtn value;
}
```

**Modifiers:**
- `pub` - Public (accessible everywhere)
- `prv` - Private (file scope)
- `pro` - Protected (class scope)
- `stc` - Static (no instance needed)
- `fn` - Function keyword
- `rtn` - Return keyword

#### Basic Functions

```cyclo
// Function with parameters
stc int add(int:a, int:b) {
    rtn a + b;
}

// Function with no parameters
stc empty greet() {
    Con.println("Hello, Cyclo!");
}

// Function returning nothing (void)
stc empty print_divider() {
    Con.println("========================");
}

// Using functions
pub stc empty main(str:[] args) { 
    int:result == add(10, 20);
    Con.println(int:result);
    
    greet();
    print_divider();
    
}
```

#### Recursive Functions

```cyclo
// Factorial
stc int factorial(int:n) {
    if (n <= 1) {
        rtn 1;
    }
    rtn n * factorial(n - 1);
}

// Fibonacci
stc int fibonacci(int:n) {
    if (n < 2) {
        rtn n;
    }
    rtn fibonacci(n - 1) + fibonacci(n - 2);
}

// Power function
stc int power(int:base, int:exp) {
    if (exp == 0) {
        rtn 1;
    }
    rtn base * power(base, exp - 1);
}
```

#### The main() Function

Every Cyclo program requires a `main()` function:

```cyclo
pub stc empty main(str:[] args) {
    // Program entry point
    // Your code here
}
```

---

### Classes

#### Class Declaration

```cyclo
[pub|prv|pro] class ClassName {
    // Constructor
    ClassName(parameters) : BaseClass {
        // initialization
    }
    
    // Methods
    [pub|prv|pro] [stc] fn return_type method_name(parameters) {
        // method body
    }
}
```

#### Basic Class Example

```cyclo
pub class Person {
    // Constructor
    Person(str:name, int:age) {
        // Initialize fields
    }
    
    // Static method
    pub stc fn empty greet() {
        Con.println("Hello from Person class!");
    }
    
    // Instance method
    pub fn empty introduce() {
        Con.println("I am a person.");
    }
}
```

#### Class Inheritance

```cyclo
// Base class
pub class Animal {
    Animal(str:name) {
        // Initialize animal
    }
    
    pub stc fn empty make_sound() {
        Con.println("Some generic animal sound");
    }
}

// Derived class
pub class Dog : Animal {
    Dog(str:name, str:breed) : Animal {
        // Initialize dog-specific fields
    }
    
    pub stc fn empty make_sound() {
        Con.println("Woof! 🐕");
    }
}
```

---

## 🖥️ Console I/O

### Output Methods

#### `Con.print(type:value)`
Prints without newline:

```cyclo
Con.print("Hello");
Con.print(" ");
Con.print("World");
// Output: Hello World
```

#### `Con.println(type:value)`
Prints with newline:

```cyclo
Con.println("First line");
Con.println("Second line");
// Output:
// First line
// Second line
```

#### Printing Variables

Always specify the type prefix:

```cyclo
int:age == 25;
str:name == "Alice";
flt:price == 19.99;

Con.println(int:age);       // Output: 25
Con.println(str:name);      // Output: Alice
Con.println(flt:price);     // Output: 19.99
```

#### Printing Expressions

```cyclo
int:x == 10;
int:y == 20;

Con.println(int:x + y);           // Output: 30
Con.println(int:x * 2);           // Output: 20
Con.println(int:(x + y) / 2);     // Output: 15
```

### Input Methods

#### `Con.Read(type:variable)`
Reads input from stdin:

```cyclo
// Reading an integer
int:age == 0;
Con.println("Enter your age:");
Con.Read(int:age);

// Reading a string
str:name == "";
Con.println("Enter your name:");
Con.Read(str:name);

// Reading a float
flt:price == 0.0;
Con.println("Enter the price:");
Con.Read(flt:price);

// Reading a boolean (0 = false, 1 = true)
bln:is_valid == false;
Con.println("Enter 1 for true, 0 for false:");
Con.Read(bln:is_valid);
```

### Complete I/O Example

```cyclo
pub stc empty main(str:[] args) {
    str:name == "";
    int:age == 0;
    int:birth_year == 2025;
    
    Con.println("=== User Registration ===");
    
    Con.print("Enter your name: ");
    Con.Read(str:name);
    
    Con.print("Enter your age: ");
    Con.Read(int:age);
    
    Con.println("");
    Con.println("=== Registration Complete ===");
    Con.print("Welcome, ");
    Con.print(str:name);
    Con.println("!");
    
    int:year_born == birth_year - age;
    Con.print("You were born in approximately ");
    Con.println(int:year_born);
    
}
```

---

## 📖 Examples

### Example 1: FizzBuzz

```cyclo
pub stc empty main(str:[] args) {
    for (int:i == 1; i <= 100; i += 1) {
        int:mod3 == i % 3;
        int:mod5 == i % 5;
        
        if (mod3 == 0) {
            if (mod5 == 0) {
                Con.println("FizzBuzz");
            } else {
                Con.println("Fizz");
            }
        } else {
            if (mod5 == 0) {
                Con.println("Buzz");
            } else {
                Con.println(int:i);
            }
        }
    }
}
```

### Example 2: Prime Number Checker

```cyclo
stc int is_prime(int:n) {
    if (n < 2) {
        rtn 0;
    }
    
    if (n == 2) {
        rtn 1;
    }
    
    if (n % 2 == 0) {
        rtn 0;
    }
    
    int:i == 3;
    while (i * i <= n) {
        if (n % i == 0) {
            rtn 0;
        }
        i += 2;
    }
    
    rtn 1;
}

pub stc empty main(str:[] args) {
    Con.println("Prime numbers from 1 to 100:");
    
    for (int:i == 1; i <= 100; i += 1) {
        if (is_prime(i) > 0) {
            Con.println(int:i);
        }
    }
    
}
```

### Example 3: Fibonacci Generator

```cyclo
stc int fibonacci(int:n) {
    if (n < 2) {
        rtn n;
    }
    rtn fibonacci(n - 1) + fibonacci(n - 2);
}

pub stc empty main(str:[] args) {
    Con.println("First 15 Fibonacci numbers:");
    
    for (int:i == 0; i < 15; i += 1) {
        int:fib == fibonacci(i);
        Con.print("F(");
        Con.print(int:i);
        Con.print(") = ");
        Con.println(int:fib);
    }
    
}
```

### Example 4: Calculator

```cyclo
stc int add(int:a, int:b) { rtn a + b; }
stc int subtract(int:a, int:b) { rtn a - b; }
stc int multiply(int:a, int:b) { rtn a * b; }
stc int divide(int:a, int:b) {
    if (b == 0) {
        Con.println("Error: Division by zero!");
        rtn 0;
    }
    rtn a / b;
}

pub stc empty main(str:[] args) {
    int:num1 == 0;
    int:num2 == 0;
    
    Con.println("=== Simple Calculator ===");
    
    Con.print("Enter first number: ");
    Con.Read(int:num1);
    
    Con.print("Enter second number: ");
    Con.Read(int:num2);
    
    Con.println("");
    Con.print("Addition: ");
    Con.println(int:add(num1, num2));
    
    Con.print("Subtraction: ");
    Con.println(int:subtract(num1, num2));
    
    Con.print("Multiplication: ");
    Con.println(int:multiply(num1, num2));
    
    Con.print("Division: ");
    Con.println(int:divide(num1, num2));
    
}
```

### Example 5: Multiplication Table

```cyclo
pub stc empty main(str:[] args) {
    Con.println("Multiplication Table (1-10):");
    Con.println("");
    
    // Header row
    Con.print("   ");
    for (int:i == 1; i <= 10; i += 1) {
        Con.print(int:i);
        Con.print("\t");
    }
    Con.println("");
    Con.println("------------------------------------------------------------------");
    
    // Table body
    for (int:i == 1; i <= 10; i += 1) {
        Con.print(int:i);
        Con.print(" |");
        
        for (int:j == 1; j <= 10; j += 1) {
            int:product == i * j;
            Con.print(int:product);
            Con.print("\t");
        }
        Con.println("");
    }
    
}
```

---

## 🔧 Compiler Usage

### Basic Compilation

```bash
# Compile a Cyclo source file
./CycloC-[YOUR_PLATFORM]-[YOUR_ARCH] source.cyc

# This generates:
# - source.ll     (LLVM IR - intermediate representation)
# - source        (executable binary)
```

### Running Your Program

```bash
# Linux/macOS
./source

# Windows (PowerShell/CMD)
source.exe
```


### Compilation Pipeline

```
source.cyc
    ↓
[Lexical Analysis] → Tokenization
    ↓
[Parsing] → Abstract Syntax Tree (2-pass)
    ↓
[Semantic Analysis] → Type checking & validation
    ↓
[Code Generation] → LLVM IR generation
    ↓
[Optimization] → LLVM optimizations
    ↓
[Linking] → Native executable
    ↓
executable
```

### Error Messages

Cyclo provides detailed, actionable error messages:

```
❌ [ERROR] Syntax error at line 5, column 12
Expected ';' after statement
Suggestion: Add semicolon at end of line

❌ [ERROR] Type mismatch at line 10
Cannot assign 'str' to variable of type 'int'
Suggestion: Use type conversion or check variable types

❌ [ERROR] Undefined variable 'x' at line 15
Variable must be declared before use
Suggestion: Declare it with: int:x == 0;

✓ Compilation successful!
✓ LLVM IR written to 'source.ll'
✓ Executable generated: 'source'
```

### Debugging

```bash
# View generated LLVM IR
cat source.ll

# Use LLVM tools for analysis
llvm-dis source.ll          # Disassemble
llvm-link source.ll         # Link modules
opt -O2 source.ll           # Optimize
```

---

## 🎯 Best Practices

### 1. Naming Conventions

```cyclo
// Variables: snake_case
int:user_count == 0;
str:first_name == "John";
flt:account_balance == 1000.50;

// Functions: snake_case
stc int calculate_total(int:a, int:b) {
    rtn a + b;
}

stc empty process_user_input() {
    // ...
}

// Classes: PascalCase
pub class StudentRecord {
    // ...
}

pub class DatabaseConnection {
    // ...
}

// Constants: UPPER_SNAKE_CASE (by convention)
int:MAX_USERS == 100;
int:DEFAULT_TIMEOUT == 30;
```

### 2. Code Organization

```cyclo
// 1. File header comment (optional)
/* 
 * File: main.cyc
 * Description: Main program entry
 * Author: Your Name
 * Date: 2025-11-07
 */

// 2. Class declarations (if any)
pub class MyClass {
    // ...
}

// 3. Helper function declarations
stc int helper_function(int:x) {
    rtn x * 2;
}

// 4. Main function at the end
pub stc empty main(str:[] args) {
    // Entry point
}
```

### 3. Error Handling

```cyclo
stc int safe_divide(int:a, int:b) {
    // Validate input
    if (b == 0) {
        Con.println("Error: Division by zero!");
        rtn 0;  // Return safe default
    }
    
    rtn a / b;
}

stc int get_positive_number() {
    int:num == 0;
    Con.print("Enter a positive number: ");
    Con.Read(int:num);
    
    // Validate
    if (num <= 0) {
        Con.println("Warning: Number must be positive, using 1 as default");
        rtn 1;
    }
    
    rtn num;
}
```

### 4. Comments

```cyclo
// Use comments to explain WHY, not WHAT

pub stc empty main(str:[] args) {
    // Initialize counter to track successful operations
    // (needed for statistics at the end)
    int:success_count == 0;
    
    /* 
     * Process loop: iterate through all users
     * Note: This could be optimized with batch processing
     * TODO: Implement batch processing in v8.0
     */
    for (int:i == 0; i < 100; i += 1) {
        // Process each user
        success_count += process_user(i);
    }
    
}
```

### 5. Function Length

```cyclo
// ❌ BAD: Too long, does too much
stc int bad_function() {
    // 200 lines of code...
    rtn 0;
}

// ✅ GOOD: Short, focused functions
stc int validate_input(int:value) {
    if (value < 0) {
        rtn 0;
    }
    rtn 1;
}

stc int process_data(int:value) {
    if (validate_input(value) == 0) {
        rtn 0;
    }
    // Process valid data
    rtn value * 2;
}

pub stc empty main(str:[] args) {
    int:result == process_data(10);
    Con.println(int:result);
}
```

---

## ⚠️ Common Pitfalls

### 1. Declaration vs Assignment

❌ **Wrong:**
```cyclo
int:x = 10;    // Single = is for assignment, not declaration!
```

✅ **Correct:**
```cyclo
int:x == 10;   // Use == for declaration and initialization
x = 20;        // Use = for assignment after declaration
```

### 2. Type Prefix in Console Output

❌ **Wrong:**
```cyclo
int:age == 25;
Con.println(age);    // Missing type prefix!
```

✅ **Correct:**
```cyclo
int:age == 25;
Con.println(int:age);    // Must include type prefix
```

### 3. Case Sensitivity

❌ **Wrong:**
```cyclo
CON.println("Hello");     // Wrong case
con.println("Hello");     // Wrong case
INT:x == 10;              // Wrong case
```

✅ **Correct:**
```cyclo
Con.println("Hello");     // Correct: Capital 'C', lowercase 'on'
int:x == 10;              // Correct: All lowercase
```

### 4. Missing Semicolons

❌ **Wrong:**
```cyclo
int:x == 10
Con.println(int:x)
rtn 0
```

✅ **Correct:**
```cyclo
int:x == 10;
Con.println(int:x);
rtn 0;
```

### 5. Scope Issues

❌ **Wrong:**
```cyclo
pub stc empty main(str:[] args) {
    if (true) {
        int:x == 10;
    }
    Con.println(int:x);    // Error: x not in scope!
}
```

✅ **Correct:**
```cyclo
pub stc empty main(str:[] args) {
    int:x == 10;           // Declare in function scope
    if (true) {
        x = 20;            // Assign inside block
    }
    Con.println(int:x);    // Accessible here
}
```

### 6. Uninitialized Variables

❌ **Wrong:**
```cyclo
int:x;                     // Error: Must initialize!
x = 10;
```

✅ **Correct:**
```cyclo
int:x == 0;                // Initialize on declaration
x = 10;                    // Then assign
```

---

## 🗺️ Roadmap

### Version 8.0 (Q1 2025)

- [ ] **Arrays** - Fixed-size and dynamic arrays
- [ ] **String Functions** - concat, substring, length, etc.
- [ ] **File I/O** - Read/write files
- [ ] **Enhanced Error Messages** - More context and suggestions

### Version 8.5 (Q2 2025)

- [ ] **Standard Library** - Math, string, collection utilities
- [ ] **Lambda Functions** - Anonymous functions
- [ ] **Generics** - Generic types and functions
- [ ] **Package Manager** - Dependency management

### Version 9.0 (Q3 2025)

- [ ] **Exception Handling** - try/catch/finally
- [ ] **Module System** - Improved code organization
- [ ] **Reflection** - Runtime type information
- [ ] **Concurrent Programming** - Threads and synchronization

### Version 10.0 (Q4 2025)

- [ ] **IDE Integration** - LSP support
- [ ] **Debugger** - Interactive debugging
- [ ] **Cross-compilation** - Target multiple platforms
- [ ] **WebAssembly** - Compile to WASM

---

## 🤝 Contributing

To be added in future updates.

## 📞 Support & Community

### Get Help

- 📧 **Email**: [Click to Email](mailto:cyclolangsupport@cyclonetworks.com)

### Resources

To be added in future updates.

---

## 🙏 Acknowledgments

Cyclo is built with amazing open-source technologies:

- **[LLVM](https://llvm.org)** - Compiler infrastructure
- **[GCC](https://gcc.gnu.org)** - GNU Compiler Collection
- **[Make](https://www.gnu.org/software/make/)** - Build automation

Special thanks to:
- The LLVM Project team
- All contributors and community members
- Everyone who provided feedback and bug reports

---

## 📊 Version History

### v7.1 (2025-11-07) - Current

- ✅ **Fixed**: For loop terminator issues with predecessors
- ✅ **Added**: `Con.Read()` for all primitive types
- ✅ **Improved**: Error messages with better context
- ✅ **Enhanced**: Post-processing for basic blocks
- ✅ **Fixed**: Scope management in nested structures
- ✅ **Added**: Comprehensive input/output support

### v7.0 (2025-11-01)

- ✅ Initial public release
- ✅ Core language features (variables, functions, classes)
- ✅ LLVM backend integration
- ✅ Basic console I/O (`Con.print`, `Con.println`)
- ✅ Control flow (if/else, for, while)
- ✅ Arithmetic and comparison operators
- ✅ Static typing with type checking
- ✅ Two-pass compilation
- ✅ Detailed error reporting

---

<div align="center">

**Made with ❤️ by [Cyclolysisss](https://github.com/Cyclolysisss)** for CycloNetworks

**Last Updated**: 2025-11-07 08:33:47 UTC  
**Version**: 7.1  
**Status**: Active Development

[⬆ Back to Top](#cyclo-programming-language)

</div>