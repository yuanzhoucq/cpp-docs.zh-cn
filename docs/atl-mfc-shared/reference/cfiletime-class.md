---
title: "CFileTime Class | Microsoft Docs"
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
  - "ATL::CFileTime"
  - "CFileTime"
  - "ATL.CFileTime"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFileTime class"
  - "shared classes, CFileTime"
ms.assetid: 1a358a65-1383-4124-b0d4-59b026e6860f
caps.latest.revision: 18
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFileTime Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

此选件类用于管理日期和时间值的方法与文件。  
  
## 语法  
  
```  
  
   class CFileTime :   
public FILETIME  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CFileTime::CFileTime](../Topic/CFileTime::CFileTime.md)|构造函数。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CFileTime::GetCurrentTime](../Topic/CFileTime::GetCurrentTime.md)|调用此静态函数检索表示当前系统日期和时间的 `CFileTime` 对象。|  
|[CFileTime::GetTime](../Topic/CFileTime::GetTime.md)|调用此方法从 `CFileTime` 对象检索时间。|  
|[CFileTime::LocalToUTC](../Topic/CFileTime::LocalToUTC.md)|调用此方法将本地时间转换文件根据协调世界时\(utc\)的文件时间\(UTC\)。|  
|[CFileTime::SetTime](../Topic/CFileTime::SetTime.md)|调用此方法设置 `CFileTime` 对象日期和时间存储的。|  
|[CFileTime::UTCToLocal](../Topic/CFileTime::UTCToLocal.md)|调用此方法将根据协调世界时\(utc\)的时间\(UTC\)转换为本地文件时。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[CFileTime::operator \-](../Topic/CFileTime::operator%20-.md)|此运算符用于执行在 `CFileTime` 或 `CFileTimeSpan` 对象的减法。|  
|[CFileTime::operator \!\=](../Topic/CFileTime::operator%20!=.md)|此运算符比较不相等的两 `CFileTime` 对象。|  
|[CFileTime::operator \+](../Topic/CFileTime::operator%20+.md)|此运算符用于执行在 `CFileTimeSpan` 对象的添加。|  
|[CFileTime::operator \+\=](../Topic/CFileTime::operator%20+=.md)|此运算符用于执行在 `CFileTimeSpan` 对象的添加并将结果赋给当前对象。|  
|[CFileTime::operator \<](../Topic/CFileTime::operator%20%3C.md)|此运算符比较两 `CFileTime` 对象确定更少。|  
|[CFileTime::operator \<\=](../Topic/CFileTime::operator%20%3C=.md)|此运算符比较两 `CFileTime` 对象确定相等或更小。|  
|[CFileTime::operator \=](../Topic/CFileTime::operator%20=.md)|赋值运算符。|  
|[CFileTime::operator \-\=](../Topic/CFileTime::operator%20-=.md)|此运算符用于执行在 `CFileTimeSpan` 对象的减法并将结果赋给当前对象。|  
|[CFileTime::operator \=\=](../Topic/CFileTime::operator%20==.md)|此运算符比较相等的两 `CFileTime` 对象。|  
|[CFileTime::operator \>](../Topic/CFileTime::operator%20%3E.md)|此运算符比较两 `CFileTime` 对象确定大。|  
|[CFileTime::operator \>\=](../Topic/CFileTime::operator%20%3E=.md)|此运算符比较两 `CFileTime` 对象确定相等或大。|  
  
### 公共常量  
  
|名称|描述|  
|--------|--------|  
|[CFileTime::Day](../Topic/CFileTime::Day.md)|存储的100纳秒间隔的数目由一天静态数据成员。|  
|[CFileTime::Hour](../Topic/CFileTime::Hour.md)|存储的100纳秒间隔数组成一小时静态数据成员。|  
|[CFileTime::Millisecond](../Topic/CFileTime::Millisecond.md)|存储的100纳秒间隔数组成一毫秒静态数据成员。|  
|[CFileTime::Minute](../Topic/CFileTime::Minute.md)|存储的100纳秒间隔数组成一分钟静态数据成员。|  
|[CFileTime::Second](../Topic/CFileTime::Second.md)|存储的100纳秒间隔数组成一个静态数据成员。|  
|[CFileTime::Week](../Topic/CFileTime::Week.md)|存储的100纳秒间隔数组成一周静态数据成员。|  
  
## 备注  
 此选件类用于管理日期和时间值的方法与文件的创建、访问和修改。  此选件类方法和数据与 `CFileTimeSpan` 对象共同频繁使用，处理相对时间值。  
  
 日期和时间值存储为表示100纳秒间隔数为64位值从1601年一月1日。  这是世界时\(utc\) \(UTC\)格式。  
  
 提供以下静态常量成员变量来简化计算:  
  
|成员变量|100纳秒间隔的数字|  
|----------|----------------|  
|毫秒|10,000|  
|第二个|毫秒\* 1,000|  
|分钟|接下来\* 60|  
|小时|\* 60分钟|  
|天|\* 24小时|  
|周|\* 7日|  
  
 **Note** 不是所有的文件系统可以记录创建和上次访问时间和并非所有的文件系统类似记录它们。  例如，在Windows NT肥胖文件系统，可以创建时间为10毫秒的解决方案，编写时间为2秒的解决方案，访问时有1天\(访问日期\)的解决方法。  在NTFS，访问时有1小时的解决方法。  此外，在磁盘上的肥胖记录时在磁盘上的本地时间，但是，NTFS记录时UTC。  有关更多信息，请参见 [文件时](http://msdn.microsoft.com/library/windows/desktop/ms724290)。  
  
## 继承层次结构  
 `FILETIME`  
  
 `CFileTime`  
  
## 要求  
 **Header:** atltime.h  
  
## 请参阅  
 [FILETIME](http://msdn.microsoft.com/library/windows/desktop/ms724284)   
 [CFileTimeSpan Class](../../atl-mfc-shared/reference/cfiletimespan-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)