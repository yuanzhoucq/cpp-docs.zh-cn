---
title: _cexit、_c_exit
ms.date: 4/2/2020
api_name:
- _c_exit
- _cexit
- _o__cexit
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
- _cexit
- c_exit
- _c_exit
- cexit
helpviewer_keywords:
- cleanup operations during processes
- cexit function
- _c_exit function
- _cexit function
- c_exit function
ms.assetid: f3072045-9924-4b1a-9fef-b0dcd6d12663
ms.openlocfilehash: 9eb856efca054423465aa7d30092edaf83a65eeb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333530"
---
# <a name="_cexit-_c_exit"></a>_cexit、_c_exit

执行清理操作并返回，而不终止进程。

## <a name="syntax"></a>语法

```C
void _cexit( void );
void _c_exit( void );
```

## <a name="remarks"></a>备注

**_cexit**函数按最后一名、先出 （LIFO） 顺序调用由**exit**和 **_onexit**注册的函数。 然后 **_cexit**刷新所有 I/O 缓冲区，并在返回之前关闭所有打开的流。 **_c_exit**与 **_exit**相同，但返回到调用进程，而不处理**exit**或 **_onexit**或刷新流缓冲区。 **退出****、_exit、_cexit**和_c_exit **_cexit**的行为显示在下表 **_c_exit**中。

|函数|行为|
|--------------|--------------|
|**exit**|执行完整的 C 库终止过程，终止进程，并使用提供的状态代码退出。|
|**_exit**|执行快速的 C 库终止过程，终止进程，并使用提供的状态代码退出。|
|**_cexit**|执行完整的 C 库终止过程并返回给调用方，但不中止进程。|
|**_c_exit**|执行快速的 C 库终止过程并返回给调用方，但不中止进程。|

调用 **_cexit**或 **_c_exit**函数时，不会调用调用时存在的任何临时或自动对象的析构函数。 自动对象是在对象未声明为静态的函数中进行定义的对象。 临时对象是由编译器创建的对象。 要在调用 **_cexit**或 **_c_exit**之前销毁自动对象，请显式调用该对象的析构函数，如下所示：

```cpp
myObject.myClass::~myClass( );
```

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_cexit**|\<process.h>|
|**_c_exit**|\<process.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[中止](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec、_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
