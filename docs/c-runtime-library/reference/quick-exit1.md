---
title: quick_exit1
ms.date: 11/04/2016
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
helpviewer_keywords:
- quick_exit function
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
ms.openlocfilehash: 50f1ee72cce04c2bebc8f7396a2b6fad98301dd7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429010"
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

**Quick_exit**函数不能返回给调用方。

## <a name="remarks"></a>备注

**Quick_exit**函数导致正常程序终止。 它将调用注册的任何函数**atexit**， **_onexit**或信号处理程序由注册**信号**函数。 行为是不确定，如果**quick_exit**称为超过一次，或如果**退出**还调用函数。

**Quick_exit**函数中最后一个单元中、 先进先出 (LIFO) 顺序、 已注册的函数调用**at_quick_exit**，但为时已调用这些函数注册的函数。  如果在已注册函数的调用过程中进行会终止该函数调用的 [longjmp](longjmp.md) 调用，则行为不确定。

调用已注册的函数之后， **quick_exit**调用 **_Exit**通过*状态*控制权返回给主机环境的值。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
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
