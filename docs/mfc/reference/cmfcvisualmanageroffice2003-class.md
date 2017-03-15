---
title: "CMFCVisualManagerOffice2003 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCVisualManagerOffice2003
dev_langs:
- C++
helpviewer_keywords:
- CMFCVisualManagerOffice2003 class
ms.assetid: 115482cd-e349-450a-8dc4-c6023d092aab
caps.latest.revision: 31
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: db48c053de741ff37aacf377f338ea4af4d3bec1
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcvisualmanageroffice2003-class"></a>CMFCVisualManagerOffice2003 类
`CMFCVisualManagerOffice2003`向应用程序提供 Microsoft Office 2003 外观。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCVisualManagerOffice2003 : public CMFCVisualManagerOfficeXP  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCVisualManagerOffice2003::DrawComboBorderWinXP](#drawcomboborderwinxp)|绘制使用当前的 Windows XP 主题的组合框边框。 (重写[CMFCVisualManager::DrawComboBorderWinXP](../../mfc/reference/cmfcvisualmanager-class.md#drawcomboborderwinxp)。)|  
|[CMFCVisualManagerOffice2003::DrawComboDropButtonWinXP](#drawcombodropbuttonwinxp)|绘制组合框下拉按钮使用当前的 Windows XP 主题。 (重写[CMFCVisualManager::DrawComboDropButtonWinXP](../../mfc/reference/cmfcvisualmanager-class.md#drawcombodropbuttonwinxp)。)|  
|[CMFCVisualManagerOffice2003::DrawCustomizeButton](#drawcustomizebutton)|绘制自定义按钮。|  
|[CMFCVisualManagerOffice2003::DrawPushButtonWinXP](#drawpushbuttonwinxp)|绘制按钮使用当前的 Windows XP 主题。 (重写[CMFCVisualManager::DrawPushButtonWinXP](../../mfc/reference/cmfcvisualmanager-class.md#drawpushbuttonwinxp)。)|  
|[CMFCVisualManagerOffice2003::GetBaseThemeColor](#getbasethemecolor)|获取基主题颜色。|  
|[CMFCVisualManagerOffice2003::GetHighlightMenuItemColor](#gethighlightmenuitemcolor)|获取用于突出显示的菜单项的颜色。|  
|[CMFCVisualManagerOffice2003::GetPropertyGridGroupColor](#getpropertygridgroupcolor)|框架调用此方法以获取属性列表的背景色。 （重写 `CMFCVisualManagerOfficeXP::GetPropertyGridGroupColor`。）|  
|[CMFCVisualManagerOffice2003::GetPropertyGridGroupTextColor](#getpropertygridgrouptextcolor)|框架调用此方法以检索的属性列表的文本颜色。 （重写 `CMFCVisualManagerOfficeXP::GetPropertyGridGroupTextColor`。）|  
|[CMFCVisualManagerOffice2003::GetShowAllMenuItemsHeight](#getshowallmenuitemsheight)|返回所有菜单项的高度。 (重写[CMFCVisualManager::GetShowAllMenuItemsHeight](../../mfc/reference/cmfcvisualmanager-class.md#getshowallmenuitemsheight)。)|  
|[CMFCVisualManagerOffice2003::GetSmartDockingBaseGuideColors](#getsmartdockingbaseguidecolors)|设置指定的基本组背景色和边框颜色。 （重写 `CMFCVisualManagerOfficeXP::GetSmartDockingBaseGuideColors`。）|  
|[CMFCVisualManagerOffice2003::GetSmartDockingHighlightToneColor](#getsmartdockinghighlighttonecolor)|获取突出显示的色调颜色。 (重写[CMFCVisualManager::GetSmartDockingHighlightToneColor](../../mfc/reference/cmfcvisualmanager-class.md#getsmartdockinghighlighttonecolor)。)|  
|[CMFCVisualManagerOffice2003::GetTabFrameColors](#gettabframecolors)|具有要检索的绘图选项卡窗口的颜色集时，框架将调用此函数。 (重写[CMFCVisualManager::GetTabFrameColors](../../mfc/reference/cmfcvisualmanager-class.md#gettabframecolors)。)|  
|[CMFCVisualManagerOffice2003::GetToolBarCustomizeButtonMargin](#gettoolbarcustomizebuttonmargin)|获取工具栏自定义按钮的边距。 （重写 `CMFCVisualManager::GetToolBarCustomizeButtonMargin`。）|  
|[CMFCVisualManagerOffice2003::GetToolbarDisabledColor](#gettoolbardisabledcolor)|获取用于工具栏已禁用的颜色。 （重写 `CMFCVisualManager::GetToolbarDisabledColor`。）|  
|[CMFCVisualManagerOffice2003::GetToolTipInfo](#gettooltipinfo)|由框架来获取工具提示信息调用。 (重写[CMFCVisualManager::GetToolTipInfo](../../mfc/reference/cmfcvisualmanager-class.md#gettooltipinfo)。)|  
|[CMFCVisualManagerOffice2003::IsDefaultWinXPColorsEnabled](#isdefaultwinxpcolorsenabled)|指示视觉管理器是否使用本机 Windows XP 主题颜色。|  
|[CMFCVisualManagerOffice2003::IsDockingTabHasBorder](#isdockingtabhasborder)|返回当前视觉管理器是否绘制边框停靠和选项卡式窗格。 (重写[CMFCVisualManager::IsDockingTabHasBorder](../../mfc/reference/cmfcvisualmanager-class.md#isdockingtabhasborder)。)|  
|[CMFCVisualManagerOffice2003::IsHighlightOneNoteTabs](#ishighlightonenotetabs)|指示是否应突出显示 OneNote 选项卡。 （重写 `CMFCVisualManager::IsHighlightOneNoteTabs`。）|  
|[CMFCVisualManagerOffice2003::IsOffsetPressedButton](#isoffsetpressedbutton)|绘制一个工具栏按钮时由框架调用。 （重写 `CMFCVisualManager::IsOffsetPressedButton`。）|  
|[CMFCVisualManagerOffice2003::IsStatusBarOfficeXPLook](#isstatusbarofficexplook)|指示是否与 Office XP 外观的状态栏。|  
|[CMFCVisualManagerOffice2003::IsToolbarRoundShape](#istoolbarroundshape)|指示指定的工具栏上是否具有圆形形状。 (重写[CMFCVisualManager::IsToolbarRoundShape](../../mfc/reference/cmfcvisualmanager-class.md#istoolbarroundshape)。)|  
|[CMFCVisualManagerOffice2003::IsUseGlobalTheme](#isuseglobaltheme)|指示是否使用全局 Windows XP 主题。|  
|[CMFCVisualManagerOffice2003::IsWindowsThemingSupported](#iswindowsthemingsupported)|指示是否支持 Windows 主题。 (重写[CMFCVisualManager::IsWindowsThemingSupported](../../mfc/reference/cmfcvisualmanager-class.md#iswindowsthemingsupported)。)|  
|[CMFCVisualManagerOffice2003::OnDrawAutoHideButtonBorder](#ondrawautohidebuttonborder)|框架在绘制自动隐藏按钮的边框时调用此方法。 (重写[CMFCVisualManager::OnDrawAutoHideButtonBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondrawautohidebuttonborder)。)|  
|[CMFCVisualManagerOffice2003::OnDrawBarGripper](#ondrawbargripper)|由框架调用时，它可绘制的控件条的手柄。 （重写 `CMFCVisualManagerOfficeXP::OnDrawBarGripper`。）|  
|[CMFCVisualManagerOffice2003::OnDrawBrowseButton](#ondrawbrowsebutton)|当绘制编辑控件的浏览按钮时，框架将调用此方法。 （重写 `CMFCVisualManagerOfficeXP::OnDrawBrowseButton`。）|  
|[CMFCVisualManagerOffice2003::OnDrawButtonBorder](#ondrawbuttonborder)|当绘制的边框的工具栏按钮时，框架将调用此方法。 （重写 `CMFCVisualManagerOfficeXP::OnDrawButtonBorder`。）|  
|[CMFCVisualManagerOffice2003::OnDrawCaptionBarBorder](#ondrawcaptionbarborder)|框架将调用此方法时，它可绘制的边框[CMFCCaptionBar 类](../../mfc/reference/cmfccaptionbar-class.md)对象。 (重写[CMFCVisualManager::OnDrawCaptionBarBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondrawcaptionbarborder)。)|  
|[CMFCVisualManagerOffice2003::OnDrawCheckBoxEx](#ondrawcheckboxex)|此外，它绘制一个复选框时，框架将调用此方法。 (重写[CMFCVisualManager::OnDrawCheckBoxEx](../../mfc/reference/cmfcvisualmanager-class.md#ondrawcheckboxex)。)|  
|[CMFCVisualManagerOffice2003::OnDrawComboBorder](#ondrawcomboborder)|框架将调用此方法时，它可绘制周围的边框[CMFCToolBarComboBoxButton 类](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)对象。 （重写 `CMFCVisualManagerOfficeXP::OnDrawComboBorder`。）|  
|[CMFCVisualManagerOffice2003::OnDrawComboDropButton](#ondrawcombodropbutton)|框架将调用此方法时，它可绘制下拉按钮的[CMFCToolBarComboBoxButton 类](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)。 （重写 `CMFCVisualManagerOfficeXP::OnDrawComboDropButton`。）|  
|[CMFCVisualManagerOffice2003::OnDrawControlBorder](#ondrawcontrolborder)|框架将调用此方法时，它可绘制控件的边框。 (重写[CMFCVisualManager::OnDrawControlBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondrawcontrolborder)。)|  
|[CMFCVisualManagerOffice2003::OnDrawExpandingBox](#ondrawexpandingbox)|在扩展的框中，它可绘制时，框架将调用此方法。 (重写[CMFCVisualManager::OnDrawExpandingBox](../../mfc/reference/cmfcvisualmanager-class.md#ondrawexpandingbox)。)|  
|[CMFCVisualManagerOffice2003::OnDrawHeaderCtrlBorder](#ondrawheaderctrlborder)|在其周围绘制边框的实例时，框架将调用此方法[CMFCHeaderCtrl 类](../../mfc/reference/cmfcheaderctrl-class.md)。 (重写[CMFCVisualManager::OnDrawHeaderCtrlBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondrawheaderctrlborder)。)|  
|[CMFCVisualManagerOffice2003::OnDrawMenuBorder](#ondrawmenuborder)|框架将调用此方法时，它可绘制的边框[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)。 （重写 `CMFCVisualManagerOfficeXP::OnDrawMenuBorder`。）|  
|[CMFCVisualManagerOffice2003::OnDrawOutlookBarSplitter](#ondrawoutlookbarsplitter)|当它绘制为 Outlook 栏拆分器时，框架将调用此方法。 (重写[CMFCVisualManager::OnDrawOutlookBarSplitter](../../mfc/reference/cmfcvisualmanager-class.md#ondrawoutlookbarsplitter)。)|  
|[CMFCVisualManagerOffice2003::OnDrawOutlookPageButtonBorder](#ondrawoutlookpagebuttonborder)|由框架调用时，它可绘制 Outlook 页面按钮的边框。 (重写[CMFCVisualManager::OnDrawOutlookPageButtonBorder](../../mfc/reference/cmfcvisualmanager-class.md#ondrawoutlookpagebuttonborder)。)|  
|[CMFCVisualManagerOffice2003::OnDrawPaneBorder](#ondrawpaneborder)|框架将调用此方法时，它可绘制的边框[CPane 类](../../mfc/reference/cpane-class.md)对象。 （重写 `CMFCVisualManagerOfficeXP::OnDrawPaneBorder`。）|  
|[CMFCVisualManagerOffice2003::OnDrawPaneCaption](#ondrawpanecaption)|框架将调用此方法时，它可绘制的标题[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)对象。 （重写 `CMFCVisualManagerOfficeXP::OnDrawPaneCaption`。）|  
|[CMFCVisualManagerOffice2003::OnDrawPopupWindowBorder](#ondrawpopupwindowborder)|当绘制的边框的弹出窗口时，框架将调用此方法。 （重写 `CMFCVisualManagerOfficeXP::OnDrawPopupWindowBorder`。）|  
|[CMFCVisualManagerOffice2003::OnDrawPopupWindowButtonBorder](#ondrawpopupwindowbuttonborder)|当它在弹出窗口中绘制的边框的按钮时，框架将调用此方法。 （重写 `CMFCVisualManagerOfficeXP::OnDrawPopupWindowButtonBorder`。）|  
|[CMFCVisualManagerOffice2003::OnDrawPopupWindowCaption](#ondrawpopupwindowcaption)|框架将调用此方法时，它可绘制一个弹出窗口的标题。 （重写 `CMFCVisualManagerOfficeXP::OnDrawPopupWindowCaption`。）|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonButtonsGroup](#ondrawribbonbuttonsgroup)|在功能区上，它绘制一组按钮时，框架将调用此方法。 (重写[CMFCVisualManager::OnDrawRibbonButtonsGroup](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonbuttonsgroup)。)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonCategoryCaption](#ondrawribboncategorycaption)|在功能区类别的标题栏，它可绘制时，框架将调用此方法。 (重写[CMFCVisualManager::OnDrawRibbonCategoryCaption](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncategorycaption)。)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonCategoryTab](#ondrawribboncategorytab)|当绘制一个功能区类别的选项卡时，框架将调用此方法。 (重写[CMFCVisualManager::OnDrawRibbonCategoryTab](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribboncategorytab)。)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonProgressBar](#ondrawribbonprogressbar)|框架将调用此方法时，它可绘制[CMFCRibbonProgressBar 类](../../mfc/reference/cmfcribbonprogressbar-class.md)。 (重写[CMFCVisualManager::OnDrawRibbonProgressBar](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonprogressbar)。)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonQuickAccessToolBarSeparator](#ondrawribbonquickaccesstoolbarseparator)|在功能区快速访问工具栏上，它绘制分隔符时，框架将调用此方法。 （重写 `CMFCVisualManagerOfficeXP::OnDrawRibbonQuickAccessToolBarSeparator`。）|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonSliderChannel](#ondrawribbonsliderchannel)|框架将调用此方法时，它可绘制的通道[CMFCRibbonSlider 类](../../mfc/reference/cmfcribbonslider-class.md)。 (重写[CMFCVisualManager::OnDrawRibbonSliderChannel](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderchannel)。)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonSliderThumb](#ondrawribbonsliderthumb)|框架将调用此方法时，它可绘制的 thumb [CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md)对象。 (重写[CMFCVisualManager::OnDrawRibbonSliderThumb](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderthumb)。)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonSliderZoomButton](#ondrawribbonsliderzoombutton)|框架将调用此方法时，它可绘制的缩放按钮[CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md)对象。 (重写[CMFCVisualManager::OnDrawRibbonSliderZoomButton](../../mfc/reference/cmfcvisualmanager-class.md#ondrawribbonsliderzoombutton)。)|  
|[CMFCVisualManagerOffice2003::OnDrawRibbonStatusBarPane](#ondrawribbonstatusbarpane)|当它在状态栏上绘制一个窗格时，框架将调用此方法。 （重写 `CMFCVisualManagerOfficeXP::OnDrawRibbonStatusBarPane`。）|  
|[CMFCVisualManagerOffice2003::OnDrawScrollButtons](#ondrawscrollbuttons)|当绘制滚动按钮时，框架将调用此方法。 （重写 `CMFCVisualManagerOfficeXP::OnDrawScrollButtons`。）|  
|[CMFCVisualManagerOffice2003::OnDrawSeparator](#ondrawseparator)|当绘制分隔符时，框架将调用此方法。 （重写 `CMFCVisualManagerOfficeXP::OnDrawSeparator`。）|  
|[CMFCVisualManagerOffice2003::OnDrawShowAllMenuItems](#ondrawshowallmenuitems)|在菜单中，它绘制的所有项时，框架将调用此方法。 (重写[CMFCVisualManager::OnDrawShowAllMenuItems](../../mfc/reference/cmfcvisualmanager-class.md#ondrawshowallmenuitems)。)|  
|[CMFCVisualManagerOffice2003::OnDrawStatusBarPaneBorder](#ondrawstatusbarpaneborder)|框架将调用此方法时，它可绘制的边框[CMFCStatusBar 类](../../mfc/reference/cmfcstatusbar-class.md)对象。 （重写 `CMFCVisualManagerOfficeXP::OnDrawStatusBarPaneBorder`。）|  
|[CMFCVisualManagerOffice2003::OnDrawStatusBarProgress](#ondrawstatusbarprogress)|框架将调用此方法在其上绘制的进度指示器时[CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)对象。 (重写[CMFCVisualManager::OnDrawStatusBarProgress](../../mfc/reference/cmfcvisualmanager-class.md#ondrawstatusbarprogress)。)|  
|[CMFCVisualManagerOffice2003::OnDrawStatusBarSizeBox](#ondrawstatusbarsizebox)|框架将调用此方法时，它可绘制的大小框[CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)。 (重写[CMFCVisualManager::OnDrawStatusBarSizeBox](../../mfc/reference/cmfcvisualmanager-class.md#ondrawstatusbarsizebox)。)|  
|[CMFCVisualManagerOffice2003::OnDrawTab](#ondrawtab)|框架将调用此方法时，它可绘制选项卡[CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)对象。 （重写 `CMFCVisualManagerOfficeXP::OnDrawTab`。）|  
|[CMFCVisualManagerOffice2003::OnDrawTabsButtonBorder](#ondrawtabsbuttonborder)|框架将调用此方法时，它可绘制选项卡按钮的边框。 （重写 `CMFCVisualManagerOfficeXP::OnDrawTabsButtonBorder`。）|  
|[CMFCVisualManagerOffice2003::OnDrawTask](#ondrawtask)|框架将调用此方法时，它可绘制[CMFCTasksPaneTask 类](../../mfc/reference/cmfctaskspanetask-class.md)对象。 （重写 `CMFCVisualManagerOfficeXP::OnDrawTask`。）|  
|[CMFCVisualManagerOffice2003::OnDrawTasksGroupAreaBorder](#ondrawtasksgroupareaborder)|框架将调用此方法在其上绘制一组周围边框时[CMFCTasksPane 类](../../mfc/reference/cmfctaskspane-class.md)对象。 （重写 `CMFCVisualManagerOfficeXP::OnDrawTasksGroupAreaBorder`。）|  
|[CMFCVisualManagerOffice2003::OnDrawTasksGroupCaption](#ondrawtasksgroupcaption)|框架将调用此方法时，它可绘制的标题[CMFCTasksPaneTaskGroup 类](../../mfc/reference/cmfctaskspanetaskgroup-class.md)对象。 （重写 `CMFCVisualManagerOfficeXP::OnDrawTasksGroupCaption`。）|  
|[CMFCVisualManagerOffice2003::OnDrawTearOffCaption](#ondrawtearoffcaption)|框架将调用此方法时，它可绘制的标题[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)对象。 （重写 `CMFCVisualManagerOfficeXP::OnDrawTearOffCaption`。）|  
|[CMFCVisualManagerOffice2003::OnErasePopupWindowButton](#onerasepopupwindowbutton)|它将擦除弹出窗口中的按钮时，框架将调用此方法。 （重写 `CMFCVisualManagerOfficeXP::OnErasePopupWindowButton`。）|  
|[CMFCVisualManagerOffice2003::OnEraseTabsArea](#onerasetabsarea)|它将擦除的选项卡窗口选项卡区域时，框架将调用此方法。 （重写 `CMFCVisualManagerOfficeXP::OnEraseTabsArea`。）|  
|[CMFCVisualManagerOffice2003::OnEraseTabsButton](#onerasetabsbutton)|它将擦除的文本和图标的选项卡按钮时，框架将调用此方法。 （重写 `CMFCVisualManagerOfficeXP::OnEraseTabsButton`。）|  
|[CMFCVisualManagerOffice2003::OnEraseTabsFrame](#onerasetabsframe)|框架将调用此方法时它将一个帧擦除上[CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)。 (重写[CMFCVisualManager::OnEraseTabsFrame](../../mfc/reference/cmfcvisualmanager-class.md#onerasetabsframe)。)|  
|[CMFCVisualManagerOffice2003::OnFillAutoHideButtonBackground](#onfillautohidebuttonbackground)|框架在填充自动隐藏按钮的背景时调用此方法。 (重写[CMFCVisualManager::OnFillAutoHideButtonBackground](../../mfc/reference/cmfcvisualmanager-class.md#onfillautohidebuttonbackground)。)|  
|[CMFCVisualManagerOffice2003::OnFillBarBackground](#onfillbarbackground)|框架将调用此方法时填充的背景的[CBasePane 类](../../mfc/reference/cbasepane-class.md)对象。 （重写 `CMFCVisualManagerOfficeXP::OnFillBarBackground`。）|  
|[CMFCVisualManagerOffice2003::OnFillButtonInterior](#onfillbuttoninterior)|填充工具栏按钮的背景时，框架将调用此方法。 （重写 `CMFCVisualManagerOfficeXP::OnFillButtonInterior`。）|  
|[CMFCVisualManagerOffice2003::OnFillCommandsListBackground](#onfillcommandslistbackground)|填充属于命令列表的工具栏按钮的背景时，框架将调用此方法。 （重写 `CMFCVisualManagerOfficeXP::OnFillCommandsListBackground`。）|  
|[CMFCVisualManagerOffice2003::OnFillHeaderCtrlBackground](#onfillheaderctrlbackground)|填充标头控件的背景时，框架将调用此方法。 (重写[CMFCVisualManager::OnFillHeaderCtrlBackground](../../mfc/reference/cmfcvisualmanager-class.md#onfillheaderctrlbackground)。)|  
|[CMFCVisualManagerOffice2003::OnFillHighlightedArea](#onfillhighlightedarea)|填充工具栏按钮的突出显示的区域时，框架将调用此方法。 （重写 `CMFCVisualManagerOfficeXP::OnFillHighlightedArea`。）|  
|[CMFCVisualManagerOffice2003::OnFillOutlookBarCaption](#onfilloutlookbarcaption)|当它填满一个 Outlook 的标题栏的背景，框架将调用此方法。 (重写[CMFCVisualManager::OnFillOutlookBarCaption](../../mfc/reference/cmfcvisualmanager-class.md#onfilloutlookbarcaption)。)|  
|[CMFCVisualManagerOffice2003::OnFillOutlookPageButton](#onfilloutlookpagebutton)|填充内部 Outlook 页面按钮时，框架将调用此方法。 (重写[CMFCVisualManager::OnFillOutlookPageButton](../../mfc/reference/cmfcvisualmanager-class.md#onfilloutlookpagebutton)。)|  
|[CMFCVisualManagerOffice2003::OnFillPopupWindowBackground](#onfillpopupwindowbackground)|填充背景的弹出窗口时，框架将调用此方法。 （重写 `CMFCVisualManagerOfficeXP::OnFillPopupWindowBackground`。）|  
|[CMFCVisualManagerOffice2003::OnFillTab](#onfilltab)|填充选项卡窗口的背景时，框架将调用此方法。 （重写 `CMFCVisualManagerOfficeXP::OnFillTab`。）|  
|[CMFCVisualManagerOffice2003::OnFillTasksGroupInterior](#onfilltasksgroupinterior)|框架将调用此方法时填充的内部[CMFCTasksPaneTaskGroup 类](../../mfc/reference/cmfctaskspanetaskgroup-class.md)对象。 （重写 `CMFCVisualManagerOfficeXP::OnFillTasksGroupInterior`。）|  
|[CMFCVisualManagerOffice2003::OnFillTasksPaneBackground](#onfilltaskspanebackground)|框架将调用此方法时填充的背景的[CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)控件。 (重写[CMFCVisualManager::OnFillTasksPaneBackground](../../mfc/reference/cmfcvisualmanager-class.md#onfilltaskspanebackground)。)|  
|[CMFCVisualManagerOffice2003::OnHighlightQuickCustomizeMenuButton](#onhighlightquickcustomizemenubutton)|框架将调用此方法时，它可绘制突出显示快速的自定义菜单按钮。 （重写 `CMFCVisualManagerOfficeXP::OnHighlightQuickCustomizeMenuButton`。）|  
|[CMFCVisualManagerOffice2003::OnHighlightRarelyUsedMenuItems](#onhighlightrarelyusedmenuitems)|当绘制突出显示的菜单命令时，框架将调用此方法。 （重写 `CMFCVisualManagerOfficeXP::OnHighlightRarelyUsedMenuItems`。）|  
|[CMFCVisualManagerOffice2003::OnUpdateSystemColors](#onupdatesystemcolors)|系统颜色更改时，框架将调用此函数。 （重写 `CMFCVisualManagerOfficeXP::OnUpdateSystemColors`。）|  
|[CMFCVisualManagerOffice2003::SetDefaultWinXPColors](#setdefaultwinxpcolors)|指定是否视觉管理器应使用本机 Windows XP 主题颜色或颜色从获取[GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371)。|  
|[CMFCVisualManagerOffice2003::SetStatusBarOfficeXPLook](#setstatusbarofficexplook)|指定应使用 Windows XP 全局主题。|  
|[CMFCVisualManagerOffice2003::SetUseGlobalTheme](#setuseglobaltheme)|指定的可视化管理器是否使用全局主题。|  
  
## <a name="remarks"></a>备注  
 您使用`CMFCVisualManagerOffice2003`类，以更改您的应用程序类似于 Microsoft Office 2003 的可视外观。  
  
## <a name="example"></a>示例  
 下面的示例演示如何设置 office 2003 视觉管理器。 此代码段属于[桌面警报演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo #&6;](../../mfc/reference/codesnippet/cpp/cmfcvisualmanageroffice2003-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
 [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)  
  
 [CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)  
  
 [CMFCVisualManagerOffice2003](../../mfc/reference/cmfcvisualmanageroffice2003-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxvisualmanageroffice2003.h  
  
##  <a name="a-namedrawcomboborderwinxpa--cmfcvisualmanageroffice2003drawcomboborderwinxp"></a><a name="drawcomboborderwinxp"></a>CMFCVisualManagerOffice2003::DrawComboBorderWinXP  
 绘制使用当前的 Windows XP 主题的组合框边框。  
  
```  
virtual BOOL DrawComboBorderWinXP(
    CDC* pDC,  
    CRect rect,  
    BOOL bDisabled,  
    BOOL bIsDropped,  
    BOOL bIsHighlighted);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 组合框边框的边框。  
  
 [in] `bDisabled`  
 指定是否禁用组合框边框。  
  
 [in] `bIsDropped`  
 指定是否向下删除组合框边框。  
  
 [in] `bIsHighlighted`  
 指定组合框边框将突出显示。  
  
### <a name="return-value"></a>返回值  
 返回`TRUE`如果启用主题 API 或`FALSE`如果不是。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namedrawcombodropbuttonwinxpa--cmfcvisualmanageroffice2003drawcombodropbuttonwinxp"></a><a name="drawcombodropbuttonwinxp"></a>CMFCVisualManagerOffice2003::DrawComboDropButtonWinXP  
 绘制组合框下拉按钮使用当前的 Windows XP 主题。  
  
```  
virtual BOOL DrawComboDropButtonWinXP(
    CDC* pDC,  
    CRect rect,  
    BOOL bDisabled,  
    BOOL bIsDropped,  
    BOOL bIsHighlighted);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 组合框下拉按钮的边框。  
  
 [in] `bDisabled`  
 指定是否禁用组合框下拉按钮。  
  
 [in] `bIsDropped`  
 指定是否向下删除组合框下拉按钮。  
  
 [in] `bIsHighlighted`  
 指定组合框下拉按钮将突出显示。  
  
### <a name="return-value"></a>返回值  
 返回`TRUE`如果启用主题 API 或`FALSE`如果不是。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namedrawcustomizebuttona--cmfcvisualmanageroffice2003drawcustomizebutton"></a><a name="drawcustomizebutton"></a>CMFCVisualManagerOffice2003::DrawCustomizeButton  
 绘制自定义按钮。  
  
```  
virtual void DrawCustomizeButton(
    CDC* pDC,  
    CRect rect,  
    BOOL bIsHorz,  
    CMFCVisualManager::AFX_BUTTON_STATE state,  
    BOOL bIsCustomize,  
    BOOL bIsMoreButtons);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向显示上下文的指针。  
  
 [in] `rect`  
 该按钮的边界的矩形  
  
 [in] `bIsHorz`  
 `TRUE`如果该按钮是水平的或`FALSE`如果它是垂直的。  
  
 [in] `state`  
 它与按钮的状态是要绘制 （常规、 按下或突出显示）。  
  
 [in] `bIsCustomize`  
 `TRUE`如果应在按钮的矩形中绘制自定义向下的箭头或箭头键向左映像或`FALSE`如果不是。  
  
 [in] `bIsMoreButtons`  
 `TRUE`如果水平或垂直自定义更多按钮应该在按钮的矩形中绘制图像或`FALSE`如果不是。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namedrawpushbuttonwinxpa--cmfcvisualmanageroffice2003drawpushbuttonwinxp"></a><a name="drawpushbuttonwinxp"></a>CMFCVisualManagerOffice2003::DrawPushButtonWinXP  
 绘制按钮使用当前的 Windows XP 主题。  
  
```  
virtual BOOL DrawPushButtonWinXP(
    CDC* pDC,  
    CRect rect,  
    CMFCButton* pButton,  
    UINT uiState);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 推送按钮的边框。  
  
 [in] `pButton`  
 一个指向[CMFCButton 类](../../mfc/reference/cmfcbutton-class.md)对象来绘制。  
  
 [in] `uiState`  
 已忽略。 状态取自`pButton`。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果启用 Theme API;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetbasethemecolora--cmfcvisualmanageroffice2003getbasethemecolor"></a><a name="getbasethemecolor"></a>CMFCVisualManagerOffice2003::GetBaseThemeColor  
 获取基主题颜色。  
  
```  
virtual COLORREF GetBaseThemeColor();
```  
  
### <a name="return-value"></a>返回值  
 返回基的主题中，如果一个参数设置的主题颜色条表面颜色。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegethighlightmenuitemcolora--cmfcvisualmanageroffice2003gethighlightmenuitemcolor"></a><a name="gethighlightmenuitemcolor"></a>CMFCVisualManagerOffice2003::GetHighlightMenuItemColor  
 获取用于突出显示的菜单项的颜色。  
  
```  
virtual COLORREF GetHighlightMenuItemColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回用于突出显示的菜单项的颜色。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetpropertygridgroupcolora--cmfcvisualmanageroffice2003getpropertygridgroupcolor"></a><a name="getpropertygridgroupcolor"></a>CMFCVisualManagerOffice2003::GetPropertyGridGroupColor  
 框架调用此方法以获取属性列表的背景色。  
  
```  
virtual COLORREF GetPropertyGridGroupColor(CMFCPropertyGridCtrl* pPropList);
```  
  
### <a name="parameters"></a>参数  
 [in] `pPropList`  
 一个指向绘制框架的属性列表。  
  
### <a name="return-value"></a>返回值  
 返回的背景色`pPropList`。  
  
### <a name="remarks"></a>备注  
 重写此函数可自定义您的应用程序中的属性列表的背景色。  
  
##  <a name="a-namegetpropertygridgrouptextcolora--cmfcvisualmanageroffice2003getpropertygridgrouptextcolor"></a><a name="getpropertygridgrouptextcolor"></a>CMFCVisualManagerOffice2003::GetPropertyGridGroupTextColor  
 框架调用此方法以检索的属性列表的文本颜色。  
  
```  
virtual COLORREF GetPropertyGridGroupTextColor(CMFCPropertyGridCtrl* pPropList);
```  
  
### <a name="parameters"></a>参数  
 [in] `pPropList`  
 指向属性列表的指针。  
  
### <a name="return-value"></a>返回值  
 返回指定的属性列表的文本颜色。  
  
### <a name="remarks"></a>备注  
 重写此函数可自定义您的应用程序中的属性列表的文本颜色。  
  
##  <a name="a-namegetshowallmenuitemsheighta--cmfcvisualmanageroffice2003getshowallmenuitemsheight"></a><a name="getshowallmenuitemsheight"></a>CMFCVisualManagerOffice2003::GetShowAllMenuItemsHeight  
 返回所有菜单项的高度。  
  
```  
virtual int GetShowAllMenuItemsHeight(
    CDC* pDC,  
    const CSize& sizeDefault);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向设备上下文的指针。  
  
 [in] `sizeDefault`  
 默认菜单大小。  
  
### <a name="return-value"></a>返回值  
 默认情况下，返回所有菜单图像加上边距的高度。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetsmartdockingbaseguidecolorsa--cmfcvisualmanageroffice2003getsmartdockingbaseguidecolors"></a><a name="getsmartdockingbaseguidecolors"></a>CMFCVisualManagerOffice2003::GetSmartDockingBaseGuideColors  
 设置指定的基本组背景色和边框颜色。  
  
```  
virtual void GetSmartDockingBaseGuideColors(
    COLORREF& clrBaseGroupBackground,  
    COLORREF& clrBaseGroupBorder);
```  
  
### <a name="parameters"></a>参数  
 [in] `clrBaseGroupBackground`  
 引用[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)将设置为背景颜色。  
  
 [in] `clrBaseGroupBorder`  
 引用[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)将设置为边框颜色。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetsmartdockinghighlighttonecolora--cmfcvisualmanageroffice2003getsmartdockinghighlighttonecolor"></a><a name="getsmartdockinghighlighttonecolor"></a>CMFCVisualManagerOffice2003::GetSmartDockingHighlightToneColor  
 返回突出显示的色调颜色。  
  
```  
virtual COLORREF GetSmartDockingHighlightToneColor();
```  
  
### <a name="return-value"></a>返回值  
 返回[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) ，其中包含突出显示的色调颜色。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegettabframecolorsa--cmfcvisualmanageroffice2003gettabframecolors"></a><a name="gettabframecolors"></a>CMFCVisualManagerOffice2003::GetTabFrameColors  
 具有要检索的绘图选项卡窗口的颜色集时，框架将调用此函数。  
  
```  
virtual void GetTabFrameColors(
    const CMFCBaseTabCtrl* pTabWnd,  
    COLORREF& clrDark,  
    COLORREF& clrBlack,  
    COLORREF& clrHighlight,  
    COLORREF& clrFace,  
    COLORREF& clrDarkShadow,  
    COLORREF& clrLight,  
    CBrush*& pbrFace,  
    CBrush*& pbrBlack);
```  
  
### <a name="parameters"></a>参数  
 [in] `pTabWnd`  
 指向框架在其中绘制一个选项卡选项卡式窗口的指针。  
  
 [out] `clrDark`  
 对引用[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)参数，此方法会将存储的选项卡的深边框的颜色。  
  
 [out] `clrBlack`  
 对引用`COLORREF`参数，此方法将存储的选项卡窗口边框的颜色。 边框的默认颜色为黑色。  
  
 [out] `clrHighlight`  
 对引用`COLORREF`参数，此方法会将存储选项卡窗口中的突出显示状态的颜色。  
  
 [out] `clrFace`  
 对引用`COLORREF`此方法存储选项卡窗口中的字体的颜色的位置的参数。  
  
 [out] `clrDarkShadow`  
 对引用`COLORREF`参数，此方法会将存储选项卡窗口中的阴影颜色。  
  
 [out] `clrLight`  
 对引用`COLORREF`参数，此方法会将存储选项卡窗口中的浅边缘的颜色。  
  
 [out] `pbrFace`  
 画笔的引用指向的指针。 此方法将存储的画笔，使用它来填充此参数中的选项卡窗口的外观。  
  
 [out] `pbrBlack`  
 画笔的引用指向的指针。 此方法将存储它使用以填充此参数中的选项卡窗口的黑色边缘的画笔。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegettoolbarcustomizebuttonmargina--cmfcvisualmanageroffice2003gettoolbarcustomizebuttonmargin"></a><a name="gettoolbarcustomizebuttonmargin"></a>CMFCVisualManagerOffice2003::GetToolBarCustomizeButtonMargin  
 获取工具栏自定义按钮的边距。  
  
```  
virtual int GetToolBarCustomizeButtonMargin() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回工具栏自定义按钮的边距。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegettoolbardisabledcolora--cmfcvisualmanageroffice2003gettoolbardisabledcolor"></a><a name="gettoolbardisabledcolor"></a>CMFCVisualManagerOffice2003::GetToolbarDisabledColor  
 获取用于工具栏已禁用的颜色。  
  
```  
virtual COLORREF GetToolbarDisabledColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) ，其中包含已禁用的颜色。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegettooltipinfoa--cmfcvisualmanageroffice2003gettooltipinfo"></a><a name="gettooltipinfo"></a>CMFCVisualManagerOffice2003::GetToolTipInfo  
 由框架来获取工具提示信息调用。  
  
```  
virtual BOOL GetToolTipInfo(
    CMFCToolTipInfo& params,  
    UINT nType = (UINT)(-1));
```  
  
### <a name="parameters"></a>参数  
 [out] `params`  
 对引用[CMFCToolTipInfo 类](../../mfc/reference/cmfctooltipinfo-class.md)，此方法所返回的工具提示信息对象。  
  
 [in] `nType`  
 键入工具提示信息要返回的信息。  
  
### <a name="return-value"></a>返回值  
 返回`TRUE`如果返回的工具提示信息，并`FALSE`否则为。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameisdefaultwinxpcolorsenableda--cmfcvisualmanageroffice2003isdefaultwinxpcolorsenabled"></a><a name="isdefaultwinxpcolorsenabled"></a>CMFCVisualManagerOffice2003::IsDefaultWinXPColorsEnabled  
 指示视觉管理器是否使用本机 Windows XP 的主题颜色。  
  
```  
static BOOL IsDefaultWinXPColorsEnabled();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果可视化管理器使用本机颜色;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 有关本机颜色的详细信息，请参阅[CMFCVisualManagerOffice2003::SetDefaultWinXPColors](#setdefaultwinxpcolors)。  
  
##  <a name="a-nameisdockingtabhasbordera--cmfcvisualmanageroffice2003isdockingtabhasborder"></a><a name="isdockingtabhasborder"></a>CMFCVisualManagerOffice2003::IsDockingTabHasBorder  
 返回当前视觉管理器是否绘制边框停靠和选项卡式窗格。  
  
```  
virtual BOOL IsDockingTabHasBorder();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果可视化管理器绘制窗格停靠和选项卡式; 周围的边框`FALSE`否则为。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameishighlightonenotetabsa--cmfcvisualmanageroffice2003ishighlightonenotetabs"></a><a name="ishighlightonenotetabs"></a>CMFCVisualManagerOffice2003::IsHighlightOneNoteTabs  
 指示是否应突出显示 OneNote 选项卡。  
  
```  
virtual BOOL IsHighlightOneNoteTabs() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameisoffsetpressedbuttona--cmfcvisualmanageroffice2003isoffsetpressedbutton"></a><a name="isoffsetpressedbutton"></a>CMFCVisualManagerOffice2003::IsOffsetPressedButton  
 绘制一个工具栏按钮时由框架调用。  
  
```  
virtual BOOL IsOffsetPressedButton() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 默认实现返回 `FALSE`。  
  
##  <a name="a-nameisstatusbarofficexplooka--cmfcvisualmanageroffice2003isstatusbarofficexplook"></a><a name="isstatusbarofficexplook"></a>CMFCVisualManagerOffice2003::IsStatusBarOfficeXPLook  
 指示是否与 Office XP 外观的状态栏。  
  
```  
static BOOL __stdcall IsStatusBarOfficeXPLook();
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 返回`TRUE`是否存在与 Office XP 的外观，状态栏或`FALSE`如果不是。  
  
##  <a name="a-nameistoolbarroundshapea--cmfcvisualmanageroffice2003istoolbarroundshape"></a><a name="istoolbarroundshape"></a>CMFCVisualManagerOffice2003::IsToolbarRoundShape  
 指示指定的工具栏是否倒圆角。  
  
```  
virtual BOOL IsToolbarRoundShape(CMFCToolBar* pToolBar);
```  
  
### <a name="parameters"></a>参数  
 [in] `pToolBar`  
 指针，指向问题工具栏。  
  
### <a name="return-value"></a>返回值  
 返回`TRUE`工具栏是圆的如果或`FALSE`是否菜单栏。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameisuseglobalthemea--cmfcvisualmanageroffice2003isuseglobaltheme"></a><a name="isuseglobaltheme"></a>CMFCVisualManagerOffice2003::IsUseGlobalTheme  
 指示您的应用程序是否使用 Windows XP 主题。  
  
```  
static BOOL IsUseGlobalTheme();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果可视化管理器使用了 Windows XP 主题;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 使用方法[CMFCVisualManagerOffice2003::SetUseGlobalTheme](#setuseglobaltheme)若要让可视化管理器使用 Windows XP 主题。  
  
##  <a name="a-nameiswindowsthemingsupporteda--cmfcvisualmanageroffice2003iswindowsthemingsupported"></a><a name="iswindowsthemingsupported"></a>CMFCVisualManagerOffice2003::IsWindowsThemingSupported  
 指示是否支持 Windows 主题。  
  
```  
virtual BOOL IsWindowsThemingSupported() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回`TRUE`如果支持 Windows 主题，或`FALSE`如果不是。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameondrawautohidebuttonbordera--cmfcvisualmanageroffice2003ondrawautohidebuttonborder"></a><a name="ondrawautohidebuttonborder"></a>CMFCVisualManagerOffice2003::OnDrawAutoHideButtonBorder  
 框架在绘制自动隐藏按钮的边框时调用此方法。  
  
```  
virtual void OnDrawAutoHideButtonBorder(
    CDC* pDC,  
    CRect rectBounds,  
    CRect rectBorderSize,  
    CMFCAutoHideButton* pButton);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rectBounds`  
 大小和位置的自动隐藏按钮。  
  
 [in] `rectBorderSize`  
 边框的大小。  
  
 [in] `pButton`  
 一个指向自动隐藏按钮。 框架在绘制此按钮的边框。  
  
### <a name="remarks"></a>备注  
 如果你想要自定义一个自动隐藏按钮的边框的外观，重写此方法在派生类中。 默认情况下，此方法填充具有您的应用程序的默认阴影颜色的平面边框。  
  
 `rectBorderSize`参数不包含边框的坐标。 它包含在边框的大小`top`， `bottom`， `left`，和`right`数据成员。 一个值小于或等于 0 指示该侧的自动隐藏按钮无边框。  
  
##  <a name="a-nameondrawbargrippera--cmfcvisualmanageroffice2003ondrawbargripper"></a><a name="ondrawbargripper"></a>CMFCVisualManagerOffice2003::OnDrawBarGripper  
 由框架调用时，它可绘制的控件条的手柄。  
  
```  
virtual void OnDrawBarGripper(
    CDC* pDC,  
    CRect rectGripper,  
    BOOL bHorz,  
    CBasePane* pBar);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向控件条的设备上下文的指针。  
  
 [in] `rectGripper`  
 控件条的边框。  
  
 [in] `bHorz`  
 一个布尔型参数，指定水平或垂直是否停靠控件条。  
  
 [in] `pBar`  
 控件条的指针。 可视化管理器绘制此控件条的控制手柄。  
  
### <a name="remarks"></a>备注  
 此方法的默认实现将显示标准的控制手柄。 若要自定义控制手柄的外观，请重写此方法在从派生的自定义类[CMFCVisualManagerOffice2003](../../mfc/reference/cmfcvisualmanageroffice2003-class.md)类。  
  
##  <a name="a-nameondrawbrowsebuttona--cmfcvisualmanageroffice2003ondrawbrowsebutton"></a><a name="ondrawbrowsebutton"></a>CMFCVisualManagerOffice2003::OnDrawBrowseButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnDrawBrowseButton(
    CDC* pDC,  
    CRect rect,  
    CMFCEditBrowseCtrl* pEdit,  
    CMFCVisualManager::AFX_BUTTON_STATE state,  
    COLORREF& clrText);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 [in] `rect`  
 [in] `pEdit`  
 [in] `state`  
 [in] `clrText`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameondrawbuttonbordera--cmfcvisualmanageroffice2003ondrawbuttonborder"></a><a name="ondrawbuttonborder"></a>CMFCVisualManagerOffice2003::OnDrawButtonBorder  
 当绘制的边框的工具栏按钮时，框架将调用此方法。  
  
```  
virtual void OnDrawButtonBorder(
    CDC* pDC,  
    CMFCToolBarButton* pButton,  
    CRect rect,  
    CMFCVisualManager::AFX_BUTTON_STATE state);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向一个工具栏按钮的设备上下文的指针。  
  
 [in] `pButton`  
 一个指向工具栏按钮。 框架将绘制此按钮的边框。  
  
 [in] `rect`  
 一个指定工具栏按钮的边界的矩形。  
  
 [in] `state`  
 枚举的数据类型，指定工具栏按钮的当前状态。  
  
### <a name="remarks"></a>备注  
 此方法的默认实现将显示标准的边框。 重写此方法在派生的视觉管理器自定义工具栏按钮的边框的外观。  
  
 工具栏按钮的可能的状态为`ButtonsIsRegular`， `ButtonsIsPressed`，或`ButtonsIsHighlighted`。  
  
##  <a name="a-nameondrawcaptionbarbordera--cmfcvisualmanageroffice2003ondrawcaptionbarborder"></a><a name="ondrawcaptionbarborder"></a>CMFCVisualManagerOffice2003::OnDrawCaptionBarBorder  
 框架将调用此方法时，它可绘制的边框[CMFCCaptionBar 类](../../mfc/reference/cmfccaptionbar-class.md)对象。  
  
```  
virtual void OnDrawCaptionBarBorder(
    CDC* pDC,  
    CMFCCaptionBar* pBar,  
    CRect rect,  
    COLORREF clrBarBorder,  
    BOOL bFlatBorder);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `pBar`  
 一个指向[CMFCCaptionBar 类](../../mfc/reference/cmfccaptionbar-class.md)对象。 框架将绘制此标题栏。  
  
 [in] `rect`  
 一个指定的标题栏的边界的矩形。  
  
 [in] `clrBarBorder`  
 边框的颜色。  
  
 [in] `bFlatBorder`  
 `TRUE`如果边框应有外观平面、 2D，或`FALSE`如果不是。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生类可以自定义标题栏的边框外观。  
  
##  <a name="a-nameondrawcheckboxexa--cmfcvisualmanageroffice2003ondrawcheckboxex"></a><a name="ondrawcheckboxex"></a>CMFCVisualManagerOffice2003::OnDrawCheckBoxEx  
 绘制一个复选框时，由框架调用。  
  
```  
virtual void OnDrawCheckBoxEx(
    CDC* pDC,  
    CRect rect,  
    int nState,  
    BOOL bHighlighted,  
    BOOL bPressed,  
    BOOL bEnabled);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向设备上下文的指针。  
  
 [in] `rect`  
 该复选框，该边框。  
  
 [in] `nState`  
 复选框状态︰ 如果未选中的 0，1，如果选中，2 如果选中混合。  
  
 [in] `bHighlighted`  
 `TRUE`如果突出显示该复选框时，或`FALSE`如果不是。  
  
 [in] `bPressed`  
 `TRUE`如果按下复选框时，或`FALSE`如果不是。  
  
 [in] `bEnabled`  
 `TRUE`如果启用此复选框，或`FALSE`如果不是。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameondrawcombobordera--cmfcvisualmanageroffice2003ondrawcomboborder"></a><a name="ondrawcomboborder"></a>CMFCVisualManagerOffice2003::OnDrawComboBorder  
 在其周围绘制边框的实例时，框架将调用此方法[CMFCToolBarComboBoxButton 类](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)。  
  
```  
virtual void OnDrawComboBorder(
    CDC* pDC,  
    CRect rect,  
    BOOL bDisabled,  
    BOOL bIsDropped,  
    BOOL bIsHighlighted,  
    CMFCToolBarComboBoxButton* pButton);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 组合框按钮的设备上下文指针。  
  
 [in] `rect`  
 指定组合框按钮的边界的矩形。  
  
 [in] `bDisabled`  
 一个布尔型参数，该值指示组合框按钮是否不可用。  
  
 [in] `bIsDropped`  
 一个布尔型参数，该值指示是否对组合框拉下。  
  
 [in] `bIsHighlighted`  
 一个布尔型参数，该值指示组合框按钮将突出显示。  
  
 [in] `pButton`  
 一个指向`CMFCToolBarComboBoxButton`对象。 框架将绘制此组合框按钮。  
  
### <a name="remarks"></a>备注  
 重写此方法在组合框的边框的外观进行自定义您派生视觉管理器中。  
  
##  <a name="a-nameondrawcombodropbuttona--cmfcvisualmanageroffice2003ondrawcombodropbutton"></a><a name="ondrawcombodropbutton"></a>CMFCVisualManagerOffice2003::OnDrawComboDropButton  
 框架将调用此方法时，它可绘制下拉按钮的[CMFCToolBarComboBoxButton 类](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)。  
  
```  
virtual void OnDrawComboDropButton(
    CDC* pDC,  
    CRect rect,  
    BOOL bDisabled,  
    BOOL bIsDropped,  
    BOOL bIsHighlighted,  
    CMFCToolBarComboBoxButton* pButton);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 指定删除按钮的边界的矩形。  
  
 [in] `bDisabled`  
 一个布尔型参数，该值指示下拉按钮是否不可用。  
  
 [in] `bIsDropped`  
 一个布尔型参数，该值指示是否对组合框拉下。  
  
 [in] `bIsHighlighted`  
 一个布尔型参数，该值指示是否突出显示删除按钮。  
  
 [in] `pButton`  
 一个指向`CMFCToolBarComboBoxButton`对象。 框架将绘制此组合框按钮的下拉按钮  
  
### <a name="remarks"></a>备注  
 重写此方法在组合框按钮的下拉按钮的外观进行自定义您派生视觉管理器中。  
  
##  <a name="a-nameondrawcontrolbordera--cmfcvisualmanageroffice2003ondrawcontrolborder"></a><a name="ondrawcontrolborder"></a>CMFCVisualManagerOffice2003::OnDrawControlBorder  
 框架将调用此方法时，它可绘制控件的边框。  
  
```  
virtual void OnDrawControlBorder(CWnd* pWndCtrl);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndCtrl`  
 指向[CWnd 类](../../mfc/reference/cwnd-class.md)对象，表示要绘制边框的控件。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameondrawexpandingboxa--cmfcvisualmanageroffice2003ondrawexpandingbox"></a><a name="ondrawexpandingbox"></a>CMFCVisualManagerOffice2003::OnDrawExpandingBox  
 由框架调用绘制扩展的框中时。  
  
```  
virtual void OnDrawExpandingBox(
    CDC* pDC,  
    CRect rect,  
    BOOL bIsOpened,  
    COLORREF colorBox);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 向显示的上下文中扩展的框中要绘制的指针。  
  
 [in] `rect`  
 扩展的框中要绘制的边框。  
  
 [in] `bIsOpened`  
 `TRUE`如果打开要绘制的框，则或`FALSE`如果不是。  
  
 [in] `colorBox`  
 要绘制的框的外边框的颜色。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameondrawheaderctrlbordera--cmfcvisualmanageroffice2003ondrawheaderctrlborder"></a><a name="ondrawheaderctrlborder"></a>CMFCVisualManagerOffice2003::OnDrawHeaderCtrlBorder  
 在其周围绘制边框的实例时，框架将调用此方法[CMFCHeaderCtrl 类](../../mfc/reference/cmfcheaderctrl-class.md)。  
  
```  
virtual void OnDrawHeaderCtrlBorder(
    CMFCHeaderCtrl* pCtrl,  
    CDC* pDC,  
    CRect& rect,  
    BOOL bIsPressed,  
    BOOL bIsHighlighted);
```  
  
### <a name="parameters"></a>参数  
 [in] `pCtrl`  
 一个指向[CMFCHeaderCtrl 类](../../mfc/reference/cmfcheaderctrl-class.md)对象。 框架将绘制此标头控件的边框。  
  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 一个指定标头控件的边界的矩形。  
  
 [in] `bIsPressed`  
 [in] `bIsHighlighted`  
 一个布尔型参数，该值指示是否按下了标头控件。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生视觉管理器，以自定义标头控件的边框。  
  
##  <a name="a-nameondrawmenubordera--cmfcvisualmanageroffice2003ondrawmenuborder"></a><a name="ondrawmenuborder"></a>CMFCVisualManagerOffice2003::OnDrawMenuBorder  
 框架将调用此方法时，它可绘制的边框[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)。  
  
```  
virtual void OnDrawMenuBorder(
    CDC* pDC,  
    CMFCPopu* pMenu,  
    CRect rect);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向设备上下文的指针[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)对象。  
  
 [in] `pMenu`  
 一个指向[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)对象。 框架周围绘制边框此弹出菜单。  
  
 [in] `rect`  
 一个指定的弹出菜单的边界的矩形。  
  
### <a name="remarks"></a>备注  
 此方法的默认实现将显示标准菜单的边框。 重写此方法在派生的视觉管理器自定义菜单边框的外观。  
  
##  <a name="a-nameondrawoutlookbarsplittera--cmfcvisualmanageroffice2003ondrawoutlookbarsplitter"></a><a name="ondrawoutlookbarsplitter"></a>CMFCVisualManagerOffice2003::OnDrawOutlookBarSplitter  
 当它绘制为 Outlook 栏拆分器时，框架将调用此方法。  
  
```  
virtual void OnDrawOutlookBarSplitter(
    CDC* pDC,  
    CRect rectSplitter);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rectSplitter`  
 一个指定拆分器的边界的矩形。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生的视觉管理器自定义 Outlook 栏上的拆分器的外观。  
  
##  <a name="a-nameondrawoutlookpagebuttonbordera--cmfcvisualmanageroffice2003ondrawoutlookpagebuttonborder"></a><a name="ondrawoutlookpagebuttonborder"></a>CMFCVisualManagerOffice2003::OnDrawOutlookPageButtonBorder  
 由框架调用时，它可绘制 Outlook 页面按钮的边框。  
  
```  
virtual void OnDrawOutlookPageButtonBorder(
    CDC* pDC,  
    CRect& rectBtn,  
    BOOL bIsHighlighted,  
    BOOL bIsPressed);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rectBtn`  
 指定 Outlook 页按钮的边界的矩形。  
  
 [in] `bIsHighlighted`  
 一个布尔值，指定按钮将突出显示。  
  
 [in] `bIsPressed`  
 一个布尔值，指定是否按下了按钮。  
  
### <a name="remarks"></a>备注  
 重写此方法中的自定义的可视管理器来更改 Outlook 页按钮的外观。  
  
##  <a name="a-nameondrawpanebordera--cmfcvisualmanageroffice2003ondrawpaneborder"></a><a name="ondrawpaneborder"></a>CMFCVisualManagerOffice2003::OnDrawPaneBorder  
 框架将调用此方法时，它可绘制的边框[CPane 类](../../mfc/reference/cpane-class.md)对象。  
  
```  
virtual void OnDrawPaneBorder(
    CDC* pDC,  
    CBasePane* pBar,  
    CRect& rect);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向控件条的设备上下文的指针。  
  
 [in] `pBar`  
 指向一个窗格的指针。 可视化管理器绘制此窗格边框。  
  
 [in] `rect`  
 一个指示窗格中的边界的矩形。  
  
### <a name="remarks"></a>备注  
 此方法的默认实现将显示标准的边框。 重写此方法在派生类以自定义的边框外观。  
  
##  <a name="a-nameondrawpanecaptiona--cmfcvisualmanageroffice2003ondrawpanecaption"></a><a name="ondrawpanecaption"></a>CMFCVisualManagerOffice2003::OnDrawPaneCaption  
 框架将调用此方法时，它可绘制的标题[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)对象。  
  
```  
virtual COLORREF OnDrawPaneCaption(
    CDC* pDC,  
    CDockablePane* pBar,  
    BOOL bActive,  
    CRect rectCaption,  
    CRect rectButtons);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `pBar`  
 一个指向[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)对象。 框架将绘制此窗格的标题。  
  
 [in] `bActive`  
 一个布尔型参数，该值指示是否将控件条处于活动状态。  
  
 [in] `rectCaption`  
 指定标题的边界的矩形。  
  
 [in] `rectButtons`  
 指定标题按钮的边界的矩形。  
  
### <a name="return-value"></a>返回值  
 一个[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)参数可指示标题的文本颜色。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameondrawpopupwindowbordera--cmfcvisualmanageroffice2003ondrawpopupwindowborder"></a><a name="ondrawpopupwindowborder"></a>CMFCVisualManagerOffice2003::OnDrawPopupWindowBorder  
 当绘制的边框的弹出窗口时，框架将调用此方法。  
  
```  
virtual void OnDrawPopupWindowBorder(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 弹出窗口中的设备上下文的指针。  
  
 [in] `rect`  
 弹出式窗口的边框。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameondrawpopupwindowbuttonbordera--cmfcvisualmanageroffice2003ondrawpopupwindowbuttonborder"></a><a name="ondrawpopupwindowbuttonborder"></a>CMFCVisualManagerOffice2003::OnDrawPopupWindowButtonBorder  
 当它在弹出窗口中绘制的边框的按钮时，框架将调用此方法。  
  
```  
virtual void OnDrawPopupWindowButtonBorder(
    CDC* pDC,  
    CRect rectClient,  
    CMFCDesktopAlertWndButton* pButton);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 按钮的设备上下文的指针。  
  
 [in] `rectClient`  
 该按钮的边框。  
  
 [in] `pButton`  
 指针，指向按钮 ( [CMFCDesktopAlertWndButton 类](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)对象)。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameondrawpopupwindowcaptiona--cmfcvisualmanageroffice2003ondrawpopupwindowcaption"></a><a name="ondrawpopupwindowcaption"></a>CMFCVisualManagerOffice2003::OnDrawPopupWindowCaption  
 框架将调用此方法时，它可绘制一个弹出窗口的标题。  
  
```  
virtual COLORREF OnDrawPopupWindowCaption(
    CDC* pDC,  
    CRect rectCaption,  
    CMFCDesktopAlertWnd* pPopupWnd);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 标题的设备上下文的指针。  
  
 [in] `rectCaption`  
 标题的边框。  
  
 [in] `pPopupWnd`  
 指向为其标题是要绘制的弹出窗口的指针。  
  
### <a name="return-value"></a>返回值  
 标题文本颜色。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生的视觉管理器自定义弹出窗口标题的外观。  
  
##  <a name="a-nameondrawribbonbuttonsgroupa--cmfcvisualmanageroffice2003ondrawribbonbuttonsgroup"></a><a name="ondrawribbonbuttonsgroup"></a>CMFCVisualManagerOffice2003::OnDrawRibbonButtonsGroup  
 在功能区上，它绘制一组按钮时，框架将调用此方法。  
  
```  
virtual COLORREF OnDrawRibbonButtonsGroup(
    CDC* pDC,  
    CMFCRibbonButtonsGroup* pGroup,  
    CRect rectGroup);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `pGroup`  
 一个指向一组功能区上的按钮。 框架将绘制该按钮组。  
  
 [in] `rectGroup`  
 一个指定组的边界的矩形。  
  
### <a name="return-value"></a>返回值  
 保留的值。 默认实现将返回 -1。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生的视觉管理器来自定义一组功能区上的按钮的外观。  
  
##  <a name="a-nameondrawribboncategorycaptiona--cmfcvisualmanageroffice2003ondrawribboncategorycaption"></a><a name="ondrawribboncategorycaption"></a>CMFCVisualManagerOffice2003::OnDrawRibbonCategoryCaption  
 在功能区类别的标题栏，它可绘制时，框架将调用此方法。  
  
```  
virtual COLORREF OnDrawRibbonCategoryCaption(
    CDC* pDC,  
    CMFCRibbonContextCaption* pContextCaption);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向功能区类别的设备上下文的指针。  
  
 [in] `pContextCaption`  
 指向标题栏的指针。 可视化管理器绘制这[CMFCRibbonContextCaption 类](../../mfc/reference/cmfcribboncontextcaption-class.md)。  
  
### <a name="return-value"></a>返回值  
 一个[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)参数可指示标题栏上的文本的颜色。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生类自定义功能区类别的标题栏的外观。  
  
##  <a name="a-nameondrawribboncategorytaba--cmfcvisualmanageroffice2003ondrawribboncategorytab"></a><a name="ondrawribboncategorytab"></a>CMFCVisualManagerOffice2003::OnDrawRibbonCategoryTab  
 当绘制一个功能区类别的选项卡时，框架将调用此方法。  
  
```  
virtual COLORREF OnDrawRibbonCategoryTab(
    CDC* pDC,  
    CMFCRibbonTab* pTab,  
    BOOL bIsActive);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `pTab`  
 指向功能区选项卡对象的指针。 框架将绘制此选项卡。  
  
 [in] `bIsActive`  
 `TRUE`如果选项卡处于活动状态，或`FALSE`如果不是。  
  
### <a name="return-value"></a>返回值  
 用于在功能区类别选项卡上的文本颜色。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生的视觉管理器自定义功能区类别选项卡的外观。  
  
##  <a name="a-nameondrawribbonprogressbara--cmfcvisualmanageroffice2003ondrawribbonprogressbar"></a><a name="ondrawribbonprogressbar"></a>CMFCVisualManagerOffice2003::OnDrawRibbonProgressBar  
 框架将调用此方法时，它可绘制[CMFCRibbonProgressBar 类](../../mfc/reference/cmfcribbonprogressbar-class.md)对象。  
  
```  
virtual void OnDrawRibbonProgressBar(
    CDC* pDC,  
    CMFCRibbonProgressBar* pProgress,  
    CRect rectProgress,  
    CRect rectChunk,  
    BOOL bInfiniteMode);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `pProgress`  
 一个指向[CMFCRibbonProgressBar 类](../../mfc/reference/cmfcribbonprogressbar-class.md)对象。 框架将绘制此进度栏。  
  
 [in] `rectProgress`  
 一个指定进度栏的边界的矩形。  
  
 [in] `rectChunk`  
 一个指定周围进度栏的区域的边界的矩形。  
  
 [in] `bInfiniteMode`  
 `TRUE`如果栏在无限模式中，或`FALSE`如果不是。 默认实现不使用此参数。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生类进度条的外观进行自定义  
  
##  <a name="a-nameondrawribbonquickaccesstoolbarseparatora--cmfcvisualmanageroffice2003ondrawribbonquickaccesstoolbarseparator"></a><a name="ondrawribbonquickaccesstoolbarseparator"></a>CMFCVisualManagerOffice2003::OnDrawRibbonQuickAccessToolBarSeparator  
 在功能区快速访问工具栏上，它绘制分隔符时，框架将调用此方法。  
  
```  
virtual void OnDrawRibbonQuickAccessToolBarSeparator(
    CDC* pDC,  
    CMFCRibbonSeparator* pSeparator,  
    CRect rect);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `pSeparator`  
 一个指向[CMFCRibbonSeparator 类](../../mfc/reference/cmfcribbonseparator-class.md)对象。 框架将绘制此功能区分隔符。  
  
 [in] `rect`  
 一个指定的分隔符的边界的矩形。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生类可以自定义功能区快速访问工具栏上的分隔符的外观。  
  
##  <a name="a-nameondrawribbonsliderchannela--cmfcvisualmanageroffice2003ondrawribbonsliderchannel"></a><a name="ondrawribbonsliderchannel"></a>CMFCVisualManagerOffice2003::OnDrawRibbonSliderChannel  
 框架将调用此方法时，它可绘制的通道[CMFCRibbonSlider 类](../../mfc/reference/cmfcribbonslider-class.md)。  
  
```  
virtual void OnDrawRibbonSliderChannel(
    CDC* pDC,  
    CMFCRibbonSlider* pSlider,  
    CRect rect);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向设备上下文的指针。  
  
 [in] `pSlider`  
 一个指向[CMFCRibbonSlider 类](../../mfc/reference/cmfcribbonslider-class.md)对象。 框架将绘制此功能区滑块的通道。  
  
 [in] `rect`  
 指定功能区滑块的通道的边界的矩形。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生类自定义功能区滑块的通道的外观。  
  
##  <a name="a-nameondrawribbonsliderthumba--cmfcvisualmanageroffice2003ondrawribbonsliderthumb"></a><a name="ondrawribbonsliderthumb"></a>CMFCVisualManagerOffice2003::OnDrawRibbonSliderThumb  
 框架将调用此方法时，它可绘制的 thumb [CMFCRibbonSlider 类](../../mfc/reference/cmfcribbonslider-class.md)对象  
  
```  
virtual void OnDrawRibbonSliderThumb(
    CDC* pDC,  
    CMFCRibbonSlider* pSlider,  
    CRect rect,  
    BOOL bIsHighlighted,  
    BOOL bIsPressed,  
    BOOL bIsDisabled);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `pSlider`  
 一个指向[CMFCRibbonSlider 类](../../mfc/reference/cmfcribbonslider-class.md)。 框架将绘制此功能区滑块条的滚动块。  
  
 [in] `rect`  
 指定功能区滑块条的滚动块的边界的矩形。  
  
 [in] `bIsHighlighted`  
 一个布尔型参数，该值指示是否突出显示缩略图。  
  
 [in] `bIsPressed`  
 一个布尔型参数，该值指示是否按下了缩略图。  
  
 [in] `bIsDisabled`  
 一个布尔型参数，该值指示滚动块是否不可用。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生的视觉管理器自定义功能区滑块条的滚动块的外观。  
  
##  <a name="a-nameondrawribbonsliderzoombuttona--cmfcvisualmanageroffice2003ondrawribbonsliderzoombutton"></a><a name="ondrawribbonsliderzoombutton"></a>CMFCVisualManagerOffice2003::OnDrawRibbonSliderZoomButton  
 框架将调用此方法时，它可绘制的缩放按钮[CMFCRibbonSlider 类](../../mfc/reference/cmfcribbonslider-class.md)对象。  
  
```  
virtual void OnDrawRibbonSliderZoomButton(
    CDC* pDC,  
    CMFCRibbonSlider* pSlider,  
    CRect rect,  
    BOOL bIsZoomOut,  
    BOOL bIsHighlighted,  
    BOOL bIsPressed,  
    BOOL bIsDisabled);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `pSlider`  
 一个指向[CMFCRibbonSlider 类](../../mfc/reference/cmfcribbonslider-class.md)对象。 框架将绘制此功能区滑块。  
  
 [in] `rect`  
 指定在功能区滑块的缩放按钮的边界的矩形。  
  
 [in] `bIsZoomOut`  
 `TRUE`如果框架应绘制为左的按钮与" ** - **"为缩小、 或`FALSE`如果框架应正确以绘制按钮" ** + **"为放大。  
  
 [in] `bIsHighlighted`  
 一个布尔型参数，该值指示是否突出显示按钮。  
  
 [in] `bIsPressed`  
 一个布尔型参数，该值指示是否按下了按钮。  
  
 [in] `bIsDisabled`  
 一个布尔型参数，该值指示按钮将不可用。  
  
### <a name="remarks"></a>备注  
 默认情况下，在功能区滑块上的缩放按钮都有任何一个的圆圈** + **或** - **登录中心。 若要自定义缩放按钮的外观，请重写此方法在派生的视觉管理器中。  
  
##  <a name="a-nameondrawribbonstatusbarpanea--cmfcvisualmanageroffice2003ondrawribbonstatusbarpane"></a><a name="ondrawribbonstatusbarpane"></a>CMFCVisualManagerOffice2003::OnDrawRibbonStatusBarPane  
 当它在状态栏上绘制一个窗格时，框架将调用此方法。  
  
```  
virtual COLORREF OnDrawRibbonStatusBarPane(
    CDC* pDC,  
    CMFCRibbonStatusBar* pBar,  
    CMFCRibbonStatusBarPane* pPane);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `pBar`  
 指向包含窗格中的状态栏的指针。  
  
 [in] `pPane`  
 指向状态栏窗格的指针。 框架将绘制这[CMFCRibbonStatusBarPane 类](../../mfc/reference/cmfcribbonstatusbarpane-class.md)对象。  
  
### <a name="return-value"></a>返回值  
 保留的值。 默认实现将返回 -1。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生的视觉管理器自定义状态栏上一个窗格的外观。  
  
##  <a name="a-nameondrawscrollbuttonsa--cmfcvisualmanageroffice2003ondrawscrollbuttons"></a><a name="ondrawscrollbuttons"></a>CMFCVisualManagerOffice2003::OnDrawScrollButtons  
 当绘制滚动按钮时，框架将调用此方法。  
  
```  
virtual void OnDrawScrollButtons(
    CDC* pDC,  
    const CRect& rect,  
    const int nBorderSize,  
    int iImage,  
    BOOL bHilited);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向设备上下文的指针。  
  
 [in] `rect`  
 滚动按钮的边框。  
  
 [in] `nBorderSize`  
 若要在滚动按钮周围绘制边框的大小。  
  
 [in] `iImage`  
 要在滚动按钮中进行绘制的图像的标识符。  
  
 [in] `bHilited`  
 `TRUE`如果突出显示的滚动按钮，或`FALSE`如果不是。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameondrawseparatora--cmfcvisualmanageroffice2003ondrawseparator"></a><a name="ondrawseparator"></a>CMFCVisualManagerOffice2003::OnDrawSeparator  
 当绘制分隔符时，框架将调用此方法。  
  
```  
virtual void OnDrawSeparator(
    CDC* pDC,  
    CBasePane* pBar,  
    CRect rect,  
    BOOL bIsHoriz);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向控件条的设备上下文的指针。  
  
 [in] `pBar`  
 指向一个窗格，其中包含分隔符的指针。  
  
 [in] `rect`  
 一个指定的分隔符的边界的矩形。  
  
 [in] `bIsHoriz`  
 `TRUE`如果水平，停靠窗格或`FALSE`如果垂直停靠窗格。  
  
### <a name="remarks"></a>备注  
 控件条上使用分隔符来分隔组相关的图标。 此方法的默认实现将显示标准的分隔符。 重写此方法在派生视觉管理器，以自定义分隔符的外观。  
  
##  <a name="a-nameondrawshowallmenuitemsa--cmfcvisualmanageroffice2003ondrawshowallmenuitems"></a><a name="ondrawshowallmenuitems"></a>CMFCVisualManagerOffice2003::OnDrawShowAllMenuItems  
 在菜单中，它绘制的所有项时，框架将调用此方法  
  
```  
virtual void OnDrawShowAllMenuItems(
    CDC* pDC,  
    CRect rect,  
    CMFCVisualManager::AFX_BUTTON_STATE state);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向设备上下文的指针。  
  
 [in] `rect`  
 菜单要绘制的边框。  
  
 [in] `state`  
 按钮的状态。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameondrawstatusbarpanebordera--cmfcvisualmanageroffice2003ondrawstatusbarpaneborder"></a><a name="ondrawstatusbarpaneborder"></a>CMFCVisualManagerOffice2003::OnDrawStatusBarPaneBorder  
 框架将调用此方法时，它可绘制的边框[CMFCStatusBar 类](../../mfc/reference/cmfcstatusbar-class.md)对象。  
  
```  
virtual void OnDrawStatusBarPaneBorder(
    CDC* pDC,  
    CMFCStatusBar* pBar,  
    CRect rectPane,  
    UINT uiID,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `pBar`  
 一个指向[CMFCStatusBar 类](../../mfc/reference/cmfcstatusbar-class.md)对象。 框架将绘制状态栏对象。  
  
 [in] `rectPane`  
 指定状态栏的边界的矩形。  
  
 [in] `uiID`  
 状态栏的 ID。  
  
 [in] `nStyle`  
 状态栏的样式。  
  
### <a name="remarks"></a>备注  
 重写此方法的派生的可视管理器的边框的外观进行自定义`CMFCStatusBar`对象。  
  
##  <a name="a-nameondrawstatusbarprogressa--cmfcvisualmanageroffice2003ondrawstatusbarprogress"></a><a name="ondrawstatusbarprogress"></a>CMFCVisualManagerOffice2003::OnDrawStatusBarProgress  
 框架将调用此方法在其上绘制的进度指示器时[CMFCStatusBar 类](../../mfc/reference/cmfcstatusbar-class.md)对象  
  
```  
virtual void OnDrawStatusBarProgress(
    CDC* pDC,  
    CMFCStatusBar* pStatusBar,  
    CRect rectProgress,  
    int nProgressTotal,  
    int nProgressCurr,  
    COLORREF clrBar,  
    COLORREF clrProgressBarDest,  
    COLORREF clrProgressText,  
    BOOL bProgressText);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向状态栏的设备上下文的指针  
  
 [in] `pStatusBar`  
 [CMFCStatusBar 类](../../mfc/reference/cmfcstatusbar-class.md)对象，其中包含在进度栏。  
  
 [in] `rectProgress`  
 一个指定进度栏的边界的矩形。  
  
 [in] `nProgressTotal`  
 进度栏的总数。  
  
 [in] `nProgressCurr`  
 进度栏当前进度。  
  
 [in] `clrBar`  
 进度栏的初始颜色。 值为颜色渐变的开始或完成进度栏的颜色。  
  
 [in] `clrProgressBarDest`  
 [in] `clrProgressText`  
 [in] `bProgressText`  
  
### <a name="remarks"></a>备注  
 重写此方法在进度栏的状态栏上的外观进行自定义的派生可视管理器中。  
  
##  <a name="a-nameondrawstatusbarsizeboxa--cmfcvisualmanageroffice2003ondrawstatusbarsizebox"></a><a name="ondrawstatusbarsizebox"></a>CMFCVisualManagerOffice2003::OnDrawStatusBarSizeBox  
 框架将调用此方法时，它可绘制的大小框[CMFCStatusBar 类](../../mfc/reference/cmfcstatusbar-class.md)。  
  
```  
virtual void OnDrawStatusBarSizeBox(
    CDC* pDC,  
    CMFCStatusBar* pStatBar,  
    CRect rectSizeBox);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `pStatBar`  
 指向一个状态栏的指针。 框架将绘制此状态栏大小。  
  
 [in] `rectSizeBox`  
 指定大小中的边界的矩形。  
  
### <a name="remarks"></a>备注  
 重写此方法在状态栏上的大小框的外观进行自定义的派生可视管理器中。  
  
##  <a name="a-nameondrawtaba--cmfcvisualmanageroffice2003ondrawtab"></a><a name="ondrawtab"></a>CMFCVisualManagerOffice2003::OnDrawTab  
 框架将调用此方法时，它可绘制选项卡[CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)对象。  
  
```  
virtual void OnDrawTab(
    CDC* pDC,  
    CRect rectTab,  
    int iTab,  
    BOOL bIsActive,  
    const CMFCBaseTabCtrl* pTabWnd);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rectTab`  
 一个指定选项卡控件的边界的矩形。  
  
 [in] `iTab`  
 框架将绘制选项卡的索引。  
  
 [in] `bIsActive`  
 一个布尔型参数，指定选项卡处于活动状态。  
  
 [in] `pTabWnd`  
 一个指向[CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)对象。 框架将绘制该选项卡控件。  
  
### <a name="remarks"></a>备注  
 一个`CMFCBaseTabCtrl`对象将调用此方法在处理时`WM_PAINT`消息。重写此方法在派生类以自定义查找范围选项卡中。  
  
##  <a name="a-nameondrawtabsbuttonbordera--cmfcvisualmanageroffice2003ondrawtabsbuttonborder"></a><a name="ondrawtabsbuttonborder"></a>CMFCVisualManagerOffice2003::OnDrawTabsButtonBorder  
 框架将调用此方法时，它可绘制选项卡按钮的边框。  
  
```  
virtual void OnDrawTabsButtonBorder(
    CDC* pDC,  
    CRect& rect,  
    CMFCButton* pButton,  
    UINT uiState,  
    CMFCBaseTabCtrl* pWndTab);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 指定选项卡按钮的边界的矩形。  
  
 [in] `pButton`  
 一个指向[CMFCButton 类](../../mfc/reference/cmfcbutton-class.md)为其框架绘制边框。  
  
 [in] `uiState`  
 按钮的状态 (请参阅[CButton::GetState](../../mfc/reference/cbutton-class.md#getstate))。  
  
 [in] `pWndTab`  
 指向父选项卡窗口的指针。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生的视觉管理器自定义选项卡按钮的边框的外观。  
  
##  <a name="a-nameondrawtaska--cmfcvisualmanageroffice2003ondrawtask"></a><a name="ondrawtask"></a>CMFCVisualManagerOffice2003::OnDrawTask  
 框架将调用此方法时，它可绘制[CMFCTasksPaneTask 类](../../mfc/reference/cmfctaskspanetask-class.md)对象。  
  
```  
virtual void OnDrawTask(
    CDC* pDC,  
    CMFCTasksPaneTask* pTask,  
    CImageList* pIcons,  
    BOOL bIsHighlighted = FALSE,  
    BOOL bIsSelected = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `pTask`  
 一个指向[CMFCTasksPaneTask 类](../../mfc/reference/cmfctaskspanetask-class.md)对象。 框架将绘制此任务。  
  
 [in] `pIcons`  
 指向任务窗格中与关联的图像列表的指针。 每个任务包含在此列表中的图像的索引。  
  
 [in] `bIsHighlighted`  
 一个布尔型参数，指定是否显示的任务突出显示。  
  
 [in] `bIsSelected`  
 一个布尔型参数，指定是否选择了显示的任务。  
  
### <a name="remarks"></a>备注  
 该框架的图标和文本作为任务栏上显示的任务。 `pIcons`参数包含所指示的任务的图标`pTask`。 重写此方法在派生类自定义任务栏上的任务的外观。  
  
##  <a name="a-nameondrawtasksgroupareabordera--cmfcvisualmanageroffice2003ondrawtasksgroupareaborder"></a><a name="ondrawtasksgroupareaborder"></a>CMFCVisualManagerOffice2003::OnDrawTasksGroupAreaBorder  
 框架将调用此方法在其上绘制一组周围边框时[CMFCTasksPane 类](../../mfc/reference/cmfctaskspane-class.md)对象。  
  
```  
virtual void OnDrawTasksGroupAreaBorder(
    CDC* pDC,  
    CRect rect,  
    BOOL bSpecial = FALSE,  
    BOOL bNoTitle = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 在任务窗格中指定的组区域的边界的矩形。  
  
 [in] `bSpecial`  
 一个布尔型参数，指定是否突出显示边框。 值为`TRUE`指示边框突出显示。  
  
 [in] `bNoTitle`  
 一个布尔型参数，用于指定的组区域是否具有一个标题。 值为`TRUE`指示的组区域不具有标题。  
  
### <a name="remarks"></a>备注  
 重写此函数在派生类以自定义任务窗格上的组区域周围的边框。  
  
##  <a name="a-nameondrawtasksgroupcaptiona--cmfcvisualmanageroffice2003ondrawtasksgroupcaption"></a><a name="ondrawtasksgroupcaption"></a>CMFCVisualManagerOffice2003::OnDrawTasksGroupCaption  
 框架将调用此方法时，它可绘制的标题[CMFCTasksPaneTaskGroup 类](../../mfc/reference/cmfctaskspanetaskgroup-class.md)对象。  
  
```  
virtual void OnDrawTasksGroupCaption(
    CDC* pDC,  
    CMFCTasksPaneTaskGroup* pGroup,  
    BOOL bIsHighlighted = FALSE,  
    BOOL bIsSelected = FALSE,  
    BOOL bCanCollapse = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `pGroup`  
 一个指向[CMFCTasksPaneTaskGroup 类](../../mfc/reference/cmfctaskspanetaskgroup-class.md)对象。 框架将绘制此组的标题。  
  
 [in] `bIsHighlighted`  
 一个布尔型参数，该值指示是否突出显示组。  
  
 [in] `bIsSelected`  
 一个布尔型参数，该值指示是否当前选择的组。  
  
 [in] `bCanCollapse`  
 一个布尔型参数，该值指示是否可以折叠组。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生类以自定义的标题`CMFCTasksPaneTaskGroup`。  
  
##  <a name="a-nameondrawtearoffcaptiona--cmfcvisualmanageroffice2003ondrawtearoffcaption"></a><a name="ondrawtearoffcaption"></a>CMFCVisualManagerOffice2003::OnDrawTearOffCaption  
 框架将调用此方法时，它可绘制的标题[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)对象。  
  
```  
virtual void OnDrawTearOffCaption(
    CDC* pDC,  
    CRect rect,  
    BOOL bIsActive);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 指定标题的边界的矩形。  
  
 [in] `bIsActive`  
 `TRUE`如果标题是活动状态，则`FALSE`否则为。  
  
### <a name="remarks"></a>备注  
 由框架调用此函数时[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)对象进程`WM_PAINT`消息，并必须绘制分开的标题。  
  
 重写此方法在派生类以自定义外观的分开的条形图的标题。  
  
##  <a name="a-nameonerasepopupwindowbuttona--cmfcvisualmanageroffice2003onerasepopupwindowbutton"></a><a name="onerasepopupwindowbutton"></a>CMFCVisualManagerOffice2003::OnErasePopupWindowButton  
 它将擦除弹出窗口中的按钮时，框架将调用此方法。  
  
```  
virtual void OnErasePopupWindowButton(
    CDC* pDC,  
    CRect rectClient,  
    CMFCDesktopAlertWndButton* pButton);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rectClient`  
 所指定的弹出窗口的客户端区域的矩形。  
  
 [in] `pButton`  
 指针，指向清除按钮。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameonerasetabsareaa--cmfcvisualmanageroffice2003onerasetabsarea"></a><a name="onerasetabsarea"></a>CMFCVisualManagerOffice2003::OnEraseTabsArea  
 它将擦除的选项卡窗口选项卡区域时，框架将调用此方法。  
  
```  
virtual void OnEraseTabsArea(
    CDC* pDC,  
    CRect rect,  
    const CMFCBaseTabCtrl* pTabWnd);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 一个指定选项卡区域的边界的矩形。  
  
 [in] `pTabWnd`  
 指向选项卡窗口的指针。 该框架会清除指定的选项卡窗口中的选项卡区域。  
  
### <a name="remarks"></a>备注  
 由框架调用此函数时[CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)对象进程`WM_PAINT`消息，然后清除选项卡区域。  
  
 重写此方法在派生视觉管理器，以自定义选项卡的外观。  
  
##  <a name="a-nameonerasetabsbuttona--cmfcvisualmanageroffice2003onerasetabsbutton"></a><a name="onerasetabsbutton"></a>CMFCVisualManagerOffice2003::OnEraseTabsButton  
 它将擦除的文本和图标的选项卡按钮时，框架将调用此方法。  
  
```  
virtual void OnEraseTabsButton(
    CDC* pDC,  
    CRect rect,  
    CMFCButton* pButton,  
    CMFCBaseTabCtrl* pWndTab);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 指定选项卡按钮的边界的矩形。  
  
 [in] `pButton`  
 一个指向选项卡按钮。 该框架会清除文本和此按钮的图标。  
  
 [in] `pWndTab`  
 指向包含选项卡按钮的选项卡控件的指针。  
  
### <a name="remarks"></a>备注  
 该框架会清除文本和按钮的图标时[CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)对象进程`WM_ERASEBKGND`消息  
  
 重写此方法在派生视觉管理器，以自定义选项卡按钮的外观。  
  
##  <a name="a-nameonerasetabsframea--cmfcvisualmanageroffice2003onerasetabsframe"></a><a name="onerasetabsframe"></a>CMFCVisualManagerOffice2003::OnEraseTabsFrame  
 框架将调用此方法时它将一个帧擦除上[CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)对象。  
  
```  
virtual BOOL OnEraseTabsFrame(
    CDC* pDC,  
    CRect rect,  
    const CMFCBaseTabCtrl* pTabWnd);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 指定选项卡窗口中的边界的矩形。  
  
 [in] `pTabWnd`  
 指向选项卡窗口的指针。 框架将帧清除此[CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果该方法是成功或`FALSE`如果不是。  
  
### <a name="remarks"></a>备注  
 此方法填充指示的区域`rect`与活动选项卡的背景色。 它时，将调用`CMFCBaseTabCtrl`对象进程`WM_PAINT`消息，然后清除选项卡帧。  
  
##  <a name="a-nameonfillautohidebuttonbackgrounda--cmfcvisualmanageroffice2003onfillautohidebuttonbackground"></a><a name="onfillautohidebuttonbackground"></a>CMFCVisualManagerOffice2003::OnFillAutoHideButtonBackground  
 框架在填充自动隐藏按钮的背景时调用此方法。  
  
```  
virtual void OnFillAutoHideButtonBackground(
    CDC* pDC,  
    CRect rect,  
    CMFCAutoHideButton* pButton);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 指定自动隐藏按钮的边界的矩形。  
  
 [in] `pButton`  
 一个指向[CMFCAutoHideButton 类](../../mfc/reference/cmfcautohidebutton-class.md)对象。 框架填充此自动隐藏按钮的背景。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生的视觉管理器自定义一个自动隐藏按钮的外观。  
  
##  <a name="a-nameonfillbarbackgrounda--cmfcvisualmanageroffice2003onfillbarbackground"></a><a name="onfillbarbackground"></a>CMFCVisualManagerOffice2003::OnFillBarBackground  
 框架将调用此方法时填充的背景的[CBasePane 类](../../mfc/reference/cbasepane-class.md)对象。  
  
```  
virtual void OnFillBarBackground(
    CDC* pDC,  
    CBasePane* pBar,  
    CRect rectClient,  
    CRect rectClip,  
    BOOL bNCArea = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向控件条的设备上下文的指针。  
  
 [in] `pBar`  
 一个指向[CBasePane 类](../../mfc/reference/cbasepane-class.md)对象。 框架填充此窗格的背景。  
  
 [in] `rectClient`  
 指定窗格中的边界的矩形。  
  
 [in] `rectClip`  
 指定窗格中的剪辑区域的矩形。  
  
 [in] `bNCArea`  
 保留的值。  
  
### <a name="remarks"></a>备注  
 此方法的默认实现将填充全局变量中的三维背景色与面板的背景`afxGlobalData`。  
  
 重写此方法在派生视觉管理器，以自定义窗格的背景。  
  
##  <a name="a-nameonfillbuttoninteriora--cmfcvisualmanageroffice2003onfillbuttoninterior"></a><a name="onfillbuttoninterior"></a>CMFCVisualManagerOffice2003::OnFillButtonInterior  
 填充工具栏按钮的背景时，框架将调用此方法。  
  
```  
virtual void OnFillButtonInterior(
    CDC* pDC,  
    CMFCToolBarButton* pButton,  
    CRect rect,  
    CMFCVisualManager::AFX_BUTTON_STATE state);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向一个工具栏按钮的设备上下文的指针。  
  
 [in] `pButton`  
 一个指向该框架将为其填充背景的按钮。  
  
 [in] `rect`  
 一个指定工具栏按钮的边界的矩形。  
  
 [in] `state`  
 工具栏按钮的状态 (工具栏按钮的可能的状态为`ButtonsIsRegular`， `ButtonsIsPressed`，或`ButtonsIsHighlighted`)。  
  
### <a name="remarks"></a>备注  
 此方法的默认实现使用的默认颜色来填充的背景。 重写此方法在派生视觉管理器，以自定义工具栏按钮的背景。  
  
##  <a name="a-nameonfillcommandslistbackgrounda--cmfcvisualmanageroffice2003onfillcommandslistbackground"></a><a name="onfillcommandslistbackground"></a>CMFCVisualManagerOffice2003::OnFillCommandsListBackground  
 填充属于命令列表的工具栏按钮的背景时，框架将调用此方法。 此命令列表是自定义对话框中的一部分。  
  
```  
virtual COLORREF OnFillCommandsListBackground(
    CDC* pDC,  
    CRect rect,  
    BOOL bIsSelected = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 指定按钮的边界的矩形。  
  
 [in] `bIsSelected`  
 一个布尔型参数，该值指示按钮处于选中状态。  
  
### <a name="return-value"></a>返回值  
 工具栏按钮文本颜色。  
  
### <a name="remarks"></a>备注  
 有关自定义列表的详细信息，请参阅[CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)。 此方法的默认实现将填充基于当前选定的外观的配色方案的背景。  
  
##  <a name="a-nameonfillheaderctrlbackgrounda--cmfcvisualmanageroffice2003onfillheaderctrlbackground"></a><a name="onfillheaderctrlbackground"></a>CMFCVisualManagerOffice2003::OnFillHeaderCtrlBackground  
 填充标头控件的背景时，框架将调用此方法。  
  
```  
virtual void OnFillHeaderCtrlBackground(
    CMFCHeaderCtrl* pCtrl,  
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>参数  
 [in] `pCtrl`  
 一个指向[CMFCHeaderCtrl 类](../../mfc/reference/cmfcheaderctrl-class.md)对象。 框架填充此标头控件的背景。  
  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 一个指定标头控件的边界的矩形。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生视觉管理器，以自定义标头控件的外观。  
  
##  <a name="a-nameonfillhighlightedareaa--cmfcvisualmanageroffice2003onfillhighlightedarea"></a><a name="onfillhighlightedarea"></a>CMFCVisualManagerOffice2003::OnFillHighlightedArea  
 填充工具栏按钮的突出显示的区域时，框架将调用此方法。  
  
```  
virtual void OnFillHighlightedArea(
    CDC* pDC,  
    CRect rect,  
    CBrush* pBrush,  
    CMFCToolBarButton* pButton);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向设备上下文的指针。  
  
 [in] `rect`  
 要填充的突出显示区域的边框。  
  
 [in] `pBrush`  
 要在填充突出显示的区域中使用的画笔。  
  
 [in] `pButton`  
 指向[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)对象表示要填充突出显示的区域。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameonfilloutlookbarcaptiona--cmfcvisualmanageroffice2003onfilloutlookbarcaption"></a><a name="onfilloutlookbarcaption"></a>CMFCVisualManagerOffice2003::OnFillOutlookBarCaption  
 当它填满一个 Outlook 的标题栏的背景，框架将调用此方法。  
  
```  
virtual void OnFillOutlookBarCaption(
    CDC* pDC,  
    CRect rectCaption,  
    COLORREF& clrText);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rectCaption`  
 一个指定的标题栏的边界的矩形。  
  
 [out] `clrText`  
 对引用`COLORREF`此方法将写入到文本的颜色在标题栏的对象。  
  
### <a name="remarks"></a>备注  
 此方法的默认实现将填充为基于当前外观上的阴影颜色的标题栏。  
  
 重写此方法在派生视觉管理器，以自定义 Outlook 标题栏的颜色。  
  
##  <a name="a-nameonfilloutlookpagebuttona--cmfcvisualmanageroffice2003onfilloutlookpagebutton"></a><a name="onfilloutlookpagebutton"></a>CMFCVisualManagerOffice2003::OnFillOutlookPageButton  
 填充内部 Outlook 页面按钮时，框架将调用此方法。  
  
```  
virtual void OnFillOutlookPageButton(
    CDC* pDC,  
    const CRect& rect,  
    BOOL bIsHighlighted,  
    BOOL bIsPressed,  
    COLORREF& clrText);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 指定 Outlook 页按钮的边界的矩形。  
  
 [in] `bIsHighlighted`  
 一个布尔型参数，指定按钮将突出显示。  
  
 [in] `bIsPressed`  
 一个布尔型参数，指定是否按下了按钮。  
  
 [out] `clrText`  
 对引用`COLORREF`对象，此方法会将存储 outlook 页按钮的文本颜色。  
  
### <a name="remarks"></a>备注  
 重写此函数在派生的视觉管理器自定义 Outlook 页面按钮的外观。  
  
##  <a name="a-nameonfillpopupwindowbackgrounda--cmfcvisualmanageroffice2003onfillpopupwindowbackground"></a><a name="onfillpopupwindowbackground"></a>CMFCVisualManagerOffice2003::OnFillPopupWindowBackground  
 填充背景的弹出窗口时，框架将调用此方法。  
  
```  
virtual void OnFillPopupWindowBackground(
    CDC* pDC,  
    CRect rect);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 一个指定的弹出窗口的边界的矩形。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生的视觉管理器自定义弹出窗口的外观。  
  
##  <a name="a-nameonfilltaba--cmfcvisualmanageroffice2003onfilltab"></a><a name="onfilltab"></a>CMFCVisualManagerOffice2003::OnFillTab  
 填充选项卡窗口的背景时，框架将调用此方法。  
  
```  
virtual void OnFillTab(
    CDC* pDC,  
    CRect rectFill,  
    CBrush* pbrFill,  
    int iTab,  
    BOOL bIsActive,  
    const CMFCBaseTabCtrl* pTabWnd);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rectFill`  
 指定选项卡窗口中的边界的矩形。  
  
 [in] `pbrFill`  
 一个指向该框架使用以填充选项卡窗口的画笔。  
  
 [in] `iTab`  
 为其框架填充背景选项卡的从零开始的选项卡索引。  
  
 [in] `bIsActive`  
 `TRUE`如果选项卡处于活动状态或`FALSE`如果不是。  
  
 [in] `pTabWnd`  
 指向父选项卡控件的指针。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生视觉管理器，以自定义选项卡的外观。  
  
##  <a name="a-nameonfilltasksgroupinteriora--cmfcvisualmanageroffice2003onfilltasksgroupinterior"></a><a name="onfilltasksgroupinterior"></a>CMFCVisualManagerOffice2003::OnFillTasksGroupInterior  
 框架将调用此方法时填充的内部[CMFCTasksPaneTaskGroup 类](../../mfc/reference/cmfctaskspanetaskgroup-class.md)对象。  
  
```  
virtual void OnFillTasksGroupInterior(
    CDC* pDC,  
    CRect rect,  
    BOOL bSpecial = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rect`  
 一个指定的任务组的边界的矩形。  
  
 [in] `bSpecial`  
 一个布尔值，该值指示是否用特殊的颜色填充其内部。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生的视觉管理器自定义任务组的外观。  
  
##  <a name="a-nameonfilltaskspanebackgrounda--cmfcvisualmanageroffice2003onfilltaskspanebackground"></a><a name="onfilltaskspanebackground"></a>CMFCVisualManagerOffice2003::OnFillTasksPaneBackground  
 框架将调用此方法时填充的背景的[CMFCTasksPane 类](../../mfc/reference/cmfctaskspane-class.md)控件。  
  
```  
virtual void OnFillTasksPaneBackground(
    CDC* pDC,  
    CRect rectWorkArea);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rectWorkArea`  
 指定任务窗格中的边界的矩形。  
  
### <a name="remarks"></a>备注  
 重写此方法的派生的可视管理器的外观进行自定义[CMFCTasksPane 类](../../mfc/reference/cmfctaskspane-class.md)对象。  
  
##  <a name="a-nameonhighlightquickcustomizemenubuttona--cmfcvisualmanageroffice2003onhighlightquickcustomizemenubutton"></a><a name="onhighlightquickcustomizemenubutton"></a>CMFCVisualManagerOffice2003::OnHighlightQuickCustomizeMenuButton  
 框架将调用此方法时，它可绘制突出显示快速的自定义菜单按钮。  
  
```  
virtual void OnHighlightQuickCustomizeMenuButton(
    CDC* pDC,  
    CMFCToolBarMenuButton* pButton,  
    CRect rect);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向按钮的设备上下文的指针。  
  
 [in] `pButton`  
 一个指向按钮。  
  
 [in] `rect`  
 该按钮的边框。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameonhighlightrarelyusedmenuitemsa--cmfcvisualmanageroffice2003onhighlightrarelyusedmenuitems"></a><a name="onhighlightrarelyusedmenuitems"></a>CMFCVisualManagerOffice2003::OnHighlightRarelyUsedMenuItems  
 当绘制突出显示的菜单命令时，框架将调用此方法。  
  
```  
virtual void OnHighlightRarelyUsedMenuItems(
    CDC* pDC,  
    CRect rectRarelyUsed);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rectRarelyUsed`  
 指定突出显示的命令的边界的矩形。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生视觉管理器，以自定义突出显示的菜单命令的外观。  
  
##  <a name="a-nameonupdatesystemcolorsa--cmfcvisualmanageroffice2003onupdatesystemcolors"></a><a name="onupdatesystemcolors"></a>CMFCVisualManagerOffice2003::OnUpdateSystemColors  
 系统颜色更改时，框架将调用此函数。  
  
```  
virtual void OnUpdateSystemColors();
```  
  
### <a name="remarks"></a>备注  
 框架将调用此方法作为处理的一部分`WM_SYSCOLORCHANGE`消息。 如果您想要在您的应用程序中的颜色更改时执行自定义代码重写此方法在派生的视觉管理器中。  
  
##  <a name="a-namesetdefaultwinxpcolorsa--cmfcvisualmanageroffice2003setdefaultwinxpcolors"></a><a name="setdefaultwinxpcolors"></a>CMFCVisualManagerOffice2003::SetDefaultWinXPColors  
 指定是否视觉管理器应使用本机 Windows XP 主题颜色或颜色从获取[GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371)。  
  
```  
static void SetDefaultWinXPColors(BOOL bDefaultWinXPColors = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bDefaultWinXPColors`  
 指定是否视觉管理器将使用本机 Windows XP 颜色。  
  
### <a name="remarks"></a>备注  
 如果`bDefaultWinXPColors`是`TRUE`，视觉管理器将使用本机 Windows XP 颜色，如蓝色、 橄榄绿或银色。 否则，可视化管理器将使用从获取的颜色`GetSysColor`。 可视化管理器使用可视元素，如`COLOR_3DFACE`， `COLOR_3DSHADOW`， `COLOR_3DHIGHLIGHT`， `COLOR_3DDKSHADOW`，和`COLOR_3DLIGHT`。  
  
 默认情况下，`CMFCVisualManagerOffice2003`对象使用本机 Windows XP 主题颜色。  
  
##  <a name="a-namesetstatusbarofficexplooka--cmfcvisualmanageroffice2003setstatusbarofficexplook"></a><a name="setstatusbarofficexplook"></a>CMFCVisualManagerOffice2003::SetStatusBarOfficeXPLook  
 指定应使用 Windows XP 全局主题。  
  
```  
static void __stdcall SetStatusBarOfficeXPLook(BOOL bStatusBarOfficeXPLook = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bStatusBarOfficeXPLook`  
 `TRUE`如果 Windows XP 全局主题应使用 （默认值），或`FALSE`如果不是。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesetuseglobalthemea--cmfcvisualmanageroffice2003setuseglobaltheme"></a><a name="setuseglobaltheme"></a>CMFCVisualManagerOffice2003::SetUseGlobalTheme  
 指定的可视化管理器是否使用全局主题。  
  
```  
static void SetUseGlobalTheme(BOOL bUseGlobalTheme = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bUseGlobalTheme`  
 `TRUE`如果您希望视觉管理器中，若要使用全局主题;`FALSE`否则为。  
  
### <a name="remarks"></a>备注  
 如果`CMFCVisualManagerOffice2003`对象使用全局主题，它通过绘制 GUI 元素[CMFCVisualManagerWindows 类](../../mfc/reference/cmfcvisualmanagerwindows-class.md)。  
  
 如果`CMFCVisualManagerOffice2003`对象不使用全局主题，它通过绘制 GUI 元素[CMFCVisualManagerOfficeXP 类](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager 类](../../mfc/reference/cmfcvisualmanager-class.md)   
 [CMFCVisualManagerOfficeXP 类](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)   
 [CMFCVisualManagerWindows 类](../../mfc/reference/cmfcvisualmanagerwindows-class.md)

