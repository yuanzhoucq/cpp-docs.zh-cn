---
title: ITopologyExecutionResource 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: adb456315b2c6d15b7a3696df9a6845a2bd2b899
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="itopologyexecutionresource-structure"></a>ITopologyExecutionResource 结构
资源管理器定义的执行资源的接口。  
  
## <a name="syntax"></a>语法  
  
```
struct ITopologyExecutionResource;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[ITopologyExecutionResource::GetId](#getid)|返回此执行资源的资源管理器的唯一标识符。|  
|[ITopologyExecutionResource::GetNext](#getnext)|返回一个指向枚举顺序中下一执行资源的接口。|  
  
## <a name="remarks"></a>备注  
 此接口通常用于为通过资源管理器已观察到引导系统的拓扑。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ITopologyExecutionResource`  
  
## <a name="requirements"></a>要求  
 **标头：** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="getid"></a>  Itopologyexecutionresource:: Getid 方法  
 返回此执行资源的资源管理器的唯一标识符。  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 此执行资源的资源管理器的唯一标识符。  
  
##  <a name="getnext"></a>  Itopologyexecutionresource:: Getnext 方法  
 返回一个指向枚举顺序中下一执行资源的接口。  
  
```
virtual ITopologyExecutionResource *GetNext() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 一个指向枚举顺序中下一执行资源的接口。 如果此执行资源所属节点的枚举顺序中没有更多的节点，此方法将返回值 `NULL`。  
  
## <a name="see-also"></a>请参阅  
 [并发命名空间](concurrency-namespace.md)
