---
title: "IUMSScheduler 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler
- CONCRTRM/concurrency::IUMSScheduler::IUMSScheduler::SetCompletionList
dev_langs: C++
helpviewer_keywords: IUMSScheduler structure
ms.assetid: 3a500225-4e02-4849-bb56-d744865f5870
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 82795e3494267f953875136bb29c701c93dbc934
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="iumsscheduler-structure"></a>IUMSScheduler 结构
工作计划程序的抽象的接口，该工作计划程序希望并发运行时的资源管理器向其传递用户模式计划 (UMS) 线程。 资源管理器使用此接口与 UMS 线程计划程序进行通信。 `IUMSScheduler` 接口继承自 `IScheduler` 接口。  
  
## <a name="syntax"></a>语法  
  
```
struct IUMSScheduler : public IScheduler;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Iumsscheduler:: Setcompletionlist](#setcompletionlist)|将分配`IUMSCompletionList`UMS 线程计划程序的接口。|  
  
## <a name="remarks"></a>备注  
 如果你要实现的自定义计划程序进行通信使用资源管理器中，并且你希望 UMS 线程能被传递给计划程序而不是普通的 Win32 线程，则应提供的实现`IUMSScheduler`接口。 此外，应将计划程序策略密钥的策略值设置`SchedulerKind`要`UmsThreadDefault`。 如果该策略都指定 UMS 线程`IScheduler`传递作为参数传递给接口[iresourcemanager:: Registerscheduler](iresourcemanager-structure.md#registerscheduler)方法必须是`IUMSScheduler`接口。  
  
 资源管理器就能够处理 UMS 线程仅在具有 UMS 功能的操作系统上。 使用 Windows 7 和更高版本的 64 位操作系统支持 UMS 线程。 如果你创建的计划程序策略所具有`SchedulerKind`密钥设置为值`UmsThreadDefault`基础平台不支持 UMS 的值和`SchedulerKind`上该策略的密钥将更改为值`ThreadScheduler`。 你应该始终读回此策略值在希望接收 UMS 线程之前。  
  
 `IUMSScheduler`接口是双向通信的通道的计划程序和资源管理器之间的一个 end。 由表示另一端`IResourceManager`和`ISchedulerProxy`接口，实现通过资源管理器。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [IScheduler](ischeduler-structure.md)  
  
 `IUMSScheduler`  
  
## <a name="requirements"></a>要求  
 **标头：** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="setcompletionlist"></a>Iumsscheduler:: Setcompletionlist 方法  
 将分配`IUMSCompletionList`UMS 线程计划程序的接口。  
  
```
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```  
  
### <a name="parameters"></a>参数  
 `pCompletionList`  
 计划程序完成列表接口。 没有一个单独的列表，每个计划程序。  
  
### <a name="remarks"></a>备注  
 资源管理器将调用此方法在指定计划程序已请求资源的初始分配后，它想 UMS 线程计划程序上。 计划程序可以使用`IUMSCompletionList`接口来确定当 UMS 线程代理已解除阻塞。 它才可访问此接口从在分配给 UMS 调度程序的虚拟处理器根上运行的线程代理。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [PolicyElementKey](concurrency-namespace-enums.md)   
 [IScheduler 结构](ischeduler-structure.md)   
 [IUMSCompletionList 结构](iumscompletionlist-structure.md)   
 [IResourceManager 结构](iresourcemanager-structure.md)
