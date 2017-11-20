---
title: "signal 常量 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SIGTERM
- SIGFPE
- SIGABRT
- SIGILL
- SIGINT
- SIGSEGV
dev_langs: C++
helpviewer_keywords:
- SIGTERM constant
- SIGABRT constant
- SIGSEGV constant
- SIGFPE constant
- SIGINT constant
- signal constants
- SIGILL constant
ms.assetid: a3b39281-dae7-4e44-8d68-e6a610c669dd
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fddb279acfbb6d8841ac17a27cd43de205dc9dbc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="signal-constants"></a>signal 常量
## <a name="syntax"></a>语法  
  
```  
#include <signal.h>  
```  
  
## <a name="remarks"></a>备注  
 `sig` 参数必须是 SIGNAL.H 定义的下列清单常量之一。  
  
 `SIGABRT`  
 异常终止。 默认操作将使用退出代码 3 终止调用程序。  
  
 `SIGABRT_COMPAT`  
 与 SIGABRT 相同。 针对与其他平台的兼容性。  
  
 `SIGFPE`  
 浮点错误，例如溢出、除数为零或操作无效。 默认操作将终止调用程序。  
  
 `SIGILL`  
 非法指令。 默认操作将终止调用程序。  
  
 `SIGINT`  
 CTRL+C 中断。 默认操作将使用退出代码 3 终止调用程序。  
  
 `SIGSEGV`  
 非法存储访问。 默认操作将终止调用程序。  
  
 `SIGTERM`  
 发送到程序的终止请求。 默认操作将使用退出代码 3 终止调用程序。  
  
 `SIG_ERR`  
 指示已发生错误的信号的返回类型。  
  
## <a name="see-also"></a>另请参阅  
 [signal](../c-runtime-library/reference/signal.md)   
 [raise](../c-runtime-library/reference/raise.md)   
 [全局常量](../c-runtime-library/global-constants.md)