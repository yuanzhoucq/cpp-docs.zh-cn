---
title: "编译器错误 C3297 | Microsoft Docs"
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
  - "C3297"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3297"
ms.assetid: 2a718b4c-6cdb-4418-92c0-fc3a259431c4
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3297
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“constraint\_2”：不能使用“constraint\_1”作为约束，因为“constraint\_1”具有值约束  
  
 值类已密封。 如果约束是值类，则永远无法从它派生其他约束。  
  
 有关详细信息，请参阅[约束](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)。  
  
## 示例  
 下面的示例生成 C3297。  
  
```  
// C3297.cpp // compile with: /clr /c generic<class T, class U> where T : value class where U : T   // C3297 public ref struct R {};  
```