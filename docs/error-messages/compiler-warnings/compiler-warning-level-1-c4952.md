---
title: "编译器警告（等级 1）C4952 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4952"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4952"
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器警告（等级 1）C4952
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”：在程序数据库“pgd\_file”中未找到配置文件数据  
  
 当使用 [\/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md) 时，编译器检测到一个在 `/LTCG:PGINSTRUMENT` 后被重新编译且具有一个新的函数 \(***function***\) 存在的输入模块。  
  
 此警告为信息性。 若要解决此警告，请运行 `/LTCG:PGINSTRUMENT`，重做所有测试，并运行 `/LTCG:PGOPTIMIZE`。  
  
 如果已使用 `/LTCG:PGOPTIMIZE`，此警告将替换为一个错误。