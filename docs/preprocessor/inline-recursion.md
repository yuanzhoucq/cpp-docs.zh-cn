---
title: "inline_recursion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "inline_recursion_CPP"
  - "vc-pragma.inline_recursion"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "inline_recursion 杂注"
  - "杂注, inline_recursion"
ms.assetid: cfef5791-63b7-45ac-9574-623747b9b9c9
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# inline_recursion
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

控制直接或相互递归函数调用的内联扩展。  
  
## 语法  
  
```  
  
#pragma inline_recursion( [{on | off}] )  
```  
  
## 备注  
 请使用此杂注控制标记为 [inline](../misc/inline-inline-forceinline.md) 和 [\_\_inline](../misc/inline-inline-forceinline.md) 的函数或编译器在 \/Ob2 选项下自动扩展的函数。  使用此杂注要求 [\/Ob](../build/reference/ob-inline-function-expansion.md) 编译器选项设置为 1 或者 2。  `inline_recursion` 的默认状态为关闭。  此杂注在出现后在第一个函数调用处生效，并且不会影响函数的定义。  
  
 `inline_recursion` 杂注控制如何扩展递归函数。  如果 `inline_recursion` 处于关闭状态，并且内联函数调用自身（直接或间接），则该函数仅扩展一次。  如果 `inline_recursion` 处于打开状态，则该函数将扩展多次，直至其达到使用 [inline\_depth](../preprocessor/inline-depth.md) 杂注设置的值（`inline_depth` 杂注定义的递归函数的默认值，或容量限制）。  
  
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [inline\_depth](../preprocessor/inline-depth.md)   
 [\/Ob（内联函数展开）](../build/reference/ob-inline-function-expansion.md)