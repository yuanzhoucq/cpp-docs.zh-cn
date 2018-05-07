---
title: _cexit、_c_exit | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _c_exit
- _cexit
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
- _cexit
- c_exit
- _c_exit
- cexit
dev_langs:
- C++
helpviewer_keywords:
- cleanup operations during processes
- cexit function
- _c_exit function
- _cexit function
- c_exit function
ms.assetid: f3072045-9924-4b1a-9fef-b0dcd6d12663
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b0840ccec85d46a13984b65ebe99e53b968bedeb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="cexit-cexit"></a>_cexit、_c_exit

执行清理操作并返回，而不终止进程。

## <a name="syntax"></a>语法

```C
void _cexit( void );
void _c_exit( void );
```

## <a name="remarks"></a>备注

**_Cexit**函数调用，在最后一个单元中、 先进先出 (LIFO) 顺序、 注册的函数**atexit**和 **_onexit**。 然后 **_cexit**刷新所有 I/O 缓冲区，并在返回之前关闭所有打开的流。 **_c_exit**相同 **_exit**但返回到调用进程而不处理**atexit**或 **_onexit**或刷新流缓冲区。 行为**退出**， **_exit**， **_cexit**，和 **_c_exit**以下表所示。

|函数|行为|
|--------------|--------------|
|**exit**|执行完整的 C 库终止过程，终止进程，并使用提供的状态代码退出。|
|**_exit**|执行快速的 C 库终止过程，终止进程，并使用提供的状态代码退出。|
|**_cexit**|执行完整的 C 库终止过程并返回给调用方，但不中止进程。|
|**_c_exit**|执行快速的 C 库终止过程并返回给调用方，但不中止进程。|

当调用 **_cexit**或 **_c_exit**不调用的函数，在调用时存在的任何临时或自动对象的析构函数。 自动对象是在对象未声明为静态的函数中进行定义的对象。 临时对象是由编译器创建的对象。 若要销毁自动对象之前调用 **_cexit**或 **_c_exit**，请显式调用析构函数的对象，如下所示：

```cpp
myObject.myClass::~myClass( );
```

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_cexit**|\<process.h>|
|**_c_exit**|\<process.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec、_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
[_spawn、_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
