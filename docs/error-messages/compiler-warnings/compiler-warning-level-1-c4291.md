---
title: 编译器警告 （等级 1） C4291 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4291
dev_langs:
- C++
helpviewer_keywords:
- C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8c5f2fe57d26de4b4b2f88a85f20b99344ac201
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038043"
---
# <a name="compiler-warning-level-1-c4291"></a>编译器警告（等级 1）C4291

declaration： 没有匹配的删除运算符; 如果找到如果初始化引发异常，不会释放内存

Placement[新](../../cpp/new-operator-cpp.md)使用它们没有任何放置[删除](../../cpp/delete-operator-cpp.md)。

当为具有运算符的对象分配内存**新**，调用对象的构造函数。 如果构造函数引发了异常，应释放已分配给对象的任何内存。 这不会发生，除非操作员**删除**函数存在匹配运算符**新**。

如果使用运算符**新**而无需任何额外的参数和使用编译[/GX](../../build/reference/gx-enable-exception-handling.md)， [/EHs](../../build/reference/eh-exception-handling-model.md)，或 /EHa 选项启用异常处理，编译器将生成到代码调用运算符**删除**在构造函数引发异常。

如果使用的放置形式**新**运算符 （带参数的形式除了大小分配的） 和对象的构造函数引发了异常，编译器仍将生成代码来调用运算符**删除**; 但它仅会进行截断如果运算符的放置形式**删除**存在匹配的运算符的放置形式**新**分配内存。 例如：

```
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

上面的示例生成警告 C4291 因为运算符没有放置窗体**删除**已定义匹配运算符的放置形式**新**。 若要解决此问题，插入以下代码上述**主要**。 请注意，所有重载运算符**删除**函数的参数匹配的重载的运算符**新**，除第一个参数。

```
void operator delete(void* pMem, char* pszFilename, int nLine)
{
   free(pMem);
}
```