---
title: "signal 操作常量 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SIG_IGN
- SIG_DFL
dev_langs: C++
helpviewer_keywords:
- signal action constants
- SIG_IGN constant
- SIG_DFL constant
ms.assetid: c3cb4f15-d39e-4d9d-84f9-0d33e3eb5993
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 256f11d3f8daa8a00e70e24aa19c31b71413c13c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="signal-action-constants"></a>signal 操作常量
收到中断信号后采取的操作取决于 `func` 的值。  
  
## <a name="syntax"></a>语法  
  
```  
#include <signal.h>  
```  
  
## <a name="remarks"></a>备注  
 `func` 参数必须是一个函数地址或 SIGNAL.H 中定义的下列清单常量之一。  
  
 `SIG_DFL`  
 使用系统默认的响应。 如果调用程序使用流 I/O，将不会刷新运行时库创建的缓冲区。  
  
 `SIG_IGN`  
 忽略中断信号。 不得为 `SIGFPE` 指定该值，因为未定义此进程的浮点状态。  
  
 `SIG_SGE`  
 指示信号中发生错误。  
  
 `SIG_ACK`  
 指示已收到确认。  
  
 `SIG_ERR`  
 指示已发生错误的信号的返回类型。  
  
## <a name="see-also"></a>请参阅  
 [signal](../c-runtime-library/reference/signal.md)   
 [全局常量](../c-runtime-library/global-constants.md)