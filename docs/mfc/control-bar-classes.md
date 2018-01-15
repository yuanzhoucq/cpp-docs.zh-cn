---
title: "控件条类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.control
dev_langs: C++
helpviewer_keywords: control bars [MFC], classes
ms.assetid: 11009103-cad8-4309-85ce-3d2e858e1818
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 44fcecbf1d7ddb6c46469f25349d972c8b317809
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="control-bar-classes"></a>控件条类
控件条附加到框架窗口中。 它们包含按钮、 状态窗格或对话框模板。 自由浮动控件条，也称为工具调色板，实现通过附加到[CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md)对象。  
  
## <a name="framework-control-bars"></a>Framework 控件条  
 这些控件条是 MFC 框架的必要组成部分。 它们是易于使用且不是 Windows 控件条，因为它们集成在一起框架功能更强大。 大多数 MFC 应用程序使用这些控件条，而不是 Windows 控件条。  
  
 [CControlBar](../mfc/reference/ccontrolbar-class.md)  
 本部分中列出的 MFC 控件条的基类。 控件条是窗口框架窗口的边缘对齐。 控件条包含以下任一`HWND`-基于子控件或控件不基于`HWND`，如工具栏按钮。  
  
 [CDialogBar](../mfc/reference/cdialogbar-class.md)  
 基于对话框模板控件条。  
  
 [CReBar](../mfc/reference/crebar-class.md)  
 支持可以包含在控件的窗体中的其他子窗口的工具栏。  
  
 [CToolBar](../mfc/reference/ctoolbar-class.md)  
 不包含位图命令按钮的工具栏控件窗口基于`HWND`。 大多数 MFC 应用程序使用此类而不是`CToolBarCtrl`。  
  
 [CStatusBar](../mfc/reference/cstatusbar-class.md)  
 状态栏控件窗口的基类。 大多数 MFC 应用程序使用此类而不是`CStatusBarCtrl`。  
  
## <a name="windows-control-bars"></a>Windows 控件条  
 这些控件条是相应的 Windows 控件的精简包装。 由于未集成到框架，它们是更难比前面所列的控件条。 大多数 MFC 应用程序使用前面所列的控件条。  
  
 [CRebarCtrl](../mfc/reference/crebarctrl-class.md)  
 实现的内部控件`CRebar`对象。  
  
 [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)  
 水平窗口中，通常分为的窗格，应用程序可在其中显示状态信息。  
  
 [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)  
 提供 Windows 工具栏公共控件的功能。  
  
## <a name="related-classes"></a>相关的类  
 [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)  
 显示的文本来描述应用程序中工具用途的单行一个小型弹出窗口。  
  
 [CDockState](../mfc/reference/cdockstate-class.md)  
 处理停靠控件条的状态数据的持久性存储的区。  
  
## <a name="see-also"></a>请参阅  
 [类概述](../mfc/class-library-overview.md)

