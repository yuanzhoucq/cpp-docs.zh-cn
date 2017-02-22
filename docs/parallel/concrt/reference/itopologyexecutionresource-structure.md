---
title: "ITopologyExecutionResource 结构 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrtrm/concurrency::ITopologyExecutionResource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ITopologyExecutionResource 结构"
ms.assetid: e36756f7-4cd9-4fa6-ba60-23fea58ef2bf
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# ITopologyExecutionResource 结构
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

为可执行资源的接口所定义的资源管理器。  
  
## 语法  
  
```  
struct ITopologyExecutionResource;  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[ITopologyExecutionResource::GetId 方法](../Topic/ITopologyExecutionResource::GetId%20Method.md)|返回此执行资源的资源管理器的唯一标识符。|  
|[ITopologyExecutionResource::GetNext 方法](../Topic/ITopologyExecutionResource::GetNext%20Method.md)|枚举顺序返回执行资源的接口。|  
  
## 备注  
 此接口通常使用的系统的拓扑作为资源管理器观察。  
  
## 继承层次结构  
 `ITopologyExecutionResource`  
  
## 要求  
 **标头：**concrtrm.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)