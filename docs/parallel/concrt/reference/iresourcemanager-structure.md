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
ms.openlocfilehash: 15e27a586fc039791255c01a053f6a1109183f90
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368184"
---
# <a name="iresourcemanager-structure"></a>IResourceManager 结构

并发运行时的资源管理器的接口。 这是计划程序与资源管理器进行通信的接口。

## <a name="syntax"></a>语法

```cpp
struct IResourceManager;
```

## <a name="members"></a>成员

### <a name="public-enumerations"></a>公共枚举

|名称|说明|
|----------|-----------------|
|[I 资源管理器：OSVersion](#osversion)|表示操作系统版本的枚举类型。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[I 资源管理器：：创建节点拓扑](#createnodetopology)|此方法仅在运行时的调试版本中存在，它是一个测试挂钩，旨在方便在不同硬件拓扑上测试资源管理器，而无需实际硬件匹配配置。 使用运行时的零售生成时，此方法将返回而不执行任何操作。|
|[I 资源管理器：：获取可用节点计数](#getavailablenodecount)|返回可供资源管理器使用的节点数。|
|[I 资源管理器：：获取第一节点](#getfirstnode)|按照资源管理器的定义，返回枚举顺序中的第一个节点。|
|[I资源管理器：参考](#reference)|增加资源管理器实例上的引用计数。|
|[I资源管理器：：注册时间表](#registerscheduler)|向资源管理器注册计划程序。 注册计划程序后，它应使用返回的`ISchedulerProxy`接口与资源管理器通信。|
|[I 资源管理器：：发布](#release)|在资源管理器实例上取消引用计数。 当资源管理器的引用计数转到`0`时，它将被销毁。|

## <a name="remarks"></a>备注

使用[CreateResourceManager](concurrency-namespace-functions.md)函数获取与单一资源管理器实例的接口。 该方法将引用计数递增到资源管理器上，您应该调用[IResourceManager：：：释放](#release)方法，在使用资源管理器时释放引用。 通常，您创建的每个计划程序将在创建期间调用此方法，并在资源管理器关闭后释放对资源管理器的引用。

## <a name="inheritance-hierarchy"></a>继承层次结构

`IResourceManager`

## <a name="requirements"></a>要求

**标题：** concrtrm.h

**命名空间：** 并发

## <a name="iresourcemanagercreatenodetopology-method"></a><a name="createnodetopology"></a>I资源管理器：：创建节点拓扑方法

此方法仅在运行时的调试版本中存在，它是一个测试挂钩，旨在方便在不同硬件拓扑上测试资源管理器，而无需实际硬件匹配配置。 使用运行时的零售生成时，此方法将返回而不执行任何操作。

```cpp
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```

### <a name="parameters"></a>参数

*节点计数*<br/>
正在模拟的处理器节点数。

*pCoreCount*<br/>
指定每个节点上的内核数的数组。

*pNode 距离*<br/>
指定任意两个节点之间的节点距离的矩阵。 此参数可以具有 值`NULL`。

*p处理器组*<br/>
指定每个节点所属的处理器组的数组。

### <a name="remarks"></a>备注

如果`nodeCount`参数已`0`传入值，或者参数`pCoreCount`具有 值`NULL`，则引发[invalid_argument。](../../../standard-library/invalid-argument-class.md)

如果调用此方法，而进程中存在其他计划程序，则引发[invalid_operation。](invalid-operation-class.md)

## <a name="iresourcemanagergetavailablenodecount-method"></a><a name="getavailablenodecount"></a>I 资源管理器：：获取可用节点计数方法

返回可供资源管理器使用的节点数。

```cpp
virtual unsigned int GetAvailableNodeCount() const = 0;
```

### <a name="return-value"></a>返回值

资源管理器可用的节点数。

## <a name="iresourcemanagergetfirstnode-method"></a><a name="getfirstnode"></a>I资源管理器：获取第一节点方法

按照资源管理器的定义，返回枚举顺序中的第一个节点。

```cpp
virtual ITopologyNode* GetFirstNode() const = 0;
```

### <a name="return-value"></a>返回值

资源管理器定义的枚举顺序中的第一个节点。

## <a name="iresourcemanagerosversion-enumeration"></a><a name="osversion"></a>I 资源管理器：：OSversion 枚举

表示操作系统版本的枚举类型。

```cpp
enum OSVersion;
```

## <a name="iresourcemanagerreference-method"></a><a name="reference"></a>I资源管理器：参考方法

增加资源管理器实例上的引用计数。

```cpp
virtual unsigned int Reference() = 0;
```

### <a name="return-value"></a>返回值

生成的引用计数。

## <a name="iresourcemanagerregisterscheduler-method"></a><a name="registerscheduler"></a>I资源管理器：：注册调度器方法

向资源管理器注册计划程序。 注册计划程序后，它应使用返回的`ISchedulerProxy`接口与资源管理器通信。

```cpp
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```

### <a name="parameters"></a>参数

*p时间*<br/>
要`IScheduler`注册的计划程序的接口。

*version*<br/>
计划程序用于与资源管理器通信的通信接口的版本。 使用版本允许资源管理器发展通信接口，同时允许计划程序访问较旧的功能。 希望使用 Visual Studio 2010 中存在的资源管理器功能的计划程序应使用版本`CONCRT_RM_VERSION_1`。

### <a name="return-value"></a>返回值

资源管理器`ISchedulerProxy`与您的计划程序关联的接口。 此时，您的计划程序应使用此接口与资源管理器进行通信。

### <a name="remarks"></a>备注

使用此方法启动与资源管理器的通信。 该方法将计划程序`IScheduler`的接口与接口关联`ISchedulerProxy`，并将其交还给您。 您可以使用返回的接口请求执行资源供计划程序使用，或者与资源管理器订阅线程。 资源管理器将使用[I-计划器返回](ischeduler-structure.md#getpolicy)的计划程序策略的策略元素来确定计划程序执行工作所需的线程类型。 `SchedulerKind`如果策略`UmsThreadDefault`键具有该值，并且该值作为值`UmsThreadDefault`从策略中读出，则传递给 方法`IScheduler`的接口必须是接口`IUMSScheduler`。

`invalid_argument`如果参数`pScheduler`具有值`NULL`或参数`version`不是通信接口的有效版本，则该方法将引发异常。

## <a name="iresourcemanagerrelease-method"></a><a name="release"></a>I资源管理器：：发布方法

在资源管理器实例上取消引用计数。 当资源管理器的引用计数转到`0`时，它将被销毁。

```cpp
virtual unsigned int Release() = 0;
```

### <a name="return-value"></a>返回值

生成的引用计数。

## <a name="see-also"></a>另请参阅

[concurrency 命名空间](concurrency-namespace.md)<br/>
[ISchedulerProxy 结构](ischedulerproxy-structure.md)<br/>
[IScheduler 结构](ischeduler-structure.md)
