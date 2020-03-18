---
title: new 和 delete 运算符
ms.date: 11/19/2019
helpviewer_keywords:
- new keyword [C++]
- delete keyword [C++]
ms.assetid: fa721b9e-0374-4f04-bb87-032ea775bcc8
ms.openlocfilehash: 2fd665ce2570bbe7750684057cdf7f517f6f64f3
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445455"
---
# <a name="new-and-delete-operators"></a>new 和 delete 运算符

C++支持使用[new](new-operator-cpp.md)和[delete](delete-operator-cpp.md)运算符动态分配和释放对象。 这些运算符为来自称为“自由存储”的池中的对象分配内存。 **New**运算符调用特殊函数[运算符 new](new-operator-cpp.md)， **delete**运算符调用特殊函数[运算符 delete](delete-operator-cpp.md)。

标准库中的**新**函数支持在C++标准中指定的行为，如果内存分配失败，则将引发 std：： bad_alloc 异常。 C++ 如果仍需要**新**的非引发版本，请将程序与 nothrownew.obj 链接。但是，当你链接到 nothrownew.obj 时， C++标准库中的默认**运算符 new**将不再工作。

有关包含 C 运行库和C++标准库的库文件的列表，请参阅[CRT 库功能](../c-runtime-library/crt-library-features.md)。

##  <a id="new_operator"> </a> New 运算符

如果程序中遇到如下语句，它将转换为对函数**运算符 new**的调用：

```cpp
char *pch = new char[BUFFER_SIZE];
```

如果请求的存储空间为零字节，则**operator new**将返回指向不同对象的指针（即对**operator new**的重复调用将返回不同的指针）。 如果分配请求没有足够的内存，则**operator new**将引发 `std::bad_alloc` 异常，如果已链接到非引发**运算符的新**支持，则返回**nullptr** 。

可以编写一个例程来尝试释放内存，然后重试分配;有关详细信息，请参阅[_set_new_handler](../c-runtime-library/reference/set-new-handler.md) 。 有关恢复方案的更多详细信息，请参阅本主题的处理内存不足部分。

下表描述了**operator new**函数的两个作用域。

### <a name="scope-for-operator-new-functions"></a>Operator new 函数的作用域

|运算符|范围|
|--------------|-----------|
|**：： new 运算符**|Global|
|*类名* **：： operator new**|类|

**Operator new**的第一个参数的类型必须为 `size_t` （在 \<stddef.h > 中定义的类型），并且返回类型始终为**void** <strong>\*</strong>。

当使用**new**运算符分配内置类型的对象、不包含用户定义的**operator new**函数的类类型的对象和任何类型的数组时，将调用全局**operator new**函数。 当使用**new**运算符分配定义了 new**运算符**的类类型的对象时，将调用该类的**operator new** 。

为类定义的**operator new**函数是静态成员函数（因此，它不能是虚函数），该函数隐藏此类类型的对象的全局**operator new**函数。 请考虑使用**new**分配内存并将其设置为给定值的情况：

```cpp
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

向**new**括号中提供的参数将作为 `chInit` 参数传递给 `Blanks::operator new`。 但是，全局**operator new**函数是隐藏的，导致如下代码生成错误：

```cpp
Blanks *SomeBlanks = new Blanks;
```

编译器在类声明中支持成员数组**new**和**delete**运算符。 例如：

```cpp
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

### <a name="handling-insufficient-memory"></a>处理内存不足

可按如下所示对失败的内存分配进行测试：

```cpp
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

还可以通过另一种方法来处理失败的内存分配请求。 编写自定义恢复例程来处理此类故障，并通过调用[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)运行时函数来注册该函数。

##  <a id="delete_operator"> </a> Delete 运算符

使用**new**运算符动态分配的内存可以使用**delete**运算符释放。 Delete 运算符调用**operator delete**函数，该函数将内存释放回可用池。 使用**delete**运算符还会导致调用类析构函数（如果有）。

存在全局和类范围的**运算符 delete**函数。 只能为给定类定义一个**operator delete**函数;如果已定义，它将隐藏全局**operator delete**函数。 始终为任何类型的数组调用全局**operator delete**函数。

全局**运算符 delete**函数。 全局**运算符 delete**和类成员**运算符 delete**函数有两种形式：

```cpp
void operator delete( void * );
void operator delete( void *, size_t );
```

对于给定的类，只能存在上述两个窗体中的一个。 第一种形式采用 `void *`类型的单个自变量，该参数包含指向要释放的对象的指针。 第二个窗体（大小释放）采用两个参数，第一个是指向要释放的内存块的指针，第二个是要释放的字节数。 这两个窗体的返回类型为**void** （**operator delete**无法返回值）。

第二种形式的目的是加快搜索要删除的对象的正确大小类别，这通常不会存储在分配本身附近并且可能未缓存。 当使用基类中的**operator delete**函数删除派生类的对象时，第二种形式很有用。

**Operator delete**函数是静态的;因此，它不能是虚拟的。 **运算符 delete**函数服从访问控制，如[成员访问控制](member-access-control-cpp.md)中所述。

下面的示例演示用户定义的**operator new**和**operator delete**函数，旨在记录内存的分配和释放：

```cpp
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

前面的代码可用于检测“内存溢出”，即在自由储存中分配但从未释放过的内存。 若要执行此检测，将重新定义全局**new**和**delete**运算符来计数分配和内存释放。

编译器在类声明中支持成员数组**new**和**delete**运算符。 例如：

```cpp
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
