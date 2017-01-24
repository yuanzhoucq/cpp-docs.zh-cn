---
title: "CEvent Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CEvent"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CEvent class"
  - "同步类, CEvent class"
  - "synchronization objects, event"
ms.assetid: df676042-ce27-4702-800a-e73ff4f44395
caps.latest.revision: 27
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CEvent Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示一个事件，是同步对象允许一个线程通知另一个操作的。  
  
## 语法  
  
```  
class CEvent : public CSyncObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CEvent::CEvent](../Topic/CEvent::CEvent.md)|构造 `CEvent` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CEvent::PulseEvent](../Topic/CEvent::PulseEvent.md)|将等待线程的活动为可用\(终止\)，版本，并将事件设置可用\(nonsignaled）。|  
|[CEvent::ResetEvent](../Topic/CEvent::ResetEvent.md)|将事件设置可用\(nonsignaled）。|  
|[CEvent::SetEvent](../Topic/CEvent::SetEvent.md)|将事件设置可用\(终止\)和版本所有等待线程。|  
|[CEvent::Unlock](../Topic/CEvent::Unlock.md)|释放事件对象。|  
  
## 备注  
 当线程时必须知道执行其任务时，事件非常有用。  例如，复制的线程传递数据的数据存档必须注意，在新数据可用时。  通过使用通知该副本的 `CEvent` 对象的线程，在新数据可用，线程可以尽快执行其任务。  
  
 `CEvent` 对象有两种类型:手动和自动。  
  
 一个自 `CEvent` 对象自动恢复为非终止\(可用\)状态，在释放后至少有一个线程。  默认情况下，除非在构造期间，通过 `bManualReset` 参数的 `TRUE``CEvent` 对象是自动的。  
  
 准则 `CEvent` 对象在 [SetEvent](../Topic/CEvent::SetEvent.md) 或 [ResetEvent](../Topic/CEvent::ResetEvent.md) 设置的状态保持，直到另一个函数调用。  若要创建手动 `CEvent` 对象，请在构造时传递 `bManualReset` 参数的 `TRUE`。  
  
 在需要时，要使用 `CEvent` 对象，请构造 `CEvent` 对象。  指定要等待事件的名称，并指定应用程序最初应拥有它。  当构造函数返回时，您可以访问该事件。  调用 [SetEvent](../Topic/CEvent::SetEvent.md) 发出信号\(可用时\)事件对象并调用 [unlock](../Topic/CEvent::Unlock.md)，在执行这种访问受控资源后。  
  
 另一种方法用于 `CEvent` 对象将添加 `CEvent` 类型的变量，要控件的选件类的数据成员。  在控制构造对象时，只需调用 `CEvent` 数据成员的构造函数并指定事件最初是否收到信号，然后的事件对象的specifythe类型需要，事件的名称\(如果它将用作进程边界\)和所需的任何安全特性。  
  
 访问 `CEvent` 对象来控件的资源，首先创建类型 [CSingleLock](../../mfc/reference/csinglelock-class.md) 的变量或键入在资源访问方法的 [CMultiLock](../../mfc/reference/cmultilock-class.md)。  然后调用锁定对象\(例如，[CMultiLock::Lock](../Topic/CMultiLock::Lock.md)\)的 `Lock` 方法。  此时，您的线程对该资源将能够访问，等待资源释放并且能够访问或等待资源释放，时间和未对该资源的访问权。  在任一情况下，您的资源访问了采用线程安全的方式。  若要释放资源，调用 `SetEvent` 用于通知事件对象，然后使用锁定对象的 `Unlock` 方法\(例如，[CMultiLock::Unlock](../Topic/CMultiLock::Unlock.md)\)，或者允许锁定对象由超出范围。  
  
 有关如何使用 `CEvent` 对象的更多信息，请参见 [多线程处理：如何使用同步类](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## 示例  
 [!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/CPP/cevent-class_1.cpp)]  
  
 [!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/CPP/cevent-class_2.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CEvent`  
  
## 要求  
 **Header:** afxmt.h  
  
## 请参阅  
 [CSyncObject Class](../../mfc/reference/csyncobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)