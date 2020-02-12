---
title: ITopologyExecutionResource 结构
ms.date: 11/04/2016
f1_keywords:
- ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetId
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetNext
helpviewer_keywords:
- ITopologyExecutionResource structure
ms.assetid: e36756f7-4cd9-4fa6-ba60-23fea58ef2bf
ms.openlocfilehash: 82193a9b592cded96f3726cbabd6cf646eaa27c8
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140065"
---
# <a name="itopologyexecutionresource-structure"></a>ITopologyExecutionResource 结构

资源管理器定义的执行资源的接口。

## <a name="syntax"></a>语法

```cpp
struct ITopologyExecutionResource;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[ITopologyExecutionResource：： GetId](#getid)|返回此执行资源的资源管理器的唯一标识符。|
|[ITopologyExecutionResource：： GetNext](#getnext)|返回一个指向枚举顺序中下一执行资源的接口。|

## <a name="remarks"></a>备注

通常使用此接口来遍历由资源管理器观察到的系统拓扑。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ITopologyExecutionResource`

## <a name="requirements"></a>要求

**标头：** concrtrm。h

**命名空间：** 并发

## <a name="getid"></a>ITopologyExecutionResource：： GetId 方法

返回此执行资源的资源管理器的唯一标识符。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>返回值

此执行资源的资源管理器的唯一标识符。

## <a name="getnext"></a>ITopologyExecutionResource：： GetNext 方法

返回一个指向枚举顺序中下一执行资源的接口。

```cpp
virtual ITopologyExecutionResource *GetNext() const = 0;
```

### <a name="return-value"></a>返回值

一个指向枚举顺序中下一执行资源的接口。 如果此执行资源所属节点的枚举顺序中没有更多的节点，此方法将返回值 `NULL`。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
