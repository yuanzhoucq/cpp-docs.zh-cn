---
title: 日期类型 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe80a16f0085e37feaf7c80611fa303f1d3bf1ab
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425764"
---
# <a name="date-type"></a>日期类型

日期类型是使用 8 字节浮点数实现的。 由从 1899 年 12 月 30 日，午夜时间为零点开始以整数增量表示天。 小时值表示为绝对值的数值的数字的小数部分。 下表说明了几个日期中的以及其日期类型数值等效项：

|日期和时间|表示形式|
|-------------------|--------------------|
|1899 年 12 月 30 日午夜|0.00|
|1 1900 年 1 月午夜|2.00|
|4 个 1900 年 1 月午夜|5.00|
|4 个 1900 年 1 月，上午 6|5.25|
|4 个 1900 年 1 月，中午|5.50|
|4 个 1900 年 1 月，晚上 9 点|5.875|

日期日期类型，并将`COleDateTime`类，表示日期和时间作为经典的数行。 `COleDateTime`类包含用于处理日期值，包括与其他常用的日期格式的转换的多个方法。

使用自动化中使用这些日期和时间格式时，应注意以下几点：

- 本地时间; 在指定日期当使用不同的时区中的日期时，必须手动执行同步。

- 日期类型不考虑夏时制。

- （在之前 30 1899 年 12 月)，日期时间线将变为不连续的日期值小于 0。 这是因为日期值的整数部分被视为带符号，而小数部分被视为无符号。 换而言之，日期值的整数部分可能为正数或负数，日期值的小数部分始终添加到整体逻辑日期时。 下表说明了几个示例：

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
|1 1900 年 1 月午夜|2.00|
|1 1900 年 1 月，中午|2.50|
|2 个 1900 年 1 月午夜|3.00|

> [!CAUTION]
>  请注意，由于上午 6:00 始终由分数值 0.25 不考虑 （后 1899 年 12 月 30 日） 表示一天的整数是否正或负 （之前 1899 年 12 月 30 日），简单的浮动点比较会错误地排序表示早于 12/30/1899 为一天上午 6:00 任何日期*更高版本*于日期表示该同一天上午 7:00。

与日期相关的问题的详细信息和`COleDateTime`下找不到类型[COleDateTime 类](../atl-mfc-shared/reference/coledatetime-class.md)并[日期和时间： 自动化支持](../atl-mfc-shared/date-and-time-automation-support.md)。

## <a name="see-also"></a>请参阅

[日期和时间](../atl-mfc-shared/date-and-time.md)<br/>
[COleDateTime 类](../atl-mfc-shared/reference/coledatetime-class.md)

