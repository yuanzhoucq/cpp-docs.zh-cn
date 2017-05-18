---
title: "CDockablePane 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDockablePane
- AFXDOCKABLEPANE/CDockablePane
- AFXDOCKABLEPANE/CDockablePane::CDockablePane
- AFXDOCKABLEPANE/CDockablePane::AttachToTabWnd
- AFXDOCKABLEPANE/CDockablePane::CalcFixedLayout
- AFXDOCKABLEPANE/CDockablePane::CanAcceptMiniFrame
- AFXDOCKABLEPANE/CDockablePane::CanAcceptPane
- AFXDOCKABLEPANE/CDockablePane::CanAutoHide
- AFXDOCKABLEPANE/CDockablePane::CanBeAttached
- AFXDOCKABLEPANE/CDockablePane::ConvertToTabbedDocument
- AFXDOCKABLEPANE/CDockablePane::CopyState
- AFXDOCKABLEPANE/CDockablePane::Create
- AFXDOCKABLEPANE/CDockablePane::CreateDefaultPaneDivider
- AFXDOCKABLEPANE/CDockablePane::CreateEx
- AFXDOCKABLEPANE/CDockablePane::CreateTabbedPane
- AFXDOCKABLEPANE/CDockablePane::DockPaneContainer
- AFXDOCKABLEPANE/CDockablePane::DockPaneStandard
- AFXDOCKABLEPANE/CDockablePane::DockToRecentPos
- AFXDOCKABLEPANE/CDockablePane::DockToWindow
- AFXDOCKABLEPANE/CDockablePane::EnableAutohideAll
- AFXDOCKABLEPANE/CDockablePane::EnableGripper
- AFXDOCKABLEPANE/CDockablePane::GetAHRestoredRect
- AFXDOCKABLEPANE/CDockablePane::GetAHSlideMode
- AFXDOCKABLEPANE/CDockablePane::GetCaptionHeight
- AFXDOCKABLEPANE/CDockablePane::GetDefaultPaneDivider
- AFXDOCKABLEPANE/CDockablePane::GetDockingStatus
- AFXDOCKABLEPANE/CDockablePane::GetDragSensitivity
- AFXDOCKABLEPANE/CDockablePane::GetLastPercentInPaneContainer
- AFXDOCKABLEPANE/CDockablePane::GetTabArea
- AFXDOCKABLEPANE/CDockablePane::GetTabbedPaneRTC
- AFXDOCKABLEPANE/CDockablePane::HasAutoHideMode
- AFXDOCKABLEPANE/CDockablePane::HitTest
- AFXDOCKABLEPANE/CDockablePane::IsAutohideAllEnabled
- AFXDOCKABLEPANE/CDockablePane::IsAutoHideMode
- AFXDOCKABLEPANE/CDockablePane::IsDocked
- AFXDOCKABLEPANE/CDockablePane::IsHideInAutoHideMode
- AFXDOCKABLEPANE/CDockablePane::IsInFloatingMultiPaneFrameWnd
- AFXDOCKABLEPANE/CDockablePane::IsResizable
- AFXDOCKABLEPANE/CDockablePane::IsTabLocationBottom
- AFXDOCKABLEPANE/CDockablePane::IsTracked
- AFXDOCKABLEPANE/CDockablePane::IsVisible
- AFXDOCKABLEPANE/CDockablePane::OnAfterChangeParent
- AFXDOCKABLEPANE/CDockablePane::OnAfterDockFromMiniFrame
- AFXDOCKABLEPANE/CDockablePane::OnBeforeChangeParent
- AFXDOCKABLEPANE/CDockablePane::OnBeforeFloat
- AFXDOCKABLEPANE/CDockablePane::RemoveFromDefaultPaneDividier
- AFXDOCKABLEPANE/CDockablePane::ReplacePane
- AFXDOCKABLEPANE/CDockablePane::RestoreDefaultPaneDivider
- AFXDOCKABLEPANE/CDockablePane::SetAutoHideMode
- AFXDOCKABLEPANE/CDockablePane::SetAutoHideParents
- AFXDOCKABLEPANE/CDockablePane::SetLastPercentInPaneContainer
- AFXDOCKABLEPANE/CDockablePane::SetRestoredDefaultPaneDivider
- AFXDOCKABLEPANE/CDockablePane::SetTabbedPaneRTC
- AFXDOCKABLEPANE/CDockablePane::ShowPane
- AFXDOCKABLEPANE/CDockablePane::Slide
- AFXDOCKABLEPANE/CDockablePane::ToggleAutoHide
- AFXDOCKABLEPANE/CDockablePane::UndockPane
- AFXDOCKABLEPANE/CDockablePane::CheckAutoHideCondition
- AFXDOCKABLEPANE/CDockablePane::CheckStopSlideCondition
- AFXDOCKABLEPANE/CDockablePane::DrawCaption
- AFXDOCKABLEPANE/CDockablePane::OnPressButtons
- AFXDOCKABLEPANE/CDockablePane::OnSlide
- AFXDOCKABLEPANE/CDockablePane::m_bDisableAnimation
- AFXDOCKABLEPANE/CDockablePane::m_bHideInAutoHideMode
- AFXDOCKABLEPANE/CDockablePane::m_nSlideSteps
dev_langs:
- C++
helpviewer_keywords:
- CDockablePane class
ms.assetid: e2495f4c-765f-48f9-a2e2-e45e47608d91
caps.latest.revision: 34
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: dea1f1ce66c0e9bedbe83109ab62055a4af2ebce
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cdockablepane-class"></a>CDockablePane Class
实现可在停靠站点停靠或包含在选项卡式窗格中的窗格。  
  
## <a name="syntax"></a>语法  
  
```  
class CDockablePane : public CPane  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CDockablePane::CDockablePane](#cdockablepane)|构造并初始化一个 `CDockablePane` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CDockablePane::AttachToTabWnd](#attachtotabwnd)|将一个窗格附加到另一个窗格。 这将创建一个选项卡式的窗格。|  
|[CDockablePane::CalcFixedLayout](#calcfixedlayout)|返回的窗格中矩形的大小。|  
|[CDockablePane::CanAcceptMiniFrame](#canacceptminiframe)|确定是否为指定的微型框架可停靠窗格。|  
|[CDockablePane::CanAcceptPane](#canacceptpane)|确定是否可停靠当前窗格中的另一窗格。|  
|[CDockablePane::CanAutoHide](#canautohide)|确定窗格中是否支持自动隐藏模式。 (重写[CBasePane::CanAutoHide](../../mfc/reference/cbasepane-class.md#canautohide)。)|  
|[CDockablePane::CanBeAttached](#canbeattached)|确定是否可以到另一窗格停靠当前窗格。|  
|[CDockablePane::ConvertToTabbedDocument](#converttotabbeddocument)|将一个或多个可停靠窗格转换为 MDI 选项卡式文档。|  
|[CDockablePane::CopyState](#copystate)|将复制可停靠窗格的状态。|  
|[CDockablePane::Create](#create)|创建 Windows 控件，并将其附加到`CDockablePane`对象。|  
|[CDockablePane::CreateDefaultPaneDivider](#createdefaultpanedivider)|创建到框架窗口停靠窗格中的默认分隔符。|  
|[CDockablePane::CreateEx](#createex)|创建 Windows 控件，并将其附加到`CDockablePane`对象。|  
|[CDockablePane::CreateTabbedPane](#createtabbedpane)|从当前窗格中创建一个选项卡式的窗格。|  
|[CDockablePane::DockPaneContainer](#dockpanecontainer)|停靠到窗格中的容器。|  
|[CDockablePane::DockPaneStandard](#dockpanestandard)|通过使用大纲 （标准） 停靠停靠窗格。|  
|`CDockablePane::DockToFrameWindow`|在内部使用。 若要将停靠窗格中，请使用[CPane::DockPane](../../mfc/reference/cpane-class.md#dockpane)或[CDockablePane::DockToWindow](#docktowindow)。|  
|[CDockablePane::DockToRecentPos](#docktorecentpos)|窗格停靠到其存储的最新停靠位置。|  
|[CDockablePane::DockToWindow](#docktowindow)|一个停靠窗格停靠到另一停靠窗格。|  
|[CDockablePane::EnableAutohideAll](#enableautohideall)|启用或禁用此窗格以及容器中的其他窗格中的自动隐藏模式。|  
|[CDockablePane::EnableGripper](#enablegripper)|显示或隐藏的标题 （控制手柄）。|  
|[CDockablePane::GetAHRestoredRect](#getahrestoredrect)|指定时在自动隐藏模式下可见窗格中的位置。|  
|[CDockablePane::GetAHSlideMode](#getahslidemode)|检索窗格中的自动隐藏幻灯片模式。|  
|`CDockablePane::GetAutoHideButton`|在内部使用。|  
|`CDockablePane::GetAutoHideToolBar`|在内部使用。|  
|[CDockablePane::GetCaptionHeight](#getcaptionheight)|返回当前标题的高度。|  
|[CDockablePane::GetDefaultPaneDivider](#getdefaultpanedivider)|返回窗格中的容器的默认窗格分隔符。|  
|[CDockablePane::GetDockingStatus](#getdockingstatus)|确定一个窗格停靠的能力根据提供的指针的位置。|  
|[CDockablePane::GetDragSensitivity](#getdragsensitivity)|返回停靠窗格中拖动的敏感性。|  
|[CDockablePane::GetLastPercentInPaneContainer](#getlastpercentinpanecontainer)|检索一个窗格，在其容器中所占据的空间的百分比。|  
|[CDockablePane::GetTabArea](#gettabarea)|检索窗格中的选项卡区域。|  
|[CDockablePane::GetTabbedPaneRTC](#gettabbedpanertc)|返回有关时另一个窗格停靠到当前窗格中，将创建一个选项卡式窗口的运行时类信息。|  
|[CDockablePane::HasAutoHideMode](#hasautohidemode)|指定是否可以为自动隐藏模式切换停靠窗格。|  
|[CDockablePane::HitTest](#hittest)|指定在用户单击鼠标的其中一个窗格中的特定位置。|  
|`CDockablePane::IsAccessibilityCompatible`|在内部使用。|  
|[CDockablePane::IsAutohideAllEnabled](#isautohideallenabled)|指示是否可以将停靠窗格中的容器中的所有其他窗格放置在自动隐藏模式下。|  
|[CDockablePane::IsAutoHideMode](#isautohidemode)|确定是否在自动隐藏模式下一个窗格。|  
|`CDockablePane::IsChangeState`|在内部使用。|  
|[CDockablePane::IsDocked](#isdocked)|确定是否停靠当前窗格。|  
|[CDockablePane::IsHideInAutoHideMode](#ishideinautohidemode)|确定的行为的窗格，只是在自动隐藏模式下，如果它正在显示 （或隐藏） 通过调用`ShowPane`。|  
|[CDockablePane::IsInFloatingMultiPaneFrameWnd](#isinfloatingmultipaneframewnd)|指定是否在多窗格框架窗口中为窗格。|  
|[CDockablePane::IsResizable](#isresizable)|指定是否可以窗格中的大小。|  
|[CDockablePane::IsTabLocationBottom](#istablocationbottom)|指定选项卡是否位于顶部或底部的窗格。|  
|[CDockablePane::IsTracked](#istracked)|指定是否由用户进行拖动一个窗格。|  
|[CDockablePane::IsVisible](#isvisible)|确定当前窗格是否可见。|  
|[Cdockablepane:: Loadstate](http://msdn.microsoft.com/en-us/96110136-4f46-4764-8a76-3b4abaf77917)|在内部使用。|  
|[CDockablePane::OnAfterChangeParent](#onafterchangeparent)|当一个窗格的父级发生更改时由框架调用。 (重写[CPane::OnAfterChangeParent](../../mfc/reference/cpane-class.md#onafterchangeparent)。)|  
|[CDockablePane::OnAfterDockFromMiniFrame](#onafterdockfromminiframe)|在框架窗口停靠浮动停靠栏时由框架调用。|  
|[CDockablePane::OnBeforeChangeParent](#onbeforechangeparent)|在窗格中的父级是将要发生更改时由框架调用。 (重写[CPane::OnBeforeChangeParent](../../mfc/reference/cpane-class.md#onbeforechangeparent)。)|  
|[CDockablePane::OnBeforeFloat](#onbeforefloat)|当一个窗格处于有关为浮点数，由框架调用。 (重写[CPane::OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat)。)|  
|[CDockablePane::RemoveFromDefaultPaneDividier](#removefromdefaultpanedividier)|当一个窗格正在取消停靠时，框架将调用此方法。|  
|[CDockablePane::ReplacePane](#replacepane)|替换指定的窗格为窗格。|  
|[CDockablePane::RestoreDefaultPaneDivider](#restoredefaultpanedivider)|一个窗格进行反序列化以还原默认窗格分隔符时，框架将调用此方法。|  
|`CDockablePane::SaveState`|在内部使用。|  
|`CDockablePane::Serialize`|序列化窗格。 （重写 `CBasePane::Serialize`。）|  
|[CDockablePane::SetAutoHideMode](#setautohidemode)|切换可见停靠窗格和自动隐藏模式。|  
|[CDockablePane::SetAutoHideParents](#setautohideparents)|设置自动隐藏按钮和窗格中的自动隐藏工具栏。|  
|`CDockablePane::SetDefaultPaneDivider`|在内部使用。|  
|[CDockablePane::SetLastPercentInPaneContainer](#setlastpercentinpanecontainer)|设置的一个窗格，在其容器中所占据的空间的百分比。|  
|`CDockablePane::SetResizeMode`|在内部使用。|  
|[CDockablePane::SetRestoredDefaultPaneDivider](#setrestoreddefaultpanedivider)|还原的默认窗格分隔符设置。|  
|[CDockablePane::SetTabbedPaneRTC](#settabbedpanertc)|设置两个窗格停靠在一起时，将创建一个选项卡式窗口的运行时类信息。|  
|[CDockablePane::ShowPane](#showpane)|显示或隐藏窗格。|  
|[CDockablePane::Slide](#slide)|显示或隐藏一个滑动动画，其中显示了仅当窗格中处于自动隐藏模式时具有的窗格。|  
|[CDockablePane::ToggleAutoHide](#toggleautohide)|切换自动隐藏模式。 (重写[CPane::ToggleAutoHide](../../mfc/reference/cpane-class.md#toggleautohide) 。)|  
|[CDockablePane::UndockPane](#undockpane)|中取消停靠窗格中，从主框架窗口或袖珍框架窗口容器。|  
|`CDockablePane::UnSetAutoHideMode`|在内部使用。 若要设置自动隐藏模式，请使用[CDockablePane::SetAutoHideMode](#setautohidemode)|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CDockablePane::CheckAutoHideCondition](#checkautohidecondition)|决定是否 （在自动隐藏模式下） 隐藏停靠窗格。|  
|[CDockablePane::CheckStopSlideCondition](#checkstopslidecondition)|确定何时自动隐藏停靠窗格应停止滑动。|  
|[CDockablePane::DrawCaption](#drawcaption)|绘制的停靠窗格标题 （控制手柄）。|  
|[CDockablePane::OnPressButtons](#onpressbuttons)|当用户按下标题按钮以外调用`AFX_HTCLOSE`和`AFX_HTMAXBUTTON`按钮。|  
|[CDockablePane::OnSlide](#onslide)|由框架时显示或隐藏窗格中呈现的自动隐藏幻灯片效果调用。|  
  
### <a name="data-members"></a>数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CDockablePane::m_bDisableAnimation](#m_bdisableanimation)|指定是否禁用了自动隐藏的可停靠窗格中的动画效果。|  
|[CDockablePane::m_bHideInAutoHideMode](#m_bhideinautohidemode)|当窗格中处于自动隐藏模式时，请确定窗格中的行为。|  
|[CDockablePane::m_nSlideSteps](#m_nslidesteps)|指定窗格中的动画速度时正对其进行显示或隐藏在自动隐藏模式下。|  
  
## <a name="remarks"></a>备注  
 `CDockablePane`实现以下功能︰  
  
-   到主框架窗口的停靠窗格。  
  
-   切换到自动隐藏模式下一个窗格。  
  
-   将一个窗格附加到选项卡式窗口。  
  
-   浮点袖珍框架窗口的窗格中。  
  
-   到浮点袖珍框架窗口中的另一窗格的停靠窗格。  
  
-   调整窗格的大小。  
  
-   加载和保存停靠窗格的状态。  
  
    > [!NOTE]
    >  状态信息保存到 Windows 注册表中。  
  
-   无论有标题，请创建一个窗格。 标题可将文本标签，并且它可以填充渐变颜色。  
  
-   显示窗格的内容的同时拖动一个窗格  
  
-   显示拖动矩形的同时拖动一个窗格。  
  
 若要在您的应用程序中使用停靠窗格中，派生出您窗格中的类从`CDockablePane`类。 或者将派生的对象嵌入到主框架窗口对象或控制您的窗格的实例的窗口对象。 然后，调用[CDockablePane::Create](#create)方法或[CDockablePane::CreateEx](#createex)方法进行处理时`WM_CREATE`主框架窗口中的消息。 最后，通过调用设置窗格对象[CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking)， [cbasepane:: Dockpane](../../mfc/reference/cbasepane-class.md#dockpane)，或[CDockablePane::AttachToTabWnd](#attachtotabwnd)。  
  
## <a name="customization-tips"></a>自定义提示  
 以下提示适用于`CDockablePane`对象︰  
  
-   如果调用[CDockablePane::AttachToTabWnd](#attachtotabwnd)对于两个非选项卡式、 可停靠窗格，指向选项卡式窗口的指针将返回在`ppTabbedControlBar`参数。 您可以继续使用此参数将选项卡添加到选项卡式窗口。  
  
-   这种由创建的选项卡式窗格[CDockablePane::AttachToTabWnd](#attachtotabwnd)由`CDockablePane`对象在`pTabControlBarAttachTo`参数。 您可以调用[CDockablePane::SetTabbedPaneRTC](#settabbedpanertc)到设置的选项卡式窗格种类`CDockablePane`将创建。 默认类型由`dwTabbedStyle`的[CDockablePane::Create](#create)当您首次创建`CDockablePane`。 如果`dwTabbedStyle`是默认的类型是的 AFX_CBRS_OUTLOOK_TABS [CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md); 如果`dwTabbedStyle`是默认的类型是的 AFX_CBRS_REGULAR_TABS [CTabbedPane 类](../../mfc/reference/ctabbedpane-class.md)。  
  
-   如果您想要将一个可停靠窗格停靠到另一台，则调用[CDockablePane::DockToWindow](#docktowindow)方法。 原始窗格中必须被停靠在某处之前调用此方法。  
  
-   成员变量[CDockablePane::m_bHideInAutoHideMode](#m_bhideinautohidemode)控件如何可停靠窗格行为在自动隐藏模式下在调用时[CDockablePane::ShowPane](#showpane)。 如果此成员变量设置为`TRUE`，将隐藏可停靠窗格以及它们的自动隐藏按钮。 否则，它们将滑入和签出。  
  
-   可以通过设置禁用自动隐藏动画[CDockablePane::m_bDisableAnimation](#m_bdisableanimation)到成员变量`TRUE`。  
  
## <a name="example"></a>示例  
 下面的示例演示如何配置`CDockablePane`使用中的各种方法的对象`CDockablePane`类。 该示例演示了如何以启用自动隐藏可停靠窗格中的所有功能、 标题或控制手柄、 都启用自动隐藏模式、 显示窗格中，和对窗格，只是在自动隐藏模式下进行动画处理。 此代码段属于[Visual Studio 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo #&27;](../../mfc/codesnippet/cpp/cdockablepane-class_1.cpp)]  
[!code-cpp[NVC_MFC_VisualStudioDemo #&28;](../../mfc/codesnippet/cpp/cdockablepane-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxDockablePane.h  
  
##  <a name="attachtotabwnd"></a>CDockablePane::AttachToTabWnd  
 将当前窗格中附加到目标窗格中，创建一个选项卡式的窗格。  
  
```  
virtual CDockablePane* AttachToTabWnd(
    CDockablePane* pTabControlBarAttachTo,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bSetActive= TRUE,  
    CDockablePane** ppTabbedControlBar = NULL);  
```  
  
### <a name="parameters"></a>参数  
 [in][out]`pTabControlBarAttachTo`  
 指定当前窗格中将附加到目标窗格。 目标窗格中必须是可停靠窗格。  
  
 [in] `dockMethod`  
 指定的扩展方法。  
  
 [in] `bSetActive`  
 `TRUE`若要在附加操作; 后激活选项卡式窗格中否则为`FALSE`。  
  
 [out] `ppTabbedControlBar`  
 包含附加操作生成的选项卡式的窗格。  
  
### <a name="return-value"></a>返回值  
 指向当前窗格中，如果它不是选项卡式的窗格中;否则为指向选项卡式窗格中，附加操作生成的指针。 返回值是`NULL`或如果不能附加当前窗格中，如果发生错误。  
  
### <a name="remarks"></a>备注  
 在一个可停靠窗格附加到另一个窗格使用此方法时，将发生以下情况︰  
  
1.  Framework 检查是否目标窗格中`pTabControlBarAttachTo`正则表达式停靠窗格或如果它派生自[CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)。  
  
2.  如果目标窗格中，选项卡式的窗格框架将当前窗格中向其添加为一个选项卡。  
  
3.  如果目标窗格中，常规的停靠窗格框架将创建一个选项卡式的窗格。  
  
    -   框架将调用`pTabControlBarAttachTo->CreateTabbedPane`。 新选项卡式窗格中的样式取决于`m_pTabbedControlBarRTC`成员。 默认情况下，此成员设置为运行时类的[CTabbedPane](../../mfc/reference/ctabbedpane-class.md)。 如果您通过`AFX_CBRS_OUTLOOK_TABS`样式为`dwTabbedStyle`参数[CDockablePane::Create](#create)方法中，运行时类对象设置为运行时类的[CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)。 可以在任何时候，若要更改新窗格中的样式更改此成员。  
  
    -   当此方法创建选项卡式窗格中时，框架将替换指向的指针`pTabControlBarAttachTo`（窗格中是否停靠或浮动处于多袖珍框架窗口） 用一个指针指向新建选项卡式窗格中。  
  
    -   框架就会将`pTabControlBarAttachTo`作为第一个选项卡选项卡式窗格中的窗格。 该框架会将当前窗格中添加作为第二个选项卡。  
  
4.  如果当前窗格中派生自`CBaseTabbedPane`，所有其选项卡移动到`pTabControlBarAttachTo`当前窗格中将被破坏。 因此，应小心时调用此方法，因为该方法将返回到当前窗格中的指针可能无效。  
  
 如果生成停靠布局时，可附加到另一个窗格中，设置`dockMethod`到`DM_SHOW`。  
  
 另一个窗格附加到它之前，应该停靠的第一个窗格。  
  
##  <a name="calcfixedlayout"></a>CDockablePane::CalcFixedLayout  
 返回的窗格中矩形的大小。  
  
```  
virtual CSize CalcFixedLayout(
    BOOL bStretch,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>参数  
 [in] `bStretch`  
 未使用。  
  
 [in] `bHorz`  
 未使用。  
  
### <a name="return-value"></a>返回值  
 一个`CSize`对象，其中包含的窗格中矩形的大小。  
  
##  <a name="canacceptminiframe"></a>CDockablePane::CanAcceptMiniFrame  
 确定是否为指定的最小化框架可停靠窗格。  
  
```  
virtual BOOL CanAcceptMiniFrame(CPaneFrameWnd* pMiniFrame) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `pMiniFrame`  
 指向 `CPaneFrameWnd` 对象的指针。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果`pMiniFrame`可停靠到窗格中; 否则为`FALSE`。  
  
##  <a name="canacceptpane"></a>CDockablePane::CanAcceptPane  
 确定是否可停靠当前窗格中的另一窗格。  
  
```  
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `pBar`  
 指定将窗格停靠到当前窗格中。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果指定窗格中可停靠此窗格;，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 前一个窗格停靠到当前窗格中，框架将调用此方法。  
  
 重写此函数在派生类来启用或禁用停靠到特定窗格中。  
  
 默认情况下，此方法返回`TRUE`如果`pBar`或其父类型`CDockablePane`。  
  
##  <a name="canautohide"></a>CDockablePane::CanAutoHide  
 确定是否窗格中可以自动隐藏。  
  
```  
virtual BOOL CanAutoHide() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格中可以自动隐藏;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 `CDockablePane::CanAutoHide`返回`FALSE`在任何以下情况之一︰  
  
-   窗格中有没有父级。  
  
-   扩展管理器不允许要自动隐藏的窗格。  
  
-   不停靠窗格。  
  
##  <a name="canbeattached"></a>CDockablePane::CanBeAttached  
 确定是否可以到另一窗格停靠当前窗格。  
  
```  
virtual BOOL CanBeAttached() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果可停靠窗格中可以停靠到另一个窗格或主框架窗口;，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 默认情况下，此方法始终返回`TRUE`。 重写此方法在派生类来启用或禁用而无需调用停靠[CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking)。  
  
##  <a name="cdockablepane"></a>CDockablePane::CDockablePane  
 构造并初始化[CDockablePane](../../mfc/reference/cdockablepane-class.md)对象。  
  
```  
CDockablePane();
```  
  
### <a name="remarks"></a>备注  
 在构造可停靠窗格对象后，调用[CDockablePane::Create](#create)或[CDockablePane::CreateEx](#createex)来创建它。  
  
##  <a name="converttotabbeddocument"></a>CDockablePane::ConvertToTabbedDocument  
 将一个或多个可停靠窗格转换为 MDI 选项卡式文档。  
  
```  
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bActiveTabOnly`  
 转换时`CTabbedPane`，指定`TRUE`转换仅活动选项卡。 指定`FALSE`要转换的窗格中的所有选项卡。  
  
##  <a name="checkautohidecondition"></a>CDockablePane::CheckAutoHideCondition  
 确定是否停靠窗格处于隐藏状态 （也称为自动隐藏模式）。  
  
```  
virtual BOOL CheckAutoHideCondition();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果满足隐藏条件;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 框架将使用一个计时器以定期检查是否隐藏自动隐藏可停靠窗格。 该方法返回`TRUE`时窗格中未处于活动状态，不在正调整大小窗格中，并且将鼠标指针离开窗格。  
  
 如果满足所有符合上述条件，框架将调用[CDockablePane::Slide](#slide)要隐藏窗格。  
  
##  <a name="checkstopslidecondition"></a>CDockablePane::CheckStopSlideCondition  
 确定何时自动隐藏停靠窗格应停止滑动。  
  
```  
virtual BOOL CheckStopSlideCondition(BOOL bDirection);
```  
  
### <a name="parameters"></a>参数  
 [in] `bDirection`  
 `TRUE`如果窗格中可见;`FALSE`如果窗格中处于隐藏状态。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果满足的停止条件;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 当可停靠的窗格中设置为自动隐藏模式时，框架将使用滑动效果以显示或隐藏窗格。 当滑动窗格中，框架将调用此函数。 `CheckStopSlideCondition`返回`TRUE`窗格中完全可见时或当完全隐藏。  
  
 重写此方法在派生类来实现自定义自动隐藏一些特殊效果。  
  
##  <a name="copystate"></a>CDockablePane::CopyState  
 将复制可停靠窗格的状态。  
  
```  
virtual void CopyState(CDockablePane* pOrgBar);
```  
  
### <a name="parameters"></a>参数  
 [in] `pOrgBar`  
 指向可停靠的窗格中的指针。  
  
### <a name="remarks"></a>备注  
 `CDockablePane::CopyState`将复制的状态`pOrgBar`到当前窗格中通过调用以下方法︰  
  
- [CPane::CopyState](../../mfc/reference/cpane-class.md#copystate)  
  
- [CDockablePane::GetAHRestoredRect](#getahrestoredrect)  
  
- [CDockablePane::GetAHSlideMode](#getahslidemode)  
  
- [CDockablePane::GetLastPercentInPaneContainer](#getlastpercentinpanecontainer)  
  
- [CDockablePane::IsAutohideAllEnabled](#isautohideallenabled)  
  
##  <a name="create"></a>CDockablePane::Create  
 创建 Windows 控件，并将其附加到[CDockablePane](../../mfc/reference/cdockablepane-class.md)对象。  
  
```  
virtual BOOL Create(
    LPCTSTR lpszCaption,  
    CWnd* pParentWnd,  
    const RECT& rect,  
    BOOL bHasGripper,  
    UINT nID,  
    DWORD dwStyle,  
    DWORD dwTabbedStyle = AFX_CBRS_REGULAR_TABS,  
    DWORD dwControlBarStyle = AFX_DEFAULT_DOCKING_PANE_STYLE,  
    CCreateContext* pContext = NULL);

 
virtual BOOL Create(
    LPCTSTR lpszWindowName,  
    CWnd* pParentWnd,  
    CSize sizeDefault,  
    BOOL bHasGripper,  
    UINT nID,  
    DWORD dwStyle = WS_CHILD|WS_VISIBLE|CBRS_TOP|CBRS_HIDE_INPLACE,  
    DWORD dwTabbedStyle = AFX_CBRS_REGULAR_TABS,  
    DWORD dwControlBarStyle = AFX_DEFAULT_DOCKING_PANE_STYLE);
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszCaption`  
 指定的窗口名称。  
  
 [in][out]`pParentWnd`  
 指定的父窗口。  
  
 [in] `rect`  
 指定的大小和窗口的位置中的工作区坐标`pParentWnd`。  
  
 [in] `bHasGripper`  
 `TRUE`若要创建窗格中用标题;否则为`FALSE`。  
  
 [in] `nID`  
 指定的子窗口的 ID。 此值必须是唯一的如果您想要保存此的停靠窗格的插接状态。  
  
 [in] `dwStyle`  
 指定的窗口样式特性。  
  
 [in] `dwTabbedStyle`  
 指定用户在此窗格的标题上拖动窗格时，将创建一个选项卡式窗口的选项卡式的样式。  
  
 [in] `dwControlBarStyle`  
 指定其他样式属性。  
  
 [in][out]`pContext`  
 指定窗口的创建上下文。  
  
 [in] `lpszWindowName`  
 指定的窗口名称。  
  
 [in] `sizeDefault`  
 指定窗口的大小。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功创建了可停靠窗格;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 创建 Windows 窗格，并将其附加到`CDockablePane`对象。  
  
 如果`dwStyle`窗口样式有`CBRS_FLOAT_MULTI`标志，与袖珍框架窗口中的其他窗格可以浮动袖珍框架窗口。 默认情况下，停靠窗格可以只浮动单独。  
  
 如果`dwTabbedStyle`参数具有`AFX_CBRS_OUTLOOK_TABS`标志已指定，在另一个窗格附加到此窗格中使用时，窗格中创建 Outlook 样式的选项卡式窗格[CDockablePane::AttachToTabWnd](#attachtotabwnd)方法。 默认情况下，可停靠窗格创建类型的常规选项卡式的窗格[CTabbedPane](../../mfc/reference/ctabbedpane-class.md)。  
  
##  <a name="createdefaultpanedivider"></a>CDockablePane::CreateDefaultPaneDivider  
 创建到框架窗口停靠窗格中的默认分隔符。  
  
```  
static CPaneDivider* __stdcall CreateDefaultPaneDivider(
    DWORD dwAlignment,  
    CWnd* pParent,  
    CRuntimeClass* pSliderRTC = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwAlignment`  
 指定向其停靠窗格中的主框架的面。 如果`dwAlignment`包含`CBRS_ALIGN_LEFT`或`CBRS_ALIGN_RIGHT`标志，此方法创建垂直 ( `CPaneDivider::SS_VERT`) 分隔线; 否则，此方法创建水平 ( `CPaneDivider::SS_HORZ`) 分隔线。  
  
 [in] `pParent`  
 指向与父框架指针。  
  
 [in] `pSliderRTC`  
 未使用。  
  
### <a name="return-value"></a>返回值  
 此方法返回一个指向新创建的分隔线，或`NULL`如果分隔符创建操作失败。  
  
### <a name="remarks"></a>备注  
 `dwAlignment`可以是下列值之一︰  
  
|值|说明|  
|-----------|-----------------|  
|`CBRS_ALIGN_TOP`|框架窗口的工作区的顶部停靠窗格。|  
|`CBRS_ALIGN_BOTTOM`|框架窗口的工作区底部停靠窗格。|  
|`CBRS_ALIGN_LEFT`|框架窗口的工作区的左侧停靠窗格。|  
|`CBRS_ALIGN_RIGHT`|在框架窗口的工作区的右侧停靠窗格。|  
  
##  <a name="createex"></a>CDockablePane::CreateEx  
 创建 Windows 控件，并将其附加到[CDockablePane](../../mfc/reference/cdockablepane-class.md)对象。  
  
```  
virtual BOOL CreateEx(
    DWORD dwStyleEx,  
    LPCTSTR lpszCaption,  
    CWnd* pParentWnd,  
    const RECT& rect,  
    BOOL bHasGripper,  
    UINT nID,  
    DWORD dwStyle,  
    DWORD dwTabbedStyle = AFX_CBRS_REGULAR_TABS,  
    DWORD dwControlBarStyle = AFX_DEFAULT_DOCKING_PANE_STYLE,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwStyleEx`  
 指定新的窗口中的扩展的样式特性。  
  
 [in] `lpszCaption`  
 指定的窗口名称。  
  
 [in][out]`pParentWnd`  
 指定的父窗口。  
  
 [in] `rect`  
 指定的大小和窗口的位置中的工作区坐标`pParentWnd`。  
  
 [in] `bHasGripper`  
 `TRUE`若要创建窗格中用标题;否则为`FALSE`。  
  
 [in] `nID`  
 指定的子窗口的 ID。 此值必须是唯一的如果您想要保存此的停靠窗格的停靠状态。  
  
 [in] `dwStyle`  
 指定的窗口样式特性。  
  
 [in] `dwTabbedStyle`  
 指定用户在此窗格的标题上拖动窗格时，将创建一个选项卡式窗口的选项卡式的样式。  
  
 [in] `dwControlBarStyle`  
 指定其他样式属性。  
  
 [in][out]`pContext`  
 指定窗口的创建上下文。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功创建了可停靠窗格;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 创建 Windows 窗格，并将其附加到`CDockablePane`对象。  
  
 如果`dwStyle`窗口样式有`CBRS_FLOAT_MULTI`标志，与袖珍框架窗口中的其他窗格可以浮动袖珍框架窗口。 默认情况下，停靠窗格可以只浮动单独。  
  
 如果`dwTabbedStyle`参数具有`AFX_CBRS_OUTLOOK_TABS`标志已指定，在另一个窗格附加到此窗格中使用时，窗格中创建 Outlook 样式的选项卡式窗格[CDockablePane::AttachToTabWnd](#attachtotabwnd)方法。 默认情况下，可停靠窗格创建类型的常规选项卡式的窗格[CTabbedPane](../../mfc/reference/ctabbedpane-class.md)。  
  
##  <a name="createtabbedpane"></a>CDockablePane::CreateTabbedPane  
 从当前窗格中创建一个选项卡式的窗格。  
  
```  
virtual CTabbedPane* CreateTabbedPane();
```  
  
### <a name="return-value"></a>返回值  
 新选项卡式窗格中，或`NULL`如果创建操作失败。  
  
### <a name="remarks"></a>备注  
 在创建可替换此窗格中的选项卡式的窗格时，框架将调用此方法。 有关详细信息，请参阅[CDockablePane::AttachToTabWnd](#attachtotabwnd)。  
  
 重写此方法在派生类以自定义如何选项卡式的窗格中，将创建和初始化。  
  
 根据存储在运行时类信息创建选项卡式的窗格`m_pTabbedControlBarRTC`成员，请通过初始化[CDockablePane::CreateEx](#createex)方法。  
  
##  <a name="dockpanecontainer"></a>CDockablePane::DockPaneContainer  
 停靠到窗格中的容器。  
  
```  
virtual BOOL DockPaneContainer(
    CPaneContainerManager& barContainerManager,  
    DWORD dwAlignment,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>参数  
 [in] `barContainerManager`  
 对要停靠的容器的容器管理器的引用。  
  
 [in] `dwAlignment`  
 `DWORD`它指定到的停靠容器窗格一侧。  
  
 [in] `dockMethod`  
 未使用。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果容器已成功停靠窗格;，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 `dwAlignment`可以是下列值之一︰  
  
|值|描述|  
|-----------|-----------------|  
|`CBRS_ALIGN_TOP`|顶部窗格的停靠容器。|  
|`CBRS_ALIGN_BOTTOM`|底部窗格的停靠容器。|  
|`CBRS_ALIGN_LEFT`|正在左侧窗格的停靠容器。|  
|`CBRS_ALIGN_RIGHT`|正在向右窗格的停靠容器。|  
  
##  <a name="dockpanestandard"></a>CDockablePane::DockPaneStandard  
 通过使用大纲 （标准） 停靠停靠窗格。  
  
```  
virtual CPane* DockPaneStandard(BOOL& bWasDocked);
```  
  
### <a name="parameters"></a>参数  
 [in] `bWasDocked`  
 该方法返回时，此值包含`TRUE`成功停靠; 否则为窗格中时，它包含`FALSE`。  
  
### <a name="return-value"></a>返回值  
 如果窗格中的停靠选项卡式窗口中，或者由于停靠创建选项卡式的窗口，此方法将返回到选项卡式窗口的指针。 如果窗格中以其他方式已成功停靠，则此方法返回`this`指针。 如果停靠失败，则此方法返回`NULL`。  
  
##  <a name="docktorecentpos"></a>CDockablePane::DockToRecentPos  
 窗格停靠到其存储的停靠位置。  
  
```  
BOOL CDockablePane::DockToRecentPos();
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功停靠窗格中;，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 可停靠窗格存储中的最新停靠信息[CRecentDockSiteInfo](../../mfc/reference/crecentdocksiteinfo-class.md)对象。  
  
##  <a name="docktowindow"></a>CDockablePane::DockToWindow  
 一个停靠窗格停靠到另一停靠窗格。  
  
```  
virtual BOOL DockToWindow(
    CDockablePane* pTargetWindow,  
    DWORD dwAlignment,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in][out]`pTargetWindow`  
 指定可停靠的窗格中，若要将停靠此窗格。  
  
 [in] `dwAlignment`  
 指定窗格中的停靠对齐方式。 可能是 CBRS_ALIGN_LEFT、 CBRS_ALIGN_TOP、 CBRS_ALIGN_RIGHT、 CBRS_ALIGN_BOTTOM 或 CBRS_ALIGN_ANY 之一。 （在 afxres.h 中定义）。  
  
 [in] `lpRect`  
 指定窗格中的停靠矩形。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果已成功，则停靠窗格，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用此方法可将一个窗格停靠到另一个窗格中，使用指定的对齐方式`dwAlignment`。  
  
##  <a name="drawcaption"></a>CDockablePane::DrawCaption  
 绘制标题的停靠窗格 （也称为控制手柄）。  
  
```  
virtual void DrawCaption(
    CDC* pDC,  
    CRect rectCaption);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 表示用于绘图的设备上下文。  
  
 [in] `rectCaption`  
 指定该窗格的标题的边框。  
  
### <a name="remarks"></a>备注  
 框架调用此方法以绘制可停靠窗格的标题。  
  
 重写此方法在派生类可以自定义标题的外观。  
  
##  <a name="enableautohideall"></a>CDockablePane::EnableAutohideAll  
 启用或禁用自动隐藏模式下，此窗格和容器中的其他窗格。  
  
```  
void EnableAutohideAll(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE`若要启用自动隐藏可停靠窗格; 的所有功能否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 当用户承载`Ctrl`键并单击 pin 按钮以切换到自动隐藏模式下，在同一个容器中的所有其他窗格的一个窗格还会切换到自动隐藏模式。  
  
 调用此方法与`bEnable`设置为`FALSE`若要为特定的窗格中禁用此功能。  
  
##  <a name="enablegripper"></a>CDockablePane::EnableGripper  
 显示或隐藏的标题 （也称为控制手柄）。  
  
```  
virtual void EnableGripper(BOOL bEnable);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE`若要启用标题;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 当框架创建可停靠窗格时，它们没有**WS_STYLE**即使指定的窗口样式。 这意味着该窗格的标题是控制由框架的非工作区，但与标准的窗口标题不同，此区域。  
  
 可以显示或隐藏在任何时候的标题。 向选项卡式窗口或袖珍框架窗口中浮动窗格中，添加一个窗格作为选项卡时，框架将隐藏标题。  
  
##  <a name="getahrestoredrect"></a>CDockablePane::GetAHRestoredRect  
 指定在自动隐藏模式下窗格中的位置。  
  
```  
CRect GetAHRestoredRect() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个`CRect`对象，其中包含窗格中的位置，在自动隐藏模式下时。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getahslidemode"></a>CDockablePane::GetAHSlideMode  
 检索窗格中的自动隐藏幻灯片模式。  
  
```  
virtual UINT GetAHSlideMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个`UINT`，它指定窗格中的自动隐藏幻灯片模式。 返回值可以是`AFX_AHSM_MOVE`或`AFX_AHSM_STRETCH`，但实现仅使用`AFX_AHSM_MOVE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="getcaptionheight"></a>CDockablePane::GetCaptionHeight  
 返回的高度，以像素为单位的当前标题。  
  
```  
virtual int GetCaptionHeight() const;  
```  
  
### <a name="return-value"></a>返回值  
 以像素为单位的标题的高度。  
  
### <a name="remarks"></a>备注  
 标题高度为 0; 如果标题隐藏由[CDockablePane::EnableGripper](#enablegripper)方法，或如果窗格没有标题。  
  
##  <a name="getdefaultpanedivider"></a>CDockablePane::GetDefaultPaneDivider  
 返回窗格中的容器的默认窗格分隔符。  
  
```  
CPaneDivider* GetDefaultPaneDivider() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个有效[CPaneDivider](../../mfc/reference/cpanedivider-class.md)对象可停靠窗格停靠到主框架窗口中，如果或`NULL`如果未停靠可停靠窗格或起来具有浮动。  
  
### <a name="remarks"></a>备注  
 有关详细信息窗格中的分隔线，请参阅[CPaneDivider 类](../../mfc/reference/cpanedivider-class.md)。  
  
##  <a name="getdockingstatus"></a>CDockablePane::GetDockingStatus  
 确定一个窗格停靠的能力根据提供的指针的位置。  
  
```  
virtual AFX_CS_STATUS GetDockingStatus(
    CPoint pt,  
    int nSensitivity);
```  
  
### <a name="parameters"></a>参数  
 [in] `pt`  
 以屏幕坐标表示的指针的位置。  
  
 [in] `nSensitivity`  
 距离，以像素为单位，从矩形的边缘指针必须以启用停靠。  
  
### <a name="return-value"></a>返回值  
 下面的状态值之一︰  
  
|`AFX_CS_STATUS` 值|含义|  
|---------------------------|-------------|  
|`CS_NOTHING`|指针不在停靠站点中。 框架将窗格未停靠。|  
|`CS_DOCK_IMMEDIATELY`|指针是否位于停靠站点通过在即时模式 (窗格中使用`DT_IMMEDIATE`停靠模式下)。 框架立即停靠窗格。|  
|`CS_DELAY_DOCK`|指针位于停靠站点是另一个的停靠窗格或边缘的主框架。 框架将窗格停靠在延迟后。 请参阅有关这种延迟的详细信息备注部分。|  
|`CS_DELAY_DOCK_TO_TAB`|鼠标指针位于通过导致窗格停靠在选项卡式窗口停靠站点。 当鼠标指针位于，通过另一个的停靠窗格的标题或选项卡式窗格中的选项卡区域时，将发生这种情况。|  
  
### <a name="remarks"></a>备注  
 框架调用此方法以处理停靠浮动窗格。  
  
 浮动工具栏或停靠窗格，使用`DT_IMMEDIATE`停靠模式下，框架会延迟停靠命令，以使用户能够将窗口移动与父框架的工作区外停靠发生之前。 以毫秒为单位的延迟时长，并由控制[CDockingManager::m_nTimeOutBeforeToolBarDock](../../mfc/reference/cdockingmanager-class.md#m_ntimeoutbeforetoolbardock)数据成员... 默认值为[CDockingManager::m_nTimeOutBeforeToolBarDock](../../mfc/reference/cdockingmanager-class.md#m_ntimeoutbeforetoolbardock)为 200。 此行为会模拟停靠行为的[!INCLUDE[ofprword](../../mfc/reference/includes/ofprword_md.md)]2007年。  
  
 被延迟停靠状态的 (`CS_DELAY_DOCK`和`CS_DELAY_DOCK_TO_TAB`)，该框架不会执行停靠直到用户释放鼠标按钮。 如果一个窗格使用`DT_STANDARD`停靠模式下，框架在投影的停靠位置显示一个矩形。 如果一个窗格使用`DT_SMART`停靠模式下，框架显示智能停靠标记和半透明矩形，从而在投影的停靠位置。 若要指定您的窗格的停靠模式，请调用[CBasePane::SetDockingMode](../../mfc/reference/cbasepane-class.md#setdockingmode)方法。 有关智能停靠的详细信息，请参阅[CDockingManager::GetSmartDockingParams](../../mfc/reference/cdockingmanager-class.md#getsmartdockingparams)。  
  
##  <a name="getdragsensitivity"></a>CDockablePane::GetDragSensitivity  
 返回停靠窗格中拖动的敏感性。  
  
```  
static const CSize& GetDragSensitivity();
```  
  
### <a name="return-value"></a>返回值  
 一个[CSize](../../atl-mfc-shared/reference/csize-class.md)对象，其中包含的宽度和高度，以像素为单位，以拖动点为中心的矩形。 直到鼠标指针移动此矩形外，才会开始拖动操作。  
  
##  <a name="getlastpercentinpanecontainer"></a>CDockablePane::GetLastPercentInPaneContainer  
 检索一个窗格，在其容器中占用的空间百分比 ( [CPaneContainer 类](../../mfc/reference/cpanecontainer-class.md))。  
  
```  
int GetLastPercentInPaneContainer() const;  
```  
  
### <a name="return-value"></a>返回值  
 `int`该值指定在其容器中的窗格中所占的空间的百分比。  
  
### <a name="remarks"></a>备注  
 当容器调整其布局时，使用此方法。  
  
##  <a name="gettabarea"></a>CDockablePane::GetTabArea  
 检索窗格中的选项卡区域。  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `rectTabAreaTop`  
 `GetTabArea`如果选项卡位于顶部的窗格中，请使用选项卡区域填充此变量。 如果选项卡位于底部的窗格中，为空矩形填充此变量。  
  
 [in] `rectTabAreaBottom`  
 `GetTabArea`如果选项卡位于底部的窗格中，请使用选项卡区域填充此变量。 如果选项卡位于顶部的窗格中，为空矩形填充此变量。  
  
### <a name="remarks"></a>备注  
 仅在从派生类中使用此方法`CDockablePane`和具有选项卡。 有关详细信息，请参阅[CTabbedPane::GetTabArea](../../mfc/reference/ctabbedpane-class.md#gettabarea)和[CMFCOutlookBar::GetTabArea](../../mfc/reference/cmfcoutlookbar-class.md#gettabarea)。  
  
##  <a name="gettabbedpanertc"></a>CDockablePane::GetTabbedPaneRTC  
 返回有关时另一个窗格停靠到当前窗格中，将创建一个选项卡式窗口的运行时类信息。  
  
```  
CRuntimeClass* GetTabbedPaneRTC() const;  
```  
  
### <a name="return-value"></a>返回值  
 可停靠窗格中运行时类信息。  
  
### <a name="remarks"></a>备注  
 调用此方法以检索运行时类信息以动态创建的选项卡式窗格。 当用户将一个窗格拖动到另一个窗格的标题，或者如果调用都会出现此[CDockablePane::AttachToTabWnd](#attachtotabwnd)方法以编程方式创建选项卡式窗格中，从两个可停靠窗格。  
  
 可以通过调用设置运行时类信息[CDockablePane::SetTabbedPaneRTC](#settabbedpanertc)方法。  
  
##  <a name="hasautohidemode"></a>CDockablePane::HasAutoHideMode  
 指定是否可以为自动隐藏模式切换停靠窗格。  
  
```  
virtual BOOL HasAutoHideMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果可停靠窗格中可以切换到自动隐藏模式;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生类来禁用特定的可停靠窗格中的自动隐藏模式中。  
  
##  <a name="hittest"></a>CDockablePane::HitTest  
 在用户单击鼠标的其中一个窗格中指定的位置。  
  
```  
virtual int HitTest(
    CPoint point,  
    BOOL bDetectCaption = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
 指定要测试的点。  
  
 [in] `bDetectCaption`  
 `TRUE`如果`HTCAPTION`应将返回该点是否在上窗格的标题; 否则为`FALSE`。  
  
### <a name="return-value"></a>返回值  
 以下值之一：  
  
- `HTNOWHERE`如果`point`不在可停靠窗格中。  
  
- `HTCLIENT`如果`point`是可停靠窗格中的工作区中。  
  
- `HTCAPTION`如果`point`可停靠窗格的标题区域中。  
  
- `AFX_HTCLOSE`如果`point`位于关闭按钮。  
  
- `HTMAXBUTTON`如果`point`位于 pin 按钮。  
  
##  <a name="isautohideallenabled"></a>CDockablePane::IsAutohideAllEnabled  
 指示是否可以将停靠窗格中的容器中的所有其他窗格切换到自动隐藏模式。  
  
```  
virtual BOOL IsAutohideAllEnabled() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果可停靠窗格中，并在容器中，所有其他窗格可以切换到自动隐藏模式;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 用户通过单击停靠 pin 按钮时保持启用自动隐藏模式**Ctrl**密钥  
  
 若要启用或禁用此行为，请调用[CDockablePane::EnableAutohideAll](#enableautohideall)方法。  
  
##  <a name="isautohidemode"></a>CDockablePane::IsAutoHideMode  
 确定是否在自动隐藏模式下一个窗格。  
  
```  
virtual BOOL IsAutoHideMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果可停靠窗格中的自动隐藏模式;否则为`FALSE`。  
  
##  <a name="isdocked"></a>CDockablePane::IsDocked  
 确定是否停靠当前窗格。  
  
```  
virtual BOOL IsDocked() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果可停靠窗格中不属于袖珍框架窗口，或者在另一个窗格与袖珍框架窗口中浮动。 `FALSE`如果窗格中是袖珍框架窗口的子级，并且不有属于袖珍框架窗口的任何其他窗格。  
  
### <a name="remarks"></a>备注  
 若要确定是否将窗格停靠到主框架窗口，请调用[CDockablePane::GetDefaultPaneDivider](#getdefaultpanedivider)。 如果该方法返回一个非 NULL 指针，则会将窗格停靠在主框架窗口。  
  
##  <a name="ishideinautohidemode"></a>CDockablePane::IsHideInAutoHideMode  
 确定的行为的窗格，只是在自动隐藏模式下，如果它正在显示 （或隐藏） 通过调用[CDockablePane::ShowPane](#showpane)。  
  
```  
virtual BOOL IsHideInAutoHideMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果应在自动隐藏模式下; 隐藏可停靠窗格，否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 在自动隐藏模式下可停靠窗格时，其行为以不同方式当您调用`ShowPane`隐藏或显示窗格。 此行为由静态成员控制[CDockablePane::m_bHideInAutoHideMode](#m_bhideinautohidemode)。 如果此成员是`TRUE`，隐藏或显示在调用时可停靠窗格及其相关的自动隐藏工具栏或 autohide 按钮`ShowPane`。 否则为可停靠窗格中激活或停用，并且其相关的自动隐藏工具栏或自动隐藏按钮始终是可见的。  
  
 重写此方法在派生类来更改各个窗格的默认行为。  
  
 `m_bHideInAutoHideMode` 的默认值为 `FALSE`。  
  
##  <a name="isinfloatingmultipaneframewnd"></a>CDockablePane::IsInFloatingMultiPaneFrameWnd  
 指定是否在多窗格框架窗口中为窗格中 ( [CMultiPaneFrameWnd 类](../../mfc/reference/cmultipaneframewnd-class.md))。  
  
```  
virtual BOOL IsInFloatingMultiPaneFrameWnd() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果窗格中处于多窗格框架窗口。否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="isresizable"></a>CDockablePane::IsResizable  
 指定是否可以窗格中的大小。  
  
```  
virtual BOOL IsResizable() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果在窗格中，可调整大小;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 默认情况下，可停靠窗格都是可调整大小。 若要防止调整大小，重写此方法在派生类中的，并返回`FALSE`。 请注意，`FALSE`值会导致故障`ASSERT`中[CPane::DockPane](../../mfc/reference/cpane-class.md#dockpane)。 使用[CDockingManager::AddPane](../../mfc/reference/cdockingmanager-class.md#addpane)改为停靠在父范围内的一个窗格。  
  
 无法调整大小的窗格选项既不浮动，也不进入自动隐藏模式，将始终位于与父框架的外边缘。  
  
##  <a name="istablocationbottom"></a>CDockablePane::IsTabLocationBottom  
 指定选项卡是否位于顶部或底部的窗格。  
  
```  
virtual BOOL IsTabLocationBottom() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果选项卡位于底部的窗格中;`FALSE`如果选项卡位于顶部的窗格。  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[CTabbedPane::IsTabLocationBottom](../../mfc/reference/ctabbedpane-class.md#istablocationbottom)。  
  
##  <a name="istracked"></a>CDockablePane::IsTracked  
 指定是否由用户移动一个窗格。  
  
```  
BOOL IsTracked() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果正在移动窗格中;否则为`FALSE`。  
  
##  <a name="isvisible"></a>CDockablePane::IsVisible  
 确定当前窗格是否可见。  
  
```  
virtual BOOL IsVisible() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果可停靠窗格中可见;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用此方法以确定可停靠窗格是否可见。 您可以使用此方法，而不是调用[CWnd::IsWindowVisible](../../mfc/reference/cwnd-class.md#iswindowvisible)或测试对于`WS_VISIBLE`样式。 返回的可见性状态取决于是否启用或禁用自动隐藏模式和的值[CDockablePane::IsHideInAutoHideMode](#ishideinautohidemode)属性。  
  
 如果可停靠窗格中的自动隐藏模式和`IsHideInAutoHideMode`返回`FALSE`可见性状态始终是`FALSE`。  
  
 如果可停靠窗格中的自动隐藏模式和`IsHideInAutoHideMode`返回`TRUE`的可见性状态取决于相关的自动隐藏工具栏的可见性状态。  
  
 如果可停靠窗格中不是在自动隐藏模式下，来确定的可见性状态[CBasePane::IsVisible](../../mfc/reference/cbasepane-class.md#isvisible)方法。  
  
##  <a name="m_bdisableanimation"></a>CDockablePane::m_bDisableAnimation  
 指定是否禁用了自动隐藏的可停靠窗格中的动画效果。  
  
```  
AFX_IMPORT_DATA static BOOL m_bDisableAnimation;  
```  
  
##  <a name="m_bhideinautohidemode"></a>CDockablePane::m_bHideInAutoHideMode  
 当窗格中处于自动隐藏模式时，请确定窗格中的行为。  
  
```  
AFX_IMPORT_DATA static BOOL m_bHideInAutoHideMode;  
```  
  
### <a name="remarks"></a>备注  
 此值会影响应用程序中的所有停靠窗格。  
  
 如果将此成员设置为`TRUE`，隐藏或显示与他们相关的自动隐藏工具栏和按钮，在调用时可停靠窗格[CDockablePane::ShowPane](#showpane)。  
  
 如果将此成员设置为`FALSE`，可停靠窗格是激活或停用在调用时[CDockablePane::ShowPane](#showpane)。  
  
##  <a name="m_nslidesteps"></a>CDockablePane::m_nSlideSteps  
 在自动隐藏模式下时，请指定窗格中的动画速度。  
  
```  
AFX_IMPORT_DATA static int m_nSlideSteps;  
```  
  
### <a name="remarks"></a>备注  
 要更快的动画效果，请减小此值。 要较慢的动画效果，请增大此值。  
  
##  <a name="onafterchangeparent"></a>CDockablePane::OnAfterChangeParent  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndOldParent`  
  
### <a name="remarks"></a>备注  
  
##  <a name="onafterdockfromminiframe"></a>CDockablePane::OnAfterDockFromMiniFrame  
 在框架窗口停靠浮动停靠栏时由框架调用。  
  
```  
virtual void OnAfterDockFromMiniFrame();
```  
  
### <a name="remarks"></a>备注  
 默认情况下，此方法没有任何效果。  
  
##  <a name="onbeforechangeparent"></a>CDockablePane::OnBeforeChangeParent  
 更改窗格中的父之前，框架将调用此方法。  
  
```  
virtual void OnBeforeChangeParent(
    CWnd* pWndNewParent,  
    BOOL bDelay = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndNewParent`  
 指向新的父窗口的指针。  
  
 [in] `bDelay`  
 `BOOL`指定是否要延迟重新计算停靠布局，如果在窗格中，未停靠状态。 有关详细信息，请参阅[CDockablePane::UndockPane](#undockpane)。  
  
### <a name="remarks"></a>备注  
 如果新的父级不允许停靠窗格即停靠，则此方法中取消停靠窗格。  
  
 如果要转换为选项卡式文档窗格中，此方法将存储其最近的停靠位置。 框架将使用最新的停靠位置转换回停靠状态时还原窗格中的位置。  
  
##  <a name="onbeforefloat"></a>CDockablePane::OnBeforeFloat  
 框架将调用前一个窗格，此方法转换为浮点状态。  
  
```  
virtual BOOL OnBeforeFloat(
    CRect& rectFloat,  
    AFX_DOCK_METHOD dockMethod);
```  
  
### <a name="parameters"></a>参数  
 [in] `rectFloat`  
 当处于浮动状态时指定的位置和大小窗格。  
  
 [in] `dockMethod`  
 指定的扩展方法。 请参阅[CPane::DockPane](../../mfc/reference/cpane-class.md#dockpane)有关的可能值列表。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果可以浮动窗格中;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 当一个窗格处于有关为浮点数，由框架调用此方法。 如果您想要执行任何处理之前浮动窗格中，可以重写此方法在派生类中。  
  
##  <a name="onpressbuttons"></a>CDockablePane::OnPressButtons  
 当用户按下标题按钮以外调用`AFX_HTCLOSE`和`AFX_HTMAXBUTTON`按钮。  
  
```  
virtual void OnPressButtons(UINT nHit);
```  
  
### <a name="parameters"></a>参数  
 [in] `nHit`  
 未使用此参数。  
  
### <a name="remarks"></a>备注  
 如果将自定义按钮添加到可停靠窗格的标题中，重写此方法以便在用户按下按钮时接收通知。  
  
##  <a name="onslide"></a>CDockablePane::OnSlide  
 由框架进行动画处理窗格中，在自动隐藏模式下时调用。  
  
```  
virtual void OnSlide(BOOL bSlideOut);
```  
  
### <a name="parameters"></a>参数  
 [in] `bSlideOut`  
 `TRUE`若要显示窗格;`FALSE`要隐藏窗格。  
  
### <a name="remarks"></a>备注  
 重写此方法在派生类来实现自定义自动隐藏一些特殊效果。  
  
##  <a name="removefromdefaultpanedividier"></a>CDockablePane::RemoveFromDefaultPaneDividier  
 当一个窗格正在取消停靠时，框架将调用此方法。  
  
```  
void RemoveFromDefaultPaneDividier();
```  
  
### <a name="remarks"></a>备注  
 此方法将默认窗格分隔符设置为`NULL`并从其容器中删除窗格。  
  
##  <a name="replacepane"></a>CDockablePane::ReplacePane  
 替换指定的窗格为窗格。  
  
```  
BOOL ReplacePane(
    CDockablePane* pBarToReplaceWith,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bRegisterWithFrame = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pBarToReplaceWith`  
 指向可停靠的窗格中的指针。  
  
 [in] `dockMethod`  
 未使用。  
  
 [in] `bRegisterWithFrame`  
 如果`TRUE`，新窗格中注册的父级的旧窗格中的扩展管理器。 新窗格中将旧窗格中都是由扩展管理器窗格的列表中的索引处插入。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则该替换是否则为`FALSE`。  
  
##  <a name="restoredefaultpanedivider"></a>CDockablePane::RestoreDefaultPaneDivider  
 一个窗格反序列化，框架将调用此方法，以还原默认窗格分隔符。  
  
```  
void RestoreDefaultPaneDivider();
```  
  
### <a name="remarks"></a>备注  
 如果它存在，还原的默认窗格分隔符将替换当前的默认值窗格中分隔线。  
  
##  <a name="setautohidemode"></a>CDockablePane::SetAutoHideMode  
 切换可见停靠窗格和自动隐藏模式。  
  
```  
virtual CMFCAutoHideBar* SetAutoHideMode(
    BOOL bMode,  
    DWORD dwAlignment,  
    CMFCAutoHideBar* pCurrAutoHideBar = NULL,  
    BOOL bUseTimer = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bMode`  
 `TRUE`若要启用自动隐藏模式;`FALSE`若要启用正则停靠模式。  
  
 [in] `dwAlignment`  
 指定自动隐藏窗格中，若要创建的对齐方式。  
  
 [in][out]`pCurrAutoHideBar`  
 指向当前自动隐藏工具栏上的指针。 可以是`NULL`。  
  
 [in] `bUseTimer`  
 指定是使用自动隐藏效果，当用户切换窗格中，为自动隐藏模式还是立即隐藏窗格。  
  
### <a name="return-value"></a>返回值  
 切换到自动隐藏模式下，由于已创建的自动隐藏工具栏或`NULL`。  
  
### <a name="remarks"></a>备注  
 当用户单击 pin 按钮以切换到自动隐藏模式或正则停靠模式下的可停靠窗格中，框架将调用此方法。  
  
 调用此方法以编程方式切换到自动隐藏模式的可停靠窗格。 窗格中必须停靠到主框架窗口 ( [CDockablePane::GetDefaultPaneDivider](#getdefaultpanedivider)必须返回到的有效指针[CPaneDivider](../../mfc/reference/cpanedivider-class.md))。  
  
##  <a name="setautohideparents"></a>CDockablePane::SetAutoHideParents  
 设置自动隐藏按钮和窗格中的自动隐藏工具栏。  
  
```  
void SetAutoHideParents(
    CMFCAutoHideBar* pToolBar,  
    CMFCAutoHideButton* pBtn);
```  
  
### <a name="parameters"></a>参数  
 [in] `pToolBar`  
 为自动隐藏工具栏的指针。  
  
 [in] `pBtn`  
 指向一个自动隐藏按钮。  
  
##  <a name="setlastpercentinpanecontainer"></a>CDockablePane::SetLastPercentInPaneContainer  
 设置窗格在其容器中所占的空间的百分比。  
  
```  
void SetLastPercentInPaneContainer(int n);
```  
  
### <a name="parameters"></a>参数  
 [in] `n`  
 `int`该值指定在其容器中的窗格中所占的空间的百分比。  
  
### <a name="remarks"></a>备注  
 框架调整时要使用的新值重新计算布局窗格。  
  
##  <a name="setrestoreddefaultpanedivider"></a>CDockablePane::SetRestoredDefaultPaneDivider  
 还原的默认窗格分隔符设置。  
  
```  
void SetRestoredDefaultPaneDivider(HWND hRestoredSlider);
```  
  
### <a name="parameters"></a>参数  
 [in] `hRestoredSlider`  
 窗格分隔符 （滑块） 句柄。  
  
### <a name="remarks"></a>备注  
 还原的默认窗格分隔符为一个窗格进行反序列化时获得。 有关详细信息，请参阅[CDockablePane::RestoreDefaultPaneDivider](#restoredefaultpanedivider)。  
  
##  <a name="settabbedpanertc"></a>CDockablePane::SetTabbedPaneRTC  
 设置两个窗格停靠在一起时，将创建一个选项卡式窗口的运行时类信息。  
  
```  
void SetTabbedPaneRTC(CRuntimeClass* pRTC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pRTC`  
 选项卡式窗格中运行时类信息。  
  
### <a name="remarks"></a>备注  
 调用此方法以设置运行时类信息以动态创建的选项卡式窗格。 当用户将一个窗格拖动到另一个窗格的标题，或者如果调用都会出现此[CDockablePane::AttachToTabWnd](#attachtotabwnd)方法以编程方式创建选项卡式窗格中，从两个可停靠窗格。  
  
 根据设置的默认运行时类`dwTabbedStyle`参数[CDockablePane::Create](#create)和[CDockablePane::CreateEx](#createex)。 要自定义新的选项卡式的窗格，请从下列类之一派生您的类︰  
  
- [CBaseTabbedPane 类](../../mfc/reference/cbasetabbedpane-class.md)  
  
- [CTabbedPane 类](../../mfc/reference/ctabbedpane-class.md)  
  
- [CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)。  
  
 然后，调用此方法用指针指向其运行时类信息。  
  
##  <a name="showpane"></a>CDockablePane::ShowPane  
 显示或隐藏窗格。  
  
```  
virtual void ShowPane(
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>参数  
 [in] `bShow`  
 `TRUE`若要显示窗格;`FALSE`要隐藏窗格。  
  
 [in] `bDelay`  
 `TRUE`若要延迟调整停靠布局;`FALSE`立即调整停靠布局。  
  
 [in] `bActivate`  
 `TRUE`若要激活窗格时显示出来;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用此方法，而不是[CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow)时显示或隐藏可停靠窗格。  
  
##  <a name="slide"></a>CDockablePane::Slide  
 进行动画处理是在自动隐藏模式下一个窗格。  
  
```  
virtual void Slide(
    BOOL bSlideOut,  
    BOOL bUseTimer = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bSlideOut`  
 `TRUE`若要显示窗格;`FALSE`要隐藏窗格。  
  
 [in] `bUseTimer`  
 `TRUE`若要显示或隐藏的自动隐藏效果; 窗格`FALSE`以显示或隐藏窗格立即。  
  
### <a name="remarks"></a>备注  
 框架将调用此方法进行动画处理是在自动隐藏模式下一个窗格。  
  
 此方法使用`CDockablePane::m_nSlideDefaultTimeOut`值以确定的滑动效果的超时时间。 超时值的默认值为 1。 如果自定义的自动隐藏算法，请修改此成员，才能更改超时值。  
  
##  <a name="toggleautohide"></a>CDockablePane::ToggleAutoHide  
 窗格之间始终可见和自动隐藏模式切换。  
  
```  
virtual void ToggleAutoHide();
```  
  
### <a name="remarks"></a>备注  
 此方法通过调用切换窗格中的自动隐藏模式[CDockablePane::SetAutoHideMode](#setautohidemode)。  
  
##  <a name="undockpane"></a>CDockablePane::UndockPane  
 中取消停靠窗格中，从主框架窗口或袖珍框架窗口容器。  
  
```  
virtual void UndockPane(BOOL bDelay = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bDelay`  
 `TRUE`延迟计算停靠布局;`FALSE`立即重新计算停靠布局。  
  
### <a name="remarks"></a>备注  
 调用此方法来取消停靠窗格从主框架窗口或从多袖珍框架窗口容器 （在单个袖珍框架窗口中，其他窗格浮动的窗格）。  
  
 在执行不会执行任何外部操作之前，必须取消停靠窗格[CDockingManager](../../mfc/reference/cdockingmanager-class.md)。 例如，您必须取消停靠它以编程方式从一个位置移动到另一个窗格。  
  
 它们将被销毁之前，框架会自动将窗格取消停靠。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CPane 类](../../mfc/reference/cpane-class.md)

