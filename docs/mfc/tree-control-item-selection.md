---
title: "树控件项选择 | Microsoft Docs"
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
  - "控件 [MFC], 选择其中的项"
  - "CTreeCtrl 类, 项选择"
  - "树控件中的项选择"
  - "树控件, 项选择"
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 树控件项选择
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当从中选择一项更改为另一个架构时，树控件 \(\) 和 [TVN\_SELCHANGED](http://msdn.microsoft.com/library/windows/desktop/bb773544) [TVN\_SELCHANGING](http://msdn.microsoft.com/library/windows/desktop/bb773547)[CTreeCtrl](../mfc/reference/ctreectrl-class.md)发送通知消息。  包括两通知指定的值更改是否是鼠标单击或按键的结果。  有关获取和失去选择项选择的包含或通知信息。  您可以使用此信息将取决于项的选择状态项的特征。  返回根据 **TVN\_SELCHANGING** 的 **TRUE** 防止更改的选项；返回 **FALSE** 允许更改。  
  
 应用程序可以通过调用 [SelectItem](../Topic/CTreeCtrl::SelectItem.md) 成员函数会更改选择。  
  
## 请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)