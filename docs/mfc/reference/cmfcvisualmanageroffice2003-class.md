---
title: "CMFCVisualManagerOffice2003 Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCVisualManagerOffice2003"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCVisualManagerOffice2003 class"
ms.assetid: 115482cd-e349-450a-8dc4-c6023d092aab
caps.latest.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 33
---
# CMFCVisualManagerOffice2003 Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCVisualManagerOffice2003` 为应用程序 Microsoft Office 2003 外观。  
  
## 语法  
  
```  
class CMFCVisualManagerOffice2003 : public CMFCVisualManagerOfficeXP  
```  
  
## 成员  
  
### 公共方法  
  
|名称|描述|  
|--------|--------|  
|[CMFCVisualManagerOffice2003::DrawComboBorderWinXP](../Topic/CMFCVisualManagerOffice2003::DrawComboBorderWinXP.md)|使用当前 Windows XP 主题，分区组合框边框。  \(重写 [CMFCVisualManager::DrawComboBorderWinXP](../Topic/CMFCVisualManager::DrawComboBorderWinXP.md)。\)|  
|[CMFCVisualManagerOffice2003::DrawComboDropButtonWinXP](../Topic/CMFCVisualManagerOffice2003::DrawComboDropButtonWinXP.md)|使用当前 Windows XP 主题，将绘制一个组合框下拉式按钮。  \(重写 [CMFCVisualManager::DrawComboDropButtonWinXP](../Topic/CMFCVisualManager::DrawComboDropButtonWinXP.md)。\)|  
|[CMFCVisualManagerOffice2003::DrawCustomizeButton](../Topic/CMFCVisualManagerOffice2003::DrawCustomizeButton.md)|绘制自定义按钮。|  
|[CMFCVisualManagerOffice2003::DrawPushButtonWinXP](../Topic/CMFCVisualManagerOffice2003::DrawPushButtonWinXP.md)|使用当前 Windows XP 主题，绘制按钮。  \(重写 [CMFCVisualManager::DrawPushButtonWinXP](../Topic/CMFCVisualManager::DrawPushButtonWinXP.md)。\)|  
|[CMFCVisualManagerOffice2003::GetBaseThemeColor](../Topic/CMFCVisualManagerOffice2003::GetBaseThemeColor.md)|获取基主题颜色。|  
|[CMFCVisualManagerOffice2003::GetHighlightMenuItemColor](../Topic/CMFCVisualManagerOffice2003::GetHighlightMenuItemColor.md)|获取颜色用于显示菜单项。|  
|[CMFCVisualManagerOffice2003::GetPropertyGridGroupColor](../Topic/CMFCVisualManagerOffice2003::GetPropertyGridGroupColor.md)|框架调用属性的背景颜色列表的此方法获取。  \(重写 `CMFCVisualManagerOfficeXP::GetPropertyGridGroupColor`。\)|  
|[CMFCVisualManagerOffice2003::GetPropertyGridGroupTextColor](../Topic/CMFCVisualManagerOffice2003::GetPropertyGridGroupTextColor.md)|框架调用此方法检索属性的文本颜色列表。  \(重写 `CMFCVisualManagerOfficeXP::GetPropertyGridGroupTextColor`。\)|  
|[CMFCVisualManagerOffice2003::GetShowAllMenuItemsHeight](../Topic/CMFCVisualManagerOffice2003::GetShowAllMenuItemsHeight.md)|返回高度所有菜单项。  \(重写 [CMFCVisualManager::GetShowAllMenuItemsHeight](../Topic/CMFCVisualManager::GetShowAllMenuItemsHeight.md)。\)|  
|[CMFCVisualManagerOffice2003::GetSmartDockingBaseGuideColors](../Topic/CMFCVisualManagerOffice2003::GetSmartDockingBaseGuideColors.md)|设置指定的基本组背景颜色和边框颜色。  \(重写 `CMFCVisualManagerOfficeXP::GetSmartDockingBaseGuideColors`。\)|  
|[CMFCVisualManagerOffice2003::GetSmartDockingHighlightToneColor](../Topic/CMFCVisualManagerOffice2003::GetSmartDockingHighlightToneColor.md)|获取突出显示音色。  \(重写 [CMFCVisualManager::GetSmartDockingHighlightToneColor](../Topic/CMFCVisualManager::GetSmartDockingHighlightToneColor.md)。\)|  
|[CMFCVisualManagerOffice2003::GetTabFrameColors](../Topic/CMFCVisualManagerOffice2003::GetTabFrameColors.md)|它在必须检索设置绘制的选项窗口时，颜色框架调用此函数。  \(重写 [CMFCVisualManager::GetTabFrameColors](../Topic/CMFCVisualManager::GetTabFrameColors.md)。\)|  
|[CMFCVisualManagerOffice2003::GetToolBarCustomizeButtonMargin](../Topic/CMFCVisualManagerOffice2003::GetToolBarCustomizeButtonMargin.md)|获取工具栏的边距自定义按钮。  \(重写 `CMFCVisualManager::GetToolBarCustomizeButtonMargin`。\)|  
|[CMFCVisualManagerOffice2003::GetToolbarDisabledColor](../Topic/CMFCVisualManagerOffice2003::GetToolbarDisabledColor.md)|获取工具栏处于禁用状态的颜色。  \(重写 `CMFCVisualManager::GetToolbarDisabledColor`。\)|  
|[CMFCVisualManagerOffice2003::GetToolTipInfo](../Topic/CMFCVisualManagerOffice2003::GetToolTipInfo.md)|调用由框架获取工具提示信息。  \(重写 [CMFCVisualManager::GetToolTipInfo](../Topic/CMFCVisualManager::GetToolTipInfo.md)。\)|  
|[CMFCVisualManagerOffice2003::IsDefaultWinXPColorsEnabled](../Topic/CMFCVisualManagerOffice2003::IsDefaultWinXPColorsEnabled.md)|指示视觉管理器是否使用本机 Windows XP 主题颜色。|  
|[CMFCVisualManagerOffice2003::IsDockingTabHasBorder](../Topic/CMFCVisualManagerOffice2003::IsDockingTabHasBorder.md)|返回当前视觉管理器是否在停靠和选项卡式窗格周围绘制边框。  \(重写 [CMFCVisualManager::IsDockingTabHasBorder](../Topic/CMFCVisualManager::IsDockingTabHasBorder.md)。\)|  
|[CMFCVisualManagerOffice2003::IsHighlightOneNoteTabs](../Topic/CMFCVisualManagerOffice2003::IsHighlightOneNoteTabs.md)|指示是否应显示、选项。  \(重写 `CMFCVisualManager::IsHighlightOneNoteTabs`。\)|  
|[CMFCVisualManagerOffice2003::IsOffsetPressedButton](../Topic/CMFCVisualManagerOffice2003::IsOffsetPressedButton.md)|调用由结构，在绘制工具栏按钮时。  \(重写 `CMFCVisualManager::IsOffsetPressedButton`。\)|  
|[CMFCVisualManagerOffice2003::IsStatusBarOfficeXPLook](../Topic/CMFCVisualManagerOffice2003::IsStatusBarOfficeXPLook.md)|指示是否存在与 Office XP 查找的状态栏。|  
|[CMFCVisualManagerOffice2003::IsToolbarRoundShape](../Topic/CMFCVisualManagerOffice2003::IsToolbarRoundShape.md)|指示指定的工具栏是否具有圆形。  \(重写 [CMFCVisualManager::IsToolbarRoundShape](../Topic/CMFCVisualManager::IsToolbarRoundShape.md)。\)|  
|[CMFCVisualManagerOffice2003::IsUseGlobalTheme](../Topic/CMFCVisualManagerOffice2003::IsUseGlobalTheme.md)|指示是否使用全局 Windows XP 主题。|  
|[CMFCVisualManagerOffice2003::IsWindowsThemingSupported](../Topic/CMFCVisualManagerOffice2003::IsWindowsThemingSupported.md)|指示主题的窗口是否支持。  \(重写 [CMFCVisualManager::IsWindowsThemingSupported](../Topic/CMFCVisualManager::IsWindowsThemingSupported.md)。\)|  
|[CMFCVisualManagerOffice2003::OnDrawAutoHideButtonBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawAutoHideButtonBorder.md)|它还自动隐藏按钮的边框时，框架调用此方法。  \(重写 [CMFCVisualManager::OnDrawAutoHideButtonBorder](../Topic/CMFCVisualManager::OnDrawAutoHideButtonBorder.md)。\)|  
|[CMFCVisualManagerOffice2003::OnDrawBarGripper](../Topic/CMFCVisualManagerOffice2003::OnDrawBarGripper.md)|调用由结构，当它绘制控件条的手柄。  \(重写 `CMFCVisualManagerOfficeXP::OnDrawBarGripper`。\)|  
|[CMFCVisualManagerOffice2003::OnDrawBrowseButton](../Topic/CMFCVisualManagerOffice2003::OnDrawBrowseButton.md)|当它绘制编辑控件时，浏览按钮框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnDrawBrowseButton`。\)|  
|[CMFCVisualManagerOffice2003::OnDrawButtonBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawButtonBorder.md)|它还工具栏按钮的边框时，框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnDrawButtonBorder`。\)|  
|[CMFCVisualManagerOffice2003::OnDrawCaptionBarBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawCaptionBarBorder.md)|它还 [CMFCCaptionBar 类](../../mfc/reference/cmfccaptionbar-class.md) 对象的边框时，框架调用此方法。  \(重写 [CMFCVisualManager::OnDrawCaptionBarBorder](../Topic/CMFCVisualManager::OnDrawCaptionBarBorder.md)。\)|  
|[CMFCVisualManagerOffice2003::OnDrawCheckBoxEx](../Topic/CMFCVisualManagerOffice2003::OnDrawCheckBoxEx.md)|当它绘制复选框时，框架调用此方法。  \(重写 [CMFCVisualManager::OnDrawCheckBoxEx](../Topic/CMFCVisualManager::OnDrawCheckBoxEx.md)。\)|  
|[CMFCVisualManagerOffice2003::OnDrawComboBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawComboBorder.md)|当在 [CMFCToolBarComboBoxButton Class](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) 对象周围时，分区边框框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnDrawComboBorder`。\)|  
|[CMFCVisualManagerOffice2003::OnDrawComboDropButton](../Topic/CMFCVisualManagerOffice2003::OnDrawComboDropButton.md)|当它绘制 [CMFCToolBarComboBoxButton Class](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)的下拉按钮时，框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnDrawComboDropButton`。\)|  
|[CMFCVisualManagerOffice2003::OnDrawControlBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawControlBorder.md)|则划分控件的边框时，框架调用此方法。  \(重写 [CMFCVisualManager::OnDrawControlBorder](../Topic/CMFCVisualManager::OnDrawControlBorder.md)。\)|  
|[CMFCVisualManagerOffice2003::OnDrawExpandingBox](../Topic/CMFCVisualManagerOffice2003::OnDrawExpandingBox.md)|当它绘制一个扩展框时，框架调用此方法。  \(重写 [CMFCVisualManager::OnDrawExpandingBox](../Topic/CMFCVisualManager::OnDrawExpandingBox.md)。\)|  
|[CMFCVisualManagerOffice2003::OnDrawHeaderCtrlBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawHeaderCtrlBorder.md)|当在 [CMFCHeaderCtrl Class](../../mfc/reference/cmfcheaderctrl-class.md)的实例周围时，分区边框框架调用此方法。  \(重写 [CMFCVisualManager::OnDrawHeaderCtrlBorder](../Topic/CMFCVisualManager::OnDrawHeaderCtrlBorder.md)。\)|  
|[CMFCVisualManagerOffice2003::OnDrawMenuBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawMenuBorder.md)|它还 [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md)的边框时，框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnDrawMenuBorder`。\)|  
|[CMFCVisualManagerOffice2003::OnDrawOutlookBarSplitter](../Topic/CMFCVisualManagerOffice2003::OnDrawOutlookBarSplitter.md)|当它绘制 Outlook 栏的时，拆分器框架调用此方法。  \(重写[CMFCVisualManager::OnDrawOutlookBarSplitter](../Topic/CMFCVisualManager::OnDrawOutlookBarSplitter.md)。\)|  
|[CMFCVisualManagerOffice2003::OnDrawOutlookPageButtonBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawOutlookPageButtonBorder.md)|调用由框架，则划分 Outlook 页按钮的边框。  \(重写 [CMFCVisualManager::OnDrawOutlookPageButtonBorder](../Topic/CMFCVisualManager::OnDrawOutlookPageButtonBorder.md)。\)|  
|[CMFCVisualManagerOffice2003::OnDrawPaneBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawPaneBorder.md)|它还 [CPane Class](../../mfc/reference/cpane-class.md) 对象的边框时，框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnDrawPaneBorder`。\)|  
|[CMFCVisualManagerOffice2003::OnDrawPaneCaption](../Topic/CMFCVisualManagerOffice2003::OnDrawPaneCaption.md)|当钢笔绘制 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) 对象时，一个声明框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnDrawPaneCaption`。\)|  
|[CMFCVisualManagerOffice2003::OnDrawPopupWindowBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawPopupWindowBorder.md)|它还一个弹出窗口的边框时，框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnDrawPopupWindowBorder`。\)|  
|[CMFCVisualManagerOffice2003::OnDrawPopupWindowButtonBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawPopupWindowButtonBorder.md)|它还一个按钮的边框在一个弹出窗口时，的框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnDrawPopupWindowButtonBorder`。\)|  
|[CMFCVisualManagerOffice2003::OnDrawPopupWindowCaption](../Topic/CMFCVisualManagerOffice2003::OnDrawPopupWindowCaption.md)|它绘制弹出窗口的标题时，框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnDrawPopupWindowCaption`。\)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonButtonsGroup](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonButtonsGroup.md)|当它绘制按钮的一组在功能区上时，的框架调用此方法。  \(重写 [CMFCVisualManager::OnDrawRibbonButtonsGroup](../Topic/CMFCVisualManager::OnDrawRibbonButtonsGroup.md)。\)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonCategoryCaption](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonCategoryCaption.md)|当它绘制功能区类别时，标题栏框架调用此方法。  \(重写 [CMFCVisualManager::OnDrawRibbonCategoryCaption](../Topic/CMFCVisualManager::OnDrawRibbonCategoryCaption.md)。\)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonCategoryTab](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonCategoryTab.md)|当它绘制功能区类别的选项时，框架调用此方法。  \(重写 [CMFCVisualManager::OnDrawRibbonCategoryTab](../Topic/CMFCVisualManager::OnDrawRibbonCategoryTab.md)。\)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonProgressBar](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonProgressBar.md)|当它绘制 [CMFCRibbonProgressBar Class](../../mfc/reference/cmfcribbonprogressbar-class.md)时，框架调用此方法。  \(重写 [CMFCVisualManager::OnDrawRibbonProgressBar](../Topic/CMFCVisualManager::OnDrawRibbonProgressBar.md)。\)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonQuickAccessToolBarSeparator](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonQuickAccessToolBarSeparator.md)|它是在功能区的快速访问工具栏时，一个分隔符框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnDrawRibbonQuickAccessToolBarSeparator`。\)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonSliderChannel](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonSliderChannel.md)|当它绘制 [CMFCRibbonSlider Class](../../mfc/reference/cmfcribbonslider-class.md)的通道时，框架调用此方法。  \(重写 [CMFCVisualManager::OnDrawRibbonSliderChannel](../Topic/CMFCVisualManager::OnDrawRibbonSliderChannel.md)。\)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonSliderThumb](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonSliderThumb.md)|当它绘制 [CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md) 对象的滚动块时，框架调用此方法。  \(重写 [CMFCVisualManager::OnDrawRibbonSliderThumb](../Topic/CMFCVisualManager::OnDrawRibbonSliderThumb.md)。\)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonSliderZoomButton](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonSliderZoomButton.md)|当它绘制 [CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md) 对象时，缩放按钮框架调用此方法。  \(重写 [CMFCVisualManager::OnDrawRibbonSliderZoomButton](../Topic/CMFCVisualManager::OnDrawRibbonSliderZoomButton.md)。\)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonStatusBarPane](../Topic/CMFCVisualManagerOffice2003::OnDrawRibbonStatusBarPane.md)|它是在状态栏时，的一个窗格框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnDrawRibbonStatusBarPane`。\)|  
|[CMFCVisualManagerOffice2003::OnDrawScrollButtons](../Topic/CMFCVisualManagerOffice2003::OnDrawScrollButtons.md)|当它绘制滚动按钮时，框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnDrawScrollButtons`。\)|  
|[CMFCVisualManagerOffice2003::OnDrawSeparator](../Topic/CMFCVisualManagerOffice2003::OnDrawSeparator.md)|当它绘制分隔符时，框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnDrawSeparator`。\)|  
|[CMFCVisualManagerOffice2003::OnDrawShowAllMenuItems](../Topic/CMFCVisualManagerOffice2003::OnDrawShowAllMenuItems.md)|它是在菜单中，的所有项目框架调用此方法。  \(重写 [CMFCVisualManager::OnDrawShowAllMenuItems](../Topic/CMFCVisualManager::OnDrawShowAllMenuItems.md)。\)|  
|[CMFCVisualManagerOffice2003::OnDrawStatusBarPaneBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawStatusBarPaneBorder.md)|它还 [CMFCStatusBar Class](../../mfc/reference/cmfcstatusbar-class.md) 对象的边框时，框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnDrawStatusBarPaneBorder`。\)|  
|[CMFCVisualManagerOffice2003::OnDrawStatusBarProgress](../Topic/CMFCVisualManagerOffice2003::OnDrawStatusBarProgress.md)|当钢笔绘制在 [CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md) 对象时，进度指示框架调用此方法。  \(重写 [CMFCVisualManager::OnDrawStatusBarProgress](../Topic/CMFCVisualManager::OnDrawStatusBarProgress.md)。\)|  
|[CMFCVisualManagerOffice2003::OnDrawStatusBarSizeBox](../Topic/CMFCVisualManagerOffice2003::OnDrawStatusBarSizeBox.md)|当它绘制 [CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)时，大小控制块框架调用此方法。  \(重写 [CMFCVisualManager::OnDrawStatusBarSizeBox](../Topic/CMFCVisualManager::OnDrawStatusBarSizeBox.md)。\)|  
|[CMFCVisualManagerOffice2003::OnDrawTab](../Topic/CMFCVisualManagerOffice2003::OnDrawTab.md)|当它绘制 [CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md) 对象时，选项框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnDrawTab`。\)|  
|[CMFCVisualManagerOffice2003::OnDrawTabsButtonBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawTabsButtonBorder.md)|它还可选按钮的边框时，框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnDrawTabsButtonBorder`。\)|  
|[CMFCVisualManagerOffice2003::OnDrawTask](../Topic/CMFCVisualManagerOffice2003::OnDrawTask.md)|当它绘制 [CMFCTasksPaneTask Class](../../mfc/reference/cmfctaskspanetask-class.md) 对象时，框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnDrawTask`。\)|  
|[CMFCVisualManagerOffice2003::OnDrawTasksGroupAreaBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawTasksGroupAreaBorder.md)|当在 [CMFCTasksPane Class](../../mfc/reference/cmfctaskspane-class.md) 对象时，一组周围绘制边框框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnDrawTasksGroupAreaBorder`。\)|  
|[CMFCVisualManagerOffice2003::OnDrawTasksGroupCaption](../Topic/CMFCVisualManagerOffice2003::OnDrawTasksGroupCaption.md)|当钢笔绘制 [CMFCTasksPaneTaskGroup Class](../../mfc/reference/cmfctaskspanetaskgroup-class.md) 对象时，声明框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnDrawTasksGroupCaption`。\)|  
|[CMFCVisualManagerOffice2003::OnDrawTearOffCaption](../Topic/CMFCVisualManagerOffice2003::OnDrawTearOffCaption.md)|当钢笔绘制 [CMFCPopupMenu Class](../../mfc/reference/cmfcpopupmenu-class.md) 对象时，声明框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnDrawTearOffCaption`。\)|  
|[CMFCVisualManagerOffice2003::OnErasePopupWindowButton](../Topic/CMFCVisualManagerOffice2003::OnErasePopupWindowButton.md)|则清除在一个弹出窗口时，的按钮框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnErasePopupWindowButton`。\)|  
|[CMFCVisualManagerOffice2003::OnEraseTabsArea](../Topic/CMFCVisualManagerOffice2003::OnEraseTabsArea.md)|则清除选项窗口的选项卡区域时，框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnEraseTabsArea`。\)|  
|[CMFCVisualManagerOffice2003::OnEraseTabsButton](../Topic/CMFCVisualManagerOffice2003::OnEraseTabsButton.md)|则清除选项按钮的文本和图标时，框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnEraseTabsButton`。\)|  
|[CMFCVisualManagerOffice2003::OnEraseTabsFrame](../Topic/CMFCVisualManagerOffice2003::OnEraseTabsFrame.md)|则清除在 [CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md)时，的一个帧框架调用此方法。  \(重写 [CMFCVisualManager::OnEraseTabsFrame](../Topic/CMFCVisualManager::OnEraseTabsFrame.md)。\)|  
|[CMFCVisualManagerOffice2003::OnFillAutoHideButtonBackground](../Topic/CMFCVisualManagerOffice2003::OnFillAutoHideButtonBackground.md)|在加载自动隐藏按钮的背景时，框架调用此方法。  \(重写 [CMFCVisualManager::OnFillAutoHideButtonBackground](../Topic/CMFCVisualManager::OnFillAutoHideButtonBackground.md)。\)|  
|[CMFCVisualManagerOffice2003::OnFillBarBackground](../Topic/CMFCVisualManagerOffice2003::OnFillBarBackground.md)|在加载 [CBasePane Class](../../mfc/reference/cbasepane-class.md) 对象的背景时，框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnFillBarBackground`。\)|  
|[CMFCVisualManagerOffice2003::OnFillButtonInterior](../Topic/CMFCVisualManagerOffice2003::OnFillButtonInterior.md)|在加载工具栏按钮的背景时，框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnFillButtonInterior`。\)|  
|[CMFCVisualManagerOffice2003::OnFillCommandsListBackground](../Topic/CMFCVisualManagerOffice2003::OnFillCommandsListBackground.md)|框架调用此方法，在加载属于命令快速表工具栏按钮的背景时。  \(重写 `CMFCVisualManagerOfficeXP::OnFillCommandsListBackground`。\)|  
|[CMFCVisualManagerOffice2003::OnFillHeaderCtrlBackground](../Topic/CMFCVisualManagerOffice2003::OnFillHeaderCtrlBackground.md)|在加载报头控件的背景时，框架调用此方法。  \(重写 [CMFCVisualManager::OnFillHeaderCtrlBackground](../Topic/CMFCVisualManager::OnFillHeaderCtrlBackground.md)。\)|  
|[CMFCVisualManagerOffice2003::OnFillHighlightedArea](../Topic/CMFCVisualManagerOffice2003::OnFillHighlightedArea.md)|在加载工具栏按钮的显示区域时，框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnFillHighlightedArea`。\)|  
|[CMFCVisualManagerOffice2003::OnFillOutlookBarCaption](../Topic/CMFCVisualManagerOffice2003::OnFillOutlookBarCaption.md)|在加载 Outlook 标题栏的背景时，框架调用此方法。  \(重写 [CMFCVisualManager::OnFillOutlookBarCaption](../Topic/CMFCVisualManager::OnFillOutlookBarCaption.md)。\)|  
|[CMFCVisualManagerOffice2003::OnFillOutlookPageButton](../Topic/CMFCVisualManagerOffice2003::OnFillOutlookPageButton.md)|在加载 Outlook 页按钮的内部时，框架调用此方法。  \(重写 [CMFCVisualManager::OnFillOutlookPageButton](../Topic/CMFCVisualManager::OnFillOutlookPageButton.md)。\)|  
|[CMFCVisualManagerOffice2003::OnFillPopupWindowBackground](../Topic/CMFCVisualManagerOffice2003::OnFillPopupWindowBackground.md)|在加载弹出窗口的背景时，框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnFillPopupWindowBackground`。\)|  
|[CMFCVisualManagerOffice2003::OnFillTab](../Topic/CMFCVisualManagerOffice2003::OnFillTab.md)|在加载可选窗口的背景时，框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnFillTab`。\)|  
|[CMFCVisualManagerOffice2003::OnFillTasksGroupInterior](../Topic/CMFCVisualManagerOffice2003::OnFillTasksGroupInterior.md)|在加载 [CMFCTasksPaneTaskGroup Class](../../mfc/reference/cmfctaskspanetaskgroup-class.md) 对象的内部时，框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnFillTasksGroupInterior`。\)|  
|[CMFCVisualManagerOffice2003::OnFillTasksPaneBackground](../Topic/CMFCVisualManagerOffice2003::OnFillTasksPaneBackground.md)|在加载 [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md) 控件的背景时，框架调用此方法。  \(重写 [CMFCVisualManager::OnFillTasksPaneBackground](../Topic/CMFCVisualManager::OnFillTasksPaneBackground.md)。\)|  
|[CMFCVisualManagerOffice2003::OnHighlightQuickCustomizeMenuButton](../Topic/CMFCVisualManagerOffice2003::OnHighlightQuickCustomizeMenuButton.md)|当它绘制显示的快速自定义菜单按钮时，框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnHighlightQuickCustomizeMenuButton`。\)|  
|[CMFCVisualManagerOffice2003::OnHighlightRarelyUsedMenuItems](../Topic/CMFCVisualManagerOffice2003::OnHighlightRarelyUsedMenuItems.md)|当它绘制一个突出显示的菜单命令时，框架调用此方法。  \(重写 `CMFCVisualManagerOfficeXP::OnHighlightRarelyUsedMenuItems`。\)|  
|[CMFCVisualManagerOffice2003::OnUpdateSystemColors](../Topic/CMFCVisualManagerOffice2003::OnUpdateSystemColors.md)|当系统颜色更改时，框架调用此函数。  \(重写 `CMFCVisualManagerOfficeXP::OnUpdateSystemColors`。\)|  
|[CMFCVisualManagerOffice2003::SetDefaultWinXPColors](../Topic/CMFCVisualManagerOffice2003::SetDefaultWinXPColors.md)|指定视觉管理器是否应使用从 [GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371)或颜色获取的本机 Windows XP 主题颜色。|  
|[CMFCVisualManagerOffice2003::SetStatusBarOfficeXPLook](../Topic/CMFCVisualManagerOffice2003::SetStatusBarOfficeXPLook.md)|指定应使用 Windows XP 全局主题。|  
|[CMFCVisualManagerOffice2003::SetUseGlobalTheme](../Topic/CMFCVisualManagerOffice2003::SetUseGlobalTheme.md)|指定视觉管理器是使用全局主题。|  
  
## 备注  
 使用 `CMFCVisualManagerOffice2003` 选件类更改应用程序的视觉外观类似于 Microsoft Office 2003。  
  
## 示例  
 下面的示例演示如何设置办公室 2003 视觉管理器。  此代码段是 [桌面通知演示示例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#6](../../mfc/reference/codesnippet/CPP/cmfcvisualmanageroffice2003-class_1.cpp)]  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
 [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)  
  
 [CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)  
  
 [CMFCVisualManagerOffice2003](../../mfc/reference/cmfcvisualmanageroffice2003-class.md)  
  
## 要求  
 **标头：** afxvisualmanageroffice2003.h  
  
## 请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager Class](../../mfc/reference/cmfcvisualmanager-class.md)   
 [CMFCVisualManagerOfficeXP Class](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)   
 [CMFCVisualManagerWindows Class](../../mfc/reference/cmfcvisualmanagerwindows-class.md)   
 [CMFCVisualManager::SetDefaultManager](../Topic/CMFCVisualManager::SetDefaultManager.md)