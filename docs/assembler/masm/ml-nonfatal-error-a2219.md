---
title: "ML Nonfatal Error A2219 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "A2219"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A2219"
ms.assetid: 5ebc2f40-e47e-4f8e-b7b9-960b9cfc9f6d
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# ML Nonfatal Error A2219
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**偏移量的错误对齐展开的代码**  
  
 [.ALLOCSTACK](../../assembler/masm/dot-allocstack.md) 和 [.SAVEREG](../../assembler/masm/dot-savereg.md) 的操作数必须是多线程的 8。  [.SAVEXMM128](../../assembler/masm/dot-savexmm128.md) 和 [.SETFRAME](../../assembler/masm/dot-setframe.md) 的操作数必须是多个为 16。  
  
## 请参阅  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)