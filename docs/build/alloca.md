---
title: "alloca | Microsoft Docs"
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
ms.assetid: 2b209335-e3a0-4934-93f0-3b5925d22918
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# alloca
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

要求 [\_alloca](../c-runtime-library/reference/alloca.md) 为 16 字节对齐，此外还有其他要求以便使用帧指针。  
  
 已分配的堆栈需要在该堆栈下为随后调用的函数的参数提供空间（请参见 [堆栈分配](../build/stack-allocation.md)）。  
  
## 请参阅  
 [堆栈使用](../build/stack-usage.md)