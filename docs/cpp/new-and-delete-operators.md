---
title: new 和 delete 运算符
ms.date: 11/19/2019
helpviewer_keywords:
- new keyword [C++]
- delete keyword [C++]
ms.assetid: fa721b9e-0374-4f04-bb87-032ea775bcc8
ms.openlocfilehash: fd170c1500e2d80879fdd89f7d825930189ae942
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367890"
---
# <a name="new-and-delete-operators"></a>new 和 delete 运算符

C++支持使用[新的](new-operator-cpp.md)运算符和[删除](delete-operator-cpp.md)运算符动态分配和分配对象。 这些运算符为来自称为“自由存储”的池中的对象分配内存。 **新**运算符调用特殊函数运算符[new](new-operator-cpp.md)，**删除**运算符调用特殊函数[运算符删除](delete-operator-cpp.md)。

C++标准库中**的新功能**支持C++标准中指定的行为，即如果内存分配失败，则引发 std：：bad_alloc 异常。 如果您仍想要**新版本的**非引发版本，请将程序链接到 nothrownew.obj。但是，当您链接到 nothrownew.obj 时，C++标准库中**的默认运算符**不再正常工作。

有关构成 C 运行时库和C++标准库的库文件的列表，请参阅[CRT 库功能](../c-runtime-library/crt-library-features.md)。

## <a name="the-new-operator"></a><a id="new_operator"> </a>新运算符

当程序中遇到如下语句时，它将转换为对函数**运算符 new**的调用：

```cpp
char *pch = new char[BUFFER_SIZE];
```

如果请求为零字节的存储，**则运算符 new**返回指向不同对象的指针（即，对**运算符的新**重复调用返回不同的指针）。 如果分配请求内存不足，**则运算符 new**会引发异常`std::bad_alloc`，或者如果已链接在非引发**运算符新**支持中，则返回**nullptr。**

您可以编写一个例程，尝试释放内存并重试分配;有关详细信息[，请参阅_set_new_handler。](../c-runtime-library/reference/set-new-handler.md) 有关恢复方案的更多详细信息，请参阅本主题的"处理内存不足"部分。

**下表描述了运算符新功能**的两个作用域。

### <a name="scope-for-operator-new-functions"></a>操作员新功能的范围

|操作员|范围|
|--------------|-----------|
|**：： 运算符新**|Global|
|*类名称* **：：运算符新**|类|

**运算符 new**的第一个参数必须为`size_t`类型（在 stddef.h>中\<定义的类型），并且返回类型始终**为空**<strong>\*</strong>。

当**使用新**运算符分配内置类型的对象、不包含用户定义的**运算符新**函数的类类型对象以及任何类型的数组时，将调用全局**运算符新功能**。 当**新**运算符用于分配定义**运算符 new**的类类型的对象时，将调用该类的**运算符 new。**

为类定义的**运算符新**函数是一个静态成员函数（因此，它不能是虚拟的），它隐藏该类类型对象的全局**运算符新**函数。 考虑使用**new**将内存分配和设置为给定值的情况：

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

以括号提供给**new**的参数作为`Blanks::operator new``chInit`参数传递给。 但是，全局**运算符新**函数被隐藏，导致以下代码生成错误：

```cpp
Blanks *SomeBlanks = new Blanks;
```

编译器支持类声明中**的新**成员数组**和删除**运算符。 例如：

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

可以测试失败的内存分配，如下所示：

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

还有另一种方法来处理失败的内存分配请求。 编写自定义恢复例程来处理此类故障，然后通过调用[_set_new_handler](../c-runtime-library/reference/set-new-handler.md)运行时函数来注册函数。

## <a name="the-delete-operator"></a><a id="delete_operator"> </a>删除运算符

可以使用**delete**运算符释放使用**新**运算符动态分配的内存。 删除运算符调用**运算符删除**函数，该函数将内存释放回可用池。 使用**delete**运算符还会导致调用类析构函数（如果有）。

有全局和类作用域**运算符删除**函数。 只能为给定类定义一个**运算符删除**函数;如果已定义，它将隐藏全局**运算符删除**函数。 对于任何类型的数组，始终调用全局**运算符删除**函数。

全局**运算符删除**函数。 全局**运算符删除**和类成员**运算符删除**函数存在两种形式：

```cpp
void operator delete( void * );
void operator delete( void *, size_t );
```

给定类只能存在前两个窗体中的一个。 第一个窗体采用类型的`void *`单个参数 ，其中包含指向要解调的对象的指针。 第二种形式（大小处理）采用两个参数，第一个参数是指向要解分配的内存块的指针，第二个参数是要解调的字节数。 两种形式的返回**类型无效（****运算符删除**不能返回值）。

第二个窗体的目的是加快搜索要删除的对象的正确大小类别，该类别通常不存储在分配本身附近，并且可能未缓存。 当运算符从基类**中删除**函数用于删除派生类的对象时，第二个窗体很有用。

**运算符删除**函数是静态的;因此，它不能是虚拟的。 **运算符删除**函数遵循访问控制，如[成员访问控制](member-access-control-cpp.md)中所述。

下面的示例显示用户定义的**运算符新的**和**运算符删除**旨在记录内存分配和分配位置的功能：

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

前面的代码可用于检测“内存溢出”，即在自由储存中分配但从未释放过的内存。 要执行此检测，将重新定义**new**全局新**运算符和删除**运算符，以计数内存的分配和分配。

编译器支持类声明中**的新**成员数组**和删除**运算符。 例如：

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
