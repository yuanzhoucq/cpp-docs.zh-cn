---
title: "CStatusBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CStatusBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStatusBar class"
  - "indicators"
  - "indicators, status bar"
  - "状态栏"
  - "status indicators"
ms.assetid: a3bde3db-e71c-4881-a3ca-1d5481c345ba
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CStatusBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

与文本输出窗格或“指示符行的控件条”。  
  
## 语法  
  
```  
class CStatusBar : public CControlBar  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CStatusBar::CStatusBar](../Topic/CStatusBar::CStatusBar.md)|构造 `CStatusBar` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CStatusBar::CommandToIndex](../Topic/CStatusBar::CommandToIndex.md)|获取给定指示符ID.的索引|  
|[CStatusBar::Create](../Topic/CStatusBar::Create.md)|创建状态栏，附加到 `CStatusBar` 对象，并将初始字体和条高度。|  
|[CStatusBar::CreateEx](../Topic/CStatusBar::CreateEx.md)|使用嵌入 `CStatusBarCtrl` 对象的附加样式创建一 `CStatusBar` 对象。|  
|[CStatusBar::DrawItem](../Topic/CStatusBar::DrawItem.md)|调用，当所有者描述状态栏控件中的可视方面是。|  
|[CStatusBar::GetItemID](../Topic/CStatusBar::GetItemID.md)|获取给定索引的指示符ID。|  
|[CStatusBar::GetItemRect](../Topic/CStatusBar::GetItemRect.md)|获取给定索引的显示矩形。|  
|[CStatusBar::GetPaneInfo](../Topic/CStatusBar::GetPaneInfo.md)|获取指示ID、样式和宽度给定索引处开始的。|  
|[CStatusBar::GetPaneStyle](../Topic/CStatusBar::GetPaneStyle.md)|获取给定索引的指示符样式。|  
|[CStatusBar::GetPaneText](../Topic/CStatusBar::GetPaneText.md)|获取给定索引的指示符文本。|  
|[CStatusBar::GetStatusBarCtrl](../Topic/CStatusBar::GetStatusBarCtrl.md)|允许直接访问基础公共控件。|  
|[CStatusBar::SetIndicators](../Topic/CStatusBar::SetIndicators.md)|设置指示符ID。|  
|[CStatusBar::SetPaneInfo](../Topic/CStatusBar::SetPaneInfo.md)|设置指示符ID、样式和宽度给定索引处开始的。|  
|[CStatusBar::SetPaneStyle](../Topic/CStatusBar::SetPaneStyle.md)|为特定的索引的指示符样式。|  
|[CStatusBar::SetPaneText](../Topic/CStatusBar::SetPaneText.md)|为特定的索引的指示符文本。|  
  
## 备注  
 输出窗格通常用作消息行并将状态指示。  示例包括简要说明选定的菜单命令和指示器scroll lock、num LOCK和其他键的状态的菜单帮助消息行。  
  
 [CStatusBar::GetStatusBarCtrl](../Topic/CStatusBar::GetStatusBarCtrl.md)，成员函数新MFC 4.0，使您可以利用公共控件为状态栏自定义项和附加功能以支持的Windows。  `CStatusBar` 成员函数最提供了Windows公共控件的功能;但是，那么，当您调用 `GetStatusBarCtrl`时，可以为状态栏Windows 95的特性\/98状态栏。  当您调用 `GetStatusBarCtrl`，它将返回对 `CStatusBarCtrl` 对象。  使用Windows公共控件，请参见 [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) 有关设计工具栏的更多信息。  有关公共控件的信息，请参见 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [公共控件](http://msdn.microsoft.com/library/windows/desktop/bb775493)。  
  
 框架在具有最左侧的指示符的数组存储指示符信息在位置0。  当您创建状态栏时，您使用数组框架与对应的指示的字符串ID。  然后可以使用字符串ID或索引访问指示符。  
  
 默认情况下，第一个指示符为“弹性”:其占据其他指示符窗格未使用的状态栏长度，因此，其他窗格是右对齐的。  
  
 若要创建状态栏，请执行以下步骤:  
  
1.  构造 `CStatusBar` 对象。  
  
2.  调用 [创建](../Topic/CStatusBar::Create.md) \(或 [CreateEx](../Topic/CStatusBar::CreateEx.md)\)函数创建状态栏窗口并将其附加到 `CStatusBar` 对象。  
  
3.  调用 [SetIndicators](../Topic/CStatusBar::SetIndicators.md) 关联字符串ID与每个指示符。  
  
 可通过三种方式更新在状态栏窗格的文本:  
  
1.  调用 [CWnd::SetWindowText](../Topic/CWnd::SetWindowText.md) 仅更新在窗格0 "的文本。  
  
2.  调用在状态栏中 `ON_UPDATE_COMMAND_UI` 处理程序的 [CCmdUI::SetText](../Topic/CCmdUI::SetText.md)。  
  
3.  调用 [SetPaneText](../Topic/CStatusBar::SetPaneText.md) 更新所有窗格的文本。  
  
 调用 [SetPaneStyle](../Topic/CStatusBar::SetPaneStyle.md) 更新状态栏窗格的样式。  
  
 有关使用 `CStatusBar`的更多信息，请参见文章 [MFC中的状态栏实现](../../mfc/status-bar-implementation-in-mfc.md) 和 [技术说明31:控制条](../../mfc/tn031-control-bars.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CStatusBar`  
  
## 要求  
 **Header:** afxext.h  
  
## 请参阅  
 [MFC示例CTRLBARS](../../top/visual-cpp-samples.md)   
 [MFC DLGCBR32示例](../../top/visual-cpp-samples.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CStatusBarCtrl Class](../../mfc/reference/cstatusbarctrl-class.md)   
 [CControlBar Class](../../mfc/reference/ccontrolbar-class.md)   
 [CWnd::SetWindowText](../Topic/CWnd::SetWindowText.md)   
 [CStatusBar::SetIndicators](../Topic/CStatusBar::SetIndicators.md)