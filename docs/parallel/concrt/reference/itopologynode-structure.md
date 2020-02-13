---
title: ITopologyNode 结构
ms.date: 11/04/2016
f1_keywords:
- ITopologyNode
- CONCRTRM/concurrency::ITopologyNode
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetExecutionResourceCount
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetFirstExecutionResource
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetId
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNext
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNumaNode
helpviewer_keywords:
- ITopologyNode structure
ms.assetid: 92e7e032-04f6-4c7c-be36-8f9a35fc4734
ms.openlocfilehash: 1b4cb6a856d6da7b8eee7f9cba1ad51e375c024d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140063"
---
# <a name="itopologynode-structure"></a>ITopologyNode 结构

资源管理器定义的拓扑节点的接口。 一个节点包含一个或多个执行资源。

## <a name="syntax"></a>语法

```cpp
struct ITopologyNode;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[ITopologyNode：： GetExecutionResourceCount](#getexecutionresourcecount)|返回在此节点下组合在一起的执行资源的数量。|
|[ITopologyNode：： GetFirstExecutionResource](#getfirstexecutionresource)|返回在此节点下以枚举顺序分组的第一个执行资源。|
|[ITopologyNode：： GetId](#getid)|返回此节点资源管理器的唯一标识符。|
|[ITopologyNode：： GetNext](#getnext)|返回一个指向枚举顺序中下一拓扑节点的接口。|
|[ITopologyNode：： GetNumaNode](#getnumanode)|返回此资源 Maanger 节点所属的 Windows 分配的 NUMA 节点号。|

## <a name="remarks"></a>备注

通常使用此接口来遍历由资源管理器观察到的系统拓扑。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ITopologyNode`

## <a name="requirements"></a>要求

**标头：** concrtrm。h

**命名空间：** 并发

## <a name="getexecutionresourcecount"></a>ITopologyNode：： GetExecutionResourceCount 方法

返回在此节点下组合在一起的执行资源的数量。

```cpp
virtual unsigned int GetExecutionResourceCount() const = 0;
```

### <a name="return-value"></a>返回值

在此节点下组合在一起的执行资源的数量。

## <a name="getfirstexecutionresource"></a>ITopologyNode：： GetFirstExecutionResource 方法

返回在此节点下以枚举顺序分组的第一个执行资源。

```cpp
virtual ITopologyExecutionResource *GetFirstExecutionResource() const = 0;
```

### <a name="return-value"></a>返回值

在此节点下以枚举顺序分组的第一个执行资源。

## <a name="getid"></a>ITopologyNode：： GetId 方法

返回此节点资源管理器的唯一标识符。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>返回值

资源管理器此节点的唯一标识符。

### <a name="remarks"></a>备注

并发运行时表示处理器节点组中系统上的硬件线程。 节点通常派生自系统的硬件拓扑。 例如，特定套接字或特定 NUMA 节点上的所有处理器可能属于同一处理器节点。 资源管理器将唯一标识符分配到这些节点，从 `0` 到（包括 `nodeCount - 1`）开始，其中 `nodeCount` 表示系统上的处理器节点的总数。

可以从函数[GetProcessorNodeCount](concurrency-namespace-functions.md)获取节点计数。

## <a name="getnext"></a>ITopologyNode：： GetNext 方法

返回一个指向枚举顺序中下一拓扑节点的接口。

```cpp
virtual ITopologyNode *GetNext() const = 0;
```

### <a name="return-value"></a>返回值

一个指向枚举顺序中下一节点的接口。 如果系统拓扑的枚举顺序中没有更多的节点，则此方法将返回值 `NULL`。

## <a name="getnumanode"></a>ITopologyNode：： GetNumaNode 方法

返回此资源 Maanger 节点所属的 Windows 分配的 NUMA 节点号。

```cpp
virtual unsigned long GetNumaNode() const = 0;
```

### <a name="return-value"></a>返回值

此资源管理器节点所属的 Windows 分配的 NUMA 节点号。

### <a name="remarks"></a>备注

在属于此节点的虚拟处理器根上运行的线程代理至少与此方法返回的 NUMA 节点的 NUMA 节点级别关联。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)
