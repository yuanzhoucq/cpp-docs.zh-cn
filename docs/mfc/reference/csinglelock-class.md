---
title: "CSingleLock Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSingleLock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSingleLock class"
  - "synchronization objects, 访问控制"
  - "线程处理 [MFC], 访问控制"
  - "线程处理 [MFC], 同步"
ms.assetid: 7dae7288-8066-4a3e-85e0-78d28bfc6bc8
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CSingleLock Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示多线程程序中用于控制对一个资源的访问的访问控制机制。  
  
## 语法  
  
```  
  
class CSingleLock  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CSingleLock::CSingleLock](../Topic/CSingleLock::CSingleLock.md)|构造 `CSingleLock` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CSingleLock::IsLocked](../Topic/CSingleLock::IsLocked.md)|确定对象是否锁定。|  
|[CSingleLock::Lock](../Topic/CSingleLock::Lock.md)|在同步对象的等待。|  
|[CSingleLock::Unlock](../Topic/CSingleLock::Unlock.md)|发布同步对象。|  
  
## 备注  
 `CSingleLock` 没有基类。  
  
 为了使用同步选件类 [CSemaphore](../../mfc/reference/csemaphore-class.md)，[CMutex](../../mfc/reference/cmutex-class.md)、 [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)和 [CEvent](../../mfc/reference/cevent-class.md)，必须创建 `CSingleLock` 或 [CMultiLock](../../mfc/reference/cmultilock-class.md) 对象到等待和发布同步对象。  当您在对象只需一次时，等待请使用 `CSingleLock`。  请使用 **CMultiLock** ，当有可以在特定时间使用的多个对象。  
  
 若要使用 `CSingleLock` 对象，请调用其在一个成员函数内构造函数在受控资源的选件类。  然后调用 [IsLocked](../Topic/CSingleLock::IsLocked.md) 成员函数确定该资源是否可用。  如果是，请继续成员函数的其余部分。  如果资源不可用，请等待资源的经过指定时释放或返回失败。  该资源的使用后完成的，或调用 [unlock](../Topic/CSingleLock::Unlock.md) 功能，如果要再次使用 `CSingleLock` 对象，以允许 `CSingleLock` 对象被销毁。  
  
 `CSingleLock` 对象需要从 [CSyncObject](../../mfc/reference/csyncobject-class.md)派生的对象的显示。  这通常是受控资源的选件类的数据成员。  有关如何使用 `CSingleLock` 对象的更多信息，请参见文章 [多线程处理:如何使用同步类选件](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## 继承层次结构  
 `CSingleLock`  
  
## 要求  
 **Header:** afxmt.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CMultiLock Class](../../mfc/reference/cmultilock-class.md)