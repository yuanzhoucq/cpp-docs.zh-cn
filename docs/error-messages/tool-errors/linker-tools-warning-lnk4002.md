---
title: "链接器工具警告 LNK4002 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4002"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4002"
ms.assetid: 09f81af5-e51c-496c-a6eb-2863e85375c3
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 链接器工具警告 LNK4002
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在对象中定义了符号  
  
 在 `object` 中以未修饰形式指定了以修饰形式显示的符号，但未能找到修饰符号的唯一匹配项。  该警告总是前有警告 [LNK4022](../../error-messages/tool-errors/linker-tools-warning-lnk4022.md)，后有错误 [LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md)。