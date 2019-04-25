---
title: _onexit、_onexit_m
ms.date: 11/04/2016
apiname:
- _onexit
- _onexit_m
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
apitype: DLLExport
f1_keywords:
- _onexit
- onexit_m
- onexit
- _onexit_m
helpviewer_keywords:
- onexit function
- registry, registering exit routines
- _onexit_m function
- onexit_m function
- _onexit function
- registering exit routines
- registering to be called on exit
ms.assetid: 45743298-0e2f-46cf-966d-1ca44babb443
ms.openlocfilehash: c190f777032904802f771bab9fc323ba305ff32e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156040"
---
# <a name="onexit-onexitm"></a>_onexit、_onexit_m

注册在退出时要调用的例程。

## <a name="syntax"></a>语法

```C
_onexit_t _onexit(
   _onexit_t function
);
_onexit_t_m _onexit_m(
   _onexit_t_m function
);
```

### <a name="parameters"></a>参数

*function*<br/>
指向在退出时要调用的函数的指针。

## <a name="return-value"></a>返回值

**_onexit**如果成功，则返回对函数的指针或**NULL**如果没有空间来存储函数指针。

## <a name="remarks"></a>备注

**_Onexit**函数被传入函数的地址 (*函数*) 程序正常终止时要调用。 后续调用 **_onexit**创建一个函数注册表的后进先出 （上一次中的先进先出） 顺序执行的函数。 函数传递给 **_onexit**不能采用参数。

在这种情况时 **_onexit**从 DLL 注册的例程中调用 **_onexit** DLL 上的运行的卸载后**DllMain**使用 DLL_PROCESS_DETACH 调用。

**_onexit**是 Microsoft 扩展。 若要获得 ANSI 可移植性，请使用 [atexit](atexit.md)。 **_Onexit_m**函数的版本是适用于混合的模式。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_onexit**|\<stdlib.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_onexit.c

#include <stdlib.h>
#include <stdio.h>

/* Prototypes */
int fn1(void), fn2(void), fn3(void), fn4 (void);

int main( void )
{
   _onexit( fn1 );
   _onexit( fn2 );
   _onexit( fn3 );
   _onexit( fn4 );
   printf( "This is executed first.\n" );
}

int fn1()
{
   printf( "next.\n" );
   return 0;
}

int fn2()
{
   printf( "executed " );
   return 0;
}

int fn3()
{
   printf( "is " );
   return 0;
}

int fn4()
{
   printf( "This " );
   return 0;
}
```

### <a name="output"></a>Output

```Output
This is executed first.
This is executed next.
```

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[atexit](atexit.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[__dllonexit](../../c-runtime-library/dllonexit.md)<br/>
