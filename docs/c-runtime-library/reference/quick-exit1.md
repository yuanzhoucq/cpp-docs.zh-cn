---
title: "quick_exit1 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname: quick_exit
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- quick_exit
- process/quick_exit
- stdlib/quick_exit
dev_langs: C++
helpviewer_keywords: quick_exit function
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d2ae187d0132ca53b1ffba2b26ef18fa467b9072
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="quickexit"></a>quick_exit
导致产生正常程序终止。  
  
## <a name="syntax"></a>语法  
  
```  
__declspec(noreturn) void quick_exit(  
    int status  
);  
```  
  
#### <a name="parameters"></a>参数  
 status  
 要返回给主机环境的状态代码。  
  
## <a name="return-value"></a>返回值  
 `quick_exit` 函数无法返回到其调用方。  
  
## <a name="remarks"></a>备注  
 `quick_exit` 函数导致正常程序终止。 它不调用 `atexit`、 `_onexit` 注册的任何函数或 `signal` 函数注册的信号处理程序。 如果多次调用 `quick_exit` ，或如果还调用了 `exit` 函数，则行为不确定。  
  
 `quick_exit` 函数会按后进先出 (LIFO) 顺序调用 `at_quick_exit`注册的函数（注册该函数时已调用的函数除外）。  如果在已注册函数的调用过程中进行会终止该函数调用的 [longjmp](../../c-runtime-library/reference/longjmp.md) 调用，则行为不确定。  
  
 调用了已注册函数之后，`quick_exit` 会使用 `_Exit` 值调用 `status`，以将控制权返回给主机环境。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`quick_exit`|\<process.h> 或 \<stdlib.h>|  
  
 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [atexit](../../c-runtime-library/reference/atexit.md)   
 [_exec、_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)   
 [exit、_Exit、_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit、_onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)   
 [_spawn、_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)   
 [system、_wsystem](../../c-runtime-library/reference/system-wsystem.md)