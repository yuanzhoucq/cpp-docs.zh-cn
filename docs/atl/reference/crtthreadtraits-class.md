---
title: CRTThreadTraits 类
ms.date: 11/04/2016
f1_keywords:
- CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits
- ATLBASE/ATL::CRTThreadTraits::CreateThread
helpviewer_keywords:
- CRTThreadTraits class
- threading [ATL], creation functions
- threading [ATL], CRT threads
ms.assetid: eb6e20b0-c2aa-4170-8e34-aaeeacc86343
ms.openlocfilehash: 1e54b4db2605c3006697d0a26d34066de666f0fc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641943"
---
# <a name="crtthreadtraits-class"></a>CRTThreadTraits 类

此类提供 CRT 线程的创建函数。 如果该线程将使用的 CRT 函数，请使用此类。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
class CRTThreadTraits
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CRTThreadTraits::CreateThread](#createthread)|（静态）调用此函数可创建可以使用的 CRT 函数的线程。|

## <a name="remarks"></a>备注

线程特征是线程的为特定类型提供创建函数的类。 创建函数将具有与 Windows 相同的签名和语义[CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread)函数。

以下类使用线程特征：

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

如果不将使用线程的 CRT 函数，使用[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)相反。

## <a name="requirements"></a>要求

**标头：** atlbase.h

##  <a name="createthread"></a>  CRTThreadTraits::CreateThread

调用此函数可创建可以使用的 CRT 函数的线程。

```
static HANDLE CreateThread(
    LPSECURITY_ATTRIBUTES lpsa,
    DWORD dwStackSize,
    LPTHREAD_START_ROUTINE pfnThreadProc,
    void* pvParam,
    DWORD dwCreationFlags,
    DWORD* pdwThreadId) throw();
```

### <a name="parameters"></a>参数

*lpsa*<br/>
新线程的安全属性。

*dwStackSize*<br/>
新线程堆栈大小。

*pfnThreadProc*<br/>
新线程的线程过程。

*pvParam*<br/>
要传递给线程过程的参数。

*dwCreationFlags*<br/>
创建标记 （0 或 CREATE_SUSPENDED）。

*pdwThreadId*<br/>
[out]成功后，接收新创建的线程的线程 ID 的 DWORD 变量的地址。

### <a name="return-value"></a>返回值

在失败时返回的新创建的线程或为 NULL 的图柄。 调用[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)若要获得扩展错误信息。

### <a name="remarks"></a>备注

请参阅[CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread)有关此函数的参数的详细信息。

此函数将调用[_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)创建的线程。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
