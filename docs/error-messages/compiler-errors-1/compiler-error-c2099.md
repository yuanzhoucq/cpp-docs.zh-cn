---
title: "编译器错误 C2099 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2099"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2099"
ms.assetid: 30e151ee-d458-4901-b0c0-d45054a913f5
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 编译器错误 C2099
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

初始值设定项不是常量  
  
 此错误仅由 C 编译器发出，并仅发生在非自动变量上。  编译器在启动程序时初始化非自动变量，并且初始化的值必须是常数。  
  
## 示例  
 下面的示例生成 C2099。  
  
```  
// C2099.c int j; int *p; j = *p;   // C2099 *p is not a constant  
```  
  
## 示例  
 由于编译时与运行时的浮点精度环境设置（有关详细信息，请参阅 [\_controlfp\_s](../../c-runtime-library/reference/controlfp-s.md)）可能不同，因此，编译器无法在 **\/fp:strict** 下对表达式执行常数合并。在这种情况下，也可能发生 C2099。  
  
 当常数折叠失败时，编译器将调用动态初始化，而这在 C 中是不被允许的。  
  
 若要解决此错误，请将模块编译为 .cpp 文件或简化表达式。  
  
 有关更多信息，请参见[\/fp（指定浮点行为）](../../build/reference/fp-specify-floating-point-behavior.md)。  
  
 下面的示例生成 C2099。  
  
```  
// C2099_2.c // compile with: /fp:strict /c float X = 2.0 - 1.0;   // C2099 float X2 = 1.0;   // OK  
```