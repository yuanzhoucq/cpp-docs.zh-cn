---
title: 原始指针（C++）
description: 如何在中使用原始指针C++
ms.date: 11/19/2019
helpviewer_keywords:
- pointers [C++]
ms.openlocfilehash: 9ea498c254bc37dc8dc550232127cb2db3bc0886
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74250684"
---
# <a name="raw-pointers-c"></a>原始指针（C++）

指针是一种变量，它将对象的地址存储在内存中，并用于访问该对象。 *原始指针*是一个指针，其生存期不受封装对象（如[智能指针](smart-pointers-modern-cpp.md)）的控制。 可以为原始指针分配另一个非指针变量的地址，也可以为其分配值[nullptr](nullptr.md)。 尚未分配值的指针包含随机数据。

还可以取消*引用*指针以检索它指向的对象的值。 *成员访问运算符*提供对象成员的访问权限。

```cpp
    int* p = nullptr; // declare pointer and initialize it
                      // so that it doesn't store a random address
    int i = 5;
    p = &i; // assign pointer to address of object
    int j = *p; // dereference p to retrieve the value at its address

```

指针可指向类型化对象或**void**。 当程序在内存中的[堆](https://wikipedia.org/wiki/Heap)上分配新对象时，它将以指针的形式接收该对象的地址。 此类指针称为*拥有指针*;如果不再需要堆分配的对象，则必须使用拥有指针（或它的副本）显式删除该对象。 删除内存失败会导致*内存泄漏*，并将该内存位置呈现给计算机上的任何其他程序不可用。 有关详细信息，请参阅[new 和 delete 运算符](new-and-delete-operators.md)。

```cpp

    MyClass* mc = new MyClass(); // allocate object on the heap
    mc->print(); // access class member
    delete mc; // delete object (please don't forget!)
```

指针（如果不声明为**const**）可以递增或递减，使其指向内存中的新位置。 这称为*指针算法*，并在 C 样式编程中用来循环访问数组或其他数据结构中的元素。 不能将**常量**指针指向不同的内存位置，并且在这种情况下，与[引用](references-cpp.md)非常类似。 有关详细信息，请参阅[const 和 volatile 指针](const-and-volatile-pointers.md)。

```cpp
    // declare a C-style string. Compiler adds terminating '\0'.
    const char* str = "Hello world";

    const int c = 1;
    const int* pconst = &c; // declare a non-const pointer to const int
    const int c2 = 2;
    pconst = &c2;  // OK pconst itself isn't const
    const int* const pconst2 = &c; 
    // pconst2 = &c2; // Error! pconst2 is const.
```

在64位操作系统上，指针的大小为64位;系统的指针大小决定了可以有多少可寻址内存。 指针指向同一内存位置的所有副本。 指针（以及引用）广泛C++地用于向传递函数和从函数传递更大的对象，因为复制对象的64位地址比复制整个对象的效率要高得多。 在定义函数时，除非您希望函数修改对象，否则请将指针参数指定为**const** 。 通常，如果对象的值可能为**nullptr**，则**常**引用是将对象传递到函数的首选方法。

指向[函数的指针](#pointers_to_functions)使函数能够传递到其他函数，并用于 C 样式编程中的 "回调"。 新式C++使用[lambda 表达式](lambda-expressions-in-cpp.md)来实现此目的。

## <a name="initialization-and-member-access"></a>初始化和成员访问

下面的示例演示如何声明一个原始指针，并使用堆上分配的对象对其进行初始化，然后使用该指针。 它还显示了一些与原始指针相关的危险。 （请记住，这是 C 样式编程，而不C++是新式的！）

```cpp
#include <iostream>
#include <string>

class MyClass
{
public:
    int num;
    std::string name;
    void print() { std::cout << name << ":" << num << std::endl; }
};

// Accepts a MyClass pointer
void func_A(MyClass* mc)
{
    // Modify the object that mc points to.
    // All copies of the pointer will point to
    // the same modified object.
    mc->num = 3;
}

// Accepts a MyClass object
void func_B(MyClass mc)
{
    // mc here is a regular object, not a pointer.
    // Use the "." operator to access members.
    // This statement modifies only the local copy of mc.
    mc.num = 21;
    std::cout << "Local copy of mc:";
    mc.print(); // "Erika, 21"
}


int main()
{
    // Use the * operator to declare a pointer type
    // Use new to allocate and initialize memory
    MyClass* pmc = new MyClass{ 108, "Nick" };

    // Prints the memory address. Usually not what you want.
    std:: cout << pmc << std::endl;

    // Copy the pointed-to object by dereferencing the pointer
    // to access the contents of the memory location.
    // mc is a separate object, allocated here on the stack
    MyClass mc = *pmc;

    // Declare a pointer that points to mc using the addressof operator
    MyClass* pcopy = &mc;

    // Use the -> operator to access the object's public members
    pmc->print(); // "Nick, 108"

    // Copy the pointer. Now pmc and pmc2 point to same object!
    MyClass* pmc2 = pmc;

    // Use copied pointer to modify the original object
    pmc2->name = "Erika";
    pmc->print(); // "Erika, 108"
    pmc2->print(); // "Erika, 108"

    // Pass the pointer to a function.
    func_A(mc);
    pmc->print(); // "Erika, 3"
    pmc2->print(); // "Erika, 3"

    // Dereference the pointer and pass a copy
    // of the pointed-to object to a function
    func_B(*mc);
    pmc->print(); // "Erika, 3" (original not modified by function)

    delete(pmc); // don't forget to give memory back to operating system!
   // delete(pmc2); //crash! memory location was already deleted
}
```

## <a name="pointer-arithmetic-and-arrays"></a>指针算法和数组

指针和数组密切相关。 当数组按值传递到函数时，它将作为指针传递到第一个元素。 下面的示例演示了指针和数组的以下重要属性：

- `sizeof` 运算符返回数组的总大小（以字节为单位）
- 若要确定元素的数目，请将总字节数除以一个元素的大小
- 当数组传递到函数时，它会*decays*到指针类型
- 应用于指针的 `sizeof` 运算符返回指针大小、x86 上的4个字节或 x64 上的8个字节

```cpp
#include <iostream>

void func(int arr[], int length)
{
    // returns pointer size. not useful here.
    size_t test = sizeof(arr);

    for(int i = 0; i < length; ++i)
    {
        std::cout << arr[i] << " ";
    }
}

int main()
{

    int i[5]{ 1,2,3,4,5 };
    // sizeof(i) = total bytes
    int j = sizeof(i) / sizeof(i[0]);
    func(i,j);
}
```

可对非常量指针执行某些算术运算，使其指向新的内存位置。 可以使用 **++** 、 **+=** 、 **-=** 和 **--** 运算符来递增和递减指针。 此方法可用于数组中，在非类型化数据的缓冲区中尤其有用。 **Void\*** 按**字符**大小（1字节）递增。 类型化的指针按其所指向的类型的大小递增。

下面的示例演示如何使用指针算法访问 Windows 上位图中的单个像素。 请注意**new**和**delete**以及取消引用运算符的使用。 

```cpp
#include <Windows.h>
#include <fstream>

using namespace std;

int main()
{

    BITMAPINFOHEADER header;
    header.biHeight = 100; // Multiple of 4 for simplicity.
    header.biWidth = 100;
    header.biBitCount = 24;
    header.biPlanes = 1;
    header.biCompression = BI_RGB;
    header.biSize = sizeof(BITMAPINFOHEADER);

    constexpr int bufferSize = 30000;
    unsigned char* buffer = new unsigned char[bufferSize];

    BITMAPFILEHEADER bf;
    bf.bfType = 0x4D42;
    bf.bfSize = header.biSize + 14 + bufferSize;
    bf.bfReserved1 = 0;
    bf.bfReserved2 = 0;
    bf.bfOffBits = sizeof(BITMAPFILEHEADER) + sizeof(BITMAPINFOHEADER); //54

    // Create a gray square with a 2-pixel wide outline.
    unsigned char* begin = &buffer[0];
    unsigned char* end = &buffer[0] + bufferSize;
    unsigned char* p = begin;
    constexpr int pixelWidth = 3;
    constexpr int borderWidth = 2;

    while (p < end)
    {
            // Is top or bottom edge?
        if ((p < begin + header.biWidth * pixelWidth * borderWidth)
            || (p > end - header.biWidth * pixelWidth * borderWidth)
            // Is left or right edge?
            || (p - begin) % (header.biWidth * pixelWidth) < (borderWidth * pixelWidth)
            || (p - begin) % (header.biWidth * pixelWidth) > ((header.biWidth - borderWidth) * pixelWidth))
        {
            *p = 0x0; // Black
        }
        else
        {
            *p = 0xC3; // Gray
        }
        p++; // Increment one byte sizeof(unsigned char).
    }

    ofstream wf(R"(box.bmp)", ios::out | ios::binary);

    wf.write(reinterpret_cast<char*>(&bf), sizeof(bf));
    wf.write(reinterpret_cast<char*>(&header), sizeof(header));
    wf.write(reinterpret_cast<char*>(begin), bufferSize);

    delete[] buffer; // Return memory to the OS.
    wf.close();
}
```

## <a name="void-pointers"></a>void * 指针

指向**void**的指针只指向原始内存位置。 有时，有必要使用**void\*** 指针，例如，在代码和 C C++函数之间传递时。 

当类型化指针强制转换为 void 指针时，内存位置的内容将不会更改，但类型信息会丢失，因此不能执行递增或递减运算。 内存位置可以强制转换，例如从 MyClass * 转换为 void * 并再次返回到 MyClass *。 此类操作本质上容易出错，并需要非常小心来避免错误。 新式C++不鼓励使用 void 指针，除非绝对必要。

```cpp

//func.c
void func(void* data, int length)
{
    char* c = (char*)(data);

    // fill in the buffer with data
    for (int i = 0; i < length; ++i)
    {
        *c = 0x41;
        ++c;
    }
}

// main.cpp
#include <iostream>

extern "C"
{
    void func(void* data, int length);
}

class MyClass
{
public:
    int num;
    std::string name;
    void print() { std::cout << name << ":" << num << std::endl; }
};

int main()
{
    MyClass* mc = new MyClass{10, "Marian"};
    void* p = static_cast<void*>(mc);
    MyClass* mc2 = static_cast<MyClass*>(p);
    std::cout << mc2->name << std::endl; // "Marian"

    // use operator new to allocate untyped memory block
    void* pvoid = operator new(1000);
    for(char* c = static_cast<char*>(pvoid); pvoid < &pvoid + 1000; ++c)
    {
        *c = 0x00;
    }
    func(pvoid, 1000);
    char ch = static_cast<char*>(pvoid)[0];
    std::cout << ch << std::endl; // 'A'
    operator delete(p);
}
```

## <a name="pointers_to_functions"></a>指向函数的指针

在 C 样式编程中，函数指针主要用于将函数传递到其他函数。 在这种情况下，调用方可以自定义函数的行为而无需修改它。 在现代C++上， [lambda 表达式](lambda-expressions-in-cpp.md)提供相同的功能以及更高的类型安全性和其他优点。

函数指针声明指定所指向的函数必须具有的签名：

```cpp
// Declare pointer to any function that...

// ...accepts a string and returns a string
string (*g)(string a);

// has no return value and no parameters
void (*x)();

// ...returns an int and takes three parameters
// of the specified types
int (*i)(int i, string s, double d);
```

下面的示例演示一个函数 `combine`，该函数将接受 `std::string` 并返回 `std::string`的任何函数作为参数。 根据传递到 `combine` 函数，该函数会预置或追加字符串。

```cpp
#include <iostream>
#include <string>

using namespace std;

string base {"hello world"};

string append(string s)
{
    return base.append(" ").append(s);
}

string prepend(string s)
{
    return s.append(" ").append(base);
}

string combine(string s, string(*g)(string a))
{
    return (*g)(s);
}

int main()
{
    cout << combine("from MSVC", append) << "\n";
    cout << combine("Good morning and", prepend) << "\n";
}
```

## <a name="see-also"></a>另请参阅

[智能指针](smart-pointers-modern-cpp.md)
[间接寻址运算符： *](indirection-operator-star.md)<br/>
[Address-of 运算符：&](address-of-operator-amp.md)</br>
[欢迎返回到C++](welcome-back-to-cpp-modern-cpp.md)
