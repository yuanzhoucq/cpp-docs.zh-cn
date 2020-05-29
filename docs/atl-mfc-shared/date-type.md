---
title: 日期类型
ms.date: 11/04/2016
f1_keywords:
- DATE
helpviewer_keywords:
- Date data type, implementing
- Date data type
- DATE type
- Date data type, about Date data type
- MFC, date and time
- hour values representation
ms.assetid: 695853ed-b614-4575-b793-b8c287372038
ms.openlocfilehash: 6fd9fde83474ff4f439c0dd3989d4dc35fe1241a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317924"
---
# <a name="date-type"></a>日期类型

日期类型使用 8 字节浮点编号实现。 天数由从 1899 年 12 月 30 日开始的整数增量表示，午夜为时间零。 小时值以数字的小数部分的绝对值表示。 下表说明了多个日期及其 DATE 类型数值等效项：

|日期和时间|表示|
|-------------------|--------------------|
|1899年12月30日，午夜|0.00|
|1900年1月1日，午夜|2.00|
|1900年1月4日，午夜|5.00|
|1900年1月4日，上午6时|5.25|
|1900年1月4日中午|5.50|
|1900年1月4日，晚上9时|5.875|

日期日期类型以及`COleDateTime`类将日期和时间表示为经典数字行。 该`COleDateTime`类包含几种用于操作 DATE 值的方法，包括转换到其他常见日期格式和转换。

在自动化中使用这些日期和时间格式时，应注意以下几点：

- 日期在本地时间指定;在不同时区处理日期时，必须手动执行同步。

- 日期类型不考虑夏令时。

- 日期时间线对于小于 0 的日期值变得不连续（1899 年 12 月 30 日之前）。 这是因为日期值的整数部分被视为已签名，而小数部分则被视为未签名。 换句话说，日期值的整数部分可以是正数或负数，而日期值的小数部分始终添加到整个逻辑日期。 下表说明了几个示例：

|日期和时间|表示|
|-------------------|--------------------|
|1899年12月27日，午夜|-3.00|
|1899年12月28日中午|-2.50|
|1899年12月28日，午夜|-2.00|
|1899年12月29日，午夜|-1.00|
|1899年12月30日下午6时|-0.75|
|1899年12月30日中午|-0.50|
|1899年12月30日，上午6时|-0.25|
|1899年12月30日，午夜|0.00|
|1899年12月30日，上午6时|0.25|
|1899年12月30日中午|0.50|
|1899年12月30日下午6时|0.75|
|1899年12月31日，午夜|1.00|
|1900年1月1日，午夜|2.00|
|1900年1月1日中午|2.50|
|1900年1月2日，午夜|3.00|

> [!CAUTION]
> 请注意，由于 6：00 AM 始终由分数值 0.25 表示，而不考虑表示该日期的整数是正数（1899 年 12 月 30 日之后）还是负值（1899 年 12 月 30 日之前），因此简单的浮点比较会错误地将早于 12/30/1899 的一天 6：00 的 DATE 排序，以*晚于*当天 7：00 表示的日期。

有关日期和`COleDateTime`类型相关问题的详细信息，请参阅[COleDateTime 类](../atl-mfc-shared/reference/coledatetime-class.md)和[日期和时间：自动化支持](../atl-mfc-shared/date-and-time-automation-support.md)。

## <a name="see-also"></a>另请参阅

[日期和时间](../atl-mfc-shared/date-and-time.md)<br/>
[COleDateTime 类](../atl-mfc-shared/reference/coledatetime-class.md)
