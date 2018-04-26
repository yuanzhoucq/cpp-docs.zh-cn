---
title: quick_exit1 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- quick_exit
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
dev_langs:
- C++
helpviewer_keywords:
- quick_exit function
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fde06fc83b27b8bba43e3fa929cc8b97bb68dd06
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="quickexit"></a>quick_exit

导致产生正常程序终止。

## <a name="syntax"></a>语法

```C
__declspec(noreturn) void quick_exit(
    int status
);
```

### <a name="parameters"></a>参数

*status*<br/>
要返回给主机环境的状态代码。

## <a name="return-value"></a>返回值

**Quick_exit**函数无法返回到其调用方。

## <a name="remarks"></a>备注

**Quick_exit**函数导致正常程序终止。 它调用注册的任何函数**atexit**， **_onexit**或信号处理程序注册的**信号**函数。 行为是不确定的如果**quick_exit**称为超过一次，或如果**退出**还调用函数。

**Quick_exit**函数调用，在最后一个单元中、 先进先出 (LIFO) 顺序、 注册的函数**at_quick_exit**，只是为时已调用这些函数注册的函数。  如果在调用已注册函数的过程中进行会终止该函数调用的 [longjmp](longjmp.md) 调用，则行为不确定。

调用了已注册的函数之后， **quick_exit**时，将调用 **_Exit**使用*状态*控制权返回给主机环境的值。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**quick_exit**|\<process.h> 或 \<stdlib.h>|

有关兼容性的更多信息，请参见 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec、_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
[_spawn、_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
