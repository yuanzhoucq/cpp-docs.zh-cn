---
title: new 和 delete 运算符
description: C + + 语言 new 和 delete 运算符允许对分配进行控制。
ms.date: 07/07/2020
helpviewer_keywords:
- new keyword [C++]
- delete keyword [C++]
ms.openlocfilehash: e609d1fdbd4f945ab8709c554d1396100027c4c1
ms.sourcegitcommit: e17cc8a478b51739d67304d7d82422967b35f716
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/08/2020
ms.locfileid: "86127840"
---
# <a name="new-and-delete-operators"></a>`new` 和 `delete` 运算符

C + + 支持使用和运算符动态分配和释放对象 [`new`](new-operator-cpp.md) [`delete`](delete-operator-cpp.md) 。 这些运算符为来自称为“自由存储”的池中的对象分配内存。 **`new`** 运算符调用特殊函数 [`operator new`](new-operator-cpp.md) ， **`delete`** 运算符调用特殊函数 [`operator delete`](delete-operator-cpp.md) 。

**`new`** C + + 标准库中的函数支持 c + + 标准中指定的行为， `std::bad_alloc` 如果内存分配失败，则会引发异常。 如果仍需要的非引发版本 **`new`** ，请将程序链接到 *`nothrownew.obj`* 。 但是，当你链接时 *`nothrownew.obj`* ， **`operator new`** c + + 标准库中的默认值将不再起作用。

有关 C 运行库和 c + + 标准库中库文件的列表，请参阅[CRT 库功能](../c-runtime-library/crt-library-features.md)。

## <a name="the-new-operator"></a><a id="new_operator"> </a> `new` 运算符

编译器将此类语句转换为对函数的调用 **`operator new`** ：

```cpp
char *pch = new char[BUFFER_SIZE];
```

如果请求的存储空间为零字节，则 **`operator new`** 返回指向不同对象的指针。 也就是说，重复调用将 **`operator new`** 返回不同的指针。 如果分配请求没有足够的内存，则会 **`operator new`** 引发 `std::bad_alloc` 异常。 或者， **`nullptr`** 如果已在非引发支持中链接，则返回 **`operator new`** 。

可以编写一个例程来尝试释放内存，然后重试分配。 有关详细信息，请参阅 [`_set_new_handler`](../c-runtime-library/reference/set-new-handler.md)。 有关恢复方案的详细信息，请参阅[处理内存不足](#handling-insufficient-memory)部分。

下表描述了函数的两个作用域 **`operator new`** 。

### <a name="scope-for-operator-new-functions"></a>函数的作用域 `operator new`

| 运算符 | 范围 |
|--|--|
| **`::operator new`** | 全球 |
| *类名***`::operator new`** | 类 |

的第一个参数 **`operator new`** 必须为类型 `size_t` ，在中定义， \<stddef.h> 并且返回类型始终为 **`void*`** 。

**`operator new`** 当 **`new`** 运算符用于分配内置类型的对象、不包含用户定义函数的类类型的对象 **`operator new`** 和任何类型的数组时，将调用全局函数。 当 **`new`** 运算符用于分配已定义的类类型的对象时 **`operator new`** ， **`operator new`** 将调用该类的。

**`operator new`** 为类定义的函数是静态成员函数（不能是虚函数），该函数隐藏此 **`operator new`** 类类型的对象的全局函数。 请考虑 **`new`** 用于分配内存并将其设置为给定值的情况：

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

在括号中提供的参数将 **`new`** `Blanks::operator new` 作为参数传递给 `chInit` 。 然而，全局 **`operator new`** 函数是隐藏的，导致如下代码生成错误：

```cpp
Blanks *SomeBlanks = new Blanks;
```

编译器 **`new`** **`delete`** 在类声明中支持成员数组和运算符。 例如：

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

还可以通过另一种方法来处理失败的内存分配请求。 编写自定义恢复例程来处理此类故障，并通过调用 [`_set_new_handler`](../c-runtime-library/reference/set-new-handler.md) 运行时函数来注册函数。

## <a name="the-delete-operator"></a><a id="delete_operator"> </a> `delete` 运算符

使用运算符动态分配的内存 **`new`** 可以使用运算符来释放 **`delete`** 。 Delete 运算符调用 **`operator delete`** 函数，该函数将内存释放回可用池。 使用 **`delete`** 运算符还会导致调用类析构函数（如果存在）。

存在全局和类范围的 **`operator delete`** 函数。 只能 **`operator delete`** 为给定类定义一个函数; 如果定义了该函数，它会隐藏全局 **`operator delete`** 函数。 **`operator delete`** 始终为任何类型的数组调用全局函数。

全局 **`operator delete`** 函数。 全局 **`operator delete`** 函数和类成员函数有两种形式 **`operator delete`** ：

```cpp
void operator delete( void * );
void operator delete( void *, size_t );
```

对于给定的类，只能存在上述两个窗体中的一个。 第一种形式采用一个类型为的参数 **`void *`** ，该参数包含指向要释放的对象的指针。 第二种形式的大小释放是使用两个参数：第一个是指向要释放的内存块的指针，第二个是要释放的字节数。 这两个窗体的返回类型为 **`void`** （ **`operator delete`** 无法返回值）。

第二种形式的目的是加快搜索要删除的对象的正确大小类别。 此信息通常不会存储在分配本身附近，这可能不会缓存。 当 **`operator delete`** 使用基类中的函数删除派生类的对象时，第二种形式很有用。

**`operator delete`** 函数是静态的，因此它不能是虚拟的。 **`operator delete`** 函数服从访问控制，如[成员访问控制](member-access-control-cpp.md)中所述。

下面的示例演示了 **`operator new`** **`operator delete`** 用于记录内存分配和释放的用户定义的和函数：

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

前面的代码可用于检测 "内存泄漏"，即，在免费存储中分配但从未释放的内存。 为了检测泄漏，将重新 **`new`** 定义全局和 **`delete`** 运算符，以计数分配和内存释放。

编译器 **`new`** **`delete`** 在类声明中支持成员数组和运算符。 例如：

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
