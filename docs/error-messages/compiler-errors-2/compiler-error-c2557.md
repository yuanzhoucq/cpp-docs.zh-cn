---
title: "编译器错误 C2557 | Microsoft Docs"
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
  - "C2557"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2557"
ms.assetid: 48a33d82-aa16-4658-b346-2311fcb39864
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2557
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”：没有构造函数则不能初始化私有成员和受保护成员  
  
 只有成员和朋友可以给私有或受保护成员赋值。 非公共成员应在类构造函数中初始化。