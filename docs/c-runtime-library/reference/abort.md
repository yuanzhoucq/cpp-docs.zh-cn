---
title: abort
ms.date: 4/2/2020
api_name:
- abort
- _o_abort
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- Abort
helpviewer_keywords:
- aborting current process
- abort function
- processes, aborting
ms.openlocfilehash: 1f70f54783ce6f6d28fdda028af4fd5a205aeb0b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350917"
---
# <a name="abort"></a>abort

中止当前进程，并返回错误代码。

> [!NOTE]
> 除非在测试或调试方案中，否则不要使用此方法关闭 Microsoft 应用商店应用或通用 Windows 平台 （UWP） 应用。 根据[Microsoft 应用商店策略](/legal/windows/agreements/store-policies)，不允许以编程或 UI 方式关闭应用商店应用。 有关详细信息，请参阅[UWP 应用生命周期](/windows/uwp/launch-resume/app-lifecycle)。

## <a name="syntax"></a>语法

```C
void abort( void );
```

## <a name="return-value"></a>返回值

**中止**不会将控制权返回到调用进程。 默认情况下，它检查中止信号处理程序，如果设置了 `SIGABRT`，则对其进行提升。 然后**中止**终止当前进程，并将退出代码返回给父进程。

## <a name="remarks"></a>备注

**微软特定**

默认情况下，当使用调试运行时库生成应用时，**中止**例程会在引发之前`SIGABRT`显示一条错误消息。 对于在控制台模式下运行的控制台应用程序，该消息发送到 `STDERR`。 以窗口模式运行的 Windows 桌面应用程序和控制台应用程序在消息框中显示此消息。 要取消该消息，请使用 [_set_abort_behavior](set-abort-behavior.md) 来清除 `_WRITE_ABORT_MSG` 标志。 所显示的消息取决于使用的运行时环境的版本。 对于使用最新版本的 Visual C++构建的应用程序，该消息类似于：

> R6010 - 中止（）已调用

在以前版本的 C 运行时库中，该消息显示为：

> This application has requested the Runtime to terminate it in an unusual way. Please contact the application's support team for more information.

当程序在调试模式下编译时，消息框显示“**中止**”、“**重试**”或“**忽略**”选项。 如果用户选择“**中止**”，该程序立即终止并返回退出代码 3。 如果用户选择“**重试**”，将调用调试器进行实时调试（如果可用）。 如果用户选择 **"忽略"，****中止**将继续正常处理。

在零售和调试版本中，**中止**然后检查是否设置了中止信号处理程序。 如果设置了非默认信号处理程序，**请中止**调用`raise(SIGABRT)`。 使用 [signal](signal.md) 函数将中止信号处理程序函数与 `SIGABRT` 信号相关联。 你可以执行自定义操作，例如清除资源或日志信息，并在处理程序函数中使用自己的错误代码终止应用程序。 如果未定义自定义信号处理程序，**则中止**不会引发`SIGABRT`信号。

默认情况下，在桌面或控制台应用的非调试版本中，**中止**然后调用 Windows 错误报告服务机制（以前称为 Watson 博士）向 Microsoft 报告故障。 调用 `_set_abort_behavior` 并设置或过滤 `_CALL_REPORTFAULT` 标志可启用或禁用此行为。 设置该标志时，Windows 将显示一个消息框，其中包含类似“出现了一个问题，导致程序无法正常工作”的文本。 用户可以选择使用“**调试**”按钮调用调试器，或选择“**关闭程序**”按钮以终止带有操作系统定义的错误代码的应用程序。

如果未调用 Windows 错误报告处理程序，则**中止**[调用_exit](exit-exit-exit.md)终止使用退出代码 3 的进程，并将控制权返回到父进程或操作系统。 `_exit` 不刷新流缓冲区或执行 `atexit`/`_onexit` 处理。

有关 CRT 调试的详细信息，请参阅 [CRT 调试技术](/visualstudio/debugger/crt-debugging-techniques)。

**结束 Microsoft 专用**

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**中止**|\<process.h> 或 \<stdlib.h>|

## <a name="example"></a>示例

下面的程序尝试打开一个文件，如果该尝试失败，则中止。

```C
// crt_abort.c
// compile with: /TC
// This program demonstrates the use of
// the abort function by attempting to open a file
// and aborts if the attempt fails.

#include  <stdio.h>
#include  <stdlib.h>

int main( void )
{
    FILE    *stream = NULL;
    errno_t err = 0;

    err = fopen_s(&stream, "NOSUCHF.ILE", "r" );
    if ((err != 0) || (stream == NULL))
    {
        perror( "File could not be opened" );
        abort();
    }
    else
    {
        fclose( stream );
    }
}
```

```Output
File could not be opened: No such file or directory
```

## <a name="see-also"></a>另请参阅

[使用 abort](../../cpp/using-abort.md)<br/>
[abort 函数](../../c-language/abort-function-c.md)<br/>
[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec、_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[提高](raise.md)<br/>
[信号](signal.md)<br/>
[_spawn, _wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
[_set_abort_behavior](set-abort-behavior.md)
