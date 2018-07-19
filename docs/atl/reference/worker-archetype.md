---
title: 辅助原型 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75f9e974a2969fa817598556e3e043626a826970
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881300"
---
# <a name="worker-archetype"></a>辅助原型
类符合*辅助*原型提供线程池上排队进程的工作项的代码。  
  
 **实现**  
  
 若要实现符合此原型的类，类必须提供以下功能：  
  
|方法|描述|  
|------------|-----------------|  
|[Initialize](#initialize)|调用以初始化辅助对象之前的任何请求传递给[Execute](#execute)。|  
|[执行](#execute)|调用以处理工作项。|  
|[终止](#terminate)|被调用的所有请求都传递给后取消初始化辅助对象[Execute](#execute)。|  
  
|Typedef|描述|  
|-------------|-----------------|  
|[RequestType](#requesttype)|可以由辅助类处理的工作项类型的 typedef。|  
  
 典型*辅助*类如下所示：  
  
 [!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]  
  
 **现有的实现**  
  
 这些类符合此原型：  
  
|类|描述|  
|-----------|-----------------|  
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|从线程池接收请求并将它们传递到一个辅助角色对象的创建和销毁为每个请求。|  
  
 **使用**  
  
 这些模板参数预期要符合此原型的类：  
  
|参数名称|通过者|  
|--------------------|-------------|  
|*辅助角色*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|  
|*辅助角色*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|  
  
### <a name="requirements"></a>要求  
 **标头：** atlutil.h  
  
## <a name="execute"></a>WorkerArchetype::Execute
调用以处理工作项。  
  
  
  
```  
void Execute(
    RequestType request,  
    void* pvWorkerParam,  
    OVERLAPPED* pOverlapped);
```  
  
#### <a name="parameters"></a>参数  
 *请求*  
 要处理的工作项。 工作项是与相同类型的`RequestType`。  
  
 *pvWorkerParam*  
 理解辅助类的一个自定义参数。 此外传递给`WorkerArchetype::Initialize`和`Terminate`。  
  
 *给 pOverlapped*  
 一个指向[OVERLAPPED](http://msdn.microsoft.com/library/windows/desktop/ms684342)用来创建的队列的工作项排队等待的结构。  
  
## <a name="initialize"></a> WorkerArchetype::Initialize
调用以初始化辅助对象之前的任何请求传递给`WorkerArchetype::Execute`。  
```
BOOL Initialize(void* pvParam) throw();
```  
  
#### <a name="parameters"></a>参数  
 *pvParam*  
 理解辅助类的一个自定义参数。 此外传递给`WorkerArchetype::Terminate`和`WorkerArchetype::Execute`。  
  
### <a name="return-value"></a>返回值  
 如果成功，返回 TRUE FALSE 失败。  
  
## <a name="requesttype"></a> WorkerArchetype::RequestType
可以由辅助类处理的工作项类型的 typedef。  
  
```  
typedef MyRequestType RequestType;    
```  
  
### <a name="remarks"></a>备注  
 此类型必须使用作为第一个参数`WorkerArchetype::Execute`，并且必须能够与 ULONG_PTR 要强制转换。  
  
## <a name="terminate"></a> WorkerArchetype::Terminate
被调用的所有请求都传递给后取消初始化辅助对象`WorkerArchetype::Execute`)。  
    
``` 
void Terminate(void* pvParam) throw();
```  
  
#### <a name="parameters"></a>参数  
 *pvParam*  
 理解辅助类的一个自定义参数。 此外传递给`WorkerArchetype::Initialize`和`WorkerArchetype::Execute`。  
  
## <a name="see-also"></a>请参阅  
 [概念](../../atl/active-template-library-atl-concepts.md)   
 [ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)



