---
layout: post
title: "Some useful tips for C and C++"
---

# Here are some useful tips I summarized for C and C++

1. When we initialize an int vector, int array, etc., they are filled with 0s.

2. `T* ptr = new T(value)` is equivalent to `T* ptr = new T[1] {value}` ((value) and {value} can be omitted.)

3. The public interface is inherited to the inherited class. (The interface of the base class is a subset of the derived class.)

4. We must initialize static data members outside of the class: 

    ```c++
    class foo {
        static int var;
    }
    
    int foo::var = 0;  
    ```  

5. Use virtual destructors when there are virtual methods in the base class.

6. When we write to a file, the data is first stored in the buffer. When the buffer is flushed, the data is written into the file.
