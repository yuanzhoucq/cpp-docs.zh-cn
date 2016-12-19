---
title: "operator new (CRT) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr90.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
  - "msvcr110.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "operator new"
  - "scalar new"
ms.assetid: 4ae51618-a4e6-4172-b324-b99d86d1bdca
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# operator new (CRT)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从堆中分配内存块。  
  
## 语法  
  
```  
  
      void *__cdecl operator new(  
   size_t count  
);  
void *__cdecl operator new(  
   size_t count,   
   void * object  
) throw();  
void *__cdecl operator new(  
   size_t count,   
   const std::nothrow_t&  
) throw();  
```  
  
#### 参数  
 *count*  
 分配的大小。  
  
 *object*  
 指向创建对象的内存块的指针。  
  
## 返回值  
 指向新分配内存的最小字节地址的指针。  
  
## 备注  
 与新矢量窗体 \([的new&#91;&#93; 运算符](../c-runtime-library/new-operator-crt.md)\) 对比之下，`operator new` 的窗体称为新标量。  
  
 此运算符的第一形式被称为 nonplacement 形式。  此运算符的第二个窗体称为放置窗体，并且此运算符第三个窗体是未抛出的放置窗体。  
  
 运算符的第一个形式由编译器定义的，并且不需要在程序中包含 new.h。  
  
 [删除运算符](../c-runtime-library/operator-delete-crt.md) 释放使用 `operator new`分配的内存。  
  
 可以配置失败时返回new运算符或抛出异常。  请参见 [有关更多new和delete运算符信息](../cpp/new-and-delete-operators.md) 。  
  
 在抛出异常或未抛出操作下，CRT`operator new` 行为类似于在标准 C\+\+ 库中的 [operator new](../Topic/operator%20new%20\(%3Cnew%3E\).md) 。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|**new**|\<new.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
 下面演示如何使用标量，`operator new`的未放置窗体。  
  
```  
// crt_new1.cpp  
#include <stdio.h>  
int main() {  
   int * i = new int(6);  
   printf("%d\n", *i);  
   delete i;  
}  
```  
  
 下面演示如何使用标量，`operator new`的放置窗体。  
  
```  
// crt_new2.cpp  
#include <stdio.h>  
#include <new.h>  
int main() {  
   int * i = new int(12);  
   printf("*i = %d\n", *i);  
   // initialize existing memory (i) with, in this case, int(7)  
   int * j = new(i) int(7);   // placement new  
   printf("*j = %d\n", *j);  
   printf("*i = %d\n", *i);  
   delete i;   // or, could have deleted j  
}  
```  
  
 下面演示如何使用标量，`operator new`的放置窗体，未抛出窗体。  
  
```  
// crt_new3.cpp  
#include <stdio.h>  
#include <new.h>  
int main() {  
   // allocates memory, initialize (8) and if call fails, new returns null  
   int * k = new(std::nothrow) int(8);   // placement new  
   printf("%d\n", *k);  
   delete k;  
}  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [内存分配](../c-runtime-library/memory-allocation.md)