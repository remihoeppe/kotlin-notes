# Difference Between `runCatching` and `try/finally` in Kotlin

## 1. Purpose & Usage

- **`try/finally`:**
  - Used for **guaranteeing that some code always runs**, typically for cleanup tasks (like closing resources, releasing locks, etc.), regardless of whether an exception occurs.
  - Structure:
    ```kotlin
    try {
        // Code that may throw an exception
    } finally {
        // Cleanup code that will always execute
    }
    ```

- **`runCatching`:**
  - Used to **handle exceptions in a functional manner**. It wraps the result of a computation in a `Result` object. If an exception occurs, it catches it and encapsulates it in the `Result`.
  - It provides utility functions like `getOrElse`, `onFailure`, etc., to handle success and failure cases.
  - Structure:
    ```kotlin
    val result = runCatching {
        // Code that may throw an exception
    }
    
    result.getOrElse {
        // Handle failure case
    }
    ```

## 2. Handling Results

- **`try/finally`:**
  - If an exception occurs, the `finally` block will still run, but the exception must be handled manually using a `catch` block (if provided).
  - No special encapsulation of the result, meaning success and failure are handled in the normal `try-catch-finally` flow.

- **`runCatching`:**
  - Automatically **encapsulates the result in a `Result` object**, which can be either `Result.success` or `Result.failure`.
  - Functional methods like `onSuccess`, `onFailure`, `getOrElse`, and `getOrNull` can be used to process the result without traditional `catch` blocks.

## 3. When to Use

- **Use `try/finally`:**
  - When you need to ensure that **certain code always runs**, regardless of exceptions (e.g., closing resources, file streams, or database connections).

- **Use `runCatching`:**
  - When you want to **handle exceptions in a more functional way**, encapsulating both success and failure in a result, and processing them with chainable methods.

## 4. Example Comparison

- **`try/finally`:**
    ```kotlin
    try {
        val result = someFunctionThatMightThrow()
        // process result
    } finally {
        cleanup() // Always runs
    }
    ```

- **`runCatching`:**
    ```kotlin
    val result = runCatching { 
        someFunctionThatMightThrow() 
    }
    
    result.onSuccess { 
        // process success 
    }.onFailure { 
        // handle exception 
    }
    ```

## Summary

- **`try/finally`:** Ensures cleanup code runs and is more suited for resource management.
- **`runCatching`:** Handles success/failure outcomes in a functional style and simplifies exception handling.
