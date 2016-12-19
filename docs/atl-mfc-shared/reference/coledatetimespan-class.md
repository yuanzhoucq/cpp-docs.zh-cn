---
title: "COleDateTimeSpan Class | Microsoft Docs"
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
  - "ATL.COleDateTimeSpan"
  - "COleDateTimeSpan"
  - "ATL::COleDateTimeSpan"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleDateTimeSpan class"
  - "日期数据类型, MFC encapsulation of"
  - "shared classes, COleDateTimeSpan"
  - "time span"
  - "timespan"
ms.assetid: 7441526d-a30a-4019-8fb3-3fee6f897cbe
caps.latest.revision: 19
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleDateTimeSpan Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

表示相对时间，时间范围。  
  
## 语法  
  
```  
class COleDateTimeSpan  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleDateTimeSpan::COleDateTimeSpan](../Topic/COleDateTimeSpan::COleDateTimeSpan.md)|构造 `COleDateTimeSpan` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleDateTimeSpan::Format](../Topic/COleDateTimeSpan::Format.md)|生成 `COleDateTimeSpan` 对象的已格式化的字符串表示形式。|  
|[COleDateTimeSpan::GetDays](../Topic/COleDateTimeSpan::GetDays.md)|返回此 `COleDateTimeSpan` 对象表示范围的日部分。|  
|[COleDateTimeSpan::GetHours](../Topic/COleDateTimeSpan::GetHours.md)|返回此 `COleDateTimeSpan` 对象表示范围的小时数部分。|  
|[COleDateTimeSpan::GetMinutes](../Topic/COleDateTimeSpan::GetMinutes.md)|返回此 `COleDateTimeSpan` 对象表示范围的详细的一部分。|  
|[COleDateTimeSpan::GetSeconds](../Topic/COleDateTimeSpan::GetSeconds.md)|返回此 `COleDateTimeSpan` 对象表示范围的第二部分。|  
|[COleDateTimeSpan::GetStatus](../Topic/COleDateTimeSpan::GetStatus.md)|获取此 `COleDateTimeSpan` 对象的状态（有效性）。|  
|[COleDateTimeSpan::GetTotalDays](../Topic/COleDateTimeSpan::GetTotalDays.md)|返回此 `COleDateTimeSpan` 对象表示的天数。|  
|[COleDateTimeSpan::GetTotalHours](../Topic/COleDateTimeSpan::GetTotalHours.md)|返回此 `COleDateTimeSpan` 对象表示小时数。|  
|[COleDateTimeSpan::GetTotalMinutes](../Topic/COleDateTimeSpan::GetTotalMinutes.md)|返回此 `COleDateTimeSpan` 对象表示分钟数。|  
|[COleDateTimeSpan::GetTotalSeconds](../Topic/COleDateTimeSpan::GetTotalSeconds.md)|返回此 `COleDateTimeSpan` 对象表示秒数。|  
|[COleDateTimeSpan::SetDateTimeSpan](../Topic/COleDateTimeSpan::SetDateTimeSpan.md)|将此 `COleDateTimeSpan` 对象的值。|  
|[COleDateTimeSpan::SetStatus](../Topic/COleDateTimeSpan::SetStatus.md)|设置此 `COleDateTimeSpan` 对象的状态（有效性）。|  
  
### 公共运算符  
  
|||  
|-|-|  
|[运算符\+ \)，](../Topic/COleDateTimeSpan::operator%20+,%20-.md)|添加，减去，并更改 `COleDateTimeSpan` 值的符号。|  
|[\+\=运算符，\- \=](../Topic/COleDateTimeSpan::operator%20+=,%20-=.md)|从此 `COleDateTimeSpan` 值增加和减少 `COleDateTimeSpan` 值。|  
|[运算符\=](../Topic/COleDateTimeSpan::operator%20=.md)|将一个 `COleDateTimeSpan` 值。|  
|[运算符\=\=，\<，\<\=](../Topic/COleDateTimeSpan%20Relational%20Operators.md)|比较两个 `COleDateTimeSpan` 值。|  
|[二进制运算符](../Topic/COleDateTimeSpan::operator%20double.md)|将此 `COleDateTimeSpan` 值转换为 **double**。|  
  
### 公共数据成员  
  
|名称|说明|  
|--------|--------|  
|[COleDateTimeSpan::m\_span](../Topic/COleDateTimeSpan::m_span.md)|包含此 `COleDateTimeSpan` 对象的基础 **double**。|  
|[COleDateTimeSpan::m\_status](../Topic/COleDateTimeSpan::m_status.md)|包含此 `COleDateTimeSpan` 对象的状态。|  
  
## 备注  
 `COleDateTimeSpan` 没有基类。  
  
 `COleDateTimeSpan` 天数保留时间。  
  
 `COleDateTimeSpan` 使用其伴随选件类 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)。  `COleDateTime` 封装OLE自动化的 **DATE** 数据类型。  `COleDateTime` 表示绝对时间值。  所有 `COleDateTime` 计算涉及 `COleDateTimeSpan` 值。  在这些选件类之间的关系类似于于 [CTime](../../atl-mfc-shared/reference/ctime-class.md) 和 [CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)之间。  
  
 有关 `COleDateTime` 和 `COleDateTimeSpan` 选件类的更多信息，请参见文章 [日期和时间:自动化支持](../../atl-mfc-shared/date-and-time-automation-support.md)。  
  
## 要求  
 **Header:** ATLComTime.h  
  
## 请参阅  
 [COleDateTime Class](../../atl-mfc-shared/reference/coledatetime-class.md)   
 [CTime Class](../../atl-mfc-shared/reference/ctime-class.md)   
 [CTimeSpan Class](../../atl-mfc-shared/reference/ctimespan-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [ATL\/MFC Shared Classes](../../atl-mfc-shared/atl-mfc-shared-classes.md)