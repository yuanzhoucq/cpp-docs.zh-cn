---
title: "alloc_text | Microsoft Docs"
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
  - "vc-pragma.alloc_text"
  - "alloc_text_CPP"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "alloc_text 杂注"
  - "杂注, alloc_text"
ms.assetid: 1fd7be18-e4f7-4f70-b079-6326f72b871a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# alloc_text
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

命名指定的函数定义驻留的代码部分。  杂注必须出现在函数声明符和命名函数的函数定义之间。  
  
## 语法  
  
```  
  
#pragma alloc_text( "  
textsection  
", function1, ... )  
```  
  
## 备注  
 **alloc\_text** 杂注不处理 C\+\+ 成员函数或重载函数。  它只适用于通过 C 链接声明的函数：即，使用 **extern "C"** 连接说明声明的函数。  如果尝试对带 C\+\+ 链接的函数使用此杂注，则会生成编译器错误。  
  
 由于不支持使用 `__based` 进行函数寻址，因此指定节位置需要使用 **alloc\_text** 杂注。  由 *textsection* 指定的名称应包含在双引号内。  
  
 **alloc\_text** 杂注必须出现在任何指定的函数声明之后和这些函数的定义之前。  
  
 **alloc\_text** 杂注中引用的函数应在杂注所在的同一模块中进行定义。  如果未这样做，并且未定义的函数稍后会被编译为其他文本部分，该错误可能会被捕获，也可能不会。  尽管此程序通常都会正常运行，但该函数不会在预期部分中分配。  
  
 有关 **alloc\_text** 的其他限制如下所示：  
  
-   它不能在函数内使用。  
  
-   必须在声明函数后且在定义函数前使用它。  
  
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)