---
title: "编译器错误 C3232 | Microsoft Docs"
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
  - "C3232"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3232"
ms.assetid: 3119b3a9-0eff-4a3f-b805-e4d160af9e39
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3232
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“param”：泛型类型参数不能用于限定名中  
  
 未正确使用泛型类型参数。  
  
 以下示例生成 C3232：  
  
```  
// C3232.cpp // compile with: /clr generic <class T> ref class C { typename T::TYPE t;   // C3232 };  
```