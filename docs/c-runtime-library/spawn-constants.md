---
title: "spawn 常量 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_P_NOWAIT"
  - "_P_OVERLAY"
  - "_P_WAIT"
  - "_P_DETACH"
  - "_P_NOWAITO"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_P_DETACH 常量"
  - "_P_NOWAIT 常量"
  - "_P_NOWAITO 常量"
  - "_P_OVERLAY 常量"
  - "_P_WAIT 常量"
  - "P_DETACH 常量"
  - "P_NOWAIT 常量"
  - "P_NOWAITO 常量"
  - "P_OVERLAY 常量"
  - "P_WAIT 常量"
  - "生成常量"
ms.assetid: e0533e88-d362-46fc-b53c-5f193226d879
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# spawn 常量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
#include <process.h>  
```  
  
## 备注  
 `mode` 参数以确定调用进程执行的操作在派生操作期间及之中。  以下 `mode` 的值可能适用：  
  
|常量|含义|  
|--------|--------|  
|`_P_OVERLAY`|为更新覆盖一过程调用的过程，使用调用进程 \(作用与 `_exec` 调用相同\)。|  
|`_P_WAIT`|挂起的调用线程，直至执行过程的更新完成 \(同步 `_spawn`\)。|  
|`_P_NOWAIT`, `_P_NOWAITO`|继续在更新过程 \(异步 `_spawn`\) 的同时执行一个名为的进程。|  
|`_P_DETACH`|继续执行调用进程；更新过程在后台运行没有到控制台或键盘的访问权限。  调用 `_cwait` 更新过程将失败。  这是一个异步`_spawn`。|  
  
## 请参阅  
 [\_spawn, \_wspawn 函数](../c-runtime-library/spawn-wspawn-functions.md)   
 [全局常量](../c-runtime-library/global-constants.md)