---
title: "CThreadPool 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: b3c944958ba73240131fba33db95dbc20ec9bec8
ms.contentlocale: zh-cn
ms.lasthandoff: 03/31/2017

---
# <a name="cthreadpool-class"></a>CThreadPool 类
此类提供处理的工作项队列的辅助线程的池。  
  
## <a name="syntax"></a>语法  
  
```
template <class Worker, class ThreadTraits = DefaultThreadTraits>  
class CThreadPool : public IThreadPoolConfig
```  
  
#### <a name="parameters"></a>参数  
 *辅助进程*  
 与类[辅助 archetype](../../atl/reference/worker-archetype.md)提供用于处理在线程池中排队项的工作的代码。  
  
 `ThreadTraits`  
 类，用于提供用来在池中创建线程的函数。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CThreadPool::CThreadPool](#cthreadpool)|线程池的构造函数。|  
|[CThreadPool:: ~ CThreadPool](#dtor)|线程池的析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CThreadPool::AddRef](#addref)|实现`IUnknown::AddRef`。|  
|[CThreadPool::GetNumThreads](#getnumthreads)|调用此方法以获取池中的线程数。|  
|[CThreadPool::GetQueueHandle](#getqueuehandle)|调用此方法以获取使用工作项排队的 IO 完成端口的句柄。|  
|[CThreadPool::GetSize](#getsize)|调用此方法以获取池中的线程数。|  
|[CThreadPool::GetTimeout](#gettimeout)|调用此方法以获取的最长时间以毫秒为单位，线程池将等待线程关闭。|  
|[CThreadPool::Initialize](#initialize)|调用此方法以初始化线程池。|  
|[CThreadPool::QueryInterface](#queryinterface)|实现**iunknown:: Queryinterface**。|  
|[CThreadPool::QueueRequest](#queuerequest)|调用此方法以将工作项排队由在池中的线程处理。|  
|[CThreadPool::Release](#release)|实现`IUnknown::Release`。|  
|[CThreadPool::SetSize](#setsize)|调用此方法以设置池中的线程数。|  
|[CThreadPool::SetTimeout](#settimeout)|调用此方法以设置的最长时间以毫秒为单位，线程池将等待线程关闭。|  
|[CThreadPool::Shutdown](#shutdown)|调用此方法来关闭线程池。|  
  
## <a name="remarks"></a>备注  
 线程池中创建和销毁时初始化、 调整大小，或关闭该池。 类的实例*辅助*将在池中每个工作线程的堆栈上创建。 每个实例将实时线程的生存期内。  
  
 在创建线程后立即*辅助*::`Initialize`将在与该线程关联的对象上调用。 立即之前的线程，析构*辅助*::`Terminate`将调用。 这两种方法必须接受**void\***自变量。 此自变量的值传递给该线程池通过`pvWorkerParam`参数[CThreadPool::Initialize](#initialize)。  
  
 当在工作项队列和辅助线程可用于工作时，工作线程将请求的队列和调用某一项**执行**方法*辅助*该线程的对象。 三个项然后传递到方法︰ 从队列中，相同项`pvWorkerParam`传递给*辅助*::`Initialize`和*辅助*:: `Terminate`，和一个指向[OVERLAPPED](http://msdn.microsoft.com/library/windows/desktop/ms684342)用于 IO 完成端口队列的结构。  
  
 *辅助*类声明了将通过提供 typedef，在线程池中排队项的类型*辅助*:: `RequestType`。 此类型必须能够正在间来回转换**ULONG_PTR**。  
  
 一个示例*辅助*类是[CNonStatelessWorker 类](../../atl/reference/cnonstatelessworker-class.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IUnknown`  
  
 [IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)  
  
 `CThreadPool`  
  
## <a name="requirements"></a>要求  
 **标头︰** atlutil.h  
  
##  <a name="addref"></a>CThreadPool::AddRef  
 实现`IUnknown::AddRef`。  
  
```
ULONG STDMETHODCALLTYPE AddRef() throw();
```  
  
### <a name="return-value"></a>返回值  
 始终返回 1。  
  
### <a name="remarks"></a>备注  
 此类不实现生存期控件使用引用计数。  
  
##  <a name="cthreadpool"></a>CThreadPool::CThreadPool  
 线程池的构造函数。  
  
```
CThreadPool() throw();
```  
  
### <a name="remarks"></a>备注  
 初始化到的超时值`ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT`。 默认时间为 36 秒。 如有必要，你可以在包括 atlutil.h 之前定义此符号自己正整数值。  
  
##  <a name="dtor"></a>CThreadPool:: ~ CThreadPool  
 线程池的析构函数。  
  
```
~CThreadPool() throw();
```  
  
### <a name="remarks"></a>备注  
 调用[CThreadPool::Shutdown](#shutdown)。  
  
##  <a name="getnumthreads"></a>CThreadPool::GetNumThreads  
 调用此方法以获取池中的线程数。  
  
```
int GetNumThreads() throw();
```  
  
### <a name="return-value"></a>返回值  
 返回在池中的线程数。  
  
##  <a name="getqueuehandle"></a>CThreadPool::GetQueueHandle  
 调用此方法以获取使用工作项排队的 IO 完成端口的句柄。  
  
```
HANDLE GetQueueHandle() throw();
```  
  
### <a name="return-value"></a>返回值  
 如果尚未初始化线程池，返回的队列句柄或为 NULL。  
  
##  <a name="getsize"></a>CThreadPool::GetSize  
 调用此方法以获取池中的线程数。  
  
```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```  
  
### <a name="parameters"></a>参数  
 `pnNumThreads`  
 [out]接收的变量，在成功时的线程数在池中的地址。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="gettimeout"></a>CThreadPool::GetTimeout  
 调用此方法以获取的最长时间以毫秒为单位，线程池将等待线程关闭。  
  
```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```  
  
### <a name="parameters"></a>参数  
 `pdwMaxWait`  
 [out]变量的成功时，接收的最长时间以毫秒为单位，线程池将等待线程关闭的地址。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 使用此超时值[CThreadPool::Shutdown](#shutdown)如果到该方法不提供任何其他值。  
  
##  <a name="initialize"></a>CThreadPool::Initialize  
 调用此方法以初始化线程池。  
  
```
HRESULT Initialize(
    void* pvWorkerParam = NULL,
    int nNumThreads = 0,
    DWORD dwStackSize = 0,
    HANDLE hCompletion = INVALID_HANDLE_VALUE) throw();
```  
  
### <a name="parameters"></a>参数  
 `pvWorkerParam`  
 辅助参数传递给辅助线程对象`Initialize`，**执行**，和`Terminate`方法。  
  
 `nNumThreads`  
 请求的池中的线程数。  
  
 如果`nNumThreads`为负，其绝对值的数值将乘以要获取的线程总数的机中的处理器数。  
  
 如果`nNumThreads`为零，`ATLS_DEFAULT_THREADSPERPROC`将乘以要获取的线程总数的机中的处理器数。  默认值为 2 个线程为每个处理器。 如有必要，你可以在包括 atlutil.h 之前定义此符号自己正整数值。
  
 `dwStackSize`  
 池中的每个线程堆栈大小。  
  
 *hCompletion*  
 要将与完成端口相关联的对象的句柄。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="queryinterface"></a>CThreadPool::QueryInterface  
 实现**iunknown:: Queryinterface**。  
  
```
HRESULT STDMETHODCALLTYPE QueryInterface(REFIID riid, void** ppv) throw();
```  
  
### <a name="remarks"></a>备注  
 此类的对象可以成功查询的**IUnknown**和[IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)接口。  
  
##  <a name="queuerequest"></a>CThreadPool::QueueRequest  
 调用此方法以将工作项排队由在池中的线程处理。  
  
```
BOOL QueueRequest(Worker::RequestType request) throw();
```  
  
### <a name="parameters"></a>参数  
 `request`  
 要进行排队的请求。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 此方法将工作项添加到队列。 池中的线程中接收它们的顺序选择从队列中移除的项。  
  
##  <a name="release"></a>CThreadPool::Release  
 实现`IUnknown::Release`。  
  
```
ULONG STDMETHODCALLTYPE Release() throw();
```  
  
### <a name="return-value"></a>返回值  
 始终返回 1。  
  
### <a name="remarks"></a>备注  
 此类不实现生存期控件使用引用计数。  
  
##  <a name="setsize"></a>CThreadPool::SetSize  
 调用此方法以设置池中的线程数。  
  
```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```  
  
### <a name="parameters"></a>参数  
 `nNumThreads`  
 请求的池中的线程数。  
  
 如果`nNumThreads`为负，其绝对值的数值将乘以要获取的线程总数的机中的处理器数。  
  
 如果`nNumThreads`为零，`ATLS_DEFAULT_THREADSPERPROC`将乘以要获取的线程总数的机中的处理器数。 默认值为 2 个线程为每个处理器。 如有必要，你可以在包括 atlutil.h 之前定义此符号自己正整数值。
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 如果指定的线程数小于当前池中的线程数，该对象会将关闭消息放在要拾取正在等待的线程的队列。 当正在等待的线程中提取消息从队列中移除时，则会通知线程池，并退出了线程过程。 重复此过程，直到池中的线程的总数达到指定的数量或任何线程已通过指定的时间内退出[GetTimeout](#gettimeout)/ [SetTimeout](#settimeout)。 在此情况下该方法将返回与对应的 HRESULT **WAIT_TIMEOUT**和取消挂起的关闭消息。  
  
##  <a name="settimeout"></a>CThreadPool::SetTimeout  
 调用此方法以设置的最长时间以毫秒为单位，线程池将等待线程关闭。  
  
```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```  
  
### <a name="parameters"></a>参数  
 `dwMaxWait`  
 以毫秒为单位，线程池将等待线程关闭请求的最大时间。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 超时初始化为`ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT`。 默认时间为 36 秒。 如有必要，你可以在包括 atlutil.h 之前定义此符号自己正整数值。 
  
 请注意，`dwMaxWait`是池将等待单线程来关闭的时间。 无法执行从池中删除多个线程的最长时间可能是略小于`dwMaxWait`的线程数的乘积。  
  
##  <a name="shutdown"></a>CThreadPool::Shutdown  
 调用此方法来关闭线程池。  
  
```
void Shutdown(DWORD dwMaxWait = 0) throw();
```  
  
### <a name="parameters"></a>参数  
 `dwMaxWait`  
 以毫秒为单位，线程池将等待线程关闭请求的最大时间。 如果提供 0 或空值，则此方法将使用设置的超时[CThreadPool::SetTimeout](#settimeout)。  
  
### <a name="remarks"></a>备注  
 此方法在池中发送到所有线程的关闭请求。 如果在超时到期，则此方法将调用[TerminateThread](http://msdn.microsoft.com/library/windows/desktop/ms686717)不存在任何线程上。 从类的析构函数自动调用此方法。  
  
## <a name="see-also"></a>另请参阅  
 [IThreadPoolConfig 接口](../../atl/reference/ithreadpoolconfig-interface.md)   
 [DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)   
 [类](../../atl/reference/atl-classes.md)

