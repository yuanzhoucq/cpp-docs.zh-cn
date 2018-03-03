---
title: "树控件样式 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c141a2b0db673f8d3c5f2c116de5b5d2ec81a8ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="tree-control-styles"></a>树控件样式
树控件 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 样式控制方面的树控件的外观。 创建树控件时，你可以设置的初始样式。 可以检索，还可以通过使用创建树控件后更改样式[GetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633584)和[SetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633591) Windows 函数，指定**GWL_STYLE**为`nIndex`参数。 样式的完整列表，请参阅[树视图控件的窗口样式](http://msdn.microsoft.com/library/windows/desktop/bb760013)Windows SDK 中。  
  
 **TVS_HASLINES**样式通过绘制将子项链接到其相应的父项的线条增强的图形表示形式树控件的层次结构。 此样式不链接层次结构的根处的项。 若要执行此操作，你需要合并**TVS_HASLINES**和**TVS_LINESATROOT**样式。  
  
 用户可以展开或折叠父项的子项列表，通过双击父项。 树控件具有**TVS_SINGLEEXPAND**样式会导致正在选定以展开的项和正在取消折叠的项。 如果用鼠标单击选定的项并关闭该项目，它将展开。 如果所选的项目用鼠标单击打开时，它将会自动折叠。  
  
 树控件具有**TVS_HASBUTTONS**样式将按钮添加到每个父项的左侧。 用户可以单击按钮以展开或折叠子项作为双击父项的替代方法。 **TVS_HASBUTTONS**不将按钮添加到层次结构的根处的项。 若要执行此操作，必须组合**TVS_HASLINES**， **TVS_LINESATROOT**，和**TVS_HASBUTTONS**。  
  
 **TVS_EDITLABELS**样式，使用户可以编辑树控件项标签。 有关编辑标签的详细信息，请参阅[树控件标签编辑](../mfc/tree-control-label-editing.md)本主题中更高版本。  
  
 **TVS_NOTOOLTIPS**样式禁用树视图控件的自动工具提示功能。 此功能会自动显示工具提示，如果整个标题不是当前可见包含鼠标光标下的项的标题。  
  
## <a name="see-also"></a>请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)

