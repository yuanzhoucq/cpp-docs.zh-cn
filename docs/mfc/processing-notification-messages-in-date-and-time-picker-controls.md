---
title: "处理日期和时间选取器控件中的通知消息 | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DTN_CLOSEUP"
  - "DTN_DATETIMECHANGE"
  - "DTN_DROPDOWN"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDateTimeCtrl 类, 处理通知"
  - "DateTimePicker 控件 [MFC]"
  - "DateTimePicker 控件 [MFC], 处理通知"
  - "DTN_CLOSEUP 通知"
  - "DTN_DATETIMECHANGE 通知"
  - "DTN_DROPDOWN 通知"
  - "DTN_FORMAT 通知"
ms.assetid: ffbe29ab-ff80-4609-89f7-260b404439c4
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 处理日期和时间选取器控件中的通知消息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当用户与日期和时间选择器控件交互，控件 \(`CDateTimeCtrl`\) 发送通知消息到其父窗口，通常视图或对话框对象。  如果您要执行某个在响应中，处理这些消息。  例如，日期时间选择器和，当用户打开显示了嵌入的月份时，日历控件的 **DTN\_DROPDOWN** 通知发送。  
  
 使用"属性"窗口添加通知处理程序为要实现的那些信息的父类。  
  
 下面的列表描述和日期时间选择器控件发送的不同通知。  
  
-   **DTN\_DROPDOWN** 通知父月历嵌入的控件显示。  当 **DTS\_UPDOWN** 未设置样式时，此通知仅发送。  此通知有关的更多信息，请参见 [月历访问嵌入的控件](../mfc/accessing-the-embedded-month-calendar-control.md)。  
  
-   **DTN\_CLOSEUP** 通知父嵌入的月历控件将关闭。  当 **DTS\_UPDOWN** 未设置样式时，此通知仅发送。  
  
-   **DTN\_DATETIMECHANGE** 通知父控件将发生。  
  
-   **DTN\_FORMAT** 通知父文本需要回调中的字段显示。  有关此通知和回调字段的更多信息，请参见 [使用日期和时间选择器控件的回调字段](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md)。  
  
-   **DTN\_FORMATQUERY** 请求提供父在回调字段将显示字符串的最大允许大小。  处理此通知允许控件始终正确查看输出，以在控件显示中闪烁。  此通知有关的更多信息，请参见 [使用日期和时间选择器控件的回调字段](../mfc/using-callback-fields-in-a-date-and-time-picker-control.md)。  
  
-   **DTN\_USERSTRING** 通知父用户完成编辑日期和时间选择器控件的内容。  当 **DTS\_APPCANPARSE** 时，此样式设置仅发送通知。  
  
-   在回调的用户类型时字段，**DTN\_WMKEYDOWN** 通知父。  此通知处理模拟为日期和时间选择器控件的回调不支持的字段相同键盘响应。  此通知有关的更多信息，请参见" [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [支持 DTP 控件的回调字段](http://msdn.microsoft.com/library/windows/desktop/bb761726)。  
  
## 请参阅  
 [使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)   
 [控件](../mfc/controls-mfc.md)