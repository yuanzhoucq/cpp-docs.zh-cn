---
title: "CWorkerThread Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CWorkerThread<ThreadTraits>"
  - "ATL::CWorkerThread"
  - "ATL.CWorkerThread"
  - "ATL.CWorkerThread<ThreadTraits>"
  - "CWorkerThread"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWorkerThread class"
ms.assetid: be79a832-1345-4a36-a13e-a406cc65286f
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 27
---
# CWorkerThread Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当其中一个处理事件信号时，此选件类在一个或多个核心对象处理创建辅助线程或使用现有工作项，等待，并执行一个指定的客户端功能。  
  
> [!IMPORTANT]
>  此选件类及其成员不能在Windows运行时执行的应用程序。  
  
## 语法  
  
```  
  
      template <  
class ThreadTraits= DefaultThreadTraits  
>  
class CWorkerThread  
```  
  
#### 参数  
 `ThreadTraits`  
 提供线程创建功能，例如 [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) 或 [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)的选件类。  
  
## 成员  
  
### 受保护的结构  
  
|名称|说明|  
|--------|--------|  
|`WorkerClientEntry`||  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CWorkerThread::CWorkerThread](../Topic/CWorkerThread::CWorkerThread.md)|辅助线程的构造函数。|  
|[CWorkerThread::~CWorkerThread](../Topic/CWorkerThread::~CWorkerThread.md)|辅助线程的析构函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CWorkerThread::AddHandle](../Topic/CWorkerThread::AddHandle.md)|调用此方法将一个等待对象的句柄辅助线程维护的列表。|  
|[CWorkerThread::AddTimer](../Topic/CWorkerThread::AddTimer.md)|调用此方法将一个时间等待计时器到辅助线程维护的列表。|  
|[CWorkerThread::GetThreadHandle](../Topic/CWorkerThread::GetThreadHandle.md)|调用此方法获取辅助线程的线程处理。|  
|[CWorkerThread::GetThreadId](../Topic/CWorkerThread::GetThreadId.md)|调用此方法获取辅助线程的线程ID。|  
|[CWorkerThread::Initialize](../Topic/CWorkerThread::Initialize.md)|调用此方法初始化辅助线程。|  
|[CWorkerThread::RemoveHandle](../Topic/CWorkerThread::RemoveHandle.md)|调用此方法从等待对象列表中移除处理。|  
|[CWorkerThread::Shutdown](../Topic/CWorkerThread::Shutdown.md)|调用此方法关闭辅助线程。|  
  
## 备注  
  
### 使用CWorkerThread  
  
1.  创建此选件类实例。  
  
2.  调用 [CWorkerThread::Initialize](../Topic/CWorkerThread::Initialize.md)。  
  
3.  调用带核心对象的句柄和指针的 [CWorkerThread::AddHandle](../Topic/CWorkerThread::AddHandle.md) 到 [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)的实现。  
  
     \- 或 \-  
  
     调用带有指针的 [CWorkerThread::AddTimer](../Topic/CWorkerThread::AddTimer.md) 到 [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md)的实现。  
  
4.  该句柄或计时器事件信号时，请实现 [IWorkerThreadClient::Execute](../Topic/IWorkerThreadClient::Execute.md) 执行一些操作。  
  
5.  从等待对象列表移除对象，请调用 [CWorkerThread::RemoveHandle](../Topic/CWorkerThread::RemoveHandle.md)。  
  
6.  若要停止线程，请调用 [CWorkerThread::Shutdown](../Topic/CWorkerThread::Shutdown.md)。  
  
## 要求  
 **Header:** atlutil.h  
  
## 请参阅  
 [DefaultThreadTraits](../Topic/DefaultThreadTraits.md)   
 [类](../../atl/reference/atl-classes.md)   
 [多线程处理：创建辅助线程](../../parallel/multithreading-creating-worker-threads.md)   
 [IWorkerThreadClient Interface](../../atl/reference/iworkerthreadclient-interface.md)