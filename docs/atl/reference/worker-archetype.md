---
title: 辅助 Archetype |Microsoft 文档
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
ms.openlocfilehash: 42ff0e71e15c70d8d5d9dee0b398d4f0c075eb47
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="worker-archetype"></a>辅助原型
类符合*辅助*archetype 提供到过程工作项的代码在线程池上排队。  
  
 **实现**  
  
 若要实现此 archetype 符合的类，类必须提供以下功能：  
  
|方法|描述|  
|------------|-----------------|  
|[Initialize](#initialize)|调用以初始化辅助对象，任何请求传递到前[执行](#execute)。|  
|[执行](#execute)|调用以处理工作项。|  
|[终止](#terminate)|调用的所有请求都传递给后取消初始化辅助对象[执行](#execute)。|  
  
|Typedef|描述|  
|-------------|-----------------|  
|[RequestType](#requesttype)|可由辅助类处理的工作项的类型的 typedef。|  
  
 典型*辅助*类类似如下所示：  
  
 [!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]  
  
 **现有实现**  
  
 这些类符合此原型：  
  
|类|描述|  
|-----------|-----------------|  
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|在线程池中接收请求，并将它们传递到创建和销毁为每个请求的辅助对象。|  
  
 **使用**  
  
 这些模板参数预期要符合此 archetype 的类：  
  
|参数名称|通过者|  
|--------------------|-------------|  
|*辅助进程*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|  
|*辅助进程*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|  
  
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
 `request`  
 要处理的工作项。 在工作项已与相同类型`RequestType`。  
  
 `pvWorkerParam`  
 理解辅助类的一个自定义参数。 此外传递给`WorkerArchetype::Initialize`和`Terminate`。  
  
 `pOverlapped`  
 指向的指针[OVERLAPPED](http://msdn.microsoft.com/library/windows/desktop/ms684342)用于创建的队列的工作项排队等待的结构。  
  
## <a name="initialize"></a> WorkerArchetype::Initialize
调用以初始化辅助对象，任何请求传递到前`WorkerArchetype::Execute`。  
```
BOOL Initialize(void* pvParam) throw();
```  
  
#### <a name="parameters"></a>参数  
 `pvParam`  
 理解辅助类的一个自定义参数。 此外传递给`WorkerArchetype::Terminate`和`WorkerArchetype::Execute`。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**成功后， **FALSE**失败。  
  
## <a name="requesttype"></a> WorkerArchetype::RequestType
可由辅助类处理的工作项的类型的 typedef。  
  
```  
typedef MyRequestType RequestType;    
```  
  
### <a name="remarks"></a>备注  
 此类型必须使用的第一个参数作为`WorkerArchetype::Execute`，并且必须能够与其他 ULONG_PTR 强制转换。  
  
## <a name="terminate"></a> WorkerArchetype::Terminate
调用的所有请求都传递给后取消初始化辅助对象`WorkerArchetype::Execute`)。  
    
``` 
void Terminate(void* pvParam) throw();
```  
  
#### <a name="parameters"></a>参数  
 `pvParam`  
 理解辅助类的一个自定义参数。 此外传递给`WorkerArchetype::Initialize`和`WorkerArchetype::Execute`。  
  
## <a name="see-also"></a>请参阅  
 [原型](../../atl/reference/atl-archetypes.md)   
 [概念](../../atl/active-template-library-atl-concepts.md)   
 [ATL COM 桌面组件](../../atl/atl-com-desktop-components.md)



