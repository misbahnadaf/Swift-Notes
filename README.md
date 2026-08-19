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

Example  

~~~swift
extension String {
    var isNotEmpty: Bool {
        return !self.isEmpty
    }
}
let name = "Misbah"
print(name.isNotEmpty)   // true
~~~

**Add a function to check even or odd**  
~~~swift
extension Int {
    func isEven() -> Bool {
        return self % 2 == 0
    }
}

print(10.isEven())  // true
print(7.isEven())   // false
~~~


 ### Que.4 What is Enum?  
 **Ans**  - Enum is used to define a fixed set of related values.   
 **Ex**  
 ~~~swift
enum TrafficLight {
    case red
    case yellow
    case green
}
~~~
Use it like  
~~~swift
var signal = TrafficLight.red

signal = .green
~~~
We can check the value using switch:  
~~~swift

switch signal {
case .red:
    print("Stop")
    
case .yellow:
    print("Get Ready")
    
case .green:
    print("Go")
}
~~~
Output:  
~~~swift
Go
~~~

  ### Que.5 Explain Properties  
  **Ans** - A property is a variable or constant that belongs to a class, struct, or enum.  
            Property = A piece of information stored inside an object.    
  **Ex** -   
  ~~~swift
struct Person {
    var name = "Misbah"
    var age = 28
}
~~~
Here:
name → property  

age → property  

  **Types of properties**  
  
  1.Stored Properties  
  a.Stored Variable Property  
  b.Stored Constant Property  

  2.Lazy Stored Properties  

  3.Computed Properties  
  a.Read-only  
  b.Get + Set  

  4.Property Observers  
  a.willSet  
  b.didSet  

  5.Type Properties  
  a.static   
  b.class  

 **1. Stored Properties 📦**
A stored property actually stores a value in memory.  
~~~swift
struct Student {
    var name = "Ali"
    var age = 20
}
~~~

Here name and age are stored properties.  

Two types:  

Variable stored property:  
~~~swift
var age = 20
age = 25
~~~
The value can change.  

Constant stored property:  
~~~swift
let name = "Ali"
~~~
The value cannot change  

**2. Lazy Stored Property ⏳**. 

A lazy property is created only when you use it for the first time.  
~~~swift
class Student {
    lazy var details = "Student Details"
}
~~~

The details value isn't created until you access:  
~~~swift
let student = Student()
print(student.details)
~~~

Easy way:  
lazy = Create it only when needed.  
Useful when creating something is expensive or unnecessary until it's actually used.   

 **3. Computed Properties 🧮**  
 
A computed property doesn't store a value. It calculates and returns a value.  
~~~swift
struct Rectangle {
    var width = 10
    var height = 5
    
    var area: Int {
        width * height
    }
}
~~~
~~~swift
let rectangle = Rectangle()
print(rectangle.area) // 50
~~~
area is calculated from width and height.  

Two types:  
Read-only computed property  

Only get is provided:  
~~~swift
var area: Int {
    width * height
}
~~~
You can read it but can't assign a new value.  

Get + Set  
~~~swift
var fullName: String {
    get {
        firstName + " " + lastName
    }
    set {
        print(newValue)
    }
}
~~~

get → read the value  
set → change/set the value  
 
**4. Property Observers 👀**  

Property observers allow you to perform something when a property changes.  
There are two:  
willSet. 
Runs before the value changes.  
~~~swift
var age = 20 {
    willSet {
        print("Age is about to change")
    }
}
~~~

didSet   
Runs after the value changes.  
~~~swift
var age = 20 {
    didSet {
        print("Age has changed")
    }
}
~~~

You can use both:  
~~~swift
var age = 20 {
    willSet {
        print("Before changing")
    }
    didSet {
        print("After changing")
    }
}
~~~

Easy memory trick:    
willSet → Before    
didSet → After    

**5. Type Properties ⭐**  

A type property belongs to the type itself, rather than to an individual object.  
There are two keywords:  
static  
~~~swift
struct Company {
    static var companyName = "Apple"
}
~~~

Access it using the type:  
~~~swift
print(Company.companyName)
~~~  
You don't need to create an object.  

class. 
class type properties are mainly used with classes and can be overridden by subclasses.  
~~~swift
class Animal {
    class var category: String {
        return "Animal"
    }
}
~~~

  ### Que 6 Protocols  
  **Ans** 
  A protocol in Swift is a blueprint that defines a set of methods, properties, and other requirements. Any class, struct, or enum that adopts the protocol must implement those requirements, enabling abstraction, polymorphism, and code reuse.  
  **Why Use Protocols?**    
  Protocols help you:  
  
1.Achieve abstraction by defining behavior without tying it to a specific implementation.  
2.Write reusable code that works with any conforming type.  
3.Reduce coupling, making code easier to test and maintain.  
4.Implement common design patterns, such as delegation.  

  


  

  
### Que 7. Functions  
**Ans**  
A function is a block of code that performs a specific task.  
Instead of writing the same code again and again, we write it once inside a function and call it whenever we need it.  
Ex.    
~~~swift
func greet() {
    print("Hello!")
}

greet()
~~~
Output  
~~~swift
Hello!
~~~

**1. Function without parameters**  
A function can perform a task without receiving any input.  
~~~swift
func sayHello() {
    print("Hello, Swift!")
}

sayHello()
~~~. 
Output:
~~~swift
Hello, Swift!
~~~

  **2. Function with parameters**. 
A parameter is an input given to a function.  
~~~swift
func greet(name: String) {
    print("Hello \(name)")
}

greet(name: "Misbah")
~~~  
Output:  
~~~swift
Hello Misbah
~~~  
Here:   
~~~swift   
name: String
~~~   
is the parameter.  
And:  
~~~swift    
"Misbah"
~~~  
is the value we pass to it.  
Another example  
~~~swift  
func add(a: Int, b: Int) {
    print(a + b)
}
add(a: 10, b: 20)
~~~  
Output:  
~~~swift  
30  
~~~

 **3. Function that returns a value**  
Sometimes we don't just want the function to perform an action—we want it to give us a result.  
We use return.  
~~~swift. 
func add(a: Int, b: Int) -> Int {
    return a + b
}

let result = add(a: 10, b: 20)

print(result) 
~~~

Output:
~~~swift   
30
~~~

Here:  
~~~swift  
-> Int
~~~  
means the function will return an Integer.  

**4. Function with String return value**  
~~~swift  
func getName() -> String {
    return "Misbah"
}

let name = getName()

print(name)
~~~

Output:  
~~~swift  
Misbah
~~~

  **5. Function with multiple parameters**  
  ~~~swift
func studentInfo(name: String, age: Int) {
    print("Name: \(name)")
    print("Age: \(age)")
}

studentInfo(name: "Sara", age: 5)
~~~

Output:  
~~~swift  
Name: Sara
Age: 5
~~~

**6. Function with no return value**  

If a function only performs an action, you don't need to write a return type.  
~~~swift  
func welcome() {
    print("Welcome to Swift")
}
~~~

This is equivalent to a function returning Void.  
~~~swift  
func welcome() -> Void {
    print("Welcome to Swift")
}
~~~
**7. External and internal parameter names**  

Swift allows us to give different names to parameters when defining and calling a function.  
~~~swift
func greet(person name: String) {
    print("Hello \(name)")
}

greet(person: "Ali")
~~~

Here:  
person → external parameter name  
name → internal parameter name  
You can also use _ when you don't want to write the parameter name while calling:  
~~~swift  
func greet(_ name: String) {
    print("Hello \(name)")
}

greet("Ali")
~~~




 
     

          
  

  


