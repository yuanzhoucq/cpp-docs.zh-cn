---
title: 设置月历控件的日状态
ms.date: 11/04/2016
f1_keywords:
- MCN_GETDAYSTATE
helpviewer_keywords:
- CMonthCalCtrl class [MFC], setting day state info
- MCN_GETDAYSTATE notification [MFC]
- month calendar controls [MFC], day state info
ms.assetid: 435d1b11-ec0e-4121-9e25-aaa6af812a3c
ms.openlocfilehash: b8a91c8b0c3bdef9256628b9226c5f3ff154ed7d
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907529"
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>设置月历控件的日状态

月历控件的一个特性是存储一个月的每一天的信息的能力（称为“控件的日状态”）。 此信息用于强调当前所显示月份的特定日期。

> [!NOTE]
>  `CMonthCalCtrl`对象必须具有 MCS_DAYSTATE 样式以显示日状态信息。

日期状态信息表示为32位数据类型**MONTHDAYSTATE**。 **MONTHDAYSTATE**位域中的每个位（1到31）表示一个月中某一天的状态。 如果某个位处于打开状态，则以粗体显示对应的那一天，否则将不会突出显示。

可以通过两种方法设置月历控件的日状态：使用对[CMonthCalCtrl：： SetDayState](../mfc/reference/cmonthcalctrl-class.md#setdaystate)的调用或通过处理 MCN_GETDAYSTATE 通知消息进行显式调用。

## <a name="handling-the-mcn_getdaystate-notification-message"></a>处理 MCN_GETDAYSTATE 通知消息

MCN_GETDAYSTATE 消息由控件发送，以确定应如何显示可见月份中的日期。

> [!NOTE]
>  由于月历控件会缓存可视月份前后的月份，因此每次选择新月份时您将收到此通知。

若要正确处理此消息，您必须确定为其请求了多少个月的省/市/自治区信息，使用正确的值初始化**MONTHDAYSTATE**结构的数组，并使用新的初始化相关结构成员。信息. 下面的过程详细说明了必需的步骤，假设你有一个`CMonthCalCtrl`名为*m_monthcal*的对象和一个**MONTHDAYSTATE**对象*mdState*的数组。

#### <a name="to-handle-the-mcn_getdaystate-notification-message"></a>处理 MCN_GETDAYSTATE 通知消息

1. 使用[类向导](reference/mfc-class-wizard.md)将 MCN_GETDAYSTATE 消息的通知处理程序添加到*m_monthcal*对象（请参阅将[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)）。

1. 在处理程序主体中，添加以下代码：

   [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]

   该示例将*pNMHDR*指针转换为正确的类型，然后确定请求的信息的月份数（`pDayState->cDayState`）。 对于每个月，当前位域 (`pDayState->prgDayState[i]`) 都会初始化为零，然后设置所需的日期（在本例中为每月的第 15 天）。

## <a name="see-also"></a>请参阅

[使用 CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
