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
ms.openlocfilehash: f1aa76514b98bbf12f8e516d3d54f68e8ef4dd7d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78862904"
---
# <a name="cworkerthread-class"></a>CWorkerThread 类

此类创建一个或多个工作线程，并使用现有的工作线程，在一个或多个内核对象句柄上等待，并在其中一个句柄发出信号时执行指定的客户端函数。

> [!IMPORTANT]
> 此类及其成员不能用于在 Windows 运行时中执行的应用程序。

## <a name="syntax"></a>语法

```
template <class ThreadTraits = DefaultThreadTraits>
class CWorkerThread
```

### <a name="parameters"></a>参数

*ThreadTraits*<br/>
提供线程创建函数的类，如[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)或[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)。

## <a name="members"></a>Members

### <a name="protected-structures"></a>受保护的结构

|名称|说明|
|----------|-----------------|
|`WorkerClientEntry`||

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CWorkerThread::CWorkerThread](#cworkerthread)|工作线程的构造函数。|
|[CWorkerThread：： ~ CWorkerThread](#dtor)|工作线程的析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CWorkerThread::AddHandle](#addhandle)|调用此方法可将可等待对象的句柄添加到由工作线程维护的列表。|
|[CWorkerThread::AddTimer](#addtimer)|调用此方法可将定期可等待计时器添加到由工作线程维护的列表。|
|[CWorkerThread::GetThreadHandle](#getthreadhandle)|调用此方法可获取工作线程的线程句柄。|
|[CWorkerThread::GetThreadId](#getthreadid)|调用此方法可获取工作线程的线程 ID。|
|[CWorkerThread：： Initialize](#initialize)|调用此方法可初始化工作线程。|
|[CWorkerThread::RemoveHandle](#removehandle)|调用此方法可从可等待对象列表中删除句柄。|
|[CWorkerThread：： Shutdown](#shutdown)|调用此方法可关闭工作线程。|

## <a name="remarks"></a>备注

### <a name="to-use-cworkerthread"></a>使用 CWorkerThread

1. 创建此类的实例。

1. 调用[CWorkerThread：： Initialize](#initialize)。

1. 调用[CWorkerThread：： AddHandle](#addhandle) ，其中包含内核对象的句柄和指向[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)的实现的指针。

   \- 或 -

   调用[CWorkerThread：： AddTimer](#addtimer) ，其中包含指向[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)的实现的指针。

1. 实现[IWorkerThreadClient：： Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)以在句柄或计时器发出信号时执行某种操作。

1. 若要从可等待对象列表中删除对象，请调用[CWorkerThread：： RemoveHandle](#removehandle)。

1. 若要终止线程，请调用[CWorkerThread：： Shutdown](#shutdown)。

## <a name="requirements"></a>要求

**标头：** atlutil

##  <a name="addhandle"></a>CWorkerThread::AddHandle

调用此方法可将可等待对象的句柄添加到由工作线程维护的列表。

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
指向对象上的[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)接口的指针，该对象将在终止句柄时调用。

*dwParam*<br/>
要传递给[IWorkerThreadClient：：](../../atl/reference/iworkerthreadclient-interface.md#execute)在句柄终止时执行的参数。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

当句柄*hObject*时， [IWorkerThreadClient：： Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)将通过*pClient*调用。

##  <a name="addtimer"></a>CWorkerThread::AddTimer

调用此方法可将定期可等待计时器添加到由工作线程维护的列表。

```
HRESULT AddTimer(
    DWORD dwInterval,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam,
    HANDLE* phTimer) throw();
```

### <a name="parameters"></a>参数

*dwInterval*<br/>
指定计时器的持续时间（以毫秒为单位）。

*pClient*<br/>
指向对象上的[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)接口的指针，该对象将在终止句柄时调用。

*dwParam*<br/>
要传递给[IWorkerThreadClient：：](../../atl/reference/iworkerthreadclient-interface.md#execute)在句柄终止时执行的参数。

*phTimer*<br/>
弄成功时接收到新创建的计时器的句柄的句柄变量的地址。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

当计时器发出信号时， [IWorkerThreadClient：： Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)将通过*pClient*调用。

将计时器句柄从*phTimer*传递到[CWorkerThread：： RemoveHandle](#removehandle)以关闭计时器。

##  <a name="cworkerthread"></a>CWorkerThread::CWorkerThread

构造函数。

```
CWorkerThread() throw();
```

##  <a name="dtor"></a>CWorkerThread：： ~ CWorkerThread

析构函数。

```
~CWorkerThread() throw();
```

### <a name="remarks"></a>备注

调用[CWorkerThread：： Shutdown](#shutdown)。

##  <a name="getthreadhandle"></a>CWorkerThread::GetThreadHandle

调用此方法可获取工作线程的线程句柄。

```
HANDLE GetThreadHandle() throw();
```

### <a name="return-value"></a>返回值

如果工作线程尚未初始化，则返回线程句柄或 NULL。

##  <a name="getthreadid"></a>CWorkerThread::GetThreadId

调用此方法可获取工作线程的线程 ID。

```
DWORD GetThreadId() throw();
```

### <a name="return-value"></a>返回值

如果工作线程尚未初始化，则返回线程 ID 或 NULL。

##  <a name="initialize"></a>CWorkerThread：： Initialize

调用此方法可初始化工作线程。

```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```

### <a name="parameters"></a>参数

*pThread*<br/>
现有的工作线程。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

调用[CWorkerThread：： Shutdown](#shutdown)后，应调用此方法来初始化对象。

若要使两个或多个 `CWorkerThread` 对象使用同一个工作线程，请在不传递任何参数的情况下初始化其中的一个，然后将指向该对象的指针传递给其他对象的 `Initialize` 方法。 使用指针初始化的对象应在用于初始化它们的对象之前关闭。

有关使用指向现有对象的指针进行初始化时该方法的行为如何发生更改的信息，请参阅[CWorkerThread：： Shutdown](#shutdown) 。

##  <a name="removehandle"></a>CWorkerThread::RemoveHandle

调用此方法可从可等待对象列表中删除句柄。

```
HRESULT RemoveHandle(HANDLE hObject) throw();
```

### <a name="parameters"></a>参数

*hObject*<br/>
要移除的句柄。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

删除句柄时，将对传递到[AddHandle](#addhandle)的关联对象调用[IWorkerThreadClient：： CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle) 。 如果此调用失败，`CWorkerThread` 将对句柄调用 Windows [CloseHandle](/windows/win32/api/handleapi/nf-handleapi-closehandle)函数。

##  <a name="shutdown"></a>CWorkerThread：： Shutdown

调用此方法可关闭工作线程。

```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```

### <a name="parameters"></a>参数

*dwWait*<br/>
等待工作线程关闭所用的时间（以毫秒为单位）。 ATL_WORKER_THREAD_WAIT 默认为10秒。 如有必要，你可以在包括 atlutil 之前为此符号定义你自己的值。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误，如超时值*dwWait*。

### <a name="remarks"></a>备注

若要重用该对象，请在调用此方法后调用[CWorkerThread：： Initialize](#initialize) 。

请注意，对使用指向另一个 `CWorkerThread` 对象的指针进行初始化的对象调用 `Shutdown` 不起作用，并且始终返回 S_OK。

## <a name="see-also"></a>另请参阅

[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[类](../../atl/reference/atl-classes.md)<br/>
[多线程处理：创建辅助线程](../../parallel/multithreading-creating-worker-threads.md)<br/>
[IWorkerThreadClient 接口](../../atl/reference/iworkerthreadclient-interface.md)
