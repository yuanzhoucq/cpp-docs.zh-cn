---
title: "编译器错误 C3491 | Microsoft Docs"
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
  - "C3491"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3491"
ms.assetid: 7f0e71b2-46a0-4d25-bd09-6158a280f509
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3491
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“var”：不能在非可变 lambda 中修改按值捕获  
  
 非可变 lambda 表达式不能修改通过值捕获的变量的值。  
  
### 更正此错误  
  
-   用 `mutable` 关键字声明 lambda 表达式，或者  
  
-   将该变量按引用传递到 lambda 表达式的捕获列表。  
  
## 示例  
 下面的示例生成 C3491，因为非可变 lambda 表达式的主体修改了捕获变量 `m`：  
  
```  
// C3491a.cpp int main() { int m = 55; [m](int n) { m = n; }(99); // C3491 }  
```  
  
## 示例  
 下面的示例通过使用 `mutable` 关键字声明 lambda 表达式来解决 C3491：  
  
```  
// C3491b.cpp int main() { int m = 55; [m](int n) mutable { m = n; }(99); }  
```  
  
## 请参阅  
 [lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)