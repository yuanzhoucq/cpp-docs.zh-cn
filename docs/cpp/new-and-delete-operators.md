---
title: "new 和 delete 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "delete_cpp"
  - "new_cpp"
  - "new"
  - "delete"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "delete 关键字 [C++], 语法"
  - "new 关键字 [C++], 对象的动态分配"
  - "nothrownew.obj"
ms.assetid: fa721b9e-0374-4f04-bb87-032ea775bcc8
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# new 和 delete 运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 支持使用 [new](../cpp/new-operator-cpp.md) 和 [delete](../cpp/delete-operator-cpp.md) 运算符动态分配和释放对象。  这些运算符为来自称为“自由存储”的池中的对象分配内存。  `new` 运算符调用特殊函数 [operator new](../misc/operator-new-function.md)，`delete` 运算符调用特殊函数 [operator delete](../misc/operator-delete-function.md)。  
  
 在 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] .NET 2002 中，标准 C\+\+ 库中的 `new` 功能将支持 C\+\+ 标准中指定的行为，如果内存分配失败，则会引发 std::bad\_alloc 异常。  
  
 如果内存分配失败，C 运行库的 `new` 函数也将引发 std::bad\_alloc 异常。  
  
 如果您仍需要 C 运行库的 `new` 的非引发版本，请将您的程序链接到 nothrownew.obj。  但是，当您链接到 nothrownew.obj 时，标准 C\+\+ 库中的 `new` 将不再起作用。  
  
 有关包含 C 运行库和标准 C\+\+ 库的库文件的列表，请参阅 [CRT 库功能](../c-runtime-library/crt-library-features.md)。  
  
## 调用 new 运算符  
 在程序中遇到以下语句时，它将转换为对函数 `operator new` 的调用：  
  
```  
char *pch = new char[BUFFER_SIZE];  
```  
  
 如果请求针对零字节存储，**operator new** 将返回一个指向不同的对象的指针（即对 **operator new** 的重复调用将返回不同的指针）。  如果分配请求没有足够的内存，则 **operator new** 将返回 **NULL** 或引发异常（有关详细信息，请参阅 [new 和 delete 运算符](../cpp/new-and-delete-operators.md)）。  
  
 可以编写尝试释放内存的例程并重试分配；有关详细信息，请参阅 [\_set\_new\_handler](../c-runtime-library/reference/set-new-handler.md)。  有关恢复方案的更多详细信息，请参阅以下主题：[处理内存不足的情况](../misc/handling-insufficient-memory-conditions.md)。  
  
 下表中描述了 `operator new` 函数的两个范围。  
  
### operator new 函数的范围  
  
|运算符|范围|  
|---------|--------|  
|**::operator new**|全局|  
|*class\-name* **::operator new**|类|  
  
 **operator new** 的第一个参数的类型必须为 **size\_t**（STDDEF.H 中定义的类型），并且返回类型始终为 **void \***。  
  
 在使用 **new** 运算符分配内置类型的对象、不包含用户定义的 **operator new** 函数的类类型的对象和任何类型的数组时，将调用全局 **operator new** 函数。  在使用 **new** 运算符分配类类型的对象时（其中定义了 **operator new**），将调用该类的 **operator new**。  
  
 为类定义的 **operator new** 函数是静态成员函数（因此，它不能是虚函数），该函数隐藏此类类型的对象的全局 **operator new** 函数。  考虑 **new** 用于分配内存并将内存设为给定值的情况：  
  
```  
// spec1_the_operator_new_function1.cpp  
#include <malloc.h>  
#include <memory.h>  
  
class Blanks  
{  
public:  
    Blanks(){}  
    void *operator new( size_t stAllocateBlock, char chInit );  
};  
void *Blanks::operator new( size_t stAllocateBlock, char chInit )  
{  
    void *pvTemp = malloc( stAllocateBlock );  
    if( pvTemp != 0 )  
        memset( pvTemp, chInit, stAllocateBlock );  
    return pvTemp;  
}  
// For discrete objects of type Blanks, the global operator new function  
// is hidden. Therefore, the following code allocates an object of type  
// Blanks and initializes it to 0xa5  
int main()  
{  
   Blanks *a5 = new(0xa5) Blanks;  
   return a5 != 0;  
}  
```  
  
 用括号包含的提供给 **new** 的参数将作为 `Blanks::operator new` 参数传递给 `chInit`。  但是，全局 **operator new** 函数将被隐藏，从而导致以下代码生成错误：  
  
```  
Blanks *SomeBlanks = new Blanks;  
```  
  
 在 Visual C\+\+ 5.0 和早期版本中，使用 **new** 运算符分配的非类类型和所有数组（无论其类型是否为 **class**）始终使用全局 **operator new**函数。  
  
 从 Visual C\+\+ 5.0 开始，编译器支持类声明中的成员数组 **new** 和 **delete** 运算符。  例如:  
  
```  
// spec1_the_operator_new_function2.cpp  
class MyClass  
{  
public:  
   void * operator new[] (size_t)  
   {  
      return 0;  
   }  
   void   operator delete[] (void*)  
   {  
   }  
};  
  
int main()   
{  
   MyClass *pMyClass = new MyClass[5];  
   delete [] pMyClass;  
}  
```  
  
### 处理内存不足  
 对失败的内存分配进行测试可以通过如下编码实现：  
  
```  
// insufficient_memory_conditions.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
#define BIG_NUMBER 100000000  
int main() {  
   int *pI = new int[BIG_NUMBER];  
   if( pI == 0x0 ) {  
      cout << "Insufficient memory" << endl;  
      return -1;  
   }  
}  
```  
  
 处理失败的内存分配要求的其他方法：编写自定义恢复例程来处理此类失败，然后通过调用 [\_set\_new\_handler](../c-runtime-library/reference/set-new-handler.md) 运行时函数来注册您的函数。  
  
## delete 运算符  
 可使用 **delete** 运算符释放使用 **new** 运算符动态分配的内存。  delete 运算符调用 **operator delete**函数，该函数将内存释放回可用池。  使用 **delete** 运算符也会导致调用类析构函数（如果有）。  
  
 存在全局和类范围的 **operator delete**函数。  只能为给定类定义一个 **operator delete**函数；如果定义了该函数，它会隐藏全局 **operator delete**函数。  始终为所有类型的数组调用全局 **operator delete**函数。  
  
 全局 **operator delete**函数（如果已声明）采用 **void \*** 类型的单个参数，该参数包含指向要释放的对象的指针。  返回类型是 `void`（**operator delete** 无法返回值）。  类成员 **operator delete** 函数有两种形式：  
  
```  
void operator delete( void * );  
void operator delete( void *, size_t );  
```  
  
 给定类中只存在前面两个变量中的一个。  第一个形式按照为全局 `operator delete` 描述的那样运行。  第二个形式采用两个参数，第一个是指向要释放的内存块的指针，第二个是要释放的字节的数量。  当基类中的 **operator delete** 函数用于删除派生类的对象时，第二个形式特别有用。  
  
 **operator delete** 函数是静态的；因此它不能是虚函数。  `operator delete` 函数服从访问控制，如[成员访问控制](../cpp/member-access-control-cpp.md)中所述。  
  
 以下示例显示旨在记录内存的分配和释放的用户定义的 **operator new** 和 **operator delete** 函数：  
  
```  
// spec1_the_operator_delete_function1.cpp  
// compile with: /EHsc  
// arguments: 3  
#include <iostream>  
using namespace std;  
  
int fLogMemory = 0;      // Perform logging (0=no; nonzero=yes)?  
int cBlocksAllocated = 0;  // Count of blocks allocated.  
  
// User-defined operator new.  
void *operator new( size_t stAllocateBlock ) {  
   static int fInOpNew = 0;   // Guard flag.  
  
   if ( fLogMemory && !fInOpNew ) {  
      fInOpNew = 1;  
      clog << "Memory block " << ++cBlocksAllocated  
          << " allocated for " << stAllocateBlock  
          << " bytes\n";  
      fInOpNew = 0;  
   }  
   return malloc( stAllocateBlock );  
}  
  
// User-defined operator delete.  
void operator delete( void *pvMem ) {  
   static int fInOpDelete = 0;   // Guard flag.  
   if ( fLogMemory && !fInOpDelete ) {  
      fInOpDelete = 1;  
      clog << "Memory block " << cBlocksAllocated--  
          << " deallocated\n";  
      fInOpDelete = 0;  
   }  
  
   free( pvMem );  
}  
  
int main( int argc, char *argv[] ) {  
   fLogMemory = 1;   // Turn logging on  
   if( argc > 1 )  
      for( int i = 0; i < atoi( argv[1] ); ++i ) {  
         char *pMem = new char[10];  
         delete[] pMem;  
      }  
   fLogMemory = 0;  // Turn logging off.  
   return cBlocksAllocated;  
}  
```  
  
 前面的代码可用于检测“内存溢出”，即在自由储存中分配但从未释放过的内存。  若要执行此检测，则应重新定义全局 **new** 和 **delete** 运算符以计算内存的分配和释放。  
  
 从 Visual C\+\+ 5.0 开始，编译器支持类声明中的成员数组 **new** 和 **delete** 运算符。  例如:  
  
```  
// spec1_the_operator_delete_function2.cpp  
// compile with: /c  
class X  {  
public:  
   void * operator new[] (size_t) {  
      return 0;  
   }  
   void operator delete[] (void*) {}  
};  
  
void f() {  
   X *pX = new X[5];  
   delete [] pX;  
}  
```  
  
## 请参阅  
 [特殊成员函数](../misc/special-member-functions-cpp.md)