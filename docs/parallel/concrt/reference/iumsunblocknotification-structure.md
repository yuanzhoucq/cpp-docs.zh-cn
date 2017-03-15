---
title: "IUMSUnblockNotification 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrtrm/concurrency::IUMSUnblockNotification
dev_langs:
- C++
helpviewer_keywords:
- IUMSUnblockNotification structure
ms.assetid: eaca9529-c1cc-472b-8ec6-722a1ff0fa2a
caps.latest.revision: 19
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
ms.openlocfilehash: 6fba6c36987107e2e8100c8b296c279592220682
ms.lasthandoff: 02/24/2017

---
# <a name="iumsunblocknotification-structure"></a>IUMSUnblockNotification 结构
表示来自资源管理器的通知，说明阻止并触发返回到计划程序的指定计划上下文的线程代理已解除阻止，并已准备好进行计划。 一旦重新计划该线程代理的关联执行上下文（从 `GetContext` 方法返回），此接口将变得无效。  
  
## <a name="syntax"></a>语法  
  
```
struct IUMSUnblockNotification;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[Iumsunblocknotification:: Getcontext 方法](#getcontext)|返回`IExecutionContext`与已解除阻塞线程代理相关联的执行上下文的接口。 此方法返回时，并通过调用已重新计划基础的执行上下文之后`IThreadProxy::SwitchTo`方法，此接口将不再有效。|  
|[Iumsunblocknotification:: Getnextunblocknotification 方法](#getnextunblocknotification)|返回下一个`IUMSUnblockNotification`从方法返回链中的接口`IUMSCompletionList::GetUnblockNotifications`。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IUMSUnblockNotification`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namegetcontexta--iumsunblocknotificationgetcontext-method"></a><a name="getcontext"></a>Iumsunblocknotification:: Getcontext 方法  
 返回`IExecutionContext`与已解除阻塞线程代理相关联的执行上下文的接口。 此方法返回时，并通过调用已重新计划基础的执行上下文之后`IThreadProxy::SwitchTo`方法，此接口将不再有效。  
  
```
virtual IExecutionContext* GetContext() = 0;
```  
  
### <a name="return-value"></a>返回值  
 `IExecutionContext`已解除阻塞线程代理的执行上下文的接口。  
  
##  <a name="a-namegetnextunblocknotificationa--iumsunblocknotificationgetnextunblocknotification-method"></a><a name="getnextunblocknotification"></a>Iumsunblocknotification:: Getnextunblocknotification 方法  
 返回下一个`IUMSUnblockNotification`从方法返回链中的接口`IUMSCompletionList::GetUnblockNotifications`。  
  
```
virtual IUMSUnblockNotification* GetNextUnblockNotification() = 0;
```  
  
### <a name="return-value"></a>返回值  
 下一步`IUMSUnblockNotification`从方法返回链中的接口`IUMSCompletionList::GetUnblockNotifications`。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [IUMSScheduler 结构](iumsscheduler-structure.md)   
 [IUMSCompletionList 结构](iumscompletionlist-structure.md)

