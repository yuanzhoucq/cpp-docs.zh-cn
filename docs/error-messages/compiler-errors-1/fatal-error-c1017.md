---
title: "错误 C1017 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1017"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1017"
ms.assetid: 5542e604-599d-4e36-8f83-1d454c5753c9
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1017
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无效的整数常数表达式  
  
 `#if` 指令中的表达式不存在或者计算结果不为常数。  
  
 用 `#define` 定义的常数在 `#if`、`#elif` 或 `#else` 指令中使用时必须具有计算结果为整数常数的值。  
  
 下面的示例生成 C1017：  
  
```  
// C1017.cpp  
#define CONSTANT_NAME "YES"  
#if CONSTANT_NAME   // C1017  
#endif  
```  
  
 可能的解决方案：  
  
```  
// C1017b.cpp  
// compile with: /c  
#define CONSTANT_NAME 1  
#if CONSTANT_NAME  
#endif  
```  
  
 因为 `CONSTANT_NAME` 计算结果为字符串而不是整数，所以 `#if` 指令生成错误 C1017。  
  
 在其他情况中，预处理器将未定义的常数作为零进行计算。  这可能导致意外的结果，如下例中所示。  因为未定义 `YES`，所以它的计算结果为零。  表达式 `#if` `CONSTANT_NAME` 计算结果为 false，而要对 `YES` 使用的代码由预处理器移除。  由于 `NO` 也未定义（零），因此 `#elif` `CONSTANT_NAME==NO` 计算结果为 true \(`0 == 0`\)，导致预处理器将代码保留在语句的 `#elif` 部分（与预期的行为完全相反）。  
  
```  
// C1017c.cpp  
// compile with: /c  
#define CONSTANT_NAME YES  
#if CONSTANT_NAME  
   // Code to use on YES...  
#elif CONSTANT_NAME==NO  
   // Code to use on NO...  
#endif  
```  
  
 若要确切了解编译器如何处理预处理器指令，请使用 [\/P](../../build/reference/p-preprocess-to-a-file.md)、[\/E](../../build/reference/e-preprocess-to-stdout.md) 或 [\/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)。