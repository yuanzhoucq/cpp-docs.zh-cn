---
title: "Date and Time: Automation Support | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "adding dates"
  - "自动化, date and time support"
  - "calculating dates and times"
  - "计算, 日期和时间"
  - "COleDateTime class, Automation date/time support"
  - "COleDateTimeSpan class, Automation date/time support"
  - "日期, Automation support"
  - "运行时间, calculating in Automation"
  - "格式设置 [Visual Studio], 日期"
  - "格式设置 [Visual Studio], 时间"
  - "时间 [Visual Studio], Automation support"
ms.assetid: 6eee94c4-943d-4ffc-bf7c-bdda89337ab0
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Date and Time: Automation Support
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文介绍如何利用选件类库服务迄今相关的和时间线。  中介绍的过程包括:  
  
-   [获取当前时间](../atl-mfc-shared/current-time-automation-classes.md)  
  
-   [计算经过的时间](../atl-mfc-shared/elapsed-time-automation-classes.md)  
  
-   [设置一个日期\/时间的字符串表示形式](../atl-mfc-shared/formatting-time-automation-classes.md)  
  
 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) 选件类提供了一种表示日期和时间信息。  它比 [CTime](../atl-mfc-shared/reference/ctime-class.md) 选件类提供更好的粒度和一个更大的范围。  [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) 选件类表示时间，例如两 `COleDateTime` 对象之间的差异。  
  
 `COleDateTime` 和 `COleDateTimeSpan` 选件类旨在使用自动化的 `COleVariant` 选件类。  `COleDateTime` 和 `COleDateTimeSpan` 也很有用在MFC编程的数据库，但是，可以使用它们，只要要操作日期和时间值。  虽然 `COleDateTime` 选件类比 `CTime` 选件类具有值和更好的粒度的一个更大的范围，所以它比 `CTime`需要更多存储每个对象。  当与基础 **DATE** 类型时，还有一些特殊注意事项。  有关更多详细信息参见 [日期类型](../atl-mfc-shared/date-type.md) 在 **DATE**的实现。  
  
 `COleDateTime` 对象可用来表示在31年一月1日，100和9999之间的日期，十二月。  `COleDateTime` 对象是浮点值，与1毫秒的近似解析。  `COleDateTime` 基于 **DATE** 数据类型，在 [COleDateTime::operator DATE](../Topic/COleDateTime::operator%20DATE.md)下的MFC文档。  **DATE** 的实际实现这些这样的限制。  `COleDateTime` 实现对这些区域便于与选件类一起使用。  
  
 `COleDateTime` 不支持朱利安日期。  公历假定实时扩展为" 100年一月1日。  
  
 `COleDateTime` 忽略夏时制\(DST）。  下面的代码示例比较计算跨DST将日期时间范围的两个方法:一个使用CRT和其他使用 `COleDateTime`。  DST开关，在大多数区域设置，第二周中4月和第三的在十月。  
  
 通过标准C类型结构 **tm** 和 `time_t`，第一个方法分别设置两 `CTime` 对象，*time1* 和 *time2*，对4月5日和4月6日。  代码演示 *time1* 和 *time2* 和timespan在它们之间。  
  
 第二个方法创建两 `COleDateTime` 对象、 `oletime1` 和 `oletime2`，然后将它们对日期和 *time1* 和 *time2相同*。  它显示 `oletime1` 和 `oletime2` 和timespan在它们之间。  
  
 CRT正确计算23小时差异。  `COleDateTimeSpan` 计算24小时差异。  
  
 请注意使用 `COleDateTime::Format`，工作区该示例快结束时使用正确显示该日期。  请参见知识库文章“BUG:格式\(“%D”\)表示 `COleDateTime` 和 `COleDateTimeSpan`失败” \(Q167338）。  
  
 [!code-cpp[NVC_ATLMFC_Utilities#176](../atl-mfc-shared/codesnippet/CPP/date-and-time-automation-support_1.cpp)]  
  
## 请参阅  
 [Date and Time](../atl-mfc-shared/date-and-time.md)