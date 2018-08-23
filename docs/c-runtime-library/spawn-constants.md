---
title: spawn 常量 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _P_NOWAIT
- _P_OVERLAY
- _P_WAIT
- _P_DETACH
- _P_NOWAITO
dev_langs:
- C++
helpviewer_keywords:
- _P_OVERLAY constant
- P_DETACH constant
- P_OVERLAY constant
- P_NOWAIT constant
- _P_DETACH constant
- _P_NOWAIT constant
- _P_NOWAITO constant
- P_NOWAITO constant
- spawn constants
- P_WAIT constant
- _P_WAIT constant
ms.assetid: e0533e88-d362-46fc-b53c-5f193226d879
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3a069f9f29f6fd15c3ce21111a37757519af229
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32408734"
---
# <a name="spawn-constants"></a>spawn 常量
## <a name="syntax"></a>语法  
  
```  
#include <process.h>  
```  
  
## <a name="remarks"></a>备注  
 `mode` 参数决定在生成操作前或操作期间由调用进程执行的操作。 `mode` 可能具有以下值：  
  
|返回的常量|含义|  
|--------------|-------------|  
|`_P_OVERLAY`|使用新进程覆盖调用进程，销毁调用进程（与 `_exec` 调用的效果相同）。|  
|`_P_WAIT`|挂起调用线程，直至执行完新进程（同步 `_spawn`）。|  
|`_P_NOWAIT`, `_P_NOWAITO`|继续将调用进程与新进程一起执行（异步 `_spawn`）。|  
|`_P_DETACH`|继续执行调用进程；在无法访问控制台或键盘的后台运行新进程。 针对新进程调用 `_cwait` 将失败。 这是一个异步 `_spawn`。|  
  
## <a name="see-also"></a>请参阅  
 [_spawn、_wspawn 函数](../c-runtime-library/spawn-wspawn-functions.md)   
 [全局常量](../c-runtime-library/global-constants.md)