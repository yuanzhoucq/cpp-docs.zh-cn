---
title: "ITopologyNode 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrtrm/concurrency::ITopologyNode
dev_langs:
- C++
helpviewer_keywords:
- ITopologyNode structure
ms.assetid: 92e7e032-04f6-4c7c-be36-8f9a35fc4734
caps.latest.revision: 10
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
ms.openlocfilehash: 8274da148f9f74cad73d63363bbbaff307943539
ms.lasthandoff: 02/24/2017

---
# <a name="itopologynode-structure"></a>ITopologyNode 结构
资源管理器定义的拓扑节点的接口。 一个节点包含一个或多个执行资源。  
  
## <a name="syntax"></a>语法  
  
```
struct ITopologyNode;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Itopologynode:: Getexecutionresourcecount 方法](#getexecutionresourcecount)|返回在此节点下组合在一起的执行资源的数量。|  
|[Itopologynode:: Getfirstexecutionresource 方法](#getfirstexecutionresource)|返回在此节点下以枚举顺序分组的第一个执行资源。|  
|[Itopologynode:: Getid 方法](#getid)|返回此节点的资源管理器的唯一标识符。|  
|[Itopologynode:: Getnext 方法](#getnext)|返回一个指向枚举顺序中下一拓扑节点的接口。|  
|[Itopologynode:: Getnumanode 方法](#getnumanode)|返回 Windows 分配此资源管理器节点所属于的 NUMA 节点号。|  
  
## <a name="remarks"></a>备注  
 此接口通常用来为资源管理器已观察到引导系统的拓扑。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ITopologyNode`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namegetexecutionresourcecounta--itopologynodegetexecutionresourcecount-method"></a><a name="getexecutionresourcecount"></a>Itopologynode:: Getexecutionresourcecount 方法  
 返回在此节点下组合在一起的执行资源的数量。  
  
```
virtual unsigned int GetExecutionResourceCount() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 在此节点下组合在一起的执行资源的数量。  
  
##  <a name="a-namegetfirstexecutionresourcea--itopologynodegetfirstexecutionresource-method"></a><a name="getfirstexecutionresource"></a>Itopologynode:: Getfirstexecutionresource 方法  
 返回在此节点下以枚举顺序分组的第一个执行资源。  
  
```
virtual ITopologyExecutionResource *GetFirstExecutionResource() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 在此节点下以枚举顺序分组的第一个执行资源。  
  
##  <a name="a-namegetida--itopologynodegetid-method"></a><a name="getid"></a>Itopologynode:: Getid 方法  
 返回此节点的资源管理器的唯一标识符。  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 资源管理器的此节点的唯一标识符。  
  
### <a name="remarks"></a>备注  
 并发运行时表示处理器节点组中的系统上的硬件线程。 节点通常派生自系统的硬件拓扑。 例如，特定的套接字或特定 NUMA 节点上的所有处理器可能都属于同一处理器节点。 资源管理器将唯一标识符分配给这些节点开头`0`达并包括`nodeCount - 1`，其中`nodeCount`表示系统上的处理器节点的总数。  
  
 可以从该函数获取节点数[GetProcessorNodeCount](concurrency-namespace-functions.md)。  
  
##  <a name="a-namegetnexta--itopologynodegetnext-method"></a><a name="getnext"></a>Itopologynode:: Getnext 方法  
 返回一个指向枚举顺序中下一拓扑节点的接口。  
  
```
virtual ITopologyNode *GetNext() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 一个指向枚举顺序中下一节点的接口。 如果系统拓扑的枚举顺序中没有更多的节点，则此方法将返回值 `NULL`。  
  
##  <a name="a-namegetnumanodea--itopologynodegetnumanode-method"></a><a name="getnumanode"></a>Itopologynode:: Getnumanode 方法  
 返回 Windows 分配此资源管理器节点所属于的 NUMA 节点号。  
  
```
virtual unsigned long GetNumaNode() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 Windows 分配此资源管理器节点所属于的 NUMA 节点号。  
  
### <a name="remarks"></a>备注  
 在对此节点所属的虚拟处理器根上运行的线程代理将具有关联到至少是此方法返回的 NUMA 节点的 NUMA 节点级别。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)

