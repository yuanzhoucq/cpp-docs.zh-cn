---
title: 原始指针 （C++）
description: 如何使用原始指针C++
ms.date: 11/19/2019
helpviewer_keywords:
- pointers [C++]
ms.openlocfilehash: 919447fcab123ce6b838391d3cc295fb8a8fe95e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374665"
---
# <a name="raw-pointers-c"></a>原始指针 （C++）

指针是一种变量类型，用于将对象的地址存储在内存中，并用于访问该对象。 *原始指针*是一个指针，其生存期不受封装对象（如[智能指针](smart-pointers-modern-cpp.md)）控制的控制。 可以为原始指针分配另一个非指针变量的地址，也可以为其分配[nullptr](nullptr.md)的值。 尚未分配值的指针包含随机数据。

也可以*取消引用*指针以检索它指向的对象的值。 *成员访问运算符*提供对对象成员的访问。

```cpp
    int* p = nullptr; // declare pointer and initialize it
                      // so that it doesn't store a random address
    int i = 5;
    p = &i; // assign pointer to address of object
    int j = *p; // dereference p to retrieve the value at its address

```

指针可以指向类型化对象或**void**。 当程序在内存中的[堆](https://wikipedia.org/wiki/Heap)上分配新对象时，它将以指针的形式接收该对象的地址。 此类指针称为*拥有指针*;必须使用拥有指针（或其副本）在不再需要堆分配的对象时显式删除它。 未能删除内存会导致*内存泄漏*，并使该内存位置对计算机上的任何其他程序不可用。 有关详细信息，请参阅[新的运算符和删除运算符](new-and-delete-operators.md)。

```cpp

    MyClass* mc = new MyClass(); // allocate object on the heap
    mc->print(); // access class member
    delete mc; // delete object (please don't forget!)
```

指针（如果未声明为**const）** 可以递增或递减，以便指向内存中的新位置。 这称为*指针算术*，用于 C 样式编程，用于迭代数组或其他数据结构中的元素。 不能用**const**指针指向不同的内存位置，因此与[引用](references-cpp.md)非常相似。 有关详细信息，请参阅[const 和易失性指针](const-and-volatile-pointers.md)。

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

在 64 位操作系统上，指针的大小为 64 位;系统的指针大小决定了它可以具有多少可寻址内存。 指针的所有副本都指向同一内存位置。 指针（以及引用）在C++中广泛使用，用于将较大的对象传递到函数，因为复制对象的 64 位地址通常比复制整个对象更有效。 定义函数时，将指针参数指定为**const，** 除非您打算让函数修改对象。 通常 **，const**引用是将对象传递给函数的首选方法，除非对象的值可能是**nullptr。**

[函数的指针](#pointers_to_functions)允许函数传递到其他函数，并用于 C 样式编程中的"回调"。 现代C++为此使用[lambda 表达式](lambda-expressions-in-cpp.md)。

## <a name="initialization-and-member-access"></a>初始化和成员访问

下面的示例演示如何声明原始指针并使用在堆上分配的对象初始化它，以及如何使用它。 它还显示了与原始指针相关的一些危险。 （请记住，这是 C 样式编程，而不是现代C++！

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

## <a name="pointer-arithmetic-and-arrays"></a>指针算术和数组

指针和数组密切相关。 当数组通过值传递给函数时，它作为指向第一个元素的指针传递。 下面的示例演示了指针和数组的以下重要属性：

- 运算符`sizeof`返回数组的总大小（以字节为单位）
- 确定元素数，将总字节除以一个元素的大小
- 当数组传递给函数时，它将*衰减*为指针类型
- 当`sizeof`应用于指针时，运算符返回指针大小，x86 上为 4 个字节，在 x64 上返回 8 个字节

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

可以对非 const 指针执行某些算术运算，使它们指向新的内存位置。 可以使用**++**、**+=****-=** 和**--** 运算符递增和递减指针。 此技术可用于数组，在未键入数据的缓冲区中特别有用。 **空隙\*** 以**字符**（1 字节）的大小递增。 类型化指针按其指向的类型的大小递增。

下面的示例演示如何使用指针算术访问 Windows 上的位图中的单个像素。 请注意**使用 new**和**delete**， 以及取消引用运算符。

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

## <a name="void-pointers"></a>空* 指针

指向**void**的指针仅指向原始内存位置。 有时需要使用**void\*** 指针，例如，在C++代码和 C 函数之间传递时。

当类型化指针被强制转换为 void 指针时，内存位置的内容不会更改，但类型信息将丢失，因此无法执行增量或递减操作。 例如，可以将内存位置强制转换，例如，从 MyClass® 到 void*，然后再次转换回 MyClass*。 此类操作本质上是容易出错的，需要非常小心以避免错误。 除非绝对必要，否则现代C++禁止使用无效指针。

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
    char* pchar = static_cast<char*>(pvoid);
    for(char* c = pchar; c < pchar + 1000; ++c)
    {
        *c = 0x00;
    }
    func(pvoid, 1000);
    char ch = static_cast<char*>(pvoid)[0];
    std::cout << ch << std::endl; // 'A'
    operator delete(p);
}
```

## <a name="pointers-to-functions"></a><a name="pointers_to_functions"></a>指向函数的指针

在 C 样式编程中，函数指针主要用于将函数传递给其他函数。 在这种情况下，调用方可以自定义函数的行为，而无需对其进行修改。 在现代C++中[，lambda 表达式](lambda-expressions-in-cpp.md)提供了相同的功能，具有更大的类型安全性和其他优势。

函数指针声明指定指向函数必须具有的签名：

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

下面的示例显示一个函数`combine`，该函数将接受`std::string`和 返回 的任何函数作为`std::string`参数。 根据传递给`combine`它的函数，将预置或追加字符串。

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
[方向运算符： |](indirection-operator-star.md)<br/>
[Address-of 运算符：&](address-of-operator-amp.md)</br>
[欢迎回到C++](welcome-back-to-cpp-modern-cpp.md)
