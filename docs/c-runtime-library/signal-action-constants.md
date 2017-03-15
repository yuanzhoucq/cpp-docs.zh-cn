---
title: "signal 操作常量 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SIG_IGN"
  - "SIG_DFL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SIG_DFL 常量"
  - "SIG_IGN 常量"
  - "signal 操作常量"
ms.assetid: c3cb4f15-d39e-4d9d-84f9-0d33e3eb5993
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# signal 操作常量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在中断接收到信号时依赖于 `func`值时采取措施。  
  
## 语法  
  
```  
#include <signal.h>  
```  
  
## 备注  
 `func`是函数参数必须在 SIGNAL.H. 列出和定义的地址或一清单常数。  
  
 `SIG_DFL`  
 使用系统默认响应。  如果调用程序使用流 I\/O，不刷新运行库创建的缓冲区。  
  
 `SIG_IGN`  
 忽略中断信号。  因为该进程的浮点状态未定义，不应为 `SIGFPE`指定此值。  
  
 `SIG_SGE`  
 在信号指示错误生成。  
  
 `SIG_ACK`  
 指示接收提交。  
  
 `SIG_ERR`  
 指示从错误的信号的返回类型发生。  
  
## 请参阅  
 [signal](../c-runtime-library/reference/signal.md)   
 [全局常量](../c-runtime-library/global-constants.md)