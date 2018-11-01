---
title: _cwait
ms.date: 11/04/2016
apiname:
- _cwait
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
- api-ms-win-crt-process-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _cwait
helpviewer_keywords:
- cwait function
- _cwait function
ms.assetid: d9b596b5-45f4-4e03-9896-3f383cb922b8
ms.openlocfilehash: f7a49497ac71ec15261e1215bd2bbed2e49f42ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50489617"
---
# <a name="cwait"></a>_cwait

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

*termstat*<br/>
指向将存储指定进程的结果代码的位置，缓冲区的指针或**NULL**。

*procHandle*<br/>
要等待的进程的句柄 (即之前, 必须终止的进程 **_cwait**可以返回)。

*action*<br/>
NULL： 忽略由 Windows 操作系统应用程序;对于其他应用程序： 若要执行的操作代码*procHandle*。

## <a name="return-value"></a>返回值

已成功完成指定的进程后，返回指定的进程的句柄，并设置*termstat*到指定的进程返回的结果代码。 否则为返回-1，并设置**errno** ，如下所示。

|“值”|描述|
|-----------|-----------------|
|**ECHILD**|指定的进程不存在， *procHandle*无效，或在调用[GetExitCodeProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess)或[WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) API 失败。|
|**EINVAL**|*操作*无效。|

有关这些代码及其他返回代码的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Cwait**函数等待提供的指定进程的进程 ID 终止*procHandle*。 值*procHandle*传递给 **_cwait**应通过调用返回的值[_spawn](../../c-runtime-library/spawn-wspawn-functions.md)创建指定的进程的函数。 如果进程 ID 终止之前 **_cwait**调用时， **_cwait**立即返回。 **_cwait**任何进程可用于等待任何其他已知的进程，为其有效的句柄 (*procHandle*) 存在。

*termstat*指向将存储指定进程的返回代码的缓冲区。 值*termstat*指示是否指定正常终止了进程通过调用 Windows [ExitProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-exitprocess) API。 **ExitProcess**如果指定的进程调用在内部调用**退出**或 **_exit**，从返回**主要**，或到达末尾**主要**. 详细了解通过传递的值*termstat*，请参阅[GetExitCodeProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess)。 如果 **_cwait**通过使用调用**NULL**值*termstat*，不存储指定进程的返回代码。

*操作*由 Windows 操作系统忽略参数，因为在这些环境中未实现父-子关系。

除非*procHandle*为-1 或-2 （句柄的当前进程或线程），将关闭此句柄。 因此，在这种情况下，请不要使用返回的句柄。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_cwait**|\<process.h>|\<errno.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn、_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
