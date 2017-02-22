---
title: "编译器错误 C3492 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3492"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3492"
ms.assetid: b1dc6342-9133-4b1f-a9c3-e8c65d20d121
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C3492
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“var”: 不能捕获匿名联合的成员  
  
 不能捕获未命名联合的成员。  
  
### 更正此错误  
  
-   为联合提供一个名称，并将整个此联合结构传递到 lambda 表达式的捕获列表。  
  
## 示例  
 以下示例将生成 C3492，因为它捕获匿名联合的成员：  
  
```  
// C3492a.cpp int main() { union { char ch; int x; }; ch = 'y'; [&x](char ch) { x = ch; }(ch); // C3492 }  
```  
  
## 示例  
 通过给此联合提供名称以及将整个联合结构传递给 lambda 表达式的捕获列表，下面的示例解析了 C3492：  
  
```  
// C3492b.cpp int main() { union { char ch; int x; } u; u.ch = 'y'; [&u](char ch) { u.x = ch; }(u.ch); }  
```  
  
## 请参阅  
 [lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)