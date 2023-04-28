# Object-Oriented Programming in C++

<details>
<summary><b>Headers and Implementation files</b></summary>

- **Why we need Header file .h**
    
    Here we have simple function in our Main.cpp file. Problem is what happens when we have multiple .cpp files with the same functions, classes, struct and so on in them. 
    

```cpp
const char* RecomendMeFood(char FirstLetter);

int main()
{
    cout << "Today I will eat " << RecomendMeFood('c');
}

const char* RecomendMeFood(char FirstLetter) {
    if (FirstLetter == 'a' || FirstLetter == 'A')return "Apple";
    else if (FirstLetter == 'b' || FirstLetter == 'B')return "Banana";
    else if (FirstLetter == 'c' || FirstLetter == 'C')return "Chocolate cake";
    else return "Pizza";
}
```

Having multiple definitions of the same functions, classes or structures in different .cpp files can lead to errors during compilation or undefined behavior during runtime.

Program compilation is the process of converting source code into an executable program. When a C++ program is compiled, every single .cpp file is compiled into an independent compilation unit. This means that for each .cpp file, the compiler generates an .obj file. It is important to keep in mind that these compilation units are independent, which means that one .cpp file has no idea what kind of code is declared in another .cpp file.

After the compiler has generated all of the .obj files, the linker combines them into one file, which will be the application or program. This process is very simple: write .cpp files, compile them into .obj files, and link them together into one application.

It is important to note that if you want to use a function in more than one .cpp file, you need to copy its declaration in each file. However, if you try to copy the definition of a function in multiple .cpp files, you will get an error when the linker tries to link all of the .obj files together. This is because there would be more than one implementation of the same function, causing the linker to be unable to determine which implementation to use.

To solve this problem, C++ programmers often create a separate file called a header file. Inside this file, they put all of the declarations of the functions they want to use in multiple .cpp files. This way, they only need to include the header file in each .cpp file, rather than copying the declarations multiple times.

- **Creating Header file and Implementation file**

![headers-And-Implementation.png](https://i.postimg.cc/52NmmLLj/headers-And-Implementation.png "Image")
  
It is a good practice to write the Implementation file and the Header file with the same name in order to be better understood by other programmers. But technically speaking, the names of implementation files and header files do not have to match as long as they are correctly referenced in each other.

- **What Header file and Implementation file should look like**

```cpp
//Practice.h
#ifndef PRACTICE_H
#define PRACTICE_H

const char* RecomendMeFood(char FirstLetter);
//declaring the function form above
#endif
```

```cpp
//Practice.cpp (Implementation file)
#include <iostream> //so we can use cin, cout ...
#include "Practice.h"

const char* RecomendMeFood(char FirstLetter) {
    if (FirstLetter == 'a' || FirstLetter == 'A')return "Apple";
    else if (FirstLetter == 'b' || FirstLetter == 'B')return "Banana";
    else if (FirstLetter == 'c' || FirstLetter == 'C')return "Chocolate cake";
    else return "Pizza";
}
```

The “include” is a preprocessor directive meaning

- **What is `#include <iostream>`**

**iostream** is also, a header file that provides us with standart input and output commands, but it comes with your compiler (if you look for it in the Visual Studio files you can find it and open it). The difference is that you can put it inside <> and “”, where for your header files we typically use “”. This is because, if we use <> the preprocessor looks for the header file in the system directories. These are directories that are specified in the compiler's include path and typically contain standard headers. 

If we use “”, the preprocessor looks for the header file in the current directory and then in the directories specified in the include path. This is typically used for including headers that are part of your own project.

- **What is `#pragma once` and `#ifndef #define #endif`**

**`#pragma once`** and **`#ifndef`**/**`#define`**/**`#endif`** are two different ways to prevent header files from being included multiple times in a single translation unit, which can cause errors due to redefinitions of types, functions, or variables.

**`#pragma once`** is a compiler-specific directive that tells the compiler to include the header file only once per translation unit. It works by placing a marker in the preprocessor output, and the compiler checks for the presence of the marker before including the file again. It is a convenient and widely supported way to prevent multiple inclusions of a header file.

**`#ifndef`**/**`#define`**/**`#endif`** is a preprocessor technique that is more widely used and is also supported by all compilers. It works by enclosing the entire contents of a header file between **`#ifndef`** and **`#endif`** directives, with a unique identifier (usually the header file name) defined between **`#ifndef`** and **`#define`**. When the header file is included for the first time, the unique identifier is defined and the contents of the header file are included. On subsequent inclusions, the unique identifier is already defined, so the contents of the header file are skipped. This technique requires a bit more boilerplate code, but it has the advantage of being more portable across different compilers.

In general, it is a good practice to use either **`#pragma once`** or **`#ifndef`**/**`#define`**/**`#endif`** in header files to prevent multiple inclusions, and to choose one of the techniques consistently throughout a project to ensure compatibility and maintainability.
</details>
<details>
<summary><b>Constructos</b></summary>

- **Initializing the data members in the heading before the body**

```cpp
class Point2D {
public:
Point2D(double xValue, double yValue);
void print() const;
private:
double x;
double y;
};
// Initializes data-members x и y
Point2D::Point2D(double xValue, double yValue) : x(xValue), y(yValue)
{//code of body goes here...}
```

[![CPP-Constructors.png](https://i.postimg.cc/9fQNzsJ8/CPP-Constructors.png)](https://postimg.cc/RW2TDprK)

- **Parameterzided Constructor**

```cpp
class SportsCar {
private:
    char Color[64];
    char Brand[128];
    char Model[128];
    unsigned short Horsepower;

public:
    SportsCar(const char* color, const char* brand, const char* model, unsigned short horsepower) {
        strcpy_s(Color, sizeof(Color), color);
        strcpy_s(Brand, sizeof(Brand), brand);
        strcpy_s(Model, sizeof(Model), model);
        Horsepower = horsepower;

/*We use const char* when giving parameter of char array 
because we send pointer to the array*/

/*We use strcpy_s to perform a bounds check 
before copying the string, to make sure 
that the destination buffer has enough space to hold the entire source string.*/

/*We can use **#pragma warning(disable:4996)** in order to surpress the warnings, though there
is still risk of buffer overflow and security vulnerabilities. */

    }
};

int main()
{
    SportsCar Car5("Red", "Ferrari", "FF", 528);
}
```

- **Copy Constructor**

Simply said we use Copy constructor to copy the data of an object

```cpp

```
</details>
<details>
<summary><b>Destructor</b></summary>

</details>
