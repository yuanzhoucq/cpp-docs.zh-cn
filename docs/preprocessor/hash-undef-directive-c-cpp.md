---
title: "#undef 指令 (C/C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "#undef"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#undef 指令"
  - "预处理器, 指令"
  - "undef 指令 (#undef)"
ms.assetid: 88900e0e-2c19-4a63-b681-f3d3133c24ca
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #undef 指令 (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

移除（取消定义）之前使用 `#define` 创建的名称。  
  
## 语法  
  
```  
  
#undef   
identifier  
  
```  
  
## 备注  
 `#undef` 指令可移除 *identifier* 的当前定义。  因此，*identifier* 的后续匹配项被预处理器忽略。  若要使用 `#undef` 移除宏定义，请仅给定宏 *identifier*；不要给定参数列表。  
  
 您还可以将 `#undef` 指令应用于之前没有定义的标识符。  这将确保该标识符是不确定的。  宏替换不在 `#undef` 语句中执行。  
  
 `#undef` 指令通常与 `#define` 指令成对，用来在源程序中创建一个区域，使其中的标识符具有特殊含义。  例如，源程序的特定函数可使用清单常量定义不会影响程序的其余部分的环境特定值。  `#undef` 指令还可与 `#if` 指令一起使用来控制源程序的条件编译。  有关详细信息，请参阅 [\#if、\#elif、\#else 和 \#endif 指令](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)。  
  
 在以下示例中，`#undef` 指令将移除符号常量和宏的定义。  请注意，只给定宏的标识符。  
  
```  
#define WIDTH 80  
#define ADD( X, Y ) ((X) + (Y))  
.  
.  
.  
#undef WIDTH  
#undef ADD  
```  
  
 **Microsoft 专用**  
  
 可以使用 \/U 选项后跟要取消定义的宏名称从命令行取消定义宏。  发出此命令的效果等效于文件开头的一系列 `#undef` *macro\-name* 语句。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [预处理器指令](../preprocessor/preprocessor-directives.md)