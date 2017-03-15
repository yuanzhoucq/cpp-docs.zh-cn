---
title: "在日期和时间选取器控件中使用自定义格式字符串 | Microsoft Docs"
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
  - "CDateTimeCtrl 类, 显示样式"
  - "DateTimePicker 控件 [MFC]"
  - "DateTimePicker 控件 [MFC], 显示样式"
ms.assetid: 7d577f03-6ca0-4597-9093-50b78f304719
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 在日期和时间选取器控件中使用自定义格式字符串
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

默认情况下，和日期时间选择器控件用于显示当前日期或时间。提供三个格式类型 \(与一个样式对应的每一格式\):  
  
-   **DTS\_LONGDATEFORMAT** 以长格式的日期，产生类似“星期三的输出，2000 年 1 月 3 日”。  
  
-   **DTS\_SHORTDATEFORMAT** 以短格式显示日期，从而导致类似“1\/3\/00 "输出。  
  
-   **DTS\_TIMEFORMAT** 以长格式的时间，从而导致类似“5:31 的输出：下午 42 点”。  
  
 但是，使用自定义格式字符串，可以自定义日期或时间的外观。  此自定义字符串组成现有的格式字符，在格式字符或者这两者的组合。  一旦生成自定义字符串，请调用传入自定义字符串对 [CDateTimeCtrl::SetFormat](../Topic/CDateTimeCtrl::SetFormat.md)。  使用自定义格式字符串，则日期和时间选择器控件将显示当前值。  
  
 以下代码示例 \(其中 `m_dtPicker` 是 `CDateTimeCtrl` 对象\) 演示一种可能的解决方案：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#7](../mfc/codesnippet/CPP/using-custom-format-strings-in-a-date-and-time-picker-control_1.cpp)]  
  
 除了自定义格式字符串外，日期和时间选择器控件还支持 [回调字段](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md)。  
  
## 请参阅  
 [使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [控件](../mfc/controls-mfc.md)