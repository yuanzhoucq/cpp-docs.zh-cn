---
title: "编译器错误 C3400 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3400"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3400"
ms.assetid: d44169a8-73b6-4766-b406-b3a6c93f2a4d
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# 编译器错误 C3400
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

涉及“constraint\_1”和“constraint\_2”的循环约束依赖项  
  
 编译器检测到循环约束。  
  
 有关详细信息，请参阅[约束](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)。  
  
## 示例  
 以下示例生成 C3400。  
  
```  
// C3400.cpp // compile with: /clr /c generic<class T, class U> where T : U where U : T   // C3400 public ref struct R {};  
```