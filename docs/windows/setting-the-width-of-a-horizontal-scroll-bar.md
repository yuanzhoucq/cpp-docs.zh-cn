---
title: "Setting the Width of a Horizontal Scroll Bar | Microsoft Docs"
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
  - "list controls, scroll bar width"
  - "CListBox::SetHorizontalExtent"
  - "controls [C++], scroll bar"
  - "scroll bars, displaying in controls"
  - "horizontal scroll bar width"
  - "CListBox class, scroll bar width"
  - "scroll bars, width"
ms.assetid: 51dad141-aa0b-46a3-a82c-46b80d603d94
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Setting the Width of a Horizontal Scroll Bar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当使用 MFC 类将带水平滚动条的列表框添加到对话框时，滚动条不自动出现在应用程序中。  
  
### 使滚动条出现  
  
1.  在代码中调用 [CListBox::SetHorizontalExtent](../Topic/CListBox::SetHorizontalExtent.md) 以设置最宽元素的最大宽度。  
  
     如果不设置此值，那么即使列表框中的项比列表框宽，滚动条也不会出现。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 要求  
  
 MFC  
  
## 请参阅  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [控件](../mfc/controls-mfc.md)