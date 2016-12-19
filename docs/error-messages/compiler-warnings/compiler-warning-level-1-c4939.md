---
title: "编译器警告（等级 1）C4939 | Microsoft Docs"
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
  - "C4939"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4939"
ms.assetid: 07096008-ba47-436c-a84c-2b03ad90d0b3
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4939
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#pragma vtordisp 已被否决，并将在 Visual C\+\+ 将来的版本移除  
  
 将从 Visual C\+\+ 将来的版本中删除 [vtordisp](../../preprocessor/vtordisp.md) 杂注。  
  
## 示例  
 下面的示例生成 C4939。  
  
```  
// C4939.cpp // compile with: /c /W1 #pragma vtordisp(off)   // C4939  
```