---
title: 设置每月的日状态月历控件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MCN_GETDAYSTATE
dev_langs:
- C++
helpviewer_keywords:
- CMonthCalCtrl class [MFC], setting day state info
- MCN_GETDAYSTATE notification [MFC]
- month calendar controls [MFC], day state info
ms.assetid: 435d1b11-ec0e-4121-9e25-aaa6af812a3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e589f07d1c9c54c3acd2fa3ff6a0f346077f9b4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053092"
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>设置月历控件的日状态

月历控件的一个特性是存储一个月的每一天的信息的能力（称为“控件的日状态”）。 此信息用于强调当前所显示月份的特定日期。

> [!NOTE]
>  `CMonthCalCtrl`对象必须具有 2&gt;mcs_daystate&lt;2 样式以显示日状态信息。

日状态信息表示为 32 位数据类型， **MONTHDAYSTATE**。 中的每个位**MONTHDAYSTATE**位域 (1 到 31 之间) 表示一个月中某天的状态。 如果某个位处于打开状态，则以粗体显示对应的那一天，否则将不会突出显示。

设置月历控件的日状态的两种方法： 通过调用显式[cmonthcalctrl:: Setdaystate](../mfc/reference/cmonthcalctrl-class.md#setdaystate)或通过处理 MCN_GETDAYSTATE 通知消息。

## <a name="handling-the-mcngetdaystate-notification-message"></a>处理 MCN_GETDAYSTATE 通知消息

MCN_GETDAYSTATE 消息由控件发送，以确定应如何显示可视月份中的日期。

> [!NOTE]
>  由于月历控件会缓存可视月份前后的月份，因此每次选择新月份时您将收到此通知。

若要正确处理此消息，必须确定多少正在显示日状态信息的几个月针对请求，初始化的数组**MONTHDAYSTATE**具有适当的值，并初始化相关的结构成员的结构使用新的信息。 以下过程详细介绍所需的步骤，假定`CMonthCalCtrl`对象调用*m_monthcal*和一个数组**MONTHDAYSTATE**对象， *mdState*.

#### <a name="to-handle-the-mcngetdaystate-notification-message"></a>处理 MCN_GETDAYSTATE 通知消息

1. 使用属性窗口中，将添加到 MCN_GETDAYSTATE 消息通知处理程序*m_monthcal*对象 (请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md))。

1. 在处理程序主体中，添加以下代码：

   [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]

   此示例将转换*pNMHDR*指向正确的类型，然后确定正在请求多少个月的信息 (`pDayState->cDayState`)。 对于每个月，当前位域 (`pDayState->prgDayState[i]`) 都会初始化为零，然后设置所需的日期（在本例中为每月的第 15 天）。

## <a name="see-also"></a>请参阅

[使用 CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[控件](../mfc/controls-mfc.md)

