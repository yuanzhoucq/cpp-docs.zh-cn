---
title: "宏和 C++ | Microsoft Docs"
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
  - "宏"
  - "宏, C++"
ms.assetid: 83a344c1-73c9-4ace-8b93-cccfb62c6133
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 宏和 C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 提供新功能，其中一些取代了 ANSI C 预处理器提供的功能。  这些新功能可增强语言的类型安全性和可预见性：  
  
-   在 C\+\+ 中，声明为 **const** 的对象可用于常量表达式。  这使程序可以声明具有类型和值信息的常量，以及可以用调试器以符号方式查看的枚举。  使用预处理器 `#define` 指令定义常量不是那么精确。  除非在程序中找到采用 **const** 对象的地址的表达式，否则不会为该对象分配存储区。  
  
-   C\+\+ 内联函数功能取代了函数类型宏。  使用内联函数取代宏的好处如下：  
  
    -   类型安全。  内联函数需要接受与常规函数相同的类型检查。  宏不是类型安全。  
  
    -   纠正具有副作用的参数的处理。  内联函数将计算在输入函数体前作为参数提供的表达式。  因此，具有副作用的表达式不可能不安全。  
  
 有关内联函数的详细信息，请参阅 [inline、\_\_inline 和 \_\_forceinline](../misc/inline-inline-forceinline.md)。  
  
 出于向后兼容性的原因，将为 Microsoft C\+\+ 保留存在于 ANSI C 以及更早的 C\+\+ 规范中的所有预处理器工具。  
  
## 请参阅  
 [预定义的宏](../preprocessor/predefined-macros.md)   
 [宏](../preprocessor/macros-c-cpp.md)