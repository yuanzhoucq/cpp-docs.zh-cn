---
title: "日期类型 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- DATE
dev_langs:
- C++
helpviewer_keywords:
- Date data type, implementing
- Date data type
- DATE type
- Date data type, about Date data type
- MFC, date and time
- hour values representation
ms.assetid: 695853ed-b614-4575-b793-b8c287372038
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1f1ed7eb2b467fd52545f65f98b87e8e34ad71f3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="date-type"></a>日期类型
**日期**使用 8 字节浮点数实现类型。 按从 1899 年 12 月 30 日，时间为零点午夜开始的整数增量表示天。 小时值表示为绝对值的数值的数字的小数部分。 下表说明了几个日期中的连同其**日期**类型数值等效项：  
  
|日期和时间|表示形式|  
|-------------------|--------------------|  
|1899 年 12 月 30 日午夜|0.00|  
|1 年 1 月 1900 年午夜|2.00|  
|4 1900 年 1 月午夜|5.00|  
|4 1900 年 1 月，上午 6|5.25|  
|4 1900 年 1 月，中午|5.50|  
|4 1900 年 1 月，晚上 9。|5.875|  
  
 **日期**日期类型，以及`COleDateTime`类，表示日期和时间与经典数一行。 `COleDateTime`类包含用于操作日期值，包括其他常见的日期格式之间来回转换的几种方法。  
  
 使用自动化中的这些日期和时间格式时，应注意以下几点：  
  
-   在本地时间; 中指定日期使用在不同时区的日期时，必须手动执行同步。  
  
-   数据类型不考虑夏时制。  
  
-   （前 30 1899 年 12 月)，日期时间线将变为不连续的日期值小于 0。 这是因为日期值的整数部分被视为带符号，而小数部分将被视为无符号。 换而言之，日期值的整数部分中的可能是正数或负数，日期值的小数部分始终添加到整体逻辑日期时。 下表说明了几个示例：  
  
|日期和时间|表示形式|  
|-------------------|--------------------|  
|1899 年 12 月 27 日午夜|-3.00|  
|28 1899 年 12 月，中午|-2.50|  
|1899 年 12 月 28 日午夜|-2.00|  
|1899 年 12 月 29 日午夜|-1.00|  
|1899 年 12 月 30 日，下午 6 点|-0.75|  
|30 1899 年 12 月，中午|-0.50|  
|1899 年 12 月 30 日，上午 6|-0.25|  
|1899 年 12 月 30 日午夜|0.00|  
|1899 年 12 月 30 日，上午 6|0.25|  
|30 1899 年 12 月，中午|0.50|  
|1899 年 12 月 30 日，下午 6 点|0.75|  
|1899 年 12 月 31 日午夜|1.00|  
|1 年 1 月 1900 年午夜|2.00|  
|1 1900 年 1 月，中午|2.50|  
|2 1900 年 1 月午夜|3.00|  
  
> [!CAUTION]
>  请注意，因为上午 6:00 始终由分数值 0.25，无论 （在 1899 年 12 月 30 日） 表示一天的整数是否正或负 （之前 1899 年 12 月 30 日），简单的浮点点比较将错误地对进行排序任何**日期**表示早于 12/30/1899 为一天上午 6:00*更高版本*比**日期**表示该同一天上午 7:00。  
  
 与相关的问题的详细信息**日期**和`COleDateTime`下找不到类型[COleDateTime 类](../atl-mfc-shared/reference/coledatetime-class.md)和[日期和时间： 自动化支持](../atl-mfc-shared/date-and-time-automation-support.md)。  
  
## <a name="see-also"></a>请参阅  
 [日期和时间](../atl-mfc-shared/date-and-time.md)   
 [COleDateTime 类](../atl-mfc-shared/reference/coledatetime-class.md)

