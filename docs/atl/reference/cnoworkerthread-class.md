---
title: "CNoWorkerThread 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CNoWorkerThread
- ATL.CNoWorkerThread
- CNoWorkerThread
dev_langs:
- C++
helpviewer_keywords:
- CNoWorkerThread class
ms.assetid: 29f06bae-b658-4aac-9c14-331e996d25d1
caps.latest.revision: 21
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
ms.openlocfilehash: 4c38d778849a31d55a657fc1022c2e9f4a370eec
ms.lasthandoff: 02/24/2017

---
# <a name="cnoworkerthread-class"></a>CNoWorkerThread 类
使用此类的参数作为`MonitorClass`到如果你想要禁用动态缓存维护的缓存类的模板参数。  
  
> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类及其成员。  
  
## <a name="syntax"></a>语法  
  
```
class CNoWorkerThread
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CNoWorkerThread::AddHandle](#addhandle)|非功能上的等同于[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。|  
|[CNoWorkerThread::AddTimer](#addtimer)|非功能上的等同于[CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer)。|  
|[CNoWorkerThread::GetThreadHandle](#getthreadhandle)|非功能上的等同于[CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle)。|  
|[CNoWorkerThread::GetThreadId](#getthreadid)|非功能上的等同于[CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid)。|  
|[CNoWorkerThread::Initialize](#initialize)|非功能上的等同于[CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize)。|  
|[CNoWorkerThread::RemoveHandle](#removehandle)|非功能上的等同于[CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle)。|  
|[CNoWorkerThread::Shutdown](#shutdown)|非功能上的等同于[CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown)。|  
  
## <a name="remarks"></a>备注  
 此类提供相同的公用界面[CWorkerThread](../../atl/reference/cworkerthread-class.md)。 此接口应由提供`MonitorClass`缓存类模板参数。  
  
 在此类方法的实现不执行任何操作。 始终返回一个 HRESULT，它的方法返回 S_OK，并始终返回一个句柄或线程 ID 的方法会返回 0。  
  
## <a name="requirements"></a>要求  
 **标头︰** atlutil.h  
  
##  <a name="a-nameaddhandlea--cnoworkerthreadaddhandle"></a><a name="addhandle"></a>CNoWorkerThread::AddHandle  
 非功能上的等同于[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。  
  
```
HRESULT AddHandle(HANDLE /* hObject
 */,
    IWorkerThreadClient* /* pClient
 */,
    DWORD_PTR /* dwParam
 */) throw();
```  
  
### <a name="return-value"></a>返回值  
 始终返回，则为 S_OK。  
  
### <a name="remarks"></a>备注  
 此类提供的实现没有任何影响。  
  
##  <a name="a-nameaddtimera--cnoworkerthreadaddtimer"></a><a name="addtimer"></a>CNoWorkerThread::AddTimer  
 非功能上的等同于[CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer)。  
  
```
HRESULT AddTimer(DWORD /* dwInterval
 */,
    IWorkerThreadClient* /* pClient
 */,
    DWORD_PTR /* dwParam
 */,
    HANDLE* /* phTimer
 */) throw();
```  
  
### <a name="return-value"></a>返回值  
 始终返回，则为 S_OK。  
  
### <a name="remarks"></a>备注  
 此类提供的实现没有任何影响。  
  
##  <a name="a-namegetthreadhandlea--cnoworkerthreadgetthreadhandle"></a><a name="getthreadhandle"></a>CNoWorkerThread::GetThreadHandle  
 非功能上的等同于[CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle)。  
  
```
HANDLE GetThreadHandle() throw();
```  
  
### <a name="return-value"></a>返回值  
 始终返回 NULL。  
  
### <a name="remarks"></a>备注  
 此类提供的实现没有任何影响。  
  
##  <a name="a-namegetthreadida--cnoworkerthreadgetthreadid"></a><a name="getthreadid"></a>CNoWorkerThread::GetThreadId  
 非功能上的等同于[CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid)。  
  
```
DWORD GetThreadId() throw();
```  
  
### <a name="return-value"></a>返回值  
 始终返回 0。  
  
### <a name="remarks"></a>备注  
 此类提供的实现没有任何影响。  
  
##  <a name="a-nameinitializea--cnoworkerthreadinitialize"></a><a name="initialize"></a>CNoWorkerThread::Initialize  
 非功能上的等同于[CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize)。  
  
```
HRESULT Initialize() throw();
```  
  
### <a name="return-value"></a>返回值  
 始终返回，则为 S_OK。  
  
### <a name="remarks"></a>备注  
 此类提供的实现没有任何影响。  
  
##  <a name="a-nameremovehandlea--cnoworkerthreadremovehandle"></a><a name="removehandle"></a>CNoWorkerThread::RemoveHandle  
 非功能上的等同于[CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle)。  
  
```
HRESULT RemoveHandle(HANDLE /* hObject
 */) throw();
```  
  
### <a name="return-value"></a>返回值  
 始终返回，则为 S_OK。  
  
### <a name="remarks"></a>备注  
 此类提供的实现没有任何影响。  
  
##  <a name="a-nameshutdowna--cnoworkerthreadshutdown"></a><a name="shutdown"></a>CNoWorkerThread::Shutdown  
 非功能上的等同于[CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown)。  
  
```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```  
  
### <a name="return-value"></a>返回值  
 始终返回，则为 S_OK。  
  
### <a name="remarks"></a>备注  
 此类提供的实现没有任何影响。

