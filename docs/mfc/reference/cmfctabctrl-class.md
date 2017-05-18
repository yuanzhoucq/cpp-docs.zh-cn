---
title: "CMFCTabCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
- CMFCTabCtrl::SwapTabs method
- CMFCTabCtrl constructor
- CMFCTabCtrl::MoveTab method
- CMFCTabCtrl::GetTabFromPoint method
- CMFCTabCtrl::PreTranslateMessage method
- CMFCTabCtrl::RecalcLayout method
- CMFCTabCtrl class
- CMFCTabCtrl::IsPtInTabArea method
ms.assetid: d441385d-2c72-4203-96fa-deae2273da35
caps.latest.revision: 33
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
ms.openlocfilehash: 595ff7fbcd55f3b756ce650e02b6247b898d7629
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

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
|[CMFCTabCtrl::ActivateMDITab](#activatemditab)|显示当前选项卡控件指定选项卡，并将焦点设置在该选项卡上。|  
|[CMFCTabCtrl::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)||  
|[CMFCTabCtrl::AutoSizeWindow](#autosizewindow)|指定是否要调整大小的工作区的所有选项卡控件窗口时用户界面元素的选项卡控件更改框架。|  
|[CMFCTabCtrl::CalcRectEdit](#calcrectedit)|压缩指定的选项卡区域的大小。 （重写 `CMFCBaseTabCtrl::CalcRectEdit`。）|  
|[CMFCTabCtrl::Create](#create)|创建选项卡上的控件并将其附加到`CMFCTabCtrl`对象。|  
|`CMFCTabCtrl::CreateObject`|由框架用于创建此类类型的动态实例。|  
|[CMFCTabCtrl::EnableActiveTabCloseButton](#enableactivetabclosebutton)|显示或隐藏关闭按钮 ( **X**) 在活动选项卡上。|  
|[CMFCTabCtrl::EnableInPlaceEdit](#enableinplaceedit)|启用或禁用可编辑的选项卡标签。 (重写[CMFCBaseTabCtrl::EnableInPlaceEdit](../../mfc/reference/cmfcbasetabctrl-class.md#enableinplaceedit)。)|  
|[CMFCTabCtrl::EnableTabDocumentsMenu](#enabletabdocumentsmenu)|将替换两个滚动窗口选项卡包含用于将打开一个菜单选项卡式窗口的按钮的按钮。|  
|[CMFCTabCtrl::EnsureVisible](#ensurevisible)|确保可见选项卡。|  
|[CMFCTabCtrl::GetDocumentIcon](#getdocumenticon)|检索与选项卡式窗口弹出菜单中的选项卡相关联的符号。|  
|[CMFCTabCtrl::GetFirstVisibleTabNum](#getfirstvisibletabnum)|检索当前选项卡控件中可见第一个选项卡的索引。|  
|[CMFCTabCtrl::GetResizeMode](#getresizemode)|检索一个值，指定如何调整大小的当前选项卡控件。|  
|[CMFCTabCtrl::GetScrollBar](#getscrollbar)|检索指向与选项卡控件关联的滚动栏对象的指针。|  
|[CMFCTabCtrl::GetTabArea](#gettabarea)|检索位于顶部或底部的选项卡控件的选项卡标签区域的边框。 (重写[CMFCBaseTabCtrl::GetTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#gettabarea)。)|  
|`CMFCTabCtrl::GetTabFromPoint`|检索包含指定的点的选项卡。 (重写[CMFCBaseTabCtrl::GetTabFromPoint](../../mfc/reference/cmfcbasetabctrl-class.md#gettabfrompoint)。)|  
|[CMFCTabCtrl::GetTabMaxWidth](#gettabmaxwidth)|检索一个选项卡的最大宽度。|  
|[CMFCTabCtrl::GetTabsHeight](#gettabsheight)|检索当前选项卡控件的选项卡区域的高度。|  
|[CMFCTabCtrl::GetTabsRect](#gettabsrect)|检索限定当前选项卡控件的选项卡区域的矩形。 (重写[CMFCBaseTabCtrl::GetTabsRect](../../mfc/reference/cmfcbasetabctrl-class.md#gettabsrect)。)|  
|`CMFCTabCtrl::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)程序与此类类型的对象。|  
|[CMFCTabCtrl::GetWndArea](#getwndarea)|检索当前选项卡控件的工作区的边界。|  
|[CMFCTabCtrl::HideActiveWindowHorzScrollBar](#hideactivewindowhorzscrollbar)|如果任何活动窗口将隐藏水平滚动条。|  
|[CMFCTabCtrl::HideInactiveWindow](#hideinactivewindow)|指定是否要显示非活动状态的选项卡控件窗口框架。|  
|[CMFCTabCtrl::HideNoTabs](#hidenotabs)|启用或禁用绘制选项卡区域，如果没有可见的选项卡。|  
|[CMFCTabCtrl::HideSingleTab](#hidesingletab)|启用或禁用单个选项卡式的窗口时绘制一个选项卡。 (重写[CMFCBaseTabCtrl::HideSingleTab](../../mfc/reference/cmfcbasetabctrl-class.md#hidesingletab)。)|  
|[CMFCTabCtrl::IsActiveInMDITabGroup](#isactiveinmditabgroup)|指示选项卡控件当前选项卡是否为多个文档接口选项卡组活动选项卡。|  
|[CMFCTabCtrl::IsActiveTabBoldFont](#isactivetabboldfont)|指示是否使用加粗字体显示活动选项卡的文本。|  
|[CMFCTabCtrl::IsActiveTabCloseButton](#isactivetabclosebutton)|指示是否关闭按钮 ( **X**) 显示在活动选项卡或选项卡区域的右上角上。|  
|[CMFCTabCtrl::IsDrawFrame](#isdrawframe)|指示是否选项卡式的窗口周围绘制一个帧矩形嵌入窗格。|  
|[CMFCTabCtrl::IsFlatFrame](#isflatframe)|指示选项卡区域周围的框架是平面或 3D。|  
|[CMFCTabCtrl::IsFlatTab](#isflattab)|指示当前选项卡控件中选项卡的外观是否平面。|  
|[CMFCTabCtrl::IsLeftRightRounded](#isleftrightrounded)|指示是否舍入的左侧和右侧当前选项卡控件中的选项卡的外观。|  
|[CMFCTabCtrl::IsMDITabGroup](#ismditabgroup)|指示当前选项卡控件是否包含的多文档界面窗口的工作区中。|  
|[CMFCTabCtrl::IsOneNoteStyle](#isonenotestyle)|指示是否在 Microsoft OneNote 样式中显示当前选项卡控件。|  
|`CMFCTabCtrl::IsPtInTabArea`|确定某个点是否在选项卡区域内。 (重写[CMFCBaseTabCtrl::IsPtInTabArea](../../mfc/reference/cmfcbasetabctrl-class.md#isptintabarea)。)|  
|[CMFCTabCtrl::IsSharedScroll](#issharedscroll)|指示当前选项卡控件是否有可以滚动作为一个组，其选项卡的滚动条。|  
|[CMFCTabCtrl::IsTabDocumentsMenu](#istabdocumentsmenu)|指示选项卡控件显示滚动按钮或显示的选项卡式窗口菜单的按钮。|  
|[CMFCTabCtrl::IsVS2005Style](#isvs2005style)|指示是否在 Visual Studio.NET 2005年的样式显示选项卡。|  
|[CMFCTabCtrl::ModifyTabStyle](#modifytabstyle)|当前选项卡控件中指定选项卡的外观。|  
|`CMFCTabCtrl::MoveTab`|将一个选项卡移动到另一个选项卡位置。 (重写[CMFCBaseTabCtrl::MoveTab](../../mfc/reference/cmfcbasetabctrl-class.md#movetab)。)|  
|[CMFCTabCtrl::OnDragEnter](#ondragenter)|第一次光标拖到选项卡控制窗口中时由框架调用。|  
|[CMFCTabCtrl::OnDragOver](#ondragover)|由框架调用在拖动操作期间当鼠标移到放置目标窗口。 (重写[CMFCBaseTabCtrl::OnDragOver](../../mfc/reference/cmfcbasetabctrl-class.md#ondragover)。)|  
|[CMFCTabCtrl::OnShowTabDocumentsMenu](#onshowtabdocumentsmenu)|显示的选项卡式窗口的弹出菜单时，一直等待，直到用户选择一个选项卡，并使活动选项卡的所选选项卡。|  
|`CMFCTabCtrl::PreTranslateMessage`|翻译窗口消息之前被发送到[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函数。 (重写[CMFCBaseTabCtrl::PreTranslateMessage](../../mfc/reference/cmfcbasetabctrl-class.md#pretranslatemessage)。)|  
|`CMFCTabCtrl::RecalcLayout`|重新计算选项卡控件的内部布局。 (重写[CMFCBaseTabCtrl::RecalcLayout](../../mfc/reference/cmfcbasetabctrl-class.md#recalclayout)。)|  
|[CMFCTabCtrl::SetActiveInMDITabGroup](#setactiveinmditabgroup)|将选项卡控件当前选项卡设置为在多文档界面选项卡组活动选项卡。|  
|[CMFCTabCtrl::SetActiveTab](#setactivetab)|激活选项卡。 (重写[CMFCBaseTabCtrl::SetActiveTab](../../mfc/reference/cmfcbasetabctrl-class.md#setactivetab)。)|  
|[CMFCTabCtrl::SetActiveTabBoldFont](#setactivetabboldfont)|启用或禁用使用活动选项卡上的加粗字体。|  
|[CMFCTabCtrl::SetDrawFrame](#setdrawframe)|启用或禁用周围嵌入栏 drawinga 帧矩形。|  
|[CMFCTabCtrl::SetFlatFrame](#setflatframe)|指定是否以选项卡区域的周围绘制以平面或 3D 的框架。|  
|[CMFCTabCtrl::SetImageList](#setimagelist)|指定图像列表。 (重写[CMFCBaseTabCtrl::SetImageList](../../mfc/reference/cmfcbasetabctrl-class.md#setimagelist)。)|  
|[CMFCTabCtrl::SetResizeMode](#setresizemode)|指定如何调整大小的当前选项卡控件，然后重新显示该控件。|  
|[CMFCTabCtrl::SetTabMaxWidth](#settabmaxwidth)|在选项卡式窗口中指定的最大的选项卡宽度。|  
|[CMFCTabCtrl::StopResize](#stopresize)|终止当前的大小调整操作选项卡控件上。|  
|`CMFCTabCtrl::SwapTabs`|交换一对选项卡。 (重写[CMFCBaseTabCtrl::SwapTabs](../../mfc/reference/cmfcbasetabctrl-class.md#swaptabs)。)|  
|[CMFCTabCtrl::SynchronizeScrollBar](#synchronizescrollbar)|在显示平面选项卡的选项卡控件上绘制的水平滚动条。|  
  
### <a name="data-members"></a>数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCTabCtrl::m_bEnableActivate](#m_benableactivate)|防止失去焦点时插入并启用一个新选项卡中的活动视图。|  
  
## <a name="remarks"></a>备注  
 `CMFCTabCtrl`类支持︰  
  
-   选项卡包括 3D、 平齐，和平面共享水平滚动条控件样式。  
  
-   选项卡位于顶部或底部的窗口中。  
  
-   显示文本、 图像或文本和图像的选项卡。  
  
-   选项卡处于活动状态时更改颜色的选项卡。  
  
-   可调整的选项卡的边框大小更改。  
  
-   可拆分的选项卡式的窗口。  
  
 `CMFCTabCtrl`类可以用于对话框中，但适用于在应用程序使用停靠控件条类似[!INCLUDE[ofprexcel](../../mfc/reference/includes/ofprexcel_md.md)]和[!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)]。 有关详细信息，请参阅[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)。  
  
 请按照上述步骤以添加可调整大小，在您的应用程序中的选项卡控件停靠在操作︰  
  
1.  创建的实例[CTabbedPane 类](../../mfc/reference/ctabbedpane-class.md)。  
  
2.  调用[CDockablePane::Create](../../mfc/reference/cdockablepane-class.md#create)。  
  
3.  使用[CBaseTabbedPane::AddTab](../../mfc/reference/cbasetabbedpane-class.md#addtab)或[cmfcbasetabctrl:: Inserttab](../../mfc/reference/cmfcbasetabctrl-class.md#inserttab)可以添加新选项卡。  
  
4.  调用[CBasePane::EnableDocking](../../mfc/reference/cbasepane-class.md#enabledocking) ，以便可以将当前的停靠选项卡控件停靠的主框架窗口。  
  
5.  调用[CFrameWndEx::DockPane](../../mfc/reference/cframewndex-class.md#dockpane)停靠在主框架选项卡式窗口。  
  
 有关如何创建作为停靠控件条条选项卡式的窗口的示例，请参阅[CTabbedPane 类](../../mfc/reference/ctabbedpane-class.md)。 若要使用`CMFCTabCtrl`作为非停靠控件，创建`CMFCTabCtrl`对象，然后调用[CMFCTabCtrl::Create](#create)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)  
  
 [CMFCTabCtrl](../../mfc/reference/cmfctabctrl-class.md)  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法`CMFCTabCtrl`用于配置类`CMFCTabCtrl`对象。 该示例说明如何添加选项卡、 活动选项卡上显示关闭按钮、 启用可编辑的选项卡标签和显示选项卡式的窗口标签的弹出菜单。 此示例摘自[状态收集样本](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_StateCollection #&1;](../../mfc/reference/codesnippet/cpp/cmfctabctrl-class_1.h)]  
[!code-cpp[NVC_MFC_StateCollection #&3;](../../mfc/reference/codesnippet/cpp/cmfctabctrl-class_2.cpp)]  
  
## <a name="requirements"></a>要求  
 **标头︰** afxtabctrl.h  
  
##  <a name="activatemditab"></a>CMFCTabCtrl::ActivateMDITab  
 显示当前选项卡控件指定选项卡，并将焦点设置在该选项卡上。  
  
```  
void ActivateMDITab(int nTab = -1);
```  
  
### <a name="parameters"></a>参数  
 [in] `nTab`  
 选项卡显示，或者为-1 以指定当前处于活动状态选项卡的从零开始索引。  
  
##  <a name="allowdestroyemptytabbedpane"></a>CMFCTabCtrl::AllowDestroyEmptyTabbedPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL AllowDestroyEmptyTabbedPane() const;  
```  
  
### <a name="return-value"></a>返回值  
 总是为 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="autosizewindow"></a>CMFCTabCtrl::AutoSizeWindow  
 指定是否要调整大小的工作区的所有选项卡控件窗口时用户界面元素的选项卡控件更改框架。  
  
```  
void AutoSizeWindow(BOOL bAutoSize = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bAutoSize`  
 `TRUE`若要自动调整大小选项卡控件窗口中︰否则为`FALSE`。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="create"></a>CMFCTabCtrl::Create  
 创建选项卡上的控件并将其附加到`CMFCTabCtrl`对象。  
  
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
 选项卡的位置。 默认值为 `LOCATION_BOTTOM`。 有关更多信息，请参见“备注”。  
  
 [in] `bCloseBtn`  
 `TRUE`若要显示在选项卡; 关闭按钮否则为`FALSE`。 默认值为 `FALSE`。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 `TRUE`；否则为 `FALSE`。  
  
### <a name="remarks"></a>备注  
 下表描述了可为指定值`style`参数。  
  
|样式|描述|  
|-----------|-----------------|  
|STYLE_3D|创建具有三维外观的选项卡控件。|  
|STYLE_FLAT|带有平面选项卡创建选项卡控件。|  
|STYLE_FLAT_SHARED_HORZ_SCROLL|带有平面选项卡和滚动条可滚动选项卡，如果它们剪裁的父窗口创建选项卡控件。|  
|STYLE_3D_ONENOTE|创建选项卡控件中的 Microsoft OneNote 样式。|  
|STYLE_3D_VS2005|在样式中的 Microsoft Visual Studio 2005 创建选项卡控件。|  
|STYLE_3D_ROUNDED|带有圆角的选项卡样式的 Microsoft Visual Studio 2005 创建选项卡控件。|  
|STYLE_3D_ROUNDED_SCROLL|创建带有圆角的选项卡和 Microsoft Visual Studio 2005 样式的滚动按钮选项卡控件。|  
  
 下表列出了可为指定值`location`参数。  
  
|位置|描述|  
|--------------|-----------------|  
|LOCATION_BOTTOM|选项卡位于底部的选项卡控件。|  
|LOCATION_TOP|选项卡位于顶部的选项卡控件。|  
  
### <a name="example"></a>示例  
 下面的示例演示如何使用`Create`中的方法`CMFCTabCtrl`类。 此示例摘自[状态收集样本](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_StateCollection #&1;](../../mfc/reference/codesnippet/cpp/cmfctabctrl-class_1.h)]  
[!code-cpp[NVC_MFC_StateCollection #&2;](../../mfc/reference/codesnippet/cpp/cmfctabctrl-class_3.cpp)]  
  
##  <a name="calcrectedit"></a>CMFCTabCtrl::CalcRectEdit  
 压缩指定的选项卡区域的大小。  
  
```  
virtual void CalcRectEdit(CRect& rectEdit);
```  
  
### <a name="parameters"></a>参数  
 [in] `rectEdit`  
 一个指定的选项卡区域的矩形。  
  
### <a name="remarks"></a>备注  
 当您更改的选项卡标签时，调用此方法。 此方法压缩的左侧和右侧指定的矩形的一半的当前选项卡高度，并压缩顶部和底部一个单位。  
  
##  <a name="enableactivetabclosebutton"></a>CMFCTabCtrl::EnableActiveTabCloseButton  
 显示或隐藏关闭按钮 ( **X**) 在活动选项卡上。  
  
```  
void EnableActiveTabCloseButton(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE`在活动选项卡; 上显示关闭按钮`FALSE`要在选项卡区域的右上角上显示关闭按钮。 默认值为 `TRUE`。  
  
##  <a name="enableinplaceedit"></a>CMFCTabCtrl::EnableInPlaceEdit  
 启用或禁用可编辑的选项卡标签。  
  
```  
virtual void EnableInPlaceEdit(BOOL bEnable);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE`若要启用可编辑的选项卡标签;`FALSE`禁用可编辑的选项卡标签。  
  
### <a name="remarks"></a>备注  
  
##  <a name="enabletabdocumentsmenu"></a>CMFCTabCtrl::EnableTabDocumentsMenu  
 一个用户界面，使用两个按钮来滚动窗口选项卡和显示选项卡式窗口弹出菜单的接口之间切换。  
  
```  
void EnableTabDocumentsMenu(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE`若要显示的选项卡式的窗口标签; 一个弹出菜单`FALSE`显示向前和向后滚动按钮。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
 当用户单击选项卡标签时，框架将显示相应的选项卡式的窗口。 如果选项卡标签可见，而无需更改其位置后打开此选项卡式的窗口。 如果用户从弹出菜单中选择一个文档和相应的选项卡式的窗口已关闭屏幕，选项卡式的窗口将成为第一个选项卡。  
  
##  <a name="ensurevisible"></a>CMFCTabCtrl::EnsureVisible  
 确保可见选项卡。  
  
```  
virtual BOOL EnsureVisible(int iTab);
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 选项卡的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则`FALSE`如果`iTab`是无效的参数索引。  
  
### <a name="remarks"></a>备注  
 使用此方法以确保指定的选项卡是可见。 如有必要，将滚动选项卡控件。  
  
##  <a name="getdocumenticon"></a>CMFCTabCtrl::GetDocumentIcon  
 检索与选项卡式窗口的弹出菜单中的选项卡相关联的映像。  
  
```  
static HICON __stdcall GetDocumentIcon(UINT nCmdID);
```  
  
### <a name="parameters"></a>参数  
 [in] `nCmdID`  
 在选项卡式窗口的弹出菜单的选项卡的命令 ID。  
  
### <a name="return-value"></a>返回值  
 位图图像的句柄。  
  
##  <a name="getfirstvisibletabnum"></a>CMFCTabCtrl::GetFirstVisibleTabNum  
 检索当前选项卡控件中可见第一个选项卡的索引。  
  
```  
virtual int GetFirstVisibleTabNum() const;  
```  
  
### <a name="return-value"></a>返回值  
 在选项卡控件的选项卡的从零开始的索引。  
  
### <a name="remarks"></a>备注  
 只有当选项卡控件显示在样式中的 Microsoft OneNote 时，请使用此方法。 使用[CMFCTabCtrl::IsOneNoteStyle](#isonenotestyle)方法，以确定该样式。  
  
##  <a name="getresizemode"></a>CMFCTabCtrl::GetResizeMode  
 检索一个值，指定如何调整大小的当前选项卡控件。  
  
```  
ResizeMode GetResizeMode() const;  
```  
  
### <a name="return-value"></a>返回值  
 其中一个`CMFCTabCtrl::ResizeMode`枚举值，该值指定如何调整大小选项卡控件。 有关可能的值的列表，请参阅备注部分的[CMFCTabCtrl::SetResizeMode](#setresizemode)方法。  
  
##  <a name="getscrollbar"></a>CMFCTabCtrl::GetScrollBar  
 检索指向与选项卡控件关联的滚动栏对象的指针。  
  
```  
CScrollBar* GetScrollBar();
```  
  
### <a name="return-value"></a>返回值  
 一种指向滚动条对象，或者`NULL`如果不通过使用创建选项卡控件`STYLE_FLAT_SHARED_HORZ_SCROLL`样式。  
  
### <a name="remarks"></a>备注  
 此方法用于访问选项卡控件嵌入的滚动条。 仅当有选项卡控件时创建了一个滚动条对象`STYLE_FLAT_SHARED_HORZ_SCROLL`样式。  
  
##  <a name="gettabarea"></a>CMFCTabCtrl::GetTabArea  
 检索位于顶部或底部的选项卡控件的选项卡标签区域的边框。  
  
```  
void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `rectTabAreaTop`  
 此方法返回时，本参考包含限定顶部的选项卡标签区域的矩形。 矩形是在工作区坐标。 此引用为空，如果没有选项卡标签区域存在顶部的选项卡控件。  
  
 [out] `rectTabAreaBottom`  
 此方法返回时，本参考包含限定底部选项卡上标签区域的矩形。 矩形是在工作区坐标。 此引用为空，如果没有选项卡标签区域存在底部的选项卡控件。  
  
### <a name="remarks"></a>备注  
 使用此方法来确定的大小和选项卡区域在选项卡式窗口中的位置。  
  
##  <a name="gettabmaxwidth"></a>CMFCTabCtrl::GetTabMaxWidth  
 检索一个选项卡的最大宽度。  
  
```  
int GetTabMaxWidth() const;  
```  
  
### <a name="return-value"></a>返回值  
 选项卡上，以像素为单位的最大宽度。 如果返回值为 0，则选项卡宽度没有限制。  
  
### <a name="remarks"></a>备注  
 使用[CMFCTabCtrl::SetTabMaxWidth](#settabmaxwidth)方法来将最大的选项卡宽度设置。  
  
##  <a name="gettabsheight"></a>CMFCTabCtrl::GetTabsHeight  
 检索当前选项卡控件的选项卡区域的高度。  
  
```  
virtual int GetTabsHeight() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果任何选项卡是可见的或为零会显示任何选项卡的选项卡区域的高度。  
  
##  <a name="gettabsrect"></a>CMFCTabCtrl::GetTabsRect  
 检索限定当前选项卡控件的选项卡区域的矩形。  
  
```  
virtual void GetTabsRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `rect`  
 此方法返回时，`rect`参数包含限定选项卡区域的矩形。  
  
##  <a name="getwndarea"></a>CMFCTabCtrl::GetWndArea  
 检索当前选项卡控件的工作区的边界。  
  
```  
void GetWndArea(CRect& rect) const;  
```  
  
### <a name="parameters"></a>参数  
 [in, out] `rect`  
 此方法返回时，此参数包含限定当前选项卡控件的矩形。  
  
### <a name="remarks"></a>备注  
  
##  <a name="hideactivewindowhorzscrollbar"></a>CMFCTabCtrl::HideActiveWindowHorzScrollBar  
 如果有的话，在活动窗口将隐藏水平滚动条。  
  
```  
void HideActiveWindowHorzScrollBar();
```  
  
### <a name="remarks"></a>备注  
 使用此方法要阻止选项卡控件闪烁选项卡控件页之间切换用户时。  
  
##  <a name="hideinactivewindow"></a>CMFCTabCtrl::HideInactiveWindow  
 指定框架是否显示非活动状态的选项卡控件窗口。  
  
```  
void HideInactiveWindow(BOOL bHide = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bHide`  
 `TRUE`不希望显示非活动窗口;`FALSE`以显示非活动窗口。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="hidenotabs"></a>CMFCTabCtrl::HideNoTabs  
 启用或禁用的选项卡区域图画，如果没有可见的选项卡。  
  
```  
void HideNoTabs(BOOL bHide=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bHide`  
 `TRUE`若要启用绘制选项卡区域;`FALSE`禁止绘图。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="hidesingletab"></a>CMFCTabCtrl::HideSingleTab  
 启用或禁用选项卡上绘图，如果没有单一的选项卡式的窗口。  
  
```  
virtual void HideSingleTab(BOOL bHide=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bHide`  
 `TRUE`若要不绘制单个选项卡式窗口; 一个选项卡`FALSE`要绘制一个选项卡。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="isactiveinmditabgroup"></a>CMFCTabCtrl::IsActiveInMDITabGroup  
 指示选项卡控件当前选项卡是否为多文档界面选项卡组活动选项卡。  
  
```  
BOOL IsActiveInMDITabGroup() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果选项卡控件当前选项卡是 MDI 选项卡组; 在活动选项卡否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 可以将任一垂直或水平选项卡分组的多个文档窗口，并轻松地无序播放文档从一个选项卡组到另一个。  
  
##  <a name="isactivetabboldfont"></a>CMFCTabCtrl::IsActiveTabBoldFont  
 指示是否使用加粗字体显示活动选项卡的文本。  
  
```  
BOOL IsActiveTabBoldFont() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果使用加粗字体; 显示活动选项卡否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 使用[CMFCTabCtrl::SetActiveTabBoldFont](#setactivetabboldfont)方法，以更改活动选项卡上的字体。  
  
##  <a name="isactivetabclosebutton"></a>CMFCTabCtrl::IsActiveTabCloseButton  
 指示是否关闭按钮 ( **X**) 将显示在活动选项卡或选项卡区域的右上角上。  
  
```  
virtual BOOL IsActiveTabCloseButton() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果关闭按钮显示在活动选项卡;`FALSE`如果上选项卡区域的右上角显示关闭按钮。  
  
### <a name="remarks"></a>备注  
  
##  <a name="isdrawframe"></a>CMFCTabCtrl::IsDrawFrame  
 指示是否选项卡式的窗口周围绘制一个帧矩形嵌入窗格。  
  
```  
BOOL IsDrawFrame() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果绘制帧矩形;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 使用[CMFCTabCtrl::SetDrawFrame](#setdrawframe)方法来启用或禁用绘制帧矩形。  
  
##  <a name="isflatframe"></a>CMFCTabCtrl::IsFlatFrame  
 指示选项卡区域周围的框架是平面或 3D。  
  
```  
BOOL IsFlatFrame() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果选项卡区域周围的框架保持不变;`FALSE`如果帧为三维图表。  
  
### <a name="remarks"></a>备注  
 使用[CMFCTabCtrl::SetFlatFrame](#setflatframe)方法，以更改如何绘制帧。  
  
##  <a name="isflattab"></a>CMFCTabCtrl::IsFlatTab  
 指示当前选项卡控件中选项卡的外观是否平面。  
  
```  
virtual BOOL IsFlatTab() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果当前选项卡控件中选项卡的外观保持不变;否则为`FALSE`。  
  
##  <a name="isleftrightrounded"></a>CMFCTabCtrl::IsLeftRightRounded  
 指示是否舍入的左侧和右侧当前选项卡控件中的选项卡的外观。  
  
```  
virtual BOOL IsLeftRightRounded() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果每个选项卡的面被舍入;，否则为`FALSE`。  
  
##  <a name="ismditabgroup"></a>CMFCTabCtrl::IsMDITabGroup  
 指示当前选项卡控件是否包含的多文档界面窗口的工作区中。  
  
```  
virtual BOOL IsMDITabGroup() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果当前的选项卡控件是在 MDI 客户端区域窗口中;否则为`FALSE`。  
  
##  <a name="isonenotestyle"></a>CMFCTabCtrl::IsOneNoteStyle  
 指示是否在 Microsoft OneNote 样式中显示当前选项卡控件。  
  
```  
virtual BOOL IsOneNoteStyle() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果该选项卡控件显示在样式中的 Microsoft OneNote;否则为`FALSE`。  
  
##  <a name="issharedscroll"></a>CMFCTabCtrl::IsSharedScroll  
 指示当前选项卡控件是否有可以滚动作为一个组，其选项卡的滚动条。  
  
```  
BOOL IsSharedScroll() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果该选项卡控件具有共享的滚动条;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法返回`TRUE`如果`style`参数[CMFCTabCtrl::Create](#create)方法是 STYLE_FLAT_SHARED_HORZ_SCROLL。  
  
##  <a name="istabdocumentsmenu"></a>CMFCTabCtrl::IsTabDocumentsMenu  
 指示选项卡控件显示滚动按钮或显示的选项卡式窗口菜单的按钮。  
  
```  
BOOL IsTabDocumentsMenu() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果使用的选项卡式的窗口标签; 的弹出菜单滚动选项卡式的窗口`FALSE`如果选项卡式的窗口的滚动量使用向前和向后滚动按钮。  
  
### <a name="remarks"></a>备注  
 使用[CMFCTabCtrl::EnableTabDocumentsMenu](#enabletabdocumentsmenu)方法，以指定的滚动方法选项卡式窗口。  
  
##  <a name="isvs2005style"></a>CMFCTabCtrl::IsVS2005Style  
 指示是否使用 Visual Studio 2005 的样式绘制选项卡。  
  
```  
virtual BOOL IsVS2005Style() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果使用 Visual Studio 2005; 的样式绘制选项卡否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 使用`style`参数[CMFCTabCtrl::Create](#create)方法，以指定如何绘制选项卡。  
  
##  <a name="m_benableactivate"></a>CMFCTabCtrl::m_bEnableActivate  
 防止失去焦点时插入并启用一个新选项卡中的活动视图。  
  
```  
static BOOL m_bEnableActivate;  
```  
  
### <a name="remarks"></a>备注  
 焦点通常均由一个新选项卡式窗口时插入并将其激活选项卡。 设置`CMFCTabCtrl::m_bEnableActivate`到成员变量`FALSE`以保留原始的焦点。 默认值为 `TRUE`。  
  
##  <a name="modifytabstyle"></a>CMFCTabCtrl::ModifyTabStyle  
 当前选项卡控件中指定选项卡的外观。  
  
```  
BOOL ModifyTabStyle(Style style);
```  
  
### <a name="parameters"></a>参数  
 [in] `style`  
 指定选项卡控件的外观的枚举值之一。 有关详细信息，请参阅备注中的表。  
  
### <a name="return-value"></a>返回值  
 总是为 `TRUE`。  
  
### <a name="remarks"></a>备注  
 值`style`参数可以是下列其中一项`CMFCTabCtrl::Style`枚举。  
  
|名称|描述|  
|----------|-----------------|  
|STYLE_3D|显示具有圆角的三维、 矩形选项卡。|  
|STYLE_3D_ONENOTE|显示三维选项卡具有一个垂直边和倾斜的一端和，有了圆形角。|  
|STYLE_3D_ROUNDED|显示具有倾斜边，并使用圆角的三维选项卡。|  
|STYLE_3D_ROUNDED_SCROLL|显示具有倾斜边，并使用圆角的三维选项卡。 如果有更多选项卡不是可以显示在同一时间，框架将显示一个下拉箭头和选项卡以使处于活动状态的菜单。|  
|STYLE_3D_SCROLLED|显示三维，矩形的选项卡。 如果有更多选项卡不是可以显示在同一时间，框架将显示一个下拉箭头和选项卡以使处于活动状态的菜单。|  
|STYLE_3D_VS2005|显示三维效果，舍入具有倾斜的一端和一个垂直边的选项卡。|  
|STYLE_FLAT|显示二维具有倾斜左侧和右侧的选项卡。|  
|STYLE_FLAT_SHARED_HORZ_SCROLL|显示二维选项卡。 如果有更多选项卡不是可以显示在同一时间，框架将显示在选项卡区域末端滚动箭头。|  
  
##  <a name="ondragenter"></a>CMFCTabCtrl::OnDragEnter  
 由框架调用拖放操作期间当光标首次进入当前选项卡控件的窗口。  
  
```  
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDataObject`  
 指向包含在用户拖动的数据的数据对象。  
  
 [in] `dwKeyState`  
 包含修改键的状态。 此参数是下列值的按位组合 (OR): `MK_CONTROL`， `MK_SHIFT`， `MK_ALT`， `MK_LBUTTON`， `MK_MBUTTON`，和`MK_RBUTTON`。 有关详细信息，请参阅**消息参数**部分[有关鼠标输入](http://msdn.microsoft.com/library/windows/desktop/ms645601)。  
  
 [in] `point`  
 包含当前工作区坐标中光标的位置。  
  
### <a name="return-value"></a>返回值  
 始终`DROPEFFECT_NONE`，这意味着拖放目标不能接受的数据。  
  
### <a name="remarks"></a>备注  
 使用此方法来支持拖放操作。 重写此方法以实现您自己的自定义行为。  
  
 默认情况下，此方法仅调用`CMFCTabCtrl::OnDragOver`，而后者始终返回`DROPEFFECT_NONE`。  
  
##  <a name="ondragover"></a>CMFCTabCtrl::OnDragOver  
 由框架调用在拖动操作期间当鼠标移到放置目标窗口。  
  
```  
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDataObject`  
 指向[COleDataObject](../../mfc/reference/coledataobject-class.md)拖放目标上方的对象。  
  
 [in] `dwKeyState`  
 状态的修改键，这是一个按位组合 （或者） `MK_CONTROL`， `MK_SHIFT`， `MK_ALT`， `MK_LBUTTON`， `MK_MBUTTON`，和`MK_RBUTTON`。 有关详细信息，请参见"消息参数"[有关鼠标输入](http://msdn.microsoft.com/library/windows/desktop/ms645601)。  
  
 [in] `point`  
 当前的鼠标位置。  
  
### <a name="return-value"></a>返回值  
 总是为 `DROPEFFECT_NONE`。  
  
### <a name="remarks"></a>备注  
 重写此方法使用您的自定义实现。 有关详细信息，请参阅[CView::OnDragOver](../../mfc/reference/cview-class.md#ondragover)方法。  
  
##  <a name="onshowtabdocumentsmenu"></a>CMFCTabCtrl::OnShowTabDocumentsMenu  
 显示弹出菜单选项卡式窗口，一直等待，直到用户选择一个选项卡，并使活动选项卡的所选选项卡。  
  
```  
virtual void OnShowTabDocumentsMenu(CPoint point);
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
 显示弹出菜单的位置的坐标。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setactiveinmditabgroup"></a>CMFCTabCtrl::SetActiveInMDITabGroup  
 将选项卡控件当前选项卡设置为多文档界面选项卡组活动选项卡。  
  
```  
void SetActiveInMDITabGroup(BOOL bActive);
```  
  
### <a name="parameters"></a>参数  
 [in] `bActive`  
 `TRUE`若要使活动选项卡; 的当前选项卡`FALSE`以使当前选项卡处于非活动状态。  
  
### <a name="remarks"></a>备注  
 可以将任一垂直或水平选项卡分组的多个文档窗口，并轻松地无序播放文档从一个选项卡组到另一个。  
  
##  <a name="setactivetab"></a>CMFCTabCtrl::SetActiveTab  
 激活选项卡。  
  
```  
virtual BOOL SetActiveTab(int iTab);
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 指定要激活的选项卡的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果已激活; 指定选项卡`FALSE`如果指定`iTab`参数值无效。  
  
### <a name="remarks"></a>备注  
 此方法不会发送`AFX_WM_CHANGE_ACTIVE_TAB`发送到父窗口的选项卡控件通知。  
  
 `SetActiveTab`方法将自动调用[CMFCTabCtrl::HideActiveWindowHorzScrollBar](#hideactivewindowhorzscrollbar)方法，以防止屏幕闪烁。  
  
##  <a name="setactivetabboldfont"></a>CMFCTabCtrl::SetActiveTabBoldFont  
 启用或禁用使用活动选项卡上的加粗字体。  
  
```  
void SetActiveTabBoldFont(BOOL bIsBold=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bIsBold`  
 `TRUE`使用加粗字体显示的标签的活动选项卡;`FALSE`若要使用的标准字体来显示标签。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setdrawframe"></a>CMFCTabCtrl::SetDrawFrame  
 指定是否嵌入栏周围绘制一个帧的矩形。  
  
```  
void SetDrawFrame(BOOL bDraw=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bDraw`  
 `TRUE`若要显示嵌入的栏; 周围的帧矩形否则为`FALSE`。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setflatframe"></a>CMFCTabCtrl::SetFlatFrame  
 指定是否以选项卡区域的周围绘制以平面或 3D 的框架。  
  
```  
void SetFlatFrame(
    BOOL bFlat=TRUE,  
    BOOL bRepaint=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bFlat`  
 `TRUE`以选项卡区域; 的周围绘制一个平面 (2D) 框架`FALSE`绘制三维 (3D) 框架。 默认值为 `TRUE`。  
  
 [in] `bRepaint`  
 `TRUE`若要立即; 重绘窗口否则为`FALSE`。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="setimagelist"></a>CMFCTabCtrl::SetImageList  
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
 一个包含图像列表的位图资源的 ID。  
  
 [in] `cx`  
 每个图像，以像素为单位的宽度。 默认值为 15。  
  
 [in] `clrTransp`  
 透明图像颜色。 是这种颜色的图像的部分将是透明的。 默认值为颜色洋红 RGB(255,0,255)。  
  
 [in] `hImageList`  
 指向一个预加载的图像列表的句柄。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此方法成功。 `FALSE`如果使用的平面样式创建选项卡控件或第一个方法重载无法加载由指定的位图`uiID`参数。  
  
### <a name="remarks"></a>备注  
 此方法用于设置选项卡控件的图像列表。 选项卡标签旁边显示的图像列表中的图像。 此方法将重新计算的选项卡高度，以便选项卡设置为包含图像和文本。  
  
 使用[cmfcbasetabctrl:: Addtab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)选项卡控件来指定要显示的图像的索引将继承的方法。  
  
##  <a name="setresizemode"></a>CMFCTabCtrl::SetResizeMode  
 指定如何调整大小的当前选项卡控件，然后重新显示该控件。  
  
```  
void SetResizeMode(ResizeMode resizeMode);
```  
  
### <a name="parameters"></a>参数  
 [in] `resizeMode`  
 其中一个`CMFCTabCtrl::ResizeMode`枚举值，该值指定如何调整大小选项卡控件。 有关可能的值的列表，请参阅备注中的表。  
  
### <a name="remarks"></a>备注  
 `resizeMode`参数可以是下列其中一项`ResizeMode`枚举值。  
  
|名称|描述|  
|----------|-----------------|  
|RESIZE_NO|无法调整大小选项卡控件。|  
|RESIZE_VERT|垂直但不是进行水平，可以调整大小选项卡控件。|  
|RESIZE_HORIZ|可以调整大小选项卡控件，水平但不是进行垂直。|  
  
##  <a name="settabmaxwidth"></a>CMFCTabCtrl::SetTabMaxWidth  
 在选项卡式窗口中指定的最大的选项卡宽度。  
  
```  
void SetTabMaxWidth(int nTabMaxWidth);
```  
  
### <a name="parameters"></a>参数  
 [in] `nTabMaxWidth`  
 最大的选项卡宽度，以像素为单位。  
  
### <a name="remarks"></a>备注  
 使用此方法来限制每个选项卡中选项卡式窗口的宽度。 此方法是在选项卡拥有很长的标签非常有用。 [CMFCTabCtrl](../../mfc/reference/cmfctabctrl-class.md)类构造函数将初始化为 0，这实际上意味着宽度不受限制的最大的选项卡宽度。  
  
##  <a name="stopresize"></a>CMFCTabCtrl::StopResize  
 终止当前的大小调整操作选项卡控件上。  
  
```  
void StopResize(BOOL bCancel);
```  
  
### <a name="parameters"></a>参数  
 [in] `bCancel`  
 `TRUE`放弃当前的大小调整操作;`FALSE`完成当前，调整大小操作。 在任一情况下，框架会停止绘制调整大小矩形。  
  
##  <a name="synchronizescrollbar"></a>CMFCTabCtrl::SynchronizeScrollBar  
 在显示平面选项卡的选项卡控件上绘制的水平滚动条。  
  
```  
BOOL SynchronizeScrollBar(SCROLLINFO* pScrollInfo = NULL);
```  
  
### <a name="parameters"></a>参数  
 [out] `pScrollInfo`  
 指向[SCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb787537)结构或`NULL`。 此方法返回时，并且此参数不是`NULL`，该结构包含滚动条的所有参数。 默认值为 `NULL`。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果此方法成功，则否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法会影响显示平面选项卡的选项卡控件。 滚动条在同一时间会影响所有选项卡。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CDockablePane 类](../../mfc/reference/cdockablepane-class.md)   
 [CDockablePane 类](../../mfc/reference/cdockablepane-class.md)   
 [CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)

