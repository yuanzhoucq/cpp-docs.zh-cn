---
title: "CSemaphore Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSemaphore"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSemaphore class"
  - "信号灯"
  - "synchronization objects, 信号灯"
ms.assetid: 385fc7e4-8f86-4be2-85e1-d23b38c12f7f
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CSemaphore Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

选件类 `CSemaphore` 对象表示“信号量” —允许线程中的有限一个或多个同步对象处理访问的维护线程数计数当前访问具有指定的资源。  
  
## 语法  
  
```  
class CSemaphore : public CSyncObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CSemaphore::CSemaphore](../Topic/CSemaphore::CSemaphore.md)|构造 `CSemaphore` 对象。|  
  
## 备注  
 信号量可用于对只能支持用户的有限数量的共享资源的访问控件。  `CSemaphore` 对象的当前计数是其他用户的数目允许的。  在计数达到零时，任何尝试使用 **CSemaphore** 对象控件的资源要插入到系统队列中，直到其等待或者计算或计数0以上引发。  一次只能访问这种受控资源用户的最大数在 `CSemaphore` 构造对象时指定。  
  
 在需要时，要使用 **CSemaphore** 对象，请构造 `CSemaphore` 对象。  指定要等待信号量的名称，并且，如果您的应用程序最初应拥有它。  当构造函数返回时，您可以访问信号量。  在执行这种访问受控资源时，应调用 [CSyncObject::Unlock](../Topic/CSyncObject::Unlock.md)。  
  
 另一种方法用于 `CSemaphore` 对象将添加 `CSemaphore` 类型的变量，您希望控件的选件类的数据成员。  在控制构造对象时，只需调用指定初始访问计数、最大访问信号量的计数、名称\(如果它将用作进程边界\)和所需的安全特性的 `CSemaphore` 数据成员的构造函数。  
  
 为 `CSemaphore` 对象来控制资源的访问，请首先创建类型 [CSingleLock](../../mfc/reference/csinglelock-class.md) 的变量或键入在资源的访问成员函数的 [CMultiLock](../../mfc/reference/cmultilock-class.md)。  然后调用锁定对象的 `Lock` 成员函数\(例如，[CSingleLock::Lock](../Topic/CSingleLock::Lock.md)）。  此时，您的线程对该资源将能够访问，等待资源释放并且能够访问或等待资源释放和超时，不能对该资源的访问权。  在任一情况下，您的资源访问了采用线程安全的方式。  若要释放资源，请使用锁定对象的 `Unlock` 成员函数\(例如，[CSingleLock::Unlock](../Topic/CSingleLock::Unlock.md)\)，或者允许访问流程的锁定对象超出范围。  
  
 此外，还可以显式创建 **CSemaphore** 对象独立应用程序和访问它在尝试访问这种受控资源。  此方法，即，而可以读取源代码的人员的更清晰，更容易出错。  
  
 有关如何使用 **CSemaphore** 对象的更多信息，请参见文章 [多线程处理:如何使用同步类选件](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CSemaphore`  
  
## 要求  
 **Header:** afxmt.h  
  
## 请参阅  
 [CSyncObject Class](../../mfc/reference/csyncobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)