---
title: "IUMSCompletionList 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList
- CONCRTRM/concurrency::IUMSCompletionList::IUMSCompletionList::GetUnblockNotifications
dev_langs:
- C++
helpviewer_keywords:
- IUMSCompletionList structure
ms.assetid: 81b5250e-3065-492c-b20d-2cdabf12271a
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 65655e4e03a7b187e0bbadbd576bc088bb57f7c8
ms.contentlocale: zh-cn
ms.lasthandoff: 03/17/2017

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
|[Iumscompletionlist:: Getunblocknotifications](#getunblocknotifications)|检索链`IUMSUnblockNotification`表示其关联的线程代理已解除阻塞，因为上一次此方法被调用的执行上下文的接口。|  
  
## <a name="remarks"></a>备注  
 计划程序必须格外小心使用此接口以从完成列表项的取消排队后要执行的操作。 项应放置在可运行的上下文的计划程序的列表，并尽可能快地进行常规访问。 它是完全有可能在某一项取消排队已被授予的任意锁所有权。 计划程序可以取消排队项的调用和上一个列表，其中通常可从计划程序中的项目的位置之间可能会阻止任何函数调用。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IUMSCompletionList`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="getunblocknotifications"></a>Iumscompletionlist:: Getunblocknotifications 方法  
 检索链`IUMSUnblockNotification`表示其关联的线程代理已解除阻塞，因为上一次此方法被调用的执行上下文的接口。  
  
```
virtual IUMSUnblockNotification *GetUnblockNotifications() = 0;
```  
  
### <a name="return-value"></a>返回值  
 链`IUMSUnblockNotification`接口。  
  
### <a name="remarks"></a>备注  
 执行上下文都将重新计划后，返回的通知均无效。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [IUMSScheduler 结构](iumsscheduler-structure.md)   
 [IUMSUnblockNotification 结构](iumsunblocknotification-structure.md)

