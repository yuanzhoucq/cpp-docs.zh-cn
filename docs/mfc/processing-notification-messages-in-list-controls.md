---
title: "处理列表控件中的通知消息 | Microsoft Docs"
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
  - "CListCtrl 类, 处理通知"
  - "处理通知"
ms.assetid: 1f0e296e-d2a3-48fc-ae38-51d7fb096f51
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 处理列表控件中的通知消息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

用户单击列标头，请拖动图标，编辑标签，依此类推，列表控件 \([CListCtrl](../mfc/reference/clistctrl-class.md)\) 发送通知消息到它的父窗口。  如果您要在响应中做些什么，处理这些消息。  例如，在中，当用户单击列标头时，您可能要根据列的内容排序单击的项，在 Microsoft Outlook。  
  
 从消息视图或在对话框类的选项卡控件处理 **WM\_NOTIFY** 。  使用属性窗口 创建[OnChildNotify](../Topic/CWnd::OnChildNotify.md)处理基于要处理的通知消息。  
  
 有关列表控件可以发送到它的父窗口的通知的列表，请参阅《[!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [列表视图控件引用](http://msdn.microsoft.com/library/windows/desktop/bb774737)。  
  
## 请参阅  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控件](../mfc/controls-mfc.md)