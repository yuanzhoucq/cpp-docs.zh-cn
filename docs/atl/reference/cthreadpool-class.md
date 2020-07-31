---
title: CThreadPool 类
ms.date: 11/04/2016
f1_keywords:
- CThreadPool
- ATLUTIL/ATL::CThreadPool
- ATLUTIL/ATL::CThreadPool::CThreadPool
- ATLUTIL/ATL::CThreadPool::AddRef
- ATLUTIL/ATL::CThreadPool::GetNumThreads
- ATLUTIL/ATL::CThreadPool::GetQueueHandle
- ATLUTIL/ATL::CThreadPool::GetSize
- ATLUTIL/ATL::CThreadPool::GetTimeout
- ATLUTIL/ATL::CThreadPool::Initialize
- ATLUTIL/ATL::CThreadPool::QueryInterface
- ATLUTIL/ATL::CThreadPool::QueueRequest
- ATLUTIL/ATL::CThreadPool::Release
- ATLUTIL/ATL::CThreadPool::SetSize
- ATLUTIL/ATL::CThreadPool::SetTimeout
- ATLUTIL/ATL::CThreadPool::Shutdown
helpviewer_keywords:
- CThreadPool class
ms.assetid: 06683718-01b9-413c-9481-2dc1734ec70f
ms.openlocfilehash: 12b28cd4f54fa426bb6ad2b2710d62b426ada2b6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226537"
---
# <a name="cthreadpool-class"></a>CThreadPool 类

此类提供处理工作项队列的工作线程池。

## <a name="syntax"></a>语法

```
template <class Worker, class ThreadTraits = DefaultThreadTraits>
class CThreadPool : public IThreadPoolConfig
```

#### <a name="parameters"></a>参数

*工人*<br/>
类符合[工作原型](../../atl/reference/worker-archetype.md)，后者提供用于处理线程池上排队的工作项的代码。

*ThreadTraits*<br/>
提供用于在池中创建线程的函数的类。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CThreadPool::CThreadPool](#cthreadpool)|线程池的构造函数。|
|[CThreadPool：： ~ CThreadPool](#dtor)|线程池的析构函数。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[CThreadPool：： AddRef](#addref)|`IUnknown::AddRef` 的实现。|
|[CThreadPool::GetNumThreads](#getnumthreads)|调用此方法可获取池中的线程数。|
|[CThreadPool::GetQueueHandle](#getqueuehandle)|调用此方法以获取用于对工作项进行排队的 IO 完成端口的句柄。|
|[CThreadPool：： GetSize](#getsize)|调用此方法可获取池中的线程数。|
|[CThreadPool::GetTimeout](#gettimeout)|调用此方法以获取线程池等待线程关闭的最长时间（以毫秒为单位）。|
|[CThreadPool：： Initialize](#initialize)|调用此方法以初始化线程池。|
|[CThreadPool：： QueryInterface](#queryinterface)|`IUnknown::QueryInterface` 的实现。|
|[CThreadPool::QueueRequest](#queuerequest)|调用此方法可将工作项排队，以便由池中的线程进行处理。|
|[CThreadPool：： Release](#release)|`IUnknown::Release` 的实现。|
|[CThreadPool：： SetSize](#setsize)|调用此方法可设置池中的线程数。|
|[CThreadPool：： SetTimeout](#settimeout)|调用此方法以设置线程池等待线程关闭的最长时间（以毫秒为单位）。|
|[CThreadPool：： Shutdown](#shutdown)|调用此方法可关闭线程池。|

## <a name="remarks"></a>备注

缓冲池时，将创建并销毁池中的线程。 将在池中每个工作线程的堆栈上创建类*辅助角色*的实例。 每个实例将在线程的生存期内生存。

在创建线程后立即开始， *Worker* `Initialize` 将在与该线程关联的对象上调用 Worker：：。 紧跟在析构之前，将调用*Worker*：： `Terminate` 。 两种方法都必须接受 **`void`** <strong>\*</strong> 参数。 通过[CThreadPool：： Initialize](#initialize)的*pvWorkerParam*参数将此参数的值传递给线程池。

当队列中有工作项并且辅助线程可用于工作时，工作线程将从队列中拉取一个项，并 `Execute` 为该线程调用*worker*对象的方法。 然后，将三个项传递给方法：队列中的项、 `pvWorkerParam` 传递给*worker*：： `Initialize` 和*worker*：：的项， `Terminate` 以及指向用于 IO 完成端口队列的[重叠](/windows/win32/api/minwinbase/ns-minwinbase-overlapped)结构的指针。

*辅助*类通过提供 Typedef， *worker*：：来声明将在线程池上排队的项的类型 `RequestType` 。 此类型必须能够与 ULONG_PTR 强制转换。

*辅助角色*类的一个示例是[CNonStatelessWorker 类](../../atl/reference/cnonstatelessworker-class.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IUnknown`

[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)

`CThreadPool`

## <a name="requirements"></a>要求

**标头：** atlutil

## <a name="cthreadpooladdref"></a><a name="addref"></a>CThreadPool：： AddRef

`IUnknown::AddRef` 的实现。

```
ULONG STDMETHODCALLTYPE AddRef() throw();
```

### <a name="return-value"></a>返回值

始终返回1。

### <a name="remarks"></a>备注

此类不使用引用计数实现生存期控制。

## <a name="cthreadpoolcthreadpool"></a><a name="cthreadpool"></a>CThreadPool::CThreadPool

线程池的构造函数。

```
CThreadPool() throw();
```

### <a name="remarks"></a>备注

将超时值初始化为 ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT。 默认时间为36秒。 如有必要，你可以在包括 atlutil 之前为此符号定义你自己的正整数值。

## <a name="cthreadpoolcthreadpool"></a><a name="dtor"></a>CThreadPool：： ~ CThreadPool

线程池的析构函数。

```
~CThreadPool() throw();
```

### <a name="remarks"></a>备注

调用[CThreadPool：： Shutdown](#shutdown)。

## <a name="cthreadpoolgetnumthreads"></a><a name="getnumthreads"></a>CThreadPool::GetNumThreads

调用此方法可获取池中的线程数。

```
int GetNumThreads() throw();
```

### <a name="return-value"></a>返回值

返回池中的线程数。

## <a name="cthreadpoolgetqueuehandle"></a><a name="getqueuehandle"></a>CThreadPool::GetQueueHandle

调用此方法以获取用于对工作项进行排队的 IO 完成端口的句柄。

```
HANDLE GetQueueHandle() throw();
```

### <a name="return-value"></a>返回值

返回队列句柄，如果尚未初始化线程池，则返回 NULL。

## <a name="cthreadpoolgetsize"></a><a name="getsize"></a>CThreadPool：： GetSize

调用此方法可获取池中的线程数。

```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```

### <a name="parameters"></a>参数

*pnNumThreads*<br/>
弄成功接收池中的线程数的变量的地址。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

## <a name="cthreadpoolgettimeout"></a><a name="gettimeout"></a>CThreadPool::GetTimeout

调用此方法以获取线程池等待线程关闭的最长时间（以毫秒为单位）。

```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```

### <a name="parameters"></a>参数

*pdwMaxWait*<br/>
弄成功时的变量地址，接收线程池等待线程关闭的最长时间（以毫秒为单位）。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

如果没有为该方法提供其他值， [CThreadPool：： Shutdown](#shutdown)将使用此超时值。

## <a name="cthreadpoolinitialize"></a><a name="initialize"></a>CThreadPool：： Initialize

调用此方法以初始化线程池。

```
HRESULT Initialize(
    void* pvWorkerParam = NULL,
    int nNumThreads = 0,
    DWORD dwStackSize = 0,
    HANDLE hCompletion = INVALID_HANDLE_VALUE) throw();
```

### <a name="parameters"></a>参数

*pvWorkerParam*<br/>
要传递到工作线程对象的 `Initialize` 、和方法的辅助参数 `Execute` `Terminate` 。

*nNumThreads*<br/>
池中请求的线程数。

如果*nNumThreads*为负，则其绝对值将乘以计算机中的处理器数，以获取线程的总数。

如果*nNumThreads*为零，ATLS_DEFAULT_THREADSPERPROC 将乘以计算机中的处理器数，以获取线程的总数。  默认值为每个处理器2个线程。 如有必要，你可以在包括 atlutil 之前为此符号定义你自己的正整数值。

*dwStackSize*<br/>
池中每个线程的堆栈大小。

*hCompletion*<br/>
要与完成端口关联的对象的句柄。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

## <a name="cthreadpoolqueryinterface"></a><a name="queryinterface"></a>CThreadPool：： QueryInterface

`IUnknown::QueryInterface` 的实现。

```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```

### <a name="remarks"></a>备注

可以为 `IUnknown` 和[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)接口成功查询此类的对象。

## <a name="cthreadpoolqueuerequest"></a><a name="queuerequest"></a>CThreadPool::QueueRequest

调用此方法可将工作项排队，以便由池中的线程进行处理。

```
BOOL QueueRequest(Worker::RequestType request) throw();
```

### <a name="parameters"></a>参数

*请求*<br/>
要排队的请求。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

此方法将工作项添加到队列。 池中的线程将按接收项的顺序从队列中选取项。

## <a name="cthreadpoolrelease"></a><a name="release"></a>CThreadPool：： Release

`IUnknown::Release` 的实现。

```
ULONG STDMETHODCALLTYPE Release() throw();
```

### <a name="return-value"></a>返回值

始终返回1。

### <a name="remarks"></a>备注

此类不使用引用计数实现生存期控制。

## <a name="cthreadpoolsetsize"></a><a name="setsize"></a>CThreadPool：： SetSize

调用此方法可设置池中的线程数。

```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```

### <a name="parameters"></a>参数

*nNumThreads*<br/>
池中请求的线程数。

如果*nNumThreads*为负，则其绝对值将乘以计算机中的处理器数，以获取线程的总数。

如果*nNumThreads*为零，ATLS_DEFAULT_THREADSPERPROC 将乘以计算机中的处理器数，以获取线程的总数。 默认值为每个处理器2个线程。 如有必要，你可以在包括 atlutil 之前为此符号定义你自己的正整数值。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

如果指定的线程数小于池中当前的线程数，则该对象会将关闭消息放在队列上以由等待线程选取。 当正在等待的线程从队列中提取消息时，它会通知线程池并退出线程过程。 此过程将重复进行，直到池中的线程数达到指定的数字或在[GetTimeout](#gettimeout)SetTimeout 指定的时间段内未退出任何线程为止 /  [SetTimeout](#settimeout)。 在这种情况下，该方法将返回一个与 WAIT_TIMEOUT 相对应的 HRESULT，并取消挂起的关闭消息。

## <a name="cthreadpoolsettimeout"></a><a name="settimeout"></a>CThreadPool：： SetTimeout

调用此方法以设置线程池等待线程关闭的最长时间（以毫秒为单位）。

```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```

### <a name="parameters"></a>参数

*dwMaxWait*<br/>
线程池等待线程关闭所需的最长时间（以毫秒为单位）。

### <a name="return-value"></a>返回值

如果成功，则返回 S_OK; 否则返回错误 HRESULT。

### <a name="remarks"></a>备注

超时初始化为 ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT。 默认时间为36秒。 如有必要，你可以在包括 atlutil 之前为此符号定义你自己的正整数值。

请注意， *dwMaxWait*是池等待单个线程关闭的时间。 从池中删除多个线程所需的最长时间可能略微小于*dwMaxWait*乘以线程数。

## <a name="cthreadpoolshutdown"></a><a name="shutdown"></a>CThreadPool：： Shutdown

调用此方法可关闭线程池。

```cpp
void Shutdown(DWORD dwMaxWait = 0) throw();
```

### <a name="parameters"></a>参数

*dwMaxWait*<br/>
线程池等待线程关闭所需的最长时间（以毫秒为单位）。 如果未提供任何值，则此方法将使用[CThreadPool：： SetTimeout](#settimeout)设置的超时值。

### <a name="remarks"></a>备注

此方法将关闭请求发送到池中的所有线程。 如果超时时间已到，则此方法将在任何未退出的线程上调用[TerminateThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-terminatethread) 。 此方法是从类的析构函数自动调用的。

## <a name="see-also"></a>另请参阅

[IThreadPoolConfig 接口](../../atl/reference/ithreadpoolconfig-interface.md)<br/>
[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)<br/>
[类](../../atl/reference/atl-classes.md)
