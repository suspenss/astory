+++
 title = "Basic data struct" 
 date = "2022-10-24T21:05:48+08:00" 
 tags = ["C","data struct"] 
 slug = "basic_data_struct"
 align = false
+++
## list
list as a abstract data type .      
list is a common data struct , it can store a given number of elements of a given data-type , write or modify element of a position , and read element at a posion. In smoe programing language , array is a data struct , it can give us same implementation  of  list, but array need set size in advance and can't change  the fixed size under normal circumstances.
```
int a[1] = {1,2,};  // a array named 'a', size of 2*int, a[0] = 1, a[1] = 2 
```

c language provide some function in `<stdlib.h>`  to change the size of array.
```
malloc:
void* malloc (size_t size);

realloc:
void* realoc (void* per, size_t size);

calloc:
void* calloc (size_t num, size_t size);
```
Even so , the function don't look so smart.

Now , we need a dynamic list whose can grow according to my needs. So the feature of the list is following:
1. Its size is zero when it is empty.
2. Insert, remove, count some elements at any position 
3. Read/modify element at aposition
4. Specity data-type when build this list.        

The above function can also be implemented using an array but  it's complicated because the arrays are contigous in memory and logic. 

### Linked list
  
