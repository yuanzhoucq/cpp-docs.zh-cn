---
title: CNoWorkerThread 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread
- ATLUTIL/ATL::CNoWorkerThread::AddHandle
- ATLUTIL/ATL::CNoWorkerThread::AddTimer
- ATLUTIL/ATL::CNoWorkerThread::GetThreadHandle
- ATLUTIL/ATL::CNoWorkerThread::GetThreadId
- ATLUTIL/ATL::CNoWorkerThread::Initialize
- ATLUTIL/ATL::CNoWorkerThread::RemoveHandle
- ATLUTIL/ATL::CNoWorkerThread::Shutdown
dev_langs:
- C++
helpviewer_keywords:
- CNoWorkerThread class
ms.assetid: 29f06bae-b658-4aac-9c14-331e996d25d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 85e1962d10f274f4f8c35ba27cb05c41e8bf19cb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363079"
---
# <a name="cnoworkerthread-class"></a>CNoWorkerThread 类
使用此类的自变量作为`MonitorClass`如果你想要禁用动态缓存维护缓存类模板参数。  
  
> [!IMPORTANT]
>  此类及其成员无法在 Windows 运行时中执行的应用中使用。  
  
## <a name="syntax"></a>语法  
  
```
class CNoWorkerThread
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CNoWorkerThread::AddHandle](#addhandle)|非功能上的等效于[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。|  
|[CNoWorkerThread::AddTimer](#addtimer)|非功能上的等效于[CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer)。|  
|[CNoWorkerThread::GetThreadHandle](#getthreadhandle)|非功能上的等效于[CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle)。|  
|[CNoWorkerThread::GetThreadId](#getthreadid)|非功能上的等效于[CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid)。|  
|[CNoWorkerThread::Initialize](#initialize)|非功能上的等效于[CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize)。|  
|[CNoWorkerThread::RemoveHandle](#removehandle)|非功能上的等效于[CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle)。|  
|[CNoWorkerThread::Shutdown](#shutdown)|非功能上的等效于[CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown)。|  
  
## <a name="remarks"></a>备注  
 此类提供相同的公共接口[CWorkerThread](../../atl/reference/cworkerthread-class.md)。 此接口应由提供`MonitorClass`缓存类模板参数。  
  
 此类中的方法的实现不执行任何操作。 始终返回一个 HRESULT 的方法返回 S_OK，并始终返回句柄或线程 ID 的方法的返回 0。  
  
## <a name="requirements"></a>要求  
 **标头：** atlutil.h  
  
##  <a name="addhandle"></a>  CNoWorkerThread::AddHandle  
 非功能上的等效于[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。  
  
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
  
##  <a name="addtimer"></a>  CNoWorkerThread::AddTimer  
 非功能上的等效于[CWorkerThread::AddTimer](../../atl/reference/cworkerthread-class.md#addtimer)。  
  
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
  
##  <a name="getthreadhandle"></a>  CNoWorkerThread::GetThreadHandle  
 非功能上的等效于[CWorkerThread::GetThreadHandle](../../atl/reference/cworkerthread-class.md#getthreadhandle)。  
  
```
HANDLE GetThreadHandle() throw();
```  
  
### <a name="return-value"></a>返回值  
 始终返回 NULL。  
  
### <a name="remarks"></a>备注  
 此类提供的实现没有任何影响。  
  
##  <a name="getthreadid"></a>  CNoWorkerThread::GetThreadId  
 非功能上的等效于[CWorkerThread::GetThreadId](../../atl/reference/cworkerthread-class.md#getthreadid)。  
  
```
DWORD GetThreadId() throw();
```  
  
### <a name="return-value"></a>返回值  
 始终返回 0。  
  
### <a name="remarks"></a>备注  
 此类提供的实现没有任何影响。  
  
##  <a name="initialize"></a>  CNoWorkerThread::Initialize  
 非功能上的等效于[CWorkerThread::Initialize](../../atl/reference/cworkerthread-class.md#initialize)。  
  
```
HRESULT Initialize() throw();
```  
  
### <a name="return-value"></a>返回值  
 始终返回，则为 S_OK。  
  
### <a name="remarks"></a>备注  
 此类提供的实现没有任何影响。  
  
##  <a name="removehandle"></a>  CNoWorkerThread::RemoveHandle  
 非功能上的等效于[CWorkerThread::RemoveHandle](../../atl/reference/cworkerthread-class.md#removehandle)。  
  
```
HRESULT RemoveHandle(HANDLE /* hObject
 */) throw();
```  
  
### <a name="return-value"></a>返回值  
 始终返回，则为 S_OK。  
  
### <a name="remarks"></a>备注  
 此类提供的实现没有任何影响。  
  
##  <a name="shutdown"></a>  CNoWorkerThread::Shutdown  
 非功能上的等效于[CWorkerThread::Shutdown](../../atl/reference/cworkerthread-class.md#shutdown)。  
  
```
HRESULT Shutdown(DWORD dwWait = ATL_WORKER_THREAD_WAIT) throw();
```  
  
### <a name="return-value"></a>返回值  
 始终返回，则为 S_OK。  
  
### <a name="remarks"></a>备注  
 此类提供的实现没有任何影响。
