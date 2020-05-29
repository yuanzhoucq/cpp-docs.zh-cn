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
ms.openlocfilehash: 69270cc5663406f2c5d38ffccdbd35f39298a3d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354181"
---
# <a name="accessing-the-embedded-month-calendar-control"></a>访问嵌入的月历控件

可以通过调用[GetMonthCalCtrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl)成员函数从`CDateTimeCtrl`对象访问嵌入的月历控制对象。

> [!NOTE]
> 仅当日期和时间选取器控件没有**设置DTS_UPDOWN**样式时，才使用嵌入的月历控件。

如果要在显示嵌入的控件之前修改特定特性，这样做很有用。 为此，请处理**DTN_DROPDOWN**通知，检索月历控件（使用[CDateTimeCtrl：：getMonthCalCtrl），](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl)然后进行修改。 遗憾的是，月历控件不是持久的。

换句话说，当用户请求显示月历控件时，将创建新的月日历控件（**在通知DTN_DROPDOWN**之前）。 当用户拒绝时，控件将销毁 **（DTN_CLOSEUP**通知后）。 这意味着，关闭嵌入的控件时，将会丢失您在显示嵌入的控件之前修改的所有特性。

下面的示例演示了此过程，使用**处理程序执行DTN_DROPDOWN**通知。 代码将月历控件的背景颜色更改为灰色，调用[SetMonthCalColor。](../mfc/reference/cdatetimectrl-class.md#setmonthcalcolor) 代码如下所示:

[!code-cpp[NVC_MFCControlLadenDialog#5](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_1.cpp)]

如前所述，在关闭嵌入的控件时，将丢失对月历控件的属性所做的全部修改，但有两个例外。 第一个例外是月历控件的颜色，前面已经讨论了。 第二个例外是月历控件使用的字体。 您可以通过调用[CDateTimeCtrl：：setMonthCalFont](../mfc/reference/cdatetimectrl-class.md#setmonthcalfont)来修改默认字体，传递现有字体的句柄。 以下示例（其中 `m_dtPicker` 是日期和时间控件对象）演示了一种可能的方法：

[!code-cpp[NVC_MFCControlLadenDialog#6](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_2.cpp)]

通过调用 `CDateTimeCtrl::SetMonthCalFont` 更改字体之后，将存储新的字体，并在下次显示月历时使用该字体。

## <a name="see-also"></a>另请参阅

[使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[控件](../mfc/controls-mfc.md)
