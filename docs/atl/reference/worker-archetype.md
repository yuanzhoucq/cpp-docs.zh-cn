---
title: "辅助原型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
caps.latest.revision: 16
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
ms.openlocfilehash: 046160644cca3bd23e4293a3c52692d2b4c94cd5
ms.lasthandoff: 02/24/2017

---
# <a name="worker-archetype"></a>辅助原型
类符合*工作人员*原型提供在线程池上的代码到进程的工作项排入队列。  
  
 **实现**  
  
 若要实现一个符合此原型的类，该类必须提供以下功能︰  
  
|方法|描述|  
|------------|-----------------|  
|[初始化](#initialize)|调用以初始化工作对象，在任何请求传递给之前[Execute](#execute)。|  
|[执行](#execute)|调用来处理工作项。|  
|[终止](#terminate)|被调用的所有请求都传递给后取消初始化 worker 对象[Execute](#execute)。|  
  
|Typedef|描述|  
|-------------|-----------------|  
|[RequestType](#requesttype)|Worker 类可以处理的工作项类型的 typedef。|  
  
 典型*工作人员*类如下所示︰  
  
 [!code-cpp[NVC_ATL_Utilities #&137;](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]  
  
 **现有的实现**  
  
 这些类符合此原型︰  
  
|类|说明|  
|-----------|-----------------|  
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|从线程池接收请求并将它们传递到创建和销毁为每个请求的工作对象。|  
  
 **使用**  
  
 这些模板参数预期要符合此原型的类︰  
  
|参数名称|通过者|  
|--------------------|-------------|  
|*辅助进程*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|  
|*辅助进程*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|  
  
### <a name="requirements"></a>要求  
 **标头︰** atlutil.h  
  
## <a name="a-nameexecuteaworkerarchetypeexecute"></a><a name="execute"></a>WorkerArchetype::Execute
调用来处理工作项。  
  
  
  
```  
void Execute(
    RequestType request,  
    void* pvWorkerParam,  
    OVERLAPPED* pOverlapped);
```  
  
#### <a name="parameters"></a>参数  
 `request`  
 要处理的工作项。 与相同类型的工作项是`RequestType`。  
  
 `pvWorkerParam`  
 理解 worker 类的一个自定义参数。 此外传递给`WorkerArchetype::Initialize`和`Terminate`。  
  
 `pOverlapped`  
 一个指向[OVERLAPPED](http://msdn.microsoft.com/library/windows/desktop/ms684342)结构，用于创建在何种工作项排队等待的队列。  
  
## <a name="a-nameinitializea-workerarchetypeinitialize"></a><a name="initialize"></a>WorkerArchetype::Initialize
调用以初始化工作对象，在任何请求传递给之前`WorkerArchetype::Execute`。  
```
BOOL Initialize(void* pvParam) throw();
```  
  
#### <a name="parameters"></a>参数  
 `pvParam`  
 理解 worker 类的一个自定义参数。 此外传递给`WorkerArchetype::Terminate`和`WorkerArchetype::Execute`。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**成功时， **FALSE**失败。  
  
## <a name="a-namerequesttypea-workerarchetyperequesttype"></a><a name="requesttype"></a>WorkerArchetype::RequestType
Worker 类可以处理的工作项类型的 typedef。  
  
```  
typedef MyRequestType RequestType;    
```  
  
### <a name="remarks"></a>备注  
 此类型必须使用作为第一个参数`WorkerArchetype::Execute`，并且必须能够与 ULONG_PTR 被强制转换。  
  
## <a name="a-nameterminatea-workerarchetypeterminate"></a><a name="terminate"></a>WorkerArchetype::Terminate
被调用的所有请求都传递给后取消初始化 worker 对象`WorkerArchetype::Execute`)。  
    
``` 
void Terminate(void* pvParam) throw();
```  
  
#### <a name="parameters"></a>参数  
 `pvParam`  
 理解 worker 类的一个自定义参数。 此外传递给`WorkerArchetype::Initialize`和`WorkerArchetype::Execute`。  
  
## <a name="see-also"></a>另请参阅  
 [原型](../../atl/reference/atl-archetypes.md)   
 [概念](../../atl/active-template-library-atl-concepts.md)   
 [ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)




