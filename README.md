# Introduction


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
