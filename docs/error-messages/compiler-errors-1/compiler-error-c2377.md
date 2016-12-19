---
title: "编译器错误 C2377 | Microsoft Docs"
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
  - "C2377"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2377"
ms.assetid: f7660965-bf4c-4cd9-8307-1bd7016678a1
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2377
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”：重定义；typedef 不能由任何其他符号重载  
  
 `typedef` 标识符被重新定义。  
  
 以下示例生成 C2377：  
  
```  
// C2377.cpp // compile with: /c typedef int i; int i;   // C2377 int j;   // OK  
```