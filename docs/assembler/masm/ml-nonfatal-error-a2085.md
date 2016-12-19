---
title: "ML Nonfatal Error A2085 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "A2085"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A2085"
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ML Nonfatal Error A2085
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**在当前 CPU 模式或注册不接受的命令**  
  
 尝试使用为当前处理器架构无效的命令、寄存器或关键字。  
  
 例如， 32 位寄存器需要 [.386](../../assembler/masm/dot-386.md) 上面。  控件注册例如 CR0 需要特权方式 [.386P](../../assembler/masm/dot-386p.md) 上面。  此错误。 **NEAR32**、 **FAR32**和 **简单** 关键字也会生成，要求。**386** 上面。  
  
## 请参阅  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)