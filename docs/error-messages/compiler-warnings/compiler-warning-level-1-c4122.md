---
title: "编译器警告（等级 1）C4122 | Microsoft Docs"
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
  - "C4122"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4122"
ms.assetid: 9a83eb0d-8708-42f7-988a-b0b6f2f646a0
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4122
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: alloc\_text 仅适用于带 C 链接的函数  
  
 **alloc\_text** 杂注仅适用于使用 **extern c** 声明的函数。 它不能与外部 C\+\+ 函数一起使用。  
  
 将忽略杂注。