---
title: CWorkerThread 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e29bf1c8265a0d92200cda2704b750dfd8db3d6f
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37885635"
---
# <a name="cworkerthread-class"></a>CWorkerThread 类
此类创建工作线程或使用现有工作区，等待上一个或多个内核对象句柄，并发出一个句柄的信号时执行指定的客户端函数。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。  
  
## <a name="syntax"></a>语法  
  
```
template <class ThreadTraits = DefaultThreadTraits>  
class CWorkerThread
```  
  
#### <a name="parameters"></a>参数  
 *ThreadTraits*  
 类提供线程创建函数，如[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)或[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)。  
  
## <a name="members"></a>成员  
  
### <a name="protected-structures"></a>受保护的结构  
  
|name|描述|  
|----------|-----------------|  
|`WorkerClientEntry`||  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CWorkerThread::CWorkerThread](#cworkerthread)|对于工作线程构造函数。|  
|[CWorkerThread:: ~ CWorkerThread](#dtor)|对于工作线程析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CWorkerThread::AddHandle](#addhandle)|调用此方法以将可等待对象的句柄添加到由工作线程维护的列表。|  
|[CWorkerThread::AddTimer](#addtimer)|调用此方法将定期的可等待计时器添加到由工作线程维护的列表。|  
|[CWorkerThread::GetThreadHandle](#getthreadhandle)|调用此方法以获取工作线程的线程句柄。|  
|[CWorkerThread::GetThreadId](#getthreadid)|调用此方法以获取工作线程的线程 ID。|  
|[CWorkerThread::Initialize](#initialize)|调用此方法来初始化工作线程。|  
|[CWorkerThread::RemoveHandle](#removehandle)|调用此方法以从可等待对象的列表中删除一个句柄。|  
|[CWorkerThread::Shutdown](#shutdown)|调用此方法以关闭该工作线程。|  
  
## <a name="remarks"></a>备注  
  
### <a name="to-use-cworkerthread"></a>若要使用 CWorkerThread  
  
1.  创建此类的实例。  
  
2.  调用[CWorkerThread::Initialize](#initialize)。  
  
3.  调用[CWorkerThread::AddHandle](#addhandle)使用的内核对象以及指向的实现的句柄[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)。  
  
     - 或 -  
  
     调用[CWorkerThread::AddTimer](#addtimer)用一个指针指向的实现[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)。  
  
4.  实现[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)发出信号的句柄或计时器时采取某种操作。  
  
5.  若要从可等待对象的列表中删除一个对象，调用[CWorkerThread::RemoveHandle](#removehandle)。  
  
6.  若要终止该线程，调用[CWorkerThread::Shutdown](#shutdown)。  
  
## <a name="requirements"></a>要求  
 **标头：** atlutil.h  
  
##  <a name="addhandle"></a>  CWorkerThread::AddHandle  
 调用此方法以将可等待对象的句柄添加到由工作线程维护的列表。  
  
```
HRESULT AddHandle(
    HANDLE hObject,
    IWorkerThreadClient* pClient,
    DWORD_PTR dwParam) throw();
```  
  
### <a name="parameters"></a>参数  
 *hObject*  
 可等待对象句柄。  
  
 *pClient*  
 指向指针[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)句柄发出信号时要调用的对象上的接口。  
  
 *dwParam*  
 参数将传递给[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)时发出信号的句柄。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)将通过调用*pClient*时，句柄*hObject*，发出信号。  
  
##  <a name="addtimer"></a>  CWorkerThread::AddTimer  
 调用此方法将定期的可等待计时器添加到由工作线程维护的列表。  
  
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
  
 *pClient*  
 指向指针[IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)句柄发出信号时要调用的对象上的接口。  
  
 *dwParam*  
 参数将传递给[IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)时发出信号的句柄。  
  
 *phTimer*  
 [out]成功后，接收到新创建的计时器的句柄的句柄变量的地址。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 [IWorkerThreadClient::Execute](../../atl/reference/iworkerthreadclient-interface.md#execute)将通过调用*pClient*计时器时发出信号。  
  
 将从计时器句柄传递*phTimer*到[CWorkerThread::RemoveHandle](#removehandle)关闭计时器。  
  
##  <a name="cworkerthread"></a>  CWorkerThread::CWorkerThread  
 构造函数。  
  
```
CWorkerThread() throw();
```  
  
##  <a name="dtor"></a>  CWorkerThread:: ~ CWorkerThread  
 析构函数。  
  
```
~CWorkerThread() throw();
```  
  
### <a name="remarks"></a>备注  
 调用[CWorkerThread::Shutdown](#shutdown)。  
  
##  <a name="getthreadhandle"></a>  CWorkerThread::GetThreadHandle  
 调用此方法以获取工作线程的线程句柄。  
  
```
HANDLE GetThreadHandle() throw();
```  
  
### <a name="return-value"></a>返回值  
 如果尚未初始化工作线程，返回的线程句柄或为 NULL。  
  
##  <a name="getthreadid"></a>  CWorkerThread::GetThreadId  
 调用此方法以获取工作线程的线程 ID。  
  
```
DWORD GetThreadId() throw();
```  
  
### <a name="return-value"></a>返回值  
 如果尚未初始化工作线程，返回线程 ID 或 NULL。  
  
##  <a name="initialize"></a>  CWorkerThread::Initialize  
 调用此方法来初始化工作线程。  
  
```
HRESULT Initialize() throw();

HRESULT Initialize(CWorkerThread<ThreadTraits>* pThread) throw();
```  
  
### <a name="parameters"></a>参数  
 *pThread*  
 现有的工作线程。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 应调用此方法以初始化对象，在创建后或在调用[CWorkerThread::Shutdown](#shutdown)。  
  
 若要有两个或多个`CWorkerThread`对象使用同一个工作线程，初始化未传入任何参数然后将指针传递给该对象的其中一个`Initialize`的其他方法。 用来对其进行初始化的对象之前，应该先关闭使用指针初始化的对象。  
  
 请参阅[CWorkerThread::Shutdown](#shutdown)上时使用的现有对象的指针初始化该方法的行为的更改的信息。  
  
##  <a name="removehandle"></a>  CWorkerThread::RemoveHandle  
 调用此方法以从可等待对象的列表中删除一个句柄。  
  
```
HRESULT RemoveHandle(HANDLE hObject) throw();
```  
  
### <a name="parameters"></a>参数  
 *hObject*  
 要删除的句柄。  
  
### <a name="return-value"></a>返回值  
 返回成功，则为 S_OK 或失败时的错误 HRESULT。  
  
### <a name="remarks"></a>备注  
 删除句柄的时间[IWorkerThreadClient::CloseHandle](../../atl/reference/iworkerthreadclient-interface.md#closehandle)将传递到关联的对象上调用[AddHandle](#addhandle)。 如果此调用失败，`CWorkerThread`将调用 Windows [CloseHandle](http://msdn.microsoft.com/library/windows/desktop/ms724211)句柄上的函数。  
  
##  <a name="shutdown"></a>  CWorkerThread::Shutdown  
 调用此方法以关闭该工作线程。  
  
```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```  
  
### <a name="parameters"></a>参数  
 *dwWait*  
 以毫秒为单位工作线程，若要关闭的情况下，等待时间。 ATL_WORKER_THREAD_WAIT 默认值为 10 秒。 如有必要，可以包括 atlutil.h 之前定义此符号自己的值。 
  
### <a name="return-value"></a>返回值  
 成功，则在失败时，例如，如果错误 HRESULT 返回 S_OK 的超时值， *dwWait*，超过了。  
  
### <a name="remarks"></a>备注  
 若要重新使用对象，调用[CWorkerThread::Initialize](#initialize)后调用此方法。  
  
 请注意，调用`Shutdown`使用到另一个指针初始化的对象上`CWorkerThread`对象不起作用，并始终返回 S_OK。  
  
## <a name="see-also"></a>请参阅  
 [DefaultThreadTraits](atl-typedefs.md#defaultthreadtraits)   
 [类](../../atl/reference/atl-classes.md)   
 [多线程处理： 创建辅助线程](../../parallel/multithreading-creating-worker-threads.md)   
 [IWorkerThreadClient 接口](../../atl/reference/iworkerthreadclient-interface.md)
