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
ms.openlocfilehash: a7cfddc64e8c1b4e192e718d05812e385fbe08ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331017"
---
# <a name="crtthreadtraits-class"></a>CRTThreadTraits 类

此类提供 CRT 线程的创建函数。 如果线程将使用 CRT 函数，请使用此类。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CRTThreadTraits
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CRTThreadtraits：创建线程](#createthread)|（静态）调用此函数以创建可以使用 CRT 函数的线程。|

## <a name="remarks"></a>备注

线程特征是为特定类型的线程提供创建函数的类。 创建函数具有与 Windows [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)函数相同的签名和语义。

线程特征由以下类使用：

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

如果线程不使用 CRT 函数，请使用[Win32ThreadTraits。](../../atl/reference/win32threadtraits-class.md)

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="crtthreadtraitscreatethread"></a><a name="createthread"></a>CRTThreadtraits：创建线程

调用此函数以创建可以使用 CRT 函数的线程。

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
新线程的堆栈大小。

*普芬线程普罗克*<br/>
新线程的线程过程。

*pvParam*<br/>
要传递给线程过程的参数。

*dw创造标志*<br/>
创建标志（0 或CREATE_SUSPENDED）。

*pdwThreadId*<br/>
[出]DWORD 变量的地址，在成功时，接收新创建的线程的线程 ID。

### <a name="return-value"></a>返回值

将句柄返回到新创建的线程或失败时为 NULL。 调用[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)获取扩展的错误信息。

### <a name="remarks"></a>备注

有关此函数的参数的详细信息，请参阅[CreateThread。](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)

此函数调用[_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)以创建线程。

## <a name="see-also"></a>另请参阅

[类概述](../../atl/atl-class-overview.md)
