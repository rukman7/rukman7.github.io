---
layout: post
title: Heap in go
tags:
  - go
  - algorithms
  - datastructures

---

##### Min heap implementation in go

```go
package main

import (
	"fmt"
	"container/heap"
)

//initialize min heap
type minHeap []int

//these are interface functions from container/heap 
//these are required because internally sort interface is being used
//these the receivers are values and not pointers so they work with copy of data
//this is a implict sign that the datastructure itself won't be modified in these functions
func (h minHeap) Len() int { return len(h)}
func (h minHeap) Less(i int, j int) bool {return h[i] < h[j]}
func (h minHeap) Swap(i int, j int) { h[i], h[j] = h[j], h[i]}

//any is being used to support any type within the heap. this was implemented before generics. 
func (h *minHeap) Push(x any){
//x.(int) gets the value from x if it's an int. interfaces in go can store
//type and value of an interface. below is how we get the value of x if it's type is any
//it's called a fat pointer
	*h = append(*h, x.(int))
}

//here container/heap has one more Pop method so it does manipulation manually
//and makes the min value available at the end of the minHeap before calling it's Pop
func (h *minHeap) Pop() any{
	old := *h
	n := len(old)
	x := old[n-1]
	*h = old[0 : n-1]
	return x
}

func main(){
	h := &minHeap{3, 9, 1}
	heap.Init(h)
	heap.Push(h, 15)
	heap.Push(h, 2)
	fmt.Println("min = ",(*h)[0])
	fmt.Printf("%d \n", heap.Pop(h))
	fmt.Println("min = ",(*h)[0])
}
```
##### Max heap implementation in go

The only change required to implement a max heap from the above code is to reverse the condition of Less function.

```go
//sample code. name changed to maxHeap to avoid confusion
//puts higher values closer to the root
func (h maxHeap) Less(i, j int) bool { return h[i] > h[j] }

```
