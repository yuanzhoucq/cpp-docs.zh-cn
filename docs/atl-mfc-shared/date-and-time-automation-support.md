---
title: 日期和时间： 自动化支持 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b5f6f0c6bf9933f06da4b50f9754a0d68814e16b
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883747"
---
# <a name="date-and-time-automation-support"></a>日期和时间： 自动化支持
本文介绍如何利用与日期和时间管理相关的类库服务。 所述的过程包括：  
  
-   [获取当前时间](../atl-mfc-shared/current-time-automation-classes.md)  
  
-   [计算经过的时间](../atl-mfc-shared/elapsed-time-automation-classes.md)  
  
-   [格式设置日期/时间的字符串表示形式](../atl-mfc-shared/formatting-time-automation-classes.md)  
  
 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)类提供了一种方法来表示日期和时间信息。 它提供了更细的粒度和更大的范围比[CTime](../atl-mfc-shared/reference/ctime-class.md)类。 [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)类表示已用时间，例如两个之间的差异`COleDateTime`对象。  
  
 `COleDateTime`并`COleDateTimeSpan`类旨在用于`COleVariant`在自动化中使用的类。 `COleDateTime` 和`COleDateTimeSpan`还可在 MFC 数据库编程中，但只要您想要操作的日期和时间值，可以使用它们。 尽管`COleDateTime`类具有更大范围的值和更细的粒度比`CTime`类，它需要更多存储每个对象比`CTime`。 也有一些特殊注意事项使用基础的日期类型时。 请参阅[日期类型](../atl-mfc-shared/date-type.md)有关的详细信息的日期的实现。  
  
 `COleDateTime` 对象可以用于表示 100，年 1 月 1 日和年 12 月 31 日之间的日期到 9999。 `COleDateTime` 对象浮点值，使用的分辨率大约为 1 毫秒。 `COleDateTime` 在 MFC 文档中定义的日期数据类型为基础[COleDateTime::operator 日期](../atl-mfc-shared/reference/coledatetime-class.md#operator_date)。 日期的实际实现超出这些边界。 `COleDateTime`实现规定了这些边界为了便于处理类。  
  
 `COleDateTime` 不支持儒略历日期。 假定公历日历以来的时间将扩展到 100 年 1 月 1 日。  
  
 `COleDateTime` 将忽略夏时制 (DST)。 下面的代码示例进行比较计算跨越 DST 切换日期的时间跨度的两种方法： 一个使用 CRT，以及其他使用`COleDateTime`。 DST 切换，在大多数区域设置中的第二周中年 4 月和年 10 月中的第三。  
  
 第一种方法中设置两个`CTime`对象， *time1*并*time2*，再到 5 年 4 月和年 4 月 6 分别使用标准的 C 类型结构`tm`和`time_t`。 代码将显示*time1*并*time2*和它们之间的时间跨度。  
  
 第二种方法创建两个`COleDateTime`对象，`oletime1`并`oletime2`，并将它们设置为的相同日期*time1*并*time2*。 它将显示`oletime1`和`oletime2`和它们之间的时间跨度。  
  
 CRT 正确地计算差值为 23 个小时。 `COleDateTimeSpan` 计算差值为 24 小时。  
  
 请注意，一种解决方法使用接近结束时的示例显示使用正确的日期`COleDateTime::Format`。 请参阅知识库文章"BUG: Format("%D") 出于`COleDateTime`和`COleDateTimeSpan`"(Q167338)。  
  
 [!code-cpp[NVC_ATLMFC_Utilities#176](../atl-mfc-shared/codesnippet/cpp/date-and-time-automation-support_1.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [日期和时间](../atl-mfc-shared/date-and-time.md)

