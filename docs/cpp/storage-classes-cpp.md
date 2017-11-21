---
title: "存储类 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- thread_local_cpp
- external_cpp
- static_cpp
dev_langs: C++
helpviewer_keywords: storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3830f91683399eba4784b5348ca252e9caa22d57
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="storage-classes-c"></a>存储类 (C++)  
  
A*存储类*在上下文中的 c + + 变量声明是控制对象的生存期、 链接和内存位置的类型说明符。 给定对象只能有一个存储类。 除非使用 `extern`、`static` 或 `thread_local` 说明符另行指定，否则在块中定义的变量具有自动存储。 自动对象和变量不具有链接；它们对于块外部的代码是不可见的。  
  
**注意**  
  
1.  [可变](../cpp/mutable-data-members-cpp.md)关键字可视为存储类说明符。 但是，它只存在于类定义的成员列表中。  
  
2.  **Visual c + + 2010年及更高版本：** `auto`关键字不再是 c + + 存储类说明符，和`register`关键字被弃用。 **Visual Studio 2017 15.3 及更高版本：** (适用于[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)):`register`关键字已不再受支持的存储类。 关键字是仍保留在将来使用的标准。 
```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="in-this-section"></a>本节内容：
  
-   [static](#static)  
-   [extern](#extern)  
-   [thread_local](#thread_local)

<a name="static"></a>
  
## <a name="static"></a>静态  
  
`static` 关键字可用于在全局范围、命名空间范围和类范围声明变量和函数。 静态变量还可在本地范围声明。  
  
静态持续时间意味着，在程序启动时分配对象或变量，并在程序结束时释放对象或变量。 外部链接意味着，变量的名称在用于声明变量的文件的外部是可见的。 相反，内部链接意味着，名称在用于声明变量的文件的外部是不可见的。 默认情况下，在全局命名空间中定义的对象或变量具有静态持续时间和外部链接。 在以下情况下，可使用 `static` 关键字。  
  
1.  在文件范围（全局和/或命名空间范围）内声明变量或函数时，`static` 关键字将指定变量或函数具有内部链接。 在声明变量时，变量具有静态持续时间，并且除非您指定另一个值，否则编译器会将变量初始化为 0。  
  
2.  在函数中声明变量时，`static` 关键字将指定变量将在对该函数的调用中保持其状态。  
  
3.  在类声明中声明数据成员时，`static` 关键字将指定类的所有实例共享该成员的一个副本。 必须在文件范围内定义静态数据成员。 你将声明为整型数据成员`const static`可以有初始值设定项。  
  
4.  在类声明中声明成员函数时，`static` 关键字将指定类的所有实例共享该函数。 由于函数没有隐式 `this` 指针，因此静态成员函数不能访问实例成员。 若要访问实例成员，请使用作为实例指针或引用的参数来声明函数。  
  
5.  不能将联合成员声明为静态的。 但是，全局声明的匿名联合必须是显式声明的 `static`。  
  
此示例演示如何声明的变量`static`函数中将保留其状态对该函数的调用之间。  
  
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
  
此示例演示如何使用`static`类中。  
  
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
  
此示例演示声明的局部变量`static`成员函数中。 静态变量对整个程序可用；该类型的所有实例共享静态变量的同一副本。  
  
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
  
从 C++11 开始，可以保证静态本地变量初始化是线程安全的。 此功能有时称为*神奇的静态对象*。 但是，在多线程应用程序中，必须同步所有后续分配。 可以通过使用禁用线程安全的静态初始化功能[/Zc:threadSafeInit-](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md)标志以避免对 crt 产生的依赖关系。  
  
<a name="extern"></a>  
  
## <a name="extern"></a>extern  
  
声明为 `extern` 的对象和变量将在另一个翻译单元或在一个封闭范围中定义的对象声明为具有外部链接。  
  
声明`const`变量`extern`存储类强制变量具有外部链接。 初始化`extern const`中定义的翻译单元允许变量。 在正在定义的翻译单元之外的翻译单元中进行初始化将生成未定义的结果。 有关详细信息，请参阅[使用 extern 指定链接](../cpp/using-extern-to-specify-linkage.md)  
  
以下代码显示了两个 `extern` 声明：`DefinedElsewhere`（引用在不同翻译单元中定义的名称）和 `DefinedHere`（引用在封闭范围内定义的名称）：  
  
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
  
<a name="thread_local"></a>  
  
## <a name="threadlocal-c11"></a>thread_local (C++11)  
  
使用 `thread_local` 说明符声明的变量仅可在它在其上创建的线程上访问。 变量在创建线程时创建，并在销毁线程时销毁。 每个线程都有其自己的变量副本。 在 Windows 上，`thread_local`功能上等效于特定于 Microsoft 的[__declspec (thread)](../cpp/thread.md)属性。  
  
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
  
-  `thread_local`说明符可以与组合`static`或`extern`。  
  
-  你可以将应用`thread_local`仅于数据声明和定义;`thread_local`不能用于函数声明或定义。  
  
-  使用`thread_local`可能会影响[延迟加载](../build/reference/linker-support-for-delay-loaded-dlls.md)DLL 导入。 
  
-  在 XP 系统上`thread_local`如果 DLL 使用可能无法正常运行`thread_local`数据和它通过动态加载`LoadLibrary`。  
  
-  只能在具有静态存储持续时间的数据项上指定 `thread_local`。 这包括全局数据对象 (同时`static`和`extern`)，本地静态对象和类的静态数据成员。 任何本地变量声明`thread_local`是隐式静态，如果没有任何其他存储类提供; 换而言之，在块范围`thread_local`等效于`thread_local static`。 
  
-  必须为线程本地对象的声明和定义指定 `thread_local`，无论声明和定义是在同一文件中发生还是在单独的文件中发生。  
  
在 Windows 上，`thread_local`功能上等效于[__declspec （thread)](../cpp/thread.md)只不过`__declspec(thread)`可以应用于类型定义，并且在 C 代码中有效。 请尽可能使用 `thread_local`，因为它是 C++ 标准的一部分，因此更易于移植。  
  
##  <a name="register"></a>注册  
**Visual Studio 2017 15.3 及更高版本**(适用于[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)):`register`关键字已不再受支持的存储类。 关键字是仍保留在将来使用的标准。 

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
  
此示例演示如何以及何时对象`I1`， `I2`，和`I3`初始化和何时销毁它们。  
  
有几个事项需要注意有关此计划：  
  
- 首先，当控制流退出在其中定义 `I1` 和 `I2` 的块时，二者将自动被销毁。  
  
- 第二，在 C++ 中，没有必要在块的开始处声明对象或变量。 此外，只有当控制流到达其定义时，才会初始化这些对象。 （`I2` 和 `I3` 是此类定义的示例。）输出说明了初始化它们的确切时间。  
  
- 最后，静态局部变量（如 `I3`）在程序持续时间内保留其值，但在程序终止时将被销毁。  
  
## <a name="see-also"></a>另请参阅  
  
 [声明和定义](../cpp/declarations-and-definitions-cpp.md)
