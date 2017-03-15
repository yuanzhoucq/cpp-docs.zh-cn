---
title: "树控件样式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TVS_SINGLEEXPAND"
  - "TVS_LINESATROOT"
  - "TVS_HASBUTTONS"
  - "TVS_NOTOOLTIPS"
  - "TVS_HASLINES"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTreeCtrl 类, 样式"
  - "样式, CTreeCtrl"
  - "样式, 树控件"
  - "树控件, 样式"
  - "TVS_EDITLABELS"
  - "TVS_HASBUTTONS"
  - "TVS_HASLINES"
  - "TVS_LINESATROOT"
  - "TVS_NOTOOLTIPS"
  - "TVS_SINGLEEXPAND"
ms.assetid: f43faebd-a355-479e-888a-bf0673d5e1b4
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 树控件样式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

树控件 \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) 样式管理树的控件外观方面。  将初始样式，当创建树控件。  使用 [GetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633584) 和 [SetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633591) Windows 函数，则可以在创建树控件以后检索和更改样式，**GWL\_STYLE** 指定为 `nIndex` 参数。  有关样式的完整列表，请参阅《[!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]的 [树视图控件窗口样式](http://msdn.microsoft.com/library/windows/desktop/bb760013)。  
  
 **TVS\_HASLINES** 通过样式绘制子链接到相应的父项的线条引发树控件级别的图形表示形式。  此样式不链接项层次结构的根。  为此，需要将 **TVS\_HASLINES** 和 **TVS\_LINESATROOT**。样式  
  
 用户可以双击父项展开或折叠子项父项的列表。  **TVS\_SINGLEEXPAND** 具有样式的树控件生成选定的项展开和是的项未选定的折叠。  如果鼠标使用对单击选定的项，则该项关闭，将展开。  如果选择的项单击时，它将打开，则它折叠。  
  
 **TVS\_HASBUTTONS** 具有样式的树控件添加一个按钮。每个父项的左侧。  用户可单击按钮展开或折叠子项来双击父项。  **TVS\_HASBUTTONS** 未添加按钮。项层次结构的根。  为此，必须将 **TVS\_HASLINES**、**TVS\_LINESATROOT**和 **TVS\_HASBUTTONS**。  
  
 **TVS\_EDITLABELS** 样式使用户能够编辑标签控件树项。  有关编辑标签的更多信息，请参见 [树控件编辑标签](../mfc/tree-control-label-editing.md) 本主题后。  
  
 **TVS\_NOTOOLTIPS** 样式禁用树视图控件的自动工具提示功能。  如果标题整个当前不可见，此功能会自动显示工具提示，其中包含项的标题在鼠标光标之下。  
  
## 请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)