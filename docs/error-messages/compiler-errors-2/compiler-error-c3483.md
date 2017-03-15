---
title: "编译器错误 C3483 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3483"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3483"
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C3483
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“var”已经是 lambda 捕获列表的一部分  
  
 你不止一次向 lambda 表达式的捕获列表传递了相同的变量。  
  
### 更正此错误  
  
-   从捕获列表中删除变量的所有其他实例。  
  
## 示例  
 下面的示例将生成 C3483，因为变量 `n` 在 lambda 表达式的捕获列表中出现了多次。  
  
```  
// C3483.cpp int main() { int m = 6, n = 5; [m,n,n] { return n + m; }(); // C3483 }  
```  
  
## 请参阅  
 [lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)