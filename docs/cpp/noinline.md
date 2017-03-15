---
title: "noinline | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "noinline"
  - "noinline_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 关键字 [C++], noinline"
  - "noinline __declspec 关键字"
ms.assetid: f259d55b-dec7-4bde-8cf9-14521e4fdc42
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# noinline
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 **\_\_declspec\(noinline\)** 通知编译器永远不内联某个特定成员函数（类中的函数）。  
  
 如果某个函数很小，并且对代码性能的影响不大，则不值得内联它。  即，如果函数很小并且不太可能经常调用（如处理错误条件的函数）。  
  
 请记住，如果某个函数标记为 `noinline`，则调用函数更小并且它本身因而是编译器内联的候选项。  
  
```  
class X {  
   __declspec(noinline) int mbrfunc() {  
      return 0;   
   }   // will not inline  
};  
```  
  
## 结束 Microsoft 专用  
  
## 请参阅  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [inline、\_\_inline、\_\_forceinline](../misc/inline-inline-forceinline.md)