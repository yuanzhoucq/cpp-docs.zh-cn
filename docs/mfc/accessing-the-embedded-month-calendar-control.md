---
title: 访问嵌入的月历控件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DateTimePicker control [MFC], accessing month calendar
- CDateTimeCtrl class [MFC], accessing embedded control
- month calendar controls [MFC], embedded in date/time picker
- CMonthCalCtrl class [MFC], changing the font
- month calendar controls [MFC], changing the font
- DateTimePicker control [MFC]
ms.assetid: 355e97ed-cf81-4df3-a2f8-9ddbbde93227
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a92660223c84c5f53bc848e72b03316602180d36
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430288"
---
# <a name="accessing-the-embedded-month-calendar-control"></a>访问嵌入的月历控件

可以从访问嵌入的月历控件对象`CDateTimeCtrl`对象通过调用[GetMonthCalCtrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl)成员函数。

> [!NOTE]
>  仅当日期和时间选取器控件没有使用嵌入的月历控件**DTS_UPDOWN**样式集。

如果要在显示嵌入的控件之前修改特定特性，这样做很有用。 若要完成此操作，处理**DTN_DROPDOWN**通知，检索月历控件 (使用[cdatetimectrl:: Getmonthcalctrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl))，然后进行修改。 遗憾的是，月历控件不是持久的。

换而言之，当用户请求显示月历控件时，将创建一个新月份日历控件 (之前**DTN_DROPDOWN**通知)。 销毁控件 (后**DTN_CLOSEUP**通知) 时由用户关闭。 这意味着，关闭嵌入的控件时，将会丢失您在显示嵌入的控件之前修改的所有特性。

下面的示例演示此过程中，使用的处理程序**DTN_DROPDOWN**通知。 在代码发生更改的月份的日历控件，通过调用的背景色[SetMonthCalColor](../mfc/reference/cdatetimectrl-class.md#setmonthcalcolor)，为灰色。 代码如下所示:

[!code-cpp[NVC_MFCControlLadenDialog#5](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_1.cpp)]

如前所述，在关闭嵌入的控件时，将丢失对月历控件的属性所做的全部修改，但有两个例外。 第一个例外是月历控件的颜色，前面已经讨论了。 第二个例外是月历控件使用的字体。 可以通过调用来修改默认字体[cdatetimectrl:: Setmonthcalfont](../mfc/reference/cdatetimectrl-class.md#setmonthcalfont)，传递现有字体的句柄。 以下示例（其中 `m_dtPicker` 是日期和时间控件对象）演示了一种可能的方法：

[!code-cpp[NVC_MFCControlLadenDialog#6](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_2.cpp)]

通过调用 `CDateTimeCtrl::SetMonthCalFont` 更改字体之后，将存储新的字体，并在下次显示月历时使用该字体。

## <a name="see-also"></a>请参阅

[使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[控件](../mfc/controls-mfc.md)

