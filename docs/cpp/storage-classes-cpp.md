---
title: 存储类 (C++)
description: 在 c + + 中，static、extern 和 thread_local 关键字指定变量或函数的生存期、链接和内存位置。
ms.date: 12/11/2019
f1_keywords:
- thread_local_cpp
- static_cpp
- register_cpp
helpviewer_keywords:
- storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
ms.openlocfilehash: c3fc87980d1fd0af5b803a8e590855f6429c847e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213159"
---
# <a name="storage-classes"></a>存储类

C + + 变量声明上下文中的*存储类*是一种类型说明符，该说明符控制对象的生存期、链接和内存位置。 给定对象只能有一个存储类。 在块中定义的变量具有自动存储，除非使用 **`extern`** 、或说明符进行了指定 **`static`** **`thread_local`** 。 自动对象和变量不具有链接；它们对于块外部的代码是不可见的。 当执行进入块并在退出块时取消分配时，将自动为其分配内存。

**备注**

1. [可变](../cpp/mutable-data-members-cpp.md)关键字可视为存储类说明符。 但是，它只存在于类定义的成员列表中。

1. **Visual Studio 2010 及更高版本：****`auto`** 关键字不再是 c + + 存储类说明符，并且 **`register`** 关键字已弃用。 **Visual Studio 2017 版本15.7 及更高版本：** （可用于 [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) ）： **`register`** 从 c + + 语言中删除关键字。

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="static"></a><a name="static"></a> `static`

**`static`** 关键字可用于声明全局范围、命名空间范围和类范围内的变量和函数。 静态变量还可在本地范围声明。

静态持续时间意味着，在程序启动时分配对象或变量，并在程序结束时释放对象或变量。 外部链接意味着，变量的名称在用于声明变量的文件的外部是可见的。 相反，内部链接意味着，名称在用于声明变量的文件的外部是不可见的。 默认情况下，在全局命名空间中定义的对象或变量具有静态持续时间和外部链接。 **`static`** 关键字可用于以下情况。

1. 在文件范围（全局和/或命名空间范围）声明变量或函数时，关键字将 **`static`** 指定变量或函数具有内部链接。 在声明变量时，变量具有静态持续时间，并且除非您指定另一个值，否则编译器会将变量初始化为 0。

1. 在函数中声明变量时， **`static`** 关键字指定该变量在调用该函数时保持其状态。

1. 在类声明中声明数据成员时， **`static`** 关键字指定成员的一个副本由类的所有实例共享。 必须在文件范围内定义静态数据成员。 声明为的整型数据成员 **`const static`** 可以有初始值设定项。

1. 在类声明中声明成员函数时， **`static`** 关键字指定该函数由类的所有实例共享。 静态成员函数不能访问实例成员，因为该函数没有隐式 **`this`** 指针。 若要访问实例成员，请使用作为实例指针或引用的参数来声明函数。

1. 不能将联合成员声明为静态的。 但是，全局声明的匿名联合必须是显式声明的 **`static`** 。

此示例演示如何 **`static`** 在函数中声明的变量在调用该函数时保持其状态。

```cpp
// static1.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
void showstat( int curr ) {
   static int nStatic;    // Value of nStatic is retained
                          // between each function call
   nStatic += curr;
   cout << "nStatic is " << nStatic << endl;
}

int main() {
   for ( int i = 0; i < 5; i++ )
      showstat( i );
}
```

```Output
nStatic is 0
nStatic is 1
nStatic is 3
nStatic is 6
nStatic is 10
```

此示例演示如何 **`static`** 在类中使用。

```cpp
// static2.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class CMyClass {
public:
   static int m_i;
};

int CMyClass::m_i = 0;
CMyClass myObject1;
CMyClass myObject2;

int main() {
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   myObject1.m_i = 1;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   myObject2.m_i = 2;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   CMyClass::m_i = 3;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;
}
```

```Output
0
0
1
1
2
2
3
3
```

此示例显示了 **`static`** 成员函数中声明的局部变量。 **`static`** 变量可用于整个程序; 该类型的所有实例共享该变量的相同副本 **`static`** 。

```cpp
// static3.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
struct C {
   void Test(int value) {
      static int var = 0;
      if (var == value)
         cout << "var == value" << endl;
      else
         cout << "var != value" << endl;

      var = value;
   }
};

int main() {
   C c1;
   C c2;
   c1.Test(100);
   c2.Test(100);
}
```

```Output
var != value
var == value
```

从 c + + 11 开始， **`static`** 本地变量初始化保证是线程安全的。 此功能有时称为 "*幻静态*"。 但是，在多线程应用程序中，必须同步所有后续分配。 可以通过使用标志来禁用线程安全静态初始化功能， [`/Zc:threadSafeInit-`](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md) 以避免依赖于 CRT。

## <a name="extern"></a><a name="extern"></a> `extern`

声明为的对象和变量 **`extern`** 声明的对象是在另一个翻译单元中定义的，或是在包含外部链接的封闭范围中定义的。 有关详细信息，请参阅 [`extern`](extern-cpp.md) 和[翻译单元和链接](program-and-linkage-cpp.md)。

## <a name="thread_local-c11"></a><a name="thread_local"></a>`thread_local`（C + + 11）

使用说明符声明的变量 **`thread_local`** 只能在创建它的线程上访问。 变量在创建线程时创建，并在销毁线程时销毁。 每个线程都有其自己的变量副本。 在 Windows 上，在 **`thread_local`** 功能上等效于 Microsoft 特定的 [`__declspec( thread )`](../cpp/thread.md) 属性。

```cpp
thread_local float f = 42.0; // Global namespace. Not implicitly static.

struct S // cannot be applied to type definition
{
    thread_local int i; // Illegal. The member must be static.
    thread_local static char buf[10]; // OK
};

void DoSomething()
{
    // Apply thread_local to a local variable.
    // Implicitly "thread_local static S my_struct".
    thread_local S my_struct;
}
```

有关说明符的注意事项 **`thread_local`** ：

- Dll 中动态初始化的线程局部变量在所有调用线程上可能未正确初始化。 有关详细信息，请参阅 [`thread`](thread.md)。

- **`thread_local`** 说明符可以与或组合在 **`static`** 一起 **`extern`** 。

- 只能应用 **`thread_local`** 于数据声明和定义; **`thread_local`** 不能用于函数声明或定义。

- 只能 **`thread_local`** 在具有静态存储持续时间的数据项上指定。 这包括全局数据对象（ **`static`** 和 **`extern`** ）、本地静态对象和类的静态数据成员。 **`thread_local`** 如果未提供任何其他存储类，则声明的任何局部变量都是隐式的; 换言之，在块范围 **`thread_local`** 等效于 **`thread_local static`** 。

- 必须 **`thread_local`** 同时为线程本地对象的声明和定义指定，声明和定义是出现在同一文件中还是单独的文件中。

在 Windows 上，在 **`thread_local`** 功能上等效于 [`__declspec(thread)`](../cpp/thread.md) ，只不过 *`*__declspec(thread)`* * 可应用于类型定义，并在 C 代码中有效。 请尽可能使用， **`thread_local`** 因为它是 c + + 标准的一部分，因此更易于移植。

## <a name="register"></a><a name="register"></a>注册

**Visual Studio 2017 版本15.3 及更高版本**（与一起提供 [`/std:c++17`](../build/reference/std-specify-language-standard-version.md) ）： **`register`** 关键字不再是受支持的存储类。 关键字仍保留在标准中，供将来使用。

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="example-automatic-vs-static-initialization"></a>示例：自动和静态初始化

当控制流到达其定义时，就会初始化本地自动对象或变量。 当控制流首次到达其定义时，将初始化本地静态对象或变量。

考虑以下示例，该示例定义一个记录对象的初始化和析构的类，然后定义三个对象（即 `I1`、`I2` 和 `I3`）：

```cpp
// initialization_of_objects.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>
using namespace std;

// Define a class that logs initializations and destructions.
class InitDemo {
public:
    InitDemo( const char *szWhat );
    ~InitDemo();

private:
    char *szObjName;
    size_t sizeofObjName;
};

// Constructor for class InitDemo
InitDemo::InitDemo( const char *szWhat ) :
    szObjName(NULL), sizeofObjName(0) {
    if ( szWhat != 0 && strlen( szWhat ) > 0 ) {
        // Allocate storage for szObjName, then copy
        // initializer szWhat into szObjName, using
        // secured CRT functions.
        sizeofObjName = strlen( szWhat ) + 1;

        szObjName = new char[ sizeofObjName ];
        strcpy_s( szObjName, sizeofObjName, szWhat );

        cout << "Initializing: " << szObjName << "\n";
    }
    else {
        szObjName = 0;
    }
}

// Destructor for InitDemo
InitDemo::~InitDemo() {
    if( szObjName != 0 ) {
        cout << "Destroying: " << szObjName << "\n";
        delete szObjName;
    }
}

// Enter main function
int main() {
    InitDemo I1( "Auto I1" ); {
        cout << "In block.\n";
        InitDemo I2( "Auto I2" );
        static InitDemo I3( "Static I3" );
    }
    cout << "Exited block.\n";
}
```

```Output
Initializing: Auto I1
In block.
Initializing: Auto I2
Initializing: Static I3
Destroying: Auto I2
Exited block.
Destroying: Auto I1
Destroying: Static I3
```

此示例演示如何以及何时初始化对象 `I1` 、 `I2` 和，以及何时对 `I3` 它们进行销毁。

有关该计划，请注意以下几点：

- 首先，当控制流退出在其中定义 `I1` 和 `I2` 的块时，二者将自动被销毁。

- 第二，在 C++ 中，没有必要在块的开始处声明对象或变量。 此外，只有当控制流到达其定义时，才会初始化这些对象。 （ `I2` 和 `I3` 是此类定义的示例。）输出显示初始化的确切时间。

- 最后，静态局部变量（如 `I3`）在程序持续时间内保留其值，但在程序终止时将被销毁。

## <a name="see-also"></a>另请参阅

[声明和定义](../cpp/declarations-and-definitions-cpp.md)
