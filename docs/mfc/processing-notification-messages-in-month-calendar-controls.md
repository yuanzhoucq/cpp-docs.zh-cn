---
title: "处理月历控件中的通知消息 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMonthCalCtrl 类, 日状态"
  - "CMonthCalCtrl 类, 通知"
  - "月历控件, 通知消息"
  - "通知, 用于 CMonthCalCtrl"
  - "通知, 月历控件"
ms.assetid: 607c3e90-0756-493b-9503-ce835a50c7ab
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 处理月历控件中的通知消息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当用户与控件交互 \(日历月份选择日期和\/或显示不同的月份\)，控件 \(`CMonthCalCtrl`\) 发送通知消息到其父窗口，通常视图或对话框对象。  如果您要在响应中做些什么，处理这些消息。  例如，在中，当用户选择一个新的月份时显示时，您可能会提供应代表的一组日期。  
  
 使用属性窗口为要实现的那些信息的父类添加通知处理程序。  
  
 下面的列表描述月历控件发送的不同通知。  
  
-   **MCN\_GETDAYSTATE** 请求天应以粗体显示的信息。  有关处理此通知的信息，请参见 [设置日历月份的日控件状态](../mfc/setting-the-day-state-of-a-month-calendar-control.md)。  
  
-   **MCN\_SELCHANGE** 通知父选择的日期或日期范围更改。  
  
-   **MCN\_SELECT** 通知父显式日期进行选择。  
  
## 请参阅  
 [使用 CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [控件](../mfc/controls-mfc.md)