---
title: 原始指针（c + +）
description: 如何在 c + + 中使用原始指针
ms.date: 04/21/2020
helpviewer_keywords:
- pointers [C++]
no-loc:
- ':::no-loc(void):::'
- ':::no-loc(nullptr):::'
- ':::no-loc(const):::'
- ':::no-loc(char):::'
- ':::no-loc(new):::'
- ':::no-loc(delete):::'
ms.openlocfilehash: 53679559888191fe7f2aad7cb5a70d607974ae96
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233647"
---
# <a name="raw-pointers-c"></a>原始指针（c + +）

*指针*是一种类型的变量。 它将对象的地址存储在内存中，并用于访问该对象。 *原始指针*是一个指针，其生存期不受封装对象（如[智能指针](smart-pointers-modern-cpp.md)）的控制。 可以为原始指针分配另一个非指针变量的地址，也可以为其分配值 [:::no-loc(nullptr):::](:::no-loc(nullptr):::.md) 。 尚未分配值的指针包含随机数据。

还可以取消*引用*指针以检索它指向的对象的值。 *成员访问运算符*提供对象成员的访问权限。

```cpp
    int* p = :::no-loc(nullptr):::; // declare pointer and initialize it
                      // so that it doesn't store a random address
    int i = 5;
    p = &i; // assign pointer to address of object
    int j = *p; // dereference p to retrieve the value at its address
```

指针可指向类型化对象或 **`:::no-loc(void):::`** 。 当程序在内存中的[堆](https://wikipedia.org/wiki/Heap)上分配对象时，它将以指针的形式接收该对象的地址。 此类指针称为*拥有指针*。 如果不再需要堆分配的对象，则必须使用拥有指针（或它的副本）来显式释放该对象。 未能释放内存会导致*内存泄漏*，并将该内存位置呈现给计算机上的任何其他程序不可用。 使用分配 **`:::no-loc(new):::`** 的内存必须使用 **`:::no-loc(delete):::`** （或** :::no-loc(delete)::: \[ ]**）释放。 有关详细信息，请参阅[ :::no-loc(new)::: 和 :::no-loc(delete)::: 运算符](:::no-loc(new):::-and-:::no-loc(delete):::-operators.md)。

```cpp
    MyClass* mc = :::no-loc(new)::: MyClass(); // allocate object on the heap
    mc->print(); // access class member
    :::no-loc(delete)::: mc; // :::no-loc(delete)::: object (please don't forget!)
```

如果指针（未声明为 **`:::no-loc(const):::`** ），则可以递增或递减到内存中的另一个位置。 此操作称为*指针算法*。 C 样式编程中使用它来循环访问数组或其他数据结构中的元素。 **`:::no-loc(const):::`** 指针不能指向不同的内存位置，在这种情况下，与[引用](references-cpp.md)类似。 有关详细信息，请参阅[ :::no-loc(const)::: 和可变指针](:::no-loc(const):::-and-volatile-pointers.md)。

```cpp
    // declare a C-style string. Compiler adds terminating '\0'.
    :::no-loc(const)::: :::no-loc(char):::* str = "Hello world";

    :::no-loc(const)::: int c = 1;
    :::no-loc(const)::: int* p:::no-loc(const)::: = &c; // declare a non-:::no-loc(const)::: pointer to :::no-loc(const)::: int
    :::no-loc(const)::: int c2 = 2;
    p:::no-loc(const)::: = &c2;  // OK p:::no-loc(const)::: itself isn't :::no-loc(const):::
    :::no-loc(const)::: int* :::no-loc(const)::: p:::no-loc(const):::2 = &c;
    // p:::no-loc(const):::2 = &c2; // Error! p:::no-loc(const):::2 is :::no-loc(const):::.
```

在64位操作系统上，指针的大小为64位。 系统的指针大小决定了可以有多少可寻址内存。 指针指向同一内存位置的所有副本。 指针（连同引用）在 c + + 中广泛用于向函数传递更大的对象。 这是因为复制对象的地址比复制整个对象通常更有效。 在定义函数时，将指针参数指定为， **`:::no-loc(const):::`** 除非您想要函数修改对象。 通常， **`:::no-loc(const):::`** 引用是将对象传递到函数的首选方式，除非对象的值可能是 **`:::no-loc(nullptr):::`** 。

指向[函数的指针](#pointers_to_functions)使函数能够传递到其他函数，并用于 C 样式编程中的 "回调"。 现代 c + + 使用[lambda 表达式](lambda-expressions-in-cpp.md)来实现此目的。

## <a name="initialization-and-member-access"></a>初始化和成员访问

下面的示例演示如何声明、初始化和使用原始指针。 它使用 **`:::no-loc(new):::`** 来对堆上分配的对象进行初始化，该对象必须显式进行 **`:::no-loc(delete):::`** 。 该示例还演示了一些与原始指针相关的危险。 （请记住，此示例是 C 样式编程，而不是新式 c + +！）

```cpp
#include <iostream>
#include <string>

class MyClass
{
public:
    int num;
    std::string name;
    :::no-loc(void)::: print() { std::cout << name << ":" << num << std::endl; }
};

// Accepts a MyClass pointer
:::no-loc(void)::: func_A(MyClass* mc)
{
    // Modify the object that mc points to.
    // All copies of the pointer will point to
    // the same modified object.
    mc->num = 3;
}

// Accepts a MyClass object
:::no-loc(void)::: func_B(MyClass mc)
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
    // Use :::no-loc(new)::: to allocate and initialize memory
    MyClass* pmc = :::no-loc(new)::: MyClass{ 108, "Nick" };

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
    func_A(pmc);
    pmc->print(); // "Erika, 3"
    pmc2->print(); // "Erika, 3"

    // Dereference the pointer and pass a copy
    // of the pointed-to object to a function
    func_B(*pmc);
    pmc->print(); // "Erika, 3" (original not modified by function)

    :::no-loc(delete):::(pmc); // don't forget to give memory back to operating system!
   // :::no-loc(delete):::(pmc2); //crash! memory location was already :::no-loc(delete):::d
}
```

## <a name="pointer-arithmetic-and-arrays"></a>指针算法和数组

指针和数组密切相关。 当数组按值传递到函数时，它将作为指向第一个元素的指针传递。 下面的示例演示了指针和数组的以下重要属性：

- **`sizeof`** 运算符返回数组的总大小（以字节为单位）
- 若要确定元素的数目，请将总字节数除以一个元素的大小
- 当数组传递到函数时，它会*decays*到指针类型
- **`sizeof`** 应用到指针时，运算符返回指针大小、x86 上的4个字节或 x64 上的8个字节

```cpp
#include <iostream>

:::no-loc(void)::: func(int arr[], int length)
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

某些算术运算可用于非 :::no-loc(const)::: 指针，以使其指向其他内存位置。 使用 **++** 、 **+=** **-=** 和运算符递增和递减指针 **--** 。 此方法可用于数组中，在非类型化数据的缓冲区中尤其有用。 以的 **:::no-loc(void):::\*** 大小增加 **`:::no-loc(char):::`** （1个字节）。 类型化指针将按它所指向的类型的大小增加。

下面的示例演示如何使用指针算法访问 Windows 上位图中的单个像素。 请注意，和的使用 **`:::no-loc(new):::`** **`:::no-loc(delete):::`** 和取消引用运算符。

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

    :::no-loc(const):::expr int bufferSize = 30000;
    unsigned :::no-loc(char):::* buffer = :::no-loc(new)::: unsigned :::no-loc(char):::[bufferSize];

    BITMAPFILEHEADER bf;
    bf.bfType = 0x4D42;
    bf.bfSize = header.biSize + 14 + bufferSize;
    bf.bfReserved1 = 0;
    bf.bfReserved2 = 0;
    bf.bfOffBits = sizeof(BITMAPFILEHEADER) + sizeof(BITMAPINFOHEADER); //54

    // Create a gray square with a 2-pixel wide outline.
    unsigned :::no-loc(char):::* begin = &buffer[0];
    unsigned :::no-loc(char):::* end = &buffer[0] + bufferSize;
    unsigned :::no-loc(char):::* p = begin;
    :::no-loc(const):::expr int pixelWidth = 3;
    :::no-loc(const):::expr int borderWidth = 2;

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
        p++; // Increment one byte sizeof(unsigned :::no-loc(char):::).
    }

    ofstream wf(R"(box.bmp)", ios::out | ios::binary);

    wf.write(reinterpret_cast<:::no-loc(char):::*>(&bf), sizeof(bf));
    wf.write(reinterpret_cast<:::no-loc(char):::*>(&header), sizeof(header));
    wf.write(reinterpret_cast<:::no-loc(char):::*>(begin), bufferSize);

    :::no-loc(delete):::[] buffer; // Return memory to the OS.
    wf.close();
}
```

## <a name="no-locvoid-pointers"></a>:::no-loc(void):::* 指针

指向 **`:::no-loc(void):::`** 原始内存位置的指针。 有时需要使用 **:::no-loc(void):::\*** 指针，例如在 c + + 代码和 c 函数之间传递时。

将类型化的指针强制转换为 :::no-loc(void)::: 指针时，内存位置的内容将保持不变。 但类型信息会丢失，因此不能执行递增或递减操作。 例如，可以将内存位置转换为，也可以强制转换 `MyClass*` **`:::no-loc(void):::*`** 回 `MyClass*` 。 此类操作本质上容易出错，并需要小心处理 :::no-loc(void)::: 错误。 现代 c + + :::no-loc(void)::: 在几乎所有情况下都不鼓励使用指针。

```cpp

//func.c
:::no-loc(void)::: func(:::no-loc(void):::* data, int length)
{
    :::no-loc(char):::* c = (:::no-loc(char):::*)(data);

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
    :::no-loc(void)::: func(:::no-loc(void):::* data, int length);
}

class MyClass
{
public:
    int num;
    std::string name;
    :::no-loc(void)::: print() { std::cout << name << ":" << num << std::endl; }
};

int main()
{
    MyClass* mc = :::no-loc(new)::: MyClass{10, "Marian"};
    :::no-loc(void):::* p = static_cast<:::no-loc(void):::*>(mc);
    MyClass* mc2 = static_cast<MyClass*>(p);
    std::cout << mc2->name << std::endl; // "Marian"

    // use operator :::no-loc(new)::: to allocate untyped memory block
    :::no-loc(void):::* p:::no-loc(void)::: = operator :::no-loc(new):::(1000);
    :::no-loc(char):::* p:::no-loc(char)::: = static_cast<:::no-loc(char):::*>(p:::no-loc(void):::);
    for(:::no-loc(char):::* c = p:::no-loc(char):::; c < p:::no-loc(char)::: + 1000; ++c)
    {
        *c = 0x00;
    }
    func(p:::no-loc(void):::, 1000);
    :::no-loc(char)::: ch = static_cast<:::no-loc(char):::*>(p:::no-loc(void):::)[0];
    std::cout << ch << std::endl; // 'A'
    operator :::no-loc(delete):::(p);
}
```

## <a name="pointers-to-functions"></a><a name="pointers_to_functions"></a>指向函数的指针

在 C 样式编程中，函数指针主要用于将函数传递到其他函数。 此方法允许调用方自定义函数的行为而不进行修改。 在现代 c + + 中， [lambda 表达式](lambda-expressions-in-cpp.md)提供相同的功能以及更高的类型安全性和其他优点。

函数指针声明指定所指向的函数必须具有的签名：

```cpp
// Declare pointer to any function that...

// ...accepts a string and returns a string
string (*g)(string a);

// has no return value and no parameters
:::no-loc(void)::: (*x)();

// ...returns an int and takes three parameters
// of the specified types
int (*i)(int i, string s, double d);
```

下面的示例演示一个函数 `combine` ，该函数将接受的任何函数作为参数 `std::string` ，并返回 `std::string` 。 根据传递到的函数 `combine` ，它将添加或追加字符串。

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
[欢迎回到 c + +](welcome-back-to-cpp-modern-cpp.md)
