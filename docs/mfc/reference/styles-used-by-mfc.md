---
title: "MFC 使用的样式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.styles"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "按钮, MFC 工具栏"
  - "组合框, 样式"
  - "编辑样式 [MFC]"
  - "扩展的窗口样式"
  - "框架窗口, 样式"
  - "列表框, 样式"
  - "消息框样式"
  - "滚动条样式 [MFC]"
  - "静态样式"
  - "样式"
  - "样式, MFC"
  - "窗口样式, 在 MFC 中"
ms.assetid: d3b9af37-31b5-4c97-a8ad-189fd724b04c
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# MFC 使用的样式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将创建相应的 MFC 对象时，使用以下样式。  在许多情况下，这些样式。类 **创建** 函数的 `dwStyle` 参数设置。  
  
### 样式 MFC  
  
|样式|说明|  
|--------|--------|  
|[按钮样式](../../mfc/reference/button-styles.md)|应用到 [CButton 类](../../mfc/reference/cbutton-class.md) 对象，如单选按钮、复选框和按钮。  指定样式的组合。[CButton::Create](../Topic/CButton::Create.md)`dwStyle` 参数。|  
|[组合框样式](../../mfc/reference/combo-box-styles.md)|应用于对象。[CComboBox 类](../../mfc/reference/ccombobox-class.md) 指定样式的组合。[CComboBox::Create](../Topic/CComboBox::Create.md)`dwStyle` 参数。|  
|[编辑样式](../../mfc/reference/edit-styles.md)|应用于对象。[CEdit 类](../../mfc/reference/cedit-class.md) 指定样式的组合。[CEdit::Create](../Topic/CEdit::Create.md)`dwStyle` 参数。|  
|[框架窗口样式](../../mfc/reference/frame-window-styles-mfc.md)|应用于对象。[CFrameWnd 类](../../mfc/reference/cframewnd-class.md) 指定样式的组合。[CFrameWnd::Create](../Topic/CFrameWnd::Create.md)`dwStyle` 参数。|  
|[列表框样式](../../mfc/reference/list-box-styles.md)|应用于对象。[CListBox 类](../../mfc/reference/clistbox-class.md) 指定样式的组合。[CListBox::Create](../Topic/CListBox::Create.md)`dwStyle` 参数。|  
|[消息框样式](../../mfc/reference/message-box-styles.md)|应用到 [AfxMessageBox](../Topic/AfxMessageBox.md) 项。  指定样式的组合在 `AfxMessageBox``nType` 参数。|  
|[滚动条控件](../../mfc/reference/scroll-bar-styles.md)|应用于对象。[CScrollBar 类](../../mfc/reference/cscrollbar-class.md) 指定样式的组合。[CScrollBar::Create](../Topic/CScrollBar::Create.md)`dwStyle` 参数。|  
|[静态样式](../../mfc/reference/static-styles.md)|应用于对象。[CStatic 类](../../mfc/reference/cstatic-class.md) 指定样式的组合。[CStatic::Create](../Topic/CStatic::Create.md)`dwStyle` 参数。|  
|[窗口样式](../../mfc/reference/window-styles.md)|应用于对象。[CWnd 类](../../mfc/reference/cwnd-class.md) 指定样式的组合。[CWnd::Create](../Topic/CWnd::Create.md)[CWnd::CreateEx](../Topic/CWnd::CreateEx.md)或 `dwStyle` 参数。|  
|[扩展窗口样式](../../mfc/reference/extended-window-styles.md)|应用于对象。[CWnd 类](../../mfc/reference/cwnd-class.md) 指定样式的组合。[CWnd::CreateEx](../Topic/CWnd::CreateEx.md)`dwExStyle` 参数。|  
  
## 请参阅  
 [类概述](../../mfc/class-library-overview.md)