---
title: "编译器错误 C2337 | Microsoft Docs"
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
  - "C2337"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2337"
ms.assetid: eccc9178-a15e-42cd-bbd0-3cea7cf2d55b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2337
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“attribute name”：未找到特性  
  
 你使用了此版本的 Visual c\+\+ 不支持的特性。  
  
 以下示例生成 C2337：  
  
```  
// C2337.cpp // compile with: /c [emitidl]; [module(name="x")]; [grasshopper]   // C2337, not a supported attribute class a{};  
```