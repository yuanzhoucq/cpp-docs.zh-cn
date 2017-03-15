---
title: "IResourceManager 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrtrm/concurrency::IResourceManager
dev_langs:
- C++
helpviewer_keywords:
- IResourceManager structure
ms.assetid: 3dd5ec2c-fe53-4121-ae77-1bc1d1167ff4
caps.latest.revision: 20
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
ms.openlocfilehash: fb523127f60c4e8cd45b2525749b536ad55849b0
ms.lasthandoff: 02/24/2017

---
# <a name="iresourcemanager-structure"></a>IResourceManager 结构
并发运行时的资源管理器的接口。 这是计划程序与资源管理器进行通信的接口。  
  
## <a name="syntax"></a>语法  
  
```
struct IResourceManager;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-enumerations"></a>公共枚举  
  
|名称|说明|  
|----------|-----------------|  
|[Iresourcemanager:: Osversion 枚举](#osversion)|表示操作系统版本的枚举类型。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[Iresourcemanager:: Createnodetopology 方法](#createnodetopology)|仅在调试中的当前版本的运行时，此方法旨在促进测试资源管理器的不同硬件拓扑，而无需与配置匹配的实际硬件上的测试挂钩。 与零售版本的运行时，此方法将返回不执行任何操作。|  
|[Iresourcemanager:: Getavailablenodecount 方法](#getavailablenodecount)|返回可供资源管理器使用的节点数。|  
|[Iresourcemanager:: Getfirstnode 方法](#getfirstnode)|按照资源管理器的定义，返回枚举顺序中的第一个节点。|  
|[Iresourcemanager:: Reference 方法](#reference)|递增上的资源管理器实例的引用计数。|  
|[Iresourcemanager:: Registerscheduler 方法](#registerscheduler)|注册计划程序与资源管理器。 计划程序注册后，应与资源管理器使用通信`ISchedulerProxy`返回的接口。|  
|[Iresourcemanager:: Release 方法](#release)|的资源管理器实例的引用计数递减。 资源管理器时的引用计数归销毁`0`。|  
  
## <a name="remarks"></a>备注  
 使用[CreateResourceManager](concurrency-namespace-functions.md)函数来获取一个指向单一资源管理器实例的接口。 该方法递增引用计数在资源管理器中，并应调用[iresourcemanager:: Release](#release)方法来完成与资源管理器时释放该引用。 通常情况下，您创建每个计划程序将在创建期间，调用此方法并释放该引用到资源管理器中之后它会关闭。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `IResourceManager`  
  
## <a name="requirements"></a>要求  
 **标头︰** concrtrm.h  
  
 **命名空间：** 并发  
  
##  <a name="a-namecreatenodetopologya--iresourcemanagercreatenodetopology-method"></a><a name="createnodetopology"></a>Iresourcemanager:: Createnodetopology 方法  
 仅在调试中的当前版本的运行时，此方法旨在促进测试资源管理器的不同硬件拓扑，而无需与配置匹配的实际硬件上的测试挂钩。 与零售版本的运行时，此方法将返回不执行任何操作。  
  
```
virtual void CreateNodeTopology(
    unsigned int nodeCount,
    _In_reads_(nodeCount) unsigned int* pCoreCount,
    _In_reads_opt_(nodeCount) unsigned int** pNodeDistance,
    _In_reads_(nodeCount) unsigned int* pProcessorGroups) = 0;
```  
  
### <a name="parameters"></a>参数  
 `nodeCount`  
 正被模拟的处理器节点数。  
  
 `pCoreCount`  
 一个数组，指定每个节点上的内核数。  
  
 `pNodeDistance`  
 一个指定任何两个节点之间的距离的矩阵。 此参数可以具有值`NULL`。  
  
 `pProcessorGroups`  
 所属的每个节点指定处理器组的数组。  
  
### <a name="remarks"></a>备注  
 [invalid_argument](../../../standard-library/invalid-argument-class.md)时引发参数`nodeCount`具有值`0`传入，或者，如果该参数`pCoreCount`具有值`NULL`。  
  
 [invalid_operation](invalid-operation-class.md)如果在其他计划程序存在于该进程时调用此方法引发。  
  
##  <a name="a-namegetavailablenodecounta--iresourcemanagergetavailablenodecount-method"></a><a name="getavailablenodecount"></a>Iresourcemanager:: Getavailablenodecount 方法  
 返回可供资源管理器使用的节点数。  
  
```
virtual unsigned int GetAvailableNodeCount() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 对资源管理器中可用的节点数。  
  
##  <a name="a-namegetfirstnodea--iresourcemanagergetfirstnode-method"></a><a name="getfirstnode"></a>Iresourcemanager:: Getfirstnode 方法  
 按照资源管理器的定义，返回枚举顺序中的第一个节点。  
  
```
virtual ITopologyNode* GetFirstNode() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 通过资源管理器中定义的枚举顺序中的第一个节点。  
  
##  <a name="a-nameiresourcemanagerosversiona--iresourcemanagerosversion-enumeration"></a><a name="iresourcemanager__osversion"></a>Iresourcemanager:: Osversion 枚举  
 表示操作系统版本的枚举类型。  
  
```
enum OSVersion;
```  
  
##  <a name="a-namereferencea--iresourcemanagerreference-method"></a><a name="reference"></a>Iresourcemanager:: Reference 方法  
 递增上的资源管理器实例的引用计数。  
  
```
virtual unsigned int Reference() = 0;
```  
  
### <a name="return-value"></a>返回值  
 在生成的引用计数。  
  
##  <a name="a-nameregisterschedulera--iresourcemanagerregisterscheduler-method"></a><a name="registerscheduler"></a>Iresourcemanager:: Registerscheduler 方法  
 注册计划程序与资源管理器。 计划程序注册后，应与资源管理器使用通信`ISchedulerProxy`返回的接口。  
  
```
virtual ISchedulerProxy *RegisterScheduler(
    _Inout_ IScheduler* pScheduler,
    unsigned int version) = 0;
```  
  
### <a name="parameters"></a>参数  
 `pScheduler`  
 `IScheduler`要注册的计划程序的接口。  
  
 `version`  
 通信接口的版本使用计划程序进行通信与资源管理器。 使用版本允许资源管理器演化通信接口，同时让计划程序以获取较早的功能的访问权限。 想要使用 Visual Studio 2010 中提供的资源管理器功能的计划程序应使用版本`CONCRT_RM_VERSION_1`。  
  
### <a name="return-value"></a>返回值  
 `ISchedulerProxy`资源管理器已与您的计划程序关联的接口。 您的计划程序应使用此接口用于资源管理器从该点在上进行通信。  
  
### <a name="remarks"></a>备注  
 使用此方法以便启动与资源管理器的通信。 该方法将关联`IScheduler`接口与您的计划程序`ISchedulerProxy`接口和双手回给您。 若要请求执行资源以供您的计划程序，或订阅线程与资源管理器，可以使用返回的接口。 资源管理器将使用从返回的计划程序策略的策略元素[ischeduler:: Getpolicy](ischeduler-structure.md#getpolicy)方法，以确定哪种类型的线程计划程序将需要执行工作。 如果您`SchedulerKind`策略的注册表项具有值`UmsThreadDefault`作为值策略外返回读取的值和`UmsThreadDefault`、`IScheduler`接口传递给该方法必须是`IUMSScheduler`接口。  
  
 该方法将引发`invalid_argument`异常如果参数`pScheduler`具有值`NULL`或者，如果该参数`version`不是有效的通信接口的版本。  
  
##  <a name="a-namereleasea--iresourcemanagerrelease-method"></a><a name="release"></a>Iresourcemanager:: Release 方法  
 的资源管理器实例的引用计数递减。 资源管理器时的引用计数归销毁`0`。  
  
```
virtual unsigned int Release() = 0;
```  
  
### <a name="return-value"></a>返回值  
 在生成的引用计数。  
  
## <a name="see-also"></a>另请参阅  
 [并发 Namespace](concurrency-namespace.md)   
 [ISchedulerProxy 结构](ischedulerproxy-structure.md)   
 [IScheduler 结构](ischeduler-structure.md)

