---
title: "更改列表控件样式 | Microsoft Docs"
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
helpviewer_keywords: 
  - "CListCtrl 类, 更改样式"
  - "CListCtrl 类, 样式"
  - "样式, CListCtrl"
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 更改列表控件样式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以随时更改列表控件 \([CListCtrl](../mfc/reference/clistctrl-class.md)\) 的窗口样式，在创建集合后。  通过将窗口样式，您更改控件的该视图。  例如，放置 Explorer，可能提供菜单项或工具栏按钮切换的控件不同视图之间切换：图标视图，列表视图，依此类推。  
  
 例如，在中，当用户选择菜单项时，您可能调用 [GetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633584) 检索控件的当前样式然后调用 [SetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633591) 重置样式。  有关更多信息，请参见" [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [使用列表视图控件](http://msdn.microsoft.com/library/windows/desktop/bb774736)。  
  
 可用样式在 [创建](../Topic/CListCtrl::Create.md)列出。  样式 `LVS_ICON`、`LVS_SMALLICON`、`LVS_LIST`和 `LVS_REPORT` 指定四个列表视图控件。  
  
## 扩展样式  
 除了列表控件的标准样式外，具有另一组，称为"扩展的样式。  这些样式，讨论在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [扩展的列表视图样式](http://msdn.microsoft.com/library/windows/desktop/bb774732)，列表控件提供自定义行为的各种有用的功能。  若要实现某些样式的悬停行为 \(如选择\)，请调用 [CListCtrl::SetExtendedStyle](../Topic/CListCtrl::SetExtendedStyle.md)，通过所需的样式。  下面的示例演示函数调用：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/CPP/changing-list-control-styles_1.cpp)]  
  
> [!NOTE]
>  对于使用的悬停选择，您还必须有 **LVS\_EX\_ONECLICKACTIVATE** 或 **LVS\_EX\_TWOCLICKACTIVATE** 打开。  
  
## 请参阅  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控件](../mfc/controls-mfc.md)