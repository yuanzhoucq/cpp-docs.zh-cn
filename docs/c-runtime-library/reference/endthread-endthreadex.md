---
title: _endthread、_endthreadex
ms.date: 11/04/2016
api_name:
- _endthread
- _endthreadex
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: c9dd4a49e534e8fa3e0f5ac735faccb4b0f65af5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937735"
---
# <a name="_endthread-_endthreadex"></a>_endthread、_endthreadex

终止线程; **_endthread**终止由 **_beginthread**创建的线程，并 **_endthreadex**终止由 **_beginthreadex**创建的线程。

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

可以显式调用 **_endthread**或 **_endthreadex**以终止线程;但是，当线程从作为参数传递给 **_beginthread**或 **_beginthreadex**的例程中返回时，会自动调用 **_endthread**或 **_endthreadex** 。 使用对**endthread**或 **_endthreadex**的调用来终止线程有助于确保正确恢复为线程分配的资源。

> [!NOTE]
> 对于与 Libcmt.lib 链接的可执行文件，请不要调用 Win32 [ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread) API；这将阻止运行时系统回收已分配的资源。 **_endthread**和 **_endthreadex**回收分配的线程资源，然后调用**ExitThread**。

**_endthread**会自动关闭线程句柄。 （此行为与 Win32 **ExitThread** API 不同。）因此，使用 **_beginthread**和 **_endthread**时，不要通过调用 Win32 [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle) API 来显式关闭线程句柄。

与 Win32 **ExitThread** API 一样， **_endthreadex**不会关闭线程句柄。 因此，在使用 **_beginthreadex**和 **_endthreadex**时，必须通过调用 Win32 **CloseHandle** API 来关闭线程句柄。

> [!NOTE]
> **_endthread**和 **_endthreadex**导致C++不会调用线程中的析构函数。

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
