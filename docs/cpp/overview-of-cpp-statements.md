---
title: "C++ 语句概述 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "语句, C++"
ms.assetid: e56996b2-b846-4b99-ac94-ac72fffc5ec7
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ 语句概述
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ 语句将按顺序执行，除非表达式语句、选择语句、迭代语句或跳转语句特意修改了顺序。  
  
 语句可以是以下类型之一：  
  
```  
  
        labeled-statement  
expression-statement  
compound-statement  
selection-statement  
iteration-statement  
jump-statement  
declaration-statement  
try-throw-catch  
```  
  
 在大多数情况下，C\+\+ 语句的语法与 ANSI C 语句的语法相同。  两者之间的主要区别在于：在 C 中只允许在块的开头进行声明；而 C\+\+ 通过添加 *declaration\-statement* 有效地消除了此限制。  这样，您就能够在程序中可以计算预计算初始化值的某个时点引入变量。  
  
 通过在块中的声明变量，您还可以对这些变量的范围和生存期进行精确的控制。  
  
 有关语句的主题描述了以下 C\+\+ 关键字：  
  
|||||  
|-|-|-|-|  
|[break](../cpp/break-statement-cpp.md)|[else](../cpp/if-else-statement-cpp.md)|[\_\_if\_exists](../cpp/if-exists-statement.md)|[\_\_try](../cpp/structured-exception-handling-c-cpp.md)|  
|[case](../cpp/switch-statement-cpp.md)|[\_\_except](../cpp/structured-exception-handling-c-cpp.md)|[\_\_if\_not\_exists](../cpp/if-not-exists-statement.md)|[try](../cpp/try-throw-and-catch-statements-cpp.md)|  
|[catch](../cpp/try-throw-and-catch-statements-cpp.md)|[for](../cpp/for-statement-cpp.md)|[\_\_leave](../c-language/try-finally-statement-c.md)|[while](../cpp/while-statement-cpp.md)|  
|[continue](../cpp/continue-statement-cpp.md)|[goto](../cpp/goto-statement-cpp.md)|[return](../cpp/return-statement-cpp.md)||  
|[default](../cpp/switch-statement-cpp.md)|[\_\_finally](../cpp/structured-exception-handling-c-cpp.md)|[switch](../cpp/switch-statement-cpp.md)||  
|[do](../cpp/do-while-statement-cpp.md)|[if](../cpp/if-else-statement-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)||  
  
## 请参阅  
 [语句](../cpp/statements-cpp.md)