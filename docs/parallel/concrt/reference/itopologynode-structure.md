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
ms.openlocfilehash: 7cb815c4f7dc5ad09e8d352abc3f3375b8d9e205
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368104"
---
# <a name="itopologynode-structure"></a>ITopologyNode 结构

资源管理器定义的拓扑节点的接口。 一个节点包含一个或多个执行资源。

## <a name="syntax"></a>语法

```cpp
struct ITopologyNode;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[I拓扑节点：获取执行资源计数](#getexecutionresourcecount)|返回在此节点下组合在一起的执行资源的数量。|
|[I拓扑节点：获取第一个执行资源](#getfirstexecutionresource)|返回在此节点下以枚举顺序分组的第一个执行资源。|
|[I拓扑节点：GetId](#getid)|返回资源管理器对此节点的唯一标识符。|
|[I拓扑节点：获取下一个](#getnext)|返回一个指向枚举顺序中下一拓扑节点的接口。|
|[I拓扑节点：：获取NumaNode](#getnumanode)|返回此资源马anger节点所属的 Windows 分配的 NUMA 节点号。|

## <a name="remarks"></a>备注

此接口通常用于遍历资源管理器观察到的系统拓扑。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ITopologyNode`

## <a name="requirements"></a>要求

**标题：** concrtrm.h

**命名空间：** 并发

## <a name="itopologynodegetexecutionresourcecount-method"></a><a name="getexecutionresourcecount"></a>I拓扑节点：获取执行资源计数方法

返回在此节点下组合在一起的执行资源的数量。

```cpp
virtual unsigned int GetExecutionResourceCount() const = 0;
```

### <a name="return-value"></a>返回值

在此节点下组合在一起的执行资源的数量。

## <a name="itopologynodegetfirstexecutionresource-method"></a><a name="getfirstexecutionresource"></a>I拓扑节点：获取第一个执行资源方法

返回在此节点下以枚举顺序分组的第一个执行资源。

```cpp
virtual ITopologyExecutionResource *GetFirstExecutionResource() const = 0;
```

### <a name="return-value"></a>返回值

在此节点下以枚举顺序分组的第一个执行资源。

## <a name="itopologynodegetid-method"></a><a name="getid"></a>I拓扑节点：GetId 方法

返回资源管理器对此节点的唯一标识符。

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>返回值

资源管理器对此节点的唯一标识符。

### <a name="remarks"></a>备注

并发运行时以处理器节点组表示系统上的硬件线程。 节点通常派生自系统的硬件拓扑。 例如，特定套接字或特定 NUMA 节点上的所有处理器可能属于同一处理器节点。 资源管理器为这些节点分配唯一标识符，从`0`最多和包括`nodeCount - 1`开始，其中`nodeCount`表示系统上的处理器节点总数。

节点计数可以从函数[GetProcessorNodeCount](concurrency-namespace-functions.md)获得。

## <a name="itopologynodegetnext-method"></a><a name="getnext"></a>I拓扑节点：获取下一个方法

返回一个指向枚举顺序中下一拓扑节点的接口。

```cpp
virtual ITopologyNode *GetNext() const = 0;
```

### <a name="return-value"></a>返回值

一个指向枚举顺序中下一节点的接口。 如果系统拓扑的枚举顺序中没有更多的节点，则此方法将返回值 `NULL`。

## <a name="itopologynodegetnumanode-method"></a><a name="getnumanode"></a>I拓扑节点：：获取NumaNode方法

返回此资源马anger节点所属的 Windows 分配的 NUMA 节点号。

```cpp
virtual unsigned long GetNumaNode() const = 0;
```

### <a name="return-value"></a>返回值

此资源管理器节点所属的 Windows 分配了 NUMA 节点号。

### <a name="remarks"></a>备注

在属于此节点的虚拟处理器根上运行的线程代理将至少具有此方法返回的 NUMA 节点的 NUMA 节点级别的关联。

## <a name="see-also"></a>另请参阅

[concurrency 命名空间](concurrency-namespace.md)
