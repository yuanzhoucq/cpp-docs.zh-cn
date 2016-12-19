---
title: "编译器错误 C3485 | Microsoft Docs"
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
  - "C3485"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3485"
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3485
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

lambda 定义不能包含任何 cv 限定符  
  
 不能使用 `const` 或 `volatile` 限定符作为 lambda 表达式定义的一部分。  
  
### 更正此错误  
  
-   从 lambda 表达式定义中删除 `const` 或 `volatile` 限定符。  
  
## 示例  
 以下示例生成 C3485，因为它使用 `const` 限定符作为 lambda 表达式定义的一部分：  
  
```  
// C3485.cpp int main() { auto x = []() const mutable {}; // C3485 }  
```  
  
## 请参阅  
 [lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)