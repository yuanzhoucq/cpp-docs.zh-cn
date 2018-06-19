---
title: 更改列表控件样式 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- styles [MFC], CListCtrl
- CListCtrl class [MFC], styles
- CListCtrl class [MFC], changing styles
ms.assetid: be74a005-0795-417c-9056-f6342aa74b26
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9d93511ad4f4ca835e09b6eaa3f612f0888e844
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344837"
---
# <a name="changing-list-control-styles"></a>更改列表控件样式
你可以更改列表控件的窗口样式 ([CListCtrl](../mfc/reference/clistctrl-class.md)) 在任何时间在创建之后。 通过更改窗口样式，可以更改该控件使用的视图的类型。 例如，若要模拟资源管理器，可能会提供菜单项或工具栏按钮以切换不同的视图之间的控件： 图标视图、 列表视图中，依次类推。  
  
 例如，当用户选择菜单项，你可以进行调用[GetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633584)若要检索的控件的当前样式，然后调用[SetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633591)重置样式。 有关详细信息，请参阅[使用列表视图控件](http://msdn.microsoft.com/library/windows/desktop/bb774736)Windows SDK 中。  
  
 中列出了可用样式[创建](../mfc/reference/clistctrl-class.md#create)。 样式`LVS_ICON`， `LVS_SMALLICON`， `LVS_LIST`，和`LVS_REPORT`指定四个列表控件视图。  
  
## <a name="extended-styles"></a>扩展的样式  
 除了列表控件的标准样式，还有另一个组，称为扩展样式。 这些样式中, 所述[扩展列表视图样式](http://msdn.microsoft.com/library/windows/desktop/bb774732)在 Windows SDK 中，提供了各种各样的自定义列表控件的行为的有用功能。 若要实现的行为的某些样式 （如悬停时选择），请调用[CListCtrl::SetExtendedStyle](../mfc/reference/clistctrl-class.md#setextendedstyle)，传递所需的样式。 下面的示例演示了函数调用：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#22](../mfc/codesnippet/cpp/changing-list-control-styles_1.cpp)]  
  
> [!NOTE]
>  悬停时选择工作，你必须还具有**LVS_EX_ONECLICKACTIVATE**或**LVS_EX_TWOCLICKACTIVATE**开启。  
  
## <a name="see-also"></a>请参阅  
 [使用 CListCtrl](../mfc/using-clistctrl.md)   
 [控件](../mfc/controls-mfc.md)

