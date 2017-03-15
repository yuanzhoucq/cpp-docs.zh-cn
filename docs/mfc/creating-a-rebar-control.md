---
title: "创建 Rebar 控件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CReBarCtrl 类, 创建"
  - "rebar 控件, 创建"
ms.assetid: 0a012e08-772b-4f6a-af86-7cb651d11d3e
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 创建 Rebar 控件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CReBarCtrl](../mfc/reference/crebarctrl-class.md) 对象，然后父对象是可见之前，应创建。  这会尽量绘制问题的可能性。  
  
 例如，rebar 控件 \(在框架窗口对象\) 通常用作工具栏控件的父窗口。  因此，rebar 控件的父窗口是框架对象。  因为框架窗口对象是父，`OnCreate` 成员函数 \(父\) 是创建 rebar 控件的极好的位置。  
  
 为了使用 `CReBarCtrl` 对象，您通常执行以下步骤：  
  
### 使用 CReBarCtrl 对象  
  
1.  构造记录集[CReBarCtrl](../mfc/reference/crebarctrl-class.md)对象。  
  
2.  调用 [创建](../Topic/CReBarCtrl::Create.md) 创建 Windows 公共控件和 rebar 附加到 `CReBarCtrl` 对象，指定所有需要的样式。  
  
3.  用与 [CBitmap::LoadBitmap](../Topic/CBitmap::LoadBitmap.md)的调用将加载一个位图，rebar 控件，用作对象的背景。  
  
4.  创建并初始化由 rebar 控件包含对象的所有子窗口对象 \(工具栏，对话框控件，等等\)。  
  
5.  初始化了必要的信息的 **REBARBANDINFO** 结构有将插入。  
  
6.  调用 [InsertBand](../Topic/CReBarCtrl::InsertBand.md) 插入现有的子窗口 \(如 `m_wndReToolBar`\) 为 rebar 新的控件。  有关 PIA 的更多信息结合到现有 rebar 控件，请参见 [Rebar 和带区控件](../mfc/rebar-controls-and-bands.md)。  
  
## 请参阅  
 [使用 CReBarCtrl](../mfc/using-crebarctrl.md)   
 [控件](../mfc/controls-mfc.md)