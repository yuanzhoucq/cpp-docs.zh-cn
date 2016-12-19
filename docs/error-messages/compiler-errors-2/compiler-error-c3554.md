---
title: "编译器错误 C3554 | Microsoft Docs"
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
  - "C3554"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3554"
ms.assetid: aede18d5-fefc-4da9-9b69-adfe90bfa742
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3554
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“decltype”不能与任何其他类型说明符组合  
  
 不可用任何类型说明符来限定 `decltype()` 关键字。 例如，下述代码片段产生错误 C3554。  
  
```  
int x; unsigned decltype(x); // C3554  
```