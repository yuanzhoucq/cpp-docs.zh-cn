---
title: "CMutex Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "Mutex"
  - "CMutex"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMutex class"
  - "mutex"
  - "同步类, CMutex class"
  - "synchronization objects, mutex"
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CMutex Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示“mutex” —允许一个线程对资源的互斥的访问的同步对象。  
  
## 语法  
  
```  
class CMutex : public CSyncObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CMutex::CMutex](../Topic/CMutex::CMutex.md)|构造 `CMutex` 对象。|  
  
## 备注  
 只有一个线程中一次允许修改数据或某些其他受控资源时，Mutex分有用。  例如，添加节点到连接表是应由一个线程次只允许的过程。  通过使用控件的 `CMutex` 对象的链接列表，因此，只有一个线程可能对列表一次访问。  
  
 在需要时，要使用 `CMutex` 对象，请构造 `CMutex` 对象。  指定要等待mutex的名称，并且，如果您的应用程序最初应拥有它。  当构造函数返回时，您可以访问mutex。  在执行这种访问受控资源时，应调用 [CSyncObject::Unlock](../Topic/CSyncObject::Unlock.md)。  
  
 另一种方法用于 `CMutex` 对象将添加 `CMutex` 类型的变量，您希望控件的选件类的数据成员。  在控制对象的构造后，调用 `CMutex` 数据成员指定mutex最初是否拥有，名称的mutex \(如果将使用该进程边界\)和所需的安全特性的构造函数。  
  
 为 `CMutex` 对象来控制资源的访问，请首先创建类型 [CSingleLock](../../mfc/reference/csinglelock-class.md) 的变量或键入在资源的访问成员函数的 [CMultiLock](../../mfc/reference/cmultilock-class.md)。  然后调用锁定对象的 `Lock` 成员函数\(例如，[CSingleLock::Lock](../Topic/CSingleLock::Lock.md)）。  此时，您的线程对该资源将能够访问，等待资源释放并且能够访问或等待资源释放和超时，不能对该资源的访问权。  在任一情况下，您的资源访问了采用线程安全的方式。  若要释放资源，请使用锁定对象的 `Unlock` 成员函数\(例如，[CSingleLock::Unlock](../Topic/CSingleLock::Unlock.md)\)，或者允许访问流程的锁定对象超出范围。  
  
 有关使用 `CMutex` 对象的更多信息，请参见文章 [多线程处理:如何使用同步类选件](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CMutex`  
  
## 要求  
 **Header:** afxmt.h  
  
## 请参阅  
 [CSyncObject Class](../../mfc/reference/csyncobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)