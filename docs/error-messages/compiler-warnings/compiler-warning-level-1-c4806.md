---
title: "编译器警告（等级 1） C4806 | Microsoft Docs"
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
  - "C4806"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4806"
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1） C4806
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operation”：不安全的操作：提升到类型 “type” 的类型 “type” 没有值与给定的常量相等  
  
 此消息警告针对代码如 `b == 3`，其中 `b` 具有类型 `bool`。 提升规则使 `bool` 被提升为 `int`。 这是合法的但绝不为 **真**。 以下示例生成 C4806：  
  
```  
// C4806.cpp // compile with: /W1 int main() { bool b = true; // try.. // int b = true; if (b == 3)   // C4806 { b = false; } }  
```