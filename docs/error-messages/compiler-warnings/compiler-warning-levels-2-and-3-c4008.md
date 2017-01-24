---
title: "编译器警告（等级 2 和等级 3）C4008 | Microsoft Docs"
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
  - "C4008"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4008"
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 2 和等级 3）C4008
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”：“attribute”属性被忽略  
  
 编译器忽略了函数（级别 3 警告）或数据（等级 2 警告）的 `__fastcall`、**static** 或 **inline** 属性。  
  
### 通过检查以下可能的原因进行修复  
  
1.  带数据的 `__fastcall` 属性。  
  
2.  带 **main** 函数的 **static** 或 **inline** 属性。