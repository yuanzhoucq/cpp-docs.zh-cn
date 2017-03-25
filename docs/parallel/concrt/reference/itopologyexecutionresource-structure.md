---
title: "ITopologyExecutionResource 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetId
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetNext
dev_langs:
- C++
helpviewer_keywords:
- ITopologyExecutionResource structure
ms.assetid: e36756f7-4cd9-4fa6-ba60-23fea58ef2bf
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: d9671dbf84a1104bc3b6f3a6f9d383aac167759c
ms.lasthandoff: 03/17/2017

---
# <a name="itopologyexecutionresource-structure"></a>ITopologyExecutionResource 结构
资源管理器定义的执行资源的接口。  
  
## <a name="syntax"></a>语法  
  
```
struct ITopologyExecutionResource;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[Itopologyexecutionresource:: Getid](#getid)|返回此执行资源的资源管理器的唯一标识符。|  
|[Itopologyexecutionresource:: Getnext](#getnext)|返回一个指向枚举顺序中下一执行资源的接口。|  
  
## <a name="remarks"></a>备注  
 此接口通常用来为资源管理器已观察到引导系统的拓扑。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ITopologyExecutionResource`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="getid"></a>Itopologyexecutionresource:: Getid 方法  
 返回此执行资源的资源管理器的唯一标识符。  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 此执行资源的资源管理器的唯一标识符。  
  
##  <a name="getnext"></a>Itopologyexecutionresource:: Getnext 方法  
 返回一个指向枚举顺序中下一执行资源的接口。  
  
```
virtual ITopologyExecutionResource *GetNext() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 一个指向枚举顺序中下一执行资源的接口。 如果此执行资源所属节点的枚举顺序中没有更多的节点，此方法将返回值 `NULL`。  
  
## <a name="see-also"></a>另请参阅  
 [并发命名空间](concurrency-namespace.md)

