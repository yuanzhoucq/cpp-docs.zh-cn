---
title: "ML Nonfatal Error A2031 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "A2031"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A2031"
ms.assetid: d5b11f58-4a00-42be-9062-8fa8728e6306
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# ML Nonfatal Error A2031
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**必须是索引或基寄存器**  
  
 尝试使用不是内存中表达式的基础或索引注册的注册。  
  
 例如，下面的表达式导致此错误:  
  
```  
[ax]  
[bl]  
```  
  
## 请参阅  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)