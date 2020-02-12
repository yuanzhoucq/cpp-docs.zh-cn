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
ms.openlocfilehash: 7ce5b07f5eb4272db1b00b7f0105b790ddbb28fe
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142988"
---
# <a name="iresourcemanager-structure"></a>IResourceManager 结构

并发运行时的资源管理器的接口。 这是计划程序与资源管理器进行通信的接口。

## <a name="syntax"></a>语法

```cpp
struct IResourceManager;
```

## <a name="members"></a>Members

### <a name="public-enumerations"></a>公共枚举

|名称|说明|
|----------|-----------------|
|[IResourceManager：： OSVersion](#osversion)|表示操作系统版本的枚举类型。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[IResourceManager：： CreateNodeTopology](#createnodetopology)|仅存在于运行时的调试版本中，此方法是一个测试挂钩，旨在简化不同硬件拓扑的资源管理器测试，而无需与配置匹配的实际硬件。 对于运行时的零售版本，此方法将返回，而不执行任何操作。|
|[IResourceManager：： GetAvailableNodeCount](#getavailablenodecount)|返回可供资源管理器使用的节点数。|
|[IResourceManager：： GetFirstNode](#getfirstnode)|按照资源管理器的定义，返回枚举顺序中的第一个节点。|
|[IResourceManager：： Reference](#reference)|递增资源管理器实例的引用计数。|
|[IResourceManager：： RegisterScheduler](#registerscheduler)|将计划程序注册到资源管理器。 注册计划程序后，它应使用返回的 `ISchedulerProxy` 接口与资源管理器进行通信。|
|[IResourceManager：： Release](#release)|递减资源管理器实例的引用计数。 资源管理器在其引用计数变为 `0`时被销毁。|

## <a name="remarks"></a>备注

使用[CreateResourceManager](concurrency-namespace-functions.md)函数可获取单一实例资源管理器实例的接口。 方法会递增资源管理器上的引用计数，并且应在完成资源管理器时调用[IResourceManager：： release](#release)方法来释放引用。 通常，创建的每个计划程序都将在创建过程中调用此方法，并在关闭后释放对资源管理器的引用。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IResourceManager`

## <a name="requirements"></a>要求

**标头：** concrtrm。h

**命名空间：** 并发

## <a name="createnodetopology"></a>IResourceManager：： CreateNodeTopology 方法

仅存在于运行时的调试版本中，此方法是一个测试挂钩，旨在简化不同硬件拓扑的资源管理器测试，而无需与配置匹配的实际硬件。 对于运行时的零售版本，此方法将返回，而不执行任何操作。

```cpp
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```

### <a name="parameters"></a>参数

*nodeCount*<br/>
正在模拟的处理器节点数。

*pCoreCount*<br/>
一个数组，该数组指定每个节点上的内核数。

*pNodeDistance*<br/>
一个矩阵，指定任意两个节点之间的节点距离。 此参数可以具有值 `NULL`。

*pProcessorGroups*<br/>
一个数组，该数组指定每个节点所属的处理器组。

### <a name="remarks"></a>备注

如果参数 `nodeCount` 具有传入 `0` 值，或者参数 `pCoreCount` 的值为 `NULL`，则会引发[invalid_argument](../../../standard-library/invalid-argument-class.md) 。

如果在进程中存在其他计划程序时调用此方法，则会引发[invalid_operation](invalid-operation-class.md) 。

## <a name="getavailablenodecount"></a>IResourceManager：： GetAvailableNodeCount 方法

返回可供资源管理器使用的节点数。

```cpp
virtual unsigned int GetAvailableNodeCount() const = 0;
```

### <a name="return-value"></a>返回值

可用于资源管理器的节点数。

## <a name="getfirstnode"></a>IResourceManager：： GetFirstNode 方法

按照资源管理器的定义，返回枚举顺序中的第一个节点。

```cpp
virtual ITopologyNode* GetFirstNode() const = 0;
```

### <a name="return-value"></a>返回值

由资源管理器定义的枚举顺序中的第一个节点。

## <a name="osversion"></a>IResourceManager：： OSVersion 枚举

表示操作系统版本的枚举类型。

```cpp
enum OSVersion;
```

## <a name="reference"></a>IResourceManager：： Reference 方法

递增资源管理器实例的引用计数。

```cpp
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>返回值

生成的引用计数。

## <a name="registerscheduler"></a>IResourceManager：： RegisterScheduler 方法

将计划程序注册到资源管理器。 注册计划程序后，它应使用返回的 `ISchedulerProxy` 接口与资源管理器进行通信。

```cpp
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```

### <a name="parameters"></a>参数

*pScheduler*<br/>
要注册的计划程序的 `IScheduler` 接口。

*version*<br/>
计划程序用来与资源管理器通信的通信接口版本。 使用版本允许资源管理器演化通信接口，同时允许计划程序获取对较旧功能的访问权限。 希望使用 Visual Studio 2010 中提供资源管理器功能的计划程序应使用 `CONCRT_RM_VERSION_1`版本。

### <a name="return-value"></a>返回值

资源管理器与计划程序关联的 `ISchedulerProxy` 接口。 计划程序应使用此接口从此点与资源管理器进行通信。

### <a name="remarks"></a>备注

使用此方法启动与资源管理器的通信。 方法将计划程序的 `IScheduler` 接口与 `ISchedulerProxy` 接口相关联，并将其返回给你。 您可以使用返回的接口请求执行资源以供您的计划程序使用，或者使用资源管理器订阅线程。 资源管理器将使用[IScheduler：： GetPolicy](ischeduler-structure.md#getpolicy)方法返回的计划程序策略中的策略元素来确定计划程序执行工作所需的线程类型。 如果 `SchedulerKind` 策略密钥的值 `UmsThreadDefault` 并且值被读回策略的值 `UmsThreadDefault`，则传递给该方法的 `IScheduler` 接口必须是 `IUMSScheduler` 接口。

如果参数 `pScheduler` 具有值 `NULL`，则方法会引发 `invalid_argument` 异常; 如果参数 `version` 不是通信接口的有效版本，则引发异常。

## <a name="release"></a>IResourceManager：： Release 方法

递减资源管理器实例的引用计数。 资源管理器在其引用计数变为 `0`时被销毁。

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>返回值

生成的引用计数。

## <a name="see-also"></a>另请参阅

[并发命名空间](concurrency-namespace.md)<br/>
[ISchedulerProxy 结构](ischedulerproxy-structure.md)<br/>
[IScheduler 结构](ischeduler-structure.md)
