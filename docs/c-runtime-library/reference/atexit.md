---
title: atexit | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- processing, at exit
- atexit function
ms.assetid: 92c156d2-8052-4e58-96dc-00128baac6f9
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3a5dbe5e8bf71c268783893665e8e95bb587891a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
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

**Atexit**函数传递的函数地址*func*当程序正常终止时调用。 对连续调用**atexit**创建按后进先出 (LIFO) 顺序执行的函数的寄存器。 函数传递给**atexit**不能接受参数。 **atexit**和 **_onexit**使用堆保存的寄存器的函数。 因此，可以注册的函数的数量仅受堆内存限制。

中的代码**atexit**函数不应包含任何依赖于可能已卸载了时的任何 DLL **atexit**调用函数。

若要生成符合 ANSI 标准的应用程序，使用 ANSI 标准**atexit**函数 (而不是类似 **_onexit**函数)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**atexit**|\<stdlib.h>|

## <a name="example"></a>示例

到堆栈上的函数时要执行此程序推送四个函数**atexit**调用。 当程序退出时，这些程序以后进先出的方式执行。

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
