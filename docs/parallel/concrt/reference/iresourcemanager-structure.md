---
title: IResourceManager 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- IResourceManager structure
ms.assetid: 3dd5ec2c-fe53-4121-ae77-1bc1d1167ff4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: afd87a71c8f5d41e38f6a1b18be96a7bab8f3bb8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33693492"
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
|[IResourceManager::CreateNodeTopology](#createnodetopology)|仅在调试中的存在的运行时版本，此方法是旨在促进测试资源管理器的不同硬件拓扑，而无需实际相匹配的配置的硬件上测试挂钩。 使用的运行时的零售版本，此方法将返回而不执行任何操作。|  
|[IResourceManager::GetAvailableNodeCount](#getavailablenodecount)|返回可供资源管理器使用的节点数。|  
|[IResourceManager::GetFirstNode](#getfirstnode)|按照资源管理器的定义，返回枚举顺序中的第一个节点。|  
|[IResourceManager::Reference](#reference)|递增上的资源管理器实例的引用计数。|  
|[IResourceManager::RegisterScheduler](#registerscheduler)|注册计划程序与资源管理器。 调度器注册后，它应与资源管理器使用`ISchedulerProxy`返回的接口。|  
|[IResourceManager::Release](#release)|递减引用计数在资源管理器实例上。 资源管理器被销毁时其引用计数变为`0`。|  
  
## <a name="remarks"></a>备注  
 使用[CreateResourceManager](concurrency-namespace-functions.md)函数来获取单一资源管理器实例的接口。 该方法递增引用计数在资源管理器中，并应调用[iresourcemanager:: Release](#release)方法来完成与资源管理器后释放该引用。 通常情况下，你创建每个计划程序将在创建期间，调用此方法并释放该引用到资源管理器中之后它会关闭。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IResourceManager`  
  
## <a name="requirements"></a>要求  
 **标头：** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="createnodetopology"></a>  Iresourcemanager:: Createnodetopology 方法  
 仅在调试中的存在的运行时版本，此方法是旨在促进测试资源管理器的不同硬件拓扑，而无需实际相匹配的配置的硬件上测试挂钩。 使用的运行时的零售版本，此方法将返回而不执行任何操作。  
  
```
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```  
  
### <a name="parameters"></a>参数  
 `nodeCount`  
 模拟的处理器节点数。  
  
 `pCoreCount`  
 一个数组，每个节点上指定的内核数。  
  
 `pNodeDistance`  
 指定任何两个节点的节点距离矩阵。 此参数可以具有值`NULL`。  
  
 `pProcessorGroups`  
 所属的每个节点指定的处理器组的数组。  
  
### <a name="remarks"></a>备注  
 [invalid_argument](../../../standard-library/invalid-argument-class.md)如果引发参数`nodeCount`具有值`0`传入，或如果参数`pCoreCount`具有值`NULL`。  
  
 [invalid_operation](invalid-operation-class.md)如果在其他计划程序存在于进程时调用此方法引发。  
  
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
 通过资源管理器中定义的枚举顺序中的第一个节点。  
  
##  <a name="iresourcemanager__osversion"></a>  Iresourcemanager:: Osversion 枚举  
 表示操作系统版本的枚举类型。  
  
```
enum OSVersion;
```  
  
##  <a name="reference"></a>  Iresourcemanager:: Reference 方法  
 递增上的资源管理器实例的引用计数。  
  
```
virtual unsigned int Reference() = 0;
```  
  
### <a name="return-value"></a>返回值  
 在生成的引用计数。  
  
##  <a name="registerscheduler"></a>  Iresourcemanager:: Registerscheduler 方法  
 注册计划程序与资源管理器。 调度器注册后，它应与资源管理器使用`ISchedulerProxy`返回的接口。  
  
```
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```  
  
### <a name="parameters"></a>参数  
 `pScheduler`  
 `IScheduler`到调度器要注册的接口。  
  
 `version`  
 通信接口的版本使用计划程序与资源管理器进行通信。 使用版本允许资源管理器演化通信接口，同时允许计划程序以获取向较旧的功能的访问权限。 想要使用 Visual Studio 2010 中提供的资源管理器功能的计划程序应使用版本`CONCRT_RM_VERSION_1`。  
  
### <a name="return-value"></a>返回值  
 `ISchedulerProxy`资源管理器已与你的计划程序关联的接口。 您的计划程序应使用此接口与使用资源管理器上从该点通信。  
  
### <a name="remarks"></a>备注  
 使用此方法来启动与资源管理器的通信。 该方法将关联`IScheduler`具有你计划程序的接口`ISchedulerProxy`接口和人工回给您。 你可以使用返回的接口，以便请求执行资源以供您的计划程序，或订阅线程与资源管理器。 资源管理器将使用从返回的计划程序策略的策略元素[ischeduler:: Getpolicy](ischeduler-structure.md#getpolicy)方法来确定哪种类型的线程计划程序将需要执行工作。 如果你`SchedulerKind`策略密钥具有值`UmsThreadDefault`和从作为值策略传回读取值`UmsThreadDefault`、`IScheduler`传递给方法的接口必须是`IUMSScheduler`接口。  
  
 该方法将引发`invalid_argument`异常如果参数`pScheduler`具有值`NULL`或者，如果参数`version`不是有效的通信接口版本。  
  
##  <a name="release"></a>  Iresourcemanager:: Release 方法  
 递减引用计数在资源管理器实例上。 资源管理器被销毁时其引用计数变为`0`。  
  
```
virtual unsigned int Release() = 0;
```  
  
### <a name="return-value"></a>返回值  
 在生成的引用计数。  
  
## <a name="see-also"></a>请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [ISchedulerProxy 结构](ischedulerproxy-structure.md)   
 [IScheduler 结构](ischeduler-structure.md)
