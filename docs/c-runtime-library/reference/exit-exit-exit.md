---
title: exit, _Exit, _exit
ms.date: 4/2/2020
api_name:
- _exit
- exit
- _o__exit
- _o_exit
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
- Exit
- _exit
- process/exit
- process/_Exit
- stdlib/exit
- stdlib/_Exit
helpviewer_keywords:
- exit function
- _exit function
- processes, terminating
- function calls, terminating
- process termination, calling
ms.openlocfilehash: 5bdb5ff5c8309e03a49f9518f65a45d5757e9bfa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347638"
---
# <a name="exit-_exit-_exit"></a>exit, _Exit, _exit

终止调用进程。 **退出**函数在清理后终止它;**_exit，_Exit**立即终止。 **_Exit**

> [!NOTE]
> 除非在测试或调试方案中，否则不要使用此方法关闭通用 Windows 平台 （UWP） 应用。 根据[Microsoft 应用商店策略](/legal/windows/agreements/store-policies)，不允许以编程或 UI 方式关闭应用商店应用。 有关详细信息，请参阅[UWP 应用程序生命周期](/windows/uwp/launch-resume/app-lifecycle)。 有关 Windows 10 应用的详细信息，请参阅 [Windows 10 应用的操作方法指南](https://developer.microsoft.com/windows/apps)。

## <a name="syntax"></a>语法

```C
void exit(
   int const status
);
void _Exit(
   int const status
);
void _exit(
   int const status
);
```

### <a name="parameters"></a>参数

*状态*<br/>
退出状态代码。

## <a name="remarks"></a>备注

**退出****、_Exit**和 **_exit**函数终止调用过程。 **退出**函数调用线程本地对象的析构函数，然后调用 -以先出后 （LIFO） 顺序调用 - 通过**atexit**和 **_onexit**注册的函数，然后在它终止进程之前刷新所有文件缓冲区。 **_Exit**和 **_exit**函数在不销毁线程本地对象或处理**exit**或 **_onexit**函数的情况下终止进程，并且不刷新流缓冲区。

尽管**退出****、_Exit**和 **_exit**调用不会返回值，但*状态*值在进程退出后将提供给主机环境或等待调用进程（如果存在）。 通常，调用方将*状态*值设置为 0 以指示正常退出，或将另一些值设置以指示错误。 *状态*值可用于操作系统批处理命令**ERRORLEVEL，** 由两个常量之一表示 **：EXIT_SUCCESS**，表示值 0，或表示值 1 的**EXIT_FAILURE。**

**出口**、_Exit、_exit、quick_exit、_cexit **_cexit**和 **_c_exit**功能如下。 **_Exit** **_exit** **quick_exit**

|函数|说明|
|--------------|-----------------|
|**exit**|执行完整的 C 库终止过程，终止进程，并向主机环境提供提供的状态代码。|
|**_Exit**|执行最少的 C 库终止过程，终止进程，并向主机环境提供提供的状态代码。|
|**_exit**|执行最少的 C 库终止过程，终止进程，并向主机环境提供提供的状态代码。|
|**quick_exit**|执行快速的 C 库终止过程，终止进程，并向主机环境提供提供的状态代码。|
|**_cexit**|执行完整的 C 库终止过程并返回给调用方。 不终止进程。|
|**_c_exit**|执行最少的 C 库终止过程并返回给调用方。 不终止进程。|

调用**出口****、_Exit**或 **_exit**函数时，不会调用调用调用时存在的任何临时或自动对象的析构函数。 自动对象是在函数中定义的非静态局部对象。 临时对象是由编译器创建的对象，例如函数调用返回的值。 要在调用**退出****、_Exit**或 **_exit**之前销毁自动对象，请显式调用对象的析构函数，如下所示：

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

请勿使用**DLL_PROCESS_ATTACH**调用**DllMain****的退出**。 要退出**DLLMain**函数，从**DLL_PROCESS_ATTACH**返回**FALSE。**

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**出口**， **_Exit**， **_exit**|\<process.h> 或 \<stdlib.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_exit.c
// This program returns an exit code of 1. The
// error code could be tested in a batch file.

#include <stdlib.h>

int main( void )
{
   exit( 1 );
}
```

## <a name="see-also"></a>另请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[中止](abort.md)<br/>
[atexit](atexit.md)<br/>
[_cexit、_c_exit](cexit-c-exit.md)<br/>
[_exec、_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
[quick_exit](quick-exit1.md)<br/>
[_spawn, _wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
