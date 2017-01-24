---
title: "signal 常量 | Microsoft Docs"
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
  - "SIGTERM"
  - "SIGFPE"
  - "SIGABRT"
  - "SIGILL"
  - "SIGINT"
  - "SIGSEGV"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "SIGABRT 常量"
  - "SIGFPE 常量"
  - "SIGILL 常量"
  - "SIGINT 常量"
  - "signal 常量"
  - "SIGSEGV 常量"
  - "SIGTERM 常量"
ms.assetid: a3b39281-dae7-4e44-8d68-e6a610c669dd
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# signal 常量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 语法  
  
```  
#include <signal.h>  
```  
  
## 备注  
 `sig` 参数必须是下面列出的某清单常数定义 \(在 SIGNAL.H\)。  
  
 `SIGABRT`  
 Abnormal termination。  默认终止操作以退出代码 3 调用的程序。  
  
 `SIGABRT_COMPAT`  
 和 SIGABRT 相同。  为了与其他平台的兼容性。  
  
 `SIGFPE`  
 浮点、溢出错误例如，被零除、无效的操作。  默认终止操作调用程序。  
  
 `SIGILL`  
 非法指令。  默认终止操作调用程序。  
  
 `SIGINT`  
 CTRL\+C 中断。  默认终止操作以退出代码 3 调用的程序。  
  
 `SIGSEGV`  
 非法存储区访问。  默认终止操作调用程序。  
  
 `SIGTERM`  
 停止请求发送到程序。  默认终止操作以退出代码 3 调用的程序。  
  
 `SIG_ERR`  
 指示从错误的信号的返回类型发生。  
  
## 请参阅  
 [signal](../c-runtime-library/reference/signal.md)   
 [raise](../c-runtime-library/reference/raise.md)   
 [全局常量](../c-runtime-library/global-constants.md)