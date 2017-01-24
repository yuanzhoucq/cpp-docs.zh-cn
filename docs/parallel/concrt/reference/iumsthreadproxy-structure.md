---
title: "IUMSThreadProxy 结构 | Microsoft Docs"
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
  - "concrtrm/concurrency::IUMSThreadProxy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IUMSThreadProxy 结构"
ms.assetid: 61c69b7e-5c37-4048-bcb4-e75c536afd86
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IUMSThreadProxy 结构
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

执行线程的抽象。  如果要为计划程序授予用户模式可计划 \(UMS\) 线程，则将计划程序策略元素 `SchedulerKind` 的值设置为 `UmsThreadDefault`，并实现 `IUMSScheduler` 接口。  UMS 线程仅在版本为 Windows 7 或更高版本的 64 位操作系统上支持。  
  
## 语法  
  
```  
struct IUMSThreadProxy : public IThreadProxy;  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[IUMSThreadProxy::EnterCriticalRegion 方法](../Topic/IUMSThreadProxy::EnterCriticalRegion%20Method.md)|调用以输入关键区域。  在关键的区域内时，计划程序将不遵循该区域中发生的异步阻止操作。  这意味着计划程序将不再重新进入 UMS 线程的页面错误、线程挂起、内核异步过程调用 \(APC\) 等。|  
|[IUMSThreadProxy::EnterHyperCriticalRegion 方法](../Topic/IUMSThreadProxy::EnterHyperCriticalRegion%20Method.md)|调用以输入超关键区域。  在超关键的区域内时，计划程序将不遵循该区域中发生的任何阻止操作。  这意味着计划程序将不再重新进入 UMS 线程的阻止函数调用、阻止锁定获取尝试、页面错误、线程挂起、内核异步过程调用 \(APC\) 等。|  
|[IUMSThreadProxy::ExitCriticalRegion 方法](../Topic/IUMSThreadProxy::ExitCriticalRegion%20Method.md)|调用以退出关键区域。|  
|[IUMSThreadProxy::ExitHyperCriticalRegion 方法](../Topic/IUMSThreadProxy::ExitHyperCriticalRegion%20Method.md)|调用以退出超关键区域。|  
|[IUMSThreadProxy::GetCriticalRegionType 方法](../Topic/IUMSThreadProxy::GetCriticalRegionType%20Method.md)|返回线程代理所处的关键区域的类型。  因为超关键区域是关键区域的超集，如果代码已输入关键区域，然后输入了超关键区域，将返回 `InsideHyperCriticalRegion`。|  
  
## 继承层次结构  
 [IThreadProxy](../../../parallel/concrt/reference/ithreadproxy-structure.md)  
  
 `IUMSThreadProxy`  
  
## 要求  
 **标头：**concrtrm.h  
  
 **命名空间：**并发  
  
## 请参阅  
 [concurrency 命名空间](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [IUMSScheduler 结构](../../../parallel/concrt/reference/iumsscheduler-structure.md)   
 [SchedulerType 枚举](../Topic/SchedulerType%20Enumeration.md)