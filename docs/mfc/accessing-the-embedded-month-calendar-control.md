---
title: 访问嵌入的月历控件
ms.date: 11/04/2016
helpviewer_keywords:
- DateTimePicker control [MFC], accessing month calendar
- CDateTimeCtrl class [MFC], accessing embedded control
- month calendar controls [MFC], embedded in date/time picker
- CMonthCalCtrl class [MFC], changing the font
- month calendar controls [MFC], changing the font
- DateTimePicker control [MFC]
ms.assetid: 355e97ed-cf81-4df3-a2f8-9ddbbde93227
ms.openlocfilehash: 66a9ef7fd49ea81ddac4779aa6d1c3f12fbe4c55
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617381"
---
# <a name="accessing-the-embedded-month-calendar-control"></a>访问嵌入的月历控件

可以通过 `CDateTimeCtrl` 调用[GetMonthCalCtrl](reference/cdatetimectrl-class.md#getmonthcalctrl)成员函数，从对象访问嵌入的月历控件对象。

> [!NOTE]
> 仅当日期和时间选取器控件没有**DTS_UPDOWN**的样式集时，才使用嵌入的月历控件。

如果要在显示嵌入的控件之前修改特定特性，这样做很有用。 若要完成此操作，请处理**DTN_DROPDOWN**通知，检索月历控件（使用[CDateTimeCtrl：： GetMonthCalCtrl](reference/cdatetimectrl-class.md#getmonthcalctrl)），并进行修改。 遗憾的是，月历控件不是持久的。

换言之，当用户请求显示月历控件时，将创建一个新的月历控件（在**DTN_DROPDOWN**通知之前）。 用户关闭控件时，控件将被销毁（在**DTN_CLOSEUP**通知之后）。 这意味着，关闭嵌入的控件时，将会丢失您在显示嵌入的控件之前修改的所有特性。

下面的示例演示了如何使用**DTN_DROPDOWN**通知的处理程序。 该代码会将月历控件的背景色（通过调用[SetMonthCalColor](reference/cdatetimectrl-class.md#setmonthcalcolor)）更改为灰色。 代码如下所示:

[!code-cpp[NVC_MFCControlLadenDialog#5](codesnippet/cpp/accessing-the-embedded-month-calendar-control_1.cpp)]

如前所述，在关闭嵌入的控件时，将丢失对月历控件的属性所做的全部修改，但有两个例外。 第一个例外是月历控件的颜色，前面已经讨论了。 第二个例外是月历控件使用的字体。 可以通过调用[CDateTimeCtrl：： SetMonthCalFont](reference/cdatetimectrl-class.md#setmonthcalfont)来修改默认字体，同时传递现有字体的句柄。 以下示例（其中 `m_dtPicker` 是日期和时间控件对象）演示了一种可能的方法：

[!code-cpp[NVC_MFCControlLadenDialog#6](codesnippet/cpp/accessing-the-embedded-month-calendar-control_2.cpp)]

通过调用 `CDateTimeCtrl::SetMonthCalFont` 更改字体之后，将存储新的字体，并在下次显示月历时使用该字体。

## <a name="see-also"></a>另请参阅

[使用 CDateTimeCtrl](using-cdatetimectrl.md)<br/>
[控件](controls-mfc.md)
