---
title: CMFCTabCtrl 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCTabCtrl
- AFXTABCTRL/CMFCTabCtrl
- AFXTABCTRL/CMFCTabCtrl::ActivateMDITab
- AFXTABCTRL/CMFCTabCtrl::AllowDestroyEmptyTabbedPane
- AFXTABCTRL/CMFCTabCtrl::AutoSizeWindow
- AFXTABCTRL/CMFCTabCtrl::CalcRectEdit
- AFXTABCTRL/CMFCTabCtrl::Create
- AFXTABCTRL/CMFCTabCtrl::EnableActiveTabCloseButton
- AFXTABCTRL/CMFCTabCtrl::EnableInPlaceEdit
- AFXTABCTRL/CMFCTabCtrl::EnableTabDocumentsMenu
- AFXTABCTRL/CMFCTabCtrl::EnsureVisible
- AFXTABCTRL/CMFCTabCtrl::GetDocumentIcon
- AFXTABCTRL/CMFCTabCtrl::GetFirstVisibleTabNum
- AFXTABCTRL/CMFCTabCtrl::GetResizeMode
- AFXTABCTRL/CMFCTabCtrl::GetScrollBar
- AFXTABCTRL/CMFCTabCtrl::GetTabArea
- AFXTABCTRL/CMFCTabCtrl::GetTabMaxWidth
- AFXTABCTRL/CMFCTabCtrl::GetTabsHeight
- AFXTABCTRL/CMFCTabCtrl::GetTabsRect
- AFXTABCTRL/CMFCTabCtrl::GetWndArea
- AFXTABCTRL/CMFCTabCtrl::HideActiveWindowHorzScrollBar
- AFXTABCTRL/CMFCTabCtrl::HideInactiveWindow
- AFXTABCTRL/CMFCTabCtrl::HideNoTabs
- AFXTABCTRL/CMFCTabCtrl::HideSingleTab
- AFXTABCTRL/CMFCTabCtrl::IsActiveInMDITabGroup
- AFXTABCTRL/CMFCTabCtrl::IsActiveTabBoldFont
- AFXTABCTRL/CMFCTabCtrl::IsActiveTabCloseButton
- AFXTABCTRL/CMFCTabCtrl::IsDrawFrame
- AFXTABCTRL/CMFCTabCtrl::IsFlatFrame
- AFXTABCTRL/CMFCTabCtrl::IsFlatTab
- AFXTABCTRL/CMFCTabCtrl::IsLeftRightRounded
- AFXTABCTRL/CMFCTabCtrl::IsMDITabGroup
- AFXTABCTRL/CMFCTabCtrl::IsOneNoteStyle
- AFXTABCTRL/CMFCTabCtrl::IsSharedScroll
- AFXTABCTRL/CMFCTabCtrl::IsTabDocumentsMenu
- AFXTABCTRL/CMFCTabCtrl::IsVS2005Style
- AFXTABCTRL/CMFCTabCtrl::ModifyTabStyle
- AFXTABCTRL/CMFCTabCtrl::OnDragEnter
- AFXTABCTRL/CMFCTabCtrl::OnDragOver
- AFXTABCTRL/CMFCTabCtrl::OnShowTabDocumentsMenu
- AFXTABCTRL/CMFCTabCtrl::SetActiveInMDITabGroup
- AFXTABCTRL/CMFCTabCtrl::SetActiveTab
- AFXTABCTRL/CMFCTabCtrl::SetActiveTabBoldFont
- AFXTABCTRL/CMFCTabCtrl::SetDrawFrame
- AFXTABCTRL/CMFCTabCtrl::SetFlatFrame
- AFXTABCTRL/CMFCTabCtrl::SetImageList
- AFXTABCTRL/CMFCTabCtrl::SetResizeMode
- AFXTABCTRL/CMFCTabCtrl::SetTabMaxWidth
- AFXTABCTRL/CMFCTabCtrl::StopResize
- AFXTABCTRL/CMFCTabCtrl::SynchronizeScrollBar
- AFXTABCTRL/CMFCTabCtrl::m_bEnableActivate
dev_langs:
- C++
helpviewer_keywords:
- CMFCTabCtrl [MFC], ActivateMDITab
- CMFCTabCtrl [MFC], AllowDestroyEmptyTabbedPane
- CMFCTabCtrl [MFC], AutoSizeWindow
- CMFCTabCtrl [MFC], CalcRectEdit
- CMFCTabCtrl [MFC], Create
- CMFCTabCtrl [MFC], EnableActiveTabCloseButton
- CMFCTabCtrl [MFC], EnableInPlaceEdit
- CMFCTabCtrl [MFC], EnableTabDocumentsMenu
- CMFCTabCtrl [MFC], EnsureVisible
- CMFCTabCtrl [MFC], GetDocumentIcon
- CMFCTabCtrl [MFC], GetFirstVisibleTabNum
- CMFCTabCtrl [MFC], GetResizeMode
- CMFCTabCtrl [MFC], GetScrollBar
- CMFCTabCtrl [MFC], GetTabArea
- CMFCTabCtrl [MFC], GetTabMaxWidth
- CMFCTabCtrl [MFC], GetTabsHeight
- CMFCTabCtrl [MFC], GetTabsRect
- CMFCTabCtrl [MFC], GetWndArea
- CMFCTabCtrl [MFC], HideActiveWindowHorzScrollBar
- CMFCTabCtrl [MFC], HideInactiveWindow
- CMFCTabCtrl [MFC], HideNoTabs
- CMFCTabCtrl [MFC], HideSingleTab
- CMFCTabCtrl [MFC], IsActiveInMDITabGroup
- CMFCTabCtrl [MFC], IsActiveTabBoldFont
- CMFCTabCtrl [MFC], IsActiveTabCloseButton
- CMFCTabCtrl [MFC], IsDrawFrame
- CMFCTabCtrl [MFC], IsFlatFrame
- CMFCTabCtrl [MFC], IsFlatTab
- CMFCTabCtrl [MFC], IsLeftRightRounded
- CMFCTabCtrl [MFC], IsMDITabGroup
- CMFCTabCtrl [MFC], IsOneNoteStyle
- CMFCTabCtrl [MFC], IsSharedScroll
- CMFCTabCtrl [MFC], IsTabDocumentsMenu
- CMFCTabCtrl [MFC], IsVS2005Style
- CMFCTabCtrl [MFC], ModifyTabStyle
- CMFCTabCtrl [MFC], OnDragEnter
- CMFCTabCtrl [MFC], OnDragOver
- CMFCTabCtrl [MFC], OnShowTabDocumentsMenu
- CMFCTabCtrl [MFC], SetActiveInMDITabGroup
- CMFCTabCtrl [MFC], SetActiveTab
- CMFCTabCtrl [MFC], SetActiveTabBoldFont
- CMFCTabCtrl [MFC], SetDrawFrame
- CMFCTabCtrl [MFC], SetFlatFrame
- CMFCTabCtrl [MFC], SetImageList
- CMFCTabCtrl [MFC], SetResizeMode
- CMFCTabCtrl [MFC], SetTabMaxWidth
- CMFCTabCtrl [MFC], StopResize
- CMFCTabCtrl [MFC], SynchronizeScrollBar
- CMFCTabCtrl [MFC], m_bEnableActivate
ms.assetid: d441385d-2c72-4203-96fa-deae2273da35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ad7a5331a2826df9dd6804e5c6a0f918bfeeb9d2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="cmfctabctrl-class"></a>CMFCTabCtrl Class
`CMFCTabCtrl`类提供的选项卡控件的功能。 选项卡控件在其顶部或底部显示具有平面或三维选项卡的可停靠窗口。 选项卡可以显示文本和图像，并可在处于活动状态时更改颜色。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCTabCtrl : public CMFCBaseTabCtrl  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|`CMFCTabCtrl::CMFCTabCtrl`|默认构造函数。|  
|`CMFCTabCtrl::~CMFCTabCtrl`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCTabCtrl::ActivateMDITab](#activatemditab)|显示当前的选项卡控件指定选项卡，并将焦点设置在该选项卡上。|  
|[CMFCTabCtrl::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)||  
|[CMFCTabCtrl::AutoSizeWindow](#autosizewindow)|指定是否要调整大小的客户端区域的所有选项卡控件时段时的选项卡控件更改的用户界面元素的框架。|  
|[CMFCTabCtrl::CalcRectEdit](#calcrectedit)|压缩指定选项卡区域的大小。 （重写 `CMFCBaseTabCtrl::CalcRectEdit`。）|  
|[CMFCTabCtrl::Create](#create)|创建选项卡控件并将其附加到`CMFCTabCtrl`对象。|  
|`CMFCTabCtrl::CreateObject`|由框架用于创建此类类型的动态实例。|  
|[CMFCTabCtrl::EnableActiveTabCloseButton](#enableactivetabclosebutton)|显示或隐藏关闭按钮 ( **X**) 上的活动选项卡。|  
|[CMFCTabCtrl::EnableInPlaceEdit](#enableinplaceedit)|启用或禁用可编辑的选项卡标签。 (重写[CMFCBaseTabCtrl::EnableInPlaceEdit](../../mfc/reference/cmfcbasetabctrl-class.md#enableinplaceedit)。)|  
|[CMFCTabCtrl::EnableTabDocumentsMenu](#enabletabdocumentsmenu)|将替换两个滚动窗口选项卡包含用于打开一个菜单的选项卡式窗口的按钮的按钮。|  
|[CMFCTabCtrl::EnsureVisible](#ensurevisible)|确保选项卡可见。|  
|[CMFCTabCtrl::GetDocumentIcon](#getdocumenticon)|检索与选项卡式窗口弹出菜单中的选项卡关联的符号。|  
|[CMFCTabCtrl::GetFirstVisibleTabNum](#getfirstvisibletabnum)|检索当前选项卡控件中可见的第一个选项卡的索引。|  
|[CMFCTabCtrl::GetResizeMode](#getresizemode)|检索一个值，指定当前选项卡控件可以调整大小。|  
|[CMFCTabCtrl::GetScrollBar](#getscrollbar)|检索指向与选项卡控件相关联的滚动栏对象的指针。|  
|[CMFCTabCtrl::GetTabArea](#gettabarea)|检索的选项卡标签区域的顶部或底部的选项卡控件的边框。 (重写[CMFCBaseTabCtrl::GetTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#gettabarea)。)|  
|`CMFCTabCtrl::GetTabFromPoint`|检索包含指定的点的选项卡。 (重写[CMFCBaseTabCtrl::GetTabFromPoint](../../mfc/reference/cmfcbasetabctrl-class.md#gettabfrompoint)。)|  
|[CMFCTabCtrl::GetTabMaxWidth](#gettabmaxwidth)|检索一个选项卡的最大宽度。|  
|[CMFCTabCtrl::GetTabsHeight](#gettabsheight)|检索当前选项卡控件的选项卡区域的高度。|  
|[CMFCTabCtrl::GetTabsRect](#gettabsrect)|检索限定当前选项卡控件的选项卡区域的矩形。 (重写[CMFCBaseTabCtrl::GetTabsRect](../../mfc/reference/cmfcbasetabctrl-class.md#gettabsrect)。)|  
|`CMFCTabCtrl::GetThisClass`|由框架用于获取指向的指针[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型关联的对象。|  
|[CMFCTabCtrl::GetWndArea](#getwndarea)|检索当前的选项卡控件的客户端区域的边界。|  
|[CMFCTabCtrl::HideActiveWindowHorzScrollBar](#hideactivewindowhorzscrollbar)|如果任何活动的窗口将隐藏在水平滚动条。|  
|[CMFCTabCtrl::HideInactiveWindow](#hideinactivewindow)|指定是否显示非活动选项卡控件窗口框架。|  
|[CMFCTabCtrl::HideNoTabs](#hidenotabs)|启用或禁用绘制选项卡区域，如果没有可见的选项卡。|  
|[CMFCTabCtrl::HideSingleTab](#hidesingletab)|启用或禁用单个选项卡式的窗口时绘制选项卡。 (重写[CMFCBaseTabCtrl::HideSingleTab](../../mfc/reference/cmfcbasetabctrl-class.md#hidesingletab)。)|  
|[CMFCTabCtrl::IsActiveInMDITabGroup](#isactiveinmditabgroup)|指示选项卡控件的当前选项卡是否在多个文档接口选项卡组活动选项卡。|  
|[CMFCTabCtrl::IsActiveTabBoldFont](#isactivetabboldfont)|指示是否使用加粗字体显示活动选项卡的文本。|  
|[CMFCTabCtrl::IsActiveTabCloseButton](#isactivetabclosebutton)|指示是否关闭按钮 ( **X**) 显示在活动选项卡或选项卡区域的右上角。|  
|[CMFCTabCtrl::IsDrawFrame](#isdrawframe)|指示是否选项卡式的窗口周围绘制一个帧矩形嵌入窗格。|  
|[CMFCTabCtrl::IsFlatFrame](#isflatframe)|指示选项卡区域周围的框架是平面的还是 3D 的。|  
|[CMFCTabCtrl::IsFlatTab](#isflattab)|指示指示包是否为当前选项卡控件中选项卡的外观。|  
|[CMFCTabCtrl::IsLeftRightRounded](#isleftrightrounded)|指示是否舍入的左侧和右侧的当前选项卡控件中的选项卡的外观。|  
|[CMFCTabCtrl::IsMDITabGroup](#ismditabgroup)|指示当前的选项卡控件是否包含在多文档界面窗口的工作区中。|  
|[CMFCTabCtrl::IsOneNoteStyle](#isonenotestyle)|指示是否以 Microsoft onenote 样式显示当前选项卡控件。|  
|`CMFCTabCtrl::IsPtInTabArea`|确定点是否在选项卡区域内。 (重写[CMFCBaseTabCtrl::IsPtInTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#isptintabarea)。)|  
|[CMFCTabCtrl::IsSharedScroll](#issharedscroll)|指示当前的选项卡控件是否具有滚动条可作为一个组滚动其选项卡。|  
|[CMFCTabCtrl::IsTabDocumentsMenu](#istabdocumentsmenu)|指示选项卡控件显示滚动按钮或显示的选项卡式窗口菜单按钮。|  
|[CMFCTabCtrl::IsVS2005Style](#isvs2005style)|指示是否在 Visual Studio.NET 2005年的样式显示选项卡。|  
|[CMFCTabCtrl::ModifyTabStyle](#modifytabstyle)|指定当前选项卡控件中选项卡的外观。|  
|`CMFCTabCtrl::MoveTab`|将选项卡移动到另一个选项卡位置。 (重写[CMFCBaseTabCtrl::MoveTab](../../mfc/reference/cmfcbasetabctrl-class.md#movetab)。)|  
|[CMFCTabCtrl::OnDragEnter](#ondragenter)|当光标首先拖到选项卡控件窗口时，由框架调用。|  
|[CMFCTabCtrl::OnDragOver](#ondragover)|由框架调用在拖动操作期间当鼠标移到放置目标窗口。 (重写[CMFCBaseTabCtrl::OnDragOver](../../mfc/reference/cmfcbasetabctrl-class.md#ondragover)。)|  
|[CMFCTabCtrl::OnShowTabDocumentsMenu](#onshowtabdocumentsmenu)|显示弹出菜单的选项卡式窗口时，等待，直到用户选择一个选项卡，并使已选定选项卡成为活动选项卡。|  
|`CMFCTabCtrl::PreTranslateMessage`|翻译窗口消息之前被发送到[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函数。 (重写[CMFCBaseTabCtrl::PreTranslateMessage](../../mfc/reference/cmfcbasetabctrl-class.md#pretranslatemessage)。)|  
|`CMFCTabCtrl::RecalcLayout`|重新计算选项卡控件的内部布局。 (重写[CMFCBaseTabCtrl::RecalcLayout](../../mfc/reference/cmfcbasetabctrl-class.md#recalclayout)。)|  
|[CMFCTabCtrl::SetActiveInMDITabGroup](#setactiveinmditabgroup)|将选项卡控件的当前选项卡设置为多个文档接口选项卡组中的活动选项卡。|  
|[CMFCTabCtrl::SetActiveTab](#setactivetab)|激活选项卡。(重写[CMFCBaseTabCtrl::SetActiveTab](../../mfc/reference/cmfcbasetabctrl-class.md#setactivetab)。)|  
|[CMFCTabCtrl::SetActiveTabBoldFont](#setactivetabboldfont)|启用或禁用使用活动选项卡上的加粗字体。|  
|[CMFCTabCtrl::SetDrawFrame](#setdrawframe)|启用或禁用 drawinga 框架矩形周围嵌入栏。|  
|[CMFCTabCtrl::SetFlatFrame](#setflatframe)|指定是否在选项卡区域周围绘制以平面或 3D 帧。|  
|[CMFCTabCtrl::SetImageList](#setimagelist)|指定图像列表。 (重写[CMFCBaseTabCtrl::SetImageList](../../mfc/reference/cmfcbasetabctrl-class.md#setimagelist)。)|  
|[CMFCTabCtrl::SetResizeMode](#setresizemode)|指定当前选项卡控件可以调整大小，然后重新显示控件。|  
|[CMFCTabCtrl::SetTabMaxWidth](#settabmaxwidth)|在选项卡式窗口中指定的最大的选项卡宽度。|  
|[CMFCTabCtrl::StopResize](#stopresize)|终止当前选项卡控件的大小调整操作。|  
|`CMFCTabCtrl::SwapTabs`|交换的成对的选项卡。 (重写[CMFCBaseTabCtrl::SwapTabs](../../mfc/reference/cmfcbasetabctrl-class.md#swaptabs)。)|  
|[CMFCTabCtrl::SynchronizeScrollBar](#synchronizescrollbar)|在显示平面选项卡的选项卡控件上绘制水平滚动条。|  
  
### <a name="data-members"></a>数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCTabCtrl::m_bEnableActivate](#m_benableactivate)|防止失去焦点时插入新选项卡并将其启用活动视图。|  
  
## <a name="remarks"></a>备注  
 `CMFCTabCtrl`类支持：  
  
-   选项卡包括三维，平面，和包共享水平滚动条控件样式。  
  
-   选项卡位于顶部或窗口的底部。  
  
-   显示文本、 图像或文本和图像的选项卡。  
  
-   选项卡处于活动状态时更改颜色的选项卡。  
  
-   可调整的选项卡边框大小更改。  
  
-   可拆分的选项卡式的窗口。  
  
 `CMFCTabCtrl`类可以用于一个对话框，但适用于在应用程序使用停靠控件条如[!INCLUDE[ofprexcel](../../mfc/reference/includes/ofprexcel_md.md)]和[!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)]。 有关详细信息，请参阅[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)。  
  
 请按照这些步骤添加可调整大小，停靠在你的应用程序中的选项卡控件：  
  
1.  创建的实例[CTabbedPane 类](../../mfc/reference/ctabbedpane-class.md)。  
  
2.  调用[CDockablePane::Create](../../mfc/reference/cdockablepane-class.md#create)。  
  
3.  使用[cbasetabbedpane:: Addtab](../../mfc/reference/cbasetabbedpane-class.md#addtab)或[cmfcbasetabctrl:: Inserttab](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab)添加新选项卡。  
  
4.  调用[CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking)以便当前停靠选项卡控件可以停靠在主框架窗口。  
  
5.  调用[CFrameWndEx::DockPane](../../mfc/reference/cframewndex-class.md#dockpane)停靠在主框架的选项卡式的窗口。  
  
 有关如何创建作为停靠控件条的选项卡式的窗口的示例，请参阅[CTabbedPane 类](../../mfc/reference/ctabbedpane-class.md)。 若要使用`CMFCTabCtrl`作为非停靠的控件，创建`CMFCTabCtrl`对象，然后调用[CMFCTabCtrl::Create](#create)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)  
  
 [CMFCTabCtrl](../../mfc/reference/cmfctabctrl-class.md)  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法`CMFCTabCtrl`用于配置类`CMFCTabCtrl`对象。 该示例说明如何添加选项卡、 在活动选项卡上显示关闭按钮、 启用可编辑的选项卡标签和显示选项卡式的窗口标签的弹出菜单。 此示例摘自[状态收集样本](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_StateCollection#1](../../mfc/reference/codesnippet/cpp/cmfctabctrl-class_1.h)]  
[!code-cpp[NVC_MFC_StateCollection#3](../../mfc/reference/codesnippet/cpp/cmfctabctrl-class_2.cpp)]  
  
## <a name="requirements"></a>要求  
 **标头：** afxtabctrl.h  
  
##  <a name="activatemditab"></a>  CMFCTabCtrl::ActivateMDITab  
 显示当前的选项卡控件指定选项卡，并将焦点设置在该选项卡上。  
  
```  
void ActivateMDITab(int nTab = -1);
```  
  
### <a name="parameters"></a>参数  
 [in] `nTab`  
 选项卡显示，或者为-1 以指定当前活动选项卡的从零开始索引。  
  
##  <a name="allowdestroyemptytabbedpane"></a>  CMFCTabCtrl::AllowDestroyEmptyTabbedPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL AllowDestroyEmptyTabbedPane() const;  
```  
  
### <a name="return-value"></a>返回值  
 总是为 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="autosizewindow"></a>  CMFCTabCtrl::AutoSizeWindow  
 指定是否要调整大小的客户端区域的所有选项卡控件时段时的选项卡控件更改的用户界面元素的框架。  
  
```  
void AutoSizeWindow(BOOL bAutoSize = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bAutoSize`  
 `TRUE` 自动调整大小选项卡控件窗口中：否则为`FALSE`。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="create"></a>  CMFCTabCtrl::Create  
 创建选项卡控件并将其附加到`CMFCTabCtrl`对象。  
  
```  
BOOL Create(
    Style style,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID,  
    Location location=LOCATION_BOTTOM,  
    BOOL bCloseBtn=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `style`  
 选项卡控件的样式。 有关更多信息，请参见“备注”。  
  
 [in] `rect`  
 限定选项卡控件的矩形。  
  
 [in] `pParentWnd`  
 指向父窗口的指针。 不得为 `NULL`。  
  
 [in] `nID`  
 选项卡控件的 ID。  
  
 [in] `location`  
 选项卡位置。 默认值为 `LOCATION_BOTTOM`。 有关更多信息，请参见“备注”。  
  
 [in] `bCloseBtn`  
 `TRUE` 若要显示的选项卡; 上的关闭按钮否则为`FALSE`。 默认值为 `FALSE`。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 `TRUE`；否则为 `FALSE`。  
  
### <a name="remarks"></a>备注  
 下表描述你可以为指定的值`style`参数。  
  
|样式|描述|  
|-----------|-----------------|  
|STYLE_3D|创建具有三维外观的选项卡控件。|  
|STYLE_FLAT|使用平面的选项卡中创建选项卡控件。|  
|STYLE_FLAT_SHARED_HORZ_SCROLL|创建具有平面选项卡和可以滚动选项卡，如果将被剪裁由父窗口的滚动条的选项卡控件。|  
|STYLE_3D_ONENOTE|创建选项卡控件中的 Microsoft OneNote 样式。|  
|STYLE_3D_VS2005|样式的 Microsoft Visual Studio 2005 创建选项卡控件。|  
|STYLE_3D_ROUNDED|使用样式的 Microsoft Visual Studio 2005 圆角的选项卡中创建选项卡控件。|  
|STYLE_3D_ROUNDED_SCROLL|创建选项卡控件具有圆角的选项卡和 Microsoft Visual Studio 2005 样式的滚动按钮。|  
  
 下表列出了可以为指定的值`location`参数。  
  
|位置|描述|  
|--------------|-----------------|  
|LOCATION_BOTTOM|选项卡位于选项卡控件的底部。|  
|LOCATION_TOP|选项卡位于顶部的选项卡控件。|  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`Create`中的方法`CMFCTabCtrl`类。 此示例摘自[状态收集样本](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_StateCollection#1](../../mfc/reference/codesnippet/cpp/cmfctabctrl-class_1.h)]  
[!code-cpp[NVC_MFC_StateCollection#2](../../mfc/reference/codesnippet/cpp/cmfctabctrl-class_3.cpp)]  
  
##  <a name="calcrectedit"></a>  CMFCTabCtrl::CalcRectEdit  
 压缩指定选项卡区域的大小。  
  
```  
virtual void CalcRectEdit(CRect& rectEdit);
```  
  
### <a name="parameters"></a>参数  
 [in] `rectEdit`  
 指定的选项卡区域的矩形。  
  
### <a name="remarks"></a>备注  
 当您更改选项卡标签时，调用此方法。此方法由一半的当前选项卡高度，压缩的左侧和右侧指定的矩形，压缩的顶部和底部一个单元。  
  
##  <a name="enableactivetabclosebutton"></a>  CMFCTabCtrl::EnableActiveTabCloseButton  
 显示或隐藏关闭按钮 ( **X**) 上的活动选项卡。  
  
```  
void EnableActiveTabCloseButton(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE` 若要在活动选项卡; 上显示关闭按钮`FALSE`右上角的选项卡区域中显示关闭按钮。 默认值为 `TRUE`。  
  
##  <a name="enableinplaceedit"></a>  CMFCTabCtrl::EnableInPlaceEdit  
 启用或禁用可编辑的选项卡标签。  
  
```  
virtual void EnableInPlaceEdit(BOOL bEnable);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE` 若要启用可编辑的选项卡标签;`FALSE`禁用可编辑的选项卡标签。  
  
### <a name="remarks"></a>备注  
  
##  <a name="enabletabdocumentsmenu"></a>  CMFCTabCtrl::EnableTabDocumentsMenu  
 在使用两个按钮来滚动窗口选项卡的用户界面和显示选项卡式窗口弹出菜单的接口之间切换。  
  
```  
void EnableTabDocumentsMenu(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE` 若要显示的选项卡式的窗口标签; 的弹出菜单`FALSE`以显示向前和向后滚动按钮。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
 当用户单击选项卡标签时，框架将显示相应的选项卡式的窗口。 如果选项卡标签才可见，而无需更改其位置打开选项卡式的窗口。 如果用户从弹出菜单中选择文档和相应的选项卡式的窗口已关闭屏幕，选项卡式的窗口将成为第一个选项卡。  
  
##  <a name="ensurevisible"></a>  CMFCTabCtrl::EnsureVisible  
 确保选项卡可见。  
  
```  
virtual BOOL EnsureVisible(int iTab);
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 选项卡的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果成功，则`FALSE`如果`iTab`参数索引无效。  
  
### <a name="remarks"></a>备注  
 使用此方法以保证指定选项卡为可见。 如果需要，将向滚动选项卡控件。  
  
##  <a name="getdocumenticon"></a>  CMFCTabCtrl::GetDocumentIcon  
 检索与选项卡式窗口弹出菜单中的选项卡关联的映像。  
  
```  
static HICON __stdcall GetDocumentIcon(UINT nCmdID);
```  
  
### <a name="parameters"></a>参数  
 [in] `nCmdID`  
 在选项卡式窗口弹出菜单的选项卡的命令 ID。  
  
### <a name="return-value"></a>返回值  
 位图图像的句柄。  
  
##  <a name="getfirstvisibletabnum"></a>  CMFCTabCtrl::GetFirstVisibleTabNum  
 检索当前选项卡控件中可见的第一个选项卡的索引。  
  
```  
virtual int GetFirstVisibleTabNum() const;  
```  
  
### <a name="return-value"></a>返回值  
 选项卡控件中选项卡的从零开始索引。  
  
### <a name="remarks"></a>备注  
 仅当以 Microsoft onenote 样式显示选项卡控件时，请使用此方法。 使用[CMFCTabCtrl::IsOneNoteStyle](#isonenotestyle)方法来确定样式。  
  
##  <a name="getresizemode"></a>  CMFCTabCtrl::GetResizeMode  
 检索一个值，指定当前选项卡控件可以调整大小。  
  
```  
ResizeMode GetResizeMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 之一`CMFCTabCtrl::ResizeMode`指定选项卡控件可以调整大小的枚举值。 有关可能的值的列表，请参阅备注部分的[CMFCTabCtrl::SetResizeMode](#setresizemode)方法。  
  
##  <a name="getscrollbar"></a>  CMFCTabCtrl::GetScrollBar  
 检索指向与选项卡控件相关联的滚动栏对象的指针。  
  
```  
CScrollBar* GetScrollBar();
```  
  
### <a name="return-value"></a>返回值  
 滚动条对象、 指针或`NULL`如果使用不创建选项卡控件`STYLE_FLAT_SHARED_HORZ_SCROLL`样式。  
  
### <a name="remarks"></a>备注  
 此方法用于访问选项卡控件嵌入的滚动条。 仅当选项卡控件具有时创建了一个滚动栏对象`STYLE_FLAT_SHARED_HORZ_SCROLL`样式。  
  
##  <a name="gettabarea"></a>  CMFCTabCtrl::GetTabArea  
 检索的选项卡标签区域的顶部或底部的选项卡控件的边框。  
  
```  
void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `rectTabAreaTop`  
 此方法返回时，本参考包含限定顶部的选项卡标签区域的矩形。 矩形是在工作区坐标。 此引用是没有选项卡标签区域存在顶部的选项卡控件的情况下为空。  
  
 [out] `rectTabAreaBottom`  
 此方法返回时，本参考包含限定底部选项卡标签区域的矩形。 矩形是在工作区坐标。 此引用是没有选项卡标签区域存在底部的选项卡控件的情况下为空。  
  
### <a name="remarks"></a>备注  
 使用此方法来确定的大小和选项卡区域在选项卡式窗口中的位置。  
  
##  <a name="gettabmaxwidth"></a>  CMFCTabCtrl::GetTabMaxWidth  
 检索一个选项卡的最大宽度。  
  
```  
int GetTabMaxWidth() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个选项卡，以像素为单位的最大宽度。 如果返回值为 0，则选项卡宽度没有限制。  
  
### <a name="remarks"></a>备注  
 使用[CMFCTabCtrl::SetTabMaxWidth](#settabmaxwidth)方法以设置最大的选项卡宽度。  
  
##  <a name="gettabsheight"></a>  CMFCTabCtrl::GetTabsHeight  
 检索当前选项卡控件的选项卡区域的高度。  
  
```  
virtual int GetTabsHeight() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果任何选项卡是可见的或为零会显示任何选项卡的选项卡区域的高度。  
  
##  <a name="gettabsrect"></a>  CMFCTabCtrl::GetTabsRect  
 检索限定当前选项卡控件的选项卡区域的矩形。  
  
```  
virtual void GetTabsRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `rect`  
 此方法返回时，`rect`参数包含限定选项卡区域的矩形。  
  
##  <a name="getwndarea"></a>  CMFCTabCtrl::GetWndArea  
 检索当前的选项卡控件的客户端区域的边界。  
  
```  
void GetWndArea(CRect& rect) const;  
```  
  
### <a name="parameters"></a>参数  
 [in, out] `rect`  
 此方法返回时，此参数将包含限定当前选项卡控件的矩形。  
  
### <a name="remarks"></a>备注  
  
##  <a name="hideactivewindowhorzscrollbar"></a>  CMFCTabCtrl::HideActiveWindowHorzScrollBar  
 如果任何活动的窗口中，则隐藏在水平滚动条。  
  
```  
void HideActiveWindowHorzScrollBar();
```  
  
### <a name="remarks"></a>备注  
 使用此方法要阻止选项卡控件闪烁当用户选项卡控件页之间切换。  
  
##  <a name="hideinactivewindow"></a>  CMFCTabCtrl::HideInactiveWindow  
 指定框架是否显示非活动选项卡控件窗口。  
  
```  
void HideInactiveWindow(BOOL bHide = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bHide`  
 `TRUE` 不希望显示非活动窗口;`FALSE`以显示非活动窗口。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="hidenotabs"></a>  CMFCTabCtrl::HideNoTabs  
 启用或禁用绘制选项卡区域中，如果没有可见的选项卡。  
  
```  
void HideNoTabs(BOOL bHide=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bHide`  
 `TRUE` 若要启用绘制选项卡区域;`FALSE`禁止绘图。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="hidesingletab"></a>  CMFCTabCtrl::HideSingleTab  
 启用或禁用选项卡上绘制，如果没有单个选项卡式的窗口。  
  
```  
virtual void HideSingleTab(BOOL bHide=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bHide`  
 `TRUE` 若要不绘制单个选项卡式窗口; 一个选项卡`FALSE`绘制单个选项卡。默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="isactiveinmditabgroup"></a>  CMFCTabCtrl::IsActiveInMDITabGroup  
 指示选项卡控件的当前选项卡是否为多个文档接口选项卡组中的活动选项卡。  
  
```  
BOOL IsActiveInMDITabGroup() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果当前选项卡选项卡控件的 MDI 选项卡组; 中的活动选项卡否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 可以将多个文档窗口组织为任一垂直或水平选项卡组，还可以轻松地随机文档从一个选项卡组排列到另一个。  
  
##  <a name="isactivetabboldfont"></a>  CMFCTabCtrl::IsActiveTabBoldFont  
 指示是否使用加粗字体显示活动选项卡的文本。  
  
```  
BOOL IsActiveTabBoldFont() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果使用粗体字体; 显示活动选项卡否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 使用[CMFCTabCtrl::SetActiveTabBoldFont](#setactivetabboldfont)方法可以更改活动选项卡字体。  
  
##  <a name="isactivetabclosebutton"></a>  CMFCTabCtrl::IsActiveTabCloseButton  
 指示是否关闭按钮 ( **X**) 或选项卡区域的右上角活动选项卡上显示。  
  
```  
virtual BOOL IsActiveTabCloseButton() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果在活动选项卡; 上显示关闭按钮`FALSE`如果上选项卡区域的右上角显示关闭按钮。  
  
### <a name="remarks"></a>备注  
  
##  <a name="isdrawframe"></a>  CMFCTabCtrl::IsDrawFrame  
 指示是否选项卡式的窗口周围绘制一个帧矩形嵌入窗格。  
  
```  
BOOL IsDrawFrame() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果绘制出框架矩形;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 使用[CMFCTabCtrl::SetDrawFrame](#setdrawframe)方法来启用或禁用绘制框架矩形。  
  
##  <a name="isflatframe"></a>  CMFCTabCtrl::IsFlatFrame  
 指示选项卡区域周围的框架是平面的还是 3D 的。  
  
```  
BOOL IsFlatFrame() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果选项卡区域周围的框架是平面;`FALSE`如果帧为三维。  
  
### <a name="remarks"></a>备注  
 使用[CMFCTabCtrl::SetFlatFrame](#setflatframe)方法可以更改如何绘制帧。  
  
##  <a name="isflattab"></a>  CMFCTabCtrl::IsFlatTab  
 指示指示包是否为当前选项卡控件中选项卡的外观。  
  
```  
virtual BOOL IsFlatTab() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果当前的选项卡控件中选项卡的外观保持不变;否则为`FALSE`。  
  
##  <a name="isleftrightrounded"></a>  CMFCTabCtrl::IsLeftRightRounded  
 指示是否舍入的左侧和右侧的当前选项卡控件中的选项卡的外观。  
  
```  
virtual BOOL IsLeftRightRounded() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果每个选项卡的一侧舍入;，否则为`FALSE`。  
  
##  <a name="ismditabgroup"></a>  CMFCTabCtrl::IsMDITabGroup  
 指示当前的选项卡控件是否包含在多文档界面窗口的工作区中。  
  
```  
virtual BOOL IsMDITabGroup() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果当前的选项卡控件在 MDI 客户端区域窗口;否则为`FALSE`。  
  
##  <a name="isonenotestyle"></a>  CMFCTabCtrl::IsOneNoteStyle  
 指示是否以 Microsoft onenote 样式显示当前选项卡控件。  
  
```  
virtual BOOL IsOneNoteStyle() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果以 Microsoft onenote; 样式显示选项卡控件否则为`FALSE`。  
  
##  <a name="issharedscroll"></a>  CMFCTabCtrl::IsSharedScroll  
 指示当前的选项卡控件是否具有滚动条可作为一个组滚动其选项卡。  
  
```  
BOOL IsSharedScroll() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果选项卡控件具有共享的滚动条;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法返回`TRUE`如果`style`参数[CMFCTabCtrl::Create](#create)方法是 STYLE_FLAT_SHARED_HORZ_SCROLL。  
  
##  <a name="istabdocumentsmenu"></a>  CMFCTabCtrl::IsTabDocumentsMenu  
 指示选项卡控件显示滚动按钮或显示的选项卡式窗口菜单按钮。  
  
```  
BOOL IsTabDocumentsMenu() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果使用弹出菜单的选项卡式的窗口标签; 滚动选项卡式的窗口`FALSE`如果使用向前和向后滚动按钮滚动选项卡式的窗口。  
  
### <a name="remarks"></a>备注  
 使用[CMFCTabCtrl::EnableTabDocumentsMenu](#enabletabdocumentsmenu)方法指定的滚动方法选项卡式窗口。  
  
##  <a name="isvs2005style"></a>  CMFCTabCtrl::IsVS2005Style  
 指示是否使用 Visual Studio 2005 的样式绘制选项卡。  
  
```  
virtual BOOL IsVS2005Style() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果使用 Visual Studio 2005; 的样式绘制选项卡否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 使用`style`参数[CMFCTabCtrl::Create](#create)方法，以指定如何绘制选项卡。  
  
##  <a name="m_benableactivate"></a>  CMFCTabCtrl::m_bEnableActivate  
 防止失去焦点时插入新选项卡并将其启用活动视图。  
  
```  
static BOOL m_bEnableActivate;  
```  
  
### <a name="remarks"></a>备注  
 焦点通常均由一个新的选项卡式窗口时插入并将其激活选项卡。 设置`CMFCTabCtrl::m_bEnableActivate`到成员变量`FALSE`保留原始的焦点。 默认值为 `TRUE`。  
  
##  <a name="modifytabstyle"></a>  CMFCTabCtrl::ModifyTabStyle  
 指定当前选项卡控件中选项卡的外观。  
  
```  
BOOL ModifyTabStyle(Style style);
```  
  
### <a name="parameters"></a>参数  
 [in] `style`  
 指定的选项卡控件外观的枚举值之一。 有关详细信息，请参阅备注中的表。  
  
### <a name="return-value"></a>返回值  
 总是为 `TRUE`。  
  
### <a name="remarks"></a>备注  
 值`style`参数可以是以下之一`CMFCTabCtrl::Style`枚举。  
  
|名称|描述|  
|----------|-----------------|  
|STYLE_3D|显示三维、 矩形具有圆角的选项卡。|  
|STYLE_3D_ONENOTE|显示三维选项卡具有一个垂直端和一个倾斜的端且，有了圆形角。|  
|STYLE_3D_ROUNDED|显示具有倾斜两边，并使用圆角的三维选项卡。|  
|STYLE_3D_ROUNDED_SCROLL|显示具有倾斜两边，并使用圆角的三维选项卡。 如果有更多选项卡可以显示在同一时间，框架将显示一个下拉箭头和选项卡以使处于活动状态的菜单。|  
|STYLE_3D_SCROLLED|显示三维、 矩形的选项卡。 如果有更多选项卡可以显示在同一时间，框架将显示一个下拉箭头和选项卡以使处于活动状态的菜单。|  
|STYLE_3D_VS2005|显示三维效果，舍入具有一个倾斜的端和一个垂直端的选项卡。|  
|STYLE_FLAT|显示具有倾斜左侧和右侧的二维选项卡。|  
|STYLE_FLAT_SHARED_HORZ_SCROLL|显示二维选项卡。 如果有更多选项卡可以显示在同一时间，框架将显示两端的选项卡区域的滚动箭头。|  
  
##  <a name="ondragenter"></a>  CMFCTabCtrl::OnDragEnter  
 由框架调用拖放操作期间当光标首次进入当前选项卡控件的窗口。  
  
```  
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDataObject`  
 指向一个包含用户拖动的数据的数据对象。  
  
 [in] `dwKeyState`  
 包含修改键的状态。 此参数是以下值的按位组合 (OR): `MK_CONTROL`， `MK_SHIFT`， `MK_ALT`， `MK_LBUTTON`， `MK_MBUTTON`，和`MK_RBUTTON`。 有关详细信息，请参阅**消息参数**部分[有关鼠标输入](http://msdn.microsoft.com/library/windows/desktop/ms645601)。  
  
 [in] `point`  
 包含当前工作区坐标中光标的位置。  
  
### <a name="return-value"></a>返回值  
 始终`DROPEFFECT_NONE`，这意味着拖放目标不能接受数据。  
  
### <a name="remarks"></a>备注  
 使用此方法支持拖放操作。 重写此方法来实现你自己的自定义行为。  
  
 默认情况下，此方法仅调用`CMFCTabCtrl::OnDragOver`，后者始终返回`DROPEFFECT_NONE`。  
  
##  <a name="ondragover"></a>  CMFCTabCtrl::OnDragOver  
 由框架调用在拖动操作期间当鼠标移到放置目标窗口。  
  
```  
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDataObject`  
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md)正在拖动到放置目标上的对象。  
  
 [in] `dwKeyState`  
 状态的修改键，即的按位组合 （或者） `MK_CONTROL`， `MK_SHIFT`， `MK_ALT`， `MK_LBUTTON`， `MK_MBUTTON`，和`MK_RBUTTON`。 有关详细信息，请参见"消息参数"[有关鼠标输入](http://msdn.microsoft.com/library/windows/desktop/ms645601)。  
  
 [in] `point`  
 当前的鼠标位置。  
  
### <a name="return-value"></a>返回值  
 总是为 `DROPEFFECT_NONE`。  
  
### <a name="remarks"></a>备注  
 重写此方法与自定义实现。 有关详细信息，请参阅[CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover)方法。  
  
##  <a name="onshowtabdocumentsmenu"></a>  CMFCTabCtrl::OnShowTabDocumentsMenu  
 显示弹出菜单的选项卡式窗口，等待，直到用户选择一个选项卡，并使已选定选项卡成为活动选项卡。  
  
```  
virtual void OnShowTabDocumentsMenu(CPoint point);
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
 显示弹出菜单的位置的坐标。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setactiveinmditabgroup"></a>  CMFCTabCtrl::SetActiveInMDITabGroup  
 将选项卡控件的当前选项卡设置为多个文档接口选项卡组中的活动选项卡。  
  
```  
void SetActiveInMDITabGroup(BOOL bActive);
```  
  
### <a name="parameters"></a>参数  
 [in] `bActive`  
 `TRUE` 若要使活动选项卡; 的当前选项卡`FALSE`以使当前选项卡处于非活动状态。  
  
### <a name="remarks"></a>备注  
 可以将多个文档窗口组织为任一垂直或水平选项卡组，还可以轻松地随机文档从一个选项卡组排列到另一个。  
  
##  <a name="setactivetab"></a>  CMFCTabCtrl::SetActiveTab  
 激活选项卡。  
  
```  
virtual BOOL SetActiveTab(int iTab);
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 指定要激活的选项卡的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果指定的选项卡已激活;`FALSE`如果指定`iTab`参数值无效。  
  
### <a name="remarks"></a>备注  
 此方法不会发送`AFX_WM_CHANGE_ACTIVE_TAB`向父窗口的选项卡控件的通知。  
  
 `SetActiveTab`方法将自动调用[CMFCTabCtrl::HideActiveWindowHorzScrollBar](#hideactivewindowhorzscrollbar)方法要阻止屏幕闪烁。  
  
##  <a name="setactivetabboldfont"></a>  CMFCTabCtrl::SetActiveTabBoldFont  
 启用或禁用使用活动选项卡上的加粗字体。  
  
```  
void SetActiveTabBoldFont(BOOL bIsBold=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bIsBold`  
 `TRUE` 若要使用粗体字体来显示活动选项卡; 标签`FALSE`使用标准字体显示标签。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setdrawframe"></a>  CMFCTabCtrl::SetDrawFrame  
 指定是否嵌入栏周围绘制框架矩形。  
  
```  
void SetDrawFrame(BOOL bDraw=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bDraw`  
 `TRUE` 若要显示一个嵌入的栏; 周围的帧矩形否则为`FALSE`。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setflatframe"></a>  CMFCTabCtrl::SetFlatFrame  
 指定是否在选项卡区域周围绘制以平面或 3D 帧。  
  
```  
void SetFlatFrame(
    BOOL bFlat=TRUE,  
    BOOL bRepaint=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bFlat`  
 `TRUE` 若要在选项卡区域; 周围绘制平面 （二维） 框架`FALSE`若要绘制三维 (3D) 框架。 默认值为 `TRUE`。  
  
 [in] `bRepaint`  
 `TRUE` 若要立即; 重绘窗口否则为`FALSE`。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setimagelist"></a>  CMFCTabCtrl::SetImageList  
 指定图像列表。  
  
```  
virtual BOOL SetImageList(
    UINT uiID,  
    int cx=15,  
    COLORREF clrTransp=RGB(255, 0, 255));  
  
virtual BOOL SetImageList(HIMAGELIST hImageList);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiID`  
 包含的图像列表位图资源的 ID。  
  
 [in] `cx`  
 每个图像，以像素为单位的宽度。 默认值为 15。  
  
 [in] `clrTransp`  
 透明图像颜色。 此颜色图像的部分将是透明的。 默认值为颜色洋红色，RGB(255,0,255)。  
  
 [in] `hImageList`  
 预加载的图像列表句柄。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果此方法成功。 `FALSE` 如果使用平面样式创建选项卡控件或第一种方法重载无法加载指定的位图`uiID`参数。  
  
### <a name="remarks"></a>备注  
 使用此方法设置的选项卡控件图像列表。 选项卡标签旁显示的图像列表的图像。 此方法重新计算选项卡高度，以便选项卡大小调整，以包含图像和文本。  
  
 使用[cmfcbasetabctrl:: Addtab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)的选项卡控件以指定要显示的图像的索引都将继承的方法。  
  
##  <a name="setresizemode"></a>  CMFCTabCtrl::SetResizeMode  
 指定当前选项卡控件可以调整大小，然后重新显示控件。  
  
```  
void SetResizeMode(ResizeMode resizeMode);
```  
  
### <a name="parameters"></a>参数  
 [in] `resizeMode`  
 之一`CMFCTabCtrl::ResizeMode`指定选项卡控件可以调整大小的枚举值。 有关可能的值的列表，请参阅备注中的表。  
  
### <a name="remarks"></a>备注  
 `resizeMode`参数可以是以下之一`ResizeMode`枚举值。  
  
|名称|描述|  
|----------|-----------------|  
|RESIZE_NO|选项卡控件不调整大小。|  
|RESIZE_VERT|选项卡控件可以调整垂直但不是进行水平大小。|  
|RESIZE_HORIZ|选项卡控件可以调整水平但不是进行垂直大小。|  
  
##  <a name="settabmaxwidth"></a>  CMFCTabCtrl::SetTabMaxWidth  
 在选项卡式窗口中指定的最大的选项卡宽度。  
  
```  
void SetTabMaxWidth(int nTabMaxWidth);
```  
  
### <a name="parameters"></a>参数  
 [in] `nTabMaxWidth`  
 最大的选项卡宽度，以像素为单位。  
  
### <a name="remarks"></a>备注  
 使用此方法以限制每个选项卡中选项卡式窗口的宽度。 此方法很有用，如果选项卡有很长的标签。 [CMFCTabCtrl](../../mfc/reference/cmfctabctrl-class.md)类构造函数初始化为 0，这实际上意味着宽度不受限制的最大的选项卡宽度。  
  
##  <a name="stopresize"></a>  CMFCTabCtrl::StopResize  
 终止当前选项卡控件的大小调整操作。  
  
```  
void StopResize(BOOL bCancel);
```  
  
### <a name="parameters"></a>参数  
 [in] `bCancel`  
 `TRUE` 放弃当前的大小调整操作;`FALSE`完成当前的调整大小操作。 在任一情况下，框架将停止绘制调整大小矩形。  
  
##  <a name="synchronizescrollbar"></a>  CMFCTabCtrl::SynchronizeScrollBar  
 在显示平面选项卡的选项卡控件上绘制水平滚动条。  
  
```  
BOOL SynchronizeScrollBar(SCROLLINFO* pScrollInfo = NULL);
```  
  
### <a name="parameters"></a>参数  
 [out] `pScrollInfo`  
 指向[SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537)结构或`NULL`。 当此方法返回时，并且如果此参数不是`NULL`，该结构包含的滚动条的所有参数。 默认值为 `NULL`。  
  
### <a name="return-value"></a>返回值  
 `TRUE` 如果此方法成功，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法会影响显示平面选项卡的选项卡控件。 滚动条在同一时间会影响所有选项卡。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CDockablePane 类](../../mfc/reference/cdockablepane-class.md)   
 [CDockablePane 类](../../mfc/reference/cdockablepane-class.md)   
 [CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)
