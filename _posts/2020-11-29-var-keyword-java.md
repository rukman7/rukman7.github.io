---
layout: post
title: var keyword in java
tags:
  - java
  - java11

---
##### The ‘var’ keyword in Java
* The var keyword was first introduced in Java 10.

1. It allows us to declare variables without declaring the type.
```java
//normal declaration 
String message1 = "Hello world!";
//using var keyword
var message2 = "Hello world"; 
```

2. It would help us reduce boiler plate code.
```java
//class name is mentioned on both sides 
Train train = new Train(EngineType.Electric, Type.Goods, EngineVersion.Six);
//using var reduces code
var train = new Train(EngineType.Electric, Type.Goods, EngineVersion.Six);
```

3. It helps us improve code readability and makes the code less verbose.
```java
//typical way
for(Map.Entry<String, Map<String, List<String>>> entry : nestedMap.entrySet()){
    //do something
   }
//using var
for(var entry : nestedMap.entrySet()){
    //do something
    }
```

##### Somethings to keep in mind while using var
* While the use of ‘var’ keyword might make it hard to understand the code in gerrit or other plain text editors as the data types are not explicitly mentioned, The IDE’s will show us the data type when hovering over the keyword.

* There are some limitations for using the ‘var’ keyword:
1. It cannot be assigned null. A compilation error would occur.
2. It cannot be used for class variables. It can only be used for local variables (inside a method)
3. var cannot be used in lambda expressions.
4. You cannot use var for method signatures (in return types and parameters/arguments).