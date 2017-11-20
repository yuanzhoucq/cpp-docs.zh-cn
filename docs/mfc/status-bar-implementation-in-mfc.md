---
title: "MFC 中的状态栏实现 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: COldStatusBar
dev_langs: C++
helpviewer_keywords:
- status bars [MFC], implementing in MFC
- CStatusBarCtrl class [MFC], and MFC status bars
- CStatusBar class [MFC], and CStatusBarCtrl class [MFC]
- CStatusBarCtrl class [MFC], and CStatusBar class [MFC]
- status bars [MFC], backward compatibility
- status bars [MFC], old with COldStatusBar class [MFC]
- COldStatusBar class [MFC]
- status bars [MFC], and CStatusBarCtrl class
- CStatusBar class [MFC], and MFC status bars
- status indicators
- status bars [MFC], Windows 95 implementation
ms.assetid: be5cd876-38e3-4d5c-b8cb-16d57a16a142
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ad340de74193bedbe817f1cd5bb5cc29b3417195
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="status-bar-implementation-in-mfc"></a>MFC 中的状态栏实现
A [CStatusBar](../mfc/reference/cstatusbar-class.md)对象是具有一行文本输出窗格的控件条。 输出窗格通常用作消息行和状态指示器。 示例包括简短解释选定的菜单命令的菜单帮助消息行和指示器显示 SCROLL LOCK、 NUM LOCK 和其他键的状态。  
  
 从 MFC 4.0 版开始，状态栏实现使用类[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)，封装状态栏公共控件。 为了向后兼容，MFC 将保留在类中的较旧状态栏实现**COldStatusBar**。 对于早期版本的 MFC 的文档介绍**COldStatusBar**下`CStatusBar`。  
  
 [CStatusBar::GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl)，成员函数新到 MFC 4.0，使你可以利用的状态栏自定义项和其他功能的 Windows 公共控件的支持。 `CStatusBar`成员函数为您提供的大多数 Windows 公共控件; 功能但是，当调用`GetStatusBarCtrl`，你可让你状态栏甚至多个状态栏的特征。 当调用`GetStatusBarCtrl`，它将返回到引用`CStatusBarCtrl`对象。 你可使用该引用操作状态栏控件。  
  
 下图显示几个指示器的状态栏。  
  
 ![状态栏](../mfc/media/vc37dy1.gif "vc37dy1")  
状态栏  
  
 工具栏上，如状态栏对象中其父框架窗口嵌入，并且构造框架窗口时，会自动构造。 状态栏，如所有控件条，则自动被销毁以及时销毁的父框架。  
  
## <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [更新状态栏窗格的文本](../mfc/updating-the-text-of-a-status-bar-pane.md)  
  
-   MFC 类[CStatusBar](../mfc/reference/cstatusbar-class.md)和[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)  
  
-   [控件条](../mfc/control-bars.md)  
  
-   [对话栏](../mfc/dialog-bars.md)  
  
-   [工具栏 （MFC 工具栏实现）](../mfc/mfc-toolbar-implementation.md)  
  
## <a name="see-also"></a>另请参阅  
 [状态栏](../mfc/status-bars.md)

