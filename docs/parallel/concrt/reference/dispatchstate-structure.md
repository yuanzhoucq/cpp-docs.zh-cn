---
title: "DispatchState 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrtrm/concurrency::DispatchState
dev_langs:
- C++
helpviewer_keywords:
- DispatchState structure
ms.assetid: 8c52546e-1650-48a0-985f-7e4a0fc26a90
caps.latest.revision: 17
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
ms.openlocfilehash: 46c2219464e57da4931596e970199549405d02ec
ms.lasthandoff: 02/24/2017

---
# <a name="dispatchstate-structure"></a>DispatchState 结构
`DispatchState` 结构用于将状态传输给 `IExecutionContext::Dispatch` 方法。 它描述了在 `IExecutionContext` 接口上调用 `Dispatch` 方法的情形。  
  
## <a name="syntax"></a>语法  
  
```
struct DispatchState;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[Dispatchstate:: Dispatchstate 构造函数](#ctor)|构造一个新`DispatchState`对象。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[Dispatchstate:: M_dispatchstatesize 数据成员](#m_dispatchstatesize)|此结构，用于版本控制的大小。|  
|[Dispatchstate:: M_fispreviouscontextasynchronouslyblocked 数据成员](#m_fispreviouscontextasynchronouslyblocked)|指示是否已进入此上下文`Dispatch`方法由于以前的上下文以异步方式阻止。 这仅用于 UMS 调度上下文，并设置为值`0`的所有其他执行上下文。|  
|[Dispatchstate:: M_reserved 数据成员](#m_reserved)|留待将来信息传递的位。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `DispatchState`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namectora--dispatchstatedispatchstate-constructor"></a><a name="ctor"></a>Dispatchstate:: Dispatchstate 构造函数  
 构造一个新`DispatchState`对象。  
  
```
DispatchState();
```  
  
##  <a name="a-namemdispatchstatesizea--dispatchstatemdispatchstatesize-data-member"></a><a name="m_dispatchstatesize"></a>Dispatchstate:: M_dispatchstatesize 数据成员  
 此结构，用于版本控制的大小。  
  
```
unsigned long m_dispatchStateSize;
```  
  
##  <a name="a-namemfispreviouscontextasynchronouslyblockeda--dispatchstatemfispreviouscontextasynchronouslyblocked-data-member"></a><a name="m_fispreviouscontextasynchronouslyblocked"></a>Dispatchstate:: M_fispreviouscontextasynchronouslyblocked 数据成员  
 指示是否已进入此上下文`Dispatch`方法由于以前的上下文以异步方式阻止。 这仅用于 UMS 调度上下文，并设置为值`0`的所有其他执行上下文。  
  
```
unsigned int m_fIsPreviousContextAsynchronouslyBlocked : 1;
```  
  
##  <a name="a-namemreserveda--dispatchstatemreserved-data-member"></a><a name="m_reserved"></a>Dispatchstate:: M_reserved 数据成员  
 留待将来信息传递的位。  
  
```
unsigned int m_reserved : 31;
```  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)

