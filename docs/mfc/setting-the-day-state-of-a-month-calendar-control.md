---
title: "设置每月的日状态月历控件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: MCN_GETDAYSTATE
dev_langs: C++
helpviewer_keywords:
- CMonthCalCtrl class [MFC], setting day state info
- MCN_GETDAYSTATE notification [MFC]
- month calendar controls [MFC], day state info
ms.assetid: 435d1b11-ec0e-4121-9e25-aaa6af812a3c
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5c634815065c68cceb3c528222c0fd60e19b6827
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>设置月历控件的日状态
月历控件的一个特性是存储一个月的每一天的信息的能力（称为“控件的日状态”）。 此信息用于强调当前所显示月份的特定日期。  
  
> [!NOTE]
>  `CMonthCalCtrl`对象必须具有**MCS_DAYSTATE**样式以显示日状态信息。  
  
 日状态信息表示为 32 位数据类型， **MONTHDAYSTATE**。 中的每个位**MONTHDAYSTATE**位域 (1 到 31) 表示一个月中的一天的状态。 如果某个位处于打开状态，则以粗体显示对应的那一天，否则将不会突出显示。  
  
 用于设置月历控件的日状态的两种方法： 显式通过调用[cmonthcalctrl:: Setdaystate](../mfc/reference/cmonthcalctrl-class.md#setdaystate)或通过处理**MCN_GETDAYSTATE**通知消息。  
  
## <a name="handling-the-mcngetdaystate-notification-message"></a>处理 MCN_GETDAYSTATE 通知消息  
 **MCN_GETDAYSTATE**控件发送消息以确定应如何显示可视月份中的日期。  
  
> [!NOTE]
>  由于月历控件会缓存可视月份前后的月份，因此每次选择新月份时您将收到此通知。  
  
 若要正确处理此消息，你必须确定多少正在显示日状态信息的几个月的请求，初始化的数组**MONTHDAYSTATE**具有适当的值，并初始化相关的结构成员的结构使用新信息。 以下过程中，详细列出了必要步骤，假定你具有`CMonthCalCtrl`调用对象`m_monthcal`和数组**MONTHDAYSTATE**对象， `mdState`。  
  
#### <a name="to-handle-the-mcngetdaystate-notification-message"></a>处理 MCN_GETDAYSTATE 通知消息  
  
1.  使用属性窗口中，添加的通知处理程序**MCN_GETDAYSTATE**消息`m_monthcal`对象 (请参阅[消息映射到函数](../mfc/reference/mapping-messages-to-functions.md))。  
  
2.  在处理程序主体中，添加以下代码：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]  
  
     本示例将 `pNMHDR` 指针转换为适当的类型，然后确定请求多少个月的信息 (`pDayState->cDayState`)。 对于每个月，当前位域 (`pDayState->prgDayState[i]`) 都会初始化为零，然后设置所需的日期（在本例中为每月的第 15 天）。  
  
## <a name="see-also"></a>请参阅  
 [使用 CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [控件](../mfc/controls-mfc.md)

