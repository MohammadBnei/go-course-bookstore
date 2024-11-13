# Module 1: Introduction and Setup

---

## Go Language: Statically Typed

- **Definition**
  - Go is a statically typed language, meaning variable types are known at compile time.
  
- **Benefits**
  - Early error detection during compilation.
  - Improved performance due to optimized machine code.
  - Clearer code with explicit type declarations.

- **Example**
  ```go
  var age int = 30
  ```

---

## Go Language: Compiled Language

- **Definition**
  - Go is a compiled language, transforming source code into machine code.

- **Benefits**
  - Faster execution compared to interpreted languages.
  - Produces standalone binaries for easy deployment.
  - Compilation checks for errors before runtime.

- **Example**
  - Use `go build` to compile a Go program.

---

## Go Language: Developed by Google

- **Background**
  - Created by Google engineers Robert Griesemer, Rob Pike, and Ken Thompson.

- **Purpose**
  - Designed to improve programming productivity in large-scale software development.
  - Emphasizes simplicity, efficiency, and ease of use.

- **Key Features**
  - Strong concurrency support.
  - Rich standard library.
  - Cross-platform compatibility.

---

## Go Language: Concurrency Support

- **Definition**
  - Go has built-in support for concurrent programming using goroutines.

- **Benefits**
  - Efficiently handles multiple tasks simultaneously.
  - Simplifies writing concurrent code compared to traditional threading.
  - Uses channels for safe communication between goroutines.

- **Example**
  ```go
  go func() {
      fmt.Println("Hello, Goroutine!")
  }()
  ```

---

## Setting Up the Go Environment: Installation

- **Download and Install**
  - Obtain Go from the official website: [golang.org](https://golang.org).
  - Follow platform-specific installation instructions.
  - Ensure system PATH is updated to include Go binaries.

- **Verify Installation**
  - Run `go version` in the terminal to confirm installation.

- **Common Issues**
  - PATH not set correctly.
  - Conflicting Go versions.
  - Missing dependencies.

---

## Setting Up the Go Environment: IDE and Editor

- **Choose an IDE or Editor**
  - Popular options: VSCode, GoLand, Sublime Text.

- **Features to Look For**
  - Go syntax highlighting.
  - Integrated terminal and debugging support.
  - Code completion and linting.

- **Configuration**
  - Install Go plugins or extensions for enhanced functionality.

---

## Basic Go Program Structure

- **Package Declaration**
  - Every Go file begins with a `package` declaration.
  - `package main` is used for executable programs.

- **Import Statements**
  - Use `import` to include necessary packages.
  - Group imports for readability.

- **Main Function**
  - The entry point of a Go program is `func main()`.
  - Contains the core logic of the application.

- **Example**
  ```go
  package main

  import "fmt"

  func main() {
      fmt.Println("Hello, World!")
  }
  ```

---

## Go Workspace Structure

- **GOPATH and GOROOT**
  - `GOPATH`: Workspace directory for Go projects.
  - `GOROOT`: Directory where Go is installed.
  - Important for managing project dependencies.

- **Modules**
  - Use `go mod` to manage dependencies and versions.
  - Simplifies project setup and collaboration.
  - Supports versioning for consistent builds.

- **Example**
  - Initialize a module with `go mod init <module-name>`.

---

## Summary

- **Go's Strengths**
  - Statically typed and compiled for performance.
  - Developed by Google with a focus on simplicity and concurrency.
  - Strong community and extensive documentation.

- **Environment Setup**
  - Install Go and choose a suitable IDE.
  - Understand basic program structure and workspace organization.
  - Familiarize with Go's tooling and commands.