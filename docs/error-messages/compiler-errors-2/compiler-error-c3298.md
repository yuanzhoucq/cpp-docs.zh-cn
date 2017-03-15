---
title: "编译器错误 C3298 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3298"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3298"
ms.assetid: 458c2680-95bb-4d5e-895f-ce4115844193
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# 编译器错误 C3298
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“constraint\_1”：不能使用“constraint\_2”作为约束，因为“constraint\_2”具有 ref 约束，而“constraint\_1”具有值约束  
  
 不能为约束指定相互排斥的特征。 例如，不能同时将泛型类型参数约束为值类型和引用类型。  
  
 有关详细信息，请参阅[约束](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)。  
  
## 示例  
 下面的示例生成 C3298。  
  
```  
// C3298.cpp // compile with: /clr /c generic<class T, class U> where T : ref class where U : T, value class   // C3298 public ref struct R {};  
```