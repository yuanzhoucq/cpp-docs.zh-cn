---
title: _onexit、_onexit_m | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- onexit function
- registry, registering exit routines
- _onexit_m function
- onexit_m function
- _onexit function
- registering exit routines
- registering to be called on exit
ms.assetid: 45743298-0e2f-46cf-966d-1ca44babb443
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ac59e64c1e47d699170af772aeba60a7895dfdc2
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
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

*函数*<br/>
指向在退出时要调用的函数的指针。

## <a name="return-value"></a>返回值

**_onexit**将指针返回到该函数，如果成功或**NULL**如果没有任何空间来存储函数的指针。

## <a name="remarks"></a>备注

**_Onexit**函数传递的函数地址 (*函数*) 在程序正常终止时调用。 对连续调用 **_onexit**创建按 LIFO （后进中第一个-出） 顺序执行的函数的寄存器。 函数传递给 **_onexit**不能接受参数。

在这种情况时 **_onexit**从 DLL，注册的例程中调用 **_onexit**在 DLL 上的运行卸载后**DllMain**使用 DLL_PROCESS_DETACH 调用。

**_onexit**是 Microsoft 扩展。 若要获得 ANSI 可移植性，请使用 [atexit](atexit.md)。 **_Onexit_m**该函数的版本为混合模式下使用。

## <a name="requirements"></a>要求

|例程|必需的标头|
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

### <a name="output"></a>输出

```Output
This is executed first.
This is executed next.
```

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[atexit](atexit.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[__dllonexit](../../c-runtime-library/dllonexit.md)<br/>
