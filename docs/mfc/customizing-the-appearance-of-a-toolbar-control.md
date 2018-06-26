---
title: 自定义工具栏控件的外观 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TBSTYLE_
dev_langs:
- C++
helpviewer_keywords:
- flat toolbars
- CToolBar class [MFC], styles
- transparent toolbars
- TBSTYLE_ styles [MFC]
- CToolBarCtrl class [MFC], object styles
- toolbar controls [MFC], style
ms.assetid: fd0a73db-7ad1-4fe4-889b-02c3980f49e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 48825a264b7d82152f47e70c5911bea400c313db
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932112"
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>自定义工具栏控件的外观
类`CToolBarCtrl`提供许多影响外观 （和，有时，行为） 的工具栏对象的样式。 通过设置来修改工具栏对象`dwCtrlStyle`参数`CToolBarCtrl::Create`(或`CToolBar::CreateEx`) 成员函数，首次创建工具栏控件时。  
  
 工具栏按钮的"三维"方面和按钮文本的位置会影响以下样式：  
  
-   **TBSTYLE_FLAT**创建其中工具栏和按钮都是透明一个平面工具栏。 按钮文本显示在按钮位图下。 当使用此样式时，将自动突出显示光标下面的按钮。  
  
-   **TBSTYLE_TRANSPARENT**创建透明工具栏。 在一个透明的工具栏，工具栏是透明但按钮。 按钮文本显示在按钮位图下。  
  
-   **TBSTYLE_LIST**位置按钮右侧的按钮位图的文本。  
  
> [!NOTE]
>  若要避免重新绘制问题**TBSTYLE_FLAT**和**TBSTYLE_TRANSPARENT**工具栏对象可见之前，应设置样式。  
  
 以下样式确定工具栏是否允许用户重新定位在使用拖工具栏对象内的各个按钮，然后放置：  
  
-   **TBSTYLE_ALTDRAG**允许用户通过在按住 ALT 的同时拖动更改工具栏按钮的位置。 如果未指定此样式，用户必须按住 SHIFT 的同时拖动按钮。  
  
    > [!NOTE]
    >  **CCS_ADJUSTABLE**样式必须指定以启用要拖动的工具栏按钮。  
  
-   **TBSTYLE_REGISTERDROP**生成**TBN_GETOBJECT**通知消息来请求删除目标对象，当鼠标指针经过工具栏按钮。  
  
 剩余的样式会影响可视化和非可视方面的工具栏对象：  
  
-   **TBSTYLE_WRAPABLE**创建一个可以有多行的按钮的工具栏。 工具栏按钮可以"包装"到下一行工具栏变得过窄而无法提供同一行上的所有按钮时。 在分离和行会边界上发生换行。  
  
-   **TBSTYLE_CUSTOMERASE**生成**NM_CUSTOMDRAW**通知邮件时它可以处理**WM_ERASEBKGND**消息。  
  
-   **TBSTYLE_TOOLTIPS**创建应用程序可以使用工具栏中显示的按钮的描述性文本的工具提示控件。  
  
 工具栏样式和扩展的样式的完整列表，请参阅[工具栏控件和按钮样式](http://msdn.microsoft.com/library/windows/desktop/bb760439)和[工具栏扩展样式](http://msdn.microsoft.com/library/windows/desktop/bb760430)Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控件](../mfc/controls-mfc.md)

