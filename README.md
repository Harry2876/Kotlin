# Kotlin Programming Language

<img src="https://upload.wikimedia.org/wikipedia/commons/7/74/Kotlin_Icon.png" alt="Kotlin Logo" width="100"> Kotlin is a modern programming language that runs on the Java Virtual Machine (JVM) and is fully interoperable with Java. It is designed to be concise, expressive, and safe, making it an excellent choice for both new and experienced developers. Kotlin is used for a variety of applications, from Android development to server-side and web development.

## Author

This documentation is created by Hariom Harsh [Harry](https://github.com/Harry2876).<img src="https://avatars.githubusercontent.com/u/132590839?s=400&u=c9383791a58e5f305b3a3b8daae453bb3a99bc1e&v=4" alt="Harry's Profile" width="50" height="50" style="margin-top: 50px; border-radius: 30px;">

## Table of Contents

1. [Variable Declarations](#val-and-var-in-kotlin)
2. [Methods in Kotlin](#methods-in-kotlin)
3. [Control Statements](#statements-in-kotlin)
4. [Loops](#loops-in-kotlin)
5. [Pair and Triple](#pair-and-triple-in-kotlin)
6. [Classes and Objects](#classes-and-object)
7. [Constructors](#constructors)
8. [Companion Object](#companion-object)
9. [Inheritance](#inheritance)
10. [this vs super Keyword](#this-vs-super-keyword)
11. [Interface](#interface)
12. [Abstraction](#abstraction)
13. [Enum](#enum)
14. [Generics](#generics)
15. [Lambdas](#lambdas)
16. [Higher-Order Functions](#high-order-function)
18. [Delegation](#delegation)
19. [Scope Functions](#scope-functions)
20. [Collections](#collections)
21. [Nullability in Kotlin](#nullability-in-kotlin)

---

# Key Points
- To inherit class in Kotlin we don't use extends keyword,
a **`:`** is used to inherit classes.
- Classes in Kotlin are not pre declared as open to use, we must declare a class `open` to inherit and use it.
- To implement anything implement keyword is not used here just apply a comma after inherited class to implement.
- Variables are declared with capital letter in Kotlin, for example, `var a : Int = 7` .

### val and var in Kotlin

- Val is used to declare final values and values can’t be changed once its declared and in var we can change or update values later.

### Methods in Kotlin

- To declare a return type in Kotlin we use `:` in method.
- While passing parameters we declare name of parameter first then the data type assigned to it.

```kotlin
fun add(a: Int, b:Int) : Int {
return a + b
}
```

### Statements in Kotlin

- We can use `when` statement instead of `if`.

```kotlin
var num = 100;

when(num){

1 -> {
//your condition here
}

40 -> {
//your condition here
}
else -> {
//cndtn
}
}
```

### Loops in Kotlin

- for Loop Syntax

```kotlin
for (i in 1..3) {
//..represents range 
    println(i)
}
for (i in 6 downTo 0 step 2) {
//we can also use untill instead of downto if
//if we want for values till n-1.
    println(i)
}
```

### Pair and Triple in Kotlin

- **Pair** represents a generic pair of two values assigned to a variable.
- **Triple** stores triple value for the variable.
- We can nest pairs and triples inside them.

```kotlin
fun main() {
   val name = Pair("Hariom",Pair("Hello",Pair("Hola","1")))
   println("${name.second.second.first} ${name.first}")
   
   val test = Triple("learning","Kotlin",Triple("is","fun","!"))
   println("${test.first} ${test.third}")
}

/*
output
Hola Hariom
learning (is, fun, !)
*/
```

### Classes and Object

- A class is a blueprint, and an object is an instance of a class.
- Usually, we define a class and then create multiple instances of that class by creating objects.

```kotlin
fun main(){

    //Accesing as object in main fucntion
    println("The sum is :" + TestLearn().add(9,4))

}

//Creating class
class TestLearn {
    fun add (x:Int, y:Int) :Int {
        return x+y
    }
}
```

### Constructors

- A constructor is a special member function that is invoked when an object of the class is created primarily to initialize variables or properties.
- A class needs to have a constructor and if we do not declare a constructor, then the compiler generates a default constructor.
- Kotlin has two types of constructors: -
    1. Primary Constructor
    2. Secondary/Custom constructor.
1. **Primary Constructor**
    
    ```kotlin
    class sum constructor(val a: Int, val b:Int) {
      //code
      }
      
      //or
      
      class sum (val a:Int, val b:Int) {
        //code
        }
    ```
    
- **Init Block**
    
    The Primary constructor cannot contain any code, the initialization code can be placed in a separate initializer block prefixed with the init keyword.
    
    Used to add Extra logic in the constructor.
    
    ```kotlin
    class sum {
       //code
       
       init {
       println("Init called")
       }
    ```
    
1. **Secondary/Custom Constructor**
    - A class in Kotlin can have at most one primary constructor, and one or more custom/secondary constructors.
    - The primary constructor initializes the class and introduce some extra logic.
    
    [https://www.notion.so](https://www.notion.so)
    

```kotlin
class TestLearn {

    constructor(a : Int , b: Int){
        val twoSum = a+b
        println("Sum of a and b is : $twoSum")

    }

    constructor(a:Int, b:Int, c:Int){
        val threeSum = a+b+c
        println("Sum of a b c is : $threeSum")

    }
    
}
```

### Companion Object

- In some languages like java and c#, we use static keyword to declare the members of the class and use them without making any object i.e. just call them with the help of class name.
- There is nothing called static in Kotlin. so, in Kotlin we use a companion object.

```kotlin
fun main() {
    val cc = companionClass()
    println("First No is : ${cc.firstNo}")
    println("Sum is : ${cc.add(4,5)}")

    println("Second No is : ${companionClass.secondNo}")
    println("Product is : ${companionClass.product(2,3)}")

}

class companionClass {
    var firstNo = 10

    fun add(a:Int , b:Int) : Int {
        return a+b
    }

    companion object {
        var secondNo = 20
        fun product(a:Int, b:Int) :Int {
            return a*b
        }
    }

}
```

### Inheritance

- It is the mechanism by which one class is allowed to inherit the features (Fields and methods) of another class.
- One object acquires all the properties and behaviors of a parent object.
- It is an important part of oops.
- Subclass can reuse methods and fields of the parent class.
- By default, Kotlin classes are final they can’t be inherited. To make a class inheritable, mark it with the open keyword.
- We can also update functionalities or can make modifications in a child class using `override` keyword.

```kotlin
fun main() {
    
    val classB = classB()
    val classA = classA()
    
    println("The name is : "+classA.name + ","+ classB.name)
    println("The sum is : " + classA.add(5,6) +"The product is : " + classB.add(3,4))
   
}

open class classA {
    //parent class
    
    open var name = "Hariom"
    
    open fun add(a:Int, b:Int) :Int {
        return a+b
    }
}

class classB : classA(){
    override var name = "Harry"
    
    override fun add(a:Int, b:Int) :Int {
        val sum = super.add(a,b)
        val sq = sum*sum
        return sq
    }
}
```

### this vs super keyword

- The `this` keyword points to a reference of the current class, while the `super` keyword points to a reference off the parent class.
- `this` can be used to access variables and methods of the current class, and `super` can be used to access variables and methods of the parent class from the subclass.

### Interface

- An Interface is a reference type.
- It is similar to class.
- It is a collection of abstract methods.
- A class implements an interface, thereby inheriting the abstract methods of the interface.
- Only method signature, no body.
- Interfaces specify what a class must do and not how. It is the blueprint of the class.

```kotlin
fun main() {
    
    val cls = newClass()
    
    println("The firstNo is : ${cls.firstNo}")
    println("The twosome is : ${cls.add(2,3)}")
    println("The threesome is : ${cls.add(3,5,7)}")
    
}

interface addNum {
    var firstNo : Int
    
    fun add(a:Int , b:Int) : Int
    
    fun add(a:Int, b:Int, c:Int) : Int
}

class newClass : addNum {
    override var firstNo= 15
    
    override fun add(a:Int, b:Int) : Int {
        return a+b
    }
    
    override fun add(a:Int, b:Int , c:Int) : Int {
        return a+b+c
    }
}
```

### Abstraction

- Abstraction is one of the core concepts of object-oriented programming.
- When there is a scenario that you are aware of what functionalities a class should have, but not aware of how the functionality is implemented or if the functionality could be implemented in several ways, it is advised to use abstraction.
- It contains abstract or non-abstract: variables and functions.
- Abstract class cannot be initiated but could be extended to a super class.

```kotlin
//creating a abstract class
abstract class abClass{
    var name : String = "Hariom"

    abstract var branch : String

     fun add(a : Int , b: Int) : Int {
        return a+b
    }

    abstract fun mult(a:Int , b:Int) :Int

}

class testClass : abClass() {

    //as its abstract we need to override methods

    override var branch = "Hello"
    override fun mult(a: Int, b: Int): Int {
        return a*b
    }

}
```

### Enum

- In programming, sometimes there arises a need for a type to have only certain values.
- To accomplish this, the concept of enumeration was introduced.
- In Kotlin, like many other programming languages, an **enum** has its own specialized type, indication that something has a number of possible values.
- Enum constants aren’t just mere collections of constants-these have properties, methods etc.
- Each of the enum constants acts as separate instances of the class and separated by commas.
- Enums increases readability of your code by assigning pre-defined names to constants.

```kotlin

fun main(){
    //Printing a day
    println("Today is ${weekDays.MONDAY}")

    //getting number of holidays
    for (day in weekDays.values()){
        if (day.holiday)
            println("${day} is Holiday")
    }

    //printing all available directions
    println("All Available directions")
    for (dir in directions.values()) {
        println(dir)
    }

}

//creating a enum class for week days
enum class weekDays(var holiday : Boolean = false){
    SUNDAY(true),
    MONDAY,
    TUESDAY,
    WEDNESDAY,
    THURSDAY,
    FRIDAY,
    SATURDAY(true)
}

//testing a enum class for directions
enum class directions {
    EAST,
    WEST,
    NORTH,
    SOUTH
}
```

### Generics

- Generic is defined as a product without a brand name.
- The definition of generic is something without a brand name.
- Generics are the powerful features that allow us to define classes, methods and properties.
- Which are accessible using different data types while keeping a check of the compile-time type safety.
- A Generic type is a class or method that is parameterized over types.
- We always use angle brackets () to specify the type of parameter in the program.

> **Advantages of Generics**
> 
- Type casting is evitable- No need to typecast the object.
- Type safety- Generic allows only single type of object at a time.
- Compile time safety- Generics code is checked at compile time for the parameterized type so that it avoids run time error.

```kotlin
fun main(){

    val genclass = genClass("Its Harry")

}

//creating a generic class
class genClass<T> (value : T) {
    init {
        println("The value Assigned is : $value")
    }
}

fun <T> check(text:T){
    println("Received value is : $text")
}
```

### Lambdas

- It is just a function without name.
- Also known as Anonymous functions.

```kotlin
fun main(){

    //using lambda expressions
    println("square of 6 is ${sqr(6)}")
    println("Sum of two numbers is ${add(3,4)}")
    printName("Hariom")

}

//writing normal function
fun square(a : Int ) : Int {
    return a*a
}

//writing lambda expressions
val  sqr = {x: Int -> x*x}

val add : (Int, Int) -> Int = {x,y -> x+y}

val printName = {name : String -> println("Hello $name")}
```

### High order Function

- A function which can accepts a function as parameter or can returns a function is called Higher-Order function.
- Kotlin functions can be stored in variables and data structures, passed as arguments to and returned from other higher-order functions.

```kotlin

fun main(){

    highOrder(printMe)
    highAdd(add)

}

//working with higher order functions
val printMe = { println("Hello How are You :)") }
val add = { a:Int, b:Int -> a+b}
val retFunc = {a:Int, b:Int -> "The sum is ${a+b}"}

fun highOrder(function: () -> Unit){
    function()
}

fun highAdd(addFunc: (Int, Int) ->Int ) : (Int, Int) -> String {
    println("The sum is ${addFunc(5,6)}")

    return retFunc
}
```

### Delegation

- Inheritance implementation in classes and functions can be altered with the help of delegation techniques.
- Object-oriented programming languages support it innately without any boilerplate code.
- Delegation is used in Kotlin with the help of `by` keyword.

```kotlin
fun main(){

val taskname: String = " Download Task"
val taskManager = TaskManager(bgTask(taskname),bgExecute(taskname))

    taskManager.create()
    taskManager.execute()
}

interface task {
    fun create()
}

interface executeTask {
    fun execute()

}

class bgTask(val taskname: String): task {
    override fun create() {
        println("Task"+taskname+"created!")
    }
}

class bgExecute(val taskname: String):executeTask{
    override fun execute() {
        println("Task $taskname is Executing...")
    }
}

//using delegation
class TaskManager(val creator:task, val executor:executeTask) :
        task by creator, executeTask by executor
```

### Scope Functions

- The Kotlin standard library contains several functions whose sole purpose is to execute a block of code within the context of an object.
- When you call such a function on an object with a lambda expression provided, it forms a temporary scope.
- In this scope, you can access the object without its name.
- **Types of Scope Functions**
1. **With**
    - Return: lambda result
    - context object: this
2. **let**
    - Return: lambda result
    - context object: it
    - Used for null values
3. **run**
    - Return: lambda result
    - context object: this
4. **apply**
    - Return: context object
    - context object: this
5. **also**
    - Return: context object
    - context object: it

```kotlin
fun main(){

    //working on let scope function
    var name: String? = null

    name?.let {
        println("The length of the name is ${it.length}")
        println("The name is $it")
        println("The reversed name is ${it.reversed()}")
    }

    //applying scope function
    val user = user().apply {
        name = "Hariom"
        age = 20
        mobNo = "0987654321"
    }

   val age = with(user){
       println("The Name of user is $name")
       age
   }
    println("The age of user is $age")

    user.also {
        it.name = "Harsh"
        it.age = 21

        println("The Name and age of user has been updated...")
    }

    println("The new name and age is ${user.name} and ${user.age}")

}

class user {
    var name: String = ""
    var age: Int = 0
    var mobNo: String = ""
}
```

- for `run` scope function

```kotlin
fun main() {

    val user = user()

    //run is used when with is used with it
    val msg = user.run {
        println("The name of user is $name")
        age
        "Msg is returned"
    }

    println("Msg is $msg")
}

class user {
    var name: String = "Hariom"
    var age: Int = 20
    var mobNo: String = "0987654321"
}
```

### Collections

- A Collection usually contains a number of objects (this number may also be zero) of the same type.
- Objects in a collection are called elements or items.
- For example, all the students in a department form a collection that can be used to calculate their average age.

> The following collection types are relevant for Kotlin
> 
1. **List**
    - It is an ordered collection with access to elements by indices - integer numbers that reflect their position.
    - Elements can occur more than once in a list.
    - An example of a list is a sentence: it’s a group of words, the order is important, and they can repeat.
2. **Set**
    - It is a collection of unique elements.
    - It reflects the mathematical abstraction of set: a group of objects without repetitions.
    - Generally, the order of set elements has no significance. For example, an alphabet is a set of letters.
3. **Map**
    - It (or dictionary) is a set of key-value pairs.
    - Keys are unique, and each of them maps to exactly one value.
    - The values can be duplicates.
    - Maps are useful for storing logical connections between objects, for example, an employee’s Id and their position.

```kotlin
//For Lists

fun main() {

    //code for list
    val aList = listOf("Hariom","Harry", "Harsh","1")
    println("$aList \n")

    val mList = mutableListOf<Any>("Harshuu", "Haruka", "Naruto")

    mList.add("Dattebayo")
    mList.add(9)

    //we can also add or nest list in other list
    val newList = mutableListOf("sasuke", "Itachi")

    mList.add(newList)

    println(mList)

}
```

- Code is same for `set` only main thing is it doesn’t allow repetitions.

```kotlin
//code for Maps

fun main() {

    val aMap = mapOf<Any, Any>(1 to "Hariom", 2 to "Alok", 3 to "Shashi")

    println(aMap)

    //creating mutable map
    val mMap = mutableMapOf<Any, Any>()

    val newMap = mutableMapOf<Any, Any>(1 to "Dattebyo", 2 to "Naruto", 3 to "Sasuke")

    //we can add diff maps by putAll keyword

    mMap.putAll(newMap)

    //we can also make changes in a specific element of a map

    mMap[1]= "Itachi"

    println(mMap)
}
```

- We can also store elements in `ArrayList<>` and can modify them.

```kotlin

fun main() {

    //creating a ArrayList

    val newNames = ArrayList<String>()

    newNames.add("Hariom")
    newNames.add("shashi")

    //we can also modify items by the index number
    newNames[0] = "Naruto"

    println(newNames)

    //we can also remove elements
    newNames.removeAt(0)

    println(newNames.toString())

}
```

### Nullability in Kotlin

- Null means declaring a variable without any value
- To give null value we use `?` to the Keyword.

```kotlin
fun main() {

    var name : String? = null

    /*  we can also use !! to forcefully print the value
    but it will give null pointer exception error.
    
    println("The length of name is ${name!!.length}")
*/
    name.let {

        println("The  name is $name")
    }
    
}
```