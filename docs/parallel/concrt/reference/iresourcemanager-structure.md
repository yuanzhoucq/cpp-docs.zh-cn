---
title: "IResourceManager 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrtrm/concurrency::IResourceManager"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IResourceManager 结构"
ms.assetid: 3dd5ec2c-fe53-4121-ae77-1bc1d1167ff4
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# IResourceManager 结构
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

并发运行时资源管理器的接口。  这是计划程序与资源管理器通信的接口。  
  
## 语法  
  
```  
struct IResourceManager;  
```  
  
## 成员  
  
### 公共枚举  
  
|名称|说明|  
|--------|--------|  
|[IResourceManager::OSVersion 枚举](../Topic/IResourceManager::OSVersion%20Enumeration.md)|表示操作系统版本的枚举类型。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IResourceManager::CreateNodeTopology 方法](../Topic/IResourceManager::CreateNodeTopology%20Method.md)|仅在运行时的调试版本中出现，此方法是旨在简化在各个硬件拓扑上测试资源管理器的测试挂钩，而无需实际硬件与配置匹配。  使用运行时的零售内部版本，将不执行任何操作返回该方法。|  
|[IResourceManager::GetAvailableNodeCount 方法](../Topic/IResourceManager::GetAvailableNodeCount%20Method.md)|返回节点的数目。资源管理器。|  
|[IResourceManager::GetFirstNode 方法](../Topic/IResourceManager::GetFirstNode%20Method.md)|返回枚举顺序中的第一个节点作为资源管理器所定义。|  
|[IResourceManager::Reference 方法](../Topic/IResourceManager::Reference%20Method.md)|递增资源管理器上的引用数。|  
|[IResourceManager::RegisterScheduler 方法](../Topic/IResourceManager::RegisterScheduler%20Method.md)|向资源管理器注册计划程序。  注册计划程序后，它应该使用返回的 `ISchedulerProxy` 接口与资源管理器进行通信。|  
|[IResourceManager::Release 方法](../Topic/IResourceManager::Release%20Method.md)|减少此计划程序组的引用计数。  资源管理器引用计数变为 `0` 时会被破坏。|  
  
## 备注  
 使用 [CreateResourceManager](../Topic/CreateResourceManager%20Function.md) 函数来获取单一资源管理器实例的接口。  该方法递增资源管理器上的引用数，您应在完成资源管理器的操作后调用 [IResourceManager::Release](../Topic/IResourceManager::Release%20Method.md) 方法来释放该引用。  通常，您创建的每个计划程序将在创建过程中调用此方法，并在资源管理器关闭后释放该引用到资源管理器。  
  
## 继承层次结构  
 `IResourceManager`  
  
## 要求  
 **标头：**concrtrm.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [ISchedulerProxy 结构](../../../parallel/concrt/reference/ischedulerproxy-structure.md)   
 [IScheduler 结构](../../../parallel/concrt/reference/ischeduler-structure.md)