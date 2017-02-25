---
title: "CThreadPool Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CThreadPool"
  - "ATL::CThreadPool"
  - "CThreadPool"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CThreadPool class"
ms.assetid: 06683718-01b9-413c-9481-2dc1734ec70f
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CThreadPool Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类提供的辅助线程池处理工作项队列。  
  
## 语法  
  
```  
  
      template <  
   class Worker,  
   class ThreadTraits = DefaultThreadTraits  
>  
class CThreadPool :  
   public IThreadPoolConfig  
```  
  
#### 参数  
 *辅助*  
 与提供代码的 [辅助原型](../../atl/reference/worker-archetype.md) 的选件类用于在线程池队列的处理工作项。  
  
 `ThreadTraits`  
 提供功能的选件类创建线程在池。  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CThreadPool::CThreadPool](../Topic/CThreadPool::CThreadPool.md)|线程池的构造函数。|  
|[CThreadPool::~CThreadPool](../Topic/CThreadPool::~CThreadPool.md)|线程池的析构函数。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CThreadPool::AddRef](../Topic/CThreadPool::AddRef.md)|`IUnknown::AddRef` 的实现。|  
|[CThreadPool::GetNumThreads](../Topic/CThreadPool::GetNumThreads.md)|调用此方法获取线程数。该池的。|  
|[CThreadPool::GetQueueHandle](../Topic/CThreadPool::GetQueueHandle.md)|调用此方法获取用于IO的完成端口的处理排队工作项。|  
|[CThreadPool::GetSize](../Topic/CThreadPool::GetSize.md)|调用此方法获取线程数。该池的。|  
|[CThreadPool::GetTimeout](../Topic/CThreadPool::GetTimeout.md)|在毫秒调用此方法以获得最大时间线程池将等待线程关闭。|  
|[CThreadPool::Initialize](../Topic/CThreadPool::Initialize.md)|调用此方法来初始化线程池。|  
|[CThreadPool::QueryInterface](../Topic/CThreadPool::QueryInterface.md)|**IUnknown::QueryInterface**的实现。|  
|[CThreadPool::QueueRequest](../Topic/CThreadPool::QueueRequest.md)|调用此方法使在该池的线程要处理的工作项。|  
|[CThreadPool::Release](../Topic/CThreadPool::Release.md)|`IUnknown::Release` 的实现。|  
|[CThreadPool::SetSize](../Topic/CThreadPool::SetSize.md)|调用此方法设置线程数。该池的。|  
|[CThreadPool::SetTimeout](../Topic/CThreadPool::SetTimeout.md)|在毫秒调用此方法设置最长时间线程池将等待线程关闭。|  
|[CThreadPool::Shutdown](../Topic/CThreadPool::Shutdown.md)|调用此方法关闭线程池。|  
  
## 备注  
 在池中的线程创建和销毁该池时初始化，调整大小或关闭。  选件类 *辅助* 实例在堆栈中创建每个辅助线程在池。  每个实例为线程的生存期将中。  
  
 在线程的创建之后，Worker::`Initialize` 要对对象与该线程。  在线程的损坏之前，Worker::`Terminate` 将调用。  两个方法必须接受 **void\*** 参数。  此参数的值传递给线程池 [CThreadPool::Initialize](../Topic/CThreadPool::Initialize.md)的 `pvWorkerParam` 参数。  
  
 当在队列中的工作项，以及辅助线程可用的工作，辅助线程将拉项队列并调用 *辅助* 对象的 **Execute** 方法该线程上。  三个项目并传递给方法:从队列中的项目，对于 `pvWorkerParam` 传递给Worker::`Initialize` 和Worker::`Terminate`，并且，对于 [重叠](http://msdn.microsoft.com/library/windows/desktop/ms684342) 结构的指针为IO完成端口队列改用。  
  
 *辅助* 选件类声明在线程池要排队通过提供typedef项类型，Worker::`RequestType`。  此类型必须能够转换来回 **ULONG\_PTR**。  
  
 *辅助* 选件类的一个示例是 [CNonStatelessWorker Class](../../atl/reference/cnonstatelessworker-class.md)。  
  
## 继承层次结构  
 `IUnknown`  
  
 [IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)  
  
 `CThreadPool`  
  
## 要求  
 **Header:** atlutil.h  
  
## 请参阅  
 [IThreadPoolConfig Interface](../../atl/reference/ithreadpoolconfig-interface.md)   
 [DefaultThreadTraits](../Topic/DefaultThreadTraits.md)   
 [类](../../atl/reference/atl-classes.md)