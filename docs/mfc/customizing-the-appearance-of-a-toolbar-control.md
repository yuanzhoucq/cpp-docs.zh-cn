---
title: "自定义工具栏控件的外观 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TBSTYLE_"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CToolBar 类, 样式"
  - "CToolBarCtrl 类, 对象样式"
  - "平面工具栏"
  - "TBSTYLE_ 样式"
  - "工具栏控件 [MFC], 样式"
  - "透明工具栏"
ms.assetid: fd0a73db-7ad1-4fe4-889b-02c3980f49e8
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 自定义工具栏控件的外观
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

类 `CToolBarCtrl` 提供许多影响外观的样式 \(，并偶尔，行为\) 工具栏对象。  通过设置 `CToolBarCtrl::Create` 或 `CToolBar::CreateEx`\) 成员函数的 `dwCtrlStyle` 参数修改工具栏对象，那么，当首次创建工具栏控件时。  
  
 工具栏按钮的“三维”影响以下样式特性以及该文本的位置：  
  
-   **TBSTYLE\_FLAT** 创建工具栏按钮和透明的平缓工具栏。  按钮文本在按钮位图。下。  当使用时，此样式将光标下的按钮自动突出显示。  
  
-   **TBSTYLE\_TRANSPARENT** 创建透明工具栏。  在的工具栏透明，但透明，工具栏按钮不是。  按钮文本在按钮位图。下。  
  
-   **TBSTYLE\_LIST** 使在位图按钮右侧按文本。  
  
> [!NOTE]
>  为了避免中重绘问题，**TBSTYLE\_FLAT**，并应将 **TBSTYLE\_TRANSPARENT** 设置样式，在工具栏对象是可见的。  
  
 下面的样式确定工具栏使用拖放，是否允许用户重新定位在工具栏对象中的各个按钮：  
  
-   **TBSTYLE\_ALTDRAG** 允许用户通过将该更改工具栏按钮的位置，在按住 Alt 时。  如果不指定此样式，用户按住 Shift，必须在拖动按钮时。  
  
    > [!NOTE]
    >  必须指定 `CCS_ADJUSTABLE` 允许拖动样式的工具栏按钮。  
  
-   当鼠标指针传递此工具栏按钮时，**TBSTYLE\_REGISTERDROP** 生成 **TBN\_GETOBJECT** 通知消息请求放置目标对象。  
  
 剩余的可视影响样式，然后工具栏的非可视对象的特性：  
  
-   创建`TBSTYLE_WRAPABLE` 可以具有多行按钮的工具栏。  当工具栏，变得太窄到包括在同一行时，中所有按钮的工具栏按钮可以通过“包装都可以过度”到下一行。  分隔并包装在 nongroup 边界发生。  
  
-   当其处理 `WM_ERASEBKGND` 消息时，**TBSTYLE\_CUSTOMERASE** 生成 **NM\_CUSTOMDRAW** 通知消息。  
  
-   `TBSTYLE_TOOLTIPS` 创建应用程序可用显示按钮的描述性文字在工具栏的工具提示控件。  
  
 有关和工具栏样式扩展样式完整列表，请参见 [控件和工具栏按钮样式](http://msdn.microsoft.com/library/windows/desktop/bb760439)[工具栏扩展样式](http://msdn.microsoft.com/library/windows/desktop/bb760430) 和 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]中。  
  
## 请参阅  
 [使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [控件](../mfc/controls-mfc.md)