---
title: "推理规则中的优先级 | Microsoft Docs"
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
  - "优先级, 一条推理规则"
  - "规则, 推理"
ms.assetid: 69e3dc02-0815-4c3a-b02b-1cb85fceaf24
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 推理规则中的优先级
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果推理规则有多个定义，NMAKE 使用优先级最高的定义。  以下列表由高至低显示了优先级的顺序：  
  
1.  在生成文件中定义的推理规则；越晚定义，优先级越高。  
  
2.  在 Tools.ini 中定义的推理规则；越晚定义，优先级越高。  
  
3.  预定义的推理规则。  
  
## 请参阅  
 [推理规则](../build/inference-rules.md)