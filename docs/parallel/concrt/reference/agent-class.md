---
title: "agent 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "agents/concurrency::agent"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "agent 类"
ms.assetid: 1b09e3d2-5e37-4966-b016-907ef1512456
caps.latest.revision: 20
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# agent 类
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

旨在用作所有独立代理的基类的类。  使用消息传递，它用于隐藏状态其他代理并与之交互。  
  
## 语法  
  
```  
class agent;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[agent::agent 构造函数](../Topic/agent::agent%20Constructor.md)|已重载。  构造代理。|  
|[agent::~agent 析构函数](../Topic/agent::~agent%20Destructor.md)|销毁代理。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[agent::cancel 方法](../Topic/agent::cancel%20Method.md)|将代理从 `agent_created` 或 `agent_runnable` 状态移到 `agent_canceled` 状态。|  
|[agent::start 方法](../Topic/agent::start%20Method.md)|将代理从 `agent_created` 状态移到 `agent_runnable` 状态，并对其进行安排以供执行。|  
|[agent::status 方法](../Topic/agent::status%20Method.md)|来自代理的状态信息的同步源。|  
|[agent::status\_port 方法](../Topic/agent::status_port%20Method.md)|来自代理的异步状态源信息。|  
|[agent::wait 方法](../Topic/agent::wait%20Method.md)|等待代理完成其任务。|  
|[agent::wait\_for\_all 方法](../Topic/agent::wait_for_all%20Method.md)|等待所有指定的代理完成其任务。|  
|[agent::wait\_for\_one 方法](../Topic/agent::wait_for_one%20Method.md)|等待任一指定的代理完成其任务。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[agent::done 方法](../Topic/agent::done%20Method.md)|将代理移到 `agent_done` 状态，表示该代理已完成。|  
|[agent::run 方法](../Topic/agent::run%20Method.md)|表示代理的主要任务。  `run` 应在派生的类中重写，并指定已启动后代理应执行的操作。|  
  
## 备注  
 有关更多信息，请参见 [异步代理](../../../parallel/concrt/asynchronous-agents.md)。  
  
## 继承层次结构  
 `agent`  
  
## 要求  
 **标头：**agents.h  
  
 **命名空间:** 并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)