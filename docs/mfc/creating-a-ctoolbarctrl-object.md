---
title: 创建 CToolBarCtrl 对象 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CToolBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c5e2ee8c0e2239de86252b3d0fb8ec0ab7cc182
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="creating-a-ctoolbarctrl-object"></a>创建 CToolBarCtrl 对象
[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)对象包含多个内部数据结构-按钮图像位图的列表、 按钮标签字符串的列表和列表`TBBUTTON`结构 — 也就是说将一个图像关联和/或带有位置、 样式、 状态、 字符串和命令 ID 的按钮。 每个这些数据结构的元素被由从零开始的索引。 你可以使用之前`CToolBarCtrl`对象，则必须将这些数据结构设置。 数据结构的列表，请参阅[工具栏控件](controls-mfc.md)Windows SDK 中。 字符串的列表可以仅用于按钮标签;从工具栏中，无法检索字符串。  
  
 为了使用 `CToolBarCtrl` 对象，您通常将执行下列步骤：  
  
### <a name="to-use-a-ctoolbarctrl-object"></a>使用 CToolBarCtrl 对象  
  
1.  构造[CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)对象。  
  
2.  调用[创建](../mfc/reference/ctoolbarctrl-class.md#create)创建 Windows 工具栏公共控件并将其附加到`CToolBarCtrl`对象。 如果你想位图图像的按钮，添加按钮位图到工具栏通过调用[AddBitmap](../mfc/reference/ctoolbarctrl-class.md#addbitmap)。 如果你需要字符串标签按钮，将字符串添加到工具栏通过调用[AddString](../mfc/reference/ctoolbarctrl-class.md#addstring)和/或[AddStrings](../mfc/reference/ctoolbarctrl-class.md#addstrings)。 在调用`AddString`和/或`AddStrings`，应调用[AutoSize](../mfc/reference/ctoolbarctrl-class.md#autosize)以获取字符串或字符串以显示。  
  
3.  将按钮结构添加到工具栏，通过调用[AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons)。  
  
4.  如果你想工具提示，处理**TTN_NEEDTEXT**文件中的邮件工具栏的所有者窗口中所述[处理工具提示通知](../mfc/handling-tool-tip-notifications.md)。  
  
5.  如果你想让用户能够自定义工具栏，处理是所有者窗口中的自定义通知消息中所述[处理自定义通知](../mfc/handling-customization-notifications.md)。  
  
## <a name="see-also"></a>请参阅  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控件](../mfc/controls-mfc.md)

