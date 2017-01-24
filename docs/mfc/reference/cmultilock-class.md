---
title: "CMultiLock Class | Microsoft Docs"
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
  - "CMultiLock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMultiLock class"
  - "synchronization objects, 访问控制"
ms.assetid: c5b7c78b-1f81-4387-b7dd-2c813c5b6b61
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMultiLock Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示多线程程序中用于控制对多个资源的访问的访问控制机制。  
  
## 语法  
  
```  
class CMultiLock  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMultiLock::CMultiLock](../Topic/CMultiLock::CMultiLock.md)|构造 `CMultiLock` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMultiLock::IsLocked](../Topic/CMultiLock::IsLocked.md)|确定该数组的特定同步对象是否锁定。|  
|[CMultiLock::Lock](../Topic/CMultiLock::Lock.md)|在一些等待同步对象。|  
|[CMultiLock::Unlock](../Topic/CMultiLock::Unlock.md)|释放所有拥有的同步对象。|  
  
## 备注  
 `CMultiLock` 没有基类。  
  
 若要使用同步选件类 [CSemaphore](../../mfc/reference/csemaphore-class.md)，[CMutex](../../mfc/reference/cmutex-class.md)和 [CEvent](../../mfc/reference/cevent-class.md)，可以创建到等待的一 **CMultiLock** 或 [CSingleLock](../../mfc/reference/csinglelock-class.md) 对象和发布同步对象。  请使用 **CMultiLock** ，当有可以在特定时间使用的多个对象。  当您在对象只需一次时，等待请使用 `CSingleLock`。  
  
 若要使用 **CMultiLock** 对象，请首先创建要等待同步对象的数组。  接下来，调用一个成员函数中 **CMultiLock** 对象的构造函数在受控资源的选件类。  然后调用 [锁定](../Topic/CMultiLock::Lock.md) 成员函数确定资源是否可用\(终止）。  如果一个是，请继续成员函数的其余部分。  如果资源不可用，请等待资源的经过指定时释放或返回失败。  资源的使用后完成的，或调用 [unlock](../Topic/CMultiLock::Unlock.md) 功能，如果要再次使用 **CMultiLock** 对象，以允许 **CMultiLock** 对象被销毁。  
  
 **CMultiLock** 对象是最有用的，则可以响应的线程具有大量 `CEvent` 对象时。  创建包含所有 `CEvent` 指针的数组，并调用 `Lock`。  这将导致线程等待，直到其中一个事件信号。  
  
 有关如何使用 **CMultiLock** 对象的更多信息，请参见文章 [多线程处理:如何使用同步类选件](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## 继承层次结构  
 `CMultiLock`  
  
## 要求  
 **Header:** afxmt.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)