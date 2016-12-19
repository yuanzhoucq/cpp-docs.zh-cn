---
title: "编译器警告（等级 3）C4723 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4723"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4723"
ms.assetid: 07669d14-3fd8-4a43-94bc-b61c50e58460
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 3）C4723
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

潜在的被 0 除  
  
 除法操作中的第二个操作数在编译时计算为零，给出未定义的结果。  
  
 仅在使用 [\/Og](../../build/reference/og-global-optimizations.md) 或暗指 \/Og 的优化选项时才发出此警告。  
  
 编译器可能已生成零操作数。