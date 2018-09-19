---
title: Win32ThreadTraits 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits
- ATLBASE/ATL::Win32ThreadTraits::CreateThread
dev_langs:
- C++
helpviewer_keywords:
- threading [ATL], Windows threads
- threading [ATL], creation functions
- Win32ThreadTraits class
ms.assetid: 50279c38-eae1-4301-9ea6-97ccea580f3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: baab04880c19cac1e0c291f2b4d8a274dea1c21b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044933"
---
# <a name="win32threadtraits-class"></a>Win32ThreadTraits 类

此类提供一个 Windows 线程的创建函数。 如果该线程不会使用的 CRT 函数，请使用此类。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
class Win32ThreadTraits
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[Win32ThreadTraits::CreateThread](#createthread)|（静态）调用此函数可创建不应使用的 CRT 函数的线程。|

## <a name="remarks"></a>备注

线程特征是线程的为特定类型提供创建函数的类。 创建函数将具有与 Windows 相同的签名和语义[CreateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createthread)函数。

以下类使用线程特征：

- [CThreadPool](../../atl/reference/cthreadpool-class.md)

- [CWorkerThread](../../atl/reference/cworkerthread-class.md)

如果该线程将使用的 CRT 函数，使用[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)相反。

## <a name="requirements"></a>要求

**标头：** atlbase.h

##  <a name="createthread"></a>  Win32ThreadTraits::CreateThread

调用此函数可创建不应使用的 CRT 函数的线程。

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

此函数将调用`CreateThread`创建的线程。

## <a name="see-also"></a>请参阅

[类概述](../../atl/atl-class-overview.md)
