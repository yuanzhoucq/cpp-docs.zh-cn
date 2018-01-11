---
title: "月历控件中的处理通知消息 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CMonthCalCtrl class [MFC], notifications
- CMonthCalCtrl class [MFC], day states
- month calendar controls [MFC], notification messages
- notifications [MFC], for CMonthCalCtrl
- notifications [MFC], month calendar control
ms.assetid: 607c3e90-0756-493b-9503-ce835a50c7ab
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 75b07973b1410c7f8bbaa527876efa9b9f1481a3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="processing-notification-messages-in-month-calendar-controls"></a>处理月历控件中的通知消息
用户月历控件 （选择日期和/或查看不同的月份），与控件进行交互 (`CMonthCalCtrl`) 将通知消息发送到其父窗口，通常是视图或对话框对象。 如果您要在响应中做些什么，请处理这些消息。 例如，当用户选择新月份查看，你可以提供一的组应强调的日期。  
  
 请使用“属性”窗口将通知处理程序添加到你希望实现的那些消息的父类。  
  
 以下列表介绍月历控件所发送的各种通知。  
  
-   **MCN_GETDAYSTATE**哪些应以粗体显示天的请求信息。 有关处理此通知的信息，请参阅[设置月历控件的日状态](../mfc/setting-the-day-state-of-a-month-calendar-control.md)。  
  
-   **MCN_SELCHANGE**通知的父文件夹的所选的日期或日期范围已更改。  
  
-   **MCN_SELECT**通知已显式日期选择父级。  
  
## <a name="see-also"></a>请参阅  
 [使用 CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)   
 [控件](../mfc/controls-mfc.md)

