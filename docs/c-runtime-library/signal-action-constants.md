---
title: signal 操作常量 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- SIG_IGN
- SIG_DFL
dev_langs:
- C++
helpviewer_keywords:
- signal action constants
- SIG_IGN constant
- SIG_DFL constant
ms.assetid: c3cb4f15-d39e-4d9d-84f9-0d33e3eb5993
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6b6f645d474e697bf662a5dd63973dd54c329eb9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409431"
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