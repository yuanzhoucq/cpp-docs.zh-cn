---
title: "CFileTimeSpan Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CFileTimeSpan"
  - "ATL.CFileTimeSpan"
  - "ATL::CFileTimeSpan"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFileTimeSpan class"
  - "shared classes, CFileTimeSpan"
ms.assetid: 5856fb39-9c82-4027-8ccf-8760890491ec
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# CFileTimeSpan Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类用于管理相对日期和时间值的方法与文件。  
  
## 语法  
  
```  
  
class CFileTimeSpan  
  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CFileTimeSpan::CFileTimeSpan](../Topic/CFileTimeSpan::CFileTimeSpan.md)|构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CFileTimeSpan::GetTimeSpan](../Topic/CFileTimeSpan::GetTimeSpan.md)|调用此方法从 `CFileTimeSpan` 对象检索时间范围。|  
|[CFileTimeSpan::SetTimeSpan](../Topic/CFileTimeSpan::SetTimeSpan.md)|调用此方法设置 `CFileTimeSpan` 对象的时间范围。|  
  
### 公共运算符  
  
|名称|说明|  
|--------|--------|  
|[CFileTimeSpan::operator \-](../Topic/CFileTimeSpan::operator%20-.md)|执行在 `CFileTimeSpan` 对象的减法。|  
|[CFileTimeSpan::operator \!\=](../Topic/CFileTimeSpan::operator%20!=.md)|比较两个 `CFileTimeSpan` 对象是否相等。|  
|[CFileTimeSpan::operator \+](../Topic/CFileTimeSpan::operator%20+.md)|对 `CFileTimeSpan` 对象的添加。|  
|[CFileTimeSpan::operator \+\=](../Topic/CFileTimeSpan::operator%20+=.md)|对 `CFileTimeSpan` 对象的添加然后将结果赋给当前对象。|  
|[CFileTimeSpan::operator \<](../Topic/CFileTimeSpan::operator%20%3C.md)|比较两 `CFileTimeSpan` 对象确定更少。|  
|[CFileTimeSpan::operator \<\=](../Topic/CFileTimeSpan::operator%20%3C=.md)|比较两 `CFileTimeSpan` 对象确定相等或更小。|  
|[CFileTimeSpan::operator \=](../Topic/CFileTimeSpan::operator%20=.md)|赋值运算符。|  
|[CFileTimeSpan::operator \-\=](../Topic/CFileTimeSpan::operator%20-=.md)|执行在 `CFileTimeSpan` 对象的减法然后将结果赋给当前对象。|  
|[CFileTimeSpan::operator \=\=](../Topic/CFileTimeSpan::operator%20==.md)|比较两个 `CFileTimeSpan` 对象是否相等。|  
|[CFileTimeSpan::operator \>](../Topic/CFileTimeSpan::operator%20%3E.md)|比较两 `CFileTimeSpan` 对象确定大。|  
|[CFileTimeSpan::operator \>\=](../Topic/CFileTimeSpan::operator%20%3E=.md)|比较两 `CFileTimeSpan` 对象确定相等或大。|  
  
## 备注  
 此选件类用于管理经常遇到的相对时间的方法，在执行操作有关时，文件中创建的，最后一个捕获或最后更新。  此选件类方法与 [CFileTime选件类](../../atl-mfc-shared/reference/cfiletime-class.md) 对象共同常用。  
  
## 示例  
 为 [CFileTime::Millisecond](../Topic/CFileTime::Millisecond.md)参见示例。  
  
## 要求  
 **Header:** atltime.h  
  
## 请参阅  
 [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)   
 [CFileTime Class](../../atl-mfc-shared/reference/cfiletime-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)