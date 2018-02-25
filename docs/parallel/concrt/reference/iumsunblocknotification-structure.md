---
title: "IUMSUnblockNotification 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetContext
- CONCRTRM/concurrency::IUMSUnblockNotification::IUMSUnblockNotification::GetNextUnblockNotification
dev_langs:
- C++
helpviewer_keywords:
- IUMSUnblockNotification structure
ms.assetid: eaca9529-c1cc-472b-8ec6-722a1ff0fa2a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9058b2f16532f99e1beea8133fd5187ac296920e
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="iumsunblocknotification-structure"></a>IUMSUnblockNotification 结构
表示来自资源管理器的通知，说明阻止并触发返回到计划程序的指定计划上下文的线程代理已解除阻止，并已准备好进行计划。 一旦重新计划该线程代理的关联执行上下文（从 `GetContext` 方法返回），此接口将变得无效。  
  
## <a name="syntax"></a>语法  
  
```
struct IUMSUnblockNotification;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[IUMSUnblockNotification::GetContext](#getcontext)|返回`IExecutionContext`与已解除阻止的线程代理关联的执行上下文的接口。 一旦此方法返回，且已通过调用重新计划的基础的执行上下文`IThreadProxy::SwitchTo`方法，此接口将不再有效。|  
|[IUMSUnblockNotification::GetNextUnblockNotification](#getnextunblocknotification)|返回下一个`IUMSUnblockNotification`从方法返回链中的接口`IUMSCompletionList::GetUnblockNotifications`。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IUMSUnblockNotification`  
  
## <a name="requirements"></a>惠?  
 **标头：** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="getcontext"></a>  IUMSUnblockNotification::GetContext Method  
 返回`IExecutionContext`与已解除阻止的线程代理关联的执行上下文的接口。 一旦此方法返回，且已通过调用重新计划的基础的执行上下文`IThreadProxy::SwitchTo`方法，此接口将不再有效。  
  
```
virtual IExecutionContext* GetContext() = 0;
```  
  
### <a name="return-value"></a>返回值  
 `IExecutionContext`已解除阻止的线程代理的执行上下文的接口。  
  
##  <a name="getnextunblocknotification"></a>  IUMSUnblockNotification::GetNextUnblockNotification Method  
 返回下一个`IUMSUnblockNotification`从方法返回链中的接口`IUMSCompletionList::GetUnblockNotifications`。  
  
```
virtual IUMSUnblockNotification* GetNextUnblockNotification() = 0;
```  
  
### <a name="return-value"></a>返回值  
 下一步`IUMSUnblockNotification`从方法返回链中的接口`IUMSCompletionList::GetUnblockNotifications`。  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [IUMSScheduler 结构](iumsscheduler-structure.md)   
 [IUMSCompletionList 结构](iumscompletionlist-structure.md)
