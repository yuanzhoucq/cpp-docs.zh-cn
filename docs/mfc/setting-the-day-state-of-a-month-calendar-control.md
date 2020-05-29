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
ms.openlocfilehash: 9892f2d853687787dd76428fc9bc95f3a4f74565
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365431"
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>设置月历控件的日状态

月历控件的一个特性是存储一个月的每一天的信息的能力（称为“控件的日状态”）。 此信息用于强调当前所显示月份的特定日期。

> [!NOTE]
> 对象`CMonthCalCtrl`必须具有MCS_DAYSTATE样式才能显示日状态信息。

日状态信息表示为 32 位数据类型 **，MONTHDAYSTATE**。 **MONTHDAYSTATE**位字段中的每个位（1 到 31）表示一个月内一天的状态。 如果某个位处于打开状态，则以粗体显示对应的那一天，否则将不会突出显示。

有两种方法可以设置月份日历控件的日状态：显式调用[CMonthCalCtrl：：setDayState](../mfc/reference/cmonthcalctrl-class.md#setdaystate)或通过处理MCN_GETDAYSTATE通知消息。

## <a name="handling-the-mcn_getdaystate-notification-message"></a>处理 MCN_GETDAYSTATE 通知消息

MCN_GETDAYSTATE 消息由控件发送，以确定应如何显示可视月份中的日期。

> [!NOTE]
> 由于月历控件会缓存可视月份前后的月份，因此每次选择新月份时您将收到此通知。

要正确处理此消息，您必须确定要为其请求多少天状态信息，使用正确的值初始化**MONTHSDAYSTATE**结构数组，以及使用新信息初始化相关结构成员。 以下过程详细说明了必要的步骤，假定您有一`CMonthCalCtrl`个称为*m_monthcal*的对象和一个**monthDAYSTATE**对象数组*mdState*。

#### <a name="to-handle-the-mcn_getdaystate-notification-message"></a>处理 MCN_GETDAYSTATE 通知消息

1. 使用[类向导](reference/mfc-class-wizard.md)，将MCN_GETDAYSTATE消息的通知处理程序添加到*m_monthcal*对象（请参阅[将消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)）。

1. 在处理程序主体中，添加以下代码：

   [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]

   该示例将*pNMHDR*指针转换为正确的类型，然后确定请求的信息月数 （ 。`pDayState->cDayState` 对于每个月，当前位域 (`pDayState->prgDayState[i]`) 都会初始化为零，然后设置所需的日期（在本例中为每月的第 15 天）。

## <a name="see-also"></a>另请参阅

[使用 CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[控件](../mfc/controls-mfc.md)
