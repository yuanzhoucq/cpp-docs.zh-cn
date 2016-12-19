---
title: "CMFCPopupMenuBar 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCPopupMenuBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCPopupMenuBar 类"
ms.assetid: 4c93c459-7f70-4240-8c63-280bb811e374
caps.latest.revision: 32
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCPopupMenuBar 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

菜单栏嵌入到弹出菜单。  
  
## 语法  
  
```  
class CMFCPopupMenuBar : public CMFCToolBar  
```  
  
## 成员  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CMFCPopupMenuBar::AdjustSizeImmediate](../Topic/CMFCPopupMenuBar::AdjustSizeImmediate.md)|立即计算窗格的格式。  \(重写 [CPane::AdjustSizeImmediate](../Topic/CPane::AdjustSizeImmediate.md)。\)|  
|[CMFCPopupMenuBar::BuildOrigItems](../Topic/CMFCPopupMenuBar::BuildOrigItems.md)|从具有指定的菜单资源加载弹出菜单项。|  
|[CMFCPopupMenuBar::CloseDelayedSubMenu](../Topic/CMFCPopupMenuBar::CloseDelayedSubMenu.md)|关闭一个延迟的弹出菜单按钮。|  
|[CMFCPopupMenuBar::ExportToMenu](../Topic/CMFCPopupMenuBar::ExportToMenu.md)|从命弹出菜单按钮一个菜单。|  
|[CMFCPopupMenuBar::FindDestintationToolBar](../Topic/CMFCPopupMenuBar::FindDestintationToolBar.md)|找到指定的点集的工具栏。|  
|[CMFCPopupMenuBar::GetCurrentMenuImageSize](../Topic/CMFCPopupMenuBar::GetCurrentMenuImageSize.md)|指示菜单按钮图像的大小。|  
|[CMFCPopupMenuBar::GetDefaultMenuId](../Topic/CMFCPopupMenuBar::GetDefaultMenuId.md)|返回默认值菜单项的标识符。|  
|[CMFCPopupMenuBar::GetLastCommandIndex](../Topic/CMFCPopupMenuBar::GetLastCommandIndex.md)|获取最近调用的菜单命令的索引。|  
|[CMFCPopupMenuBar::GetOffset](../Topic/CMFCPopupMenuBar::GetOffset.md)|获取弹出菜单栏的行偏移量。|  
|[CMFCPopupMenuBar::ImportFromMenu](../Topic/CMFCPopupMenuBar::ImportFromMenu.md)|从指定的菜单导入弹出菜单按钮。|  
|[CMFCPopupMenuBar::IsDropDownListMode](../Topic/CMFCPopupMenuBar::IsDropDownListMode.md)|指示弹出菜单栏是否下拉列表模式。|  
|[CMFCPopupMenuBar::IsPaletteMode](../Topic/CMFCPopupMenuBar::IsPaletteMode.md)|指示弹出菜单栏是否在"模式。|  
|[CMFCPopupMenuBar::IsRibbonPanel](../Topic/CMFCPopupMenuBar::IsRibbonPanel.md)|指示这是一个 \(`FALSE` 默认情况下\)。|  
|[CMFCPopupMenuBar::IsRibbonPanelInRegularMode](../Topic/CMFCPopupMenuBar::IsRibbonPanelInRegularMode.md)|指示这是一个功能区面板在普通模式 \(`FALSE` 下默认情况下\)。|  
|[CMFCPopupMenuBar::LoadFromHash](../Topic/CMFCPopupMenuBar::LoadFromHash.md)|加载一个存档的菜单。|  
|[CMFCPopupMenuBar::RestoreDelayedSubMenu](../Topic/CMFCPopupMenuBar::RestoreDelayedSubMenu.md)|还原关闭的弹出菜单栏一个延迟菜单按钮。|  
|[CMFCPopupMenuBar::SetButtonStyle](../Topic/CMFCPopupMenuBar::SetButtonStyle.md)|设置工具栏按钮的样式在给定索引。  \(重写 [CMFCToolBar::SetButtonStyle](../Topic/CMFCToolBar::SetButtonStyle.md)。\)|  
|[CMFCPopupMenuBar::SetOffset](../Topic/CMFCPopupMenuBar::SetOffset.md)|设置弹出菜单栏的行偏移量。|  
|[CMFCPopupMenuBar::StartPopupMenuTimer](../Topic/CMFCPopupMenuBar::StartPopupMenuTimer.md)|开始一个指定延迟的弹出菜单按钮的计时器。|  
  
### 数据成员  
  
|名称|描述|  
|--------|--------|  
|[CMFCPopupMenuBar::m\_bDisableSideBarInXPMode](../Topic/CMFCPopupMenuBar::m_bDisableSideBarInXPMode.md)|指定灰色侧栏是否将显示，如果应用程序具有 Windows XP 外观。|  
  
## 备注  
 `CMFCPopupMenuBar` 是在 [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md) 的同时并嵌入在其中。  `CMFCPopupMenuBar` 包括 `CMFCPopupMenu` 对象的整个客户端区域。  它支持键盘和鼠标输入。  它还将该输入到 `CMFCPopupMenu` 和到顶部框架窗口。  
  
## 示例  
 下面的示例演示从 `CMFCPopupMenu` 对象的一 `CMFCPopupMenuBar` 对象。  此代码段是 [绘制客户端示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DrawClient#7](../../mfc/reference/codesnippet/CPP/cmfcpopupmenubar-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)  
  
## 要求  
 **标头：** afxpopupmenubar.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCColorBar Class](../../mfc/reference/cmfccolorbar-class.md)   
 [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md)