---
title: "设置月历控件的日状态 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MCN_GETDAYSTATE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMonthCalCtrl 类, 设置日状态信息"
  - "MCN_GETDAYSTATE 通知"
  - "月历控件, 日状态信息"
ms.assetid: 435d1b11-ec0e-4121-9e25-aaa6af812a3c
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 设置月历控件的日状态
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

一个月历控件的特性是存储信息，参考控件的日状态对于月份的每天。  此信息用于强调当前显示的月份特定日期。  
  
> [!NOTE]
>  "CMonthCalCtrl"  对象必须具有 **MCS\_DAYSTATE** 样式显示日状态信息。  
  
 日状态信息表示为 32 位数据类型， **MONTHDAYSTATE**。  每位在 **MONTHDAYSTATE** 位域 \(1 到 31\) 表示一个月中一天的状态。  如果位打开，相应的天以粗体显示；否则它将显示无强调。  
  
 有两个方法设置日历控件的日状态：显式地调用 [CMonthCalCtrl::SetDayState](../Topic/CMonthCalCtrl::SetDayState.md) 或通过处理 **MCN\_GETDAYSTATE** 通知消息。  
  
## 处理 MCN\_GETDAYSTATE 通知消息  
 MCN\_GETDAYSTATE  信息由控件发送确定应如何显示可见月份的天。  
  
> [!NOTE]
>  由于控件缓存可见月份前后的月份，所以在选择新月份时您将收到此通知。  
  
 正确处理此消息，您必须确定请求多少个月的日信息状态，使用适当值初始化 **MONTHDAYSTATE** 结构数组，并使用新信息初始化相关的结构成员。  以下过程，详细给出了必要步骤，假定您有一个称为 `m_monthcal` 的 `CMonthCalCtrl` 对象和一个 **MONTHDAYSTATE** 数组对象， `mdState` 。  
  
#### 处理 MCN\_GETDAYSTATE 通知消息  
  
1.  使用属性窗口中，为传递到 `m_monthcal` 对象的 **MCN\_GETDAYSTATE** 消息添加通知处理程序， \(参见 [指向函数的映射信息](../mfc/reference/mapping-messages-to-functions.md)\)。  
  
2.  将以下代码添加到处理方法的主体：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/CPP/setting-the-day-state-of-a-month-calendar-control_1.cpp)]  
  
     示例转换 `pNMHDR` 指针到适当的类型，然后确定请求多少个月的信息 \(`pDayState->cDayState`\)。  对于每月，当前位域 \(`pDayState->prgDayState[i]`\) 初始化为零然后设置为需要的日期 \(在本例中，使用每月的第 15 天\)。  
  
## 请参阅  
 [使用 CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [控件](../mfc/controls-mfc.md)