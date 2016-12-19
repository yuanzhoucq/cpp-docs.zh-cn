---
title: "CMFCMenuBar Class | Microsoft Docs"
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
  - "CMFCMenuBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCMenuBar class"
ms.assetid: 8a3ce4c7-b012-4dc0-b4f8-53c10b4b86b8
caps.latest.revision: 36
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCMenuBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

菜单栏实现停靠。  
  
## 语法  
  
```  
class CMFCMenuBar : public CMFCToolbar  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCMenuBar::AdjustLocations](../Topic/CMFCMenuBar::AdjustLocations.md)|（重写 `CMFCToolBar::AdjustLocations`。）|  
|[CMFCMenuBar::AllowChangeTextLabels](../Topic/CMFCMenuBar::AllowChangeTextLabels.md)|指定文本标签是否可以显示在工具栏按钮的图像下。  （重写 [CMFCToolBar::AllowChangeTextLabels](../Topic/CMFCToolBar::AllowChangeTextLabels.md)。）|  
|[CMFCMenuBar::AllowShowOnPaneMenu](../Topic/CMFCMenuBar::AllowShowOnPaneMenu.md)|（重写 `CPane::AllowShowOnPaneMenu`。）|  
|[CMFCMenuBar::CalcFixedLayout](../Topic/CMFCMenuBar::CalcFixedLayout.md)|计算工具栏的水平大小。  （重写 [CMFCToolBar::CalcFixedLayout](../Topic/CMFCToolBar::CalcFixedLayout.md)。）|  
|[CMFCMenuBar::CalcLayout](../Topic/CMFCMenuBar::CalcLayout.md)|（重写 `CMFCToolBar::CalcLayout`。）|  
|[CMFCMenuBar::CalcMaxButtonHeight](../Topic/CMFCMenuBar::CalcMaxButtonHeight.md)|计算最大高度工具栏中的按钮。  （重写 [CMFCToolBar::CalcMaxButtonHeight](../Topic/CMFCToolBar::CalcMaxButtonHeight.md)。）|  
|[CMFCMenuBar::CanBeClosed](../Topic/CMFCMenuBar::CanBeClosed.md)|指定用户是否可以关闭工具栏。  （重写 [CMFCToolBar::CanBeClosed](../Topic/CMFCToolBar::CanBeClosed.md)。）|  
|[CMFCMenuBar::CanBeRestored](../Topic/CMFCMenuBar::CanBeRestored.md)|确定系统是否能还原工具栏到其原始状态在自定义项之后。  （重写 [CMFCToolBar::CanBeRestored](../Topic/CMFCToolBar::CanBeRestored.md)。）|  
|[CMFCMenuBar::Create](../Topic/CMFCMenuBar::Create.md)|创建menu控件并将它附加到 `CMFCMenuBar` 对象。|  
|[CMFCMenuBar::CreateEx](../Topic/CMFCMenuBar::CreateEx.md)|用不同的样式选项创建一 `CMFCMenuBar` 对象。|  
|[CMFCMenuBar::CreateFromMenu](../Topic/CMFCMenuBar::CreateFromMenu.md)|初始化 `CMFCMenuBar` 对象。  接受作为填充的 `CMFCMenuBar`的模板中的一个 `HMENU` 参数。|  
|[CMFCMenuBar::EnableHelpCombobox](../Topic/CMFCMenuBar::EnableHelpCombobox.md)|启用菜单栏上的右侧所在的 **帮助** 组合框。|  
|[CMFCMenuBar::EnableMenuShadows](../Topic/CMFCMenuBar::EnableMenuShadows.md)|指定是否显示弹出菜单的阴影。|  
|[CMFCMenuBar::GetAvailableExpandSize](../Topic/CMFCMenuBar::GetAvailableExpandSize.md)|（重写 [CPane::GetAvailableExpandSize](../Topic/CPane::GetAvailableExpandSize.md)。）|  
|[CMFCMenuBar::GetColumnWidth](../Topic/CMFCMenuBar::GetColumnWidth.md)|返回工具栏按钮的宽度。  （重写 [CMFCToolBar::GetColumnWidth](../Topic/CMFCToolBar::GetColumnWidth.md)。）|  
|[CMFCMenuBar::GetDefaultMenu](../Topic/CMFCMenuBar::GetDefaultMenu.md)|将处理返回到资源文件的原始菜单。|  
|[CMFCMenuBar::GetDefaultMenuResId](../Topic/CMFCMenuBar::GetDefaultMenuResId.md)|返回原始菜单的资源标识符在资源文件。|  
|[CMFCMenuBar::GetFloatPopupDirection](../Topic/CMFCMenuBar::GetFloatPopupDirection.md)||  
|[CMFCMenuBar::GetForceDownArrows](../Topic/CMFCMenuBar::GetForceDownArrows.md)||  
|[CMFCMenuBar::GetHelpCombobox](../Topic/CMFCMenuBar::GetHelpCombobox.md)|返回指向 **帮助** 组合框。|  
|[CMFCMenuBar::GetHMenu](../Topic/CMFCMenuBar::GetHMenu.md)|返回的句柄附加到 `CMFCMenuBar` 对象的菜单。|  
|[CMFCMenuBar::GetMenuFont](../Topic/CMFCMenuBar::GetMenuFont.md)|返回菜单对象的当前全局字体。|  
|[CMFCMenuBar::GetMenuItem](../Topic/CMFCMenuBar::GetMenuItem.md)|返回工具栏按钮与提供的项的索引。|  
|[CMFCMenuBar::GetRowHeight](../Topic/CMFCMenuBar::GetRowHeight.md)|返回高度工具栏按钮。  （重写 [CMFCToolBar::GetRowHeight](../Topic/CMFCToolBar::GetRowHeight.md)。）|  
|[CMFCMenuBar::GetSystemButton](../Topic/CMFCMenuBar::GetSystemButton.md)||  
|[CMFCMenuBar::GetSystemButtonsCount](../Topic/CMFCMenuBar::GetSystemButtonsCount.md)||  
|[CMFCMenuBar::GetSystemMenu](../Topic/CMFCMenuBar::GetSystemMenu.md)||  
|[CMFCMenuBar::HighlightDisabledItems](../Topic/CMFCMenuBar::HighlightDisabledItems.md)|指示禁用菜单项是否显示。|  
|[CMFCMenuBar::IsButtonExtraSizeAvailable](../Topic/CMFCMenuBar::IsButtonExtraSizeAvailable.md)|定位工具栏是否可以显示扩展的边框的按钮。  （重写 [CMFCToolBar::IsButtonExtraSizeAvailable](../Topic/CMFCToolBar::IsButtonExtraSizeAvailable.md)。）|  
|[CMFCMenuBar::IsHighlightDisabledItems](../Topic/CMFCMenuBar::IsHighlightDisabledItems.md)|指示禁用项目是否显示。|  
|[CMFCMenuBar::IsMenuShadows](../Topic/CMFCMenuBar::IsMenuShadows.md)|指示阴影是否为弹出菜单绘制。|  
|[CMFCMenuBar::IsRecentlyUsedMenus](../Topic/CMFCMenuBar::IsRecentlyUsedMenus.md)|指示最近使用的菜单命令是否在菜单栏上显示。|  
|[CMFCMenuBar::IsShowAllCommands](../Topic/CMFCMenuBar::IsShowAllCommands.md)|指示弹出菜单是否显示所有命令。|  
|[CMFCMenuBar::IsShowAllCommandsDelay](../Topic/CMFCMenuBar::IsShowAllCommandsDelay.md)|指示菜单是否经过短时间的延迟后显示所有命令。|  
|[CMFCMenuBar::LoadState](../Topic/CMFCMenuBar::LoadState.md)|从注册表中加载 `CMFCMenuBar` 对象的状态。|  
|[CMFCMenuBar::OnChangeHot](../Topic/CMFCMenuBar::OnChangeHot.md)|调用由结构，当用户选择工具栏上的按钮。  （重写 [CMFCToolBar::OnChangeHot](../Topic/CMFCToolBar::OnChangeHot.md)。）|  
|[CMFCMenuBar::OnDefaultMenuLoaded](../Topic/CMFCMenuBar::OnDefaultMenuLoaded.md)|调用由结构，当框架窗口加载资源文件中默认菜单。|  
|[CMFCMenuBar::OnSendCommand](../Topic/CMFCMenuBar::OnSendCommand.md)|（重写 `CMFCToolBar::OnSendCommand`。）|  
|[CMFCMenuBar::OnSetDefaultButtonText](../Topic/CMFCMenuBar::OnSetDefaultButtonText.md)|调用由框架，当菜单在自定义模式和用户下时将菜单项的文本。|  
|[CMFCMenuBar::OnToolHitTest](../Topic/CMFCMenuBar::OnToolHitTest.md)|（重写 `CMFCToolBar::OnToolHitTest`。）|  
|[CMFCMenuBar::PreTranslateMessage](../Topic/CMFCMenuBar::PreTranslateMessage.md)|（重写 `CMFCToolBar::PreTranslateMessage`。）|  
|[CMFCMenuBar::RestoreOriginalstate](../Topic/CMFCMenuBar::RestoreOriginalstate.md)|调用由框架，当菜单在自定义模式和用户下时对菜单栏选择 **重置**。|  
|[CMFCMenuBar::SaveState](../Topic/CMFCMenuBar::SaveState.md)|保存 `CMFCMenuBar` 对象的状态对注册表的。|  
|[CMFCMenuBar::SetDefaultMenuResId](../Topic/CMFCMenuBar::SetDefaultMenuResId.md)|将资源文件的原始菜单。|  
|[CMFCMenuBar::SetForceDownArrows](../Topic/CMFCMenuBar::SetForceDownArrows.md)||  
|[CMFCMenuBar::SetMaximizeMode](../Topic/CMFCMenuBar::SetMaximizeMode.md)|调用由结构，当MDI子窗口更改其显示模式。  如果MDI子窗口最近最大化或不再最大化，此方法将更新菜单栏。|  
|[CMFCMenuBar::SetMenuButtonRTC](../Topic/CMFCMenuBar::SetMenuButtonRTC.md)|设置生成的运行时选件类信息，当用户动态地创建菜单按钮时。|  
|[CMFCMenuBar::SetMenuFont](../Topic/CMFCMenuBar::SetMenuFont.md)|将所有菜单的字体在应用程序。|  
|[CMFCMenuBar::SetRecentlyUsedMenus](../Topic/CMFCMenuBar::SetRecentlyUsedMenus.md)|指定菜单栏是否显示最近使用的菜单命令。|  
|[CMFCMenuBar::SetShowAllCommands](../Topic/CMFCMenuBar::SetShowAllCommands.md)|指定菜单栏是显示所有命令。|  
  
## 备注  
 `CMFCMenuBar` 选件类是一个菜单栏停靠功能的实现。  它类似于工具栏，不过，它不能关闭的\(它始终显示。  
  
 `CMFCMenuBar` 支持显示最近使用的菜单项对象的选项。  此选项有效，`CMFCMenuBar` 显示可用命令的一个子集在第一查看的。  之后，最近使用的命令随指令一起的原始子集显示。  此外，用户始终可以展开菜单查看所有可用命令。  因此，因此，只有当最近后，每个可用的命令配置通常显示，或显示。  
  
 若要使用 `CMFCMenuBar` 对象，请将它在主窗口帧对象。  在处理 `WM_CREATE` 消息时，应调用 `CMFCMenuBar::Create` 或 `CMFCMenuBar::CreateEx`。  无论要创建自己使用的功能，请将指针到主框架窗口。  然后通过调用 [CFrameWndEx::EnableDocking](../Topic/CFrameWndEx::EnableDocking.md)启用停靠。  通过调用 [CFrameWndEx::DockPane](../Topic/CFrameWndEx::DockPane.md)停靠此菜单。  
  
## 示例  
 下面的示例在 `CMFCMenuBar` 选件类演示如何使用各种方法。  此示例演示如何设置窗格的样式，以使自定义按钮，启用帮助框中，启用弹出菜单的阴影和更新菜单栏。  此代码段是 [pocket IE演示示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/CPP/cmfcmenubar-class_1.h)]  
[!code-cpp[NVC_MFC_IEDemo#3](../../mfc/reference/codesnippet/CPP/cmfcmenubar-class_2.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)  
  
 [CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)  
  
 [CMFCMenuBar](../../mfc/reference/cmfcmenubar-class.md)  
  
## 要求  
 **标头:** afxmenubar.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBar Class](../../mfc/reference/cmfctoolbar-class.md)