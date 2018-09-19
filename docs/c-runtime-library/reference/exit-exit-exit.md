---
title: exit、_Exit、_exit | Microsoft 文档
ms.custom: ''
ms.date: 1/02/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _exit
- exit
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- Exit
- _exit
- process/exit
- process/_Exit
- stdlib/exit
- stdlib/_Exit
dev_langs:
- C++
helpviewer_keywords:
- exit function
- _exit function
- processes, terminating
- function calls, terminating
- process termination, calling
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d26cc39039b95b8c12e429d333918e83628b2619
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110599"
---
# <a name="exit-exit-exit"></a>exit, _Exit, _exit

终止调用进程。 **退出**函数将终止该进程后清除;**_exit**并 **_Exit**立即终止。

> [!NOTE]
> 不使用此方法关闭通用 Windows 平台 (UWP) 应用，除测试或调试方案中。 以编程或 UI 方式关闭应用商店应用程序不允许根据[Microsoft Store 策略](/legal/windows/agreements/store-policies)。 有关详细信息，请参阅[UWP 应用程序生命周期](/windows/uwp/launch-resume/app-lifecycle)。 有关 Windows 10 应用的详细信息，请参阅 [Windows 10 应用的操作方法指南](https://developer.microsoft.com/en-us/windows/apps)。

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

**退出**， **_Exit**并 **_exit**函数会终止调用进程。 **退出**函数会调用析构函数的线程本地对象，然后调用-先出 (LIFO) 顺序-由注册的函数**atexit**和 **_onexit**，它会终止进程之前刷新所有文件缓冲区。 **_Exit**并 **_exit**函数而无需销毁线程本地对象或处理会终止进程**atexit**或 **_onexit**函数，且无需刷新流缓冲区。

尽管**退出**， **_Exit**并 **_exit**调用不会返回一个值，在值*状态*提供给主机环境或者，如果存在，在进程退出后等待调用进程。 通常情况下，调用方集*状态*值为 0 来指示正常退出，或为其他值以指示错误。 *状态*值是可用于操作系统批处理命令**ERRORLEVEL** ，并且由两个常量之一： **EXIT_SUCCESS**，后者表示值为 0，或**EXIT_FAILURE**，它表示的值为 1。

**退出**， **_Exit**， **_exit**， **quick_exit**， **_cexit**，和 **_c_exit**函数的行为，如下所示。

|函数|描述|
|--------------|-----------------|
|**exit**|执行完整的 C 库终止过程，终止进程，并向主机环境提供提供的状态代码。|
|**_Exit**|执行最少的 C 库终止过程，终止进程，并向主机环境提供提供的状态代码。|
|**_exit**|执行最少的 C 库终止过程，终止进程，并向主机环境提供提供的状态代码。|
|**quick_exit**|执行快速的 C 库终止过程，终止进程，并向主机环境提供提供的状态代码。|
|**_cexit**|执行完整的 C 库终止过程并返回给调用方。 不终止进程。|
|**_c_exit**|执行最少的 C 库终止过程并返回给调用方。 不终止进程。|

当您调用**退出**， **_Exit**或 **_exit**函数，不会调用在调用时存在的任何临时或自动对象的析构函数。 自动对象是在函数中定义的非静态本地对象。 临时对象是由编译器，如函数调用所返回的值创建的对象。 若要在调用之前销毁自动对象**退出**， **_Exit**，或 **_exit**，请显式调用析构函数的对象，如下所示：

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

不要使用**DLL_PROCESS_ATTACH**调用**退出**从**DllMain**。 若要退出**DLLMain**函数，返回**FALSE**从**DLL_PROCESS_ATTACH**。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**退出**， **_Exit**， **_exit**|\<process.h> 或 \<stdlib.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_cexit、_c_exit](cexit-c-exit.md)<br/>
[_exec、_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
[quick_exit](quick-exit1.md)<br/>
[_spawn、_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
