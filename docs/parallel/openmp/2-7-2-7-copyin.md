---
title: "2.7.2.7 copyin | Microsoft Docs"
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
ms.assetid: 76cfb9f8-bf65-4585-adbf-fd933f5606b4
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2.7 copyin
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**copyin** 子句为在执行并行区域的团队的每个线程提供一种机制进行相同的值。 **threadprivate** 变量。  对于每个 **copyin** 在子句中指定的变量，变量的值在团队中的主线程在并行区域开始复制，，如同按指派\)，对线程专用副本。  **copyin** 子句的语法如下所示:  
  
```  
  
copyin(  
variable-list  
)  
  
```  
  
 为 **copyin** 子句的限制如下所示:  
  
-   在 **copyin** 子句中指定的变量必须具有访问，明确的复制赋值运算符。  
  
-   在 **copyin** 子句中指定的变量必须是 **threadprivate** 变量。