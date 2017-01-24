---
title: "CMFCVisualManagerWindows Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCVisualManagerWindows"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCVisualManagerWindows class"
ms.assetid: 568b6e9e-8e67-4477-9a3d-2981cbd09861
caps.latest.revision: 46
caps.handback.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCVisualManagerWindows Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当用户选择某Windows XP或vista主题时，`CMFCVisualManagerWindows` 模式Microsoft Windows XP或Microsoft vista外观。  
  
## 语法  
  
```  
class CMFCVisualManagerWindows : public CMFCVisualManagerOfficeXP  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|`CMFCVisualManagerWindows::CMFCVisualManagerWindows`|默认构造函数。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CMFCVisualManagerWindows::AlwaysHighlight3DTabs](../Topic/CMFCVisualManagerWindows::AlwaysHighlight3DTabs.md)|框架调用此方法来确定三维是否在应用程序应始终显示选项。  （重写 [CMFCVisualManager::AlwaysHighlight3DTabs](../Topic/CMFCVisualManager::AlwaysHighlight3DTabs.md)。）|  
|[CMFCVisualManagerWindows::DrawComboBorderWinXP](../Topic/CMFCVisualManagerWindows::DrawComboBorderWinXP.md)|（重写 `CMFCVisualManager::DrawComboBorderWinXP`。）|  
|[CMFCVisualManagerWindows::DrawComboDropButtonWinXP](../Topic/CMFCVisualManagerWindows::DrawComboDropButtonWinXP.md)|（重写 [CMFCVisualManager::DrawComboDropButtonWinXP](../Topic/CMFCVisualManager::DrawComboDropButtonWinXP.md)。）|  
|[CMFCVisualManagerWindows::DrawPushButtonWinXP](../Topic/CMFCVisualManagerWindows::DrawPushButtonWinXP.md)|（重写 [CMFCVisualManager::DrawPushButtonWinXP](../Topic/CMFCVisualManager::DrawPushButtonWinXP.md)。）|  
|[CMFCVisualManagerWindows::GetButtonExtraBorder](../Topic/CMFCVisualManagerWindows::GetButtonExtraBorder.md)|当它绘制工具栏按钮时，框架调用此方法。  （重写 [CMFCVisualManager::GetButtonExtraBorder](../Topic/CMFCVisualManager::GetButtonExtraBorder.md)。）|  
|[CMFCVisualManagerWindows::GetCaptionButtonExtraBorder](../Topic/CMFCVisualManagerWindows::GetCaptionButtonExtraBorder.md)|（重写 [CMFCVisualManager::GetCaptionButtonExtraBorder](../Topic/CMFCVisualManager::GetCaptionButtonExtraBorder.md)。）|  
|[CMFCVisualManagerWindows::GetDockingPaneCaptionExtraHeight](../Topic/CMFCVisualManagerWindows::GetDockingPaneCaptionExtraHeight.md)|（重写 `CMFCVisualManager::GetDockingPaneCaptionExtraHeight`。）|  
|[CMFCVisualManagerWindows::GetHighlightedMenuItemTextColor](../Topic/CMFCVisualManagerWindows::GetHighlightedMenuItemTextColor.md)|（重写 `CMFCVisualManagerOfficeXP::GetHighlightedMenuItemTextColor`。）|  
|[CMFCVisualManagerWindows::GetPopupMenuGap](../Topic/CMFCVisualManagerWindows::GetPopupMenuGap.md)|（重写 `CMFCVisualManagerOfficeXP::GetPopupMenuGap`。）|  
|[CMFCVisualManagerWindows::GetToolbarButtonTextColor](../Topic/CMFCVisualManagerWindows::GetToolbarButtonTextColor.md)|（重写 `CMFCVisualManagerOfficeXP::GetToolbarButtonTextColor`。）|  
|[CMFCVisualManagerWindows::IsDefaultWinXPPopupButton](../Topic/CMFCVisualManagerWindows::IsDefaultWinXPPopupButton.md)|（重写 [CMFCVisualManager::IsDefaultWinXPPopupButton](../Topic/CMFCVisualManager::IsDefaultWinXPPopupButton.md)。）|  
|[CMFCVisualManagerWindows::IsHighlightWholeMenuItem](../Topic/CMFCVisualManagerWindows::IsHighlightWholeMenuItem.md)|（重写 `CMFCVisualManagerOfficeXP::IsHighlightWholeMenuItem`。）|  
|[CMFCVisualManagerWindows::IsOfficeStyleMenus](../Topic/CMFCVisualManagerWindows::IsOfficeStyleMenus.md)||  
|[CMFCVisualManagerWindows::IsOfficeXPStyleMenus](../Topic/CMFCVisualManagerWindows::IsOfficeXPStyleMenus.md)|指示视觉管理器是否实现Office XP式菜单。  （重写 [CMFCVisualManager::IsOfficeXPStyleMenus](../Topic/CMFCVisualManager::IsOfficeXPStyleMenus.md)。）|  
|[CMFCVisualManagerWindows::IsWindowsThemingSupported](../Topic/CMFCVisualManagerWindows::IsWindowsThemingSupported.md)|（重写 `CMFCVisualManager::IsWindowsThemingSupported`。）|  
|[CMFCVisualManagerWindows::IsWinXPThemeAvailable](../Topic/CMFCVisualManagerWindows::IsWinXPThemeAvailable.md)|指示Windows主题是否可用。  主题可以是Windows XP主题或 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] 主题。|  
|[CMFCVisualManagerWindows::OnDrawBarGripper](../Topic/CMFCVisualManagerWindows::OnDrawBarGripper.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawBarGripper`。）|  
|[CMFCVisualManagerWindows::OnDrawBrowseButton](../Topic/CMFCVisualManagerWindows::OnDrawBrowseButton.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawBrowseButton`。）|  
|[CMFCVisualManagerWindows::OnDrawButtonBorder](../Topic/CMFCVisualManagerWindows::OnDrawButtonBorder.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawButtonBorder`。）|  
|[CMFCVisualManagerWindows::OnDrawButtonSeparator](../Topic/CMFCVisualManagerWindows::OnDrawButtonSeparator.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawButtonSeparator`。）|  
|[CMFCVisualManagerWindows::OnDrawCaptionButton](../Topic/CMFCVisualManagerWindows::OnDrawCaptionButton.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawCaptionButton`。）|  
|[CMFCVisualManagerWindows::OnDrawCaptionButtonIcon](../Topic/CMFCVisualManagerWindows::OnDrawCaptionButtonIcon.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawCaptionButtonIcon`。）|  
|[CMFCVisualManagerWindows::OnDrawCheckBoxEx](../Topic/CMFCVisualManagerWindows::OnDrawCheckBoxEx.md)|（重写 [CMFCVisualManager::OnDrawCheckBoxEx](../Topic/CMFCVisualManager::OnDrawCheckBoxEx.md)。）|  
|[CMFCVisualManagerWindows::OnDrawComboBorder](../Topic/CMFCVisualManagerWindows::OnDrawComboBorder.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawComboBorder`。）|  
|[CMFCVisualManagerWindows::OnDrawComboDropButton](../Topic/CMFCVisualManagerWindows::OnDrawComboDropButton.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawComboDropButton`。）|  
|[CMFCVisualManagerWindows::OnDrawControlBorder](../Topic/CMFCVisualManagerWindows::OnDrawControlBorder.md)|（重写 [CMFCVisualManager::OnDrawControlBorder](../Topic/CMFCVisualManager::OnDrawControlBorder.md)。）|  
|[CMFCVisualManagerWindows::OnDrawEditBorder](../Topic/CMFCVisualManagerWindows::OnDrawEditBorder.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawEditBorder`。）|  
|[CMFCVisualManagerWindows::OnDrawExpandingBox](../Topic/CMFCVisualManagerWindows::OnDrawExpandingBox.md)|（重写 [CMFCVisualManager::OnDrawExpandingBox](../Topic/CMFCVisualManager::OnDrawExpandingBox.md)。）|  
|[CMFCVisualManagerWindows::OnDrawFloatingToolbarBorder](../Topic/CMFCVisualManagerWindows::OnDrawFloatingToolbarBorder.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawFloatingToolbarBorder`。）|  
|[CMFCVisualManagerWindows::OnDrawHeaderCtrlBorder](../Topic/CMFCVisualManagerWindows::OnDrawHeaderCtrlBorder.md)|当在 [CMFCHeaderCtrl Class](../../mfc/reference/cmfcheaderctrl-class.md)的实例周围时，分区边框框架调用此方法。  （重写 [CMFCVisualManager::OnDrawHeaderCtrlBorder](../Topic/CMFCVisualManager::OnDrawHeaderCtrlBorder.md)。）|  
|[CMFCVisualManagerWindows::OnDrawHeaderCtrlSortArrow](../Topic/CMFCVisualManagerWindows::OnDrawHeaderCtrlSortArrow.md)|当它绘制标头控件的排序箭头时，框架调用此函数。  （重写 [CMFCVisualManager::OnDrawHeaderCtrlSortArrow](../Topic/CMFCVisualManager::OnDrawHeaderCtrlSortArrow.md)。）|  
|[CMFCVisualManagerWindows::OnDrawMenuBorder](../Topic/CMFCVisualManagerWindows::OnDrawMenuBorder.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawMenuBorder`。）|  
|[CMFCVisualManagerWindows::OnDrawMenuSystemButton](../Topic/CMFCVisualManagerWindows::OnDrawMenuSystemButton.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawMenuSystemButton`。）|  
|[CMFCVisualManagerWindows::OnDrawMiniFrameBorder](../Topic/CMFCVisualManagerWindows::OnDrawMiniFrameBorder.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawMiniFrameBorder`。）|  
|[CMFCVisualManagerWindows::OnDrawOutlookPageButtonBorder](../Topic/CMFCVisualManagerWindows::OnDrawOutlookPageButtonBorder.md)|调用由框架，则划分Outlook页按钮的边框。  （重写 [CMFCVisualManager::OnDrawOutlookPageButtonBorder](../Topic/CMFCVisualManager::OnDrawOutlookPageButtonBorder.md)。）|  
|[CMFCVisualManagerWindows::OnDrawPaneBorder](../Topic/CMFCVisualManagerWindows::OnDrawPaneBorder.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawPaneBorder`。）|  
|[CMFCVisualManagerWindows::OnDrawPaneCaption](../Topic/CMFCVisualManagerWindows::OnDrawPaneCaption.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawPaneCaption`。）|  
|[CMFCVisualManagerWindows::OnDrawPopupWindowButtonBorder](../Topic/CMFCVisualManagerWindows::OnDrawPopupWindowButtonBorder.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawPopupWindowButtonBorder`。）|  
|[CMFCVisualManagerWindows::OnDrawScrollButtons](../Topic/CMFCVisualManagerWindows::OnDrawScrollButtons.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawScrollButtons`。）|  
|[CMFCVisualManagerWindows::OnDrawSeparator](../Topic/CMFCVisualManagerWindows::OnDrawSeparator.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawSeparator`。）|  
|[CMFCVisualManagerWindows::OnDrawSpinButtons](../Topic/CMFCVisualManagerWindows::OnDrawSpinButtons.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawSpinButtons`。）|  
|[CMFCVisualManagerWindows::OnDrawStatusBarPaneBorder](../Topic/CMFCVisualManagerWindows::OnDrawStatusBarPaneBorder.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawStatusBarPaneBorder`。）|  
|[CMFCVisualManagerWindows::OnDrawStatusBarProgress](../Topic/CMFCVisualManagerWindows::OnDrawStatusBarProgress.md)|当钢笔绘制在 [CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md) 对象时，进度指示框架调用此方法。  （重写 [CMFCVisualManager::OnDrawStatusBarProgress](../Topic/CMFCVisualManager::OnDrawStatusBarProgress.md)。）|  
|[CMFCVisualManagerWindows::OnDrawStatusBarSizeBox](../Topic/CMFCVisualManagerWindows::OnDrawStatusBarSizeBox.md)|当它绘制 [CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)时，大小控制块框架调用此方法。  （重写 [CMFCVisualManager::OnDrawStatusBarSizeBox](../Topic/CMFCVisualManager::OnDrawStatusBarSizeBox.md)。）|  
|[CMFCVisualManagerWindows::OnDrawTab](../Topic/CMFCVisualManagerWindows::OnDrawTab.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawTab`。）|  
|[CMFCVisualManagerWindows::OnDrawTabCloseButton](../Topic/CMFCVisualManagerWindows::OnDrawTabCloseButton.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawTabCloseButton`。）|  
|[CMFCVisualManagerWindows::OnDrawTabsButtonBorder](../Topic/CMFCVisualManagerWindows::OnDrawTabsButtonBorder.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawTabsButtonBorder`。）|  
|[CMFCVisualManagerWindows::OnDrawTask](../Topic/CMFCVisualManagerWindows::OnDrawTask.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawTask`。）|  
|[CMFCVisualManagerWindows::OnDrawTasksGroupAreaBorder](../Topic/CMFCVisualManagerWindows::OnDrawTasksGroupAreaBorder.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawTasksGroupAreaBorder`。）|  
|[CMFCVisualManagerWindows::OnDrawTasksGroupCaption](../Topic/CMFCVisualManagerWindows::OnDrawTasksGroupCaption.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawTasksGroupCaption`。）|  
|[CMFCVisualManagerWindows::OnDrawTearOffCaption](../Topic/CMFCVisualManagerWindows::OnDrawTearOffCaption.md)|（重写 `CMFCVisualManagerOfficeXP::OnDrawTearOffCaption`。）|  
|[CMFCVisualManagerWindows::OnErasePopupWindowButton](../Topic/CMFCVisualManagerWindows::OnErasePopupWindowButton.md)|（重写 `CMFCVisualManagerOfficeXP::OnErasePopupWindowButton`。）|  
|[CMFCVisualManagerWindows::OnEraseTabsArea](../Topic/CMFCVisualManagerWindows::OnEraseTabsArea.md)|（重写 `CMFCVisualManagerOfficeXP::OnEraseTabsArea`。）|  
|[CMFCVisualManagerWindows::OnEraseTabsButton](../Topic/CMFCVisualManagerWindows::OnEraseTabsButton.md)|（重写 `CMFCVisualManagerOfficeXP::OnEraseTabsButton`。）|  
|[CMFCVisualManagerWindows::OnEraseTabsFrame](../Topic/CMFCVisualManagerWindows::OnEraseTabsFrame.md)|则清除在 [CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md)时，的一个帧框架调用此方法。  （重写 [CMFCVisualManager::OnEraseTabsFrame](../Topic/CMFCVisualManager::OnEraseTabsFrame.md)。）|  
|[CMFCVisualManagerWindows::OnFillBarBackground](../Topic/CMFCVisualManagerWindows::OnFillBarBackground.md)|（重写 `CMFCVisualManagerOfficeXP::OnFillBarBackground`。）|  
|[CMFCVisualManagerWindows::OnFillButtonInterior](../Topic/CMFCVisualManagerWindows::OnFillButtonInterior.md)|（重写 `CMFCVisualManagerOfficeXP::OnFillButtonInterior`。）|  
|[CMFCVisualManagerWindows::OnFillCommandsListBackground](../Topic/CMFCVisualManagerWindows::OnFillCommandsListBackground.md)|（重写 `CMFCVisualManagerOfficeXP::OnFillCommandsListBackground`。）|  
|[CMFCVisualManagerWindows::OnFillMiniFrameCaption](../Topic/CMFCVisualManagerWindows::OnFillMiniFrameCaption.md)|（重写 `CMFCVisualManagerOfficeXP::OnFillMiniFrameCaption`。）|  
|[CMFCVisualManagerWindows::OnFillOutlookPageButton](../Topic/CMFCVisualManagerWindows::OnFillOutlookPageButton.md)|在加载Outlook页按钮的内部时，框架调用此方法。  （重写 [CMFCVisualManager::OnFillOutlookPageButton](../Topic/CMFCVisualManager::OnFillOutlookPageButton.md)。）|  
|[CMFCVisualManagerWindows::OnFillTasksGroupInterior](../Topic/CMFCVisualManagerWindows::OnFillTasksGroupInterior.md)|（重写 `CMFCVisualManagerOfficeXP::OnFillTasksGroupInterior`。）|  
|[CMFCVisualManagerWindows::OnFillTasksPaneBackground](../Topic/CMFCVisualManagerWindows::OnFillTasksPaneBackground.md)|在加载 [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md) 控件的背景时，框架调用此方法。  （重写 [CMFCVisualManager::OnFillTasksPaneBackground](../Topic/CMFCVisualManager::OnFillTasksPaneBackground.md)。）|  
|[CMFCVisualManagerWindows::OnHighlightMenuItem](../Topic/CMFCVisualManagerWindows::OnHighlightMenuItem.md)|（重写 `CMFCVisualManagerOfficeXP::OnHighlightMenuItem`。）|  
|[CMFCVisualManagerWindows::OnHighlightRarelyUsedMenuItems](../Topic/CMFCVisualManagerWindows::OnHighlightRarelyUsedMenuItems.md)|（重写 `CMFCVisualManagerOfficeXP::OnHighlightRarelyUsedMenuItems`。）|  
|[CMFCVisualManagerWindows::OnUpdateSystemColors](../Topic/CMFCVisualManagerWindows::OnUpdateSystemColors.md)|（重写 `CMFCVisualManagerOfficeXP::OnUpdateSystemColors`。）|  
|[CMFCVisualManagerWindows::SetOfficeStyleMenus](../Topic/CMFCVisualManagerWindows::SetOfficeStyleMenus.md)||  
  
### 数据成员  
  
|名称|说明|  
|--------|--------|  
|[CMFCVisualManagerWindows::m\_b3DTabsXPTheme](../Topic/CMFCVisualManagerWindows::m_b3DTabsXPTheme.md)|指定Windows XP主题是否显示三维选项。|  
  
## 备注  
 使用 `CMFCVisualManagerWindows` 选件类来更改应用程序的外观模式当前Windows XP或 [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)] 主题在运行应用程序的计算机上。  
  
 但是，Windows主题可能不可用，如果应用程序在Windows的版本早于Windows XP运行或，如果主题是禁用的，因为用户使用 **经典** 视图。  如果主题不可用，则使用默认视觉管理器中定义的应用程序在 [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)。  
  
## 示例  
 下面的示例演示如何使用 `CMFCVisualManagerWindows`。  此代码段是 [桌面通知演示示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#10](../../mfc/reference/codesnippet/CPP/cmfcvisualmanagerwindows-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
 [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)  
  
 [CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)  
  
 [CMFCVisualManagerWindows](../../mfc/reference/cmfcvisualmanagerwindows-class.md)  
  
## 要求  
 **标头:** afxvisualmanagerwindows.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager Class](../../mfc/reference/cmfcvisualmanager-class.md)   
 [CMFCVisualManagerOfficeXP Class](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)   
 [CMFCVisualManager::SetDefaultManager](../Topic/CMFCVisualManager::SetDefaultManager.md)