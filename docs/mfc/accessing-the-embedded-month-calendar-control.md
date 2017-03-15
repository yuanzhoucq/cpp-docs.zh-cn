---
title: "访问嵌入的月历控件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDateTimeCtrl 类, 访问嵌入控件"
  - "CMonthCalCtrl 类, 更改字体"
  - "DateTimePicker 控件 [MFC]"
  - "DateTimePicker 控件 [MFC], 访问月历"
  - "月历控件, 更改字体"
  - "月历控件, 嵌入在日期/时间选择器中"
ms.assetid: 355e97ed-cf81-4df3-a2f8-9ddbbde93227
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 访问嵌入的月历控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

月历嵌入的控件对象可与调用的 `CDateTimeCtrl` 对象访问 [GetMonthCalCtrl](../Topic/CDateTimeCtrl::GetMonthCalCtrl.md) 成员函数。  
  
> [!NOTE]
>  月历嵌入的控件，仅当和日期时间选择器控件没有 **DTS\_UPDOWN** 的样式设置时。  
  
 如果要修改特定特性，在嵌入的控件显示是有用的。  为此，请处理 **DTN\_DROPDOWN** 通知，检索月历控件 \(使用 [CDateTimeCtrl::GetMonthCalCtrl](../Topic/CDateTimeCtrl::GetMonthCalCtrl.md)\)，然后进行修改。  遗憾的是月份，日历控件无需采用不可变的。  
  
 换言之，那么，当用户请求月历控件显示一个新月份，日历控件创建 \(在 **DTN\_DROPDOWN** 之前通知\)。  销毁控件 \(在 **DTN\_CLOSEUP** 通知\) 后，在用户关闭。  这意味着您修改的任何特性，嵌入的控件关闭时在嵌入控件的显示之前会丢失。  
  
 使用 **DTN\_DROPDOWN** 通知的，一个处理程序。下面的示例演示此过程。  代码更改月历控件的背景色，并调用为 [SetMonthCalColor](../Topic/CDateTimeCtrl::SetMonthCalColor.md)，设置为灰色。  代码如下所示:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#5](../mfc/codesnippet/CPP/accessing-the-embedded-month-calendar-control_1.cpp)]  
  
 当嵌入的控件关闭时，如前所述，该月历控件属性的任何修改将丢失，会有两个异常。  第一个异常，月历控件的颜色，在前面已经讨论。  第二个异常是月历控件的字体。  可以通过调用修改默认字体为 [CDateTimeCtrl::SetMonthCalFont](../Topic/CDateTimeCtrl::SetMonthCalFont.md)，将现有的字体的句柄。  以下示例 \(其中 `m_dtPicker` 是日期和时间对象控件\) 演示一种可能的方法：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#6](../mfc/codesnippet/CPP/accessing-the-embedded-month-calendar-control_2.cpp)]  
  
 字体更改之后，使用对 `CDateTimeCtrl::SetMonthCalFont`的调用上，新的字体和使用，当下次月历将显示。  
  
## 请参阅  
 [使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [控件](../mfc/controls-mfc.md)