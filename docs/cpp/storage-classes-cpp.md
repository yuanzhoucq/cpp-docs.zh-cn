---
title: 存储类 （C++）|Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- thread_local_cpp
- external_cpp
- static_cpp
- register_cpp
dev_langs:
- C++
helpviewer_keywords:
- storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 659b76a640a0dfaee75179f135fee9d1eeb5ba02
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50058331"
---
# <a name="storage-classes-c"></a>存储类 (C++)

A*存储类*在上下文中的 C++ 变量声明是控制对象的生存期、 链接和内存位置的类型说明符。 给定对象只能有一个存储类。 在块中定义的变量具有自动存储，除非另有指定使用**extern**，**静态**，或`thread_local`说明符。 自动对象和变量不具有链接；它们对于块外部的代码是不可见的。

**备注**

1. [可变](../cpp/mutable-data-members-cpp.md)关键字视为存储类说明符。 但是，它只存在于类定义的成员列表中。

1. **Visual c + + 2010年及更高版本：** **自动**关键字不再是 c + + 存储类说明符，并**注册**关键字被弃用。 **Visual Studio 2017 版本 15.7 及更高版本：** (适用于[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)):**注册**从 c + + 语言中删除关键字。

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="in-this-section"></a>本节内容：

- [static](#static)
- [extern](#extern)
- [thread_local](#thread_local)

## <a name="static"></a> 静态

**静态**关键字用于声明变量和函数在全局范围、 命名空间范围和类范围。 静态变量还可在本地范围声明。

静态持续时间意味着，在程序启动时分配对象或变量，并在程序结束时释放对象或变量。 外部链接意味着，变量的名称在用于声明变量的文件的外部是可见的。 相反，内部链接意味着，名称在用于声明变量的文件的外部是不可见的。 默认情况下，在全局命名空间中定义的对象或变量具有静态持续时间和外部链接。 **静态**关键字可在以下情况下。

1. 当你声明一个变量或函数在文件范围内 (全局和/或命名空间范围)，则**静态**关键字指定变量或函数具有内部链接。 在声明变量时，变量具有静态持续时间，并且除非您指定另一个值，否则编译器会将变量初始化为 0。

1. 当你在函数中，将变量声明**静态**关键字指定该变量将保持其状态对该函数的调用之间。

1. 当你声明一个类声明中的数据成员时**静态**关键字将指定的类的所有实例共享成员的一个副本。 必须在文件范围内定义静态数据成员。 声明为整型数据成员**const 静态**可以有初始值设定项。

1. 当声明在类声明中，成员函数**静态**关键字指定的类的所有实例共享该函数。 静态成员函数不能访问实例成员，因为函数没有隐式**这**指针。 若要访问实例成员，请使用作为实例指针或引用的参数来声明函数。

1. 不能将联合成员声明为静态的。 但是，全局声明的匿名联合必须显式声明**静态**。

此示例演示如何声明的变量**静态**中函数间保持其状态对该函数的调用。

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

此示例演示如何使用**静态**类中。

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

此示例演示声明的局部变量**静态**成员函数中。 静态变量对整个程序可用；该类型的所有实例共享静态变量的同一副本。

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

从 C++11 开始，可以保证静态本地变量初始化是线程安全的。 此功能有时称为*magic 静态变量*。 但是，在多线程应用程序中，必须同步所有后续分配。 可以通过禁用线程安全的静态初始化功能[/zc: threadsafeinit-](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md)标志来避免依赖于 CRT。

## <a name="extern"></a> extern

对象和变量声明为**extern**声明另一个翻译单元中或在为具有外部链接的封闭范围中定义的对象。

声明**const**变量**extern**存储类会强制变量具有外部链接。 一个初始化**extern const**定义的翻译单元中允许使用变量。 在正在定义的翻译单元之外的翻译单元中进行初始化将生成未定义的结果。 有关详细信息，请参阅[使用 extern 指定链接](../cpp/using-extern-to-specify-linkage.md)

[/Zc: externconstexpr](../build/reference/zc-externconstexpr.md)编译器选项将使编译器要应用[外部链接]()到通过使用声明的变量`extern constexpr`。 在早期版本的 Visual Studio 中，并且默认情况下或者如果 **/Zc:externConstexpr-** 指定，则 Visual Studio 将应用到的内部链接**constexpr**变量，即使**extern**关键字使用。 **/Zc: externconstexpr**选项是从开始在 Visual Studio 2017 更新 15.6 版中提供。 和默认情况下处于关闭状态。 /Permissive-option 不会启用 /zc: externconstexpr。

下面的代码演示两个**extern**声明， `DefinedElsewhere` （引用不同的翻译单元中定义的名称） 和`DefinedHere`（引用在封闭范围中定义的名称）：

```cpp
// external.cpp
// DefinedElsewhere is defined in another translation unit
extern int DefinedElsewhere;
int main() {
   int DefinedHere;
   {
      // refers to DefinedHere in the enclosing scope
      extern int DefinedHere;
   }
}
```

## <a name="thread_local"></a> thread_local (C++ 11)

使用 `thread_local` 说明符声明的变量仅可在它在其上创建的线程上访问。 变量在创建线程时创建，并在销毁线程时销毁。 每个线程都有其自己的变量副本。 在 Windows 中，`thread_local`功能上等同于 Microsoft 专用[__declspec （线程）](../cpp/thread.md)属性。

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

需要注意的事项`thread_local`说明符：

- Dll 中的动态初始化的线程本地变量可能不正确初始化的所有调用的线程上。 有关详细信息，请参阅[线程](thread.md)。

- `thread_local`说明符可配合**静态**或**extern**。

- 您可以将应用`thread_local`仅于数据声明和定义;`thread_local`不能用于函数声明或定义。

- 只能在具有静态存储持续时间的数据项上指定 `thread_local`。 这包括全局数据对象 (同时**静态**并**extern**)，本地静态对象和类的静态数据成员。 声明的任何局部变量`thread_local`是隐式静态，如果未不提供任何其他存储类; 换而言之，在块范围内`thread_local`等效于`thread_local static`。

- 必须为线程本地对象的声明和定义指定 `thread_local`，无论声明和定义是在同一文件中发生还是在单独的文件中发生。

在 Windows 中，`thread_local`功能上等效于[__declspec （thread)](../cpp/thread.md)只不过 **__declspec （thread)** 可应用于类型定义和在 C 代码中有效。 请尽可能使用 `thread_local`，因为它是 C++ 标准的一部分，因此更易于移植。

##  <a name="register"></a>  注册

**Visual Studio 2017 版本 15.3 及更高版本**(适用于[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)):**注册**关键字不再是受支持的存储类。 关键字是仍保留供将来使用标准中。

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="example-automatic-vs-static-initialization"></a>示例： 自动与静态初始化

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

此示例演示如何以及何时对象`I1`， `I2`，和`I3`进行初始化和何时销毁它们。

有几个事项需要注意有关此计划：

- 首先，当控制流退出在其中定义 `I1` 和 `I2` 的块时，二者将自动被销毁。

- 第二，在 C++ 中，没有必要在块的开始处声明对象或变量。 此外，只有当控制流到达其定义时，才会初始化这些对象。 （`I2` 和 `I3` 是此类定义的示例。）输出说明了初始化它们的确切时间。

- 最后，静态局部变量（如 `I3`）在程序持续时间内保留其值，但在程序终止时将被销毁。

## <a name="see-also"></a>请参阅

[声明和定义](../cpp/declarations-and-definitions-cpp.md)