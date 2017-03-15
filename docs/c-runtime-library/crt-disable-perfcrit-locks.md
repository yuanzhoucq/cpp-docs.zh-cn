---
title: "_CRT_DISABLE_PERFCRIT_LOCKS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_CRT_DISABLE_PERFCRIT_LOCKS"
  - "CRT_DISABLE_PERFCRIT_LOCKS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CRT_DISABLE_PERFCRIT_LOCKS 常量"
  - "CRT_DISABLE_PERFCRIT_LOCKS 常量"
ms.assetid: 36cc2d86-cdb1-4b2b-a03c-c0d3818e7c6f
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# _CRT_DISABLE_PERFCRIT_LOCKS
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 I\/O 操作中禁用关键型性能锁定。  
  
## 语法  
  
```  
#define _CRT_DISABLE_PERFCRIT_LOCKS  
```  
  
## 备注  
 通过强制所有 I\/O 操作均采用单线程 I\/O 模型定义该符号可以增强单线程 I\/O 绑定的程序的性能。  有关详细信息，请参阅[多线程库性能](../c-runtime-library/multithreaded-libraries-performance.md)。  
  
## 请参阅  
 [全局常量](../c-runtime-library/global-constants.md)