---
title: "CWorkerThread 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CWorkerThread class
ms.assetid: be79a832-1345-4a36-a13e-a406cc65286f
caps.latest.revision: 24
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 25d102e7e47898ee2f93326756b3d50e8bb3bbff
ms.lasthandoff: 04/01/2017

---
# <a name="cworkerthread-class"></a>CWorkerThread 类
此类创建一个工作线程或使用一个现有，等待上一个或多个内核对象句柄，并在其中一个的句柄处于有信号状态时执行指定的客户端函数。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
template <class ThreadTraits = DefaultThreadTraits>  
class CWorkerThread
```  
  
#### <a name="parameters"></a>参数  
 `ThreadTraits`  
 类，用于提供线程创建函数，如[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)或[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)。  
  
## <a name="members"></a>成员  
  
### <a name="protected-structures"></a>受保护的结构  
  
|名称|描述|  
|----------|-----------------|  
|`WorkerClientEntry`||  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CWorkerThread::CWorkerThread](#cworkerthread)|工作线程构造函数。|  
|[CWorkerThread:: ~ CWorkerThread](#dtor)|工作线程析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CWorkerThread::AddHandle](#addhandle)|调用此方法以将可等待对象的句柄添加到工作线程由维护的列表。|  
|[CWorkerThread::AddTimer](#addtimer)|调用此方法以将定期可等待计时器添加到工作线程由维护的列表。|  
|[CWorkerThread::GetThreadHandle](#getthreadhandle)|调用此方法以获取工作线程的线程句柄。|  
|[CWorkerThread::GetThreadId](#getthreadid)|调用此方法以获取工作线程的线程 ID。|  
|[CWorkerThread::Initialize](#initialize)|调用此方法以初始化工作线程。|  
|[CWorkerThread::RemoveHandle](#removehandle)|调用此方法以从可等待对象的列表中删除一个句柄。|  
|[CWorkerThread::Shutdown](#shutdown)|调用此方法来关闭辅助线程。|  
  
## <a name="remarks"></a>备注  
  
### <a name="to-use-cworkerthread"></a>若要使用 CWorkerThread  
  
1.  创建此类的实例。  
  
2.  调用[CWorkerThread::Initialize](#initialize)。  
  
3.  调用[CWorkerThread::AddHandle](#addhandle)内核对象和一个指向的实现的句柄与[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)。  
  
     - 或 -  
  
     调用[CWorkerThread::AddTimer](#addtimer)用一个指针指向的实现[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)。  
  
4.  实现[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)采取某种操作时的句柄或计时器处于有信号状态。  
  
5.  若要从可等待对象列表中移除一个对象，调用[CWorkerThread::RemoveHandle](#removehandle)。  
  
6.  若要终止线程，调用[CWorkerThread::Shutdown](#shutdown)。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlutil.h  
  
##  <a name="addhandle"></a>CWorkerThread::AddHandle  
 调用此方法以将可等待对象的句柄添加到工作线程由维护的列表。  
  
```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```  
  
### <a name="parameters"></a>参数  
 `hObject`  
 可等待对象句柄。  
  
 `pClient`  
 将指针与[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)接口在句柄处于有信号状态时要调用的对象上。  
  
 `dwParam`  
 参数传递给[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)时句柄处于有信号状态。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)将通过调用`pClient`时该句柄， `hObject`，处于有信号状态。  
  
##  <a name="addtimer"></a>CWorkerThread::AddTimer  
 调用此方法以将定期可等待计时器添加到工作线程由维护的列表。  
  
```
HRESULT AddTimer(
    DWORD dwInterval,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam,
    HANDLE* phTimer) throw();
```  
  
### <a name="parameters"></a>参数  
 *dwInterval*  
 以毫秒为单位指定的计时器的期限。  
  
 `pClient`  
 将指针与[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)接口在句柄处于有信号状态时要调用的对象上。  
  
 `dwParam`  
 参数传递给[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)时句柄处于有信号状态。  
  
 `phTimer`  
 [out]成功时，接收新创建的计时器的句柄的句柄变量的地址。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)将通过调用`pClient`向计时器发出信号。  
  
 将从计时器句柄传递`phTimer`到[CWorkerThread::RemoveHandle](#removehandle)关闭计时器。  
  
##  <a name="cworkerthread"></a>CWorkerThread::CWorkerThread  
 构造函数。  
  
```
CWorkerThread() throw();
```  
  
##  <a name="dtor"></a>CWorkerThread:: ~ CWorkerThread  
 析构函数。  
  
```
~CWorkerThread() throw();
```  
  
### <a name="remarks"></a>备注  
 调用[CWorkerThread::Shutdown](#shutdown)。  
  
##  <a name="getthreadhandle"></a>CWorkerThread::GetThreadHandle  
 调用此方法以获取工作线程的线程句柄。  
  
```
HANDLE GetThreadHandle() throw();
```  
  
### <a name="return-value"></a>返回值  
 如果尚未初始化工作线程，则返回的线程句柄或为 NULL。  
  
##  <a name="getthreadid"></a>CWorkerThread::GetThreadId  
 调用此方法以获取工作线程的线程 ID。  
  
```
DWORD GetThreadId() throw();
```  
  
### <a name="return-value"></a>返回值  
 如果尚未初始化工作线程，则返回的线程 ID 或为 NULL。  
  
##  <a name="initialize"></a>CWorkerThread::Initialize  
 调用此方法以初始化工作线程。  
  
```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```  
  
### <a name="parameters"></a>参数  
 `pThread`  
 现有的工作线程。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 应调用此方法以初始化对象，在创建后或在调用[CWorkerThread::Shutdown](#shutdown)。  
  
 若要包含两个或多个`CWorkerThread`对象使用相同的工作线程，初始化其中一个未传入任何自变量然后将指针传递给该对象`Initialize`的其他方法。 用于初始化它们的对象之前应关闭使用指针初始化的对象。  
  
 请参阅[CWorkerThread::Shutdown](#shutdown)有关使用指向现有对象的指针初始化时，如何更改该方法的行为的信息。  
  
##  <a name="removehandle"></a>CWorkerThread::RemoveHandle  
 调用此方法以从可等待对象的列表中删除一个句柄。  
  
```
HRESULT RemoveHandle(HANDLE hObject) throw();
```  
  
### <a name="parameters"></a>参数  
 `hObject`  
 要删除的句柄。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 当删除句柄[IWorkerThreadClient::CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle)将在传递到关联的对象上调用[AddHandle](#addhandle)。 如果此调用失败，`CWorkerThread`将调用 Windows [CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211)句柄上的函数。  
  
##  <a name="shutdown"></a>CWorkerThread::Shutdown  
 调用此方法来关闭辅助线程。  
  
```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```  
  
### <a name="parameters"></a>参数  
 `dwWait`  
 以毫秒为单位等待要关闭的工作线程时间。 ATL_WORKER_THREAD_WAIT 默认值为 10 秒。 如有必要，您可以在包括 atlutil.h 之前定义此符号自己值。 
  
### <a name="return-value"></a>返回值  
 返回成功，则在失败时，如的错误 HRESULT，则为 S_OK 超时值， `dwWait`，超出。  
  
### <a name="remarks"></a>备注  
 若要重用该对象，调用[CWorkerThread::Initialize](#initialize)后调用此方法。  
  
 请注意，调用**关闭**初始化用一个指针指向另一个对象上`CWorkerThread`对象有影响，并且始终返回，则为 S_OK。  
  
## <a name="see-also"></a>另请参阅  
 [DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)   
 [类](../../atl/reference/atl-classes.md)   
 [多线程处理︰ 创建辅助线程](../../parallel/multithreading-creating-worker-threads.md)   
 [IWorkerThreadClient 接口](../../atl/reference/iworkerthreadclient-interface.md)

