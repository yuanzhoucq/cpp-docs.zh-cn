---
title: "CTimeSpan Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CTimeSpan"
  - "CTimeSpan"
  - "timespan"
  - "ATL::CTimeSpan"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTimeSpan class"
  - "运行时间, CTimeSpan object"
  - "shared classes, CTimeSpan"
  - "time span"
  - "时间, elapsed"
  - "timespan"
ms.assetid: ee1e42f6-1839-477a-8435-fb26ad475140
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CTimeSpan Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

时间，在内部存储为秒数。时间范围。  
  
## 语法  
  
```  
class CTimeSpan  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CTimeSpan::CTimeSpan](../Topic/CTimeSpan::CTimeSpan.md)|构造 `CTimeSpan` 对象以多种方式。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CTimeSpan::Format](../Topic/CTimeSpan::Format.md)|转换 `CTimeSpan` 转换为格式化的字符串。|  
|[CTimeSpan::GetDays](../Topic/CTimeSpan::GetDays.md)|返回表示完整日期数本 `CTimeSpan`的值。|  
|[CTimeSpan::GetHours](../Topic/CTimeSpan::GetHours.md)|返回在当前日期表示小时数的值\(– 23到23）。|  
|[CTimeSpan::GetMinutes](../Topic/CTimeSpan::GetMinutes.md)|返回在当前小时内表示分钟数的值\(– 59到59）。|  
|[CTimeSpan::GetSeconds](../Topic/CTimeSpan::GetSeconds.md)|返回在当前分钟内表示秒数的值\(– 59到59）。|  
|[CTimeSpan::GetTimeSpan](../Topic/CTimeSpan::GetTimeSpan.md)|返回 `CTimeSpan` 对象的值。|  
|[CTimeSpan::GetTotalHours](../Topic/CTimeSpan::GetTotalHours.md)|返回表示完整的小时总数本 `CTimeSpan`的值。|  
|[CTimeSpan::GetTotalMinutes](../Topic/CTimeSpan::GetTotalMinutes.md)|返回表示完整分钟的总数本 `CTimeSpan`的值。|  
|[CTimeSpan::GetTotalSeconds](../Topic/CTimeSpan::GetTotalSeconds.md)|返回表示完整的秒数本 `CTimeSpan`的值。|  
|[CTimeSpan::Serialize64](../Topic/CTimeSpan::Serialize64.md)|序列化数据。\/从存档。|  
  
### 运算符  
  
|||  
|-|-|  
|[运算符\+ –](../Topic/CTimeSpan::operator%20+,%20-.md)|增加和减少 `CTimeSpan` 对象。|  
|[\+\=运算符– \=](../Topic/CTimeSpan::operator%20+=,%20-=.md)|来回此 `CTimeSpan`增加和减少 `CTimeSpan` 对象。|  
|[运算符\=\= \<等.](../Topic/CTimeSpan%20Comparison%20Operators.md)|比较两个相对时间值。|  
  
## 备注  
 `CTimeSpan` 没有基类。  
  
 `CTimeSpan` 函数秒为天、小时、分钟和秒的各种组合。  
  
 `CTimeSpan` 对象在 **\_\_time64\_t** framework内存，为8字节。  
  
 该选件类，[CTime](../../atl-mfc-shared/reference/ctime-class.md)，表示绝对时间。  
  
 `CTime` 和 `CTimeSpan` 选件类没有为派生模型。  由于没有虚函数，两 `CTime` 和 `CTimeSpan` 对象的大小正确为8字节。  大多数成员函数内联。  
  
 有关使用 `CTimeSpan`的更多信息，请参见位于 [日期和时间](../../atl-mfc-shared/date-and-time.md)，并且，[时间线](../../c-runtime-library/time-management.md) " *运行库参考*。  
  
## 要求  
 **Header:** atltime.h  
  
## 请参阅  
 [asctime、\_wasctime](../../c-runtime-library/reference/asctime-wasctime.md)   
 [\_ftime, \_ftime32, \_ftime64](../../c-runtime-library/reference/ftime-ftime32-ftime64.md)   
 [gmtime、\_gmtime32、\_gmtime64](../../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)   
 [localtime、\_localtime32、\_localtime64](../../c-runtime-library/reference/localtime-localtime32-localtime64.md)   
 [strftime、wcsftime、\_strftime\_l、\_wcsftime\_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)