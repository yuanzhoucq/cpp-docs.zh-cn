---
title: 处理日期和时间选取器控件中的通知消息
ms.date: 11/04/2016
f1_keywords:
- DTN_CLOSEUP
- DTN_DATETIMECHANGE
- DTN_DROPDOWN
helpviewer_keywords:
- DTN_DROPDOWN notification [MFC]
- DTN_DATETIMECHANGE notification [MFC]
- DTN_CLOSEUP notification [MFC]
- DateTimePicker control [MFC], handling notifications
- CDateTimeCtrl class [MFC], handling notifications
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: ffbe29ab-ff80-4609-89f7-260b404439c4
ms.openlocfilehash: ce84863744629d30248f94b94448d776177f9841
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57292882"
---
# <a name="processing-notification-messages-in-date-and-time-picker-controls"></a>处理日期和时间选取器控件中的通知消息

在用户与日期和时间选取器控件，该控件进行交互 (`CDateTimeCtrl`) 将通知消息发送到其父窗口，通常是视图或对话框对象。 如果您要在响应中做些什么，请处理这些消息。 例如，当用户打开的日期和时间选取器，以显示嵌入的月历控件时，发送 DTN_DROPDOWN 通知。

请使用“属性”窗口将通知处理程序添加到你希望实现的那些消息的父类。

以下列表介绍由日期和时间选取器控件发送的各种通知。

- DTN_DROPDOWN 通知即将显示嵌入的月历控件的父级。 尚未设置 DTS_UPDOWN 样式时，才发送此通知。 此通知的详细信息，请参阅[访问嵌入月历控件](../mfc/accessing-the-embedded-month-calendar-control.md)。

- DTN_CLOSEUP 通知即将关闭嵌入的月历控件的父级。 尚未设置 DTS_UPDOWN 样式时，才发送此通知。

- DTN_DATETIMECHANGE 通知控件中发生了更改的父级。

- DTN_FORMAT 通知父级文本所需的回调字段中显示。 此通知并回调字段的详细信息，请参阅[日期和时间选取器控件中使用回调字段](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md)。

- DTN_FORMATQUERY 请求要提供将在回调字段中显示的字符串的最大大小的父级。 处理此通知允许在所有时间，减少闪烁控件的显示中正确显示输出到控件。 此通知的详细信息，请参阅[日期和时间选取器控件中使用回调字段](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md)。

- DTN_USERSTRING 通知用户已完成的日期和时间选取器内容编辑的父控件。 如果已设置 DTS_APPCANPARSE 样式，将只发送此通知。

- 当用户在回调字段中，DTN_WMKEYDOWN 通知父级。 处理此通知来模拟用于日期和时间选取器控件中的非回调字段的相同键盘响应。 此通知的详细信息，请参阅[在 DTP 控件支持回调字段](/windows/desktop/Controls/date-and-time-picker-controls)Windows SDK 中。

## <a name="see-also"></a>请参阅

[使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[控件](../mfc/controls-mfc.md)
