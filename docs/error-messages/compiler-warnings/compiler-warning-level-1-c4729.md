---
title: "编译器警告（等级 1）C4729 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4729"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4729"
ms.assetid: 36a0151f-f258-48d9-9444-ae6d41ff70a4
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器警告（等级 1）C4729
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

根据警告，函数对于流图形太大  
  
 当函数太大，不能用可靠的方法（如检查是否有将生成警告的情况）进行编译时生成此警告。 仅在使用 [\/Od](../../build/reference/od-disable-debug.md) 编译器选项时生成此警告。  
  
 若要解决此警告，请将函数拆成较小的函数。