---
title: atexit
ms.date: 11/04/2016
apiname:
- atexit
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
- atexit
helpviewer_keywords:
- processing, at exit
- atexit function
ms.assetid: 92c156d2-8052-4e58-96dc-00128baac6f9
ms.openlocfilehash: 48f0fbfa1f3350f73899fcdbb3bf7922f1c6174d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556633"
---
# <a name="atexit"></a>atexit

处理退出时指定的函数。

## <a name="syntax"></a>语法

```C
int atexit(
   void (__cdecl *func )( void )
);
```

### <a name="parameters"></a>参数

*func*<br/>
要调用的函数。

## <a name="return-value"></a>返回值

**atexit**返回如果成功，则为 0 或一个非零值，如果发生错误。

## <a name="remarks"></a>备注

**Atexit**函数传递的函数地址*func*程序正常终止时要调用。 后续调用**atexit**创建按后进先出 (LIFO) 顺序执行的函数的一个函数注册表。 函数传递给**atexit**不能采用参数。 **atexit**并 **_onexit**使用堆保存函数注册表。 因此，可以注册的函数的数量仅受堆内存限制。

中的代码**atexit**函数不应包含已被卸载时的任何 DLL 上的任何依赖项**atexit**调用函数。

若要生成符合 ANSI 的应用程序，请使用 ANSI 标准**atexit**函数 (而不是类似 **_onexit**函数)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**atexit**|\<stdlib.h>|

## <a name="example"></a>示例

此程序四个函数推送到堆栈上时执行的函数**atexit**调用。 当程序退出时，这些程序以后进先出的方式执行。

```C
// crt_atexit.c
#include <stdlib.h>
#include <stdio.h>

void fn1( void ), fn2( void ), fn3( void ), fn4( void );

int main( void )
{
   atexit( fn1 );
   atexit( fn2 );
   atexit( fn3 );
   atexit( fn4 );
   printf( "This is executed first.\n" );
}

void fn1()
{
   printf( "next.\n" );
}

void fn2()
{
   printf( "executed " );
}

void fn3()
{
   printf( "is " );
}

void fn4()
{
   printf( "This " );
}
```

```Output
This is executed first.
This is executed next.
```

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
