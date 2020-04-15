---
title: 使用 CDateTimeCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- DateTimePicker control [MFC], CDateTimeCtrl class
ms.assetid: cb2a8720-43f1-4c33-a3a4-def9a1622e00
ms.openlocfilehash: 697ca7446712853594d6e4e3e49872d5710562aa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366549"
---
# <a name="using-cdatetimectrl"></a>使用 CDateTimeCtrl

日期和时间选取器控件 （[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)） 实现了输入或选择特定日期的直观且可识别的方法。 控件的主接口在功能上与组合框类似。 但是，如果用户展开控件，则会出现一个月的日历控件（默认情况下），允许用户指定特定日期。 选择日期时，月历控件将自动消失。

> [!NOTE]
> 要在项目中同时`CDateTimePicker`使用`CMonthCalCtrl`和 类，必须包括 AFXDTCTL。H，通常在项目的STDAFX中。H 文件。

## <a name="what-do-you-want-to-know-more-about"></a>你想知道更多

- [创建日期和时间选取器控件](../mfc/creating-the-date-and-time-picker-control.md)

- [日期和时间选取器控制示例](../mfc/date-and-time-picker-control-examples.md)

- [访问嵌入式月历控件](../mfc/accessing-the-embedded-month-calendar-control.md)

- [在日期和时间选取器控件中使用自定义格式字符串](../mfc/using-custom-format-strings-in-a-date-and-time-picker-control.md)

- [在日期和时间选取器控件中使用回调字段](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md)

- [在日期和时间选取器控件中处理通知消息](../mfc/processing-notification-messages-in-date-and-time-picker-controls.md)

## <a name="see-also"></a>另请参阅

[控件](../mfc/controls-mfc.md)
