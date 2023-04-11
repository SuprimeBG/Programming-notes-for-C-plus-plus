# Introduction to Programming with C++

<details>
<summary><b>Pointers</b></summary>


*   **Array and pointers**
```c++
    int main()
    {
    //initialize the array
        int luckyNumbers[5]; 
    
    //enter the numbers through for loop
        for (int i = 0; i <= 4; i++) {
    	      cout << "Enter a num: " << endl;  
            cin >> luckyNumbers[i];
        }
    
    //Different ways to cout the elements
    
        cout << *luckyNumbers << endl;  
    //deference the first element
    
        cout << &luckyNumbers[1] << endl; 
    //gives us the adress of the second element
    
        cout << *(luckyNumbers+2) << endl; 
    //dereference the third element after moving the adress 2 times to the right
    
        cout << luckyNumbers[2] << endl; 
    //give us the value of the third position of the array
    
    }
```

*   **Return multiple values from function using pointers**
```c++
    void getMinAndMax(int numbers[], int size, int* min, int* max) {
        for (int i =0; i <= size - 1; i++) {
            if (numbers[i] > *max) {
                *max = numbers[i];
            }
            if (numbers[i] < *min) {
                *min = numbers[i];
            }
        }
    }
    
    int main()
    {
        int luckyNumbers[5] = {5, 64, 31, 74, 2 };
        int min = luckyNumbers[0];
        int max = luckyNumbers[0];
        getMinAndMax(luckyNumbers, 5, &min, &max);
    }
```
                                  
```c++
    int getMin(int numbers[], int size) {
        int min = numbers[0];
        int i = 1;
        for (; i <= size-1; i++) {
            if (numbers[i] < min) {
                min = numbers[i];
            }
        }
        return min;
    }
    
    int getMax(int numbers[], int size) {
        int max = numbers[0];
        int i = 1;
        for (; i <= size - 1; i++) {
            if (numbers[i] > max) {
                max = numbers[i];
            }
        }
        return max;
    }
    
    
    int main()
    {
        int luckyNumbers[5] = {5, 64, 31, 74, 2 };
        cout << "Min is " << getMin(luckyNumbers, 5)<<endl;
        cout << "Max is " << getMax(luckyNumbers, 5)<<endl;
    
    }
```
    
*   **Dynamic arrays**
```c++
    int main()
    {
        int size;
        cout << "Give arr size: " << endl;
        cin >> size;
       
        //initialize dynamic memory
        int* luckyNumbers = new int[size];
    
    
        for (int i = 0; i < size; i++) {
            cout << "Array: [ " << i << " ]";
            cin >> luckyNumbers[i];
        }
        for (int i = 0; i < size; i++) {
            cout << *(luckyNumbers+i) << " ";
        }
        //deallocate memory
        delete[]luckyNumbers;
        luckyNumbers = NULL;
    }
```
                                         
*   **Multidimentionals arrays (two-dimentionals arrays)**
```c++
    int main()
    {
        int rows, col;
        cin >> rows >> col;
    
        int** matrix = new int*[rows]; 
    
        for (int i = 0; i < rows; i++) {
            matrix[i] = new int[col];
        }
        matrix[1][2] = 88;
        for (int i = 0; i < rows; i++) {
    //first we delete the 
            delete[] matrix[i];
        }
        delete[]matrix; 
    //good practice to point to NULL ptr in order to avoid crashes;
        matrix = NULL;
        
    }
```
\*\*ptr - pointer to a pointer

[Explanation of multidimentional arrays in C++](https://docs.google.com/spreadsheets/d/1hxaGMNQSqil0xuskA98oDDLKojDyHlfQOqB8ws4b2k0/edit?usp=sharing)

*   **Function Pointers**

Without parameters
```c++
    //initialize simple function
    int getNumber() {
        return 5;
    }
    
    int main()
    {
    //pointer pointing to the function 
        int(*funcPtr)(/*parameters of the function*/) = getNumber;
        cout << funcPtr();
    
    }
```

With parameters
```c++
    //initialize simple function
    int addNums(int a, int b) {
        return a + b;
    }
    
    int main()
    {
    //pointer pointing to the function
        int(*funcPtr)(int, int) = addNums;
        cout << addNums(2, 3) << endl;
        cout << funcPtr(3, 4) << endl;
    
    }
```
We use it for code optimization

*   **Smart Pointers**

unique, shared, weak
    
</details>
    
<details>
    
<summary><b>CONST</b></summary>

*   **Some common uses of CONST**
    
```c++
    const int* ptr = new int; 
    int const* ptr = new int; 
    //key is cont is before the * (asterisk)
    //both const here are the same.
    //const here means we cannot modify the content of the pointer
    
    *ptr = 5 //gives error
    ptr = (int*)
    
    /*--------------------------------------------------------------------------*/
    
    int * const ptr = new int; 
    
    /*const here means we can change the content, but we cannot
    reassign the pointer to point to something else*/
    
    /*--------------------------------------------------------------------------*/
    
    const int* const ptr = new const int;
  ```
        
</details>
