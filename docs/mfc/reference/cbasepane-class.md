---
title: CBasePane 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CBasePane
- AFXBASEPANE/CBasePane
- AFXBASEPANE/CBasePane::AccNotifyObjectFocusEvent
- AFXBASEPANE/CBasePane::AddPane
- AFXBASEPANE/CBasePane::AdjustDockingLayout
- AFXBASEPANE/CBasePane::AdjustLayout
- AFXBASEPANE/CBasePane::CalcFixedLayout
- AFXBASEPANE/CBasePane::CanAcceptPane
- AFXBASEPANE/CBasePane::CanAutoHide
- AFXBASEPANE/CBasePane::CanBeAttached
- AFXBASEPANE/CBasePane::CanBeClosed
- AFXBASEPANE/CBasePane::CanBeDocked
- AFXBASEPANE/CBasePane::CanBeResized
- AFXBASEPANE/CBasePane::CanBeTabbedDocument
- AFXBASEPANE/CBasePane::CanFloat
- AFXBASEPANE/CBasePane::CanFocus
- AFXBASEPANE/CBasePane::CopyState
- AFXBASEPANE/CBasePane::CreateDefaultMiniframe
- AFXBASEPANE/CBasePane::CreateEx
- AFXBASEPANE/CBasePane::DockPane
- AFXBASEPANE/CBasePane::DockPaneUsingRTTI
- AFXBASEPANE/CBasePane::DockToFrameWindow
- AFXBASEPANE/CBasePane::DoesAllowDynInsertBefore
- AFXBASEPANE/CBasePane::EnableDocking
- AFXBASEPANE/CBasePane::EnableGripper
- AFXBASEPANE/CBasePane::FloatPane
- AFXBASEPANE/CBasePane::get_accHelpTopic
- AFXBASEPANE/CBasePane::get_accSelection
- AFXBASEPANE/CBasePane::GetCaptionHeight
- AFXBASEPANE/CBasePane::GetControlBarStyle
- AFXBASEPANE/CBasePane::GetCurrentAlignment
- AFXBASEPANE/CBasePane::GetDockingMode
- AFXBASEPANE/CBasePane::GetDockSiteFrameWnd
- AFXBASEPANE/CBasePane::GetEnabledAlignment
- AFXBASEPANE/CBasePane::GetMFCStyle
- AFXBASEPANE/CBasePane::GetPaneIcon
- AFXBASEPANE/CBasePane::GetPaneRow
- AFXBASEPANE/CBasePane::GetPaneStyle
- AFXBASEPANE/CBasePane::GetParentDockSite
- AFXBASEPANE/CBasePane::GetParentMiniFrame
- AFXBASEPANE/CBasePane::GetParentTabbedPane
- AFXBASEPANE/CBasePane::GetParentTabWnd
- AFXBASEPANE/CBasePane::GetRecentVisibleState
- AFXBASEPANE/CBasePane::HideInPrintPreviewMode
- AFXBASEPANE/CBasePane::InsertPane
- AFXBASEPANE/CBasePane::IsAccessibilityCompatible
- AFXBASEPANE/CBasePane::IsAutoHideMode
- AFXBASEPANE/CBasePane::IsDialogControl
- AFXBASEPANE/CBasePane::IsDocked
- AFXBASEPANE/CBasePane::IsFloating
- AFXBASEPANE/CBasePane::IsHorizontal
- AFXBASEPANE/CBasePane::IsInFloatingMultiPaneFrameWnd
- AFXBASEPANE/CBasePane::IsMDITabbed
- AFXBASEPANE/CBasePane::IsPaneVisible
- AFXBASEPANE/CBasePane::IsPointNearDockSite
- AFXBASEPANE/CBasePane::IsResizable
- AFXBASEPANE/CBasePane::IsRestoredFromRegistry
- AFXBASEPANE/CBasePane::IsTabbed
- AFXBASEPANE/CBasePane::IsVisible
- AFXBASEPANE/CBasePane::LoadState
- AFXBASEPANE/CBasePane::MoveWindow
- AFXBASEPANE/CBasePane::OnAfterChangeParent
- AFXBASEPANE/CBasePane::OnBeforeChangeParent
- AFXBASEPANE/CBasePane::OnDrawCaption
- AFXBASEPANE/CBasePane::OnMovePaneDivider
- AFXBASEPANE/CBasePane::OnPaneContextMenu
- AFXBASEPANE/CBasePane::OnRemoveFromMiniFrame
- AFXBASEPANE/CBasePane::OnSetAccData
- AFXBASEPANE/CBasePane::PaneFromPoint
- AFXBASEPANE/CBasePane::RecalcLayout
- AFXBASEPANE/CBasePane::RemovePaneFromDockManager
- AFXBASEPANE/CBasePane::SaveState
- AFXBASEPANE/CBasePane::SelectDefaultFont
- AFXBASEPANE/CBasePane::SetControlBarStyle
- AFXBASEPANE/CBasePane::SetDockingMode
- AFXBASEPANE/CBasePane::SetPaneAlignment
- AFXBASEPANE/CBasePane::SetPaneStyle
- AFXBASEPANE/CBasePane::SetWindowPos
- AFXBASEPANE/CBasePane::ShowPane
- AFXBASEPANE/CBasePane::StretchPane
- AFXBASEPANE/CBasePane::UndockPane
- AFXBASEPANE/CBasePane::DoPaint
dev_langs:
- C++
helpviewer_keywords:
- CBasePane [MFC], AccNotifyObjectFocusEvent
- CBasePane [MFC], AddPane
- CBasePane [MFC], AdjustDockingLayout
- CBasePane [MFC], AdjustLayout
- CBasePane [MFC], CalcFixedLayout
- CBasePane [MFC], CanAcceptPane
- CBasePane [MFC], CanAutoHide
- CBasePane [MFC], CanBeAttached
- CBasePane [MFC], CanBeClosed
- CBasePane [MFC], CanBeDocked
- CBasePane [MFC], CanBeResized
- CBasePane [MFC], CanBeTabbedDocument
- CBasePane [MFC], CanFloat
- CBasePane [MFC], CanFocus
- CBasePane [MFC], CopyState
- CBasePane [MFC], CreateDefaultMiniframe
- CBasePane [MFC], CreateEx
- CBasePane [MFC], DockPane
- CBasePane [MFC], DockPaneUsingRTTI
- CBasePane [MFC], DockToFrameWindow
- CBasePane [MFC], DoesAllowDynInsertBefore
- CBasePane [MFC], EnableDocking
- CBasePane [MFC], EnableGripper
- CBasePane [MFC], FloatPane
- CBasePane [MFC], get_accHelpTopic
- CBasePane [MFC], get_accSelection
- CBasePane [MFC], GetCaptionHeight
- CBasePane [MFC], GetControlBarStyle
- CBasePane [MFC], GetCurrentAlignment
- CBasePane [MFC], GetDockingMode
- CBasePane [MFC], GetDockSiteFrameWnd
- CBasePane [MFC], GetEnabledAlignment
- CBasePane [MFC], GetMFCStyle
- CBasePane [MFC], GetPaneIcon
- CBasePane [MFC], GetPaneRow
- CBasePane [MFC], GetPaneStyle
- CBasePane [MFC], GetParentDockSite
- CBasePane [MFC], GetParentMiniFrame
- CBasePane [MFC], GetParentTabbedPane
- CBasePane [MFC], GetParentTabWnd
- CBasePane [MFC], GetRecentVisibleState
- CBasePane [MFC], HideInPrintPreviewMode
- CBasePane [MFC], InsertPane
- CBasePane [MFC], IsAccessibilityCompatible
- CBasePane [MFC], IsAutoHideMode
- CBasePane [MFC], IsDialogControl
- CBasePane [MFC], IsDocked
- CBasePane [MFC], IsFloating
- CBasePane [MFC], IsHorizontal
- CBasePane [MFC], IsInFloatingMultiPaneFrameWnd
- CBasePane [MFC], IsMDITabbed
- CBasePane [MFC], IsPaneVisible
- CBasePane [MFC], IsPointNearDockSite
- CBasePane [MFC], IsResizable
- CBasePane [MFC], IsRestoredFromRegistry
- CBasePane [MFC], IsTabbed
- CBasePane [MFC], IsVisible
- CBasePane [MFC], LoadState
- CBasePane [MFC], MoveWindow
- CBasePane [MFC], OnAfterChangeParent
- CBasePane [MFC], OnBeforeChangeParent
- CBasePane [MFC], OnDrawCaption
- CBasePane [MFC], OnMovePaneDivider
- CBasePane [MFC], OnPaneContextMenu
- CBasePane [MFC], OnRemoveFromMiniFrame
- CBasePane [MFC], OnSetAccData
- CBasePane [MFC], PaneFromPoint
- CBasePane [MFC], RecalcLayout
- CBasePane [MFC], RemovePaneFromDockManager
- CBasePane [MFC], SaveState
- CBasePane [MFC], SelectDefaultFont
- CBasePane [MFC], SetControlBarStyle
- CBasePane [MFC], SetDockingMode
- CBasePane [MFC], SetPaneAlignment
- CBasePane [MFC], SetPaneStyle
- CBasePane [MFC], SetWindowPos
- CBasePane [MFC], ShowPane
- CBasePane [MFC], StretchPane
- CBasePane [MFC], UndockPane
- CBasePane [MFC], DoPaint
ms.assetid: 8163dd51-d7c7-4def-9c74-61f8ecdfad82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5cbd24042e7f309a28cea5e72b6a134f3205e541
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357954"
---
# <a name="cbasepane-class"></a>CBasePane 类
MFC 中的所有窗格的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class CBasePane : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|`CBasePane::CBasePane`|默认构造函数。|  
|`CBasePane::~CBasePane`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|`CBasePane::accHitTest`|由框架调用以检索屏幕上给定点处的子元素或子对象。 (重写[CWnd::accHitTest](../../mfc/reference/cwnd-class.md#acchittest)。)|  
|`CBasePane::accLocation`|由框架调用以检索指定的对象的当前屏幕位置。 (重写[CWnd::accLocation](../../mfc/reference/cwnd-class.md#acclocation)。)|  
|[CBasePane::AccNotifyObjectFocusEvent](#accnotifyobjectfocusevent)|`CBasePane` 不使用此方法。|  
|`CBasePane::accSelect`|由框架调用以修改选定内容或移动指定对象的键盘焦点。 (重写[CWnd::accSelect](../../mfc/reference/cwnd-class.md#accselect)。)|  
|[CBasePane::AddPane](#addpane)|将一个窗格添加到停靠管理器。|  
|[Cbasepane:: Adjustdockinglayout](#adjustdockinglayout)|将重定向到停靠管理器的调用来调整停靠布局。|  
|[Cbasepane:: Adjustlayout](#adjustlayout)|当窗格中应调整其内部的布局时，由框架调用。|  
|[Cbasepane:: Calcfixedlayout](#calcfixedlayout)|计算的控件条的水平大小。|  
|[Cbasepane:: Canacceptpane](#canacceptpane)|确定是否可以将另一个窗格停靠到窗格中。|  
|[CBasePane::CanAutoHide](#canautohide)|确定窗格中是否支持自动隐藏模式。|  
|[CBasePane::CanBeAttached](#canbeattached)|确定是否可将窗格停靠到另一个窗格。|  
|[Cbasepane:: Canbeclosed](#canbeclosed)|确定是否可以关闭窗格。|  
|[CBasePane::CanBeDocked](#canbedocked)|确定是否可将窗格停靠到另一个窗格。|  
|[CBasePane::CanBeResized](#canberesized)|确定是否可以调整窗格的大小。|  
|[CBasePane::CanBeTabbedDocument](#canbetabbeddocument)|指定是否可将窗格转换 MDI 选项卡式文档。|  
|[CBasePane::CanFloat](#canfloat)|确定是否可以浮动窗格。|  
|[CBasePane::CanFocus](#canfocus)|指定窗格中是否可以接收焦点。|  
|[CBasePane::CopyState](#copystate)|将复制给定的窗格中的状态。|  
|[CBasePane::CreateDefaultMiniframe](#createdefaultminiframe)|如果可以浮动窗格中，将创建微型框架窗口。|  
|[Cbasepane:: Createex](#createex)|创建窗格控件。|  
|[Cbasepane:: Dockpane](#dockpane)|窗格停靠到另一个窗格或框架窗口。|  
|[CBasePane::DockPaneUsingRTTI](#dockpaneusingrtti)|通过使用运行时类型信息停靠窗格。|  
|[CBasePane::DockToFrameWindow](#docktoframewindow)|可停靠窗格停靠到的帧。|  
|[Cbasepane:: Doesallowdyninsertbefore](#doesallowdyninsertbefore)|确定是否另一个窗格可以动态地插入此窗格之间的父框架。|  
|[CBasePane::EnableDocking](#enabledocking)|启用窗格的停靠到主框架。|  
|[CBasePane::EnableGripper](#enablegripper)|启用或禁用控制手柄。 如果启用了控制手柄，用户可以拖动它以重新定位窗格。|  
|`CBasePane::FillWindowRect`|内部使用。|  
|[CBasePane::FloatPane](#floatpane)|浮动窗格。|  
|`CBasePane::get_accChild`|由框架调用以检索指定子级的 `IDispatch` 接口地址。 (重写[CWnd::get_accChild](../../mfc/reference/cwnd-class.md#get_accchild)。)|  
|`CBasePane::get_accChildCount`|由框架调用以检索属于此对象的子级的数量。 (重写[CWnd::get_accChildCount](../../mfc/reference/cwnd-class.md#get_accchildcount)。)|  
|`CBasePane::get_accDefaultAction`|由框架调用以检索描述对象默认操作的字符串。 (重写[CWnd::get_accDefaultAction](../../mfc/reference/cwnd-class.md#get_accdefaultaction)。)|  
|`CBasePane::get_accDescription`|由框架调用以检索描述指定对象的可视外观的字符串。 (重写[CWnd::get_accDescription](../../mfc/reference/cwnd-class.md#get_accdescription)。)|  
|`CBasePane::get_accFocus`|由框架调用以检索具有键盘焦点的对象。 (重写[CWnd::get_accFocus](../../mfc/reference/cwnd-class.md#get_accfocus)。)|  
|`CBasePane::get_accHelp`|由框架调用以检索对象的帮助属性字符串。 (重写[CWnd::get_accHelp](../../mfc/reference/cwnd-class.md#get_acchelp)。)|  
|[CBasePane::get_accHelpTopic](#get_acchelptopic)|由框架调用以检索与指定的对象相关联的 WinHelp 文件的完整路径和该文件中的相应主题的标识符。 (重写[CWnd::get_accHelpTopic](../../mfc/reference/cwnd-class.md#get_acchelptopic)。)|  
|`CBasePane::get_accKeyboardShortcut`|由框架调用以检索对象的指定的快捷键。 (重写[CWnd::get_accKeyboardShortcut](../../mfc/reference/cwnd-class.md#get_acckeyboardshortcut)。)|  
|`CBasePane::get_accName`|由框架调用以检索指定对象的名称。 (重写[CWnd::get_accName](../../mfc/reference/cwnd-class.md#get_accname)。)|  
|`CBasePane::get_accParent`|由框架检索调用`IDispatch`的父对象的接口。 (重写[CWnd::get_accParent](../../mfc/reference/cwnd-class.md#get_accparent)。)|  
|`CBasePane::get_accRole`|由框架调用以检索描述指定对象的角色的信息。 (重写[CWnd::get_accRole](../../mfc/reference/cwnd-class.md#get_accrole)。)|  
|[CBasePane::get_accSelection](#get_accselection)|由框架调用以检索该对象的选定子级。 (重写[CWnd::get_accSelection](../../mfc/reference/cwnd-class.md#get_accselection)。)|  
|`CBasePane::get_accState`|由框架调用以检索指定对象的当前状态。 (重写[CWnd::get_accState](../../mfc/reference/cwnd-class.md#get_accstate)。)|  
|`CBasePane::get_accValue`|由框架调用以检索指定对象的值。 (重写[CWnd::get_accValue](../../mfc/reference/cwnd-class.md#get_accvalue)。)|  
|[Cbasepane:: Getcaptionheight](#getcaptionheight)|返回标题高度。|  
|[CBasePane::GetControlBarStyle](#getcontrolbarstyle)|返回控件栏样式。|  
|[CBasePane::GetCurrentAlignment](#getcurrentalignment)|返回当前窗格中对齐方式。|  
|[Cbasepane:: Getdockingmode](#getdockingmode)|返回当前窗格停靠模式。|  
|[CBasePane::GetDockSiteFrameWnd](#getdocksiteframewnd)|返回指向将窗格停靠站点窗口的指针。|  
|[CBasePane::GetEnabledAlignment](#getenabledalignment)|返回到窗格中应用的 CBRS_ALIGN_ 样式。|  
|[CBasePane::GetMFCStyle](#getmfcstyle)|MFC 的针对返回的窗格样式。|  
|[CBasePane::GetPaneIcon](#getpaneicon)|返回窗格图标的句柄。|  
|`CBasePane::GetPaneRect`|内部使用。|  
|[CBasePane::GetPaneRow](#getpanerow)|返回一个指向[CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)停靠窗格中的位置的对象。|  
|[CBasePane::GetPaneStyle](#getpanestyle)|返回的窗格样式。|  
|[CBasePane::GetParentDockSite](#getparentdocksite)|将指针返回到父停靠站点。|  
|[CBasePane::GetParentMiniFrame](#getparentminiframe)|返回到父微型框架窗口的指针。|  
|[CBasePane::GetParentTabbedPane](#getparenttabbedpane)|将指针返回到父选项卡式窗格。|  
|[CBasePane::GetParentTabWnd](#getparenttabwnd)|返回指向选项卡内的父窗口的指针。|  
|[CBasePane::GetRecentVisibleState](#getrecentvisiblestate)|从存档在还原一个窗格时，框架将调用此方法。|  
|[CBasePane::HideInPrintPreviewMode](#hideinprintpreviewmode)|指定是否在打印预览中隐藏窗格。|  
|[CBasePane::InsertPane](#insertpane)|注册到停靠管理器指定窗格。|  
|[CBasePane::IsAccessibilityCompatible](#isaccessibilitycompatible)|指定窗格中是否支持 Active Accessibility。|  
|[CBasePane::IsAutoHideMode](#isautohidemode)|确定一个窗格是否在自动隐藏模式下。|  
|[CBasePane::IsDialogControl](#isdialogcontrol)|指定是否在窗格中，对话框控件。|  
|[CBasePane::IsDocked](#isdocked)|确定是否停靠窗格。|  
|[CBasePane::IsFloating](#isfloating)|确定是否浮动窗格。|  
|[CBasePane::IsHorizontal](#ishorizontal)|确定是否水平停靠的窗格。|  
|[CBasePane::IsInFloatingMultiPaneFrameWnd](#isinfloatingmultipaneframewnd)|指定窗格是否在多窗格框架窗口中。|  
|[CBasePane::IsMDITabbed](#ismditabbed)|确定窗格中是否已添加到选项卡式文档作为 MDI 子窗口。|  
|[CBasePane::IsPaneVisible](#ispanevisible)|指定是否`WS_VISIBLE`标志设置为窗格。|  
|[CBasePane::IsPointNearDockSite](#ispointneardocksite)|确定指定的点是否在停靠站点附近。|  
|[Cbasepane:: Isresizable](#isresizable)|确定是否可以调整窗格的大小。|  
|[CBasePane::IsRestoredFromRegistry](#isrestoredfromregistry)|确定是否从注册表还原窗格。|  
|[CBasePane::IsTabbed](#istabbed)|确定是否已在选项卡式窗口选项卡控件中插入窗格。|  
|`CBasePane::IsTooltipTopmost`|内部使用。|  
|[CBasePane::IsVisible](#isvisible)|确定窗格是否可见。|  
|[CBasePane::LoadState](#loadstate)|从注册表加载窗格状态。|  
|[CBasePane::MoveWindow](#movewindow)|将窗格的移动。|  
|[CBasePane::OnAfterChangeParent](#onafterchangeparent)|当窗格的父发生更改时由框架调用。|  
|[CBasePane::OnBeforeChangeParent](#onbeforechangeparent)|恰好在窗格中更改其父窗口之前，由框架调用。|  
|[CBasePane::OnDrawCaption](#ondrawcaption)|绘制标题时，框架将调用此方法。|  
|[CBasePane::OnMovePaneDivider](#onmovepanedivider)|当前未使用此方法。|  
|[CBasePane::OnPaneContextMenu](#onpanecontextmenu)|在构建具有窗格的列表菜单时由框架调用。|  
|[CBasePane::OnRemoveFromMiniFrame](#onremovefromminiframe)|从其父微型框架窗口删除窗格中时，由框架调用。|  
|[Cbasepane:: Onsetaccdata](#onsetaccdata)|`CBasePane` 不使用此方法。|  
|`CBasePane::OnUpdateCmdUI`|内部使用。|  
|[CBasePane::PaneFromPoint](#panefrompoint)|返回包含给定的点的窗格。|  
|`CBasePane::PreTranslateMessage`|在将窗口消息发送到 [TranslateMessage](../../mfc/reference/cwinapp-class.md) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) Windows 函数之前，由 [CWinApp](http://msdn.microsoft.com/library/windows/desktop/ms644934) 类用于对此消息进行转换。 （重写 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。）|  
|[CBasePane::RecalcLayout](#recalclayout)|`CBasePane` 不使用此方法。|  
|[CBasePane::RemovePaneFromDockManager](#removepanefromdockmanager)|注销一个窗格并将其从列表中到停靠管理器中删除。|  
|[CBasePane::SaveState](#savestate)|将窗格的状态保存到注册表。|  
|[CBasePane::SelectDefaultFont](#selectdefaultfont)|选择给定的设备上下文的默认字体。|  
|`CBasePane::Serialize`|从存档读取该对象或将该对象写入存档。 （重写 [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)。）|  
|[CBasePane::SetControlBarStyle](#setcontrolbarstyle)|设置控件栏样式。|  
|[CBasePane::SetDockingMode](#setdockingmode)|设置窗格的停靠模式。|  
|`CBasePane::SetMDITabbed`|内部使用。|  
|[CBasePane::SetPaneAlignment](#setpanealignment)|设置窗格中的对齐方式。|  
|`CBasePane::SetPaneRect`|内部使用。|  
|[CBasePane::SetPaneStyle](#setpanestyle)|设置窗格中的样式。|  
|`CBasePane::SetRestoredFromRegistry`|内部使用。|  
|[CBasePane::SetWindowPos](#setwindowpos)|更改大小、 位置和 Z 顺序的窗格。|  
|[CBasePane::ShowPane](#showpane)|显示或隐藏窗格。|  
|[Cbasepane:: Stretchpane](#stretchpane)|垂直或水平拉伸窗格。|  
|[CBasePane::UndockPane](#undockpane)|从停靠站点、 默认滑块或它当前停靠的微型框架窗口删除窗格。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CBasePane::DoPaint](#dopaint)|填充窗格的背景。|  
  
## <a name="remarks"></a>备注  
 如果你想要创建窗格中支持的类，MFC 中可用的扩展坞功能，你必须从中进行派生`CBasePane`或从[CPane 类](../../mfc/reference/cpane-class.md)。  
  
## <a name="customization-tips"></a>自定义提示  
 以下自定义提示适用于`CBasePane Class`和从其继承的任何类：  
  
-   当你创建了窗格时，可以应用几种新样式：  
  
    - `AFX_CBRS_FLOAT` 使窗格浮动。  
  
    - `AFX_CBRS_AUTOHIDE` 启用自动隐藏模式。  
  
    - `AFX_CBRS_CLOSE` 使即将关闭 （隐藏） 的窗格。  
  
     这些是你可以将与按位或运算结合的标志。  
  
 `CBasePane` 实现以下虚拟布尔方法以反映这些标志： [cbasepane:: Canbeclosed](#canbeclosed)， [CBasePane::CanAutoHide](#canautohide)， [CBasePane::CanFloat](#canfloat)。 你可以重写它们中派生类进行自定义它们的行为。  
  
-   可以通过重写来自定义停靠行为[cbasepane:: Canacceptpane](#canacceptpane)。 具有返回你窗格`FALSE`从此方法若要防止另一个窗格停靠到它。  
  
-   如果你想要创建静态窗格中，不能 float 和，可阻止其他窗格停靠在它之前 （类似于在 OutlookDemo 示例中的 Outlook 栏）、 将其创建为非浮点和重写[cbasepane:: Doesallowdyninsertbefore](#doesallowdyninsertbefore)返回`FALSE`。 默认实现返回`FALSE`如果窗格中创建没有`AFX_CBRS_FLOAT`样式。  
  
-   创建具有 Id 的所有窗格，而-1。  
  
-   若要确定窗格可见性，请使用[CBasePane::IsVisible](#isvisible)。 它能正确地处理可见性状态中选项卡式和自动隐藏模式。  
  
-   如果你想要创建非浮点可调整大小的窗格，则创建它而不`AFX_CBRS_FLOAT`样式和调用[CFrameWnd::DockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar)。  
  
-   若要从停靠布局中排除一个窗格或从其停靠栏中删除一个工具栏，调用[CBasePane::UndockPane](#undockpane)。 在自动隐藏模式下的窗格或驻留在选项卡式窗口的选项卡的窗格，则不调用此方法。  
  
-   如果你希望为浮动或取消停靠在自动隐藏模式下的窗格，则必须调用[CDockablePane::SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode)与`FALSE`的第一个参数，然后才能调用[CBasePane::FloatPane](#floatpane)或[CBasePane::UndockPane](#undockpane)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法`CBasePane`类。 该示例演示如何检索从窗格`CFrameWndEx`类以及如何设置停靠模式、 窗格中的对齐方式，和窗格中的样式。 代码摘自[Word Pad 示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_WordPad#2](../../mfc/reference/codesnippet/cpp/cbasepane-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxbasepane.h  
  
##  <a name="accnotifyobjectfocusevent"></a>  CBasePane::AccNotifyObjectFocusEvent  
 `CBasePane` 不使用此方法。  
  
```  
virtual void AccNotifyObjectFocusEvent(int);
```  
  
### <a name="parameters"></a>参数  
 [in] `int`  
 未使用。  
  
##  <a name="addpane"></a>  CBasePane::AddPane  
 将一个窗格添加到停靠管理器。  
  
```  
void AddPane(CBasePane* pBar);
```  
  
### <a name="parameters"></a>参数  
 [in] `pBar`  
 指向要添加的窗格的指针。  
  
### <a name="remarks"></a>备注  
 这是将一个窗格添加到停靠管理器的便捷方法。 通过使用此方法，无需编写代码，它分析的一种的父框架。  
  
 有关详细信息，请参阅[CDockingManager 类](../../mfc/reference/cdockingmanager-class.md)和[CMDIFrameWndEx::AddPane](../../mfc/reference/cmdiframewndex-class.md#addpane)。  
  
##  <a name="adjustdockinglayout"></a>  Cbasepane:: Adjustdockinglayout  
 将重定向到停靠管理器的调用来调整停靠布局。  
  
```  
virtual void AdjustDockingLayout(HDWP hdwp=NULL);
```  
  
### <a name="parameters"></a>参数  
 [out] `hdwp`  
 一个包含多个窗口的位置的结构句柄。  
  
### <a name="remarks"></a>备注  
 这是调整停靠布局的便捷方法。 通过使用此方法，无需编写代码，它分析的一种的父框架。  
  
 有关详细信息，请参阅[CDockingManager::AdjustDockingLayout](../../mfc/reference/cdockingmanager-class.md#adjustdockinglayout)  
  
##  <a name="adjustlayout"></a>  Cbasepane:: Adjustlayout  
 由框架调用以调整窗格中的内部布局。  
  
```  
virtual void AdjustLayout();
```  
  
### <a name="remarks"></a>备注  
 在窗格中进行调整其内部的布局时，框架将调用此方法。 基实现没有任何影响。  
  
##  <a name="calcfixedlayout"></a>  Cbasepane:: Calcfixedlayout  
 计算的控件条的水平大小。  
  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>参数  
 [in] `bStretch`  
 指示是否应被栏拉伸到的帧的大小。 `bStretch`时栏 （不可用于停靠） 停靠栏并不为 0 时停靠或浮动 （适用于停靠），则为非零参数。  
  
 [in] `bHorz`  
 指示该拆分条是水平或垂直方向。 `bHorz`如果栏是水平方向和垂直方向是否为 0，则为非零参数。  
  
### <a name="return-value"></a>返回值  
 控件条的大小，以像素为单位的`CSize`对象。  
  
### <a name="remarks"></a>备注  
 请参阅备注部分中[CControlBar::CalcFixedLayout](../../mfc/reference/ccontrolbar-class.md#calcfixedlayout)  
  
##  <a name="canacceptpane"></a>  Cbasepane:: Canacceptpane  
 确定是否可以将另一个窗格停靠到窗格中。  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `pBar`  
 指向要将停靠的窗格的指针。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果可以接受另一个窗格中;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 框架在调用此方法之前它停靠窗格指定`pBar`到当前窗格中。  
  
 使用此方法与[CBasePane::CanBeDocked](#canbedocked)方法可控制如何将窗格停靠到你的应用程序中的其他窗格。  
  
 默认实现返回 `FALSE`。  
  
##  <a name="canautohide"></a>  CBasePane::CanAutoHide  
 确定窗格中是否支持自动隐藏模式。  
  
```  
virtual BOOL CanAutoHide() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果此窗格支持自动隐藏模式;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 框架调用此函数可确定窗格中是否支持自动隐藏模式。  
  
 在构造期间中,，你可以设置此功能通过将传递`AFX_CBRS_AUTOHIDE`标志切换为[cbasepane:: Createex](#createex)。  
  
 默认实现可检查`AFX_CBRS_AUTOHIDE`标志。 重写此方法在派生类以自定义此行为。  
  
##  <a name="canbeattached"></a>  CBasePane::CanBeAttached  
 确定是否可将窗格停靠到另一个窗格或框架窗口。  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果窗格可以停靠到另一个窗格或框架窗口;，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 默认实现返回 `FALSE`。 重写此方法在派生类来启用或禁用的功能而无需调用停靠[CBasePane::EnableDocking](#enabledocking)。  
  
##  <a name="canbeclosed"></a>  Cbasepane:: Canbeclosed  
 确定是否可以关闭窗格。  
  
```  
virtual BOOL CanBeClosed() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果可以关闭窗格;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 框架调用此方法以确定是否可以关闭窗格。 如果该方法返回`TRUE`、**关闭**按钮添加到窗格的标题栏或浮动窗格中时，到窗格的袖珍框架窗口的标题栏。  
  
 在构造期间中,，你可以设置此功能通过将传递`AFX_CBRS_CLOSE`标志切换为[cbasepane:: Createex](#createex)。  
  
 默认实现可检查`AFX_CBRS_CLOSE`标志。  
  
##  <a name="canbedocked"></a>  CBasePane::CanBeDocked  
 确定是否可将窗格停靠到另一个窗格。  
  
```  
virtual BOOL CanBeDocked(CBasePane* pDockBar) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `pDockBar`  
 指向另一个窗格的指针。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果此窗格可以停靠到另一个窗格中;，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 框架在调用此方法之前它停靠窗格指定`pDockBar`到当前窗格中。  
  
 使用此方法与[cbasepane:: Canacceptpane](#canacceptpane)方法可控制如何将窗格停靠到你的应用程序中的其他窗格。  
  
 默认实现返回 `FALSE`。  
  
##  <a name="canberesized"></a>  CBasePane::CanBeResized  
 确定是否可以调整窗格的大小。  
  
```  
virtual BOOL CanBeResized() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果可调整大小的窗格中;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法检查`AFX_CBRS_RESIZE`标志，指定在默认情况下`CBasePane::OnCreate`。 如果未指定此标志，到停靠管理器标志而不是停靠其内部可移动窗格。  
  
##  <a name="canbetabbeddocument"></a>  CBasePane::CanBeTabbedDocument  
 指定是否可将窗格转换 MDI 选项卡式文档。  
  
```  
virtual BOOL CanBeTabbedDocument() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果窗格可以转换到选项卡式文档中。否则为`FALSE`。 `CBasePane::CanBeTabbedDocument` 始终返回 `FALSE`。  
  
### <a name="remarks"></a>备注  
 唯一对象的某些`CBasePane`-派生类型，如[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)，可以转换为选项卡式文档。  
  
##  <a name="canfloat"></a>  CBasePane::CanFloat  
 确定是否可以浮动窗格。  
  
```  
virtual BOOL CanFloat() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果窗格可以浮动;，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 框架调用此方法以确定是否可以浮动窗格。  
  
 在构造期间中,，你可以设置此功能通过将传递`AFX_CBRS_FLOAT`标志切换为[cbasepane:: Createex](#createex)。  
  
> [!NOTE]
>  框架将假定非浮动窗格是静态的无法更改其停靠状态。 因此，框架不保存非浮动窗格的停靠状态。  
  
 默认实现可检查`AFX_CBRS_FLOAT`样式。  
  
##  <a name="canfocus"></a>  CBasePane::CanFocus  
 指定窗格中是否可以接收焦点。  
  
```  
virtual BOOL CanFocus() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果窗格可以接收焦点，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生类来控制焦点。 例如，因为工具栏无法接收焦点，则此方法返回`FALSE`当工具栏对象上调用。  
  
 框架将尝试时停靠或浮动窗格中设置输入的焦点。  
  
##  <a name="copystate"></a>  CBasePane::CopyState  
 将复制给定的窗格中的状态。  
  
```  
virtual void CopyState(CBasePane* pOrgBar);
```  
  
### <a name="parameters"></a>参数  
 [in] `pOrgBar`  
 指向另一个窗格的指针。  
  
### <a name="remarks"></a>备注  
 此方法会复制状态从`pOrgBar`此窗格中。  
  
##  <a name="createdefaultminiframe"></a>  CBasePane::CreateDefaultMiniframe  
 如果可以浮动窗格中，此方法会为它创建微型框架窗口。  
  
```  
virtual CPaneFrameWnd* CreateDefaultMiniframe(CRect rectInitial);
```  
  
### <a name="parameters"></a>参数  
 [in] `rectInitial`  
 指定微型框架窗口的初始坐标。  
  
### <a name="return-value"></a>返回值  
 指向新的微型框架窗口的指针或`NULL`如果创建失败。  
  
### <a name="remarks"></a>备注  
 当一个窗格切换到浮动状态时，框架将调用此方法。 方法创建微型框架窗口，并将窗格中附加到此窗口。  
  
 默认实现返回 `NULL`。  
  
##  <a name="createex"></a>  Cbasepane:: Createex  
 创建窗格控件。  
  
```  
virtual BOOL CreateEx(
    DWORD dwStyleEx,  
    LPCTSTR lpszClassName,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    DWORD dwControlBarStyle=0,  
    CCreateContext* pContext=NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwStyleEx`  
 扩展的样式 (请参阅[CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex)有关详细信息)。  
  
 [in] `lpszClassName`  
 窗口类名称。  
  
 [in] `lpszWindowName`  
 窗口名称。  
  
 [in] `dwStyle`  
 窗口样式 (请参阅[CWnd::CreateEx](../../mfc/reference/cwnd-class.md#createex))。  
  
 [in] `rect`  
 初始的矩形。  
  
 [in] `pParentWnd`  
 指向父窗口的指针。  
  
 [in] `nID`  
 指定窗格 id。 必须是唯一的。  
  
 [in] `dwControlBarStyle`  
 样式标志窗格。  
  
 [in] `pContext`  
 指向的指针 `CcreateContext`  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果成功，则创建窗格否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 创建类窗口的`lpszClassName`。 如果指定`WS_CAPTION`，此方法清除`WS_CAPTION`样式位，集`CBasePane::m_bHasCaption`到`TRUE`，因为库不支持带有字幕的窗格。  
  
 你可以使用子窗口样式和条形图 (CBRS_) 样式的 MFC 控件的任意组合。  
  
 库将添加一些用于窗格的新样式。 下表描述了新的样式：  
  
|样式|描述|  
|-----------|-----------------|  
|`AFX_CBRS_FLOAT`|该窗格可以浮动。|  
|`AFX_CBRS_AUTOHIDE`|窗格支持自动隐藏模式|  
|`AFX_CBRS_RESIZE`|可以调整大小的窗格。 **重要说明：** 未实现此样式。|  
|`AFX_CBRS_CLOSE`|可以关闭窗格。|  
|`AFX_CBRS_AUTO_ROLLUP`|可将其汇总窗格中，当它浮动。|  
|`AFX_CBRS_REGULAR_TABS`|当一个窗格停靠到另一个具有此样式的窗格中时，将创建常规选项卡式的窗口。 (有关详细信息，请参阅[CTabbedPane 类](../../mfc/reference/ctabbedpane-class.md)。)|  
|`AFX_CBRS_OUTLOOK_TABS`|当一个窗格停靠到另一个具有此样式的窗格中时，将创建 Outlook 样式选项卡式的窗口。 (有关详细信息，请参阅[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。)|  
  
 若要使用的新样式，指定在`dwControlBarStyle`。  
  
##  <a name="dockpane"></a>  Cbasepane:: Dockpane  
 窗格停靠到另一个窗格或框架窗口。  
  
```  
virtual BOOL DockPane(
    CBasePane* pDockBar,  
    LPCRECT lpRect,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDockBar`  
 指向另一个窗格的指针。  
  
 [in] `lpRect`  
 指定目标矩形。  
  
 [in] `dockMethod`  
 指定的停靠的方法。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果已成功，则停靠控件条，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用此函数可将一个窗格停靠到另一个窗格或停靠栏 ( [CDockSite 类](../../mfc/reference/cdocksite-class.md)) 指定`pDockBar`，或到主框架如果`pDockBar`是`NULL`。  
  
 `dockMethod` 指定如何停靠窗格。 请参阅[CPane::DockPane](../../mfc/reference/cpane-class.md#dockpane)有关可能的值的列表。  
  
##  <a name="dockpaneusingrtti"></a>  CBasePane::DockPaneUsingRTTI  
 通过使用运行时类型信息停靠窗格。  
  
```  
void DockPaneUsingRTTI(BOOL bUseDockSite);
```  
  
### <a name="parameters"></a>参数  
 [in] `bUseDockSite`  
 如果`TRUE`，到停靠站点停靠。 如果`FALSE`，将停靠到父框架。  
  
##  <a name="docktoframewindow"></a>  CBasePane::DockToFrameWindow  
 可停靠窗格停靠到的帧。  
  
```  
virtual BOOL DockToFrameWindow(
    DWORD dwAlignment,  
    LPCRECT lpRect = NULL,  
    DWORD dwDockFlags = DT_DOCK_LAST,  
    CBasePane* pRelativeBar = NULL,  
    int nRelativeIndex = -1,  
    BOOL bOuterEdge = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwAlignment`  
 你想要停靠的窗格中的父框架的一端。  
  
 [in] `lpRect`  
 所需的大小。  
  
 [in] `dwDockFlags`  
 已忽略。  
  
 [in] `pRelativeBar`  
 已忽略。  
  
 [in] `nRelativeIndex`  
 已忽略。  
  
 [in] `bOuterEdge`  
 如果`TRUE`还有其他可停靠窗格在指定的一侧`dwAlignment`，窗格停靠在其他窗格中，更接近于父框架边缘。 如果`FALSE`，窗格停靠在更接近的工作区的中心。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果此方法成功，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 如果窗格分隔线，此方法将失败 ( [CPaneDivider 类](../../mfc/reference/cpanedivider-class.md)) 无法创建。 否则，它始终返回`TRUE`。  
  
##  <a name="doesallowdyninsertbefore"></a>  Cbasepane:: Doesallowdyninsertbefore  
 确定是否另一个窗格可以动态地插入此窗格之间的父框架。  
  
```  
virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果用户可以插入另一个窗格中;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 框架调用此方法以确定用户是否可以动态插入之前此窗格中的窗格。  
  
 例如，假设你的应用程序创建停靠在框架 （如 Outlook 栏中） 的左侧窗格。 若要防止用户停靠到第一个窗格的左侧的另一个窗格中，重写此方法，并返回`FALSE`。  
  
 我们建议你重写此方法，并返回`FALSE`非浮动窗格派生自[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)。  
  
 默认实现返回 `TRUE`。  
  
##  <a name="dopaint"></a>  CBasePane::DoPaint  
 填充窗格的背景。  
  
```  
virtual void DoPaint(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
### <a name="remarks"></a>备注  
 默认实现调用当前的视觉管理器，以填充背景 ( [CMFCVisualManager::OnFillBarBackground](../../mfc/reference/cmfcvisualmanager-class.md#onfillbarbackground))。  
  
##  <a name="enabledocking"></a>  CBasePane::EnableDocking  
 启用窗格的停靠到主框架。  
  
```  
virtual void EnableDocking(DWORD dwAlignment);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwAlignment`  
 指定要启用的停靠对齐方式。  
  
### <a name="remarks"></a>备注  
 调用此方法可启用到主框架的停靠对齐方式。 你可以将传递的组合`CBRS_ALIGN_`标志 (有关详细信息，请参阅[CControlBar::EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking))。  
  
 `EnableDocking` 设置内部标志`CBasePane::m_dwEnabledAlignment`和停靠窗格时，框架将检查此标志。  
  
 调用[CBasePane::GetEnabledAlignment](#getenabledalignment)来确定一个窗格的停靠对齐方式。  
  
##  <a name="enablegripper"></a>  CBasePane::EnableGripper  
 启用或禁用控制手柄。 如果启用了控制手柄，用户可以拖动它以重新定位窗格。  
  
```  
virtual void EnableGripper(BOOL bEnable);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE` 若要启用控制手柄;`FALSE`以禁用它。  
  
### <a name="remarks"></a>备注  
 框架将使用此方法启用而不是使用的控制手柄`WS_CAPTION`样式。  
  
##  <a name="floatpane"></a>  CBasePane::FloatPane  
 浮动窗格。  
  
```  
virtual BOOL FloatPane(
    CRect rectFloat,  
    AFX_DOCK_METHOD dockMethod=DM_UNKNOWN,  
    bool bShow=true);
```  
  
### <a name="parameters"></a>参数  
 [in] `rectFloat`  
 指定浮动窗格中出现的屏幕坐标。  
  
 [in] `dockMethod`  
 指定要用于浮动窗格的停靠方法。  
  
 [in] `bShow`  
 指定是否浮动窗格是可见的 ( `TRUE`) 或隐藏 ( `FALSE`)。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果已成功，则浮动窗格否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用此方法以浮动窗格中指定的屏幕位置`rectFloat`。  
  
##  <a name="get_acchelptopic"></a>  CBasePane::get_accHelpTopic  
 框架调用此方法来检索其中的完整路径`WinHelp`与指定的对象和该文件中的相应主题的标识符关联的文件。  
  
```  
virtual HRESULT get_accHelpTopic(
    BSTR* pszHelpFile,  
    VARIANT varChild,  
    long* pidTopic);
```  
  
### <a name="parameters"></a>参数  
 [in] `pszHelpFile`  
 地址`BSTR`接收的完整路径`WinHelp`关联文件，与指定的对象，如果有的话。  
  
 [in] `varChild`  
 指定要检索的帮助主题是否为对象或对象的子元素之一。 此参数可以是`CHILDID_SELF`（以获取帮助主题的对象） 或一个子 ID （以获取帮助主题的一个子对象的元素）。  
  
 [in] `pidTopic`  
 标识`Help`文件的主题，它与指定的对象相关联。  
  
### <a name="return-value"></a>返回值  
 `CBasePane` 未实现此方法。 因此，`CBasePane::get_accHelpTopic`始终返回`S_FALSE`。  
  
### <a name="remarks"></a>备注  
 此函数是在 MFC 中的 Active Accessibility 支持的一部分。 重写此函数在派生类提供有关你的对象的帮助信息中。  
  
##  <a name="get_accselection"></a>  CBasePane::get_accSelection  
 框架调用此方法来检索此对象的选定的子级。  
  
```  
virtual HRESULT get_accSelection(VARIANT* pvarChildren);
```  
  
### <a name="parameters"></a>参数  
 [in] `pvarChildren`  
 接收标识所选的子级的信息。  
  
### <a name="return-value"></a>返回值  
 `CBasePane` 未实现此方法。 如果 `pvarChildren` 为 `NULL`，则此方法返回 `E_INVALIDARG`。 否则，此方法返回`DISP_E_MEMBERNOTFOUND`。  
  
### <a name="remarks"></a>备注  
 此函数是在 MFC 中的 Active Accessibility 支持的一部分。 如果你有非窗口式用户界面元素以外无窗口的 ActiveX 控件，重写此函数在派生类中。  
  
##  <a name="getcaptionheight"></a>  Cbasepane:: Getcaptionheight  
 返回标题高度。  
  
```  
virtual int GetCaptionHeight() const;  
```  
  
### <a name="return-value"></a>返回值  
 标题高度。  
  
##  <a name="getcontrolbarstyle"></a>  CBasePane::GetControlBarStyle  
 返回控件栏样式。  
  
```  
virtual DWORD GetControlBarStyle() const 
```  
  
### <a name="return-value"></a>返回值  
 AFX_CBRS_ 标志的按位 OR 组合。  
  
### <a name="remarks"></a>备注  
 返回值是以下可能值的组合。  
  
|样式|描述|  
|-----------|-----------------|  
|`AFX_CBRS_FLOAT`|使控件栏浮点数。|  
|`AFX_CBRS_AUTOHIDE`|启用自动隐藏模式。|  
|`AFX_CBRS_RESIZE`|使控件条的调整大小。 当设置此标志时，则可以在可停靠的窗格中放置控件条。|  
|`AFX_CBRS_CLOSE`|启用隐藏的控件条。|  
  
##  <a name="getcurrentalignment"></a>  CBasePane::GetCurrentAlignment  
 返回当前窗格中对齐方式。  
  
```  
virtual DWORD GetCurrentAlignment() const;  
```  
  
### <a name="return-value"></a>返回值  
 控件条的当前对齐方式。 下表显示可能的值：  
  
|值|对齐方式|  
|-----------|---------------|  
|`CBRS_ALIGN_LEFT`|左对齐方式。|  
|`CBRS_ALIGN_RIGHT`|右对齐方式。|  
|`CBRS_ALIGN_TOP`|顶部对齐方式。|  
|`CBRS_ALIGN_BOTTOM`|底部对齐方式。|  
  
##  <a name="getdockingmode"></a>  Cbasepane:: Getdockingmode  
 返回当前窗格停靠模式。  
  
```  
virtual AFX_DOCK_TYPE GetDockingMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果将窗格拖动 DT_STANDARD 由拖动矩形指示在屏幕上。 DT_IMMEDIATE 如果拖动窗格的内容。  
  
### <a name="remarks"></a>备注  
 框架调用此方法以确定当前窗格的停靠模式。  
  
 如果`CBasePane::m_dockMode`是未定义 (DT_UNDEFINED)，则停靠模式执行从全局停靠模式 ( `AFX_GLOBAL_DATA::m_dockModeGlobal`)。  
  
 通过设置`m_dockMode`或重写`GetDockingMode`可以控制每个窗格的停靠模式。  
  
##  <a name="getdocksiteframewnd"></a>  CBasePane::GetDockSiteFrameWnd  
 返回一个指向[CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)停靠窗格中的位置的对象。  
  
```  
virtual CWnd* GetDockSiteFrameWnd() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向窗格的停靠站点的指针。  
  
### <a name="remarks"></a>备注  
 调用此方法来检索指向窗格的停靠站点。 如果窗格浮动的可以是主框架窗口如果窗格停靠到主框架或微型框架窗口停靠站点。  
  
##  <a name="getenabledalignment"></a>  CBasePane::GetEnabledAlignment  
 返回到窗格中应用的 CBRS_ALIGN_ 样式。  
  
```  
virtual DWORD GetEnabledAlignment() const;  
```  
  
### <a name="return-value"></a>返回值  
 CBRS_ALIGN_ 样式的组合。 下表显示可能的样式：  
  
|Flag|启用对齐方式|  
|----------|-----------------------|  
|`CBRS_ALIGN_LEFT`|左。|  
|`CBRS_ALIGN_RIGHT`|权限。|  
|`CBRS_ALIGN_TOP`|返回页首。|  
|`CBRS_ALIGN_BOTTOM`|底部。|  
|`CBRS_ALIGN_ANY`|所有标志的组合。|  
  
### <a name="remarks"></a>备注  
 调用此方法以确定该窗格的启用对齐方式。 启用的对齐意味着窗格可以停靠到在主框架窗口的侧。  
  
 使用启用停靠对齐[CBasePane::EnableDocking](#enabledocking)。  
  
##  <a name="getmfcstyle"></a>  CBasePane::GetMFCStyle  
 返回特定于 MFC 的窗格样式。  
  
```  
virtual DWORD GetMFCStyle() const;  
```  
  
### <a name="return-value"></a>返回值  
 库特定 (AFX_CBRS_) 窗格样式的组合。  
  
##  <a name="getpaneicon"></a>  CBasePane::GetPaneIcon  
 返回窗格图标的句柄。  
  
```  
virtual HICON GetPaneIcon(BOOL bBigIcon);
```  
  
### <a name="parameters"></a>参数  
 [in] `bBigIcon`  
 如果通过 32 像素的图标指定 32 像素`TRUE`; 如果由 16 像素图标指定 16 像素`FALSE`。  
  
### <a name="return-value"></a>返回值  
 窗格图标句柄。 如果不成功，则返回`NULL`。  
  
### <a name="remarks"></a>备注  
 默认实现调用[CWnd::GetIcon](../../mfc/reference/cwnd-class.md#geticon)。  
  
##  <a name="getpanerow"></a>  CBasePane::GetPaneRow  
 返回一个指向[CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)停靠窗格中的位置的对象。  
  
```  
CDockingPanesRow* GetPaneRow();
```  
  
### <a name="return-value"></a>返回值  
 指向的指针`CDockingPanesRow`停靠窗格中，如果或`NULL`它是否为浮点。  
  
### <a name="remarks"></a>备注  
 调用此方法来访问停靠窗格中的位置的行。 例如，若要排列中的特定行的窗格，调用`GetPaneRow`，然后调用[CDockingPanesRow::ArrangePanes](../../mfc/reference/cdockingpanesrow-class.md#arrangepanes)。  
  
##  <a name="getpanestyle"></a>  CBasePane::GetPaneStyle  
 返回的窗格样式。  
  
```  
virtual DWORD GetPaneStyle() const;  
```  
  
### <a name="return-value"></a>返回值  
 所设置的控件条样式 （包括 CBRS_ 样式） 的组合[CBasePane::SetPaneStyle](#setpanestyle)在创建时的方法。  
  
##  <a name="getparentdocksite"></a>  CBasePane::GetParentDockSite  
 将指针返回到父停靠站点。  
  
```  
virtual CDockSite* GetParentDockSite() const;  
```  
  
### <a name="return-value"></a>返回值  
 父停靠站点。  
  
##  <a name="getparentminiframe"></a>  CBasePane::GetParentMiniFrame  
 返回到父微型框架窗口的指针。  
  
```  
virtual CPaneFrameWnd* GetParentMiniFrame(BOOL bNoAssert=FALSE) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `bNoAssert`  
 如果`TRUE`，此方法不会检查无效指针。 如果应用程序退出时调用此方法，将此参数设置为`TRUE`。  
  
### <a name="return-value"></a>返回值  
 指向父微型框架窗口窗格中为浮点; 的有效指针否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 调用此函数可检索指向父微型框架窗口的指针。 此方法循环访问所有父级，并检查对象派生自[CPaneFrameWnd 类](../../mfc/reference/cpaneframewnd-class.md)。  
  
 使用`GetParentMiniFrame`以确定是否浮动窗格。  
  
##  <a name="getparenttabbedpane"></a>  CBasePane::GetParentTabbedPane  
 将指针返回到父选项卡式窗格。  
  
```  
CBaseTabbedPane* GetParentTabbedPane() const;  
```  
  
### <a name="return-value"></a>返回值  
 父选项卡式窗格，如果它存在，则指向的指针否则为`NULL`。  
  
##  <a name="getparenttabwnd"></a>  CBasePane::GetParentTabWnd  
 返回指向选项卡内的父窗口的指针。  
  
```  
CMFCBaseTabCtrl* GetParentTabWnd(HWND& hWndTab) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `hWndTab`  
 如果返回值不是`NULL`，此参数将包含父选项卡式窗口的句柄。  
  
### <a name="return-value"></a>返回值  
 指向父级的有效选项卡式窗口或`NULL`。  
  
### <a name="remarks"></a>备注  
 使用此函数可检索指向父选项卡式窗口的指针。 有时并不足够，以调用`GetParent`，因为一个窗格可能会在停靠包装 ( [CDockablePaneAdapter 类](../../mfc/reference/cdockablepaneadapter-class.md)) 还是内部窗格适配器 ( [CDockablePaneAdapter 类](../../mfc/reference/cdockablepaneadapter-class.md))。 通过使用`GetParentTabWnd`你将能够检索这种情况下 （假设父选项卡式的窗口） 中的有效指针。  
  
##  <a name="getrecentvisiblestate"></a>  CBasePane::GetRecentVisibleState  
 从存档在还原一个窗格时，框架将调用此方法。  
  
```  
virtual BOOL GetRecentVisibleState() const;  
```  
  
### <a name="return-value"></a>返回值  
 A `BOOL` ，指定新的可见状态。 如果`TRUE`，窗格是可见的时间序列化和应是可见的还原时。 如果`FALSE`，窗格时序列化和还原时，将隐藏已隐藏。  
  
##  <a name="hideinprintpreviewmode"></a>  CBasePane::HideInPrintPreviewMode  
 指定是否在打印预览中隐藏窗格。  
  
```  
virtual BOOL HideInPrintPreviewMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果在打印预览; 中不显示窗格否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 在打印预览中不显示基本的窗格。 因此，此方法始终返回`TRUE`。  
  
##  <a name="insertpane"></a>  CBasePane::InsertPane  
 注册到停靠管理器指定窗格。  
  
```  
BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pControlBar`  
 指向要插入的窗格的指针。  
  
 [in] `pTarget`  
 指向相邻窗格的指针。  
  
 [in] `bAfter`  
 如果`TRUE`，`pControlBar`之后插入`pTarget`。 如果`FALSE`，`pControlBar`之前插入`pTarget`。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果该方法成功，`FALSE`否则为。  
  
##  <a name="isaccessibilitycompatible"></a>  CBasePane::IsAccessibilityCompatible  
 指定窗格中是否支持 Active Accessibility。  
  
```  
virtual BOOL IsAccessibilityCompatible();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果窗格支持 Active Accessibility;否则为`FALSE`。  
  
##  <a name="isautohidemode"></a>  CBasePane::IsAutoHideMode  
 确定一个窗格是否在自动隐藏模式下。  
  
```  
virtual BOOL IsAutoHideMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果在窗格中，在自动隐藏模式下;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 基窗格无法自动隐藏。 此方法始终返回 `FALSE`。  
  
##  <a name="isdialogcontrol"></a>  CBasePane::IsDialogControl  
 指定窗格是否对话框控件。  
  
```  
BOOL IsDialogControl() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果在窗格中，对话框控件;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 框架使用此方法以确保所有窗格的布局一致性。  
  
##  <a name="isdocked"></a>  CBasePane::IsDocked  
 确定是否停靠窗格。  
  
```  
virtual BOOL IsDocked() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果窗格中的父级不是最小化框架或窗格浮动的与另一个窗格; 的最小化帧中否则为`FALSE`。  
  
##  <a name="isfloating"></a>  CBasePane::IsFloating  
 确定是否浮动窗格。  
  
```  
virtual BOOL IsFloating() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果窗格浮动的;，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法返回的相反值[CBasePane::IsDocked](#isdocked)。  
  
##  <a name="ishorizontal"></a>  CBasePane::IsHorizontal  
 确定是否水平停靠的窗格。  
  
```  
virtual BOOL IsHorizontal() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果窗格停靠水平空间。，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 默认实现将检查当前停靠对齐方式`CBRS_ORIENT_HORZ`。  
  
##  <a name="isinfloatingmultipaneframewnd"></a>  CBasePane::IsInFloatingMultiPaneFrameWnd  
 指定窗格是否在多窗格框架窗口 ( [CMultiPaneFrameWnd 类](../../mfc/reference/cmultipaneframewnd-class.md))。  
  
```  
virtual BOOL IsInFloatingMultiPaneFrameWnd() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果在窗格中，在多窗格框架窗口;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 仅可停靠窗格可以浮动在多窗格框架窗口中。 因此，`CBasePane::IsInFloatingMultiPaneFrameWnd`始终返回`FALSE`。  
  
##  <a name="ismditabbed"></a>  CBasePane::IsMDITabbed  
 确定窗格中是否已添加到选项卡式文档作为 MDI 子窗口。  
  
```  
virtual BOOL IsMDITabbed() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果窗格中已添加到 MDI 子窗口选项卡式文档，则为否则为`FALSE`。  
  
##  <a name="ispanevisible"></a>  CBasePane::IsPaneVisible  
 指定是否`WS_VISIBLE`标志设置为窗格。  
  
```  
BOOL IsPaneVisible() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果`WS_VISIBLE`设置; 否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 使用[CBasePane::IsVisible](#isvisible)来确定窗格中可见。  
  
##  <a name="ispointneardocksite"></a>  CBasePane::IsPointNearDockSite  
 确定指定的点是否在停靠站点附近。  
  
```  
BOOL IsPointNearDockSite(
    CPoint point,  
    DWORD& dwBarAlignment,  
    BOOL& bOuterEdge) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
 指定的点。  
  
 [out] `dwBarAlignment`  
 指定的点附近是哪个边缘。 可能的值为`CBRS_ALIGN_LEFT`， `CBRS_ALIGN_RIGHT`， `CBRS_ALIGN_TOP`，和 `CBRS_ALIGN_BOTTOM`  
  
 [out] `bOuterEdge`  
 `TRUE` 如果该点附近的外边框的停靠站点中;`FALSE`否则为。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果该点附近停靠站点中;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 在停靠管理器中设置的敏感度中时，该点则在停靠站点附近。 默认敏感度为 15 像素。  
  
##  <a name="isresizable"></a>  Cbasepane:: Isresizable  
 确定是否可以调整窗格的大小。  
  
```  
virtual BOOL IsResizable() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果可以由用户; 调整窗格的大小否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 窗格[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)可调整大小。  
  
 状态栏 ( [CMFCStatusBar 类](../../mfc/reference/cmfcstatusbar-class.md)) 和停靠栏 ( [CDockSite 类](../../mfc/reference/cdocksite-class.md)) 不能调整大小。  
  
##  <a name="isrestoredfromregistry"></a>  CBasePane::IsRestoredFromRegistry  
 确定是否从注册表还原窗格。  
  
```  
virtual BOOL IsRestoredFromRegistry() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果从注册表; 还原窗格否则为`FALSE`。  
  
##  <a name="istabbed"></a>  CBasePane::IsTabbed  
 确定是否已在选项卡式窗口选项卡控件中插入窗格。  
  
```  
virtual BOOL IsTabbed() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果在选项卡式窗口中; 的选项卡中插入控件条否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法检索到的直接父指针，并确定是否运行时父类[CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)。  
  
##  <a name="isvisible"></a>  CBasePane::IsVisible  
 确定窗格是否可见。  
  
```  
virtual BOOL IsVisible() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果窗格是可见的;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 使用此方法来确定的窗格中可见。 不要使用`::IsWindowVisible`。  
  
 如果不选项卡式窗格中 (请参阅[CBasePane::IsTabbed](#istabbed))，此方法检查`WS_VISIBLE`样式。 如果选项卡式窗格中，此方法将检查父选项卡式窗口的可见性。 如果父窗口可见时，该函数检查的可见性窗格中的选项卡上使用[CMFCBaseTabCtrl::IsTabVisible](../../mfc/reference/cmfcbasetabctrl-class.md#istabvisible)。  
  
##  <a name="loadstate"></a>  CBasePane::LoadState  
 从注册表加载窗格的状态。  
  
```  
virtual BOOL LoadState(
    LPCTSTR lpszProfileName=NULL,  
    int nIndex=-1,  
    UINT uiID=(UINT)-1);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszProfileName`  
 配置文件名称。  
  
 [in] `nIndex`  
 配置文件的索引。  
  
 [in] `uiID`  
 窗格中的 id。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果成功，则加载窗格状态否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 框架调用此方法以从注册表加载窗格状态。 在要加载保存的其他信息派生类中重写它[CBasePane::SaveState](#savestate)。  
  
##  <a name="movewindow"></a>  CBasePane::MoveWindow  
 将窗格的移动。  
  
```  
virtual HDWP MoveWindow(
    CRect& rect,  
    BOOL bRepaint = TRUE,  
    HDWP hdwp = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `rect`  
 指定新位置和窗格的大小的矩形。  
  
 [in] `bRepaint`  
 如果`TRUE`，窗格重新绘制。 如果`FALSE`，窗格不重新绘制。  
  
 [in] `hdwp`  
 延迟的窗口位置结构的句柄。  
  
### <a name="return-value"></a>返回值  
 延迟的窗口位置结构的句柄或`NULL`。  
  
### <a name="remarks"></a>备注  
 如果你通过`NULL`作为`hdwp`参数，此方法通常移动窗口。 如果您传入句柄，此方法将执行延迟的窗口移动。 你可以通过调用获取句柄[BeginDeferWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms632672)或通过将存储上次调用此方法的返回值。  
  
##  <a name="onafterchangeparent"></a>  CBasePane::OnAfterChangeParent  
 在窗格中的父更改后由框架调用。  
  
```  
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndOldParent`  
 指向上一个父级的指针。  
  
### <a name="remarks"></a>备注  
 框架在调用此方法窗格中的父更改之后，通常由于停靠或浮动的操作。  
  
 默认实现不执行任何操作。  
  
##  <a name="onbeforechangeparent"></a>  CBasePane::OnBeforeChangeParent  
 恰好在窗格中更改其父窗口之前，由框架调用。  
  
```  
virtual void OnBeforeChangeParent(
    CWnd* pWndNewParent,  
    BOOL bDelay=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndNewParent`  
 指向新的父窗口的指针。  
  
 [in] `bDelay`  
 指定是否必须推迟布局调整。  
  
### <a name="remarks"></a>备注  
 框架在由于停靠、 浮动的或自动隐藏操作通常调用之前窗格的父更改，此方法。  
  
 默认实现不执行任何操作。  
  
##  <a name="ondrawcaption"></a>  CBasePane::OnDrawCaption  
 绘制标题时，框架将调用此方法。  
  
```  
virtual void OnDrawCaption();
```  
  
### <a name="remarks"></a>备注  
 此方法具有无功能`CBasePane`类。  
  
##  <a name="onmovepanedivider"></a>  CBasePane::OnMovePaneDivider  
 当前未使用此方法。  
  
```  
virtual void OnMovePaneDivider(CPaneDivider*);
```  
  
### <a name="parameters"></a>参数  
 [in] `CPaneDivider*`  
 未使用。  
  
##  <a name="onpanecontextmenu"></a>  CBasePane::OnPaneContextMenu  
 在构建具有窗格的列表菜单时由框架调用。  
  
```  
virtual void OnPaneContextMenu(
    CWnd* pParentFrame,  
    CPoint point);
```  
  
### <a name="parameters"></a>参数  
 [in] `pParentFrame`  
 指向的父框架的指针。  
  
 [in] `point`  
 指定的位置的快捷菜单。  
  
### <a name="remarks"></a>备注  
 `OnPaneContextMenu` 调用维护属于当前的框架窗口的窗格的列表到停靠管理器。 此方法将窗格的名称添加到快捷菜单，并显示它。 菜单上的命令显示或隐藏各个窗格。  
  
 重写此方法以自定义此行为。  
  
##  <a name="onremovefromminiframe"></a>  CBasePane::OnRemoveFromMiniFrame  
 从其父微型框架窗口删除窗格中时，由框架调用。  
  
```  
virtual void OnRemoveFromMiniFrame(CPaneFrameWnd* pMiniFrame);
```  
  
### <a name="parameters"></a>参数  
 [in] `pMiniFrame`  
 指向从中删除窗格的微型框架窗口的指针。  
  
### <a name="remarks"></a>备注  
 从 （由于停靠，例如） 其父微型框架窗口删除窗格中时，框架将调用此方法。  
  
 默认实现不执行任何操作。  
  
##  <a name="onsetaccdata"></a>  Cbasepane:: Onsetaccdata  
 `CBasePane` 不使用此方法。  
  
```  
virtual BOOL OnSetAccData(long lVal);
```  
  
### <a name="parameters"></a>参数  
 [in] `lVal`  
 未使用。  
  
### <a name="return-value"></a>返回值  
 此方法始终返回 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="panefrompoint"></a>  CBasePane::PaneFromPoint  
 返回包含给定的点的窗格。  
  
```  
CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    bool bExactBar = false,  
    CRuntimeClass* pRTCBarType = NULL) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
 指定在屏幕坐标中，检查点。  
  
 [in] `nSensitivity`  
 增加此数量搜索区域。 窗格中将满足搜索条件，如果给的定点落在增加的区域。  
  
 [in] `bExactBar`  
 `TRUE` 若要忽略`nSensitivity`参数; 否则为`FALSE`。  
  
 [in] `pRTCBarType`  
 如果不是`NULL`，该方法将搜索仅指定类型的窗格。  
  
### <a name="return-value"></a>返回值  
 `CBasePane`-派生的对象，包含给定的点，或`NULL`如果不找到任何窗格。  
  
##  <a name="recalclayout"></a>  CBasePane::RecalcLayout  
 `CBasePane` 不使用此方法。  
  
```  
virtual void RecalcLayout();
```  
  
##  <a name="removepanefromdockmanager"></a>  CBasePane::RemovePaneFromDockManager  
 注销一个窗格并将其从列表中到停靠管理器中删除。  
  
```  
void RemovePaneFromDockManager(
    CBasePane* pBar,  
    BOOL bDestroy = TRUE,  
    BOOL bAdjustLayout = FALSE,  
    BOOL bAutoHide = FALSE,  
    CBasePane* pBarReplacement = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `pBar`  
 指向要删除的窗格的指针。  
  
 [in] `bDestroy`  
 如果`TRUE`，销毁删除窗格。  
  
 [in] `bAdjustLayout`  
 如果`TRUE`，立即调整停靠布局。  
  
 [in] `bAutoHide`  
 如果`TRUE`，停靠布局与自动隐藏栏列表。 如果`FALSE`，停靠布局与正则窗格的列表。  
  
 [in] `pBarReplacement`  
 指向替换删除窗格中的窗格的指针。  
  
##  <a name="savestate"></a>  CBasePane::SaveState  
 将窗格的状态保存到注册表。  
  
```  
virtual BOOL SaveState(
    LPCTSTR lpszProfileName=NULL,  
    int nIndex=-1,  
    UINT uiID=(UINT)-1);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszProfileName`  
 配置文件名称。  
  
 [in] `nIndex`  
 配置文件的索引。  
  
 [in] `uiID`  
 窗格中的 id。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果成功，则保存状态否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 框架调用此方法时它将窗格的状态保存到注册表。 重写`SaveState`在派生类来存储的其他信息。  
  
##  <a name="selectdefaultfont"></a>  CBasePane::SelectDefaultFont  
 选择给定的设备上下文的默认字体。  
  
```  
CFont* SelectDefaultFont(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 设备上下文。  
  
### <a name="return-value"></a>返回值  
 默认值指向的指针[CFont 类](../../mfc/reference/cfont-class.md)对象。  
  
##  <a name="setcontrolbarstyle"></a>  CBasePane::SetControlBarStyle  
 设置控件栏样式。  
  
```  
virtual void SetControlBarStyle(DWORD dwNewStyle);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwNewStyle`  
 以下的可能值的按位 OR 组合。  
  
|样式|描述|  
|-----------|-----------------|  
|`AFX_CBRS_FLOAT`|使控件栏浮点数。|  
|`AFX_CBRS_AUTOHIDE`|启用自动隐藏模式。|  
|`AFX_CBRS_RESIZE`|使控件条的调整大小。 当设置此标志时，则可以在可停靠的窗格中放置控件条。|  
|`AFX_CBRS_CLOSE`|启用隐藏的控件条。|  
  
##  <a name="setdockingmode"></a>  CBasePane::SetDockingMode  
 设置窗格的停靠模式。  
  
```  
void SetDockingMode(AFX_DOCK_TYPE dockModeNew);
```  
  
### <a name="parameters"></a>参数  
 [in] `dockModeNew`  
 指定新的窗格的停靠模式。  
  
### <a name="remarks"></a>备注  
 框架支持两种停靠模式： 标准和快速。  
  
 在标准停靠模式中，围绕使用拖动矩形移动窗格和微型框架窗口。 在即时停靠模式中，控件条及微型框架窗口将立即与其上下文一起。  
  
 最初，停靠模式通过全局定义[CDockingManager::m_dockModeGlobal](../../mfc/reference/cdockingmanager-class.md#m_dockmodeglobal)。 你可以设置使用单独的每个窗格的停靠模式`SetDockingMode`方法。  
  
##  <a name="setpanealignment"></a>  CBasePane::SetPaneAlignment  
 设置窗格中的对齐方式。  
  
```  
virtual void SetPaneAlignment(DWORD dwAlignment);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwAlignment`  
 指定新的对齐方式。  
  
### <a name="remarks"></a>备注  
 通常情况下，框架时窗格停靠在从主框架的一侧到另一个调用此方法。  
  
 下表显示的可能值`dwAlignment`:  
  
|值|对齐方式|  
|-----------|---------------|  
|`CBRS_ALIGN_LEFT`|左对齐方式。|  
|`CBRS_ALIGN_RIGHT`|右对齐方式。|  
|`CBRS_ALIGN_TOP`|顶部对齐方式。|  
|`CBRS_ALIGN_BOTTOM`|底部对齐方式。|  
  
##  <a name="setpanestyle"></a>  CBasePane::SetPaneStyle  
 设置窗格中的样式。  
  
```  
virtual void SetPaneStyle(DWORD dwNewStyle);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwNewStyle`  
 指定要设置的新样式。  
  
### <a name="remarks"></a>备注  
 此方法可以用于设置任何 afxres.h 中定义的 CBRS_ 样式。 由于窗格样式和窗格中的对齐方式存储在一起，通过结合基于它的当前对齐方式，如下所示设置新的样式。  
  
 `pPane->SetPaneStyle (pPane->GetCurrentAlignment() | CBRS_TOOLTIPS);`  
  
##  <a name="setwindowpos"></a>  CBasePane::SetWindowPos  
 更改大小、 位置和 Z 顺序的窗格。  
  
```  
virtual HDWP SetWindowPos(
    const CWnd* pWndInsertAfter,  
    int x,  
    int y,  
    int cx,  
    int cy,  
    UINT nFlags,  
    HDWP hdwp = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndInsertAfter`  
 标识`CWnd`对象之前此`CWnd`按 Z 顺序的对象。 有关详细信息，请参阅[CWnd::SetWindowPos](../../mfc/reference/cwnd-class.md#setwindowpos)。  
  
 [in] `x`  
 指定窗口的左侧的位置。  
  
 [in] `y`  
 指定的窗口顶部的位置。  
  
 [in] `cx`  
 指定窗口的宽度。  
  
 [in] `cy`  
 指定窗口的高度。  
  
 [in] `nFlags`  
 指定大小和位置选项。 有关详细信息，请参阅[CWnd::SetWindowPos](../../mfc/reference/cwnd-class.md#setwindowpos)。  
  
 [in] `hdwp`  
 包含一个或多个窗口的大小和位置信息的结构的句柄。  
  
### <a name="return-value"></a>返回值  
 更新后的延迟的窗口位置结构的句柄或`NULL`。  
  
### <a name="remarks"></a>备注  
 如果`pWndInsertAfter`是`NULL`，此方法调用[CWnd::SetWindowPos](../../mfc/reference/cwnd-class.md#setwindowpos)。 如果`pWndInsertAfter`为非`NULL`，此方法调用`DeferWindowPos`。  
  
##  <a name="showpane"></a>  CBasePane::ShowPane  
 显示或隐藏窗格。  
  
```  
virtual void ShowPane(
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>参数  
 [in] `bShow`  
 指定是否显示 ( `TRUE`) 或隐藏 ( `FALSE`) 窗格。  
  
 [in] `bDelay`  
 如果`TRUE`，重新计算停靠布局被延迟。  
  
 [in] `bActivate`  
 如果`TRUE`，窗格处于活动状态时显示。  
  
### <a name="remarks"></a>备注  
 此方法显示或隐藏窗格。 使用此方法，而不是`ShowWindow`因为此方法通知中的窗格中的可见性的更改的相关停靠管理器。  
  
 使用[CBasePane::IsVisible](#isvisible)来确定窗格中的当前可见。  
  
##  <a name="stretchpane"></a>  Cbasepane:: Stretchpane  
 垂直或水平拉伸窗格。  
  
```  
virtual CSize StretchPane(
    int nLength,  
    BOOL bVert);
```  
  
### <a name="parameters"></a>参数  
 [in] `nLength`  
 用于拉伸窗格长度。  
  
 [in] `bVert`  
 如果`TRUE`，垂直拉伸窗格。 如果`FALSE`，水平拉伸窗格。  
  
### <a name="return-value"></a>返回值  
 外延式窗格的大小。  
  
##  <a name="undockpane"></a>  CBasePane::UndockPane  
 从停靠站点、 默认滑块或它当前停靠的微型框架窗口删除窗格。  
  
```  
virtual void UndockPane(BOOL bDelay=FALSE);
```  
  
### <a name="parameters"></a>参数  
 `bDelay`  
 如果为 TRUE，停靠布局立即就不必重新计算。  
  
### <a name="remarks"></a>备注  
 调用此方法以对操作窗格状态或排除窗格从停靠布局。  
  
 如果你想要继续使用此窗格中，调用[cbasepane:: Dockpane](#dockpane)或[CBasePane::FloatPane](#floatpane)之前调用此方法。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CPane](../../mfc/reference/cbasepane-class.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)
