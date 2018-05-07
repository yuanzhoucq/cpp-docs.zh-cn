---
title: 使用工具栏控件中的下拉按钮 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TBN_DROPDOWN
- TBSTYLE_EX_DRAWDDARROWS
dev_langs:
- C++
helpviewer_keywords:
- CToolBarCtrl class [MFC], drop-down buttons
- toolbars [MFC], drop-down buttons
- drop-down buttons in toolbars
- TBSTYLE_EX_DRAWDDARROWS
- TBN_DROPDOWN notification [MFC]
ms.assetid: b859f758-d2f6-40d9-9c26-0ff61993b9b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 39edda143e28d262e8eea826ced5c24855fb310b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="using-drop-down-buttons-in-a-toolbar-control"></a>使用工具栏控件中的下拉按钮
除了标准下压按钮，工具栏也可以有下拉按钮。 下拉按钮通常由存在附加下箭头指示。  
  
> [!NOTE]
>  才会显示附加下箭头`TBSTYLE_EX_DRAWDDARROWS`已设置扩展的样式。  
  
 当用户单击此箭头 （或本身，如果存在则没有箭头的按钮），`TBN_DROPDOWN`通知消息发送到工具栏控件的父级。 然后可以处理此通知，并显示一个弹出菜单;类似于 Internet Explorer 的行为。  
  
 以下过程演示如何实现一个弹出菜单的下拉工具栏按钮：  
  
### <a name="to-implement-a-drop-down-button"></a>若要实现下拉按钮  
  
1.  一次你`CToolBarCtrl`创建对象，设置`TBSTYLE_EX_DRAWDDARROWS`样式，使用下面的代码：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]  
  
2.  设置`TBSTYLE_DROPDOWN`样式任何新 ([InsertButton](../mfc/reference/ctoolbarctrl-class.md#insertbutton)或[AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons)) 或现有 ([SetButtonInfo](../mfc/reference/ctoolbarctrl-class.md#setbuttoninfo)) 将下拉列表按钮的按钮。 下面的示例演示修改中的现有按钮`CToolBarCtrl`对象：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]  
  
3.  添加`TBN_DROPDOWN`到工具栏对象的父类的处理程序。  
  
     [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]  
  
4.  在新的处理中，显示相应的弹出菜单。 下面的代码演示一种方法：  
  
     [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控件](../mfc/controls-mfc.md)

