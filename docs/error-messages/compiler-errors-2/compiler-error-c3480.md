---
title: "编译器错误 C3480 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3480"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3480"
ms.assetid: 7b2e055a-9604-4d13-861b-b38bda1a6940
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C3480
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“var”：lambda 捕获变量必须来自封闭函数范围  
  
 Lambda 捕获变量不是来自封闭函数范围。  
  
### 更正此错误  
  
-   从 lambda 表达式的捕获列表中删除该变量。  
  
## 示例  
 下面的示例将生成 C3480，因为变量 `global` 不是来自封闭函数范围：  
  
```  
// C3480a.cpp int global = 0; int main() { [&global] { global = 5; }(); // C3480 }  
```  
  
## 示例  
 下面的示例通过从 lambda 表达式的捕获列表中删除变量 `global` 来解决 C3480：  
  
```  
// C3480b.cpp int global = 0; int main() { [] { global = 5; }(); }  
```  
  
## 请参阅  
 [lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)