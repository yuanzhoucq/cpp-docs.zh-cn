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
ms.openlocfilehash: 452d24bf1ffd157366f357a510e8c8cfaad28d91
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908084"
---
# <a name="processing-notification-messages-in-month-calendar-controls"></a>处理月历控件中的通知消息

当用户与月历控件交互（选择日期和/或查看不同月份）时，控件（`CMonthCalCtrl`）会将通知消息发送到其父窗口，通常是视图或对话框对象。 如果您要在响应中做些什么，请处理这些消息。 例如，当用户选择一个新月份来查看时，可以提供一组应强调的日期。

使用[类向导](reference/mfc-class-wizard.md)将通知处理程序添加到要实现的那些消息的父类。

以下列表描述了月历控件发送的各种通知。

- MCN_GETDAYSTATE 请求应以粗体显示的日期。 有关处理此通知的信息，请参阅[设置月历控件的日状态](../mfc/setting-the-day-state-of-a-month-calendar-control.md)。

- MCN_SELCHANGE 通知父项所选日期或日期范围已更改。

- MCN_SELECT 通知父项已进行了显式日期选择。

## <a name="see-also"></a>请参阅

[使用 CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
