---
title: 编译器警告（等级 1）C4291
ms.date: 11/04/2016
f1_keywords:
- C4291
helpviewer_keywords:
- C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
ms.openlocfilehash: c1972236e30be4e6ca738b606b00398f5c7860e0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754864"
---
# <a name="compiler-warning-level-1-c4291"></a>编译器警告（等级 1）C4291

"声明"：未找到匹配的运算符删除;如果初始化引发异常，则不会释放内存

使用没有放置[删除](../../cpp/delete-operator-cpp.md)的[放置新](../../cpp/new-operator-cpp.md)放置。

当为具有运算符**new**的对象分配内存时，将调用对象的构造函数。 如果构造函数引发异常，则为对象分配的任何内存都应处理。 除非存在与运算符**new**匹配的运算符**删除**函数，否则无法执行此操作。

如果使用运算符**new**而不提供任何额外的参数，并使用[/GX](../../build/reference/gx-enable-exception-handling.md) [、/EHs](../../build/reference/eh-exception-handling-model.md)或 /EHa 选项编译以启用异常处理，则编译器将生成代码，以便在构造函数引发异常时调用运算符**删除**。

如果使用**新**运算符的放置形式（除了分配大小之外带有参数的窗体），并且对象的构造函数引发异常，编译器仍将生成代码来调用运算符**删除**;但只有在运算符**删除**的放置窗体与分配内存的运算符**的新**放置形式匹配时，才会执行此操作。 例如：

```cpp
// C4291.cpp
// compile with: /EHsc /W1
#include <malloc.h>

class CList
{
public:
   CList(int)
   {
      throw "Fail!";
   }
};

void* operator new(size_t size, char* pszFilename, int nLine)
{
   return malloc(size);
}

int main(void)
{
   try
   {
      // This will call ::operator new(unsigned int) to allocate heap
      // memory. Heap memory pointed to by pList1 will automatically be
      // deallocated by a call to ::operator delete(void*) when
      // CList::CList(int) throws an exception.
      CList* pList1 = new CList(10);
   }
   catch (...)
   {
   }

   try
   {
      // This will call the overloaded ::operator new(size_t, char*, int)
      // to allocate heap memory. When CList::CList(int) throws an
      // exception, ::operator delete(void*, char*, int) should be called
      // to deallocate the memory pointed to by pList2. Since
      // ::operator delete(void*, char*, int) has not been implemented,
      // memory will be leaked when the deallocation cannot occur.
      CList* pList2 = new(__FILE__, __LINE__) CList(20);   // C4291
   }
   catch (...)
   {
   }
}
```

上述示例生成警告 C4291，因为未定义与运算符**new**的放置形式匹配的运算符**删除**放置形式。 要解决此问题，请在**主**上插入以下代码。 请注意，除第一个参数外，所有重载运算符**删除**函数参数都与重载运算符**new**的函数参数匹配。

```cpp
void operator delete(void* pMem, char* pszFilename, int nLine)
{
   free(pMem);
}
```
