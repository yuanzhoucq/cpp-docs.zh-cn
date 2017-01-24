---
title: "Naked 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "epilog 代码"
  - "函数 [C++], naked"
  - "naked 函数"
  - "prolog 代码"
ms.assetid: 2543c8af-00d4-4a2a-8a87-e746da1f9929
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Naked 函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 `naked` 存储类特性是特定于 Microsoft 的 C 语言扩展。  对于使用 `naked` 存储类特性声明的函数，编译器生成不带 prolog 和 epilog 代码的代码。  利用此功能，可以使用内联汇编程序代码编写您自己的 prolog\/epilog 代码序列。  裸函数对于编写虚拟设备驱动程序特别有用。  
  
 由于 `naked` 特性仅与函数定义相关且不是类型修饰符，因此裸函数使用扩展的特性语法，如[扩展的存储类特性](../c-language/c-extended-storage-class-attributes.md)中所述。  
  
 下面的示例利用 `naked` 特性定义了一个函数：  
  
```  
__declspec( naked ) int func( formal_parameters )  
{  
   /* Function body */  
}  
```  
  
 或者：  
  
```  
#define Naked   __declspec( naked )  
  
Naked int func( formal_parameters )  
{  
   /* Function body */  
}  
```  
  
 `naked` 特性仅影响函数的 prolog 和 epilog 序列的编译器代码生成的性质。  它不影响为调用这些函数而生成的代码。  因此，`naked` 特性不被视为函数的类型的一部分，并且函数指针不能具有 `naked` 特性。  此外，`naked` 特性不能应用于数据定义。  例如，下面的代码将生成错误：  
  
```  
__declspec( naked ) int i;  /* Error--naked attribute not */  
                            /* permitted on data declarations. */  
```  
  
 `naked` 特性仅与函数的定义相关，且无法在函数原型中指定。  下面的声明生成编译器错误：  
  
```  
__declspec( naked ) int func();   /* Error--naked attribute not */  
                     /* permitted on function declarations.    */   \  
```  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [C 函数定义](../c-language/c-function-definitions.md)