---
title: "推导出的依赖项 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 推导出的依赖项
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

推理依赖项从推理规则中派生，并先于显式依赖项进行评估。  如果推理依赖项对于它的目标是过期的，则 NMAKE 调用该依赖项的命令块。  如果推理依赖项不存在或对于它自己的依赖项已过期，则 NMAKE 首先更新推理依赖项。  有关推理依赖项的更多信息，请参见[推理规则](../build/inference-rules.md)。  
  
## 请参阅  
 [依赖项](../build/dependents.md)