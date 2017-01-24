---
title: "编译器错误 C3488 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3488"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3488"
ms.assetid: 0a6fcd76-dd3b-48d7-abb3-22eccda96034
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3488
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当默认捕获模式为按引用捕获时，不允许使用“var”  
  
 当指定 lambda 表达式的默认捕获模式为按引用捕获时，无法按引用将变量传递给该表达式的捕获子句。  
  
### 更正此错误  
  
-   不要显式将变量传递给捕获子句，或者  
  
-   不要将按引用指定为默认捕获模式，或者  
  
-   将按值指定为默认捕获模式，或者  
  
-   按值将变量传递到捕获子句。 （这可能会更改 lambda 表达式的行为。）  
  
## 示例  
 下面的示例生成 C3488，因为对变量 `n` 的引用出现在默认模式为按引用的 lambda 表达式的捕获子句中：  
  
```  
// C3488a.cpp int main() { int n = 5; [&, &n]() { return n; } (); // C3488 }  
```  
  
## 示例  
 下面的示例演示 C3488 的四种可能的解决方法：  
  
```  
// C3488b.cpp int main() { int n = 5; // Possible resolution 1: // Do not explicitly pass &n to the capture clause. [&]() { return n; } (); // Possible resolution 2: // Do not specify by-reference as the default capture mode. [&n]() { return n; } (); // Possible resolution 3: // Specify by-value as the default capture mode. [=, &n]() { return n; } (); // Possible resolution 4: // Pass n by value to the capture clause. [n]() { return n; } (); }  
```  
  
## 请参阅  
 [lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)