---
title: CNoWorkerThread 类
ms.date: 11/04/2016
f1_keywords:
- CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread::AddHandle
- ATLUTIL/ATL::CNoWorkerThread::AddTimer
- ATLUTIL/ATL::CNoWorkerThread::GetThreadHandle
- ATLUTIL/ATL::CNoWorkerThread::GetThreadId
- ATLUTIL/ATL::CNoWorkerThread::Initialize
- ATLUTIL/ATL::CNoWorkerThread::RemoveHandle
- ATLUTIL/ATL::CNoWorkerThread::Shutdown
helpviewer_keywords:
- CNoWorkerThread class
ms.assetid: 29f06bae-b658-4aac-9c14-331e996d25d1
ms.openlocfilehash: fcd103283738ce7d573faa2fb1025ee2af642021
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258489"
---
# <a name="cnoworkerthread-class"></a>CNoWorkerThread 类

使用此类的自变量作为`MonitorClass`到你想要禁用动态缓存维护的缓存类模板参数。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
class CNoWorkerThread
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CNoWorkerThread::AddHandle](#addhandle)|非功能上的等同于[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。|
|[CNoWorkerThread::AddTimer](#addtimer)|非功能上的等同于[CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer)。|
|[CNoWorkerThread::GetThreadHandle](#getthreadhandle)|非功能上的等同于[CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle)。|
|[CNoWorkerThread::GetThreadId](#getthreadid)|非功能上的等同于[CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid)。|
|[CNoWorkerThread::Initialize](#initialize)|非功能上的等同于[CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize)。|
|[CNoWorkerThread::RemoveHandle](#removehandle)|非功能上的等同于[CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle)。|
|[CNoWorkerThread::Shutdown](#shutdown)|非功能上的等同于[CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown)。|

## <a name="remarks"></a>备注

此类提供相同的公共接口[CWorkerThread](../../atl/reference/cworkerthread-class.md)。 此接口应由提供`MonitorClass`缓存类模板参数。

此类中的方法的实现不执行任何操作。 始终返回一个 HRESULT，方法返回 S_OK，并始终返回的句柄或线程 ID 的方法返回 0。

## <a name="requirements"></a>要求

**标头：** atlutil.h

##  <a name="addhandle"></a>  CNoWorkerThread::AddHandle

非功能上的等同于[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。

```
HRESULT AddHandle(HANDLE /* hObject */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */) throw();
```

### <a name="return-value"></a>返回值

始终返回 S_OK。

### <a name="remarks"></a>备注

提供此类的实现没有任何影响。

##  <a name="addtimer"></a>  CNoWorkerThread::AddTimer

非功能上的等同于[CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer)。

```
HRESULT AddTimer(DWORD /* dwInterval */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */,
    HANDLE* /* phTimer */) throw();
```

### <a name="return-value"></a>返回值

始终返回 S_OK。

### <a name="remarks"></a>备注

提供此类的实现没有任何影响。

##  <a name="getthreadhandle"></a>  CNoWorkerThread::GetThreadHandle

非功能上的等同于[CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle)。

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>返回值

始终返回 NULL。

### <a name="remarks"></a>备注

提供此类的实现没有任何影响。

##  <a name="getthreadid"></a>  CNoWorkerThread::GetThreadId

非功能上的等同于[CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid)。

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>返回值

始终返回 0。

### <a name="remarks"></a>备注

提供此类的实现没有任何影响。

##  <a name="initialize"></a>  CNoWorkerThread::Initialize

非功能上的等同于[CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize)。

```
HRESULT Initialize() throw();
```

### <a name="return-value"></a>返回值

始终返回 S_OK。

### <a name="remarks"></a>备注

提供此类的实现没有任何影响。

##  <a name="removehandle"></a>  CNoWorkerThread::RemoveHandle

非功能上的等同于[CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle)。

```
HRESULT RemoveHandle(HANDLE /* hObject */) throw();
```

### <a name="return-value"></a>返回值

始终返回 S_OK。

### <a name="remarks"></a>备注

提供此类的实现没有任何影响。

##  <a name="shutdown"></a>  CNoWorkerThread::Shutdown

非功能上的等同于[CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown)。

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="return-value"></a>返回值

始终返回 S_OK。

### <a name="remarks"></a>备注

提供此类的实现没有任何影响。
