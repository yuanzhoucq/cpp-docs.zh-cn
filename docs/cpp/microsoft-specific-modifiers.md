---
title: "Microsoft 专用的修饰符 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: 22c7178c-f854-47fa-9de6-07d23fda58e1
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Microsoft 专用的修饰符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本节从以下方面描述特定于 Microsoft 的 C\+\+ 扩展：  
  
-   [基寻址](../cpp/based-addressing.md)，将一个指针用作其他指针可进行偏移的基的做法  
  
-   [函数调用约定](../cpp/calling-conventions.md)  
  
-   使用 [\_\_declspec](../cpp/declspec.md) 关键字声明的扩展存储类特性  
  
-   [\_\_w64](../cpp/w64.md) 关键字  
  
 许多特定于 Microsoft 的关键字可用于修改声明符以构成派生类型。  有关声明符的详细信息，请参阅[声明符](http://msdn.microsoft.com/zh-cn/8a7b9b51-92bd-4ac0-b3fe-0c4abe771838)。  
  
### Microsoft 专用关键字  
  
|关键字|含义|是否已用于构成派生类型？|  
|---------|--------|------------------|  
|[\_\_based](../cpp/based-grammar.md)|后跟的名称将 32 位偏移量声明为包含在声明中的 32 位基。|是|  
|[\_\_cdecl](../cpp/cdecl.md)|后跟的名称使用 C 命名和调用约定。|是|  
|[\_\_declspec](../cpp/declspec.md)|后跟的名称指定 Microsoft 特定的存储类特性。|否|  
|[\_\_fastcall](../cpp/fastcall.md)|后跟的名称声明一个函数，该函数使用寄存器（如果可用）而不是用于参数传递的堆栈。|是|  
|[\_\_restrict](../cpp/extension-restrict.md)|与 \_\_declspec\([restrict](../cpp/restrict.md)\) 类似，只不过它用于变量。|否|  
|[\_\_stdcall](../cpp/stdcall.md)|后跟的名称指定遵循标准调用约定的函数。|是|  
|[\_\_w64](../cpp/w64.md)|将数据类型标记为 64 位编译器上较大数据类型。|否|  
|[\_\_unaligned](../cpp/unaligned.md)|指定指向类型或其他数据的指针未对齐。|否|  
|[\_\_vectorcall](../cpp/vectorcall.md)|后跟的名称声明一个函数，如果可能，该函数将使用寄存器（包括 SSE 寄存器）而不是用于参数传递的堆栈。|是|  
  
## 请参阅  
 [C\+\+ 语言参考](../cpp/cpp-language-reference.md)