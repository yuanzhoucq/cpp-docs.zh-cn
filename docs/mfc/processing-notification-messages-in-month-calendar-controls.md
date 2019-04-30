---
title: 处理月历控件中的通知消息
ms.date: 11/04/2016
helpviewer_keywords:
- CMonthCalCtrl class [MFC], notifications
- CMonthCalCtrl class [MFC], day states
- month calendar controls [MFC], notification messages
- notifications [MFC], for CMonthCalCtrl
- notifications [MFC], month calendar control
ms.assetid: 607c3e90-0756-493b-9503-ce835a50c7ab
ms.openlocfilehash: fc0bb475a95450c281c92b500083c9502df50931
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346148"
---
# <a name="processing-notification-messages-in-month-calendar-controls"></a>处理月历控件中的通知消息

在用户与月历控件 （选择的日期和/或查看不同的月份），该控件进行交互 (`CMonthCalCtrl`) 将通知消息发送到其父窗口，通常是视图或对话框对象。 如果您要在响应中做些什么，请处理这些消息。 例如，当用户选择一个新的月份，即可查看，可以提供一组应突出显示的日期。

请使用“属性”窗口将通知处理程序添加到你希望实现的那些消息的父类。

以下列表介绍由月历控件发送的各种通知。

- 有关哪些应以粗体显示天 MCN_GETDAYSTATE 请求信息。 有关处理此通知的信息，请参阅[设置月历控件的日状态](../mfc/setting-the-day-state-of-a-month-calendar-control.md)。

- MCN_SELCHANGE 向所选的日期的范围已更改的父级。

- MCN_SELECT 通知进行显式日期选择父级。

## <a name="see-also"></a>请参阅

[使用 CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
