---
title: "编译器错误 C3384 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3384"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3384"
ms.assetid: c9f92c6a-62a9-4333-b2b1-bc55c7f288b6
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# 编译器错误 C3384
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type\_parameter”: 值约束与 ref 约束互相排斥  
  
 无法将泛型类型约束为 `value class` 和 `ref class`。  
  
 有关更多信息，请参见[约束](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)。  
  
## 示例  
 下面的示例生成 C3384。  
  
```  
// C3384.cpp // compile with: /c /clr generic <typename T> where T : ref class where T : value class   // C3384 ref class List {};  
```