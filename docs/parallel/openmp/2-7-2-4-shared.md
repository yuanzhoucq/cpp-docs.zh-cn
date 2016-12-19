---
title: "2.7.2.4 shared | Microsoft Docs"
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
ms.assetid: c9c5d653-58fc-4620-ab0a-443ac4f8ba2e
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.2.4 shared
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此子句共享出现在所有线程中的 *变量列出* 团队的变量。  所有在 team access 中线程 **共享** 变量的同一内存块。  
  
 **共享** 子句的语法如下所示:  
  
```  
shared(variable-list)  
```