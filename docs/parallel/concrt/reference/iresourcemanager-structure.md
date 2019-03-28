---
title: IResourceManager 结构
ms.date: 03/27/2019
f1_keywords:
- IResourceManager
- CONCRTRM/concurrency::IResourceManager
- CONCRTRM/concurrency::IResourceManager::IResourceManager::OSVersion
- CONCRTRM/concurrency::IResourceManager::IResourceManager::CreateNodeTopology
- CONCRTRM/concurrency::IResourceManager::IResourceManager::GetAvailableNodeCount
- CONCRTRM/concurrency::IResourceManager::IResourceManager::GetFirstNode
- CONCRTRM/concurrency::IResourceManager::IResourceManager::Reference
- CONCRTRM/concurrency::IResourceManager::IResourceManager::RegisterScheduler
- CONCRTRM/concurrency::IResourceManager::IResourceManager::Release
helpviewer_keywords:
- IResourceManager structure
ms.assetid: 3dd5ec2c-fe53-4121-ae77-1bc1d1167ff4
ms.openlocfilehash: 7afb37fb35040975d6e9471a1d12465e5163fafc
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/28/2019
ms.locfileid: "58565199"
---
# <a name="iresourcemanager-structure"></a>IResourceManager 结构

并发运行时的资源管理器的接口。 这是计划程序与资源管理器进行通信的接口。

## <a name="syntax"></a>语法

```
struct IResourceManager;
```

## <a name="members"></a>成员

### <a name="public-enumerations"></a>公共枚举

|名称|描述|
|----------|-----------------|
|[IResourceManager::OSVersion](#osversion)|表示操作系统版本的枚举类型。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[IResourceManager::CreateNodeTopology](#createnodetopology)|仅在调试中的当前版本的运行时，此方法旨在便于测试资源管理器的不同硬件拓扑，而无需匹配的配置的实际硬件上的测试挂钩。 使用零售版本的运行时，此方法将返回而不执行任何操作。|
|[IResourceManager::GetAvailableNodeCount](#getavailablenodecount)|返回可供资源管理器使用的节点数。|
|[IResourceManager::GetFirstNode](#getfirstnode)|按照资源管理器的定义，返回枚举顺序中的第一个节点。|
|[IResourceManager::Reference](#reference)|资源管理器实例的引用计数会递增。|
|[IResourceManager::RegisterScheduler](#registerscheduler)|注册计划程序与资源管理器。 计划程序在注册后，应与资源管理器使用通信`ISchedulerProxy`返回的接口。|
|[IResourceManager::Release](#release)|递减引用计数在资源管理器实例。 资源管理器被销毁时其引用计数变为`0`。|

## <a name="remarks"></a>备注

使用[CreateResourceManager](concurrency-namespace-functions.md)函数来获取接口的单一实例资源管理器实例。 方法递增引用计数在资源管理器中，并应调用[iresourcemanager:: Release](#release)方法来完成与资源管理器时释放该引用。 通常情况下，创建每个计划程序将在创建期间，调用此方法，并关闭后发布到资源管理器的引用。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IResourceManager`

## <a name="requirements"></a>要求

**标头：** concrtrm.h

**命名空间：** 并发

##  <a name="createnodetopology"></a>  Iresourcemanager:: Createnodetopology 方法

仅在调试中的当前版本的运行时，此方法旨在便于测试资源管理器的不同硬件拓扑，而无需匹配的配置的实际硬件上的测试挂钩。 使用零售版本的运行时，此方法将返回而不执行任何操作。

```
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```

### <a name="parameters"></a>参数

*nodeCount*<br/>
模拟的处理器节点数。

*pCoreCount*<br/>
一个数组，指定每个节点上的内核数。

*pNodeDistance*<br/>
指定任意两个节点之间的距离矩阵。 此参数可以具有值`NULL`。

*pProcessorGroups*<br/>
所属的每个节点指定处理器组的数组。

### <a name="remarks"></a>备注

[invalid_argument](../../../standard-library/invalid-argument-class.md)如果引发参数`nodeCount`具有值`0`传递中，或者，如果该参数`pCoreCount`的值`NULL`。

[invalid_operation](invalid-operation-class.md)如果在其他计划程序存在于进程时调用此方法将引发。

##  <a name="getavailablenodecount"></a>  Iresourcemanager:: Getavailablenodecount 方法

返回可供资源管理器使用的节点数。

```
virtual unsigned int GetAvailableNodeCount() const = 0;
```

### <a name="return-value"></a>返回值

到资源管理器中可用的节点数。

##  <a name="getfirstnode"></a>  Iresourcemanager:: Getfirstnode 方法

按照资源管理器的定义，返回枚举顺序中的第一个节点。

```
virtual ITopologyNode* GetFirstNode() const = 0;
```

### <a name="return-value"></a>返回值

资源管理器定义的枚举顺序中的第一个节点。

##  <a name="osversion"></a>  Iresourcemanager:: Osversion 枚举

表示操作系统版本的枚举类型。

```
enum OSVersion;
```

##  <a name="reference"></a>  Iresourcemanager:: Reference 方法

资源管理器实例的引用计数会递增。

```
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>返回值

在生成的引用计数。

##  <a name="registerscheduler"></a>  Iresourcemanager:: Registerscheduler 方法

注册计划程序与资源管理器。 计划程序在注册后，应与资源管理器使用通信`ISchedulerProxy`返回的接口。

```
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```

### <a name="parameters"></a>参数

*pScheduler*<br/>
`IScheduler`到调度器注册接口。

*版本*<br/>
通信接口的版本使用计划程序进行通信使用资源管理器。 使用的是版本允许资源管理器，同时允许计划程序以获取访问权限向较旧的功能改进的通信接口。 想要使用 Visual Studio 2010 中存在的资源管理器功能的计划程序应使用版本`CONCRT_RM_VERSION_1`。

### <a name="return-value"></a>返回值

`ISchedulerProxy`资源管理器已与你的计划程序关联的接口。 你的计划程序应使用此接口将使用资源管理器从该点上。

### <a name="remarks"></a>备注

使用此方法来启动与资源管理器的通信。 该方法将相关联`IScheduler`与你的计划程序的接口`ISchedulerProxy`接口和人工回给您。 若要请求执行资源以供你的计划程序，或订阅线程使用资源管理器，可以使用返回的接口。 资源管理器将使用从返回的计划程序策略的策略元素[ischeduler:: Getpolicy](ischeduler-structure.md#getpolicy)方法，以确定哪种类型的线程计划程序将需要执行工作。 如果你`SchedulerKind`策略的注册表项具有值`UmsThreadDefault`作为值策略范围返回读取的值和`UmsThreadDefault`，则`IScheduler`接口传递给该方法必须是`IUMSScheduler`接口。

该方法将引发`invalid_argument`异常如果参数`pScheduler`具有值`NULL`或者，如果该参数`version`不是有效的通信接口的版本。

##  <a name="release"></a>  Iresourcemanager:: Release 方法

递减引用计数在资源管理器实例。 资源管理器被销毁时其引用计数变为`0`。

```
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>返回值

在生成的引用计数。

## <a name="see-also"></a>请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[ISchedulerProxy 结构](ischedulerproxy-structure.md)<br/>
[IScheduler 结构](ischeduler-structure.md)
