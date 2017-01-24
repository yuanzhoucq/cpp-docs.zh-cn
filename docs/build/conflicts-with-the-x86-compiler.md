---
title: "与 x86 编译器冲突 | Microsoft Docs"
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
ms.assetid: 8e47f0d3-afe0-42d9-9efa-de239ddd3a05
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 与 x86 编译器冲突
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当使用 x86 编译器编译应用程序时，大于 4 字节的数据类型不会自动在堆栈上对齐。  由于 x86 编译器的体系结构为 4 字节对齐堆栈，因此大于 4 字节的任何数据类型（例如，64 位整数）均无法自动与 8 字节地址对齐。  
  
 使用未对齐的数据具有两层隐含意义。  
  
-   与访问对齐的位置相比，可能需要更长的时间来访问未对齐的位置。  
  
-   在互锁操作中，不能使用未对齐的位置。  
  
 如果您需要更为严格的对齐，请使用 `__declspec(align(N)) on your variable declarations`。  这会导致编译器与堆栈动态对齐以满足您的规范。  但是，在运行时动态调整堆栈可能会导致应用程序的执行速度变慢。  
  
## 请参阅  
 [类型和存储](../build/types-and-storage.md)   
 [align](../cpp/align-cpp.md)