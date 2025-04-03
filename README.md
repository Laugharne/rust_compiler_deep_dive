**How the Rust Compiler Works, a Deep Dive - Video Highlights**


# [00:00](https://youtu.be/Ju7v6vgfEt8?t=0)  Introduction to Rust and the Rust Compiler

## Overview of the Presentation
- [00:00](https://youtu.be/Ju7v6vgfEt8?t=0)  Daniel introduces himself as a formal verification engineer at Runtime Verification, focusing on Rust and its compiler.
- [00:28](https://youtu.be/Ju7v6vgfEt8?t=28)  He acknowledges the ambitious goal of covering a complex topic within an hour, likening it to fitting a school bus into a living room.
- [00:52](https://youtu.be/Ju7v6vgfEt8?t=52)  Daniel checks if everyone can see his screen share and adjusts his presentation setup for better visibility.Structure of the Talk
- [01:15](https://youtu.be/Ju7v6vgfEt8?t=75)  The presentation will begin with a brief overview of Rust as a language (3-5 minutes).
- [01:46](https://youtu.be/Ju7v6vgfEt8?t=106)  Discussion will then shift to the Rust compiler's role in transforming source code into binaries, emphasizing properties that must be maintained during this process.
- [02:09](https://youtu.be/Ju7v6vgfEt8?t=129)  A detailed look inside the Rust compiler is planned for 20-30 minutes, followed by interactive callbacks related to using the compiler.

# [03:02](https://youtu.be/Ju7v6vgfEt8?t=182)  What is Rust?

## Key Features of Rust
- [03:02](https://youtu.be/Ju7v6vgfEt8?t=182)  Defined by the Rust Lang group as empowering users to build reliable and efficient software through explicit memory control.
- [03:34](https://youtu.be/Ju7v6vgfEt8?t=214)  Capable of compiling down small enough for embedded systems without needing a garbage collector, enhancing efficiency.

## Safety Guarantees
- [03:55](https://youtu.be/Ju7v6vgfEt8?t=235)  Strong guarantees regarding memory safety and thread safety are provided by its type system, preventing common errors like buffer overflows or dangling pointers.
- [04:32](https://youtu.be/Ju7v6vgfEt8?t=272)  Data race freedom is ensured during concurrency; however, logical deadlocks may still occur.

# [05:06](https://youtu.be/Ju7v6vgfEt8?t=306)  Memory Management in Rust

## Borrowing and Lifetime Semantics
![](images/2025-03-31-15-28-12.png)
- [05:06](https://youtu.be/Ju7v6vgfEt8?t=306)  The borrowing mechanism ensures shared data cannot be mutated while multiple references exist, maintaining integrity.

## Use of Unsafe Code
![](images/2025-03-31-15-31-29.png)
- [05:39](https://youtu.be/Ju7v6vgfEt8?t=339)  While memory safety relies on proper usage of safe constructs, misuse of the `unsafe` keyword allows direct manipulation but risks introducing bugs.

## Standard Library Utilization
- [06:36](https://youtu.be/Ju7v6vgfEt8?t=396)  The standard library provides safe abstractions over unsafe code (e.g., vectors), allowing developers to manage concurrency safely while leveraging powerful features.
![](images/2025-03-31-15-33-34.png)

# [07:14](https://youtu.be/Ju7v6vgfEt8?t=434)  Exploring the Rust Compiler

![](images/2025-03-31-15-35-07.png)

## Introduction to rustc
- [07:14](https://youtu.be/Ju7v6vgfEt8?t=434)  Daniel transitions to discussing `rustc`, which compiles Rust source code into target binaries.

# [07:46](https://youtu.be/Ju7v6vgfEt8?t=466)  Understanding the Rust Compiler and Its Components

## Overview of the Source Directory and Compiler
- [07:46](https://youtu.be/Ju7v6vgfEt8?t=466)  The source directory is not central to today's discussion; focus will be on documentation, compiler, and library.
- [08:10](https://youtu.be/Ju7v6vgfEt8?t=490)  Cloning the compiler repository allows building a fourth directory called "build," which contains the Rust C binary. Building takes significant time and space.
- [08:33](https://youtu.be/Ju7v6vgfEt8?t=513)  To build, users must utilize specific scripts (X scripts), particularly x.p for configuration purposes.

## Bootstrapping in Rust
- [08:55](https://youtu.be/Ju7v6vgfEt8?t=535)  The Rust compiler is a bootstrap compiler; its code is written in Rust itself, showcasing clever design principles.
- [09:28](https://youtu.be/Ju7v6vgfEt8?t=568)  Inside the compiler directory are numerous crates responsible for translating source language into binary while performing various analyses.

## Compiler Frameworks and Languages
- [10:02](https://youtu.be/Ju7v6vgfEt8?t=602)  Compilers can be built using external languages; frameworks like Java Cup and Flex YYC exist for defining grammars dynamically.
- [10:38](https://youtu.be/Ju7v6vgfEt8?t=638)  There are multiple bootstrap compilers available, each with unique benefits in compiling Rust into binaries.

## Cargo Tooling in Rust
- [11:15](https://youtu.be/Ju7v6vgfEt8?t=675)  Users familiar with Rust may have used Cargo, which simplifies interactions with the Rust compiler by running `rustc` under the hood.
- [11:39](https://youtu.be/Ju7v6vgfEt8?t=699)  When executing `cargo run`, it automatically handles arguments for `rustc`, streamlining user experience.

## Versions of the Compiler
- [12:13](https://youtu.be/Ju7v6vgfEt8?t=733)  The GitHub repository features nightly builds of the compiler that include frequent updates from community contributions aimed at improving functionality.
- [12:50](https://youtu.be/Ju7v6vgfEt8?t=770)  Stable releases of the compiler are also available, providing more reliability by excluding experimental features.

## Library Directory Insights
- [13:13](https://youtu.be/Ju7v6vgfEt8?t=793)  The library directory contains core primitives essential to Rust, including types related to memory allocation and standard libraries like vectors and slices.
- [13:47](https://youtu.be/Ju7v6vgfEt8?t=827)  Understanding these components is crucial as they support building robust applications within the language framework.

## Community Engagement and Learning Resources
- [14:10]([How the Rust Compiler Works, a Deep Dive - YouTube](https://youtu.be/Ju7v6vgfEt8?t=850))  For those interested in learning more about the Rust compiler or engaging with others, [**Zulip**](https://forge.rust-lang.org/platforms/zulip.html) serves as an excellent platform for questions and discussions.

## Compilation Process Breakdown

![](images/2025-03-31-15-48-23.png)

- [14:50](https://youtu.be/Ju7v6vgfEt8?t=890)  The process of converting source code to binary can be divided into **three main stages**:
  1. Source Code Level
  2. Intermediate Representation Level
  3. Code Generation Stage

# [15:35](https://youtu.be/Ju7v6vgfEt8?t=935)  Understanding Rust Compilation Process

## Overview of Code Transformation

![](images/2025-03-31-15-52-22.png)

- [15:35](https://youtu.be/Ju7v6vgfEt8?t=935)  The process of transforming code into the desired format involves multiple rounds of analysis to ensure it conforms to the language's specifications.
- [15:57](https://youtu.be/Ju7v6vgfEt8?t=957)  A simple "Hello World" program in Rust serves as a motivating example for understanding these transformations.

## Lexing and Parsing

![](images/2025-03-31-15-55-05.png)

- [16:29](https://youtu.be/Ju7v6vgfEt8?t=989)  An **Abstract Syntax Tree (AST)** is created from source code, which requires two main processes: **lexing** and **parsing**.
- [17:05](https://youtu.be/Ju7v6vgfEt8?t=1025)  Lexing involves reading a stream of characters and recognizing tokens that match the language's syntax, such as function definitions.

## Abstract Syntax Tree Representation
- [17:29]([How the Rust Compiler Works, a Deep Dive - YouTube](https://youtu.be/Ju7v6vgfEt8?t=1049))  The [**AST**](https://en.wikipedia.org/wiki/Abstract_syntax_tree) visually represents a program in a tree structure, useful for compilers. It includes various statements like conditions and assignments.

![](images/2025-03-31-15-59-43.png)

- [17:52](https://youtu.be/Ju7v6vgfEt8?t=1072)  The initial step for the Rust compiler is to create this AST through lexing and parsing before further processing.

## Macro Expansion and Name Resolution
- [18:50](https://youtu.be/Ju7v6vgfEt8?t=1130)  After creating the AST, the compiler must expand macros and resolve names to fully understand the program structure.
- [19:13](https://youtu.be/Ju7v6vgfEt8?t=1153)  Commands can be run in Rust C using specific flags (e.g., -Z help), allowing users to view different states within the compiler during this process. `rustc -Z unpretty="ast-free" src/main.rs`

![](images/2025-03-31-16-09-21.png)

## Viewing Compiler Output
- [19:47](https://youtu.be/Ju7v6vgfEt8?t=1187)  By utilizing commands like `rustc -Z help`, users can access various compiler flags that provide insights into its operations.
- [20:57](https://youtu.be/Ju7v6vgfEt8?t=1257)  The output of an AST does not resemble traditional graphical representations but instead appears as nodes with pointers indicating relationships between them.

![](images/2025-03-31-16-07-12.png)

## Practical Tools for Rust Development
- [21:52]([How the Rust Compiler Works, a Deep Dive - YouTube](https://youtu.be/Ju7v6vgfEt8?t=1312))  The [**Rust Analyzer**](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust-analyzer) is highly recommended for developers; it provides extensive information about code within IDE environments, enhancing productivity.

# [23:35](https://youtu.be/Ju7v6vgfEt8?t=1415)  Understanding the Role of Intermediate Representations in Rust Compilers

## The Purpose of Intermediate Representations
- [23:35](https://youtu.be/Ju7v6vgfEt8?t=1415)  The discussion begins with a question about the utility of seeing the intermediate representations (IR) of a program, primarily aimed at those interested in compilers.
- [23:59](https://youtu.be/Ju7v6vgfEt8?t=1439)  While IR is crucial for compiler developers, it also serves others who need to understand runtime verification and build tooling like theorem proving and interpreters for Rust.
- [24:35](https://youtu.be/Ju7v6vgfEt8?t=1475)  Many programs utilize IR from the Rust compiler for various business cases, although most users are typically compiler enthusiasts.

## Relationship Between Macros and Intermediate Representations
- [25:07](https://youtu.be/Ju7v6vgfEt8?t=1507)  A question arises regarding the relationship between macros in Rust and their representation; it's noted that there is indeed a connection.
- [25:28](https://youtu.be/Ju7v6vgfEt8?t=1528)  The existence of an intermediate representation depends on macros, which can be expanded into larger structures during compilation.
- [26:14](https://youtu.be/Ju7v6vgfEt8?t=1574)  When creating procedural macros in Rust, developers must consider lexing and parsing tokens, indicating a deeper level of complexity involved.

## Analyzing Abstract Syntax Trees
- [26:38](https://youtu.be/Ju7v6vgfEt8?t=1598)  The abstract syntax tree (AST) is introduced as a tool for debugging complex programs by revealing what gets outputted by the compiler.
- [27:00](https://youtu.be/Ju7v6vgfEt8?t=1620)  Transforming AST into **high-level intermediate representation** involves lowering and desugaring features to streamline control flow constructs like loops into singular representations.

![](images/2025-03-31-16-17-30.png)

## Lowering and Desugaring Process

- [27:24](https://youtu.be/Ju7v6vgfEt8?t=1644)  Features such as `for` loops, `while` loops, and infinite loops are consolidated into **one loop keyword** to simplify analysis.
- [28:18](https://youtu.be/Ju7v6vgfEt8?t=1698)  This process leads to transforming multiple control flow statements into match statements for easier handling within the compiler's analysis phase.

## Type Safety Guarantees in Rust Compilation

![](images/2025-03-31-16-21-35.png)

- [28:52](https://youtu.be/Ju7v6vgfEt8?t=1732)  After **lowering**, type inference, trait solving, and type checking occur within this new representation to ensure type safety guarantees provided by the Rust compiler.
- [29:32](https://youtu.be/Ju7v6vgfEt8?t=1772)  The transition from surface language to high-level IR shows added details like prelude inclusions and macro expansions that enhance clarity for further analysis.

`rustc -Z unpretty="hir" src/main.rs`
![](images/2025-03-31-16-25-53.png)

`rustc -Z unpretty="hir-tree" src/main.rs`
![](images/2025-03-31-16-27-18.png)

## Allocation IDs in Compiler Analysis
- [30:04](https://youtu.be/Ju7v6vgfEt8?t=1804)  In this stage of compilation, every expression receives **unique identifiers** known as `DefId` essential for tracking elements throughout various analysis rounds.


# Understanding Rust Compiler Analysis Techniques

## Overview of Analysis Techniques
- [31:30](https://youtu.be/Ju7v6vgfEt8?t=1890)  The analysis techniques at the high-level include **trait solving**, **type inference**, and **type checking**. These processes are essential for understanding how Rust handles types and generics during compilation.

## Type Inference in Rust

![](images/2025-04-01-13-58-35.png)

- [32:14](https://youtu.be/Ju7v6vgfEt8?t=1934)  **Type inference** allows the Rust compiler to deduce types without explicit declarations. For example, it can identify a variable as a vector of strings based on context.

## Trait Solving Explained
- [32:38](https://youtu.be/Ju7v6vgfEt8?t=1958)  Trait solving involves determining if generics used in functions can be instantiated correctly. The compiler checks if the generic types meet required traits, such as implementing `Display` for printing elements.
- [33:13](https://youtu.be/Ju7v6vgfEt8?t=1993)  An example is provided where a function logs elements from a vector of type `T`, which must implement the `Display` trait to ensure **proper output formatting**.

## Importance of Type Checking
- [34:11](https://youtu.be/Ju7v6vgfEt8?t=2051)  Type checking ensures that variables conform to their defined types, preventing errors like assigning negative numbers to unsigned integers (`u32`). This process is more complex than simply verifying basic constraints.

## Transitioning to Intermediate Representation (IR)

![](images/2025-03-31-16-17-30.png)

![](images/2025-04-01-14-05-52.png)

- [35:03](https://youtu.be/Ju7v6vgfEt8?t=2103)  After initial analysis, the representation evolves into an intermediate representation (IR), which retains more detailed information necessary for further analysis.
- [35:48](https://youtu.be/Ju7v6vgfEt8?t=2148)  The IR is fully type checked and elaborated, allowing for deeper safety checks related to unsafe code usage within Rust programs.

`rustc -Z unpretty="thir-tree" src/main.rs`
`rustc -Z unpretty="thir-flat" src/main.rs`

![](images/2025-04-01-14-09-07.png)

## Control Flow Graph (CFG)

![](images/2025-04-01-14-12-29.png)

# [40:05](https://youtu.be/Ju7v6vgfEt8?t=2405)  Understanding Control Flow Graphs in Rust

## Overview of Memory Representation

- [40:05](https://youtu.be/Ju7v6vgfEt8?t=2405)  The **Mir (Middle IR)** level involves declaring memory locations that will eventually be assigned types, forming the basis for program execution within nodes of a [**control flow graph (CFG)**](https://en.wikipedia.org/wiki/Control-flow_graph).

## Structure of Control Flow Graph (CFG)

![](images/2025-04-01-14-22-34.png)

- [40:27](https://youtu.be/Ju7v6vgfEt8?t=2427)  CFG consists of **basic blocks** where each block contains statements performing assignments to memory locations, culminating in a terminator that decides branching based on an integer value.
- [40:51](https://youtu.be/Ju7v6vgfEt8?t=2451)  Basic Block 1 includes two assignment statements and has a direct edge to Basic Block 4, which concludes with return statements.

## Looping and Analysis Benefits
- [41:14](https://youtu.be/Ju7v6vgfEt8?t=2474)  CFG can include loops; for instance, it is valid for Basic Block 2 to branch back to Basic Block 1.
- [41:14](https://youtu.be/Ju7v6vgfEt8?t=2474) This structure aids in subsequent analysis rounds.
- [41:48](https://youtu.be/Ju7v6vgfEt8?t=2508)  The analysis at this level focuses on **Drop Elaboration** and **Borrow Checking**, crucial for enforcing Rust's memory safety guarantees regarding lifetimes and allocation.

## Visualizing MIR Representations
- [42:09](https://youtu.be/Ju7v6vgfEt8?t=2529)  Using tools like `unpretty=mir` allows visualization of the MIR representation alongside source code, providing insights into memory declarations without taking them too literally.

  `rustc -Z unpretty="mir" src/main.rs`

  `rustc -Z unpretty="mir" -Zmir-enable-passes=-PromoteTemps src/main.rs`
  ![](images/2025-04-01-14-28-57.png)

- [43:29](https://youtu.be/Ju7v6vgfEt8?t=2609)  In MIR, **variables are replaced by memory places with specific types**; Place Zero is reserved for function returns while others act as registers or memory locations.

## Execution Flow in MIR Programs
- [44:03](https://youtu.be/Ju7v6vgfEt8?t=2643)  The execution starts from Basic Block Zero, assigning "Hello World" to Place Four and creating a non-mutable reference. If successful, it branches to Basic Block One.
- [44:39](https://youtu.be/Ju7v6vgfEt8?t=2679)  In Basic Block One, the output from printing is assigned to Place One. If no errors occur during this process, it transitions through the terminator to Basic Block Two.

# [45:11](https://youtu.be/Ju7v6vgfEt8?t=2711)  Transitioning from MIR to Code Generation

![](images/2025-04-01-14-35-33.png)

## Final Steps Before Code Generation
- [45:47](https://youtu.be/Ju7v6vgfEt8?t=2747)  After completing analyses in MIR, the next step involves transitioning towards **code generation using LLVM** or other backends like GCC or custom solutions tailored for specific use cases.

## Importance of Constant Evaluation
- [46:22](https://youtu.be/Ju7v6vgfEt8?t=2782)  Prior to code generation, all constants within Rust programs undergo evaluation. This ensures that constant values are resolved before further processing occurs.

## Lowering Process Explained

[**Static single-assignment form (SSA)**](https://en.wikipedia.org/wiki/Static_single-assignment_form)

# [47:39](https://youtu.be/Ju7v6vgfEt8?t=2859)  Understanding Monomorphization in Rust

## The Role of Monomorphization
- [47:39](https://youtu.be/Ju7v6vgfEt8?t=2859)  In Rust, generics allow functions to handle multiple types, but binaries do not understand these abstractions. [**Monomorphization**](https://en.wikipedia.org/wiki/Monomorphization) converts generics into specific functions for each type used.
- [48:00](https://youtu.be/Ju7v6vgfEt8?t=2880)  The process involves creating individual functions during code generation, ensuring that the binary can execute all necessary operations for the generic code.

## Transitioning to LLVM
- [48:32](https://youtu.be/Ju7v6vgfEt8?t=2912)  Once in LLVM (Low-Level Virtual Machine), extensive optimization occurs, bringing the representation closer to a binary format.
- [49:05](https://youtu.be/Ju7v6vgfEt8?t=2945)  Users can view LLVM's output through tools like `llvm BC`, which provides insights into the compiled code structure before reaching the final binary.

  **`rustc --emiy llvm-ir src/main.rs`**
  ![](images/2025-04-01-14-51-38.png)

  **`rustc --emiy llvm-bc src/main.rs`**
  ![](images/2025-04-01-14-53-39.png)

## Compilation Process Overview

![](images/2025-04-01-15-03-27.png)

- [49:42](https://youtu.be/Ju7v6vgfEt8?t=2982)  The compilation journey typically starts with writing a Rust source program and using Cargo to build it, resulting in a target binary.
- [50:03](https://youtu.be/Ju7v6vgfEt8?t=3003)  An example provided is an **x86 assembly instruction** set generated from a simple "Hello World" program, illustrating how high-level code translates into lower-level instructions.

  **`rustc --emiy ASM src/main.rs`**
  ![](images/2025-04-01-15-05-27.png)

# [51:03](https://youtu.be/Ju7v6vgfEt8?t=3063)  Exploring Intermediate Representations

## Interaction and Further Learning
- [51:03](https://youtu.be/Ju7v6vgfEt8?t=3063)  A suggestion was made to collect emails for further discussions on **intermediate representations (IR)**, indicating interest in deeper engagement with participants.

## Abstract Syntax Tree (AST)
- [51:24](https://youtu.be/Ju7v6vgfEt8?t=3084)  The abstract syntax tree represents the structure of source programs in Rust. It captures function definitions and validates syntax rules during parsing.
- [51:56](https://youtu.be/Ju7v6vgfEt8?t=3116)  **ABI (Application Binary Interface)** relates more closely to compiled bytecode than AST; it defines how different components interact at runtime.

## Code Generation Insights
- [52:19](https://youtu.be/Ju7v6vgfEt8?t=3139)  **The Rust compiler does not generate binary code directly; this task falls under LLVM or other backends like GCC**. This separation emphasizes modularity within compilers.
- [52:56](https://youtu.be/Ju7v6vgfEt8?t=3176)  Code generation is crucial as it determines how high-level constructs translate into machine-specific instructions based on chosen targets like **x86** or **ARM**.

# [53:21](https://youtu.be/Ju7v6vgfEt8?t=3201)  Intermediate Representations and Their Importance

## Understanding IR Structures
- [53:21](https://youtu.be/Ju7v6vgfEt8?t=3201)  Different IR stages exist within the Rust environment, facilitating various analyses and transformations before reaching final executable form.

## Lexical Analysis and Parsing

# [55:35](https://youtu.be/Ju7v6vgfEt8?t=3335)  Understanding Rust's Compilation Process

## Overview of Intermediate Representations (IR)
- [55:35](https://youtu.be/Ju7v6vgfEt8?t=3335)  The compilation process begins with expanding macros to fully elaborate names, leading down to the crate root. This sets the stage for further analysis.
- [56:08](https://youtu.be/Ju7v6vgfEt8?t=3368)  The first pass of guarantees involves type checking, where the compiler infers types not explicitly defined and checks trait bounds for instantiation feasibility.
- [56:30](https://youtu.be/Ju7v6vgfEt8?t=3390)  After type checking, a desugaring process occurs, resulting in a typed High Intermediate Representation (HIR), which includes checks for unsafety.

## Transitioning to Middle Intermediate Representation (MIR)
- [56:54](https://youtu.be/Ju7v6vgfEt8?t=3414)  The transition from an abstract syntax tree to a control flow graph marks the next phase. This graph consists of basic blocks containing statements that reference memory locations rather than variables.
- [57:18](https://youtu.be/Ju7v6vgfEt8?t=3438)  Each basic block concludes with a terminator that can branch out to other blocks, creating a structured layout of program execution paths.
- [57:41](https://youtu.be/Ju7v6vgfEt8?t=3461)  MIR is crucial for analyzing borrowing and lifetimes, ensuring shared data remains unmutated while managing multiple references effectively.

## Code Generation and Final Steps
- [58:14](https://youtu.be/Ju7v6vgfEt8?t=3494)  Following MIR analysis, code generation requires evaluating constants and processing generics into concrete instantiations before reaching the final representation.
- [58:37](https://youtu.be/Ju7v6vgfEt8?t=3517)  The output can be directed towards various code generation backends like LLVM; however, this step ultimately leads to producing the target binary.

## Enhancing Compilation Insights
- [59:12](https://youtu.be/Ju7v6vgfEt8?t=3552)  Typically overlooked steps in compilation are examined here; understanding these processes enriches knowledge about how binaries are built from source code.
- [59:35](https://youtu.be/Ju7v6vgfEt8?t=3575)  A proposal is made to improve visibility into IR by allowing inspection during runtime instead of just at compile time through pretty printed representations.

## Utilizing Rust Compiler Internally

  ![](images/2025-04-02-13-56-43.png)

- [01:00:18](https://youtu.be/Ju7v6vgfEt8?t=3618)  Rust enables calling its own compiler via an internal crate called **"rustc driver"** facilitating nested compilation within Rust programs.
- [01:00:41](https://youtu.be/Ju7v6vgfEt8?t=3641)  A pseudo-code example illustrates how one might create an instance of the compiler within their main function using this driver module.

## Practical Implementation Steps
- [01:01:27](https://youtu.be/Ju7v6vgfEt8?t=3687)  To implement nested compilation successfully, developers must include `extern crate rustc_driver` in their program along with specific feature flags for proper functionality.

# [01:02:23](https://youtu.be/Ju7v6vgfEt8?t=3743)  Installation and Setup of rustc Driver

## Overview of Required Components
- [01:02:23](https://youtu.be/Ju7v6vgfEt8?t=3743)  The command line indicates the need to install additional components for the task at hand, specifically related to the Rust crate. `rustup component add rust-src rustc-dev llvm-tools-preview`
- [01:02:56](https://youtu.be/Ju7v6vgfEt8?t=3776)  Two main crates are highlighted: `rustc_driver` and `rustc_driver_impl`, which contain essential code for leveraging nested calls in the compiler.

## Minimum Example for Running the Compiler
- [01:03:27](https://youtu.be/Ju7v6vgfEt8?t=3807)  A minimum example is presented for running the compiler, with a suggestion to increase font size for better visibility during demonstration.
  ![](images/2025-04-02-14-05-36.png)
- [01:03:50](https://youtu.be/Ju7v6vgfEt8?t=3830)  The source directory contains only a `main.rs` file, while an external **"Hello World" program** is referenced but not included in any crates, meaning it won't be part of cargo build processes.
  ![](images/2025-04-02-14-06-40.png)

## Command Line Arguments and Callbacks
- [01:04:12](https://youtu.be/Ju7v6vgfEt8?t=3852)  The example focuses on using the driver without interrupting callbacks; instead, it runs the compiler directly from a compiled program.
- [01:04:56](https://youtu.be/Ju7v6vgfEt8?t=3896)  An empty struct called `callback` is created to implement necessary traits without overriding functions, allowing default behavior that simply passes through to the compiler.

## Building and Running Programs
- [01:05:43](https://youtu.be/Ju7v6vgfEt8?t=3943)  The process begins with building the main program using `cargo build`, resulting in a binary that can call the Rust compiler.
- [01:06:15](https://youtu.be/Ju7v6vgfEt8?t=3975)  When running this binary with arguments pointing to "hello.rs" (`cargo run -- ~/presentation/hello.rs`), it should compile successfully and output **"Hello Rare Skills"**.

## Understanding Compiler Callbacks
- [01:06:51](https://youtu.be/Ju7v6vgfEt8?t=4011)  If no input is provided when calling Rust C, an error message appears indicating incorrect usage; however, providing valid arguments leads to successful compilation.
- [01:07:15](https://youtu.be/Ju7v6vgfEt8?t=4035)  After confirming successful execution of a simple program, attention shifts towards examining callback traits within the Rust compiler's implementation.

# [01:07:40](https://youtu.be/Ju7v6vgfEt8?t=4060)  Exploring Callback Traits in Rust Compiler

## Key Functions within Callback Trait
- [01:08:17](https://youtu.be/Ju7v6vgfEt8?t=4097)  The discussion introduces key functions within the callback trait such as `after_create_root_passing`, which allows custom code insertion during compilation phases.

## Queries System Explanation
- [01:08:40](https://youtu.be/Ju7v6vgfEt8?t=4120)  It’s noted that some functions may be deprecated but still functional. Custom code can manipulate queries during different stages of compilation (e.g., after macro expansion).

## Clarification on Queries
- [01:09:14](https://youtu.be/Ju7v6vgfEt8?t=4154)  A request for clarification on queries leads to an explanation that they serve as a system within the Rust compiler for retrieving information at various points during compilation.

## Typing Context Manipulation

# [01:10:05](https://youtu.be/Ju7v6vgfEt8?t=4205)  Understanding Rust Compiler Queries

![](images/2025-04-02-14-15-22.png)

## Overview of Compiler Queries
- [01:10:05](https://youtu.be/Ju7v6vgfEt8?t=4205)  The speaker introduces **compiler queries**, explaining that they allow for feeding information through the Rust compiler at specific points of interest during compilation.
- [01:10:39](https://youtu.be/Ju7v6vgfEt8?t=4239)  **Three key points** in the compilation process are identified where analysis can be interrupted:
  1. after crate root parsing: `after_crate_root_parsing`
  2. after macro expansion and name resolution: `after_expansion`
  3. and after full analysis: `after_analysis`

## Compilation Phases
- [01:11:01](https://youtu.be/Ju7v6vgfEt8?t=4261)  The first phase occurs post-abstract syntax tree (AST) creation, where macros remain unexpanded. No analysis is performed at this stage.
- [01:11:37](https://youtu.be/Ju7v6vgfEt8?t=4297)  The second phase involves analyzing the AST after macro expansion but before type checking and trait solving. Programs with borrow checker violations can still be analyzed here without errors.

## Practical Example of Callbacks

  ![](images/2025-04-02-14-20-39.png)

- [01:12:01](https://youtu.be/Ju7v6vgfEt8?t=4321)  The speaker demonstrates adding **custom code to callbacks** within the compilation phases, showing how to print messages indicating which phase is currently being executed.
  ![](images/2025-04-02-14-21-58.png)
- [01:12:43](https://youtu.be/Ju7v6vgfEt8?t=4363)  By running the compiler multiple times, it becomes evident that stopping at different phases affects whether a binary is created or not.

  **`cargo run -- ~/presentation/hello.rs`**
  ![](images/2025-04-02-14-33-48.png)

## Error Handling in Compilation
- [01:13:45](https://youtu.be/Ju7v6vgfEt8?t=4425)  If compilation is stopped after macro expansion but before analysis, illegal Rust programs can still produce an AST without throwing errors.
- [01:14:23](https://youtu.be/Ju7v6vgfEt8?t=4463)  An example illustrates that if a variable isn't flagged as mutable and an attempt to reassign it occurs, no error will be thrown until reaching the analysis phase.

## Insights on Syntax Validity
- [01:15:00](https://youtu.be/Ju7v6vgfEt8?t=4500)  The discussion highlights that even syntactically incorrect programs may pass initial checks without triggering immediate errors due to halted analysis.
- [01:16:20](https://youtu.be/Ju7v6vgfEt8?t=4580)  A further exploration into creating invalid syntax reveals that certain constructs can still generate an AST despite being semantically incorrect.

# [01:18:12](https://youtu.be/Ju7v6vgfEt8?t=4692)  Error Handling and Compiler Insights

## Understanding Error Reporting in Compilation
- [01:18:12](https://youtu.be/Ju7v6vgfEt8?t=4692)  The program's error handling system is designed to collect comprehensive information about errors rather than stopping at the first encountered issue, allowing for richer debugging insights.
- [01:18:33](https://youtu.be/Ju7v6vgfEt8?t=4713)  The compiler continues processing even after encountering an error, aiming to provide as much context as possible for troubleshooting.

## Macro Expansion and Error Detection
- [01:18:56](https://youtu.be/Ju7v6vgfEt8?t=4736)  Discusses the implications of introducing a non-existent macro during the expansion phase, highlighting how errors can be detected before full expansion occurs.
- [01:19:32](https://youtu.be/Ju7v6vgfEt8?t=4772)  Emphasizes that error messages are streamed directly from the compiler without delay, ensuring immediate feedback on issues.

## Analyzing Compiler Behavior
- [01:19:54](https://youtu.be/Ju7v6vgfEt8?t=4794)  Transitioning to a more complex example with additional crates allows for deeper exploration of compiler behavior post-analysis phase.
- [01:20:29](https://youtu.be/Ju7v6vgfEt8?t=4829)  Introduces querying global context within the Rust compiler, demonstrating how to access mutable references and utilize closures effectively.

# [01:20:52](https://youtu.be/Ju7v6vgfEt8?t=4852)  Exploring Type Context in Rust

![](images/2025-04-02-14-47-02.png)

## Accessing Internal Functions
- [01:21:14](https://youtu.be/Ju7v6vgfEt8?t=4874)  Explains how various internal functions can be accessed through the **typing context (tcx)**, enabling extensive manipulation capabilities within the Rust compiler.

## Practical Example: Crate Information Retrieval
- [01:21:48](https://youtu.be/Ju7v6vgfEt8?t=4908)  Demonstrates retrieving crate definitions and names using internal functions, showcasing aspects of Rust's internals typically hidden from users.
- [01:22:20](https://youtu.be/Ju7v6vgfEt8?t=4940)  Highlights that understanding crate identifiers is crucial for navigating multiple crates within a project.

![](images/2025-04-02-14-56-34.png)

# [01:23:31](https://youtu.be/Ju7v6vgfEt8?t=5011)  Utilizing CLI Commands for Code Analysis

## Pretty Printing with rustc
- [01:23:31](https://youtu.be/Ju7v6vgfEt8?t=5011)  Discusses using CLI commands like   `rustc -Z unpretty="mir" src/main.rs` to generate human-readable representations of code structures such as MIR (Mid-level Intermediate Representation).

  **`rustc -Z unpretty="mir" src/main.rs`**
  ![](images/2025-04-03-14-34-28.png)

## Internal Function Calls for Enhanced Output
- [01:24:13](https://youtu.be/Ju7v6vgfEt8?t=5053)  Describes accessing internal pretty-printing functions directly via typing context handles, illustrating how developers can leverage existing tools within the Rust ecosystem.
  ![](images/2025-04-03-14-40-20.png)
  ![](images/2025-04-03-14-40-53.png)
  ![](images/2025-04-03-14-42-27.png)

# Understanding Promoted Types in Rust Compiler

## Exploring Promoted Functions

  ![](images/2025-04-03-14-46-18.png)

- [01:26:28](https://youtu.be/Ju7v6vgfEt8?t=5188)  The speaker investigates the concept of **"promoted" types** by searching for related functions in the Rust compiler, specifically focusing on a function named `promoted_mir`.
  ![](images/2025-04-03-14-48-04.png)
- [01:27:02](https://youtu.be/Ju7v6vgfEt8?t=5222)  They explain that every body within the context has a **definition ID (DefId)**, and they plan to iterate through these bodies to identify promoters and print their sizes.
  ![](images/2025-04-03-14-50-24.png)

## Analyzing Internal Representations
- [01:27:39](https://youtu.be/Ju7v6vgfEt8?t=5259)  Upon running their analysis, they receive warnings but successfully output internal representations of promoted types, contrasting this with a more user-friendly printed version.
- [01:28:12](https://youtu.be/Ju7v6vgfEt8?t=5292)  The speaker notes that while there may be multiple promoted items, only one is present in this case, confirming expectations through length checks.

## Practical Applications of Analysis
- [01:29:19](https://youtu.be/Ju7v6vgfEt8?t=5359)  The discussion shifts to practical applications where runtime verification is necessary; they mention a project requiring JSON serialization of intermediate representation (MIR).
- [01:29:55](https://youtu.be/Ju7v6vgfEt8?t=5395)  They describe using a driver function called `emit_smir` to facilitate this serialization process, highlighting its role in obtaining global context and executing callbacks.
  ![](images/2025-04-03-15-05-12.png)

## Serialization Challenges
- [01:30:58](https://youtu.be/Ju7v6vgfEt8?t=5458)  The speaker elaborates on challenges faced during serialization due to the initial format not being ready for direct conversion into JSON.
- [01:31:54](https://youtu.be/Ju7v6vgfEt8?t=5514)  They emphasize the importance of normalizing data forms before serialization and how carrying around typing contexts aids in achieving this goal.

## Custom Code Generation Backends

![](images/2025-04-03-15-18-38.png)

- [01:32:29](https://youtu.be/Ju7v6vgfEt8?t=5549)  Transitioning from interaction with IR levels, they discuss options for custom code generation backends within the Rust compiler beyond default LLVM or GCC options.
- [01:33:08](https://youtu.be/Ju7v6vgfEt8?t=5588)  By implementing the **`CodegenBackend` trait**, developers can create tailored code generation solutions suited for specific use cases like **custom blockchains**.

## Potential Use Cases in Blockchain Development
- [01:34:04](https://youtu.be/Ju7v6vgfEt8?t=5644)  The speaker speculates about **compiling Rust for unique blockchain environments** that require specialized virtual machines (VM), suggesting it’s feasible though not widely reported.

# Understanding Rust Compiler Configuration and Building Process

## Initial Thoughts on M Consumption
- [01:35:00](https://youtu.be/Ju7v6vgfEt8?t=5700) The speaker expresses uncertainty about the consumption of Mir from a stream, noting a lack of serialization encountered. This suggests that there may not be widespread usage in a portable sense.

## Exploring Rust Environment
- [01:35:37](https://youtu.be/Ju7v6vgfEt8?t=5737) Discussion on using **L2 layer blockchain** within the Rust environment indicates potential for direct access to resources, allowing users to write custom Rust programs. However, no concrete answers are provided regarding its feasibility.

## Bounded Model Checking with Coen Backend
- [01:36:00](https://youtu.be/Ju7v6vgfEt8?t=5760) The speaker mentions a project called [**Kani**](https://model-checking.github.io/kani/) ([Getting started - The Kani Rust Verifier](https://model-checking.github.io/kani/) (_open-source verification tool that uses [model checking](https://model-checking.github.io/kani/tool-comparison.html) to analyze Rust programs._) that utilizes a paradigm for transferring data necessary for Bounded Model Checking (CBMC). They encourage further exploration into specific traits being overwritten in real-world applications.

## Setting Up rustc for Compiler Work
- [01:36:34](https://youtu.be/Ju7v6vgfEt8?t=5794) Transitioning to **building rustc**, the speaker highlights challenges faced when modifying the compiler and offers tips to ease this process.
- They emphasize the **importance of selecting appropriate build scripts** during setup.

  `./x.py setup`
  ![](images/2025-04-03-15-33-02.png)
  type **b**

  `time ./x build`

## Build Scripts and Configuration Options
- [01:37:30](https://youtu.be/Ju7v6vgfEt8?t=5850) As they initiate the build process, they explain that choosing specific profiles (like 'compiler') provides configurations tailored for easier modifications while working on the Rust compiler itself. This includes options like debugging settings and incremental compilation enabled by default.

## Understanding Compiler Profiles and Configurations
- [01:39:20](https://youtu.be/Ju7v6vgfEt8?t=5960) The configuration file (`config.example.toml`) is discussed as containing numerous customizable settings essential for building the compiler effectively.
- The speaker notes that defaults are set up by the Rust team to assist newcomers in navigating these options efficiently.

## Stages of Compiler Building Process

# [01:42:48](https://youtu.be/Ju7v6vgfEt8?t=6168)  Rust Compiler Optimization Techniques

## Overview of the rustc Dev Guide
- [01:42:48](https://youtu.be/Ju7v6vgfEt8?t=6168)  The speaker encourages viewers to refer to the [**rustc Dev guide**](https://rustc-dev-guide.rust-lang.org/building/how-to-build-and-run.html), which serves as a comprehensive resource for building and running the Rust compiler.
- [01:42:48](https://youtu.be/Ju7v6vgfEt8?t=6168)  The guide includes [**suggested workflows**](https://rustc-dev-guide.rust-lang.org/building/suggested.html) that streamline processes like profiling, enhancing overall efficiency.

## Improving Compilation Speed
- [01:43:10](https://youtu.be/Ju7v6vgfEt8?t=6190)  Initial compilation times can be lengthy; for example, a first run took 28 minutes of user time.
- [01:43:44](https://youtu.be/Ju7v6vgfEt8?t=6224)  Even with multi-threading capabilities, reducing compile time from 28 minutes to 3 minutes is still not ideal for iterative development.

## Incremental Compilation Strategy
- [01:44:44](https://youtu.be/Ju7v6vgfEt8?t=6284)  After making minor changes in the code (_e.g., modifying a function_), there's no need to rebuild the entire compiler.
- [01:45:29](https://youtu.be/Ju7v6vgfEt8?t=6329)  By using **incremental compilation** and **retaining stage one** components, significant reductions in build times can be achieved.



## Performance Metrics
- [01:46:18](https://youtu.be/Ju7v6vgfEt8?t=6378)  With incremental compilation, build times improved dramatically to 21 seconds of real time and only 1 minute and 20 seconds of user time.
- `./x build --keep-stage 1`
  ```
  real    3m18.777s
  user    27m9.879s
  sys     1m5.075s

  real    0m21.599s
  user    1m19.740s
  sys     0m10.388s
  ```
- [01:46:57](https://youtu.be/Ju7v6vgfEt8?t=6417)  The speaker demonstrates how to locate the compiled binary within the target directory after making changes. `./build/x86_64-unknow-linux-gnu/stage1/bin/rustc -Z unpretty=mir hello.rs`

## Practical Application of Changes
- [01:48:14](https://youtu.be/Ju7v6vgfEt8?t=6494)  A simple change was made in a Rust program (hello.rs), showcasing how modifications are reflected in the output.
- [01:48:48](https://youtu.be/Ju7v6vgfEt8?t=6528)  The speaker emphasizes that even small changes can lead to meaningful improvements in performance metrics.

## Advanced Build Techniques
- [01:49:22](https://youtu.be/Ju7v6vgfEt8?t=6562)  Further optimizations involve specifying **library builds** while maintaining stage one settings for faster results.
- `./x build library --keep-stage 1`
- [01:50:07](https://youtu.be/Ju7v6vgfEt8?t=6607)  Understanding build dependencies is crucial; certain operations must occur sequentially (_e.g., rustdoc after library_).

## Conclusion and Q&A Session
- [01:51:07](https://youtu.be/Ju7v6vgfEt8?t=6667)  The session concludes with an invitation for questions regarding common backend swaps among compilers like **Kany**, **GCC**, and **LLVM**.

# [01:52:05](https://youtu.be/Ju7v6vgfEt8?t=6725)  Compiler Projects and Their Challenges

## Overview of Compiler Projects
- [01:52:05](https://youtu.be/Ju7v6vgfEt8?t=6725)  Discussion on projects like Anas and Caron that focus on exchanging the Coen backend to enhance interactive theorem proving within formal methods.
- [01:52:27](https://youtu.be/Ju7v6vgfEt8?t=6747)  Mention of existing queries in the Rust compiler, highlighting limited options due to predetermined namespaces.

## Namespace Clarifications
- [01:53:03](https://youtu.be/Ju7v6vgfEt8?t=6783)  Explanation of namespace resolution, emphasizing that function names should not conflict with query names during usage.
- [01:53:28](https://youtu.be/Ju7v6vgfEt8?t=6808)  Insight into different Intermediate Representation (IR) layers accessible during compilation, showcasing how they interact throughout the process.

## Internal Compiler Errors
- [01:54:15](https://youtu.be/Ju7v6vgfEt8?t=6855)  Acknowledgment of bugs in compilers, including **rustc** and comparison with other compilers like **Solidity** and **Viper** which also have historical bugs.
- [01:54:47](https://youtu.be/Ju7v6vgfEt8?t=6887)  Definition of an **Internal Compiler Error (ICE)**, characterized by unusual error messages indicating issues within the compiler rather than user code.

## Reporting Bugs
- [01:55:24](https://youtu.be/Ju7v6vgfEt8?t=6924)  Guidance on reporting ICE occurrences to the compiler's GitHub issue board for resolution, stressing the importance of providing context for errors.


- Web: https://runtimeverification.com
- Twitter: @rv_inc
- Discord: https://discord.com/invite/CurfmXNtbN
- Mail: contact@runtimeverification.com


---

📺 [Watch the full video](https://youtu.be/Ju7v6vgfEt8)

