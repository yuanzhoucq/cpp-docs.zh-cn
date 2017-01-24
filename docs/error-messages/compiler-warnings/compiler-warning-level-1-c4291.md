---
title: "编译器警告（等级 1）C4291 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4291"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4291"
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4291
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“declaration”: 未找到匹配的 delete 运算符；如果初始化引发异常，则不会释放内存  
  
 在没有放置 [delete](../../cpp/delete-operator-cpp.md) 的情况下放置 [new](../../cpp/new-operator-cpp.md)。  
  
 在用 **new** 运算符为对象分配内存时，会调用此对象的构造函数。  如果构造函数引发异常，则应释放为对象分配的任何内存。  除非存在与 **new** 运算符匹配的 **delete** 运算符函数，否则不会发生这种情况。  
  
 如果使用不带任何额外参数的 **new** 运算符，并用 [\/GX](../../build/reference/gx-enable-exception-handling.md)、[\/EHs](../../build/reference/eh-exception-handling-model.md) 或 \/EHa 选项进行编译以启用异常处理，则当构造函数引发异常时，编译器将生成调用 **delete** 运算符的代码。  
  
 如果使用 **new** 运算符的放置形式（除了带分配大小还带参数的形式），并且对象的构造函数引发异常，编译器仍将生成调用 **delete** 运算符的代码；但只有当存在与分配内存的 **new** 运算符的放置形式匹配的 **delete** 运算符的放置形式时，编译器才会这样做。  例如：  
  
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
  
 上面的示例生成警告 C4291，因为未定义与 **new** 运算符的放置形式匹配的 **delete** 运算符的放置形式。  若要解决此问题，请在 **main** 上面插入以下代码。  注意，除第一个参数外，所有重载 **delete** 运算符函数参数均与重载 **new** 运算符函数参数匹配。  
  
```  
void operator delete(void* pMem, char* pszFilename, int nLine)  
{  
   free(pMem);  
}  
```