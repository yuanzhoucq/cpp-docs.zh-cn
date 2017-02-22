---
title: "位域 | Microsoft Docs"
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
  - "位域"
ms.assetid: e9a1010d-1e1b-487f-9943-3c574e08f544
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 位域
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

结构位域限制为 64 位，可以是有符号整数、无符号整数、int64 或无符号 int64。  跨越类型边界的位域将跳过位，以使位域与下一个类型对齐方式对齐。  例如，整数位域可能不能跨越 32 位边界。  
  
## 请参阅  
 [类型和存储](../build/types-and-storage.md)