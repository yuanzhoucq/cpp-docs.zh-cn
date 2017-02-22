---
title: "ITopologyNode 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrtrm/concurrency::ITopologyNode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ITopologyNode 结构"
ms.assetid: 92e7e032-04f6-4c7c-be36-8f9a35fc4734
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# ITopologyNode 结构
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

为拓扑节点的接口所定义的资源管理器。   节点包含一个或多个执行资源。  
  
## 语法  
  
```  
struct ITopologyNode;  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[ITopologyNode::GetExecutionResourceCount 方法](../Topic/ITopologyNode::GetExecutionResourceCount%20Method.md)|返回执行资源的数量进行分组在此节点下。|  
|[ITopologyNode::GetFirstExecutionResource 方法](../Topic/ITopologyNode::GetFirstExecutionResource%20Method.md)|返回第一执行资源组合在枚举顺序中的此节点下。|  
|[ITopologyNode::GetId 方法](../Topic/ITopologyNode::GetId%20Method.md)|返回此节点的资源管理器的唯一标识符。|  
|[ITopologyNode::GetNext 方法](../Topic/ITopologyNode::GetNext%20Method.md)|返回接口为枚举顺序的拓扑节点下。|  
|[ITopologyNode::GetNumaNode 方法](../Topic/ITopologyNode::GetNumaNode%20Method.md)|返回窗口分配 NUMA 此资源 Maanger 节点所属的节点号。|  
  
## 备注  
 此接口通常使用的系统的拓扑作为资源管理器观察。  
  
## 继承层次结构  
 `ITopologyNode`  
  
## 要求  
 **标头：**concrtrm.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)