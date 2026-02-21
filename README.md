# Swift-Notes

## Swift Questions
---

### Question 1: What is class?  
**Ans** - Class is used for Concrete implemetation. Class consists of **properties** & **Methods**.  

Example: 
```swift

Class Arithmatic {

//MARK: Properties

var firstNumber: Int = 0
var secondNumber: Int = 0

//MARK: Methods

func addTwoNumbers(first: Int: second: Int) -> Int {
      return first + second
  }
}
```
### Question 2: What is Sub class?  

**Ans** - A subclass is a child class that gets features from a parent class and can also add its own features.  

~~~swift
// Superclass
class Animal {
    func sound() {
        print("Animal makes a sound")
    }
}

// Subclass
class Dog: Animal {
    func bark() {
        print("Dog barks")
    }
}

let myDog = Dog()
myDog.sound()  // Inherited from Animal
myDog.bark()   // Own method
~~~

Output  

~~~yml
Animal makes a sound
Dog barks
~~~

### Question 3: What is Extansion?  

Ans - An extension in Swift lets you add new functionality to an existing type (like Int, String, Double, etc.) without modifying its original code.  

You can:

- Add new functions
- Add computed properties
- Add initializers
- Make the type conform to protocols






