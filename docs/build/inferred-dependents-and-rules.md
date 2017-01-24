---
title: "推导出的依赖项和规则 | Microsoft Docs"
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
  - "依赖项, 推断"
  - "NMAKE 中推断出的依赖项"
  - "NMAKE 中推断出的规则"
  - "规则, 推断"
ms.assetid: 9381e74a-53d9-445c-836d-0ff7ef6112d9
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 推导出的依赖项和规则
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果存在适用的推理规则，NMAKE 则为目标采用推理的依赖项。  规则适用下列情况：  
  
-   *toext* 与目标的扩展名匹配。  
  
-   *fromext* 与具有目标的基名称并存在于当前或指定目录中的文件的扩展名匹配。  
  
-   *fromext* 位于 [.SUFFIXES](../build/dot-directives.md) 中；匹配规则中没有其他的 *fromext* 有更高的 **.SUFFIXES** 优先级。  
  
-   没有显式依赖项有更高的 **.SUFFIXES** 优先级。  
  
 推理的依赖项会导致意外的副作用。  如果目标的描述块包含命令，NMAKE 将执行这些命令而不是规则中的命令。  
  
## 请参阅  
 [推理规则](../build/inference-rules.md)