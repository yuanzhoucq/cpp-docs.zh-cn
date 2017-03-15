---
title: "编译器错误 C3493 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3493"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3493"
ms.assetid: 734b4257-12a3-436f-8488-c8c55ec81634
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C3493
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法隐式捕获“var”，因为尚未指定默认捕获模式  
  
 空 lambda 表达式捕获 `[]` 指定 lambda 表达式不显式或隐式捕获任何变量。  
  
### 更正此错误  
  
-   提供默认捕获模式，或  
  
-   显式捕获一个或多个变量。  
  
## 示例  
 下面的示例生成 C3493，因为它将修改外部变量，但指定空的 capture 子句：  
  
```  
// C3493a.cpp int main() { int m = 55; [](int n) { m = n; }(99); // C3493 }  
```  
  
## 示例  
 下面的示例通过将“按引用”指定为默认捕获模式来解决 C3493。  
  
```  
// C3493b.cpp int main() { int m = 55; [&](int n) { m = n; }(99); }  
```  
  
## 请参阅  
 [lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)