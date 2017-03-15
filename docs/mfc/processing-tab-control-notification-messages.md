---
title: "处理选项卡控件通知消息 | Microsoft Docs"
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
  - "CTabCtrl 类, 处理通知"
  - "通知, 在 CTabCtrl 中处理"
  - "通知, 选项卡控件"
  - "处理通知"
  - "选项卡控件, 处理通知"
ms.assetid: 758ccb7a-9e73-48f8-9073-23f7cb09918c
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 处理选项卡控件通知消息
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

因为用户单击选项卡或按钮，选项卡控件 \([CTabCtrl](../mfc/reference/ctabctrl-class.md)\) 发送通知消息到它的父窗口。  如果您要在响应中做些什么，处理这些消息。  例如，如果用户单击该选项卡，您可能需要在显示它之前预设页上控件的数据。  
  
 从消息视图或在对话框类的选项卡控件处理 **WM\_NOTIFY** 。  使用属性窗口 创建[OnChildNotify](../Topic/CWnd::OnChildNotify.md)处理基于要处理的通知消息。  有关选项卡控件可以发送到它的父窗口的通知的列表，请参见 [选项卡控件引用](http://msdn.microsoft.com/library/windows/desktop/bb760548) 的 **通知** 部分在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]中。  
  
## 请参阅  
 [使用 CTabCtrl](../mfc/using-ctabctrl.md)   
 [控件](../mfc/controls-mfc.md)