---
title: "错误 C1021 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1021"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1021"
ms.assetid: e23171f4-ca6b-40c0-a913-a2edc6fa3766
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 错误 C1021
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无效的预处理器命令“string”  
  
 `string` 不是有效的[预处理器指令](../../preprocessor/preprocessor-directives.md)。 若要解决此错误，请使用对于 `string` 有效预处理器名称。  
  
 下面的示例生成 C1021：  
  
```  
// C1021.cpp #BadPreProcName    // C1021 delete line  
```