---
title: "编译器错误 C3499 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3499"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3499"
ms.assetid: 6717de5c-ae0f-4024-bdf2-b5598009e7b6
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C3499
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

已指定返回类型为 void 的 lambda 无法返回值  
  
 当将 `void` 指定为返回类型的 lambda 表达式返回值时，编译器产生此错误；或者当 lambda 表达式包含多条语句并返回一个值，但是未指定其返回类型时也会产生此错误。  
  
### 更正此错误  
  
-   请勿从 lambda 表达式返回值，或  
  
-   提供 lambda 表达式的返回类型，或  
  
-   将构成 lambda 表达式主体的语句合并成一条语句。  
  
## 示例  
 以下示例将生成 C3499，因为 lambda 表达式的主体包含多条语句并返回一个值，但 lambda 表达式未指定返回类型：  
  
```  
// C3499a.cpp int main() { [](int x) { int n = x * 2; return n; } (5); // C3499 }  
```  
  
## 示例  
 以下示例演示 C3499 的两个可能的解决方法。 第一个解决方法是提供 lambda 表达式的返回类型。 第二个解决方法是将构成 lambda 表达式主体的语句合并成一条语句。  
  
```  
// C3499b.cpp int main() { // Possible resolution 1: // Provide the return type of the lambda expression. [](int x) -> int { int n = x * 2; return n; } (5); // Possible resolution 2: // Combine the statements that make up the body of // the lambda expression into a single statement. [](int x) { return x * 2; } (5); }  
```  
  
## 请参阅  
 [lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)