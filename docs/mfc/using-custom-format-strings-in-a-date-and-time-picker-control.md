---
title: 在日期和时间选取器控件中使用自定义格式字符串
ms.date: 11/04/2016
helpviewer_keywords:
- CDateTimeCtrl class [MFC], display styles
- DateTimePicker control [MFC], display styles
- DateTimePicker control [MFC]
ms.assetid: 7d577f03-6ca0-4597-9093-50b78f304719
ms.openlocfilehash: 8da5ecaf473d6d3c35ddc1b95ac856ce8c12f163
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57286881"
---
# <a name="using-custom-format-strings-in-a-date-and-time-picker-control"></a>在日期和时间选取器控件中使用自定义格式字符串

默认情况下，日期和时间选取器控件提供了 3 种格式（每种格式对应于一个唯一样式）来显示当前日期或时间：

- **DTS_LONGDATEFORMAT**长格式，生成类似"星期三，2000 年 1 月 3，"的输出中显示的日期。

- **DTS_SHORTDATEFORMAT**短格式，生成类似"1/3/00"的输出中显示的日期。

- **DTS_TIMEFORMAT**长格式，生成类似"下午 5:31:42"的输出中显示的时间。

但是，您可通过使用自定义格式字符串来自定义日期或时间的外观。 此自定义字符串组成现有格式字符、无格式字符或二者的组合。 自定义字符串生成后，请调用[cdatetimectrl:: Setformat](../mfc/reference/cdatetimectrl-class.md#setformat)自定义字符串中传递。 日期和时间选取器控件之后将使用您的自定义格式字符串显示当前值。

下面的代码示例 (其中*m_dtPicker*是`CDateTimeCtrl`对象) 演示了一个可能的解决方案：

[!code-cpp[NVC_MFCControlLadenDialog#7](../mfc/codesnippet/cpp/using-custom-format-strings-in-a-date-and-time-picker-control_1.cpp)]

除了自定义格式字符串的日期和时间选取器控件还支持[回调字段](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md)。

## <a name="see-also"></a>请参阅

[使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[控件](../mfc/controls-mfc.md)
