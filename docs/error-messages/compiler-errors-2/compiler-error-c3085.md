---
title: "编译器错误 C3085 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3085"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3085"
ms.assetid: 1ac40bf2-f63e-439e-8921-47e6dadc8354
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C3085
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“constructor”：构造函数不能是“keyword”  
  
 未正确声明构造函数。 有关更多信息，请参见[重写说明符](../../windows/override-specifiers-cpp-component-extensions.md)。  
  
## 示例  
 以下示例生成 C3085。  
  
```  
// C3085.cpp // compile with: /c /clr ref struct S { S() abstract;   // C3085 S(S%) abstract;   // C3085 }; ref struct T { T() sealed {}   // C3085 T(T%) sealed {}   // C3085 };  
```