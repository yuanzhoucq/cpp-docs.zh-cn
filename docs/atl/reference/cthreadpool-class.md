---
title: "CThreadPool 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 632514d03e7037ef42a1566462db5dec6f5cc1e5
ms.lasthandoff: 02/24/2017

---
# <a name="cthreadpool-class"></a>CThreadPool 类
此类提供处理的工作项队列的工作线程池。  
  
## <a name="syntax"></a>语法  
  
```
template <class Worker, class ThreadTraits = DefaultThreadTraits>  
class CThreadPool : public IThreadPoolConfig
```  
  
#### <a name="parameters"></a>参数  
 *辅助进程*  
 类符合[辅助原型](../../atl/reference/worker-archetype.md)提供用来处理的工作项排队线程池的代码。  
  
 `ThreadTraits`  
 类提供用来创建多个线程池中的函数。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CThreadPool::CThreadPool](#cthreadpool)|线程池的构造函数。|  
|[CThreadPool:: ~ CThreadPool](#dtor)|线程池析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CThreadPool::AddRef](#addref)|实现`IUnknown::AddRef`。|  
|[CThreadPool::GetNumThreads](#getnumthreads)|调用此方法以获取在池中的线程数。|  
|[CThreadPool::GetQueueHandle](#getqueuehandle)|调用此方法以获取使用工作项排队的 IO 完成端口的句柄。|  
|[CThreadPool::GetSize](#getsize)|调用此方法以获取在池中的线程数。|  
|[CThreadPool::GetTimeout](#gettimeout)|调用此方法以获取以毫秒为单位，线程池可以关闭一个线程将等待的最长时间。|  
|[CThreadPool::Initialize](#initialize)|调用此方法以初始化线程池。|  
|[CThreadPool::QueryInterface](#queryinterface)|实现**iunknown:: Queryinterface**。|  
|[CThreadPool::QueueRequest](#queuerequest)|调用此方法以在池中的线程来处理工作项目排队。|  
|[CThreadPool::Release](#release)|实现`IUnknown::Release`。|  
|[CThreadPool::SetSize](#setsize)|调用此方法以设置池中的线程数。|  
|[CThreadPool::SetTimeout](#settimeout)|调用此方法以设置以毫秒为单位，线程池可以关闭一个线程将等待的最长时间。|  
|[CThreadPool::Shutdown](#shutdown)|调用此方法来关闭线程池。|  
  
## <a name="remarks"></a>备注  
 池中的线程创建和销毁初始化、 调整大小时，或关闭的情况下该池时。 类的实例*工作人员*将在池中每个工作线程的堆栈上创建。 每个实例将实时线程的生存期内。  
  
 在创建线程后立即*工作人员*::`Initialize`将在与该线程关联的对象上调用。 之前的线程，析构*工作人员*::`Terminate`将被调用。 这两种方法必须接受**void\* **参数。 此参数的值传递给线程池通过`pvWorkerParam`参数[CThreadPool::Initialize](#initialize)。  
  
 当有可用的工作项队列和辅助线程中工作时，工作线程将获取队列并调用某一项**Execute**方法*工作人员*关于该主题的对象。 三个项然后传递给该方法︰ 从队列中相同的项`pvWorkerParam`传递给*工作人员*::`Initialize`和*工作人员*:: `Terminate`，和一个指向[OVERLAPPED](http://msdn.microsoft.com/library/windows/desktop/ms684342)结构用于 IO 完成端口队列。  
  
 *工作人员*类声明了将通过提供一个 typedef，线程池排队的项的类型*工作人员*:: `RequestType`。 此类型必须能够被间来回转换**ULONG_PTR**。  
  
 举例说明如何*工作人员*类是[CNonStatelessWorker 类](../../atl/reference/cnonstatelessworker-class.md)。  
  
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
 此类不实现生存期控制使用引用计数。  
  
##  <a name="cthreadpool"></a>CThreadPool::CThreadPool  
 线程池的构造函数。  
  
```
CThreadPool() throw();
```  
  
### <a name="remarks"></a>备注  
 初始化的超时值[ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT](http://msdn.microsoft.com/library/c1e660a7-d490-42af-bbe1-ded76e80cc10)。  
  
##  <a name="dtor"></a>CThreadPool:: ~ CThreadPool  
 线程池析构函数。  
  
```
~CThreadPool() throw();
```  
  
### <a name="remarks"></a>备注  
 调用[CThreadPool::Shutdown](#shutdown)。  
  
##  <a name="getnumthreads"></a>CThreadPool::GetNumThreads  
 调用此方法以获取在池中的线程数。  
  
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
 如果尚未初始化线程池，返回队列句柄或为空的。  
  
##  <a name="getsize"></a>CThreadPool::GetSize  
 调用此方法以获取在池中的线程数。  
  
```
HRESULT STDMETHODCALLTYPE GetSize(int* pnNumThreads) throw();
```  
  
### <a name="parameters"></a>参数  
 `pnNumThreads`  
 [out]接收的变量，在成功时的线程数在池中的地址。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
##  <a name="gettimeout"></a>CThreadPool::GetTimeout  
 调用此方法以获取以毫秒为单位，线程池可以关闭一个线程将等待的最长时间。  
  
```
HRESULT STDMETHODCALLTYPE GetTimeout(DWORD* pdwMaxWait) throw();
```  
  
### <a name="parameters"></a>参数  
 `pdwMaxWait`  
 [out]成功时，接收的最长时间以毫秒为单位，线程池将等到有线程，若要关闭的情况下，该变量的地址。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 使用此超时值[CThreadPool::Shutdown](#shutdown)如果任何其他值不提供给该方法。  
  
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
 要传递给辅助线程对象的工作人员参数`Initialize`， **Execute**，和`Terminate`方法。  
  
 `nNumThreads`  
 请求的池中的线程数。  
  
 如果`nNumThreads`是负数，其绝对值的数值将乘以要获取的线程总数的计算机中的处理器数。  
  
 如果`nNumThreads`为零， [ATLS_DEFAULT_THREADSPERPROC](http://msdn.microsoft.com/library/e0dcf107-72a9-4122-abb4-83c63aa7d571)将乘以要获取的线程总数的计算机中的处理器数。  
  
 `dwStackSize`  
 每个线程池中，堆栈大小。  
  
 *hCompletion*  
 要将与完成端口相关联的对象句柄。  
  
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
 调用此方法以在池中的线程来处理工作项目排队。  
  
```
BOOL QueueRequest(Worker::RequestType request) throw();
```  
  
### <a name="parameters"></a>参数  
 `request`  
 要进行排队的请求。  
  
### <a name="return-value"></a>返回值  
 如果成功，则返回 TRUE FALSE 失败。  
  
### <a name="remarks"></a>备注  
 此方法将工作项添加到队列。 池中的线程选取项从队列中接收它们的顺序。  
  
##  <a name="release"></a>CThreadPool::Release  
 实现`IUnknown::Release`。  
  
```
ULONG STDMETHODCALLTYPE Release() throw();
```  
  
### <a name="return-value"></a>返回值  
 始终返回 1。  
  
### <a name="remarks"></a>备注  
 此类不实现生存期控制使用引用计数。  
  
##  <a name="setsize"></a>CThreadPool::SetSize  
 调用此方法以设置池中的线程数。  
  
```
HRESULT STDMETHODCALLTYPE SetSizeint nNumThreads) throw();
```  
  
### <a name="parameters"></a>参数  
 `nNumThreads`  
 请求的池中的线程数。  
  
 如果`nNumThreads`是负数，其绝对值的数值将乘以要获取的线程总数的计算机中的处理器数。  
  
 如果`nNumThreads`为零， [ATLS_DEFAULT_THREADSPERPROC](http://msdn.microsoft.com/library/e0dcf107-72a9-4122-abb4-83c63aa7d571)将乘以要获取的线程总数的计算机中的处理器数。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 如果指定的线程数小于当前池中的线程数，该对象放入关闭消息要拾取正在等待的线程的队列。 当正在等待的线程中提取从队列消息时，则会通知线程池，并退出该线程过程。 重复此过程，直到池中的线程的总数达到指定的数量或任何线程都已由指定的时间内退出[GetTimeout](#gettimeout)/ [SetTimeout](#settimeout)。 在此情况下该方法将返回与对应的 HRESULT **WAIT_TIMEOUT**并且取消挂起的关闭消息。  
  
##  <a name="settimeout"></a>CThreadPool::SetTimeout  
 调用此方法以设置以毫秒为单位，线程池可以关闭一个线程将等待的最长时间。  
  
```
HRESULT STDMETHODCALLTYPE SetTimeout(DWORD dwMaxWait) throw();
```  
  
### <a name="parameters"></a>参数  
 `dwMaxWait`  
 以毫秒为单位，线程池可以关闭一个线程将等待请求的最大时间。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 超时值初始化为[ATLS_DEFAULT_THREADPOOLSHUTDOWNTIMEOUT](http://msdn.microsoft.com/library/c1e660a7-d490-42af-bbe1-ded76e80cc10)构造函数中。  
  
 请注意，`dwMaxWait`是该池将等待一个线程可以关闭的时间。 可能是要努力从池中删除多个线程的最长时间略小于`dwMaxWait`乘以线程数。  
  
##  <a name="shutdown"></a>CThreadPool::Shutdown  
 调用此方法来关闭线程池。  
  
```
void Shutdown(DWORD dwMaxWait = 0) throw();
```  
  
### <a name="parameters"></a>参数  
 `dwMaxWait`  
 以毫秒为单位，线程池可以关闭一个线程将等待请求的最大时间。 如果提供 0 或空值，则此方法将使用设置的超时[CThreadPool::SetTimeout](#settimeout)。  
  
### <a name="remarks"></a>备注  
 此方法将在池中中发布所有线程的关闭的请求。 如果在超时过期，则此方法将调用[TerminateThread](http://msdn.microsoft.com/library/windows/desktop/ms686717)不存在的任何线程上。 从类的析构函数自动调用此方法。  
  
## <a name="see-also"></a>另请参阅  
 [IThreadPoolConfig 接口](../../atl/reference/ithreadpoolconfig-interface.md)   
 [DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)   
 [类](../../atl/reference/atl-classes.md)

