---
title: "使用工具栏控件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- GetToolBarCtrl method [MFC]
- toolbars [MFC], accessing common control
- CToolBarCtrl class [MFC], accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 475b44b856c874064a4ccbdaf7b648342eb9c657
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="working-with-the-toolbar-control"></a>使用工具栏控件
此文章介绍了如何访问[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)对象基础[CToolBar](../mfc/reference/ctoolbar-class.md)更好地控制您的工具栏。 这是一个高级的主题。  
  
## <a name="procedures"></a>过程  
  
#### <a name="to-access-the-toolbar-common-control-underlying-your-ctoolbar-object"></a>若要访问基础 CToolBar 对象工具栏公共控件  
  
1.  调用[CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl)。  
  
 `GetToolBarCtrl`返回的引用[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)对象。 你可以使用该引用调用工具栏控件类的成员函数。  
  
> [!CAUTION]
>  虽然通过调用`CToolBarCtrl`**获取**函数是安全的如果调用要格外小心**设置**函数。 这是一个高级的主题。 通常情况下则不需要访问基础工具栏控件。  
  
### <a name="what-do-you-want-to-know-more-about"></a>你想进一步了解什么  
  
-   [控件 （Windows 公共控件）](../mfc/controls-mfc.md)  
  
-   [工具栏基础知识](../mfc/toolbar-fundamentals.md)  
  
-   [停靠和浮动工具栏](../mfc/docking-and-floating-toolbars.md)  
  
-   [动态调整大小工具栏](../mfc/docking-and-floating-toolbars.md)  
  
-   [工具栏工具提示](../mfc/toolbar-tool-tips.md)  
  
-   [越过状态栏更新](../mfc/toolbar-tool-tips.md)  
  
-   [处理工具提示通知](../mfc/handling-tool-tip-notifications.md)  
  
-   [CToolBar](../mfc/reference/ctoolbar-class.md)和[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)类  
  
-   [处理自定义通知](../mfc/handling-customization-notifications.md)  
  
-   [多个工具栏](../mfc/toolbar-fundamentals.md)  
  
-   [使用您的旧工具栏](../mfc/using-your-old-toolbars.md)  
  
-   [控件条](../mfc/control-bars.md)  
  
 有关使用 Windows 公共控件的常规信息，请参阅[公共控件](http://msdn.microsoft.com/library/windows/desktop/bb775493)。  
  
## <a name="see-also"></a>请参阅  
 [MFC 工具栏实现](../mfc/mfc-toolbar-implementation.md)

