---
title: "编译器错误 C3484 | Microsoft Docs"
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
  - "C3484"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3484"
ms.assetid: 2fe847fa-f6ee-4978-bc1d-b6dc6ae906ac
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3484
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

返回类型前应为“\-\>”  
  
 你必须在 lambda 表达式的返回类型前提供 `->`。  
  
### 更正此错误  
  
-   在返回类型前提供 `->`。  
  
## 示例  
 下面的示例生成 C3484：  
  
```  
// C3484a.cpp int main() { return []() . int { return 42; }(); // C3484 }  
```  
  
## 示例  
 下面的示例通过在 lambda 表达式的返回类型之前提供 `->` 来解决 C3484：  
  
```  
// C3484b.cpp int main() { return []() -> int { return 42; }(); }  
```  
  
## 请参阅  
 [lambda 表达式](../../cpp/lambda-expressions-in-cpp.md)