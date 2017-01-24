---
title: "_WAIT_CHILD、_WAIT_GRANDCHILD | Microsoft Docs"
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
  - "_WAIT_GRANDCHILD"
  - "WAIT_CHILD"
  - "WAIT_GRANDCHILD"
  - "_WAIT_CHILD"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_WAIT_CHILD 常量"
  - "_WAIT_GRANDCHILD 常量"
  - "WAIT_CHILD 常量"
  - "WAIT_GRANDCHILD 常量"
ms.assetid: 7acd96fa-d118-4339-bb00-e5afaf286945
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _WAIT_CHILD、_WAIT_GRANDCHILD
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
  
#include <process.h>  
  
```  
  
## 备注  
 `_cwait` 函数可以由所有进程使用来等待其他进程（如果知道进程 ID）。  该行为参数可以是下列值之一：  
  
|常量|含义|  
|--------|--------|  
|`_WAIT_CHILD`|直到制定的新进程终止才调用进程等待。|  
|`_WAIT_GRANDCHILD`|直到指定新进程才调用程序，并且终止所有由新进程创建的进程。|  
  
## 请参阅  
 [\_cwait](../c-runtime-library/reference/cwait.md)   
 [全局常量](../c-runtime-library/global-constants.md)