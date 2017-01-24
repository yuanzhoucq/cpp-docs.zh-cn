---
title: "编译器错误 C3075 | Microsoft Docs"
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
  - "C3075"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3075"
ms.assetid: f431daa9-e0fa-48f0-a5c3-f99be96b55e3
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3075
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“instance”：无法将引用类型“type”的实例嵌入到值类型中  
  
 值类型不能包含引用类型的实例。  
  
 有关详细信息，请参阅[参考类型的 C\+\+ 堆栈语义](../../dotnet/cpp-stack-semantics-for-reference-types.md)。  
  
## 示例  
 以下示例生成 C3075。  
  
```  
// C3075.cpp // compile with: /clr /c ref struct U {}; value struct X { U y;   // C3075 }; ref struct Y { U y;   // OK };  
```