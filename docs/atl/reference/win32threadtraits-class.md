---
title: Win32ThreadTraits 类
ms.date: 11/04/2016
f1_keywords:
- Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits::CreateThread
helpviewer_keywords:
- threading [ATL], Windows threads
- threading [ATL], creation functions
- Win32ThreadTraits class
ms.assetid: 50279c38-eae1-4301-9ea6-97ccea580f3e
ms.openlocfilehash: d086a42f5dcdf005d10c8853776da66b691a8e11
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495476"
---
# <a name="win32threadtraits-class"></a>Win32ThreadTraits 类

此类提供 Windows 线程的创建功能。 如果线程不使用 CRT 函数, 请使用此类。

> [!IMPORTANT]
>  此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
class Win32ThreadTraits
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[Win32ThreadTraits::CreateThread](#createthread)|静止调用此函数可创建不应使用 CRT 函数的线程。|

## <a name="remarks"></a>备注

线程特征是为特定类型的线程提供创建函数的类。 创建函数的签名和语义与 Windows [CreateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)函数相同。

线程特征由以下类使用:

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

如果该线程将使用 CRT 函数, 请改用[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) 。

## <a name="requirements"></a>要求

**标头:** atlbase.h

##  <a name="createthread"></a>Win32ThreadTraits:: CreateThread

调用此函数可创建不应使用 CRT 函数的线程。

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

此函数调用`CreateThread`以创建线程。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
