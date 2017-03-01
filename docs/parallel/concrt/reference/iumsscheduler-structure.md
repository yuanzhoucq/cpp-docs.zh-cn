---
title: "IUMSScheduler 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrtrm/concurrency::IUMSScheduler
dev_langs:
- C++
helpviewer_keywords:
- IUMSScheduler structure
ms.assetid: 3a500225-4e02-4849-bb56-d744865f5870
caps.latest.revision: 18
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
ms.sourcegitcommit: fa774c7f025b581d65c28d65d83e22ff2d798230
ms.openlocfilehash: 658c0d0c9ddb9bbe51134f0a7ea0211be9c39815
ms.lasthandoff: 02/24/2017

---
# <a name="iumsscheduler-structure"></a>IUMSScheduler 结构
工作计划程序的抽象的接口，该工作计划程序希望并发运行时的资源管理器向其传递用户模式计划 (UMS) 线程。 资源管理器使用此接口与 UMS 线程计划程序进行通信。 `IUMSScheduler` 接口继承自 `IScheduler` 接口。  
  
## <a name="syntax"></a>语法  
  
```
struct IUMSScheduler : public IScheduler;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[Iumsscheduler:: Setcompletionlist 方法](#setcompletionlist)|将分配`IUMSCompletionList`UMS 线程计划程序的接口。|  
  
## <a name="remarks"></a>备注  
 如果您要实现与资源管理器中，进行通信的自定义计划，并且您希望 UMS 线程要传递给您的计划程序，而不是普通的 Win32 线程，则应提供的实现`IUMSScheduler`接口。 此外，还应设置计划程序策略注册表项的策略值`SchedulerKind`要`UmsThreadDefault`。 如果策略指定 UMS 线程`IScheduler`作为参数传递的接口[iresourcemanager:: Registerscheduler](iresourcemanager-structure.md#registerscheduler)方法必须是`IUMSScheduler`接口。  
  
 资源管理器就能够处理 UMS 线程仅在具有 UMS 功能的操作系统上。 安装有 Windows 7 和更高版本的 64 位操作系统支持 UMS 线程。 如果您创建的计划程序策略所具有`SchedulerKind`键设置为值`UmsThreadDefault`，并且基础平台不支持 UMS，值`SchedulerKind`密钥对该策略将更改为值`ThreadScheduler`。 您应该始终读回此策略值在预料到会收到 UMS 线程之前。  
  
 `IUMSScheduler`接口是一个计划程序和资源管理器之间的通信的双向通道的一端。 另一端都由`IResourceManager`和`ISchedulerProxy`实现资源管理器的接口。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [IScheduler](ischeduler-structure.md)  
  
 `IUMSScheduler`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namesetcompletionlista--iumsschedulersetcompletionlist-method"></a><a name="setcompletionlist"></a>Iumsscheduler:: Setcompletionlist 方法  
 将分配`IUMSCompletionList`UMS 线程计划程序的接口。  
  
```
virtual void SetCompletionList(_Inout_ IUMSCompletionList* pCompletionList) = 0;
```  
  
### <a name="parameters"></a>参数  
 `pCompletionList`  
 用于计划程序的完成列表接口。 没有一个单独的列表，每个计划程序。  
  
### <a name="remarks"></a>备注  
 资源管理器将调用此方法指定其在计划程序已请求资源的初始分配后才需要 UMS 线程计划程序上。 计划程序可以使用`IUMSCompletionList`接口，以确定当 UMS 线程代理已解除阻塞。 它才可分配给 UMS 调度程序的虚拟处理器根上运行的线程代理从访问此接口。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [PolicyElementKey 枚举](concurrency-namespace-enums.md)   
 [IScheduler 结构](ischeduler-structure.md)   
 [IUMSCompletionList 结构](iumscompletionlist-structure.md)   
 [IResourceManager 结构](iresourcemanager-structure.md)

