---
title: "operator delete(CRT) | Microsoft Docs"
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
  - "msvcr90.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr120.dll"
  - "msvcr100.dll"
  - "msvcr80.dll"
apitype: "DLLExport"
f1_keywords: 
  - "delete[]"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "运算符 delete[]"
  - "向量删除"
ms.assetid: e91bd0df-3815-40ca-950a-67b470518aed
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# operator delete(CRT)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

释放分配块。  
  
## 语法  
  
```  
  
      void __cdecl operator delete[](void * object);  
void __cdecl operator delete[](void * object,   
   void * memory) throw();  
void __cdecl operator delete[](void * object,   
   const std::nothrow_t&) throw();  
```  
  
#### 参数  
 *内存*  
 被释放的内存位置。  
  
 *object*  
 指向被删除的对象的指针。  
  
## 备注  
 与标量删除形式 \([删除运算符](../c-runtime-library/operator-delete-crt.md)\) 不同，**运算符 删除** 的形式，被称为向量删除。  
  
 **运算符** `delete[]` 释放由[运算符 new&#91;&#93;](../c-runtime-library/new-operator-crt.md)分配的内存。  
  
 此运算符的第一形式被称为 nonplacement 形式。  此运算符的第二和第三形式通常不会从代码调用，但存在当调用新发生失败时，为编译器提供匹配删除，。  
  
 运算符的第一个形式由编译器定义的，并且不需要在程序中包含 new.h。  
  
 除引发的或非引发的行为之外，CRT **运算符** `delete[]` 行为类似于在标准 C\+\+ 库中的 [运算符 delete&#91;&#93;](../Topic/operator%20delete\(%3Cnew%3E\).md) 。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`delete[]`|\<new.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
 有关使用操作符 **delete**的示例，请参见 [operator new&#91;&#93;](../c-runtime-library/new-operator-crt.md)。  
  
## 请参阅  
 [内存分配](../c-runtime-library/memory-allocation.md)