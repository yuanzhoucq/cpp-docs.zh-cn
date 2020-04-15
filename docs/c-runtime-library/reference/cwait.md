---
title: _cwait
ms.date: 4/2/2020
api_name:
- _cwait
- _o__cwait
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
- api-ms-win-crt-process-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cwait
helpviewer_keywords:
- cwait function
- _cwait function
ms.assetid: d9b596b5-45f4-4e03-9896-3f383cb922b8
ms.openlocfilehash: d54f62c8ce391b2c8ead92a0a73ac48e6f2b3cb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348154"
---
# <a name="_cwait"></a>_cwait

请等待，直到另一个进程终止。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
intptr_t _cwait(
   int *termstat,
   intptr_t procHandle,
   int action
);
```

### <a name="parameters"></a>参数

*术语统计*<br/>
指向将存储指定进程的结果代码的缓冲区的指针，或**NULL**。

*普罗克汉德尔*<br/>
要等待的进程的句柄（即，在 **_cwait**可以返回之前必须终止的进程）。

*行动*<br/>
NULL：被 Windows 操作系统应用程序忽略;对于其他应用程序：要在*procHandle*上执行的操作代码。

## <a name="return-value"></a>返回值

当指定的进程成功完成时，返回指定进程的句柄，并将*术语统计*到指定进程返回的结果代码。 否则，返回 -1 并设置**errno，** 如下所示。

|“值”|说明|
|-----------|-----------------|
|**ECHILD**|不存在指定的进程，*进程*无效，或者对[GetExitCodeProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess)或[WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject) API 的调用失败。|
|**埃因瓦尔**|*操作*无效。|

有关这些代码及其他返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_cwait**函数等待*进程提供的*指定进程的进程 ID 的终止。 传递给 **_cwait**的*procHandle*值应该是调用创建指定进程的[_spawn](../../c-runtime-library/spawn-wspawn-functions.md)函数返回的值。 如果在调用 **_cwait**之前进程 ID 终止 **，_cwait**立即返回。 **_cwait**可用于任何进程以等待存在有效句柄 （*procHandle*） 的任何其他已知进程。

*术语统计*指向将存储指定进程的返回代码的缓冲区。 *术语统计值*指示指定进程是否通过调用 Windows [ExitProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) API 正常终止。 如果指定的进程调用**退出**或 **_exit、** 从**main**返回或到达**主**的末尾，则内部调用**ExitProcess。** 有关通过*术语统计表*传回的值的详细信息，请参阅[GetExitCodeProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess)。 如果使用*术语统计*的**NULL**值调用 **_cwait，** 则不存储指定进程的返回代码。

Windows 操作系统将忽略*操作*参数，因为在这些环境中未实现父子关系。

除非*进程处理*是 -1 或 -2（对当前进程或线程的句柄），否则句柄将关闭。 因此，在这种情况下，请不要使用返回的句柄。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_cwait**|\<process.h>|\<errno.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_cwait.c
// compile with: /c
// This program launches several processes and waits
// for a specified process to finish.

#define _CRT_RAND_S

#include <windows.h>
#include <process.h>
#include <stdlib.h>
#include <stdio.h>
#include <time.h>

// Macro to get a random integer within a specified range
#define getrandom( min, max ) (( (rand_s (&number), number) % (int)((( max ) + 1 ) - ( min ))) + ( min ))

struct PROCESS
{
   int     nPid;
   char    name[40];
} process[4] = { { 0, "Ann" }, { 0, "Beth" }, { 0, "Carl" }, { 0, "Dave" } };

int main( int argc, char *argv[] )
{
   int termstat, c;
   unsigned int number;

   srand( (unsigned)time( NULL ) );    // Seed randomizer

   // If no arguments, this is the calling process
   if ( argc == 1 )
   {
      // Spawn processes in numeric order
      for ( c = 0; c < 4; c++ ) {
         _flushall();
         process[c].nPid = _spawnl( _P_NOWAIT, argv[0], argv[0],
                                    process[c].name, NULL );
      }

      // Wait for randomly specified process, and respond when done
      c = getrandom( 0, 3 );
      printf( "Come here, %s.\n", process[c].name );
      _cwait( &termstat, process[c].nPid, _WAIT_CHILD );
      printf( "Thank you, %s.\n", process[c].name );

   }
   // If there are arguments, this must be a spawned process
   else
   {
      // Delay for a period that's determined by process number
      Sleep( (argv[1][0] - 'A' + 1) * 1000L );
      printf( "Hi, Dad. It's %s.\n", argv[1] );
   }
}
```

```Output
Hi, Dad. It's Ann.
Come here, Ann.
Thank you, Ann.
Hi, Dad. It's Beth.
Hi, Dad. It's Carl.
Hi, Dad. It's Dave.
```

## <a name="see-also"></a>另请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn, _wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
