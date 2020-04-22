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
ms.openlocfilehash: 5e52868f23883836919b96be9aec1815bc1c17b3
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747445"
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
类符合[辅助角色原型](../../atl/reference/worker-archetype.md)，提供用于处理线程池上排队的工作项的代码。

*线程特征*<br/>
提供用于在池中创建线程的函数的类。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CThreadPool：CThreadPool](#cthreadpool)|线程池的构造函数。|
|[CThreadPool：*CThreadPool](#dtor)|线程池的析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CThreadPool：：添加参考](#addref)|`IUnknown::AddRef` 的实现。|
|[CThreadPool：获取线程](#getnumthreads)|调用此方法获取池中的线程数。|
|[CThreadPool：获取QueueHandle](#getqueuehandle)|调用此方法获取用于对工作项进行排队的 IO 完成端口的句柄。|
|[CThreadPool：获取 Size](#getsize)|调用此方法获取池中的线程数。|
|[CThreadPool：获取超时](#gettimeout)|调用此方法，获取线程池将等待线程关闭的最大时间（以毫秒为单位）。|
|[CThreadPool：初始化](#initialize)|调用此方法以初始化线程池。|
|[CThreadPool：查询接口](#queryinterface)|`IUnknown::QueryInterface` 的实现。|
|[CThreadPool：队列请求](#queuerequest)|调用此方法以对池中的线程要处理的工作项进行排队。|
|[CThreadPool：发布](#release)|`IUnknown::Release` 的实现。|
|[CThreadPool：设置大小](#setsize)|调用此方法以设置池中的线程数。|
|[CThreadPool：设置超时](#settimeout)|调用此方法以设置线程池将等待线程关闭的最大时间（以毫秒为单位）。|
|[CThreadPool：关闭](#shutdown)|调用此方法以关闭线程池。|

## <a name="remarks"></a>备注

在初始化、调整大小或关闭池时，将创建和销毁池中的线程。 将在池中每个辅助线程的堆栈上创建类*辅助角色*实例。 每个实例将活在线程的生存期内。

创建线程后，将立即调用与该线程关联的`Initialize`对象上的*辅助角色*：： 。 在销毁线程之前，将立即调用*辅助角色*`Terminate` ：： 。 这两种方法都必须接受**void**<strong>\*</strong>参数。 此参数的值通过 CThreadPool 的*pvWorkerParam*参数传递给线程池[：：初始化](#initialize)。

当队列中的工作项和工作线程中可用于工作时，工作线程将从队列中拉出一个项，并调用该线程`Execute`*的辅助对象*的方法。 然后，三个项传递给方法：队列中的项，相同的`pvWorkerParam`传递给*辅助角色*：：`Initialize`和*辅助角色*：： `Terminate`， 以及指向 IO 完成端口队列的[OVERLAPPED](/windows/win32/api/minwinbase/ns-minwinbase-overlapped)结构的指针。

Worker 类通过提供`RequestType`typedef、Worker：： ， 声明将在线程池上排队的项的类型。 *Worker* *Worker* 此类型必须能够强制转换到ULONG_PTR。

*辅助工*类的一个示例是["无状态辅助角色"类](../../atl/reference/cnonstatelessworker-class.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IUnknown`

[IThreadPool 配置](../../atl/reference/ithreadpoolconfig-interface.md)

`CThreadPool`

## <a name="requirements"></a>要求

**标题：** atlutil.h

## <a name="cthreadpooladdref"></a><a name="addref"></a>CThreadPool：：添加参考

`IUnknown::AddRef` 的实现。

```
ULONG STDMETHODCALLTYPE AddRef() throw();
```

### <a name="return-value"></a>返回值

始终返回 1。

### <a name="remarks"></a>备注

此类不使用引用计数实现生存期控制。

## <a name="cthreadpoolcthreadpool"></a><a name="cthreadpool"></a>CThreadPool：CThreadPool

线程池的构造函数。

```
CThreadPool() throw();
```

### <a name="remarks"></a>备注

将超时值初始化为ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT。 默认时间是 36 秒。 如有必要，您可以在包含 atlutil.h 之前为此符号定义您自己的正整数值。

## <a name="cthreadpoolcthreadpool"></a><a name="dtor"></a>CThreadPool：*CThreadPool

线程池的析构函数。

```
~CThreadPool() throw();
```

### <a name="remarks"></a>备注

调用[CThreadPool：：关闭](#shutdown)。

## <a name="cthreadpoolgetnumthreads"></a><a name="getnumthreads"></a>CThreadPool：获取线程

调用此方法获取池中的线程数。

```
int GetNumThreads() throw();
```

### <a name="return-value"></a>返回值

返回池中的线程数。

## <a name="cthreadpoolgetqueuehandle"></a><a name="getqueuehandle"></a>CThreadPool：获取QueueHandle

调用此方法获取用于对工作项进行排队的 IO 完成端口的句柄。

```
HANDLE GetQueueHandle() throw();
```

### <a name="return-value"></a>返回值

如果线程池尚未初始化，则返回队列句柄或 NULL。

## <a name="cthreadpoolgetsize"></a><a name="getsize"></a>CThreadPool：获取 Size

调用此方法获取池中的线程数。

```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```

### <a name="parameters"></a>参数

*pnNumThreads*<br/>
[出]变量的地址，在成功时，接收池中的线程数。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cthreadpoolgettimeout"></a><a name="gettimeout"></a>CThreadPool：获取超时

调用此方法，获取线程池将等待线程关闭的最大时间（以毫秒为单位）。

```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```

### <a name="parameters"></a>参数

*pdwMaxWait*<br/>
[出]变量的地址，在成功时，接收线程池将等待线程关闭的最大时间（以毫秒为单位）。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

[CThreadPool：：](#shutdown)如果未向该方法提供其他值，则使用此超时值：：如果未向该方法提供其他值，则关闭。

## <a name="cthreadpoolinitialize"></a><a name="initialize"></a>CThreadPool：初始化

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
要传递给辅助线程对象的`Initialize`辅助角色参数`Execute`， 和方法。 `Terminate`

*nNumThreads*<br/>
池中请求的线程数。

如果*nNumThreads*为负值，则其绝对值将乘以计算机中的处理器数，以获得线程总数。

如果*nNumThreads*为零，ATLS_DEFAULT_THREADSPERPROC将乘以计算机中的处理器数，以获得线程总数。  默认值为每处理器 2 个线程。 如有必要，您可以在包含 atlutil.h 之前为此符号定义您自己的正整数值。

*dwStackSize*<br/>
池中每个线程的堆栈大小。

*h 完成*<br/>
要与完成端口关联的对象的句柄。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

## <a name="cthreadpoolqueryinterface"></a><a name="queryinterface"></a>CThreadPool：查询接口

`IUnknown::QueryInterface` 的实现。

```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```

### <a name="remarks"></a>备注

可以成功查询此类的对象`IUnknown`和[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)接口。

## <a name="cthreadpoolqueuerequest"></a><a name="queuerequest"></a>CThreadPool：队列请求

调用此方法以对池中的线程要处理的工作项进行排队。

```
BOOL QueueRequest(Worker::RequestType request) throw();
```

### <a name="parameters"></a>参数

*请求*<br/>
要排队的请求。

### <a name="return-value"></a>返回值

成功时返回 TRUE，在失败时返回 FALSE。

### <a name="remarks"></a>备注

此方法将工作项添加到队列中。 池中的线程按接收项的顺序从队列中选取项。

## <a name="cthreadpoolrelease"></a><a name="release"></a>CThreadPool：发布

`IUnknown::Release` 的实现。

```
ULONG STDMETHODCALLTYPE Release() throw();
```

### <a name="return-value"></a>返回值

始终返回 1。

### <a name="remarks"></a>备注

此类不使用引用计数实现生存期控制。

## <a name="cthreadpoolsetsize"></a><a name="setsize"></a>CThreadPool：设置大小

调用此方法以设置池中的线程数。

```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```

### <a name="parameters"></a>参数

*nNumThreads*<br/>
池中请求的线程数。

如果*nNumThreads*为负值，则其绝对值将乘以计算机中的处理器数，以获得线程总数。

如果*nNumThreads*为零，ATLS_DEFAULT_THREADSPERPROC将乘以计算机中的处理器数，以获得线程总数。 默认值为每处理器 2 个线程。 如有必要，您可以在包含 atlutil.h 之前为此符号定义您自己的正整数值。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

如果指定的线程数小于池中当前线程数，则对象将在队列中放置一条关机消息，以便等待线程选取。 当等待的线程将消息从队列中拉出时，它会通知线程池并退出线程过程。 此过程将重复，直到池中的线程数达到指定数量，或者直到[GetTimeout](#gettimeout)/ [设置超时](#settimeout)指定的期间没有线程退出。 在此情况下，该方法将返回一个对应于WAIT_TIMEOUT的 HRESULT，并且挂起的关机消息将被取消。

## <a name="cthreadpoolsettimeout"></a><a name="settimeout"></a>CThreadPool：设置超时

调用此方法以设置线程池将等待线程关闭的最大时间（以毫秒为单位）。

```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```

### <a name="parameters"></a>参数

*dwMaxWait*<br/>
请求的最大时间（以毫秒为单位）用于线程池将等待线程关闭。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="remarks"></a>备注

超时初始化为ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT。 默认时间是 36 秒。 如有必要，您可以在包含 atlutil.h 之前为此符号定义您自己的正整数值。

请注意 *，dwMaxWait*是池将等待单个线程关闭的时间。 从池中删除多个线程所可能需要的最大时间可能略低于*dwMaxWait*乘以线程数。

## <a name="cthreadpoolshutdown"></a><a name="shutdown"></a>CThreadPool：关闭

调用此方法以关闭线程池。

```cpp
void Shutdown(DWORD dwMaxWait = 0) throw();
```

### <a name="parameters"></a>参数

*dwMaxWait*<br/>
请求的最大时间（以毫秒为单位）用于线程池将等待线程关闭。 如果提供 0 或没有值，此方法将使用[CThreadPool：：SetTimeout](#settimeout)设置的超时设置。

### <a name="remarks"></a>备注

此方法将关机请求发布到池中的所有线程。 如果超时过期，此方法将在未退出的任何线程上调用[TerminateThread。](/windows/win32/api/processthreadsapi/nf-processthreadsapi-terminatethread) 此方法从类的析构函数自动调用。

## <a name="see-also"></a>请参阅

[IThreadPoolConfig 接口](../../atl/reference/ithreadpoolconfig-interface.md)<br/>
[默认线程特征](atl-typedefs.md#defaultthreadtraits)<br/>
[类](../../atl/reference/atl-classes.md)
