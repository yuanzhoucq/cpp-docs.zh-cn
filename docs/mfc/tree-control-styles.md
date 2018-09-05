---
title: 树控件样式 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TVS_SINGLEEXPAND
- TVS_LINESATROOT
- TVS_HASBUTTONS
- TVS_NOTOOLTIPS
- TVS_HASLINES
dev_langs:
- C++
helpviewer_keywords:
- TVS_LINESATROOT [MFC]
- styles [MFC], CTreeCtrl
- styles [MFC], tree control
- TVS_HASLINES
- TVS_SINGLEEXPAND
- CTreeCtrl class [MFC], styles
- TVS_EDITLABELS [MFC]
- TVS_NOTOOLTIPS [MFC]
- TVS_HASBUTTONS [MFC]
- tree controls [MFC], styles
ms.assetid: f43faebd-a355-479e-888a-bf0673d5e1b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b6f3f28bbc2a69a5ad5c4fe9910d8312b236c34f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43686493"
---
# <a name="tree-control-styles"></a>树控件样式
树控件 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 样式可以控制以下方面的树控件的外观。 创建树控件时，设置初始样式。 您可以检索和创建使用树控件后更改样式[GetWindowLong](/windows/desktop/api/winuser/nf-winuser-getwindowlonga)并[SetWindowLong](/windows/desktop/api/winuser/nf-winuser-setwindowlonga) Windows 函数，指定**GWL_STYLE**为*nIndex*参数。 有关样式的完整列表，请参阅[树视图控件的窗口样式](/windows/desktop/Controls/tree-view-control-window-styles)Windows SDK 中。  
  
 **TVS_HASLINES**样式绘制链接到其相应的父项的子项的行，从而增强了树控件的层次结构的图形表示形式。 此样式不会链接层次结构的根处的项。 若要执行此操作，你需要合并**TVS_HASLINES**并**TVS_LINESATROOT**样式。  
  
 用户可以展开或折叠通过双击父项的父项的子项列表。 树控件具有**TVS_SINGLEEXPAND**样式会导致以展开所选定的项和正在取消选择折叠项。 如果使用鼠标单击所的选项并关闭该项目，它将展开。 如果所选的项用鼠标单击打开时，它将折叠状态。  
  
 树控件具有**TVS_HASBUTTONS**样式将按钮添加到左侧和右侧的每个父项。 用户可以单击按钮以展开或折叠子项目作为双击父项的替代方法。 **TVS_HASBUTTONS**不会将按钮添加到层次结构的根处的项。 若要执行此操作，必须组合**TVS_HASLINES**， **TVS_LINESATROOT**，并**TVS_HASBUTTONS**。  
  
 **TVS_EDITLABELS**样式，使用户可以编辑树控件项的标签。 有关编辑标签的详细信息，请参阅[树控件标签编辑](../mfc/tree-control-label-editing.md)本主题中更高版本。  
  
 **TVS_NOTOOLTIPS**样式可禁用自动工具提示功能的树视图控件。 此功能将自动显示工具提示，其中包含鼠标光标下的项的标题，如果整个标题不是当前可见。  
  
## <a name="see-also"></a>请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)

