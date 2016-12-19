---
title: "Default Control Events | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "Dialog editor, default control events"
  - "controls [C++], default control events"
  - "events [C++], controls"
  - "dialog box controls, events"
ms.assetid: 75556b23-18f5-4390-97a4-2ecad3309741
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Default Control Events
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

以下控件名称具有伴随的默认事件：  
  
|控件名称|默认事件|  
|----------|----------|  
|Animate|**ACN\_START**|  
|Check box|**BN\_CLICKED**|  
|Combo box|**CBN\_SELCHANGE**|  
|自定义|**TTN\_GETDISPINFO**|  
|Date time picker|**DTN\_DATETIMECHANGE**|  
|编辑框|**EN\_CHANGE**|  
|分组框|（不适用）|  
|Hot key|**NM\_OUTOFMEMORY**|  
|IP 地址|**IPN\_FIELDCHANGED**|  
|列表|**LVN\_ITEMCHANGE**|  
|列表框|**LBN\_SELCHANGE**|  
|Month calendar|**MCN\_SELCHANGE**|  
|图片控件|（不适用）|  
|Progress|**NM\_CUSTOMDRAW**|  
|Push button|**BN\_CLICKED**|  
|Radio button|**BN\_CLICKED**|  
|Rich Edit|**EN\_CHANGE**|  
|Scroll bar|**NM\_THEMECHANGED**|  
|Slider|**NM\_CUSTOMDRAW**|  
|Spin|**UDN\_DELTAPOS**|  
|静态文本|（不适用）|  
|Tab|**TCN\_SELCHANGE**|  
|树|**TVN\_SELCHANGE**|  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
## 要求  
 Win32  
  
## 请参阅  
 [Defining Member Variables for Dialog Controls](../mfc/defining-member-variables-for-dialog-controls.md)   
 [与用户界面对象关联的消息类型](../mfc/reference/message-types-associated-with-user-interface-objects.md)   
 [编辑消息处理程序](../mfc/reference/editing-a-message-handler.md)   
 [为反射消息定义消息处理程序](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)   
 [声明基于新控件类的变量](../mfc/reference/declaring-a-variable-based-on-your-new-control-class.md)   
 [重写虚函数](../ide/overriding-a-virtual-function-visual-cpp.md)