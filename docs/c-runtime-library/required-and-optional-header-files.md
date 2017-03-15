---
title: "必需和可选的头文件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.headers"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "头文件, 运行时所需的"
  - "包含文件, 运行时所需的"
ms.assetid: f64d0bf5-e2c3-4b42-97d0-443b3d901d9f
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 必需和可选的头文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每个运行期程序的说明包括列表所需和选项包括，或标头\(H\)，该例程的文件。  必需的头文件包括需要获得其他例程或定义的例程的函数声明内部调用。  选项头文件通常使用预定义常数、类型定义内联或宏。  下表列出可选文件头内容的一些示例：  
  
|定义|示例|  
|--------|--------|  
|宏定义|如果库类型程序实现为宏，头文件可在头文件中定义宏，除原始的例程。  例如，`toupper`宏在头文件 CTYPE.H中定义，而函数`_toupper` 声明在 STDLIB.H头文件。|  
|Predefined 常数|许多库类型程序引用的常量在头文件中定义。  例如，在头文件 FCNTL.H. 定义的`_open` 通常使用常数，如 `_O_CREAT`。|  
|类型定义|某些库类型程序返回结构或将结构作为参数传递。  例如，流输入\/输出例程使用类型 `FILE`结构，该结构在 STDIO.H. 定义。|  
  
 运行库头文件中提供了建议 ANSI\/ISO C 标准样式的函数声明。  编译器对在其关联的函数声明后进行定期发生的所有引用的类型检查。  函数声明为 `int`以外，返回值是一些类型，默认的例程特别重要。  在其声明不指定其适当的返回值的例程将由编译器考虑，来返回 `int`，会产生意外的结果。  有关更多信息，请参见 [Type Checking](../c-runtime-library/type-checking-crt.md)。  
  
## 请参阅  
 [CRT 库功能](../c-runtime-library/crt-library-features.md)