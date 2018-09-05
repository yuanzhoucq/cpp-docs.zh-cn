---
title: CThreadPool 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CThreadPool class
ms.assetid: 06683718-01b9-413c-9481-2dc1734ec70f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9753599f08d1e8ee238097027c501a0b56e40300
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757389"
---
# <a name="cthreadpool-class"></a>CThreadPool 类

此类提供处理的工作项队列的工作线程的池。

## <a name="syntax"></a>语法

```
template <class Worker, class ThreadTraits = DefaultThreadTraits>  
class CThreadPool : public IThreadPoolConfig
```

#### <a name="parameters"></a>参数

*辅助角色*  
类符合[辅助原型](../../atl/reference/worker-archetype.md)提供用来处理的工作项排入队列在线程池的代码。

*ThreadTraits*  
类，用于提供用来在池中创建线程的函数。

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CThreadPool::CThreadPool](#cthreadpool)|线程池的构造函数。|
|[CThreadPool:: ~ CThreadPool](#dtor)|线程池的析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CThreadPool::AddRef](#addref)|实现`IUnknown::AddRef`。|
|[CThreadPool::GetNumThreads](#getnumthreads)|调用此方法以获取池中的线程数。|
|[CThreadPool::GetQueueHandle](#getqueuehandle)|调用此方法以获取用于队列工作项的 IO 完成端口的句柄。|
|[CThreadPool::GetSize](#getsize)|调用此方法以获取池中的线程数。|
|[CThreadPool::GetTimeout](#gettimeout)|调用此方法以获取最长时间以毫秒为单位，线程池将等待一个线程来关闭的情况下。|
|[CThreadPool::Initialize](#initialize)|调用此方法来初始化线程池。|
|[CThreadPool::QueryInterface](#queryinterface)|实现`IUnknown::QueryInterface`。|
|[CThreadPool::QueueRequest](#queuerequest)|调用此方法以将工作项要由线程池中排队。|
|[CThreadPool::Release](#release)|实现`IUnknown::Release`。|
|[CThreadPool::SetSize](#setsize)|调用此方法以设置在池中的线程数。|
|[CThreadPool::SetTimeout](#settimeout)|调用此方法，以毫秒为单位，线程池将等待一个线程来关闭的情况下设置最长的时间。|
|[CThreadPool::Shutdown](#shutdown)|调用此方法以关闭该线程池。|

## <a name="remarks"></a>备注

池中的线程创建和销毁时初始化、 调整大小，或关闭的情况下该池。 类的实例*辅助*将在池中每个工作线程的堆栈上创建。 每个实例将实时线程的生存期内。

创建一个线程后立即*辅助角色*::`Initialize`将与该线程关联的对象上调用。 之前的某个线程，析构*辅助角色*::`Terminate`将调用。 这两种方法必须接受**void** <strong>\*</strong>参数。 此参数的值传递给线程池通过*pvWorkerParam*的参数[CThreadPool::Initialize](#initialize)。

工作线程时有可用的工作项队列和辅助角色线程中工作，将提取队列并调用某一项`Execute`方法*辅助*该线程的对象。 三个项然后传递给该方法： 从队列中相同的项`pvWorkerParam`传递给*辅助角色*::`Initialize`并*辅助*:: `Terminate`，和指向[OVERLAPPED](/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped)结构用于 IO 完成端口队列。

*辅助角色*类声明了将通过提供一个 typedef，线程池排队的项的类型*辅助*:: `RequestType`。 此类型必须能够与 ULONG_PTR 要强制转换。

举例*辅助角色*类是[CNonStatelessWorker 类](../../atl/reference/cnonstatelessworker-class.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IUnknown`

[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)

`CThreadPool`

## <a name="requirements"></a>要求

**标头：** atlutil.h

##  <a name="addref"></a>  CThreadPool::AddRef

实现`IUnknown::AddRef`。

```
ULONG STDMETHODCALLTYPE AddRef() throw();
```

### <a name="return-value"></a>返回值

始终返回 1。

### <a name="remarks"></a>备注

此类未实现使用引用计数的生存期控件。

##  <a name="cthreadpool"></a>  CThreadPool::CThreadPool

线程池的构造函数。

```
CThreadPool() throw();
```

### <a name="remarks"></a>备注

初始化到 ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT 的超时值。 默认时间为 36 秒。 如有必要，可以包括 atlutil.h 之前定义此符号自己正整数值。

##  <a name="dtor"></a>  CThreadPool:: ~ CThreadPool

线程池的析构函数。

```
~CThreadPool() throw();
```

### <a name="remarks"></a>备注

调用[CThreadPool::Shutdown](#shutdown)。

##  <a name="getnumthreads"></a>  CThreadPool::GetNumThreads

调用此方法以获取池中的线程数。

```
int GetNumThreads() throw();
```

### <a name="return-value"></a>返回值

返回在池中的线程数。

##  <a name="getqueuehandle"></a>  CThreadPool::GetQueueHandle

调用此方法以获取用于队列工作项的 IO 完成端口的句柄。

```
HANDLE GetQueueHandle() throw();
```

### <a name="return-value"></a>返回值

如果尚未初始化线程池，返回的队列句柄或为 NULL。

##  <a name="getsize"></a>  CThreadPool::GetSize

调用此方法以获取池中的线程数。

```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```

### <a name="parameters"></a>参数

*pnNumThreads*  
[out]，如果成功，接收变量的线程数在池中的地址。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

##  <a name="gettimeout"></a>  CThreadPool::GetTimeout

调用此方法以获取最长时间以毫秒为单位，线程池将等待一个线程来关闭的情况下。

```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```

### <a name="parameters"></a>参数

*pdwMaxWait*  
[out]成功后，接收的最长时间以毫秒为单位，线程池将等待一个线程来关闭的情况下的变量的地址。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

此超时值由[CThreadPool::Shutdown](#shutdown)如果任何其他值不提供给该方法。

##  <a name="initialize"></a>  CThreadPool::Initialize

调用此方法来初始化线程池。

```
HRESULT Initialize(
    void* pvWorkerParam = NULL,
    int nNumThreads = 0,
    DWORD dwStackSize = 0,
    HANDLE hCompletion = INVALID_HANDLE_VALUE) throw();
```

### <a name="parameters"></a>参数

*pvWorkerParam*  
辅助参数传递给辅助线程对象`Initialize`， `Execute`，和`Terminate`方法。

*nNumThreads*  
请求的池中的线程数。

如果*nNumThreads*是负数，其绝对值的数值将乘以中要获取的线程总数的计算机的处理器数。

如果*nNumThreads*为零，ATLS_DEFAULT_THREADSPERPROC 将乘以中要获取的线程总数的计算机的处理器数。  默认值为每个处理器的 2 个线程。 如有必要，可以包括 atlutil.h 之前定义此符号自己正整数值。

*dwStackSize*  
在池中每个线程堆栈大小。

*hCompletion*  
若要将与完成端口相关联的对象的句柄。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

##  <a name="queryinterface"></a>  CThreadPool::QueryInterface

实现`IUnknown::QueryInterface`。

```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```

### <a name="remarks"></a>备注

此类的对象可以成功完成的查询`IUnknown`并[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)接口。

##  <a name="queuerequest"></a>  CThreadPool::QueueRequest

调用此方法以将工作项要由线程池中排队。

```
BOOL QueueRequest(Worker::RequestType request) throw();
```

### <a name="parameters"></a>参数

*请求*  
要排入队列的请求。

### <a name="return-value"></a>返回值

如果成功，则返回 TRUE FALSE 失败。

### <a name="remarks"></a>备注

此方法将工作项添加到队列。 在池中的线程选择项从队列中接收它们的顺序。

##  <a name="release"></a>  CThreadPool::Release

实现`IUnknown::Release`。

```
ULONG STDMETHODCALLTYPE Release() throw();
```

### <a name="return-value"></a>返回值

始终返回 1。

### <a name="remarks"></a>备注

此类未实现使用引用计数的生存期控件。

##  <a name="setsize"></a>  CThreadPool::SetSize

调用此方法以设置在池中的线程数。

```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```

### <a name="parameters"></a>参数

*nNumThreads*  
请求的池中的线程数。

如果*nNumThreads*是负数，其绝对值的数值将乘以中要获取的线程总数的计算机的处理器数。

如果*nNumThreads*为零，ATLS_DEFAULT_THREADSPERPROC 将乘以中要获取的线程总数的计算机的处理器数。 默认值为每个处理器的 2 个线程。 如有必要，可以包括 atlutil.h 之前定义此符号自己正整数值。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

如果指定的线程数小于当前池中的线程数，该对象放入关闭消息要拾取等待线程的队列。 当等待线程中提取从队列消息时，则会通知线程池，并退出线程过程。 重复此过程，直到池中的线程数达到指定的数目或由指定的时间内没有线程已退出[GetTimeout](#gettimeout)/ [SetTimeout](#settimeout)。 在此情况下该方法将返回一个 HRESULT，对应于 WAIT_TIMEOUT 和取消挂起的关闭消息。

##  <a name="settimeout"></a>  CThreadPool::SetTimeout

调用此方法，以毫秒为单位，线程池将等待一个线程来关闭的情况下设置最长的时间。

```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```

### <a name="parameters"></a>参数

*dwMaxWait*  
以毫秒为单位，线程池将等待一个线程来关闭请求的最大时间。

### <a name="return-value"></a>返回值

返回成功，则为 S_OK 或失败时的错误 HRESULT。

### <a name="remarks"></a>备注

超时值初始化为 ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT。 默认时间为 36 秒。 如有必要，可以包括 atlutil.h 之前定义此符号自己正整数值。

请注意， *dwMaxWait*是关闭的情况下有一个线程池将等待的时间。 无法使从池中删除多个线程的最长时间可能略小于*dwMaxWait*乘以的线程数。

##  <a name="shutdown"></a>  CThreadPool::Shutdown

调用此方法以关闭该线程池。

```
void Shutdown(DWORD dwMaxWait = 0) throw();
```

### <a name="parameters"></a>参数

*dwMaxWait*  
以毫秒为单位，线程池将等待一个线程来关闭请求的最大时间。 如果提供 0 或空值，则此方法将使用设置的超时[CThreadPool::SetTimeout](#settimeout)。

### <a name="remarks"></a>备注

此方法将池中发布的全部线程的关闭请求。 如果在超时到期，则此方法将调用[TerminateThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-terminatethread)上不存在任何线程。 从类的析构函数自动调用此方法。

## <a name="see-also"></a>请参阅

[IThreadPoolConfig 接口](../../atl/reference/ithreadpoolconfig-interface.md)   
[DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)   
[类](../../atl/reference/atl-classes.md)
