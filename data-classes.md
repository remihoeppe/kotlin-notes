
# Kotlin Data Classes Summary

Data classes in Kotlin are a special type of class designed to hold data. They come with several useful features like `equals()`, `hashCode()`, `toString()`, and `copy()` without requiring explicit implementation. Here’s what you should know about Kotlin data classes:

## 1. Basic Syntax
A data class is declared using the `data` keyword followed by the class declaration:
```kotlin
data class User(val name: String, val age: Int)
```
In this example, `User` is a data class with two properties: `name` and `age`.

## 2. Primary Features of Data Classes
When you declare a class as a `data class`, Kotlin automatically generates the following methods:
- **`equals()`**: Compares two instances of the data class based on their properties.
- **`hashCode()`**: Generates a hash code using the properties.
- **`toString()`**: Provides a string representation of the object.
- **`copy()`**: Creates a copy of the object, allowing you to modify specific properties.

Example:
```kotlin
val user1 = User("John", 25)
val user2 = user1.copy(age = 30) // Modifies age, keeps name
```

## 3. Requirements of Data Classes
A data class must meet the following requirements:
- It must have at least one primary constructor parameter.
- The primary constructor parameters must be `val` (read-only) or `var` (mutable).
- Data classes **cannot** be abstract, open, sealed, or inner classes.

## 4. Destructuring Declarations
Data classes support destructuring, allowing you to extract properties into variables:
```kotlin
val (name, age) = user1
```

## 5. Component Functions
Data classes automatically generate **component functions** like `component1()`, `component2()`, etc., which correspond to properties:
```kotlin
val name = user1.component1() // "John"
```

## 6. Customizing Data Classes
You can override the default `equals()`, `hashCode()`, and `toString()` methods if you need custom behavior.

## 7. Immutable Data
By using `val` for all properties, data class instances become immutable, promoting functional programming.

## 8. Default Values
You can assign default values to data class properties:
```kotlin
data class User(val name: String = "Unknown", val age: Int = 0)
```

## 9. Equality
Data classes use **structural equality** by default, meaning two objects are equal if their properties are equal.

## 10. Copying Data Classes
The `copy()` function allows for creating a copy of an object with some modified properties:
```kotlin
val original = User("Alice", 25)
val updated = original.copy(age = 30)
```

## 11. Nested Data Classes
Data classes can be nested inside other classes:
```kotlin
data class Address(val city: String, val zipCode: String)
data class User(val name: String, val address: Address)
```

## 12. Data Class vs Regular Class
While regular classes can store data, data classes minimize boilerplate code by providing useful methods automatically.

## Example Usage
```kotlin
data class Person(val name: String, val age: Int)

fun main() {
    val person1 = Person("Alice", 25)
    val person2 = person1.copy(age = 30)

    println(person1)  // Person(name=Alice, age=25)
    println(person2)  // Person(name=Alice, age=30)

    val (name, age) = person2
    println("Name: $name, Age: $age")  // Name: Alice, Age: 30
}
```

### When to Use Data Classes:
- When you need to hold simple data and want automatic implementations of common methods.
- When you prefer immutability and functional programming patterns.
- When working with collections where equality or string representation is important.
