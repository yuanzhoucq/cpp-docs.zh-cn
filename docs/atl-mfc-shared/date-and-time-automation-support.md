---
title: "日期和时间： 自动化支持 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- adding dates
- calculating dates and times
- formatting [Visual Studio], dates
- dates, Automation support
- elapsed time, calculating in Automation
- COleDateTime class, Automation date/time support
- COleDateTimeSpan class, Automation date/time support
- Automation, date and time support
- formatting [Visual Studio], time
- calculations, date and time
- time [Visual Studio], Automation support
ms.assetid: 6eee94c4-943d-4ffc-bf7c-bdda89337ab0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6a40a8fe49d9564714c328b657bc0d85d52ad84b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="date-and-time-automation-support"></a>日期和时间： 自动化支持
本文介绍如何利用与日期和时间的管理相关的类库服务。 所述过程包括：  
  
-   [获取当前时间](../atl-mfc-shared/current-time-automation-classes.md)  
  
-   [计算经过的时间](../atl-mfc-shared/elapsed-time-automation-classes.md)  
  
-   [格式设置的字符串表示形式为日期/时间](../atl-mfc-shared/formatting-time-automation-classes.md)  
  
 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)类提供一种方法来表示日期和时间信息。 它提供了更细的粒度和更大的范围比[CTime](../atl-mfc-shared/reference/ctime-class.md)类。 [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)类表示经过的时间，如两个区别`COleDateTime`对象。  
  
 `COleDateTime`和`COleDateTimeSpan`类旨在用于`COleVariant`在自动化中使用的类。 `COleDateTime`和`COleDateTimeSpan`还可在 MFC 数据库编程中，但无论何时你想要操作日期和时间值，可以使用它们。 尽管`COleDateTime`类具有更大范围的值和更细的粒度比`CTime`类，它需要更多的存储，每个对象比`CTime`。 也有一些特殊的注意事项使用基础时**日期**类型。 请参阅[日期类型](../atl-mfc-shared/date-type.md)有关详细信息的实现**日期**。  
  
 `COleDateTime`对象可以用于表示 100，年 1 月 1 日和年 12 月 31 日之间的日期 9999。 `COleDateTime`对象浮点值，使用的近似分辨率为 1 毫秒。 `COleDateTime`基于**日期**下的 MFC 文档中定义的数据类型[COleDateTime::operator 日期](../atl-mfc-shared/reference/coledatetime-class.md#operator_date)。 实际实现**日期**超出这些边界。 `COleDateTime`实现未施加这些边界以方便使用类。  
  
 `COleDateTime`不支持儒略历日期。 公历假定将扩展后移到 100 年 1 月 1 日。  
  
 `COleDateTime`将忽略夏令时 (DST)。 下面的代码示例将两种方法可以计算跨越 DST 切换日期的时间范围进行比较： 使用 CRT，和其他使用`COleDateTime`。 DST 切换，在大多数区域设置中的第二个一周内年 4 月和年 10 月的第三。  
  
 第一种方法中设置两个`CTime`对象， *time1*和*time2*，再到 5 年 4 月和年 4 月 6 分别使用标准的 C 类型结构**tm**和`time_t`. 该代码将显示*time1*和*time2*和它们之间的时间跨度。  
  
 第二种方法创建两个`COleDateTime`对象，`oletime1`和`oletime2`，并将它们设置为同一个日期作为*time1*和*time2*。 它显示`oletime1`和`oletime2`和它们之间的时间跨度。  
  
 CRT 正确地计算 23 个小时的差异。 `COleDateTimeSpan`计算 24 小时的差异。  
  
 请注意，一种解决方法用于快结束时的示例显示使用正常的日期`COleDateTime::Format`。 请参阅知识库文章"BUG: Format("%D") 失败`COleDateTime`和`COleDateTimeSpan`"(Q167338)。  
  
 [!code-cpp[NVC_ATLMFC_Utilities#176](../atl-mfc-shared/codesnippet/cpp/date-and-time-automation-support_1.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [日期和时间](../atl-mfc-shared/date-and-time.md)

