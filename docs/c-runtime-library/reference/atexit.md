---
title: atexit
ms.date: 11/04/2016
api_name:
- atexit
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- atexit
helpviewer_keywords:
- processing, at exit
- atexit function
ms.assetid: 92c156d2-8052-4e58-96dc-00128baac6f9
ms.openlocfilehash: b91e6dad81f006b0b94ac17a940e840386f6d2b1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939662"
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

如果成功，则**atexit**返回 0; 如果出现错误，则返回非零值。

## <a name="remarks"></a>备注

当程序正常终止时，向**atexit**函数传递要调用的函数*func*的地址。 对**atexit**的后续调用将创建一个函数寄存器，这些函数按后进先出（LIFO）顺序执行。 传递给**atexit**的函数不能采用参数。 **atexit**和 **_onexit**使用堆来保存函数的注册。 因此，可以注册的函数的数量仅受堆内存限制。

**Atexit**函数中的代码不应包含任何在调用**atexit**函数时可能已卸载的 DLL 的依赖项。

若要生成符合 ANSI 标准的应用程序，请使用 ANSI 标准的**atexit**函数（而不是类似的 **_onexit**函数）。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**atexit**|\<stdlib.h>|

## <a name="example"></a>示例

调用**atexit**时，此程序将四个函数推送到要执行的函数堆栈上。 当程序退出时，这些程序以后进先出的方式执行。

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
