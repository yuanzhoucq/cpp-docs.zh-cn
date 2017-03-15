---
title: "内联程序集中的段引用 | Microsoft Docs"
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
  - "内联程序集, 寄存器"
  - "内联程序集, 段引用"
  - "引用, 内联程序集"
  - "寄存器"
  - "寄存器, 内联程序集"
  - "内联程序集中的段引用"
ms.assetid: c63e6bb4-49d9-4fa1-bb22-eea21b5cbc0f
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 内联程序集中的段引用
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 必须按寄存器而不是按名称引用段（例如，段名 `_TEXT` 是无效的）。  段重写必须显式使用寄存器，就像在 ES:\[BX\] 中一样。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [在 \_\_asm 块中使用汇编语言](../../assembler/inline/using-assembly-language-in-asm-blocks.md)