---
layout: post
title: pointers in go
tags:
  - go

---
##### Pointers in Go
* Pointers in Go are special variables that store the memory addresses of other variables.

* It allows us to declare variables without declaring the type.

* They allow you to work with original data indirectly through its memory location.


```go
package main

import (
	"fmt"
)

func main() {
	// fmt.Print("hello world")

	var num = 100

	//assigning a value to pointer variable (address of another variable)
	var numPtr *int = &num 

	fmt.Println(numPtr) //prints 0x1400011e018 (address of num variable)

	//printing the value of the pointer (dereferencing)
	fmt.Println(*numPtr) //prints 100

	//changing the value of num through the pointer variable
	*numPtr = 200
	fmt.Println(*numPtr) //prints 200

	//What happens if we directly assign some value to pointer variable
	// numPtr = 10 //compiler error

}
```
##### Advantages of pointers in go
###### Efficiency

By passing pointers to functions instead of the entire data structure, you can avoid unnecessary copying of large objects.

###### Modifying function arguments

Pointers allow you to modify the original data passed to a function. This is useful when you want functions to update exisiting data structures.

###### nil checking

Pointers allow for checking if a variable points to a valid memory location using the nil comparison. This helps avoid dereferencing pointers that don't point to any data, preventing runtime errors.

###### Pass by reference

Go primarily uses pass by value. This means that when you pass a variable to a function, a copy of the value is passed, not the original memory location.  Go achieves a behaviour similar to pass-by-reference throught the use of pointers. 

##### Are pointers in Go same as C language?

Pointers in Go share some similarities with C pointers but they also have some differences.

###### Similarities

* **Memory Addresses**: Both store memory addresses of other variables.
* **Dereferencing**: In both languages, the `*` operator is used to dereference a pointer and access the value at the momory location it points to.
* **Nil Pointers**: Both have a concept of `nil` pointers, which indicate they don't point to any valid memory location.

###### Differences
* **Pointer Arithmetic**: Go does not allow pointer arithmetic like adding or subtracting integers from pointers.
* **Type Saftey**: Go pointers are more type safe than C pointers. In Go, a pointer to a specific data type can only point to that type or a compatible type. C pointers are more flexible in a way that they can be cast to different pointer types. (This could be dangerous if not used properly)
* **Automatic memory management**: Go handles memory management automatically through garbage collection. C requires manual memory management. 