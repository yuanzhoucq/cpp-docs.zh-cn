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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: a1c0eeaa6d66e91b913ce7940d37409fc4f6ac29
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909670"
---
# <a name="exit-_exit-_exit"></a>exit, _Exit, _exit

终止调用进程。 **Exit**函数会在清除后终止它;**_exit** ， **_Exit**立即终止它。

> [!NOTE]
> 不要使用此方法关闭通用 Windows 平台（UWP）应用程序，除非在测试或调试方案中。 根据[Microsoft Store 策略](/legal/windows/agreements/store-policies)，不允许以编程方式或 UI 方式关闭应用商店应用。 有关详细信息，请参阅[UWP 应用生命周期](/windows/uwp/launch-resume/app-lifecycle)。 有关 Windows 10 应用的详细信息，请参阅 [Windows 10 应用的操作方法指南](https://developer.microsoft.com/windows/apps)。

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

*status*<br/>
退出状态代码。

## <a name="remarks"></a>备注

**Exit**、 **_Exit**和 **_exit**函数终止调用进程。 **Exit**函数调用线程本地对象的析构函数，然后调用（后进先出（LIFO）顺序） **atexit**和 **_onexit**注册的函数，然后在终止进程之前刷新所有文件缓冲区。 **_Exit**和 **_exit**函数终止进程，而无需销毁线程本地对象或处理**atexit**或 **_onexit**函数，并且无需刷新流缓冲区。

尽管**exit**、 **_Exit**和 **_exit**调用不返回值，但是在进程退出后，*状态*中的值可用于主机环境或等待调用进程（如果存在）。 通常，调用方将*状态值*设置为0，指示正常退出，或设置为其他值来指示错误。 *Status*值可用于操作系统批处理命令**ERRORLEVEL** ，它由以下两个常量之一表示： **EXIT_SUCCESS**，它表示值0，或者**EXIT_FAILURE**，该值为1。

**Exit**、 **_Exit**、 **_exit**、 **quick_exit**、 **_cexit**和 **_c_exit**函数的行为如下所示。

|函数|说明|
|--------------|-----------------|
|**exit**|执行完整的 C 库终止过程，终止进程，并向主机环境提供提供的状态代码。|
|**_Exit**|执行最少的 C 库终止过程，终止进程，并向主机环境提供提供的状态代码。|
|**_exit**|执行最少的 C 库终止过程，终止进程，并向主机环境提供提供的状态代码。|
|**quick_exit**|执行快速的 C 库终止过程，终止进程，并向主机环境提供提供的状态代码。|
|**_cexit**|执行完整的 C 库终止过程并返回给调用方。 不终止进程。|
|**_c_exit**|执行最少的 C 库终止过程并返回给调用方。 不终止进程。|

调用**exit**、 **_Exit**或 **_exit**函数时，不会调用在调用时存在的任何临时或自动对象的析构函数。 自动对象是在函数中定义的非静态本地对象。 临时对象是由编译器创建的对象，例如函数调用返回的值。 若要在调用**exit**、 **_Exit**或 **_exit**之前销毁自动对象，请显式调用该对象的析构函数，如下所示：

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

不要使用**DLL_PROCESS_ATTACH**从**DllMain**调用**exit** 。 若要退出**DLLMain**函数，请从**DLL_PROCESS_ATTACH**返回**FALSE** 。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**退出**、 **_Exit**、 **_exit**|\<process.h> 或 \<stdlib.h>|

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
