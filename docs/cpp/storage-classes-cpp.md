---
title: 存储类 (C++)
description: 在C++中，静态、外部和thread_local关键字指定变量或函数的生存期、链接和内存位置。
ms.date: 12/11/2019
f1_keywords:
- thread_local_cpp
- static_cpp
- register_cpp
helpviewer_keywords:
- storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
ms.openlocfilehash: 75ccb11689b4863d2d0df5edd6d066be6bd3858c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365351"
---
# <a name="storage-classes"></a>存储类

C++变量声明上下文中的*存储类*是控制对象的生存期、链接和内存位置的类型指定器。 给定对象只能有一个存储类。 在块中定义的变量具有自动存储，除非使用**外部**、**静态**或**thread_local**指定器指定。 自动对象和变量不具有链接；它们对于块外部的代码是不可见的。 当执行进入块时，将自动为其分配内存，并在模块退出时取消分配内存。

**说明**

1. [可变](../cpp/mutable-data-members-cpp.md)关键字可被视为存储类指定器。 但是，它只存在于类定义的成员列表中。

1. **视觉工作室 2010 及更高版本：****自动**关键字不再是存储类C++指定器，**寄存器**关键字被弃用。 **Visual Studio 2017 版本 15.7 及更高版本：（** 提供[/std：c++17）：](../build/reference/std-specify-language-standard-version.md)**注册**关键字从C++语言中删除。

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="static"></a><a name="static"></a>静态

**静态**关键字可用于在全局作用域、命名空间范围和类作用域中声明变量和函数。 静态变量还可在本地范围声明。

静态持续时间意味着，在程序启动时分配对象或变量，并在程序结束时释放对象或变量。 外部链接意味着，变量的名称在用于声明变量的文件的外部是可见的。 相反，内部链接意味着，名称在用于声明变量的文件的外部是不可见的。 默认情况下，在全局命名空间中定义的对象或变量具有静态持续时间和外部链接。 **静态**关键字可用于以下情况。

1. 在文件作用域（全局和/或命名空间作用域）中声明变量或函数时，**静态**关键字指定变量或函数具有内部链接。 在声明变量时，变量具有静态持续时间，并且除非您指定另一个值，否则编译器会将变量初始化为 0。

1. 在函数中声明变量时，**静态**关键字指定变量在调用该函数之间保留其状态。

1. 在类声明中声明数据成员时，**静态**关键字指定该成员的一个副本由类的所有实例共享。 必须在文件范围内定义静态数据成员。 您声明为**const 静态**的整积分数据成员可以具有初始化程序。

1. 在类声明中声明成员函数时，**静态**关键字指定该函数由类的所有实例共享。 静态成员函数无法访问实例成员，因为该函数没有隐式**此**指针。 若要访问实例成员，请使用作为实例指针或引用的参数来声明函数。

1. 不能将联合成员声明为静态的。 但是，必须显式声明全局声明的匿名联合**是静态**的 。

此示例显示函数中声明**静态**的变量如何在调用该函数之间保持其状态。

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

此示例显示在类中使用**静态**。

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

此示例显示成员函数中声明**静态**的局部变量。 静态变量对整个程序可用；该类型的所有实例共享静态变量的同一副本。

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

从 C++11 开始，可以保证静态本地变量初始化是线程安全的。 此功能有时称为*魔法静态*。 但是，在多线程应用程序中，必须同步所有后续分配。 可以使用[/Zc：线程SafeInit-](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md)标志来禁用线程安全的静态初始化功能，以避免依赖 CRT。

## <a name="extern"></a><a name="extern"></a>Extern

声明为**extern**的对象和变量声明在另一个转换单元或封闭作用域中定义的对象具有外部链接。 有关详细信息，请参阅[外部](extern-cpp.md)和[翻译单元和链接](program-and-linkage-cpp.md)。

## <a name="thread_local-c11"></a><a name="thread_local"></a>thread_local （C++11）

使用**thread_local**指定器声明的变量只能在创建该变量的线程上访问。 变量在创建线程时创建，并在销毁线程时销毁。 每个线程都有其自己的变量副本。 在 Windows 上 **，thread_local**在功能上等效于特定于 Microsoft[的__declspec（线程 ）](../cpp/thread.md)属性。

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

关于**thread_local**规格需要注意的事项：

- 并非所有调用线程上都正确初始化 DLL 中的动态初始化线程局部变量。 有关详细信息，请参阅[线程](thread.md)。

- **thread_local**规格器可与**静态**或**外部**结合。

- 您可以仅将**thread_local**应用于数据声明和定义;因此，您可以将thread_local应用于数据声明和定义。**thread_local**不能用于函数声明或定义。

- 只能对具有静态存储持续时间的数据项指定**thread_local。** 这包括全局数据对象（**静态**和**外部**）、本地静态对象和类的静态数据成员。 如果未提供其他存储类，则声明**thread_local**的任何本地变量都是隐式静态的;换句话说，在块范围**thread_local**等效于`thread_local static`。

- 您必须为线程本地对象的声明和定义指定**thread_local，** 无论声明和定义是在同一文件中发生的还是单独的文件。

在 Windows 上 **，thread_local**在功能上等效于[__declspec（线程），](../cpp/thread.md)只不过 **__declspec（线程）** 可以应用于类型定义，并且在 C 代码中有效。 尽可能使用**thread_local**因为它是C++标准的一部分，因此更加便携。

## <a name="register"></a><a name="register"></a>注册

**Visual Studio 2017 版本 15.3 及更高版本**（随[/std：c++17](../build/reference/std-specify-language-standard-version.md)提供）：**寄存器**关键字不再是受支持的存储类。 关键字仍保留在标准中以供将来使用。

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="example-automatic-vs-static-initialization"></a>示例：自动与静态初始化

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

此示例演示如何以及何时初始化对象`I1`，`I2``I3`以及何时销毁它们。

关于该程序，需要注意几点：

- 首先，当控制流退出在其中定义 `I1` 和 `I2` 的块时，二者将自动被销毁。

- 第二，在 C++ 中，没有必要在块的开始处声明对象或变量。 此外，只有当控制流到达其定义时，才会初始化这些对象。 （`I2`是`I3`此类定义的示例。输出准确显示初始化时间。

- 最后，静态局部变量（如 `I3`）在程序持续时间内保留其值，但在程序终止时将被销毁。

## <a name="see-also"></a>另请参阅

[声明和定义](../cpp/declarations-and-definitions-cpp.md)
