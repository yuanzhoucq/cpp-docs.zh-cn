---
title: _endthread、_endthreadex
ms.date: 11/04/2016
apiname:
- _endthread
- _endthreadex
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
- _endthread
- endthreadex
- _endthreadex
- endthread
helpviewer_keywords:
- _endthread function
- endthread function
- terminating threads
- endthreadex function
- _endthreadex function
- threading [C++], terminating threads
ms.assetid: 18a91f2f-659e-40b4-b266-ec12dcf2abf5
ms.openlocfilehash: 2f54ca9c4cd5e863ca960f1d9c3634b85e7896dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62288818"
---
# <a name="endthread-endthreadex"></a>_endthread、_endthreadex

终止线程;**_endthread**终止创建的线程 **_beginthread**并 **_endthreadex**终止创建的线程 **_beginthreadex**.

## <a name="syntax"></a>语法

```C
void _endthread( void );
void _endthreadex(
   unsigned retval
);
```

### <a name="parameters"></a>参数

*retval*<br/>
线程退出代码。

## <a name="remarks"></a>备注

可以调用 **_endthread**或 **_endthreadex**显式以终止线程; 但是， **_endthread**或者 **_endthreadex**称为自动当线程返回例程作为参数传递给 **_beginthread**或 **_beginthreadex**。 终止线程通过调用**endthread**或 **_endthreadex**有助于确保适当恢复为线程分配的资源。

> [!NOTE]
> 对于与 Libcmt.lib 链接的可执行文件，请不要调用 Win32 [ExitThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-exitthread) API；这将阻止运行时系统回收已分配的资源。 **_endthread**并 **_endthreadex**回收分配的线程资源，然后调用**ExitThread**。

**_endthread**会自动关闭线程句柄。 (此行为不同于 Win32 **ExitThread** API。)因此，当你使用 **_beginthread**并 **_endthread**，不要显式关闭线程句柄通过调用 Win32 [CloseHandle](/windows/desktop/api/handleapi/nf-handleapi-closehandle) API。

与 Win32 **ExitThread** API， **_endthreadex**不会关闭线程句柄。 因此，当你使用 **_beginthreadex**并 **_endthreadex**，您必须通过调用 Win32 关闭线程句柄**CloseHandle** API。

> [!NOTE]
> **_endthread**并 **_endthreadex**导致C++中不会调用线程挂起的析构函数。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_endthread**|\<process.h>|
|**_endthreadex**|\<process.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行库](../../c-runtime-library/crt-library-features.md) 的多线程版本。

## <a name="example"></a>示例

请参阅 [_beginthread](beginthread-beginthreadex.md)示例。

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_beginthread、_beginthreadex](beginthread-beginthreadex.md)<br/>
