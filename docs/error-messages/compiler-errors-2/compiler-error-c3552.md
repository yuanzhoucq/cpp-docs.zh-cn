---
title: "编译器错误 C3552 | Microsoft Docs"
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
  - "C3552"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3552"
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3552
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“typename”: 后指定返回类型不能包含“auto”  
  
 如果你使用 `auto` 关键字作为函数返回类型的占位符，必须提供后指定返回类型。 但是，不能使用其他 `auto` 关键字来指定后指定返回类型。 例如，下述代码片段产生错误 C3552。  
  
 `auto myFunction->auto; // C3552`