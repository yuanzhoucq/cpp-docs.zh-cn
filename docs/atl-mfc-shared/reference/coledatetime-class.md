---
title: "COleDateTime Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleDateTime"
  - "ATL.COleDateTime"
  - "ATL::COleDateTime"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleDateTime class"
  - "日期数据类型, MFC encapsulation of"
  - "日期, handling in MFC"
  - "shared classes, COleDateTime"
  - "时间, handling in MFC"
  - "time-only values"
ms.assetid: e718f294-16ec-4649-88b6-a4dbae5178fb
caps.latest.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 35
---
# COleDateTime Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封装用于 OLE 自动化的 `DATE` 数据类型。  
  
## 语法  
  
```  
class COleDateTime  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|描述|  
|--------|--------|  
|[COleDateTime::COleDateTime](../Topic/COleDateTime::COleDateTime.md)|构造 `COleDateTime` 对象。|  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[COleDateTime::Format](../Topic/COleDateTime::Format.md)|生成 `COleDateTime` 对象的已格式化的字符串表示形式。|  
|[COleDateTime::GetAsDBTIMESTAMP](../Topic/COleDateTime::GetAsDBTIMESTAMP.md)|调用此方法获取在 `COleDateTime` 对象的时间作为 **DBTIMESTAMP** 数据结构。|  
|[COleDateTime::GetAsSystemTime](../Topic/COleDateTime::GetAsSystemTime.md)|调用此方法获取在 `COleDateTime` 对象的时间作为 [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) 数据结构。|  
|[COleDateTime::GetAsUDATE](../Topic/COleDateTime::GetAsUDATE.md)|调用此方法获取在 `COleDateTime` 的时间作为 **UDATE** 数据结构。|  
|[COleDateTime::GetCurrentTime](../Topic/COleDateTime::GetCurrentTime.md)|创建表示当前时间的一 `COleDateTime` 对象 \(静态成员函数\)。|  
|[COleDateTime::GetDay](../Topic/COleDateTime::GetDay.md)|返回此 `COleDateTime` 对象表示的日 \(1 – 31\)。|  
|[COleDateTime::GetDayOfWeek](../Topic/COleDateTime::GetDayOfWeek.md)|返回此 `COleDateTime` 对象表示的周 \(sunday \= 1\)。|  
|[COleDateTime::GetDayOfYear](../Topic/COleDateTime::GetDayOfYear.md)|返回此 `COleDateTime` 对象表示中的日 \(一月 1 日\= 1\)。|  
|[COleDateTime::GetHour](../Topic/COleDateTime::GetHour.md)|返回此 `COleDateTime` 对象表示的小时 \(0 – 23\)。|  
|[COleDateTime::GetMinute](../Topic/COleDateTime::GetMinute.md)|返回此 `COleDateTime` 对象表示的分钟 \(0 – 59\)。|  
|[COleDateTime::GetMonth](../Topic/COleDateTime::GetMonth.md)|返回此 `COleDateTime` 对象表示的月份 \(1 – 12\)。|  
|[COleDateTime::GetSecond](../Topic/COleDateTime::GetSecond.md)|返回第二此 `COleDateTime` 对象表示 \(0 – 59\)。|  
|[COleDateTime::GetStatus](../Topic/COleDateTime::GetStatus.md)|获取 `COleDateTime` 对象的状态 \(有效性\) 。|  
|[COleDateTime::GetYear](../Topic/COleDateTime::GetYear.md)|返回此 `COleDateTime` 对象表示的年份。|  
|[COleDateTime::ParseDateTime](../Topic/COleDateTime::ParseDateTime.md)|从字符串中读取一个日期\/时间值并将 `COleDateTime`的值。|  
|[COleDateTime::SetDate](../Topic/COleDateTime::SetDate.md)|将此 `COleDateTime` 对象的值设置为指定的日期值的。|  
|[COleDateTime::SetDateTime](../Topic/COleDateTime::SetDateTime.md)|将此 `COleDateTime` 对象的值设置为指定的日期\/时间值的。|  
|[COleDateTime::SetStatus](../Topic/COleDateTime::SetStatus.md)|设置此 `COleDateTime` 对象的状态 \(有效性\)。|  
|[COleDateTime::SetTime](../Topic/COleDateTime::SetTime.md)|将此 `COleDateTime` 对象的值设置为指定的时间的值。|  
  
### 公共运算符  
  
|名称|描述|  
|--------|--------|  
|[COleDateTime::operator \=\=、COleDateTime::operator \<等.](../Topic/COleDateTime%20Relational%20Operators.md)|比较两个 `COleDateTime` 值。|  
|[COleDateTime::operator \+，COleDateTime::operator \-](../Topic/COleDateTime::operator%20+,%20-.md)|增加和减少 `COleDateTime` 值。|  
|[COleDateTime::operator \+\=，COleDateTime::operator \- \=](../Topic/COleDateTime::operator%20+=,%20-=.md)|从此 `COleDateTime` 对象增加和减少 `COleDateTime` 值。|  
|[COleDateTime::operator \=](../Topic/COleDateTime::operator%20=.md)|将一个 `COleDateTime` 值。|  
|[COleDateTime::operator 日期，COleDateTime::operator Date\*](../Topic/COleDateTime::operator%20DATE.md)|转换 `COleDateTime` 值转换为 `DATE` 或 `DATE*`。|  
  
### 公共数据成员  
  
|名称|描述|  
|--------|--------|  
|[COleDateTime::m\_dt](../Topic/COleDateTime::m_dt.md)|包含此 `COleDateTime` 对象的基础 **DATE**。|  
|[COleDateTime::m\_status](../Topic/COleDateTime::m_status.md)|包含此 `COleDateTime` 对象的状态。|  
  
## 备注  
 `COleDateTime` 没有基类。  
  
 它是一个 OLE 自动化的 [VARIANT](http://msdn.microsoft.com/zh-cn/e305240e-9e11-4006-98cc-26f4932d2118) 数据类型的类型。  `COleDateTime` 值表示绝对日期和时间值。  
  
 `DATE` 类型实现为浮点值。  天数从 1899 年十二月 30 日\) 测量，在午夜。  下表显示了的日期及其关联的值：  
  
|日期|值|  
|--------|-------|  
|1899 年十二月 29 日午夜，|\-1.0|  
|1899 年十二月 29 日，6 AM|\-1.25|  
|1899 年十二月 30 日午夜，|0.0|  
|1899 年十二月 31 日午夜，|1.0|  
|1900 年一月 1 日，6 AM..|2.25|  
  
> [!CAUTION]
>  说明在该控件上的表中，虽然日值变为负数在 1899 年十二月 30 日的午夜之前，时间值不。  例如，凌晨 6:00 由一部分 0.25 的值始终表示无论表示日的该整数是否为正 \(在 1899 年十二月 30 日之后\) 或负值 \(在 1899 年十二月 30 日之前\)。  这意味着一个简单的浮点比较比个代表的凌晨 7:00 将不正确排序表示在 12\/29\/1899 的 `COleDateTime` 凌晨 6:00，因为 **later** 当天。  
  
 `COleDateTime` 选件类处理通过十二月 31 日日期 100 年一月 1 日，9999。  `COleDateTime` 选件类使用公历，它不支持朱利安日期。  `COleDateTime` 忽略夏时制。  \(请参见 [日期和时间：自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。\)  
  
> [!NOTE]
>  可以使用 `%y` 格式检索一个仅中开始在 1900 年的日期。  如果在 1900 年前用于日期的 `%y` 格式，代码生成一个断言失败。  
  
 此类型还用于表示日期或时间值。  按照约定，日期 0 \(1899 年十二月 30 日\)。时间值和时间 00:00 \(午夜\) 为日期值。  
  
 如果您创建一 `COleDateTime` 对象使用日期小于 100，日期接受，但是，对的后续调用 `GetYear`、`GetMonth`、`GetDay`、`GetHour`、`GetMinute`和 `GetSecond` 失败并返回\-1。  过去，您可以使用两位数日期，但是，日期必须为 100 或用在 MFC 4.2 和更高版本。  
  
 为了避免问题，请指定一个四位日期。  例如：  
  
 [!code-cpp[NVC_ATLMFC_Utilities#1](../../atl-mfc-shared/codesnippet/CPP/coledatetime-class_1.cpp)]  
  
 `COleDateTime` 值的基本算术运算使用该选件类 [COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)。  `COleDateTimeSpan` 值定义时间间隔。  这些选件类之间的关系类似于 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 和 [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)之间。  
  
 有关 `COleDateTime` 和 `COleDateTimeSpan` 选件类的更多信息，请参见中的文章 [日期和时间：自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。  
  
## 要求  
 **标头：** ATLComTime.h  
  
## 请参阅  
 [COleVariant Class](../../mfc/reference/colevariant-class.md)   
 [CTime Class](../../atl-mfc-shared/reference/ctime-class.md)   
 [CTimeSpan Class](../../atl-mfc-shared/reference/ctimespan-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)