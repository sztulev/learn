# Java SE 11 Programmer I | 1Z0-815
<https://education.oracle.com/en/java-se-11-programmer-i/pexam_1Z0-815>

## Exam Topics

### Understanding Java Technology  and environment
* Describe Java Technology and the Java development environment
* Identify key features of the Java language

### Working With Java Primitive Data Types and String APIs
* [Declare and initialize variables (including casting and promoting primitive data types)](variables.md)
* [Identify the scope of variables](variable-scope.md)
* [Use local variable type inference](local-var-type-inference.md)
* [Create and manipulate Strings](string.md)
* [Manipulate data using the StringBuilder class and its methods](StringBuilder.md)

### Working with Java Arrays
* Declare, instantiate, initialize and use a one-dimensional array
* Declare, instantiate, initialize and use two-dimensional array

### Creating and Using Methods
* Create methods and constructors with arguments and return values
* Create and invoke overloaded methods
* Apply the static keyword to methods and fields

### Reusing Implementations Through Inheritance
* Create and use subclasses and superclasses
* Create and extend abstract classes
* Enable polymorphism by overriding methods
* Utilize polymorphism to cast and call methods, differentiating object type versus reference type
* Distinguish overloading, overriding, and hiding

### Handling Exceptions
* Describe the advantages of Exception handling and differentiate among checked exceptions, unchecked exceptions, and Errors
* Create a try-catch block and determine how exceptions alter normal program flow
* Create and invoke a method that throws an exception

### Creating a Simple Java Program
* Create an executable Java program with a main class
* Compile and run a Java program from the command line
* Create and import packages

### Using Operators and Decision Constructs 
* Use Java operators including the use of parenthesis to override operator precedence
* Use Java control statements including if, if/else, switch
* Create and use do/while, while, for and for each loops, including nested loops, use break and continue statements

### Describing Objects and Classes
* Declare and instantiate Java objects, and explain objects' lifecycles (including creation, dereferencing by reassignment, and garbage collection) 
* Define the structure of a Java class
* Read or write to object fields

### Applying Encapsulation
* Apply access modifiers
* Apply encapsulation principles to a class

### Programming Abstractly Through Interfaces
* Create and implement interfaces
* Distinguish class inheritance from interface inheritance including abstract classes
* Declare and use List and ArrayList instances
* Understanding lambda Expressions

### Understanding Modules
* Describe the Modular JDK
* Declare modules and enable access between modules
* Describe how a modular project is compiled and run



## Potential new topics 
<https://enthuware.com/resources/new-topics-in-ocajp-11-ocjp-11>

1. __private methods in interfaces__
You have already seen default and static methods in interfaces in Java 8. There was a serious shortcoming with these methods. If you have even a couple of default/static methods in an interface with a lot of common code, you cannot refactor the common code into a single helper method without exposing that helper method to the general public because interface rules require all methods in an interface to be public. Java 9 solves this problem by relaxing this rule. It allows you to have private methods in an interface. Since OCAJP 8 covers default and static methods, OCAJP 11 will most certainly require you to know about private methods as well.

2. __Collection Factory methods__
For example, Set<Integer> ints = Set.of(1, 2, 3); and List<String> strings = List.of("first", "second");

3. __New methods in Stream interface__
dropWhile, takeWhile, ofNullable and a new iterate method that allows you to provide a Predicate on when to stop iterating. For example, IntStream.iterate(1, i -> i < 10, i -> i + 1).forEach(System.out::println);

4. __Local variable type inferencing using "var"__
This basically reduces code clutter by allowing you to write var list = new ArrayList<String>(); instead of ArrayList<String> list = new ArrayList<String>();

5. __Launch Single-File Source-Code Programs__
This feature allows you to directly run a Java source file instead of you having to compile it first. Since the OCAJP exam focuses on the basics of compiling and running a Java program, we think this is an important feature to cover in OCAJP 11.

6. __New methods in String class__
Strings have always been a strong focus area in OCAJP certification. Therefore, OCAJP 11 will most probably test you on new methods isBlank(), lines(), repeat(int), strip(), stripLeading(), stripTrainling(). You would also be required to know how strip() is different from trim().

7. __New method in Predicate__
Since OCAJP 8 covers Predicate, OCAJP 11 will most likely test you on the new Predicate.not(Predicate ) method as well, which returns a predicate that is the negation of the supplied predicate.
