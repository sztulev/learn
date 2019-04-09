# OCAJP 11

## Potential new topics 
<https://enthuware.com/resources/new-topics-in-ocajp-11-ocjp-11>

1. private methods in interfaces
You have already seen default and static methods in interfaces in Java 8. There was a serious shortcoming with these methods. If you have even a couple of default/static methods in an interface with a lot of common code, you cannot refactor the common code into a single helper method without exposing that helper method to the general public because interface rules require all methods in an interface to be public. Java 9 solves this problem by relaxing this rule. It allows you to have private methods in an interface. Since OCAJP 8 covers default and static methods, OCAJP 11 will most certainly require you to know about private methods as well.

2. Collection Factory methods
For example, Set<Integer> ints = Set.of(1, 2, 3); and List<String> strings = List.of("first", "second");

3. New methods in Stream interface
dropWhile, takeWhile, ofNullable and a new iterate method that allows you to provide a Predicate on when to stop iterating. For example, IntStream.iterate(1, i -> i < 10, i -> i + 1).forEach(System.out::println);

4. Local variable type inferencing using "var"
This basically reduces code clutter by allowing you to write var list = new ArrayList<String>(); instead of ArrayList<String> list = new ArrayList<String>();

5. Launch Single-File Source-Code Programs
This feature allows you to directly run a Java source file instead of you having to compile it first. Since the OCAJP exam focuses on the basics of compiling and running a Java program, we think this is an important feature to cover in OCAJP 11.

6. New methods in String class
Strings have always been a strong focus area in OCAJP certification. Therefore, OCAJP 11 will most probably test you on new methods isBlank(), lines(), repeat(int), strip(), stripLeading(), stripTrainling(). You would also be required to know how strip() is different from trim().

7. New method in Predicate
Since OCAJP 8 covers Predicate, OCAJP 11 will most likely test you on the new Predicate.not(Predicate ) method as well, which returns a predicate that is the negation of the supplied predicate.
