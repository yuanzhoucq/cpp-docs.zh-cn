---
title: "编译器错误 C3050 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3050"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3050"
ms.assetid: ee090a0b-29cc-4215-a2f9-d82af79b8e82
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C3050
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type1”：ref 类不能从“type1”继承  
  
 `System::ValueType` 不能作为引用类型的基类。  
  
 以下示例生成 C3050：  
  
```  
// C3050.cpp // compile with: /clr /LD ref struct X : System::ValueType {};   // C3050 ref struct Y {};   // OK  
```