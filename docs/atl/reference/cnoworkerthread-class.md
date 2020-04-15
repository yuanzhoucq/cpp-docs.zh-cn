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
ms.openlocfilehash: 90056e648a53218ac06083d43ca34870e1ca72fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326712"
---
# <a name="cnoworkerthread-class"></a>CNoWorkerThread 类

如果要禁用动态缓存维护，`MonitorClass`请使用此类作为模板参数的参数来缓存类。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CNoWorkerThread
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CNoWorker 线程：：添加句柄](#addhandle)|CWorkerThread 的非功能等效项[：addHandle](../../atl/reference/cworkerthread-class.md#addhandle)。|
|[CNoWorkerThread：：添加计时器](#addtimer)|CWorkerThread 的非功能等效项[：addTimer](../../atl/reference/cworkerthread-class.md#addtimer)。|
|[CNoWorker线程：获取线程句柄](#getthreadhandle)|CWorkerThread 的非功能等效项[：获取线程句柄](../../atl/reference/cworkerthread-class.md#getthreadhandle)。|
|[CNoWorker 线程：获取线程 Id](#getthreadid)|CWorkerThread 的非功能等效项[：getThreadId](../../atl/reference/cworkerthread-class.md#getthreadid)。|
|[CNoWorkerThread：初始化](#initialize)|CWorkerThread 的非功能等效项[：：初始化](../../atl/reference/cworkerthread-class.md#initialize)。|
|[CNoWorker 线程：：删除句柄](#removehandle)|CWorkerThread 的非功能等效项[：：删除句柄](../../atl/reference/cworkerthread-class.md#removehandle)。|
|[CNoWorker 线程：：关闭](#shutdown)|CWorkerThread 的非功能等效项[：：关机](../../atl/reference/cworkerthread-class.md#shutdown)。|

## <a name="remarks"></a>备注

此类提供与[CWorkerThread](../../atl/reference/cworkerthread-class.md)相同的公共接口。 此接口预期由`MonitorClass`模板参数提供给缓存类。

类中的方法实现不执行任何操作。 返回 HRESULT 的方法始终返回S_OK，返回 HANDLE 或线程 ID 的方法始终返回 0。

## <a name="requirements"></a>要求

**标题：** atlutil.h

## <a name="cnoworkerthreadaddhandle"></a><a name="addhandle"></a>CNoWorker 线程：：添加句柄

CWorkerThread 的非功能等效项[：addHandle](../../atl/reference/cworkerthread-class.md#addhandle)。

```
HRESULT AddHandle(HANDLE /* hObject */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */) throw();
```

### <a name="return-value"></a>返回值

始终返回S_OK。

### <a name="remarks"></a>备注

此类提供的实现不执行任何操作。

## <a name="cnoworkerthreadaddtimer"></a><a name="addtimer"></a>CNoWorkerThread：：添加计时器

CWorkerThread 的非功能等效项[：addTimer](../../atl/reference/cworkerthread-class.md#addtimer)。

```
HRESULT AddTimer(DWORD /* dwInterval */,
    IWorkerThreadClient* /* pClient */,
    DWORD_PTR /* dwParam */,
    HANDLE* /* phTimer */) throw();
```

### <a name="return-value"></a>返回值

始终返回S_OK。

### <a name="remarks"></a>备注

此类提供的实现不执行任何操作。

## <a name="cnoworkerthreadgetthreadhandle"></a><a name="getthreadhandle"></a>CNoWorker线程：获取线程句柄

CWorkerThread 的非功能等效项[：获取线程句柄](../../atl/reference/cworkerthread-class.md#getthreadhandle)。

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>返回值

始终返回 NULL。

### <a name="remarks"></a>备注

此类提供的实现不执行任何操作。

## <a name="cnoworkerthreadgetthreadid"></a><a name="getthreadid"></a>CNoWorker 线程：获取线程 Id

CWorkerThread 的非功能等效项[：getThreadId](../../atl/reference/cworkerthread-class.md#getthreadid)。

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>返回值

始终返回 0。

### <a name="remarks"></a>备注

此类提供的实现不执行任何操作。

## <a name="cnoworkerthreadinitialize"></a><a name="initialize"></a>CNoWorkerThread：初始化

CWorkerThread 的非功能等效项[：：初始化](../../atl/reference/cworkerthread-class.md#initialize)。

```
HRESULT Initialize() throw();
```

### <a name="return-value"></a>返回值

始终返回S_OK。

### <a name="remarks"></a>备注

此类提供的实现不执行任何操作。

## <a name="cnoworkerthreadremovehandle"></a><a name="removehandle"></a>CNoWorker 线程：：删除句柄

CWorkerThread 的非功能等效项[：：删除句柄](../../atl/reference/cworkerthread-class.md#removehandle)。

```
HRESULT RemoveHandle(HANDLE /* hObject */) throw();
```

### <a name="return-value"></a>返回值

始终返回S_OK。

### <a name="remarks"></a>备注

此类提供的实现不执行任何操作。

## <a name="cnoworkerthreadshutdown"></a><a name="shutdown"></a>CNoWorker 线程：：关闭

CWorkerThread 的非功能等效项[：：关机](../../atl/reference/cworkerthread-class.md#shutdown)。

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="return-value"></a>返回值

始终返回S_OK。

### <a name="remarks"></a>备注

此类提供的实现不执行任何操作。
