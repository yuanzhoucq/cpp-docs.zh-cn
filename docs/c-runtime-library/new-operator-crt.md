---
title: "operator new(CRT) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr110_clr0400.dll"
  - "msvcr100.dll"
  - "msvcr120.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
f1_keywords: 
  - "new[]"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "operator new[]"
  - "vector new"
ms.assetid: 79682f85-6889-40f6-b8f7-9eed5176ea35
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# operator new(CRT)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从堆中分配内存块。  
  
## 语法  
  
```  
  
      void *__cdecl operator new[](size_t count);  
void *__cdecl operator new[] (  
   size_t count,   
   void * object  
) throw();  
void *__cdecl operator new[] (  
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
 与标量新的窗体 \([new 运算符](../c-runtime-library/operator-new-crt.md)\) 对比之下，`operator new` 的窗体称为矢量新。  
  
 此运算符的第一形式被称为 nonplacement 形式。  此运算符的第二个窗体称为放置窗体，并且此运算符第三个窗体是未抛出的放置窗体。  
  
 运算符的第一个形式由编译器定义的，并且不需要在程序中包含 new.h。  
  
 [operator delete&#91;&#93;](../Topic/operator%20delete\(%3Cnew%3E\).md) 使用新的运算符释放已分配的内存。  
  
 可以配置 `operator new[]` 是否返回空或在失败时抛出异常。  请参见 [有关更多new和delete运算符信息](../cpp/new-and-delete-operators.md) 。  
  
 在抛出异常或未抛出操作下，CRT`operator new` 行为类似于在标准 C\+\+ 库中的 [operator new&#91;&#93;](../Topic/operator%20new\(%3Cnew%3E\).md) 。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`new[]`|\<new.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
 下面演示如何使用矢量，`operator new`的未放置窗体。  
  
```  
// crt_new4.cpp  
#include <stdio.h>  
int main() {  
   int * k = new int[10];  
   k[0] = 21;  
   printf("%d\n", k[0]);  
   delete [] k;  
}  
```  
  
 下面演示如何使用矢量，`operator new`的放置窗体。  
  
```  
// crt_new5.cpp  
#include <stdio.h>  
#include <new.h>  
int main() {  
   int * i = new int[10];  
   i[0] = 21;  
   printf("%d\n", i[0]);  
   // initialize existing memory (i) with, in this case, int[[10]  
   int * j = new(i) int[10];   // placement vector new  
   printf("%d\n", j[0]);  
   j[0] = 22;  
   printf("%d\n", i[0]);  
   delete [] i;   // or, could have deleted [] j   
}  
```  
  
 下面演示如何使用矢量，`operator new`的放置窗体，未抛出窗体。  
  
```  
// crt_new6.cpp  
#include <stdio.h>  
#include <new.h>  
int main() {  
   int * k = new(std::nothrow) int[10];  
   k[0] = 21;  
   printf("%d\n", k[0]);  
   delete [] k;  
}  
```  
  
## 请参阅  
 [内存分配](../c-runtime-library/memory-allocation.md)