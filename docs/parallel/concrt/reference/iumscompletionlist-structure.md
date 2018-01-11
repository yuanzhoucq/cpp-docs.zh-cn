---
title: "IUMSCompletionList 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList::IUMSCompletionList::GetUnblockNotifications
dev_langs: C++
helpviewer_keywords: IUMSCompletionList structure
ms.assetid: 81b5250e-3065-492c-b20d-2cdabf12271a
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 50fd2381174e947e243ad6aa40516be5fd728902
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="iumscompletionlist-structure"></a>IUMSCompletionList 结构
表示 UMS 完成列表。 UMS 线程阻止时，将分派计划程序的指定计划上下文，以便决定原始线程被阻止时，在基础虚拟处理器根上计划哪些内容。 如果原始线程解除阻止，则操作系统将它排队到完成列表，该列表可以通过此接口访问。 计划程序可以在指定计划上下文中或其搜索工作的任何其他位置查询完成列表。  
  
## <a name="syntax"></a>语法  
  
```
struct IUMSCompletionList;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Iumscompletionlist:: Getunblocknotifications](#getunblocknotifications)|检索的链`IUMSUnblockNotification`表示其相关联的线程代理已解除阻止，因为上一次此方法调用的执行上下文的接口。|  
  
## <a name="remarks"></a>备注  
 计划程序必须要格外小心利用此接口可取消排队从完成列表项后要执行的操作。 项应放置在可运行的上下文的计划程序的列表，并可通常越早越好。 完全有可能某一取消排队项已被授予的任意锁的所有权。 计划程序可以进行可能会阻止取消排队项的调用和通常可以通过在调度器的列表上的这些项的位置之间没有任意函数调用。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IUMSCompletionList`  
  
## <a name="requirements"></a>惠?  
 **标头：** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="getunblocknotifications"></a>Iumscompletionlist:: Getunblocknotifications 方法  
 检索的链`IUMSUnblockNotification`表示其相关联的线程代理已解除阻止，因为上一次此方法调用的执行上下文的接口。  
  
```
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```  
  
### <a name="return-value"></a>返回值  
 链`IUMSUnblockNotification`接口。  
  
### <a name="remarks"></a>备注  
 一旦重新计划任务的执行上下文，返回的通知均无效。  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [IUMSScheduler 结构](iumsscheduler-structure.md)   
 [IUMSUnblockNotification 结构](iumsunblocknotification-structure.md)
