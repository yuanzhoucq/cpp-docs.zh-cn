---
title: "CSyncObject Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSyncObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSyncObject class"
  - "同步类, CSyncObject"
ms.assetid: c62ea6eb-a17b-4e01-aed4-321fc435a5f4
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CSyncObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供通用功能在Win32的同步对象的纯虚选件类。  
  
## 语法  
  
```  
class CSyncObject : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CSyncObject::CSyncObject](../Topic/CSyncObject::CSyncObject.md)|构造 `CSyncObject` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CSyncObject::Lock](../Topic/CSyncObject::Lock.md)|同步对象的访问权。|  
|[CSyncObject::Unlock](../Topic/CSyncObject::Unlock.md)|同步对象的访问权。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CSyncObject::operator HANDLE](../Topic/CSyncObject::operator%20HANDLE.md)|提供对同步对象。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[CSyncObject::m\_hObject](../Topic/CSyncObject::m_hObject.md)|对于基础同步对象的句柄。|  
  
## 备注  
 Microsoft基础选件类库提供从 `CSyncObject`派生的几选件类。  这些是 [CEvent](../../mfc/reference/cevent-class.md)、 [CMutex](../../mfc/reference/cmutex-class.md)、 [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)和 [CSemaphore](../../mfc/reference/csemaphore-class.md)。  
  
 有关如何使用同步对象的信息，请参见文章 [多线程处理:如何使用同步类选件](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CSyncObject`  
  
## 要求  
 **Header:** afxmt.h  
  
## 请参阅  
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)