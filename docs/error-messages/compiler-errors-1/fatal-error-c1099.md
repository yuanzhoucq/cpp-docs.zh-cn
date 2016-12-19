---
title: "错误 C1099 | Microsoft Docs"
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
  - "C1099"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1099"
ms.assetid: c050b074-a06a-4026-9e10-569029cc0739
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1099
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“编辑并继续”引擎正在终止编译  
  
 “编辑并继续”在准备进行编译代码更改的过程中加载了一个预编译头文件，但后续操作（例如预编译头 `#include` 语句前的代码更改或停止调试器）阻止“编辑并继续”使用该进程完成编译。 不需要执行任何操作来修复此错误。