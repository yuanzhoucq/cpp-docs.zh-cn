---
title: "CCriticalSection Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CCriticalSection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCriticalSection class"
  - "critical sections"
  - "同步类, CCriticalSection class"
  - "synchronization objects, critical section"
ms.assetid: f776f74b-5b0b-4f32-9c13-2b8e4a0d7b2b
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CCriticalSection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示“临界区” —每个允许一个线程同时访问资源或代码段的同步对象。  
  
## 语法  
  
```  
class CCriticalSection : public CSyncObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CCriticalSection::CCriticalSection](../Topic/CCriticalSection::CCriticalSection.md)|构造 `CCriticalSection` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CCriticalSection::Lock](../Topic/CCriticalSection::Lock.md)|用于 `CCriticalSection` 对象的访问权。|  
|[CCriticalSection::Unlock](../Topic/CCriticalSection::Unlock.md)|释放 `CCriticalSection` 对象。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CCriticalSection::operator CRITICAL\_SECTION\*](../Topic/CCriticalSection::operator%20CRITICAL_SECTION*.md)|检索指向内部 **CRITICAL\_SECTION** 对象。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CCriticalSection::m\_sect](../Topic/CCriticalSection::m_sect.md)|**CRITICAL\_SECTION** 对象。|  
  
## 备注  
 只有一个线程中一次允许修改数据或某些其他受控资源时，临界区很有用。  例如，添加节点到连接表是应由一个线程次只允许的过程。  通过使用控件的 `CCriticalSection` 对象的链接列表，因此，只有一个线程可能对列表一次访问。  
  
> [!NOTE]
>  实际Win32 **CRITICAL\_SECTION** 对象提供 `CCriticalSection` 选件类的功能。  
  
 临界区使用而不是mutex \(请参见 [CMutex](../../mfc/reference/cmutex-class.md)\)，而速度是重要的，而不会使用资源进程边界。  
  
 有两个方法用于 `CCriticalSection` 对象:独立应用程序和嵌入选件类。  
  
-   在需要时，使用独立 `CCriticalSection` 对象的独立方法，构造 `CCriticalSection` 对象。  在成功从构造函数后返回，显式锁定使用名为的对象。[锁定](../Topic/CCriticalSection::Lock.md)。  在执行访问临界区时，应调用 [unlock](../Topic/CCriticalSection::Unlock.md)。  此方法，即，而可以读取源代码的人员的更清晰，更容易出错在访问前后，必须记住锁定和取消锁定临界区。  
  
     一种更更好的方法是使用 [CSingleLock](../../mfc/reference/csinglelock-class.md) 选件类。  它还有一个 `Lock` 和 `Unlock` 方法，但是，您不需要考虑打开该资源，如果发生异常。  
  
-   嵌入方法可以使用多个线程间共享选件类通过添加 `CCriticalSection`类型的数据成员添加到选件类和锁定数据成员，并根据需要。  
  
 有关使用 `CCriticalSection` 对象的更多信息，请参见文章 [多线程处理:如何使用同步类选件](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CCriticalSection`  
  
## 要求  
 **Header:** afxmt.h  
  
## 请参阅  
 [CSyncObject Class](../../mfc/reference/csyncobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CMutex Class](../../mfc/reference/cmutex-class.md)