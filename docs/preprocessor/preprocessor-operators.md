---
title: "预处理器运算符 | Microsoft Docs"
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
  - "运算符 [C++], 预处理器"
  - "预处理器运算符"
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 预处理器运算符
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

四个预处理器特定运算符在 `#define` 指令的上下文中使用（参见下面的对每一个的摘要的列表\)。  字符串话、字符化和标记粘贴运算符在接下来的三个部分中讨论。  有关**已定义**运算符的信息，请参见 [\#if、 \#elif、 \#else 和 \#endif 指令](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)。  
  
|运算符|操作|  
|---------|--------|  
|[字符串化运算符 （\#）](../preprocessor/stringizing-operator-hash.md)|导致对应的实参括在双引号内|  
|[Charizing 运算符 \(\#@\)](../preprocessor/charizing-operator-hash-at.md)|导致对应的参数括在单引号内且其被认为是字符 （Microsoft 特定）|  
|[标记粘贴运算符 \(\#\#\)](../preprocessor/token-pasting-operator-hash-hash.md)|允许用作实参的标记串联以形成其他标记|  
|[定义的运算符](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|简化在特定宏指令的复合表达式的书写。|  
  
## 请参阅  
 [预处理器指令](../preprocessor/preprocessor-directives.md)   
 [预定义的宏](../preprocessor/predefined-macros.md)   
 [C\/C\+\+ 预处理器参考](../preprocessor/c-cpp-preprocessor-reference.md)