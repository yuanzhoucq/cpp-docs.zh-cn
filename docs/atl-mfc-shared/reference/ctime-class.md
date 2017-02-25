---
title: "CTime Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CTime"
  - "CTime"
  - "ATL::CTime"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTime class"
  - "shared classes, CTime"
ms.assetid: 0a299544-485b-48dc-9d3c-fdc30f57d612
caps.latest.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 31
---
# CTime Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示绝对时间和日期。  
  
## 语法  
  
```  
class CTime  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[CTime::CTime](../Topic/CTime::CTime.md)|构造 `CTime` 对象以多种方式。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CTime::Format](../Topic/CTime::Format.md)|转换 `CTime` 对象转换为基于本地时区—的已格式化的字符串。|  
|[CTime::FormatGmt](../Topic/CTime::FormatGmt.md)|转换 `CTime` 对象转换为基于UTC —的已格式化的字符串。|  
|[CTime::GetAsDBTIMESTAMP](../Topic/CTime::GetAsDBTIMESTAMP.md)|将对Win32兼容 <xref:System.Data.OleDb.OleDbType> 结构的 `CTime` 对象存储的时间信息。|  
|[CTime::GetAsSystemTime](../Topic/CTime::GetAsSystemTime.md)|将对Win32兼容 [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) 结构的 `CTime` 对象存储的时间信息。|  
|[CTime::GetCurrentTime](../Topic/CTime::GetCurrentTime.md)|创建表示当前时间的一 `CTime` 对象\(静态成员函数\)。|  
|[CTime::GetDay](../Topic/CTime::GetDay.md)|返回日 `CTime` 由对象表示。|  
|[CTime::GetDayOfWeek](../Topic/CTime::GetDayOfWeek.md)|返回 `CTime` 对象表示的周日期。|  
|[CTime::GetGmtTm](../Topic/CTime::GetGmtTm.md)|是根据UTC —的组件分解 `CTime` 对象。|  
|[CTime::GetHour](../Topic/CTime::GetHour.md)|返回 `CTime` 对象表示的小时数。|  
|[CTime::GetLocalTm](../Topic/CTime::GetLocalTm.md)|是根据本地时区—的组件分解 `CTime` 对象。|  
|[CTime::GetMinute](../Topic/CTime::GetMinute.md)|返回 `CTime` 对象表示的分钟。|  
|[CTime::GetMonth](../Topic/CTime::GetMonth.md)|返回 `CTime` 对象表示的月份。|  
|[CTime::GetSecond](../Topic/CTime::GetSecond.md)|返回 `CTime` 对象表示的第二个。|  
|[CTime::GetTime](../Topic/CTime::GetTime.md)|返回给定 `CTime` 对象的一个 **\_\_time64\_t** 值。|  
|[CTime::GetYear](../Topic/CTime::GetYear.md)|返回 `CTime` 对象表示的年份。|  
|[CTime::Serialize64](../Topic/CTime::Serialize64.md)|序列化数据。\/从存档。|  
  
### 运算符  
  
|||  
|-|-|  
|[运算符\+ –](../Topic/CTime::operator%20+,%20-.md)|这些运算符增加和减少 `CTimeSpan` 和 `CTime` 对象。|  
|[\+\=运算符，– \=](../Topic/CTime::operator%20+=,%20-=.md)|这些运算符来回此 `CTime` 对象增加和减少 `CTimeSpan` 对象。|  
|[运算符\=](../Topic/CTime::operator%20=.md)|赋值运算符。|  
|[运算符\=\=，\<等.](../Topic/CTime%20Comparison%20Operators.md)|比较运算符。|  
  
## 备注  
 `CTime` 没有基类。  
  
 `CTime` 值根据协调世界时\(utc\) \(UTC\)，与协调世界时\(utc\) \(格林尼治标准时间，GMT\)是等效的。  请参见 [时间管理](../../c-runtime-library/time-management.md) 有关如何时区的信息确定。  
  
 在创建 `CTime` 对象时，与具有零请将 `nDST` 参数为0指示标准时间实际上是，或者给的值大于0表示夏时制实际上是，或将值是否比C运行库代码评估条件时或夏时制是否有效。  `tm_isdst` 是必需字段。  如果未设置，其值是未定义的，并从 [mktime](../../c-runtime-library/reference/mktime-mktime32-mktime64.md) 的返回值是不可预知的。  如果 `timeptr` 指向上返回的tm结构调用 [asctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)，[\_gmtime\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)，或者 [localtime\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)，`tm_isdst` 字段包含正确的值。  
  
 该选件类，[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)，表示时间间隔。  
  
 `CTime` 和 `CTimeSpan` 选件类没有为派生模型。  由于没有虚函数，`CTime` 和 `CTimeSpan` 对象的大小正确为8字节。  大多数成员函数内联。  
  
> [!NOTE]
>  上面的日期来限制是12\/31\/3000。  该下限是1\/1\/1970 12:00: 00 AM GMT。  
  
 有关使用 `CTime`的更多信息，请参见位于 [日期和时间](../../atl-mfc-shared/date-and-time.md)，并且，[时间线](../../c-runtime-library/time-management.md) "运行库参考。  
  
> [!NOTE]
>  从MFC更改的 `CTime` framework 7.1到MFC 8.0。  如果序列化一 `CTime` framework使用 `operator <<` 在MFC 8.0或更高版本下，生成的文件不可读、在MFC的更早版本。  
  
## 要求  
 **标头:** atltime.h  
  
## 请参阅  
 [asctime\_s、\_wasctime\_s](../../c-runtime-library/reference/asctime-s-wasctime-s.md)   
 [\_ftime\_s、\_ftime32\_s、\_ftime64\_s](../../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)   
 [gmtime\_s、\_gmtime32\_s、\_gmtime64\_s](../../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)   
 [localtime\_s, \_localtime32\_s, \_localtime64\_s](../../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)   
 [strftime、wcsftime、\_strftime\_l、\_wcsftime\_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [time、\_time32、\_time64](../../c-runtime-library/reference/time-time32-time64.md)   
 [CTimeSpan Class](../../atl-mfc-shared/reference/ctimespan-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)