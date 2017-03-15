---
title: "CBasePane 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBasePane::get_accKeyboardShortcut
- CBasePane.get_accKeyboardShortcut
- CBasePane.accSelect
- get_accDefaultAction
- accSelect
- CBasePane.accHitTest
- CBasePane.get_accRole
- get_accKeyboardShortcut
- CBasePane::Serialize
- CBasePane
- CBasePane::get_accDefaultAction
- get_accParent
- CBasePane::accSelect
- accLocation
- CBasePane.get_accDescription
- get_accName
- CBasePane::get_accChildCount
- CBasePane.get_accChild
- CBasePane::accHitTest
- accHitTest
- get_accHelp
- CBasePane.get_accChildCount
- CBasePane.get_accValue
- CBasePane::get_accDescription
- get_accChildCount
- CBasePane.accLocation
- CBasePane.PreTranslateMessage
- CBasePane.get_accName
- PreTranslateMessage
- CBasePane::get_accFocus
- get_accDescription
- CBasePane::get_accRole
- get_accValue
- CBasePane.Serialize
- CBasePane::accLocation
- get_accRole
- CBasePane::get_accChild
- get_accFocus
- CBasePane::get_accHelp
- CBasePane.get_accDefaultAction
- CBasePane.get_accHelp
- CBasePane::PreTranslateMessage
- CBasePane::get_accState
- CBasePane.get_accParent
- CBasePane::get_accParent
- get_accChild
- CBasePane::get_accValue
- Serialize
- get_accState
- CBasePane.get_accState
- CBasePane.get_accFocus
- CBasePane::get_accName
dev_langs:
- C++
helpviewer_keywords:
- get_accState method
- get_accHelp method
- CBasePane class
- accLocation method
- accHitTest method
- get_accDescription method
- get_accDefaultAction method
- get_accName method
- get_accFocus method
- get_accRole method
- get_accValue method
- get_accChild method
- accSelect method
- get_accKeyboardShortcut method
- get_accChildCount method
- Serialize method
- PreTranslateMessage method
- get_accParent method
ms.assetid: 8163dd51-d7c7-4def-9c74-61f8ecdfad82
caps.latest.revision: 43
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
ms.openlocfilehash: 0444c0647d83a1e9b431dd0c5bdb369da213b91b
ms.lasthandoff: 02/24/2017

---
# <a name="cbasepane-class"></a>CBasePane 类
在 MFC 中的所有窗格的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class CBasePane : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|`CBasePane::CBasePane`|默认构造函数。|  
|`CBasePane::~CBasePane`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|`CBasePane::accHitTest`|由框架调用以检索屏幕上给定点处的子元素或子对象。 (重写[CWnd::accHitTest](../../mfc/reference/cwnd-class.md#acchittest)。)|  
|`CBasePane::accLocation`|由框架可检索指定对象的当前屏幕位置调用。 (重写[CWnd::accLocation](../../mfc/reference/cwnd-class.md#acclocation)。)|  
|[CBasePane::AccNotifyObjectFocusEvent](#accnotifyobjectfocusevent)|`CBasePane`不使用此方法。|  
|`CBasePane::accSelect`|由框架调用以修改选定内容或移动指定对象的键盘焦点。 (重写[CWnd::accSelect](../../mfc/reference/cwnd-class.md#accselect)。)|  
|[CBasePane::AddPane](#addpane)|扩展管理器中添加一个窗格。|  
|[Cbasepane:: Adjustdockinglayout](#adjustdockinglayout)|若要调整停靠布局的扩展管理器调用将重定向。|  
|[Cbasepane:: Adjustlayout](#adjustlayout)|当窗格中应调整其内部的布局时，由框架调用。|  
|[Cbasepane:: Calcfixedlayout](#calcfixedlayout)|计算控件条的水平大小。|  
|[Cbasepane:: Canacceptpane](#canacceptpane)|确定是否可停靠窗格中的另一窗格。|  
|[CBasePane::CanAutoHide](#canautohide)|确定窗格中是否支持自动隐藏模式。|  
|[CBasePane::CanBeAttached](#canbeattached)|确定是否可以到另一窗格停靠窗格。|  
|[CBasePane::CanBeClosed](#canbeclosed)|确定是否可以关闭窗格。|  
|[CBasePane::CanBeDocked](#canbedocked)|确定是否可以到另一窗格停靠窗格。|  
|[CBasePane::CanBeResized](#canberesized)|确定是否可以调整大小窗格。|  
|[CBasePane::CanBeTabbedDocument](#canbetabbeddocument)|指定窗格中是否可以转换为 MDI 选项卡式文档。|  
|[CBasePane::CanFloat](#canfloat)|确定是否可以浮动窗格。|  
|[CBasePane::CanFocus](#canfocus)|指定窗格中是否可以接收焦点。|  
|[CBasePane::CopyState](#copystate)|复制给定窗格的状态。|  
|[CBasePane::CreateDefaultMiniframe](#createdefaultminiframe)|如果可以浮动窗格中，将创建的微型框架窗口。|  
|[Cbasepane:: Createex](#createex)|创建窗格控件。|  
|[Cbasepane:: Dockpane](#dockpane)|窗格停靠到另一个窗格或框架窗口。|  
|[CBasePane::DockPaneUsingRTTI](#dockpaneusingrtti)|通过使用运行时类型信息停靠窗格。|  
|[CBasePane::DockToFrameWindow](#docktoframewindow)|可停靠窗格停靠到的帧中。|  
|[Cbasepane:: Doesallowdyninsertbefore](#doesallowdyninsertbefore)|确定是否另一个窗格可以动态地插入此窗格中与父框架之间。|  
|[CBasePane::EnableDocking](#enabledocking)|启用窗格中的停靠到主框架。|  
|[CBasePane::EnableGripper](#enablegripper)|启用或禁用控制手柄。 如果启用了控制手柄，用户可拖动重新定位窗格。|  
|`CBasePane::FillWindowRect`|在内部使用。|  
|[CBasePane::FloatPane](#floatpane)|浮动窗格。|  
|`CBasePane::get_accChild`|由框架调用以检索指定子级的 `IDispatch` 接口地址。 (重写[CWnd::get_accChild](../../mfc/reference/cwnd-class.md#get_accchild)。)|  
|`CBasePane::get_accChildCount`|由要检索的属于该对象的子级的个数的框架调用。 (重写[CWnd::get_accChildCount](../../mfc/reference/cwnd-class.md#get_accchildcount)。)|  
|`CBasePane::get_accDefaultAction`|由框架来检索一个字符串，描述该对象的默认操作调用。 (重写[CWnd::get_accDefaultAction](../../mfc/reference/cwnd-class.md#get_accdefaultaction)。)|  
|`CBasePane::get_accDescription`|由框架调用以检索描述指定对象的可视外观的字符串。 (重写[CWnd::get_accDescription](../../mfc/reference/cwnd-class.md#get_accdescription)。)|  
|`CBasePane::get_accFocus`|由框架调用以检索具有键盘焦点的对象。 (重写[CWnd::get_accFocus](../../mfc/reference/cwnd-class.md#get_accfocus)。)|  
|`CBasePane::get_accHelp`|由框架来检索该对象的帮助属性字符串调用。 (重写[CWnd::get_accHelp](../../mfc/reference/cwnd-class.md#get_acchelp)。)|  
|[CBasePane::get_accHelpTopic](#get_acchelptopic)|由框架来检索与指定对象相关联的 WinHelp 文件的完整路径和该文件中的相应主题的标识符调用。 (重写[CWnd::get_accHelpTopic](../../mfc/reference/cwnd-class.md#get_acchelptopic)。)|  
|`CBasePane::get_accKeyboardShortcut`|由框架来检索对象的指定快捷方式键调用。 (重写[CWnd::get_accKeyboardShortcut](../../mfc/reference/cwnd-class.md#get_acckeyboardshortcut)。)|  
|`CBasePane::get_accName`|由框架调用以检索指定对象的名称。 (重写[CWnd::get_accName](../../mfc/reference/cwnd-class.md#get_accname)。)|  
|`CBasePane::get_accParent`|由框架调用以检索`IDispatch`对象的父对象的接口。 (重写[CWnd::get_accParent](../../mfc/reference/cwnd-class.md#get_accparent)。)|  
|`CBasePane::get_accRole`|由框架调用以检索描述指定对象的角色的信息。 (重写[CWnd::get_accRole](../../mfc/reference/cwnd-class.md#get_accrole)。)|  
|[CBasePane::get_accSelection](#get_accselection)|由框架调用以检索该对象的选定子级。 (重写[CWnd::get_accSelection](../../mfc/reference/cwnd-class.md#get_accselection)。)|  
|`CBasePane::get_accState`|由框架调用以检索指定对象的当前状态。 (重写[CWnd::get_accState](../../mfc/reference/cwnd-class.md#get_accstate)。)|  
|`CBasePane::get_accValue`|由框架调用以检索指定对象的值。 (重写[CWnd::get_accValue](../../mfc/reference/cwnd-class.md#get_accvalue)。)|  
|[CBasePane::GetCaptionHeight](#getcaptionheight)|返回标题高度。|  
|[CBasePane::GetControlBarStyle](#getcontrolbarstyle)|返回控件栏样式。|  
|[CBasePane::GetCurrentAlignment](#getcurrentalignment)|返回当前窗格对齐方式。|  
|[CBasePane::GetDockingMode](#getdockingmode)|返回窗格中的当前停靠模式。|  
|[CBasePane::GetDockSiteFrameWnd](#getdocksiteframewnd)|返回指向是窗格中的停靠站点窗口的指针。|  
|[CBasePane::GetEnabledAlignment](#getenabledalignment)|返回应用于窗格中的 CBRS_ALIGN_ 样式。|  
|[CBasePane::GetMFCStyle](#getmfcstyle)|返回特定于 MFC 的窗格中的样式。|  
|[CBasePane::GetPaneIcon](#getpaneicon)|返回窗格中图标的句柄。|  
|`CBasePane::GetPaneRect`|在内部使用。|  
|[CBasePane::GetPaneRow](#getpanerow)|返回一个指向[CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)窗格中的停靠位置的对象。|  
|[CBasePane::GetPaneStyle](#getpanestyle)|返回的窗格中的样式。|  
|[CBasePane::GetParentDockSite](#getparentdocksite)|返回一个指向父停靠站点。|  
|[CBasePane::GetParentMiniFrame](#getparentminiframe)|返回一个指向父微型框架窗口。|  
|[CBasePane::GetParentTabbedPane](#getparenttabbedpane)|返回一个指向父选项卡式窗格中。|  
|[CBasePane::GetParentTabWnd](#getparenttabwnd)|返回指向选项卡内的父窗口的指针。|  
|[CBasePane::GetRecentVisibleState](#getrecentvisiblestate)|当从存档中还原一个窗格时，框架将调用此方法。|  
|[CBasePane::HideInPrintPreviewMode](#hideinprintpreviewmode)|指定是否在打印预览中隐藏窗格。|  
|[CBasePane::InsertPane](#insertpane)|使用扩展管理器注册指定窗格。|  
|[CBasePane::IsAccessibilityCompatible](#isaccessibilitycompatible)|指定窗格中是否支持活动辅助功能。|  
|[CBasePane::IsAutoHideMode](#isautohidemode)|确定是否在自动隐藏模式下一个窗格。|  
|[CBasePane::IsDialogControl](#isdialogcontrol)|指定窗格中是否为对话框控件。|  
|[CBasePane::IsDocked](#isdocked)|确定是否停靠窗格。|  
|[CBasePane::IsFloating](#isfloating)|确定是否浮动的窗格。|  
|[CBasePane::IsHorizontal](#ishorizontal)|确定是否水平停靠窗格。|  
|[CBasePane::IsInFloatingMultiPaneFrameWnd](#isinfloatingmultipaneframewnd)|指定是否在多窗格框架窗口中为窗格。|  
|[CBasePane::IsMDITabbed](#ismditabbed)|确定窗格中是否已添加到作为选项卡式文档的 MDI 子窗口。|  
|[CBasePane::IsPaneVisible](#ispanevisible)|指定是否`WS_VISIBLE`标志设置为窗格。|  
|[CBasePane::IsPointNearDockSite](#ispointneardocksite)|确定指定的点是否在停靠站点附近。|  
|[Cbasepane:: Isresizable](#isresizable)|确定是否可以调整大小窗格。|  
|[CBasePane::IsRestoredFromRegistry](#isrestoredfromregistry)|确定是否从注册表还原为窗格。|  
|[CBasePane::IsTabbed](#istabbed)|确定是否已在选项卡式窗口选项卡控件中插入窗格。|  
|`CBasePane::IsTooltipTopmost`|在内部使用。|  
|[CBasePane::IsVisible](#isvisible)|确定窗格中是否可见。|  
|[CBasePane::LoadState](#loadstate)|从注册表加载窗格中的状态。|  
|[CBasePane::MoveWindow](#movewindow)|将移动窗格。|  
|[CBasePane::OnAfterChangeParent](#onafterchangeparent)|当窗格中的父级发生更改时由框架调用。|  
|[CBasePane::OnBeforeChangeParent](#onbeforechangeparent)|只需在窗格中更改其父窗口之前，由框架调用。|  
|[CBasePane::OnDrawCaption](#ondrawcaption)|绘制标题时，框架将调用此方法。|  
|[CBasePane::OnMovePaneDivider](#onmovepanedivider)|当前未使用此方法。|  
|[CBasePane::OnPaneContextMenu](#onpanecontextmenu)|在构建一个菜单，有一个窗格的列表时，由框架调用。|  
|[CBasePane::OnRemoveFromMiniFrame](#onremovefromminiframe)|从其父微型框架窗口中移除一个窗格时，由框架调用。|  
|[CBasePane::OnSetAccData](#onsetaccdata)|`CBasePane`不使用此方法。|  
|`CBasePane::OnUpdateCmdUI`|在内部使用。|  
|[CBasePane::PaneFromPoint](#panefrompoint)|返回包含给定的点的窗格。|  
|`CBasePane::PreTranslateMessage`|类使用[CWinApp](../../mfc/reference/cwinapp-class.md)将窗口消息转换之前调度到[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函数。 (重写[cwnd:: Pretranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|  
|[CBasePane::RecalcLayout](#recalclayout)|`CBasePane`不使用此方法。|  
|[CBasePane::RemovePaneFromDockManager](#removepanefromdockmanager)|注销一个窗格，并将其从列表中的扩展管理器中删除。|  
|[CBasePane::SaveState](#savestate)|将窗格的状态保存到注册表。|  
|[CBasePane::SelectDefaultFont](#selectdefaultfont)|选择给定的设备上下文的默认字体。|  
|`CBasePane::Serialize`|从存档读取该对象或将该对象写入存档。 (重写[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)。)|  
|[CBasePane::SetControlBarStyle](#setcontrolbarstyle)|将控件栏样式设置。|  
|[CBasePane::SetDockingMode](#setdockingmode)|设置窗格中的停靠模式。|  
|`CBasePane::SetMDITabbed`|在内部使用。|  
|[CBasePane::SetPaneAlignment](#setpanealignment)|设置窗格中的对齐方式。|  
|`CBasePane::SetPaneRect`|在内部使用。|  
|[CBasePane::SetPaneStyle](#setpanestyle)|设置窗格中的样式。|  
|`CBasePane::SetRestoredFromRegistry`|在内部使用。|  
|[CBasePane::SetWindowPos](#setwindowpos)|更改大小、 位置和 Z 顺序的一个窗格。|  
|[CBasePane::ShowPane](#showpane)|显示或隐藏窗格。|  
|[CBasePane::StretchPane](#stretchpane)|垂直或水平拉伸窗格。|  
|[CBasePane::UndockPane](#undockpane)|从停靠站点、 默认滑块或当前停靠位置的微型框架窗口中删除窗格。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CBasePane::DoPaint](#dopaint)|填充窗格的背景。|  
  
## <a name="remarks"></a>备注  
 如果您想要创建窗格支持的类，MFC 中可用的扩展坞功能，则必须从中进行派生`CBasePane`或从[CPane 类](../../mfc/reference/cpane-class.md)。  
  
## <a name="customization-tips"></a>自定义提示  
 以下自定义提示适用于`CBasePane Class`和从其继承的任何类︰  
  
-   在创建窗格时，您可以应用几种新的样式︰  
  
    - `AFX_CBRS_FLOAT`使的窗格中的 float 值。  
  
    - `AFX_CBRS_AUTOHIDE`启用自动隐藏模式。  
  
    - `AFX_CBRS_CLOSE`启用关闭 （隐藏） 窗格。  
  
     这些是您可以使用按位或运算组合的标志。  
  
 `CBasePane`实现以下虚拟布尔方法以反映这些标志︰ [CBasePane::CanBeClosed](#canbeclosed)， [CBasePane::CanAutoHide](#canautohide)， [CBasePane::CanFloat](#canfloat)。 您可以重写它们在派生类中用于自定义其行为。  
  
-   您可以通过重写自定义停靠的行为[cbasepane:: Canacceptpane](#canacceptpane)。 已返回您窗格`FALSE`从此方法若要防止另一个窗格停靠到它。  
  
-   如果您想要创建静态窗格中，不能浮动，可阻止其他窗格停靠在其之前 （类似于 OutlookDemo 示例中的 Outlook 栏），将其创建为非浮点并重写[cbasepane:: Doesallowdyninsertbefore](#doesallowdyninsertbefore)返回`FALSE`。 默认实现返回`FALSE`如果窗格中创建但未`AFX_CBRS_FLOAT`样式。  
  
-   创建具有 Id 除-1 之外的所有窗格。  
  
-   若要确定窗格的可见性，请使用[CBasePane::IsVisible](#isvisible)。 它会正确地处理的可见性状态中的选项卡式和自动隐藏模式。  
  
-   如果您想要创建非浮点的可调整大小窗格中，则创建它而无需`AFX_CBRS_FLOAT`样式和调用[CFrameWnd::DockControlBar](../../mfc/reference/cframewnd-class.md#dockcontrolbar)。  
  
-   若要从停靠布局中排除一个窗格或从其停靠栏中删除一个工具栏，调用[CBasePane::UndockPane](#undockpane)。 在自动隐藏模式中的窗格或驻留在选项卡式窗口的选项卡的窗格，则不调用此方法。  
  
-   如果您想为 float 或取消停靠窗格，只是在自动隐藏模式下，你必须致电[CDockablePane::SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode)与`FALSE`作为第一个参数调用之前[CBasePane::FloatPane](#floatpane)或[CBasePane::UndockPane](#undockpane)。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法`CBasePane`类。 该示例演示如何检索从一个窗格`CFrameWndEx`类以及如何设置停靠模式、 窗格中对齐和窗格中的样式。 此代码摘自[Word 板示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_WordPad #&2;](../../mfc/reference/codesnippet/cpp/cbasepane-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxbasepane.h  
  
##  <a name="a-nameaccnotifyobjectfocuseventa--cbasepaneaccnotifyobjectfocusevent"></a><a name="accnotifyobjectfocusevent"></a>CBasePane::AccNotifyObjectFocusEvent  
 `CBasePane`不使用此方法。  
  
```  
virtual void AccNotifyObjectFocusEvent(int);
```  
  
### <a name="parameters"></a>参数  
 [in] `int`  
 未使用。  
  
##  <a name="a-nameaddpanea--cbasepaneaddpane"></a><a name="addpane"></a>CBasePane::AddPane  
 扩展管理器中添加一个窗格。  
  
```  
void AddPane(CBasePane* pBar);
```  
  
### <a name="parameters"></a>参数  
 [in] `pBar`  
 指向要添加一个窗格的指针。  
  
### <a name="remarks"></a>备注  
 这是添加了与管理器的停靠窗格的便捷方法。 通过使用此方法，无需编写代码，用于分析与父框架的类型。  
  
 有关详细信息，请参阅[CDockingManager 类](../../mfc/reference/cdockingmanager-class.md)和[CMDIFrameWndEx::AddPane](../../mfc/reference/cmdiframewndex-class.md#addpane)。  
  
##  <a name="a-nameadjustdockinglayouta--cbasepaneadjustdockinglayout"></a><a name="adjustdockinglayout"></a>Cbasepane:: Adjustdockinglayout  
 若要调整停靠布局的扩展管理器调用将重定向。  
  
```  
virtual void AdjustDockingLayout(HDWP hdwp=NULL);
```  
  
### <a name="parameters"></a>参数  
 [out] `hdwp`  
 一个包含多个窗口位置的结构的句柄。  
  
### <a name="remarks"></a>备注  
 这是调整停靠布局的便捷方法。 通过使用此方法，无需编写代码，用于分析与父框架的类型。  
  
 有关详细信息，请参阅[CDockingManager::AdjustDockingLayout](../../mfc/reference/cdockingmanager-class.md#adjustdockinglayout)  
  
##  <a name="a-nameadjustlayouta--cbasepaneadjustlayout"></a><a name="adjustlayout"></a>Cbasepane:: Adjustlayout  
 由框架来调整窗格中的内部布局调用。  
  
```  
virtual void AdjustLayout();
```  
  
### <a name="remarks"></a>备注  
 当一个窗格，必须将其调整其内部的布局时，框架将调用此方法。 基实现没有任何影响。  
  
##  <a name="a-namecalcfixedlayouta--cbasepanecalcfixedlayout"></a><a name="calcfixedlayout"></a>Cbasepane:: Calcfixedlayout  
 计算控件条的水平大小。  
  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>参数  
 [in] `bStretch`  
 指示是否应被栏拉伸到的帧的大小。 `bStretch`栏的停靠栏 （不可用于停靠） 并不为 0 时停靠或浮动 （适用于停靠） 时，参数为非零值。  
  
 [in] `bHorz`  
 指示栏为水平或垂直方向。 `bHorz`如果的栏是水平方向和垂直方向是否为 0，则为非零参数。  
  
### <a name="return-value"></a>返回值  
 控件条的大小，以像素为单位的`CSize`对象。  
  
### <a name="remarks"></a>备注  
 请参阅备注部分中[CControlBar::CalcFixedLayout](../../mfc/reference/ccontrolbar-class.md#calcfixedlayout)  
  
##  <a name="a-namecanacceptpanea--cbasepanecanacceptpane"></a><a name="canacceptpane"></a>Cbasepane:: Canacceptpane  
 确定是否可停靠窗格中的另一窗格。  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `pBar`  
 指向停靠窗格中的指针。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果可以接受的另一窗格;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 框架将调用此方法之前由指定窗格停靠它`pBar`到当前窗格中。  
  
 使用此方法与[CBasePane::CanBeDocked](#canbedocked)方法，以控制您的应用程序中的其他窗格将窗格的停靠。  
  
 默认实现返回 `FALSE`。  
  
##  <a name="a-namecanautohidea--cbasepanecanautohide"></a><a name="canautohide"></a>CBasePane::CanAutoHide  
 确定窗格中是否支持自动隐藏模式。  
  
```  
virtual BOOL CanAutoHide() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此窗格支持自动隐藏模式;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 框架调用此函数可确定窗格中是否支持自动隐藏模式。  
  
 在构造期间，可以设置此功能通过传递`AFX_CBRS_AUTOHIDE`标记，用于[cbasepane:: Createex](#createex)。  
  
 默认实现可检查`AFX_CBRS_AUTOHIDE`标志。 重写此方法在派生类以自定义此行为。  
  
##  <a name="a-namecanbeattacheda--cbasepanecanbeattached"></a><a name="canbeattached"></a>CBasePane::CanBeAttached  
 确定是否可以到另一个窗格或框架窗口中停靠窗格。  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格中可以停靠到另一个窗格或框架窗口;，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 默认实现返回 `FALSE`。 重写此方法在派生类来启用或禁用的功能而无需调用停靠[CBasePane::EnableDocking](#enabledocking)。  
  
##  <a name="a-namecanbecloseda--cbasepanecanbeclosed"></a><a name="canbeclosed"></a>CBasePane::CanBeClosed  
 确定是否可以关闭窗格。  
  
```  
virtual BOOL CanBeClosed() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果可以关闭窗格中;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 框架调用此方法以确定是否可以关闭窗格。 如果该方法返回`TRUE`、**关闭**按钮添加到窗格的标题栏或窗格浮动的为窗格中的袖珍框架窗口的标题栏。  
  
 在构造期间，可以设置此功能通过传递`AFX_CBRS_CLOSE`标记，用于[cbasepane:: Createex](#createex)。  
  
 默认实现可检查`AFX_CBRS_CLOSE`标志。  
  
##  <a name="a-namecanbedockeda--cbasepanecanbedocked"></a><a name="canbedocked"></a>CBasePane::CanBeDocked  
 确定是否可以到另一窗格停靠窗格。  
  
```  
virtual BOOL CanBeDocked(CBasePane* pDockBar) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `pDockBar`  
 一个指向另一个窗格。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此窗格可以停靠到另一窗格;，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 框架将调用此方法之前由指定窗格停靠它`pDockBar`到当前窗格中。  
  
 使用此方法与[cbasepane:: Canacceptpane](#canacceptpane)方法，以控制您的应用程序中的其他窗格将窗格的停靠。  
  
 默认实现返回 `FALSE`。  
  
##  <a name="a-namecanberesizeda--cbasepanecanberesized"></a><a name="canberesized"></a>CBasePane::CanBeResized  
 确定是否可以调整大小窗格。  
  
```  
virtual BOOL CanBeResized() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格中可以调整大小;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法检查`AFX_CBRS_RESIZE`标志，默认情况下，在指定`CBasePane::OnCreate`。 如果未指定此标志，扩展管理器标志而不是它停放内部可移动窗格。  
  
##  <a name="a-namecanbetabbeddocumenta--cbasepanecanbetabbeddocument"></a><a name="canbetabbeddocument"></a>CBasePane::CanBeTabbedDocument  
 指定窗格中是否可以转换为 MDI 选项卡式文档。  
  
```  
virtual BOOL CanBeTabbedDocument() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格中可以转换到选项卡式文档中。否则为`FALSE`。 `CBasePane::CanBeTabbedDocument` 始终返回 `FALSE`。  
  
### <a name="remarks"></a>备注  
 唯一对象的某些`CBasePane`的派生类型，如[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)，可以转换为选项卡式文档。  
  
##  <a name="a-namecanfloata--cbasepanecanfloat"></a><a name="canfloat"></a>CBasePane::CanFloat  
 确定是否可以浮动窗格。  
  
```  
virtual BOOL CanFloat() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格可以浮动;，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 框架调用此方法以确定是否可以浮动窗格。  
  
 在构造期间，可以设置此功能通过传递`AFX_CBRS_FLOAT`标记，用于[cbasepane:: Createex](#createex)。  
  
> [!NOTE]
>  框架将假定非浮动窗格是静态的不能更改其停靠状态。 因此，该框架不会保存非浮动窗格的停靠状态。  
  
 默认实现可检查`AFX_CBRS_FLOAT`样式。  
  
##  <a name="a-namecanfocusa--cbasepanecanfocus"></a><a name="canfocus"></a>CBasePane::CanFocus  
 指定窗格中是否可以接收焦点。  
  
```  
virtual BOOL CanFocus() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格中可以接收焦点，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生类来控制焦点。 例如，因为工具栏不能接收焦点，则此方法返回`FALSE`时在工具栏上的对象上调用。  
  
 框架尝试设置输入的焦点时停靠或浮动窗格。  
  
##  <a name="a-namecopystatea--cbasepanecopystate"></a><a name="copystate"></a>CBasePane::CopyState  
 复制给定窗格的状态。  
  
```  
virtual void CopyState(CBasePane* pOrgBar);
```  
  
### <a name="parameters"></a>参数  
 [in] `pOrgBar`  
 一个指向另一个窗格。  
  
### <a name="remarks"></a>备注  
 此方法将复制的状态从`pOrgBar`到此窗格。  
  
##  <a name="a-namecreatedefaultminiframea--cbasepanecreatedefaultminiframe"></a><a name="createdefaultminiframe"></a>CBasePane::CreateDefaultMiniframe  
 如果可以浮动窗格中，此方法为其创建的微型框架窗口。  
  
```  
virtual CPaneFrameWnd* CreateDefaultMiniframe(CRect rectInitial);
```  
  
### <a name="parameters"></a>参数  
 [in] `rectInitial`  
 指定的初始坐标的微型框架窗口。  
  
### <a name="return-value"></a>返回值  
 指向新的微型框架窗口的指针或`NULL`如果创建失败。  
  
### <a name="remarks"></a>备注  
 当一个窗格切换到浮动状态时，框架将调用此方法。 方法创建的微型框架窗口，并将窗格中附加到此窗口。  
  
 默认实现返回 `NULL`。  
  
##  <a name="a-namecreateexa--cbasepanecreateex"></a><a name="createex"></a>Cbasepane:: Createex  
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
 指定窗格中的 id。 必须是唯一的。  
  
 [in] `dwControlBarStyle`  
 窗格的样式标志。  
  
 [in] `pContext`  
 指向的指针`CcreateContext`  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则创建窗格否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 创建一个窗口类`lpszClassName`。 如果指定`WS_CAPTION`，此方法清除`WS_CAPTION`样式位和集`CBasePane::m_bHasCaption`到`TRUE`，因为库不支持带有字幕的窗格。  
  
 可以使用子窗口样式和条形图 (CBRS_) 样式的 MFC 控件的任意组合。  
  
 库将添加几个新窗格样式。 下表描述了新的样式︰  
  
|样式|描述|  
|-----------|-----------------|  
|`AFX_CBRS_FLOAT`|窗格可以浮动。|  
|`AFX_CBRS_AUTOHIDE`|窗格中支持自动隐藏模式|  
|`AFX_CBRS_RESIZE`|可以调整大小窗格。 **重要提示︰**未实现此样式。|  
|`AFX_CBRS_CLOSE`|可以关闭窗格。|  
|`AFX_CBRS_AUTO_ROLLUP`|可将其汇总窗格中，当将浮动。|  
|`AFX_CBRS_REGULAR_TABS`|当一个窗格停靠到具有此样式时的另一窗格中时，创建常规选项卡式的窗口。 (有关详细信息，请参阅[CTabbedPane 类](../../mfc/reference/ctabbedpane-class.md)。)|  
|`AFX_CBRS_OUTLOOK_TABS`|当一个窗格停靠到具有此样式时的另一窗格中时，创建 Outlook 样式选项卡式的窗口。 (有关详细信息，请参阅[CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。)|  
  
 若要使用的新样式，他们在指定`dwControlBarStyle`。  
  
##  <a name="a-namedockpanea--cbasepanedockpane"></a><a name="dockpane"></a>Cbasepane:: Dockpane  
 窗格停靠到另一个窗格或框架窗口。  
  
```  
virtual BOOL DockPane(
    CBasePane* pDockBar,  
    LPCRECT lpRect,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDockBar`  
 一个指向另一个窗格。  
  
 [in] `lpRect`  
 指定目标矩形。  
  
 [in] `dockMethod`  
 指定的扩展方法。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果已成功，则停靠控件条，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用此函数可将窗格停靠到另一个窗格或停靠栏 ( [CDockSite 类](../../mfc/reference/cdocksite-class.md)) 由指定`pDockBar`，或到主框架如果`pDockBar`是`NULL`。  
  
 `dockMethod`指定如何停靠窗格。 请参阅[CPane::DockPane](../../mfc/reference/cpane-class.md#dockpane)有关的可能值列表。  
  
##  <a name="a-namedockpaneusingrttia--cbasepanedockpaneusingrtti"></a><a name="dockpaneusingrtti"></a>CBasePane::DockPaneUsingRTTI  
 通过使用运行时类型信息停靠窗格。  
  
```  
void DockPaneUsingRTTI(BOOL bUseDockSite);
```  
  
### <a name="parameters"></a>参数  
 [in] `bUseDockSite`  
 如果`TRUE`，到停靠站点停靠。 如果`FALSE`，停靠到与父框架。  
  
##  <a name="a-namedocktoframewindowa--cbasepanedocktoframewindow"></a><a name="docktoframewindow"></a>CBasePane::DockToFrameWindow  
 可停靠窗格停靠到的帧中。  
  
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
 您希望将停靠到窗格中的父框架的一端。  
  
 [in] `lpRect`  
 所需的大小。  
  
 [in] `dwDockFlags`  
 已忽略。  
  
 [in] `pRelativeBar`  
 已忽略。  
  
 [in] `nRelativeIndex`  
 已忽略。  
  
 [in] `bOuterEdge`  
 如果`TRUE`还有其他可停靠窗格在指定的一侧`dwAlignment`，在其他窗格，请外停靠窗格中更接近于父框架的边缘。 如果`FALSE`，窗格中更接近停靠到客户端区域的中心。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此方法已成功，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法将失败，如果窗格分隔符 ( [CPaneDivider 类](../../mfc/reference/cpanedivider-class.md)) 不能创建。 否则，它始终返回`TRUE`。  
  
##  <a name="a-namedoesallowdyninsertbeforea--cbasepanedoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>Cbasepane:: Doesallowdyninsertbefore  
 确定是否另一个窗格可以动态地插入此窗格中与父框架之间。  
  
```  
virtual BOOL DoesAllowDynInsertBefore() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果用户可以插入另一个窗格;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 框架调用此方法以确定用户是否可以动态插入之前此窗格中的窗格。  
  
 例如，假设您的应用程序创建一个窗格停靠在框架窗口 （如 Outlook 栏中） 的左侧。 若要阻止用户从左边的第一个窗格停靠在另一个窗格中，重写此方法并返回`FALSE`。  
  
 我们建议你重写此方法并返回`FALSE`有关非浮动窗格派生自[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)。  
  
 默认实现返回 `TRUE`。  
  
##  <a name="a-namedopainta--cbasepanedopaint"></a><a name="dopaint"></a>CBasePane::DoPaint  
 填充窗格的背景。  
  
```  
virtual void DoPaint(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
### <a name="remarks"></a>备注  
 默认实现调用当前的可视管理器，以填充背景 ( [CMFCVisualManager::OnFillBarBackground](../../mfc/reference/cmfcvisualmanager-class.md#onfillbarbackground))。  
  
##  <a name="a-nameenabledockinga--cbasepaneenabledocking"></a><a name="enabledocking"></a>CBasePane::EnableDocking  
 启用窗格中的停靠到主框架。  
  
```  
virtual void EnableDocking(DWORD dwAlignment);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwAlignment`  
 指定要启用的停靠对齐方式。  
  
### <a name="remarks"></a>备注  
 调用此方法可启用停靠到主框架的对齐方式。 您可以将传递的组合`CBRS_ALIGN_`标志 (有关详细信息，请参阅[CControlBar::EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking))。  
  
 `EnableDocking`设置内部标志`CBasePane::m_dwEnabledAlignment`和框架停靠窗格时都将检查此标志。  
  
 调用[CBasePane::GetEnabledAlignment](#getenabledalignment)以确定一个窗格的停靠对齐方式。  
  
##  <a name="a-nameenablegrippera--cbasepaneenablegripper"></a><a name="enablegripper"></a>CBasePane::EnableGripper  
 启用或禁用控制手柄。 如果启用了控制手柄，用户可拖动重新定位窗格。  
  
```  
virtual void EnableGripper(BOOL bEnable);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE`若要启用控制手柄;`FALSE`以将其禁用。  
  
### <a name="remarks"></a>备注  
 框架将使用此方法启用而不是使用的控制手柄`WS_CAPTION`样式。  
  
##  <a name="a-namefloatpanea--cbasepanefloatpane"></a><a name="floatpane"></a>CBasePane::FloatPane  
 浮动窗格。  
  
```  
virtual BOOL FloatPane(
    CRect rectFloat,  
    AFX_DOCK_METHOD dockMethod=DM_UNKNOWN,  
    bool bShow=true);
```  
  
### <a name="parameters"></a>参数  
 [in] `rectFloat`  
 指定浮动窗格中的显示位置的屏幕坐标。  
  
 [in] `dockMethod`  
 指定要用于浮动窗格的停靠方法。  
  
 [in] `bShow`  
 指定浮动窗格中是否可见 ( `TRUE`) 或隐藏 ( `FALSE`)。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果已成功，则浮动窗格中否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用此方法以浮动窗格中所指定的屏幕位置`rectFloat`。  
  
##  <a name="a-namegetacchelptopica--cbasepanegetacchelptopic"></a><a name="get_acchelptopic"></a>CBasePane::get_accHelpTopic  
 框架将调用此方法以检索的完整路径`WinHelp`与指定的对象和该文件中的相应主题的标识符相关联的文件。  
  
```  
virtual HRESULT get_accHelpTopic(
    BSTR* pszHelpFile,  
    VARIANT varChild,  
    long* pidTopic);
```  
  
### <a name="parameters"></a>参数  
 [in] `pszHelpFile`  
 地址的指针`BSTR`，它接收的完整路径`WinHelp`是如果有与指定对象关联的文件。  
  
 [in] `varChild`  
 指定是否要检索的帮助主题为对象或某一对象的子元素。 此参数可以是`CHILDID_SELF`（若要获取针对该对象的帮助主题） 或子 ID （以获取帮助主题的一个子对象的元素）。  
  
 [in] `pidTopic`  
 标识`Help`文件的主题，它与指定对象相关联。  
  
### <a name="return-value"></a>返回值  
 `CBasePane`未实现此方法。 因此，`CBasePane::get_accHelpTopic`始终返回`S_FALSE`。  
  
### <a name="remarks"></a>备注  
 此函数是在 MFC 中的活动辅助功能支持的一部分。 重写此函数在派生类以提供有关您的对象的帮助信息。  
  
##  <a name="a-namegetaccselectiona--cbasepanegetaccselection"></a><a name="get_accselection"></a>CBasePane::get_accSelection  
 框架调用此方法以检索所选的对象的子级的此。  
  
```  
virtual HRESULT get_accSelection(VARIANT* pvarChildren);
```  
  
### <a name="parameters"></a>参数  
 [in] `pvarChildren`  
 收到标识所选的子级的信息。  
  
### <a name="return-value"></a>返回值  
 `CBasePane`未实现此方法。 如果 `pvarChildren` 为 `NULL`，则此方法返回 `E_INVALIDARG`。 否则，此方法返回`DISP_E_MEMBERNOTFOUND`。  
  
### <a name="remarks"></a>备注  
 此函数是在 MFC 中的活动辅助功能支持的一部分。 如果您有无窗口的 ActiveX 控件以外的非窗口式用户界面元素，重写此函数在派生类中。  
  
##  <a name="a-namegetcaptionheighta--cbasepanegetcaptionheight"></a><a name="getcaptionheight"></a>CBasePane::GetCaptionHeight  
 返回标题高度。  
  
```  
virtual int GetCaptionHeight() const;  
```  
  
### <a name="return-value"></a>返回值  
 标题高度。  
  
##  <a name="a-namegetcontrolbarstylea--cbasepanegetcontrolbarstyle"></a><a name="getcontrolbarstyle"></a>CBasePane::GetControlBarStyle  
 返回控件栏样式。  
  
```  
virtual DWORD GetControlBarStyle() const 
```  
  
### <a name="return-value"></a>返回值  
 AFX_CBRS_ 标志的按位 OR 组合。  
  
### <a name="remarks"></a>备注  
 返回值是以下可能的值的组合。  
  
|样式|说明|  
|-----------|-----------------|  
|`AFX_CBRS_FLOAT`|使控件条浮点数。|  
|`AFX_CBRS_AUTOHIDE`|启用自动隐藏模式。|  
|`AFX_CBRS_RESIZE`|使控件条的调整大小。 当设置此标志时，则可以在可停靠的窗格中放置控件条。|  
|`AFX_CBRS_CLOSE`|启用的控件条的隐藏。|  
  
##  <a name="a-namegetcurrentalignmenta--cbasepanegetcurrentalignment"></a><a name="getcurrentalignment"></a>CBasePane::GetCurrentAlignment  
 返回当前窗格对齐方式。  
  
```  
virtual DWORD GetCurrentAlignment() const;  
```  
  
### <a name="return-value"></a>返回值  
 控件条的当前对齐方式。 下表显示了可能的值︰  
  
|值|对齐方式|  
|-----------|---------------|  
|`CBRS_ALIGN_LEFT`|左对齐方式。|  
|`CBRS_ALIGN_RIGHT`|右对齐方式。|  
|`CBRS_ALIGN_TOP`|靠上对齐。|  
|`CBRS_ALIGN_BOTTOM`|靠下对齐。|  
  
##  <a name="a-namegetdockingmodea--cbasepanegetdockingmode"></a><a name="getdockingmode"></a>CBasePane::GetDockingMode  
 返回窗格中的当前停靠模式。  
  
```  
virtual AFX_DOCK_TYPE GetDockingMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 DT_STANDARD，如果在拖动窗格中表示在屏幕上拖动矩形。 如果拖动窗格的内容是，DT_IMMEDIATE。  
  
### <a name="remarks"></a>备注  
 框架调用此方法以确定当前停靠窗格的模式。  
  
 如果`CBasePane::m_dockMode`是未定义 (DT_UNDEFINED)，然后停靠模式取自全局停靠模式 ( `AFX_GLOBAL_DATA::m_dockModeGlobal`)。  
  
 通过设置`m_dockMode`或重写`GetDockingMode`可以控制每个窗格的停靠模式。  
  
##  <a name="a-namegetdocksiteframewnda--cbasepanegetdocksiteframewnd"></a><a name="getdocksiteframewnd"></a>CBasePane::GetDockSiteFrameWnd  
 返回一个指向[CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)窗格中的停靠位置的对象。  
  
```  
virtual CWnd* GetDockSiteFrameWnd() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向窗格中的停靠站点的指针。  
  
### <a name="remarks"></a>备注  
 调用此方法来检索指向窗格的停靠站点。 如果浮动的窗格中，可以是如果窗格停靠到主框架的主框架窗口或微型框架窗口停靠站点。  
  
##  <a name="a-namegetenabledalignmenta--cbasepanegetenabledalignment"></a><a name="getenabledalignment"></a>CBasePane::GetEnabledAlignment  
 返回应用于窗格中的 CBRS_ALIGN_ 样式。  
  
```  
virtual DWORD GetEnabledAlignment() const;  
```  
  
### <a name="return-value"></a>返回值  
 CBRS_ALIGN_ 样式组合。 下表显示可能的样式︰  
  
|Flag|已启用的对齐方式|  
|----------|-----------------------|  
|`CBRS_ALIGN_LEFT`|左。|  
|`CBRS_ALIGN_RIGHT`|权限。|  
|`CBRS_ALIGN_TOP`|返回页首。|  
|`CBRS_ALIGN_BOTTOM`|底部。|  
|`CBRS_ALIGN_ANY`|所有标志的组合。|  
  
### <a name="remarks"></a>备注  
 调用此方法以确定窗格中的已启用对齐方式。 已启用的对齐方式意味着一个窗格可停靠到的主框架窗口的旁边。  
  
 使用启用停靠对齐[CBasePane::EnableDocking](#enabledocking)。  
  
##  <a name="a-namegetmfcstylea--cbasepanegetmfcstyle"></a><a name="getmfcstyle"></a>CBasePane::GetMFCStyle  
 返回特定于 MFC 的窗格样式。  
  
```  
virtual DWORD GetMFCStyle() const;  
```  
  
### <a name="return-value"></a>返回值  
 库特定 (AFX_CBRS_) 窗格中样式的组合。  
  
##  <a name="a-namegetpaneicona--cbasepanegetpaneicon"></a><a name="getpaneicon"></a>CBasePane::GetPaneIcon  
 返回窗格中图标的句柄。  
  
```  
virtual HICON GetPaneIcon(BOOL bBigIcon);
```  
  
### <a name="parameters"></a>参数  
 [in] `bBigIcon`  
 如果指定 32 像素的图标 32 像素`TRUE`; 如果由 16 像素图标指定 16 像素`FALSE`。  
  
### <a name="return-value"></a>返回值  
 指向窗格中图标的句柄。 如果不成功，返回`NULL`。  
  
### <a name="remarks"></a>备注  
 默认实现调用[CWnd::GetIcon](../../mfc/reference/cwnd-class.md#geticon)。  
  
##  <a name="a-namegetpanerowa--cbasepanegetpanerow"></a><a name="getpanerow"></a>CBasePane::GetPaneRow  
 返回一个指向[CDockingPanesRow](../../mfc/reference/cdockingpanesrow-class.md)窗格中的停靠位置的对象。  
  
```  
CDockingPanesRow* GetPaneRow();
```  
  
### <a name="return-value"></a>返回值  
 一个指向`CDockingPanesRow`如果停靠窗格中，或`NULL`如果它浮动的。  
  
### <a name="remarks"></a>备注  
 调用此方法来访问一个窗格的停靠位置的行。 例如，若要安排在特定行中的窗格，请调用`GetPaneRow`，然后调用[CDockingPanesRow::ArrangePanes](../../mfc/reference/cdockingpanesrow-class.md#arrangepanes)。  
  
##  <a name="a-namegetpanestylea--cbasepanegetpanestyle"></a><a name="getpanestyle"></a>CBasePane::GetPaneStyle  
 返回的窗格中的样式。  
  
```  
virtual DWORD GetPaneStyle() const;  
```  
  
### <a name="return-value"></a>返回值  
 所设置的控件条样式 （包括 CBRS_ 样式） 的组合[CBasePane::SetPaneStyle](#setpanestyle)可以在创建时的方法。  
  
##  <a name="a-namegetparentdocksitea--cbasepanegetparentdocksite"></a><a name="getparentdocksite"></a>CBasePane::GetParentDockSite  
 返回一个指向父停靠站点。  
  
```  
virtual CDockSite* GetParentDockSite() const;  
```  
  
### <a name="return-value"></a>返回值  
 父停靠站点。  
  
##  <a name="a-namegetparentminiframea--cbasepanegetparentminiframe"></a><a name="getparentminiframe"></a>CBasePane::GetParentMiniFrame  
 返回一个指向父微型框架窗口。  
  
```  
virtual CPaneFrameWnd* GetParentMiniFrame(BOOL bNoAssert=FALSE) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `bNoAssert`  
 如果`TRUE`，此方法不会检查非有效指针。 如果您的应用程序退出时调用此方法，此参数设置为`TRUE`。  
  
### <a name="return-value"></a>返回值  
 父微型框架窗口窗格浮动的; 如果指向的有效指针否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 调用此函数可检索指向父微型框架窗口的指针。 此方法循环访问所有父级，并将检查对象派生自[CPaneFrameWnd 类](../../mfc/reference/cpaneframewnd-class.md)。  
  
 使用`GetParentMiniFrame`以确定是否浮动的窗格。  
  
##  <a name="a-namegetparenttabbedpanea--cbasepanegetparenttabbedpane"></a><a name="getparenttabbedpane"></a>CBasePane::GetParentTabbedPane  
 返回一个指向父选项卡式窗格中。  
  
```  
CBaseTabbedPane* GetParentTabbedPane() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果存在，则父选项卡式窗格指向的指针否则为`NULL`。  
  
##  <a name="a-namegetparenttabwnda--cbasepanegetparenttabwnd"></a><a name="getparenttabwnd"></a>CBasePane::GetParentTabWnd  
 返回指向选项卡内的父窗口的指针。  
  
```  
CMFCBaseTabCtrl* GetParentTabWnd(HWND& hWndTab) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `hWndTab`  
 如果返回值不是`NULL`，此参数将包含父选项卡式窗口的句柄。  
  
### <a name="return-value"></a>返回值  
 到父级的有效指针选项卡式窗口或`NULL`。  
  
### <a name="remarks"></a>备注  
 使用此函数可检索指向父选项卡式窗口的指针。 有时并不足够，以调用`GetParent`，这是因为一个窗格可能会在停靠包装内 ( [CDockablePaneAdapter 类](../../mfc/reference/cdockablepaneadapter-class.md)) 还是内部的窗格中适配器 ( [CDockablePaneAdapter 类](../../mfc/reference/cdockablepaneadapter-class.md))。 通过使用`GetParentTabWnd`能够检索在这种情况下 （假定的父元素选项卡式的窗口） 中的有效指针。  
  
##  <a name="a-namegetrecentvisiblestatea--cbasepanegetrecentvisiblestate"></a><a name="getrecentvisiblestate"></a>CBasePane::GetRecentVisibleState  
 当从存档中还原一个窗格时，框架将调用此方法。  
  
```  
virtual BOOL GetRecentVisibleState() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个`BOOL`，它指定的最新的可见状态。 如果`TRUE`，窗格中是时，可看到序列化，并且应该是当还原时才可见。 如果`FALSE`，窗格中隐藏的序列化和还原时，将隐藏时。  
  
##  <a name="a-namehideinprintpreviewmodea--cbasepanehideinprintpreviewmode"></a><a name="hideinprintpreviewmode"></a>CBasePane::HideInPrintPreviewMode  
 指定是否在打印预览中隐藏窗格。  
  
```  
virtual BOOL HideInPrintPreviewMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格中未显示在打印预览中;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 在打印预览中不显示基窗格。 因此，此方法始终返回`TRUE`。  
  
##  <a name="a-nameinsertpanea--cbasepaneinsertpane"></a><a name="insertpane"></a>CBasePane::InsertPane  
 使用扩展管理器注册指定窗格。  
  
```  
BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pControlBar`  
 指向插入窗格中的指针。  
  
 [in] `pTarget`  
 指向相邻窗格中的指针。  
  
 [in] `bAfter`  
 如果`TRUE`，`pControlBar`之后插入`pTarget`。 如果`FALSE`，`pControlBar`之前插入`pTarget`。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果该方法成功，`FALSE`否则为。  
  
##  <a name="a-nameisaccessibilitycompatiblea--cbasepaneisaccessibilitycompatible"></a><a name="isaccessibilitycompatible"></a>CBasePane::IsAccessibilityCompatible  
 指定窗格中是否支持活动辅助功能。  
  
```  
virtual BOOL IsAccessibilityCompatible();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格中支持活动辅助功能;否则为`FALSE`。  
  
##  <a name="a-nameisautohidemodea--cbasepaneisautohidemode"></a><a name="isautohidemode"></a>CBasePane::IsAutoHideMode  
 确定是否在自动隐藏模式下一个窗格。  
  
```  
virtual BOOL IsAutoHideMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格中的自动隐藏模式;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 基窗格不能自动隐藏。 此方法始终返回 `FALSE`。  
  
##  <a name="a-nameisdialogcontrola--cbasepaneisdialogcontrol"></a><a name="isdialogcontrol"></a>CBasePane::IsDialogControl  
 指定窗格中是否为对话框控件。  
  
```  
BOOL IsDialogControl() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格中为对话框控件;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 框架使用此方法以确保所有窗格的布局一致性。  
  
##  <a name="a-nameisdockeda--cbasepaneisdocked"></a><a name="isdocked"></a>CBasePane::IsDocked  
 确定是否停靠窗格。  
  
```  
virtual BOOL IsDocked() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格中的父级不是最小化框架或窗格浮动在其他窗格; 具有的最小化框架否则为`FALSE`。  
  
##  <a name="a-nameisfloatinga--cbasepaneisfloating"></a><a name="isfloating"></a>CBasePane::IsFloating  
 确定是否浮动的窗格。  
  
```  
virtual BOOL IsFloating() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格浮动;，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法返回的相反值[CBasePane::IsDocked](#isdocked)。  
  
##  <a name="a-nameishorizontala--cbasepaneishorizontal"></a><a name="ishorizontal"></a>CBasePane::IsHorizontal  
 确定是否水平停靠窗格。  
  
```  
virtual BOOL IsHorizontal() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格停靠水平空间。，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 默认实现可检查的当前停靠对齐方式`CBRS_ORIENT_HORZ`。  
  
##  <a name="a-nameisinfloatingmultipaneframewnda--cbasepaneisinfloatingmultipaneframewnd"></a><a name="isinfloatingmultipaneframewnd"></a>CBasePane::IsInFloatingMultiPaneFrameWnd  
 指定是否在多窗格框架窗口中为窗格中 ( [CMultiPaneFrameWnd 类](../../mfc/reference/cmultipaneframewnd-class.md))。  
  
```  
virtual BOOL IsInFloatingMultiPaneFrameWnd() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格中处于多窗格框架窗口。否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 仅可停靠窗格可以浮动在多窗格框架窗口中。 因此，`CBasePane::IsInFloatingMultiPaneFrameWnd`始终返回`FALSE`。  
  
##  <a name="a-nameismditabbeda--cbasepaneismditabbed"></a><a name="ismditabbed"></a>CBasePane::IsMDITabbed  
 确定窗格中是否已添加到作为选项卡式文档的 MDI 子窗口。  
  
```  
virtual BOOL IsMDITabbed() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格中作为选项卡式文档，则添加到 MDI 子窗口否则为`FALSE`。  
  
##  <a name="a-nameispanevisiblea--cbasepaneispanevisible"></a><a name="ispanevisible"></a>CBasePane::IsPaneVisible  
 指定是否`WS_VISIBLE`标志设置为窗格。  
  
```  
BOOL IsPaneVisible() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果`WS_VISIBLE`设置; 否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 使用[CBasePane::IsVisible](#isvisible)来确定窗格的可见性。  
  
##  <a name="a-nameispointneardocksitea--cbasepaneispointneardocksite"></a><a name="ispointneardocksite"></a>CBasePane::IsPointNearDockSite  
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
 指定的点是附近的边缘。 可能的值为`CBRS_ALIGN_LEFT`， `CBRS_ALIGN_RIGHT`， `CBRS_ALIGN_TOP`，和`CBRS_ALIGN_BOTTOM`  
  
 [out] `bOuterEdge`  
 `TRUE`如果该点附近的外边框的停靠站点中;`FALSE`否则为。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果该点附近停靠站点中;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 在扩展管理器中设置的敏感度内时，关键是在停靠站点附近。 默认设置为 15 个像素。  
  
##  <a name="a-nameisresizablea--cbasepaneisresizable"></a><a name="isresizable"></a>Cbasepane:: Isresizable  
 确定是否可以调整大小窗格。  
  
```  
virtual BOOL IsResizable() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果可以调整大小窗格中，用户;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 窗格[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)可调整大小。  
  
 状态栏 ( [CMFCStatusBar 类](../../mfc/reference/cmfcstatusbar-class.md)) 和停靠栏 ( [CDockSite 类](../../mfc/reference/cdocksite-class.md)) 不能调整大小。  
  
##  <a name="a-nameisrestoredfromregistrya--cbasepaneisrestoredfromregistry"></a><a name="isrestoredfromregistry"></a>CBasePane::IsRestoredFromRegistry  
 确定是否从注册表还原为窗格。  
  
```  
virtual BOOL IsRestoredFromRegistry() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果从注册表中; 还原窗格中否则为`FALSE`。  
  
##  <a name="a-nameistabbeda--cbasepaneistabbed"></a><a name="istabbed"></a>CBasePane::IsTabbed  
 确定是否已在选项卡式窗口选项卡控件中插入窗格。  
  
```  
virtual BOOL IsTabbed() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果在一个选项卡式窗口; 一个选项卡中插入控件条否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法检索到的直接父级的指针，并确定是否运行时父类[CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)。  
  
##  <a name="a-nameisvisiblea--cbasepaneisvisible"></a><a name="isvisible"></a>CBasePane::IsVisible  
 确定窗格中是否可见。  
  
```  
virtual BOOL IsVisible() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格中可见;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 使用此方法以确定一个窗格的可见性。 请不要使用`::IsWindowVisible`。  
  
 如果窗格中的选项卡式不 (请参阅[CBasePane::IsTabbed](#istabbed))，此方法检查`WS_VISIBLE`样式。 窗格中选项卡式，此方法将检查父选项卡式窗口的可见性。 如果父窗口可见时，该函数检查的窗格中的选项卡上使用可见性[CMFCBaseTabCtrl::IsTabVisible](../../mfc/reference/cmfcbasetabctrl-class.md#istabvisible)。  
  
##  <a name="a-nameloadstatea--cbasepaneloadstate"></a><a name="loadstate"></a>CBasePane::LoadState  
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
 窗格 id。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则加载窗格状态否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 框架调用此方法以从注册表加载的窗格中的状态。 若要加载保存的其他信息派生类中重写它[CBasePane::SaveState](#savestate)。  
  
##  <a name="a-namemovewindowa--cbasepanemovewindow"></a><a name="movewindow"></a>CBasePane::MoveWindow  
 将移动窗格。  
  
```  
virtual HDWP MoveWindow(
    CRect& rect,  
    BOOL bRepaint = TRUE,  
    HDWP hdwp = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `rect`  
 一个指定新位置和窗格的大小的矩形。  
  
 [in] `bRepaint`  
 如果`TRUE`，窗格中将重新绘制。 如果`FALSE`，窗格中将不会重新绘制。  
  
 [in] `hdwp`  
 延迟的窗口位置结构的句柄。  
  
### <a name="return-value"></a>返回值  
 延迟的窗口位置结构的句柄或`NULL`。  
  
### <a name="remarks"></a>备注  
 如果您通过`NULL`作为`hdwp`参数，此方法通常移动窗口。 如果传递的句柄，则此方法执行延迟的窗口移动。 可以通过调用获取句柄[BeginDeferWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms632672)或通过将存储此方法的以前调用的返回值。  
  
##  <a name="a-nameonafterchangeparenta--cbasepaneonafterchangeparent"></a><a name="onafterchangeparent"></a>CBasePane::OnAfterChangeParent  
 由框架调用窗格中的父发生更改后。  
  
```  
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndOldParent`  
 一个指向上一个父级。  
  
### <a name="remarks"></a>备注  
 窗格中的父更改之后，通常由于停靠或浮动状态操作，框架将调用此方法。  
  
 默认实现不执行任何操作。  
  
##  <a name="a-nameonbeforechangeparenta--cbasepaneonbeforechangeparent"></a><a name="onbeforechangeparent"></a>CBasePane::OnBeforeChangeParent  
 只需在窗格中更改其父窗口之前，由框架调用。  
  
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
 框架之前调用此方法只是窗格中的父更改通常由于停靠、 浮点型或自动隐藏操作。  
  
 默认实现不执行任何操作。  
  
##  <a name="a-nameondrawcaptiona--cbasepaneondrawcaption"></a><a name="ondrawcaption"></a>CBasePane::OnDrawCaption  
 绘制标题时，框架将调用此方法。  
  
```  
virtual void OnDrawCaption();
```  
  
### <a name="remarks"></a>备注  
 此方法不具有的任何功能`CBasePane`类。  
  
##  <a name="a-nameonmovepanedividera--cbasepaneonmovepanedivider"></a><a name="onmovepanedivider"></a>CBasePane::OnMovePaneDivider  
 当前未使用此方法。  
  
```  
virtual void OnMovePaneDivider(CPaneDivider*);
```  
  
### <a name="parameters"></a>参数  
 [in] `CPaneDivider*`  
 未使用。  
  
##  <a name="a-nameonpanecontextmenua--cbasepaneonpanecontextmenu"></a><a name="onpanecontextmenu"></a>CBasePane::OnPaneContextMenu  
 在构建一个菜单，有一个窗格的列表时，由框架调用。  
  
```  
virtual void OnPaneContextMenu(
    CWnd* pParentFrame,  
    CPoint point);
```  
  
### <a name="parameters"></a>参数  
 [in] `pParentFrame`  
 指向与父框架的指针。  
  
 [in] `point`  
 指定的位置的快捷菜单。  
  
### <a name="remarks"></a>备注  
 `OnPaneContextMenu`调用将属于当前的框架窗口的窗格的列表来维护的扩展管理器。 此方法将窗格的名称添加到快捷菜单，并将其显示。 在菜单上的命令显示或隐藏各个窗格。  
  
 重写此方法以自定义此行为。  
  
##  <a name="a-nameonremovefromminiframea--cbasepaneonremovefromminiframe"></a><a name="onremovefromminiframe"></a>CBasePane::OnRemoveFromMiniFrame  
 从其父微型框架窗口中移除一个窗格时，由框架调用。  
  
```  
virtual void OnRemoveFromMiniFrame(CPaneFrameWnd* pMiniFrame);
```  
  
### <a name="parameters"></a>参数  
 [in] `pMiniFrame`  
 指向从中删除窗格中的微型框架窗口的指针。  
  
### <a name="remarks"></a>备注  
 从其父微型框架窗口 （由于停靠，例如） 中移除一个窗格时，框架将调用此方法。  
  
 默认实现不执行任何操作。  
  
##  <a name="a-nameonsetaccdataa--cbasepaneonsetaccdata"></a><a name="onsetaccdata"></a>CBasePane::OnSetAccData  
 `CBasePane`不使用此方法。  
  
```  
virtual BOOL OnSetAccData(long lVal);
```  
  
### <a name="parameters"></a>参数  
 [in] `lVal`  
 未使用。  
  
### <a name="return-value"></a>返回值  
 此方法始终返回 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namepanefrompointa--cbasepanepanefrompoint"></a><a name="panefrompoint"></a>CBasePane::PaneFromPoint  
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
 指定在屏幕坐标中，若要检查该点。  
  
 [in] `nSensitivity`  
 增加此数量的搜索区域。 如果给的定点落在增加的区域中，一个窗格将满足搜索条件。  
  
 [in] `bExactBar`  
 `TRUE`若要忽略`nSensitivity`参数; 否则为`FALSE`。  
  
 [in] `pRTCBarType`  
 如果不是`NULL`，该方法将搜索仅指定类型的窗格。  
  
### <a name="return-value"></a>返回值  
 `CBasePane`-派生的对象，其中包含给定的时间，或`NULL`如果不找到任何窗格。  
  
##  <a name="a-namerecalclayouta--cbasepanerecalclayout"></a><a name="recalclayout"></a>CBasePane::RecalcLayout  
 `CBasePane`不使用此方法。  
  
```  
virtual void RecalcLayout();
```  
  
##  <a name="a-nameremovepanefromdockmanagera--cbasepaneremovepanefromdockmanager"></a><a name="removepanefromdockmanager"></a>CBasePane::RemovePaneFromDockManager  
 注销一个窗格，并将其从列表中的扩展管理器中删除。  
  
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
 指向要删除一个窗格的指针。  
  
 [in] `bDestroy`  
 如果`TRUE`，删除窗格中被销毁。  
  
 [in] `bAdjustLayout`  
 如果`TRUE`，立即调整停靠布局。  
  
 [in] `bAutoHide`  
 如果`TRUE`，停靠布局与自动隐藏栏列表。 如果`FALSE`，停靠布局与正则窗格的列表。  
  
 [in] `pBarReplacement`  
 指向替换删除窗格中的窗格的指针。  
  
##  <a name="a-namesavestatea--cbasepanesavestate"></a><a name="savestate"></a>CBasePane::SaveState  
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
 窗格 id。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则已保存的状态否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 在窗格的状态保存到注册表时，框架将调用此方法。 重写`SaveState`在派生类可存储附加信息。  
  
##  <a name="a-nameselectdefaultfonta--cbasepaneselectdefaultfont"></a><a name="selectdefaultfont"></a>CBasePane::SelectDefaultFont  
 选择给定的设备上下文的默认字体。  
  
```  
CFont* SelectDefaultFont(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 设备上下文。  
  
### <a name="return-value"></a>返回值  
 为默认值的指针[CFont 类](../../mfc/reference/cfont-class.md)对象。  
  
##  <a name="a-namesetcontrolbarstylea--cbasepanesetcontrolbarstyle"></a><a name="setcontrolbarstyle"></a>CBasePane::SetControlBarStyle  
 将控件栏样式设置。  
  
```  
virtual void SetControlBarStyle(DWORD dwNewStyle);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwNewStyle`  
 以下可能的值按位 OR 组合。  
  
|样式|说明|  
|-----------|-----------------|  
|`AFX_CBRS_FLOAT`|使控件条浮点数。|  
|`AFX_CBRS_AUTOHIDE`|启用自动隐藏模式。|  
|`AFX_CBRS_RESIZE`|使控件条的调整大小。 当设置此标志时，则可以在可停靠的窗格中放置控件条。|  
|`AFX_CBRS_CLOSE`|启用的控件条的隐藏。|  
  
##  <a name="a-namesetdockingmodea--cbasepanesetdockingmode"></a><a name="setdockingmode"></a>CBasePane::SetDockingMode  
 设置窗格中的停靠模式。  
  
```  
void SetDockingMode(AFX_DOCK_TYPE dockModeNew);
```  
  
### <a name="parameters"></a>参数  
 [in] `dockModeNew`  
 指定窗格中的新停靠模式。  
  
### <a name="remarks"></a>备注  
 该框架支持两种停靠模式︰ 标准和快速。  
  
 在标准停靠模式下，通过拖动矩形移窗格和最小化框架窗口。 在即时停靠模式下，控件条和最小化框架窗口会立即随移动其上下文。  
  
 最初，通过全局定义停靠模式[CDockingManager::m_dockModeGlobal](../../mfc/reference/cdockingmanager-class.md#m_dockmodeglobal)。 您可以设置为分别使用每个窗格的停靠模式`SetDockingMode`方法。  
  
##  <a name="a-namesetpanealignmenta--cbasepanesetpanealignment"></a><a name="setpanealignment"></a>CBasePane::SetPaneAlignment  
 设置窗格中的对齐方式。  
  
```  
virtual void SetPaneAlignment(DWORD dwAlignment);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwAlignment`  
 指定新的对齐方式。  
  
### <a name="remarks"></a>备注  
 通常情况下，框架将调用此方法，一个窗格，从主框架的一侧停靠到另一个时。  
  
 下表显示的可能值`dwAlignment`:  
  
|值|对齐方式|  
|-----------|---------------|  
|`CBRS_ALIGN_LEFT`|左对齐方式。|  
|`CBRS_ALIGN_RIGHT`|右对齐方式。|  
|`CBRS_ALIGN_TOP`|靠上对齐。|  
|`CBRS_ALIGN_BOTTOM`|靠下对齐。|  
  
##  <a name="a-namesetpanestylea--cbasepanesetpanestyle"></a><a name="setpanestyle"></a>CBasePane::SetPaneStyle  
 设置窗格中的样式。  
  
```  
virtual void SetPaneStyle(DWORD dwNewStyle);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwNewStyle`  
 指定要设置新的样式。  
  
### <a name="remarks"></a>备注  
 此方法可以用于设置任何 afxres.h 中定义的 CBRS_ 样式。 由于窗格中样式和窗格中的对齐方式存储在一起，通过将其结合起来使用当前的对齐方式，如下所示设置新的样式。  
  
 `pPane->SetPaneStyle (pPane->GetCurrentAlignment() | CBRS_TOOLTIPS);`  
  
##  <a name="a-namesetwindowposa--cbasepanesetwindowpos"></a><a name="setwindowpos"></a>CBasePane::SetWindowPos  
 更改大小、 位置和 Z 顺序的一个窗格。  
  
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
 标识`CWnd`对象，它在此之前`CWnd`的 Z 顺序的对象。 有关详细信息，请参阅[CWnd::SetWindowPos](../../mfc/reference/cwnd-class.md#setwindowpos)。  
  
 [in] `x`  
 指定窗口的左侧位置。  
  
 [in] `y`  
 指定窗口顶部的位置。  
  
 [in] `cx`  
 指定窗口的宽度。  
  
 [in] `cy`  
 指定窗口的高度。  
  
 [in] `nFlags`  
 指定的大小和位置选项。 有关详细信息，请参阅[CWnd::SetWindowPos](../../mfc/reference/cwnd-class.md#setwindowpos)。  
  
 [in] `hdwp`  
 包含一个或多个窗口的大小和位置信息的结构的句柄。  
  
### <a name="return-value"></a>返回值  
 更新后的延迟的窗口位置结构的句柄或`NULL`。  
  
### <a name="remarks"></a>备注  
 如果`pWndInsertAfter`是`NULL`，此方法调用[CWnd::SetWindowPos](../../mfc/reference/cwnd-class.md#setwindowpos)。 如果`pWndInsertAfter`为非`NULL`，此方法调用`DeferWindowPos`。  
  
##  <a name="a-nameshowpanea--cbasepaneshowpane"></a><a name="showpane"></a>CBasePane::ShowPane  
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
 如果`TRUE`，窗格中处于活动状态时所示。  
  
### <a name="remarks"></a>备注  
 此方法显示或隐藏窗格。 使用此方法，而不是`ShowWindow`因为此方法通知有关中窗格的可见性的更改相关的停靠管理人员。  
  
 使用[CBasePane::IsVisible](#isvisible)来确定一个窗格的当前可见。  
  
##  <a name="a-namestretchpanea--cbasepanestretchpane"></a><a name="stretchpane"></a>CBasePane::StretchPane  
 垂直或水平拉伸窗格。  
  
```  
virtual CSize StretchPane(
    int nLength,  
    BOOL bVert);
```  
  
### <a name="parameters"></a>参数  
 [in] `nLength`  
 进行拉伸窗格中所依据长度。  
  
 [in] `bVert`  
 如果`TRUE`，垂直拉伸窗格。 如果`FALSE`，水平伸缩窗格。  
  
### <a name="return-value"></a>返回值  
 已扩展窗格中的大小。  
  
##  <a name="a-nameundockpanea--cbasepaneundockpane"></a><a name="undockpane"></a>CBasePane::UndockPane  
 从停靠站点、 默认滑块或当前停靠位置的微型框架窗口中删除窗格。  
  
```  
virtual void UndockPane(BOOL bDelay=FALSE);
```  
  
### <a name="parameters"></a>参数  
 `bDelay`  
 如果为 TRUE，停靠布局是不立即重新计算。  
  
### <a name="remarks"></a>备注  
 调用此方法来操作窗格中的状态或排除的停靠布局中的窗格。  
  
 如果您想要继续使用此窗格中，调用[cbasepane:: Dockpane](#dockpane)或[CBasePane::FloatPane](#floatpane)之前调用此方法。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CPane](../../mfc/reference/cbasepane-class.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)

