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
ms.openlocfilehash: 9e12e64041e38b8fa014815870132a75885014bf
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496569"
---
# <a name="crtthreadtraits-class"></a>CRTThreadTraits 类

此类为 CRT 线程提供创建函数。 如果线程将使用 CRT 函数, 请使用此类。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
class CRTThreadTraits
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CRTThreadTraits::CreateThread](#createthread)|静止调用此函数可创建可以使用 CRT 函数的线程。|

## <a name="remarks"></a>备注

线程特征是为特定类型的线程提供创建函数的类。 创建函数的签名和语义与 Windows [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)函数相同。

线程特征由以下类使用:

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

如果该线程将不使用 CRT 函数, 请改用[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md) 。

## <a name="requirements"></a>要求

**标头:** atlbase.h

##  <a name="createthread"></a>  CRTThreadTraits::CreateThread

调用此函数可创建可以使用 CRT 函数的线程。

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
新线程的安全特性。

*dwStackSize*<br/>
新线程的堆栈大小。

*pfnThreadProc*<br/>
新线程的线程过程。

*pvParam*<br/>
要传递给线程过程的参数。

*dwCreationFlags*<br/>
创建标志 (0 或 CREATE_SUSPENDED)。

*pdwThreadId*<br/>
弄成功接收新创建的线程的线程 ID 的 DWORD 变量的地址。

### <a name="return-value"></a>返回值

返回新创建的线程的句柄, 如果失败, 则返回 NULL。 拨打[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)获取扩展错误信息。

### <a name="remarks"></a>备注

有关此函数的参数的详细信息, 请参阅[CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread) 。

此函数调用[_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)创建线程。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
