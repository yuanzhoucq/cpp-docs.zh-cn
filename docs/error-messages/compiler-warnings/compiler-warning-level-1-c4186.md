---
title: "编译器警告（等级 1）C4186 | Microsoft Docs"
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
  - "C4186"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4186"
ms.assetid: caf3f7d8-f305-426b-8d4e-2b96f5c269ea
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4186
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#import 特性“attribute”需要计数参数；已忽略  
  
 `#import` 特性的参数数量不正确。  
  
## 示例  
  
```  
// C4186.cpp // compile with: /W1 /c #import "stdole2.tlb" no_namespace("abc") rename("a","b","c")  // C4186  
```  
  
 `no_namespace` 特性不采用任何参数。**rename** 特性仅采用两个参数。