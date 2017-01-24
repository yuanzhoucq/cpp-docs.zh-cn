---
title: "推理规则 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NMAKE 中的推理规则"
  - "NMAKE 程序, 推理规则"
  - "规则, 推理"
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 推理规则
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

推理规则提供命令来更新目标并推理目标的依赖项。  推理规则中的扩展名与具有相同基名称的单个目标和依赖项匹配。  推理规则是用户定义的，或预定义的；预定义的规则可以重新定义。  
  
 如果过期的依赖项没有命令，并且如果 [.SUFFIXES](../build/dot-directives.md) 包含依赖项的扩展名，则 NMAKE 使用其扩展名与当前或指定目录中的目标和现有文件匹配的规则。  如果有多个规则与现有文件匹配，**.SUFFIXES** 列表将确定使用哪一个规则；列表优先级从左向右按降序排列。  如果依赖文件不存在，并且未在另一个描述块中作为目标列出，则推理规则可以从具有相同基名称的另一个文件创建缺少的依赖项。  如果描述块的目标没有依赖项或命令，推理规则可以更新目标。  即使不存在描述块，推理规则也可以生成命令行目标。  即使指定了显式依赖项，NMAKE 也可以调用推理依赖项的规则。  
  
## 您想进一步了解什么？  
 [定义规则](../build/defining-a-rule.md)  
  
 [批模式规则](../build/batch-mode-rules.md)  
  
 [预定义的规则](../build/predefined-rules.md)  
  
 [推导出的依赖项和规则](../build/inferred-dependents-and-rules.md)  
  
 [推理规则中的优先级](../build/precedence-in-inference-rules.md)  
  
## 请参阅  
 [NMAKE 参考](../build/nmake-reference.md)