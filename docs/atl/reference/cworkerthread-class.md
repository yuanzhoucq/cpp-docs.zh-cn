---
title: CWorkerThread 类
ms.date: 11/04/2016
f1_keywords:
- CWorkerThread
- ATLUTIL/ATL::CWorkerThread
- ATLUTIL/ATL::CWorkerThread::CWorkerThread
- ATLUTIL/ATL::CWorkerThread::AddHandle
- ATLUTIL/ATL::CWorkerThread::AddTimer
- ATLUTIL/ATL::CWorkerThread::GetThreadHandle
- ATLUTIL/ATL::CWorkerThread::GetThreadId
- ATLUTIL/ATL::CWorkerThread::Initialize
- ATLUTIL/ATL::CWorkerThread::RemoveHandle
- ATLUTIL/ATL::CWorkerThread::Shutdown
helpviewer_keywords:
- CWorkerThread class
ms.assetid: be79a832-1345-4a36-a13e-a406cc65286f
ms.openlocfilehash: 05e6b432d44927fa7e276792643e29c80c42d822
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330211"
---
# <a name="cworkerthread-class"></a>CWorkerThread 类

此类创建辅助线程或使用现有线程，在一个或多个内核对象句柄上等待，并在其中一个句柄发出信号时执行指定的客户端函数。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
template <class ThreadTraits = DefaultThreadTraits>
class CWorkerThread
```

### <a name="parameters"></a>参数

*线程特征*<br/>
提供线程创建函数的类，如[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)或[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)。

## <a name="members"></a>成员

### <a name="protected-structures"></a>受保护结构

|名称|说明|
|----------|-----------------|
|`WorkerClientEntry`||

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CWorker 线程：CWorkerThread](#cworkerthread)|辅助线程的构造函数。|
|[CWorker 线程：*CWorkerThread](#dtor)|辅助线程的析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CWorkerThread：：添加句柄](#addhandle)|调用此方法以将可等待对象的句柄添加到辅助线程维护的列表。|
|[CWorkerThread：：添加计时器](#addtimer)|调用此方法以将定期可等待计时器添加到辅助线程维护的列表。|
|[CWorker 线程：获取线程句柄](#getthreadhandle)|调用此方法以获取辅助线程的线程句柄。|
|[CWorkerThread：getThreadId](#getthreadid)|调用此方法以获取辅助线程的线程 ID。|
|[CWorkerThread：初始化](#initialize)|调用此方法以初始化辅助线程。|
|[CWorkerThread：：删除句柄](#removehandle)|调用此方法从可等待对象列表中删除句柄。|
|[CWorkerThread：：关闭](#shutdown)|调用此方法以关闭辅助线程。|

## <a name="remarks"></a>备注

### <a name="to-use-cworkerthread"></a>使用 CWorkerThread

1. 创建此类的实例。

1. 调用[CWorkerThread：：初始化](#initialize)。

1. 调用[CWorkerThread：使用](#addhandle)内核对象的句柄和指向[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)实现的指针添加Handle。

   \- 或 -

   调用[CWorkerThread：使用](#addtimer)指向[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)实现的指针添加Timer。

1. 实现[IWorkerThreadClient：：执行](../../atl/reference/iworkerthreadclient-interface.md#execute)在发出信号的句柄或计时器时执行一些操作。

1. 要从可等待对象列表中删除对象，请调用[CWorkerThread：：删除句柄](#removehandle)。

1. 要终止线程，请调用[CWorkerThread：：关机](#shutdown)。

## <a name="requirements"></a>要求

**标题：** atlutil.h

## <a name="cworkerthreadaddhandle"></a><a name="addhandle"></a>CWorkerThread：：添加句柄

调用此方法以将可等待对象的句柄添加到辅助线程维护的列表。

```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```

### <a name="parameters"></a>参数

*hObject*<br/>
可等待对象的句柄。

*pClient*<br/>
指向对象上的[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)接口的指针，当句柄发出信号时，要调用该接口。

*德帕拉姆*<br/>
要传递给[IWorkerThreadClient 的参数：](../../atl/reference/iworkerthreadclient-interface.md#execute)在发出信号时执行。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

[IWorkerThreadClient：当](../../atl/reference/iworkerthreadclient-interface.md#execute)句柄*hObject*发出信号时，将通过*pClient*调用执行。

## <a name="cworkerthreadaddtimer"></a><a name="addtimer"></a>CWorkerThread：：添加计时器

调用此方法以将定期可等待计时器添加到辅助线程维护的列表。

```
HRESULT AddTimer(
    DWORD dwInterval,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam,
    HANDLE* phTimer) throw();
```

### <a name="parameters"></a>参数

*dw间隔*<br/>
指定计时器的周期（以毫秒为单位）。

*pClient*<br/>
指向对象上的[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)接口的指针，当句柄发出信号时，要调用该接口。

*德帕拉姆*<br/>
要传递给[IWorkerThreadClient 的参数：](../../atl/reference/iworkerthreadclient-interface.md#execute)在发出信号时执行。

*phTimer*<br/>
[出]HANDLE 变量的地址，在成功时，接收新创建的计时器的句柄。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

[IWorkerThreadClient：当](../../atl/reference/iworkerthreadclient-interface.md#execute)计时器发出信号时，将通过*pClient*调用执行。

将计时器句柄从*phTimer*传递到[CWorkerThread：：删除手柄](#removehandle)以关闭计时器。

## <a name="cworkerthreadcworkerthread"></a><a name="cworkerthread"></a>CWorker 线程：CWorkerThread

构造函数。

```
CWorkerThread() throw();
```

## <a name="cworkerthreadcworkerthread"></a><a name="dtor"></a>CWorker 线程：*CWorkerThread

析构函数。

```
~CWorkerThread() throw();
```

### <a name="remarks"></a>备注

调用[CWorkerThread：：关闭](#shutdown)。

## <a name="cworkerthreadgetthreadhandle"></a><a name="getthreadhandle"></a>CWorker 线程：获取线程句柄

调用此方法以获取辅助线程的线程句柄。

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>返回值

如果工作线程尚未初始化，则返回线程句柄或 NULL。

## <a name="cworkerthreadgetthreadid"></a><a name="getthreadid"></a>CWorkerThread：getThreadId

调用此方法以获取辅助线程的线程 ID。

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>返回值

如果工作线程尚未初始化，则返回线程 ID 或 NULL。

## <a name="cworkerthreadinitialize"></a><a name="initialize"></a>CWorkerThread：初始化

调用此方法以初始化辅助线程。

```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```

### <a name="parameters"></a>参数

*pThread*<br/>
现有辅助线程。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

应调用此方法在创建后或调用[CWorkerThread：：：：：关机](#shutdown)后初始化对象。

要让两个或多个`CWorkerThread`对象使用相同的辅助线程，请初始化其中一个对象而不传递任何参数，然后将指向该对象的指针传递给其他对象`Initialize`的方法。 使用指针初始化的对象应在用于初始化的对象之前关闭。

有关使用指向现有对象的指针初始化时该方法的行为如何变化的信息，请参阅[CWorkerThread：：关机](#shutdown)。

## <a name="cworkerthreadremovehandle"></a><a name="removehandle"></a>CWorkerThread：：删除句柄

调用此方法从可等待对象列表中删除句柄。

```
HRESULT RemoveHandle(HANDLE hObject) throw();
```

### <a name="parameters"></a>参数

*hObject*<br/>
要删除的句柄。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

删除句柄时[，IWorkerThreadClient：：关闭处理](../../atl/reference/iworkerthreadclient-interface.md#closehandle)将在传递给[AddHandle](#addhandle)的关联对象上调用。 如果此调用失败，`CWorkerThread`将在句柄上调用 Windows [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle)函数。

## <a name="cworkerthreadshutdown"></a><a name="shutdown"></a>CWorkerThread：：关闭

调用此方法以关闭辅助线程。

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="parameters"></a>参数

*dwWait*<br/>
等待辅助线程关闭的时间（以毫秒为单位）。 ATL_WORKER_THREAD_WAIT默认值为 10 秒。 如有必要，您可以在包含 atlutil.h 之前为此符号定义您自己的值。

### <a name="return-value"></a>返回值

返回成功时S_OK，或失败时出现错误 HRESULT，例如如果超过超时值*dwWait。*

### <a name="remarks"></a>备注

要重用该对象，请调用[CWorkerThread：：](#initialize)调用此方法后初始化。

请注意，使用`Shutdown`指向另`CWorkerThread`一个对象的指针初始化的对象调用不起作用，并且始终返回S_OK。

## <a name="see-also"></a>另请参阅

[默认线程特征](atl-typedefs.md#defaultthreadtraits)<br/>
[类](../../atl/reference/atl-classes.md)<br/>
[多线程处理：创建辅助线程](../../parallel/multithreading-creating-worker-threads.md)<br/>
[IWorkerThreadClient 接口](../../atl/reference/iworkerthreadclient-interface.md)
