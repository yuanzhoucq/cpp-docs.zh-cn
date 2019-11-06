---
title: 编译器警告（等级1） C4291
ms.date: 11/04/2016
f1_keywords:
- C4291
helpviewer_keywords:
- C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
ms.openlocfilehash: c8dc35a58d40d2619f6e035e07b4ad0b3351c45d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626643"
---
# <a name="compiler-warning-level-1-c4291"></a>编译器警告（等级1） C4291

"声明"：未找到匹配的运算符删除;如果初始化引发异常，则不会释放内存

放置[新](../../cpp/new-operator-cpp.md)的用于没有位置[删除](../../cpp/delete-operator-cpp.md)。

使用 operator **new**为对象分配内存时，将调用该对象的构造函数。 如果构造函数引发异常，则应释放为该对象分配的任何内存。 除非存在与运算符**new**匹配的 operator **delete**函数，否则不能进行此操作。

如果使用不带任何额外参数的**new**运算符，并使用[/gx](../../build/reference/gx-enable-exception-handling.md)、 [/ehs](../../build/reference/eh-exception-handling-model.md)或/eha 选项进行编译以启用异常处理，则编译器将在构造函数引发异常时生成代码来调用运算符**delete** 。

如果使用**new**运算符的放置窗体（除了分配的大小外，具有参数的窗体），并且对象的构造函数引发异常，则编译器仍会生成代码来调用运算符**delete**;但如果运算符**删除**的放置形式与分配了内存的运算符**new**的放置形式匹配，则它将仅执行此操作。 例如:

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

上面的示例将生成警告 C4291，因为未定义与运算符**new**的放置形式匹配的运算符**删除**的放置形式。 若要解决此问题，请将以下代码插入到**main**之上。 请注意，除第一个参数外，所有重载的运算符**delete**函数参数都与重载运算符**new**的函数参数匹配。

```
void operator delete(void* pMem, char* pszFilename, int nLine)
{
   free(pMem);
}
```