---
title: "编译器错误 C2159 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2159"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2159"
ms.assetid: 925a2cbd-43c9-45ee-a373-84004350b380
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2159
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定了一个以上的存储类  
  
 声明包含多个存储类。  
  
 下面的示例生成 C2159：  
  
```  
// C2159.cpp // compile with: /c static int i;   // OK extern static int i;   // C2159  
```