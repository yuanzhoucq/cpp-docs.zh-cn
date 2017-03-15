---
title: "CMFCBaseTabCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCBaseTabCtrl
dev_langs:
- C++
helpviewer_keywords:
- CMFCBaseTabCtrl class
ms.assetid: 7270c55f-6f6e-4dd2-b0d2-291afeac3882
caps.latest.revision: 41
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: d82cde70595bf6d7a4629f54cc48e2b422cd5e8c
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcbasetabctrl-class"></a>CMFCBaseTabCtrl 类
实现选项卡式窗口的基本功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCBaseTabCtrl : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCBaseTabCtrl::AddIcon](#addicon)||  
|[Cmfcbasetabctrl:: Addtab](#addtab)|向选项卡式窗口添加新选项卡。|  
|[CMFCBaseTabCtrl::ApplyRestoredTabInfo](#applyrestoredtabinfo)||  
|[CMFCBaseTabCtrl::AutoDestroyWindow](#autodestroywindow)||  
|[CMFCBaseTabCtrl::CalcRectEdit](#calcrectedit)||  
|[CMFCBaseTabCtrl::CleanUp](#cleanup)||  
|[CMFCBaseTabCtrl::ClearImageList](#clearimagelist)||  
|[CMFCBaseTabCtrl::DetachTab](#detachtab)|从选项卡式窗口分离选项卡。|  
|[CMFCBaseTabCtrl::EnableActivateLastActive](#enableactivatelastactive)||  
|[CMFCBaseTabCtrl::EnableAutoColor](#enableautocolor)|启用或禁用自动选项卡着色。|  
|[CMFCBaseTabCtrl::EnableCustomToolTips](#enablecustomtooltips)|启用或禁用选项卡的自定义工具提示。|  
|[CMFCBaseTabCtrl::EnableInPlaceEdit](#enableinplaceedit)|启用或禁用直接编辑选项卡标签。|  
|[CMFCBaseTabCtrl::EnableTabDetach](#enabletabdetach)|启用可拆分选项卡。|  
|[Cmfcbasetabctrl:: Enabletabswap](#enabletabswap)|启用或禁用用户是否可以使用鼠标更改选项卡顺序。|  
|[CMFCBaseTabCtrl::EnsureVisible](#ensurevisible)|滚动选项卡，直到指定选项卡可见。 如果指定选项卡已经可见，则此方法无效。|  
|[CMFCBaseTabCtrl::EnterDragMode](#enterdragmode)||  
|[CMFCBaseTabCtrl::FindTargetWnd](#findtargetwnd)|返回包含指定点的窗格。|  
|[CMFCBaseTabCtrl::FireChangeActiveTab](#firechangeactivetab)||  
|[CMFCBaseTabCtrl::FireChangingActiveTab](#firechangingactivetab)||  
|[CMFCBaseTabCtrl::GetActiveTab](#getactivetab)|返回活动选项卡的索引。|  
|[CMFCBaseTabCtrl::GetActiveTabColor](#getactivetabcolor)|返回活动选项卡的背景色。|  
|[CMFCBaseTabCtrl::GetActiveTabTextColor](#getactivetabtextcolor)|返回活动选项卡的文本颜色。|  
|[CMFCBaseTabCtrl::GetActiveWnd](#getactivewnd)|返回指向选项卡控件的活动页面的指针。|  
|[CMFCBaseTabCtrl::GetAutoColors](#getautocolors)|返回对用于自动着色的颜色数组的引用。|  
|[CMFCBaseTabCtrl::GetFirstVisibleTab](#getfirstvisibletab)|返回指向第一个可见选项卡的指针。|  
|[CMFCBaseTabCtrl::GetFirstVisibleTabNum](#getfirstvisibletabnum)||  
|[CMFCBaseTabCtrl::GetHighlightedTab](#gethighlightedtab)|返回当前突出显示的选项卡的索引。|  
|[CMFCBaseTabCtrl::GetImageList](#getimagelist)||  
|[CMFCBaseTabCtrl::GetImageSize](#getimagesize)||  
|[CMFCBaseTabCtrl::GetLastVisibleTab](#getlastvisibletab)||  
|[CMFCBaseTabCtrl::GetLocation](#getlocation)|返回指示相对于选项卡控件定位的选项卡区域的 LOCATION 数据类型的变量。 例如位于顶部或底部。|  
|[CMFCBaseTabCtrl::GetMaxWindowSize](#getmaxwindowsize)||  
|[CMFCBaseTabCtrl::GetTabArea](#gettabarea)|返回选项卡区域在选项卡式窗口中的大小和位置。 使用坐标定义选项卡区域的位置。|  
|[CMFCBaseTabCtrl::GetTabBkColor](#gettabbkcolor)|返回指定选项卡的背景色。|  
|[CMFCBaseTabCtrl::GetTabBorderSize](#gettabbordersize)|返回选项卡控件中选项卡边框的大小。|  
|[CMFCBaseTabCtrl::GetTabByID](#gettabbyid)|返回由指定 ID 标识的选项卡的索引。|  
|[CMFCBaseTabCtrl::GetTabCloseButton](#gettabclosebutton)||  
|[CMFCBaseTabCtrl::GetTabFromHwnd](#gettabfromhwnd)|返回包含指定 HWND 对象的选项卡的索引。|  
|[CMFCBaseTabCtrl::GetTabFromPoint](#gettabfrompoint)|返回包含指定点的选项卡。|  
|[CMFCBaseTabCtrl::GetTabFullWidth](#gettabfullwidth)||  
|[CMFCBaseTabCtrl::GetTabHicon](#gettabhicon)|返回与指定选项卡关联的图标。|  
|[CMFCBaseTabCtrl::GetTabID](#gettabid)|使用选项卡索引返回选项卡 ID。|  
|[CMFCBaseTabCtrl::GetTabIcon](#gettabicon)|返回指定选项卡的图标 ID。|  
|[CMFCBaseTabCtrl::GetTabLabel](#gettablabel)|返回指定选项卡的文本。|  
|[CMFCBaseTabCtrl::GetTabRect](#gettabrect)|检索指定选项卡的大小和位置。|  
|[CMFCBaseTabCtrl::GetTabsHeight](#gettabsheight)||  
|[CMFCBaseTabCtrl::GetTabsRect](#gettabsrect)||  
|[CMFCBaseTabCtrl::GetTabTextColor](#gettabtextcolor)|返回指定选项卡的文本颜色。|  
|[CMFCBaseTabCtrl::GetTabWnd](#gettabwnd)|返回指向驻留在指定选项卡页上的窗格的指针。|  
|[CMFCBaseTabCtrl::GetTabWndNoWrapper](#gettabwndnowrapper)|返回指向驻留在指定选项卡页上的控件的直接指针，即使该控件具有包装。|  
|[CMFCBaseTabCtrl::GetTabsNum](#gettabsnum)|返回选项卡控件中包含的选项卡的数目。|  
|[CMFCBaseTabCtrl::GetToolTipCtrl](#gettooltipctrl)|返回对与 `CMFCBaseTabCtrl` 对象关联的工具提示控件的引用。|  
|[CMFCBaseTabCtrl::GetVisibleTabsNum](#getvisibletabsnum)|返回可见选项卡的数目。|  
|[CMFCBaseTabCtrl::HasImage](#hasimage)||  
|[CMFCBaseTabCtrl::HideSingleTab](#hidesingletab)|设置隐藏窗口选项卡的选项，但仅当选项卡式窗口只显示一个可见选项卡时设置。|  
|[Cmfcbasetabctrl:: Inserttab](#inserttab)|插入新选项卡。|  
|[CMFCBaseTabCtrl::InvalidateTab](#invalidatetab)||  
|[CMFCBaseTabCtrl::IsActiveTabCloseButton](#isactivetabclosebutton)||  
|[CMFCBaseTabCtrl::IsAutoColor](#isautocolor)|返回一个值，用于指示选项卡式窗口是否处于自动配色模式。|  
|[CMFCBaseTabCtrl::IsAutoDestroyWindow](#isautodestroywindow)||  
|[CMFCBaseTabCtrl::IsColored](#iscolored)||  
|[CMFCBaseTabCtrl::IsDialogControl](#isdialogcontrol)||  
|[CMFCBaseTabCtrl::IsDrawNoPrefix](#isdrawnoprefix)||  
|[CMFCBaseTabCtrl::IsFlatFrame](#isflatframe)|返回一个值，用于指示选项卡区域的框架是平面的还是 3D 的。|  
|[CMFCBaseTabCtrl::IsFlatTab](#isflattab)||  
|[CMFCBaseTabCtrl::IsHideSingleTab](#ishidesingletab)|返回一个值，用于指示选项卡控件是否配置为隐藏选项卡，但仅当选项卡式窗口只具有一个可见选项卡时设置。|  
|[CMFCBaseTabCtrl::IsIconAdded](#isiconadded)||  
|[CMFCBaseTabCtrl::IsInPlaceEdit](#isinplaceedit)|指示用户是否可以修改选项卡上的标签。|  
|[CMFCBaseTabCtrl::IsLeftRightRounded](#isleftrightrounded)||  
|[CMFCBaseTabCtrl::IsMDITab](#ismditab)||  
|[CMFCBaseTabCtrl::IsOneNoteStyle](#isonenotestyle)|指示选项卡式窗口是否以 Microsoft OneNote 样式显示选项卡。|  
|[CMFCBaseTabCtrl::IsPtInTabArea](#isptintabarea)|检查选项卡区域中是否存在指定的点。|  
|[CMFCBaseTabCtrl::IsTabCloseButtonHighlighted](#istabclosebuttonhighlighted)||  
|[CMFCBaseTabCtrl::IsTabCloseButtonPressed](#istabclosebuttonpressed)||  
|[CMFCBaseTabCtrl::IsTabDetachable](#istabdetachable)|指示选项卡是否可拆分。|  
|[CMFCBaseTabCtrl::IsTabIconOnly](#istabicononly)|指示选项卡是否显示图标而不显示标签。|  
|[CMFCBaseTabCtrl::IsTabSwapEnabled](#istabswapenabled)|指示用户是否可以通过拖动选项卡来更改选项卡位置。|  
|[CMFCBaseTabCtrl::IsTabVisible](#istabvisible)|指示指定选项卡是否可见。|  
|[CMFCBaseTabCtrl::IsVS2005Style](#isvs2005style)||  
|[CMFCBaseTabCtrl::MoveTab](#movetab)||  
|[CMFCBaseTabCtrl::OnChangeTabs](#onchangetabs)|选项卡数量更改时由框架调用。|  
|[CMFCBaseTabCtrl::OnDragEnter](#ondragenter)||  
|[CMFCBaseTabCtrl::OnDragLeave](#ondragleave)||  
|[CMFCBaseTabCtrl::OnDragOver](#ondragover)||  
|[CMFCBaseTabCtrl::OnDrop](#ondrop)||  
|[CMFCBaseTabCtrl::OnRenameTab](#onrenametab)||  
|[CMFCBaseTabCtrl::PreTranslateMessage](#pretranslatemessage)|类使用[CWinApp](../../mfc/reference/cwinapp-class.md)将窗口消息转换之前调度到[TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955)和[DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函数。 (重写[cwnd:: Pretranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|  
|[CMFCBaseTabCtrl::RecalcLayout](#recalclayout)|重新计算选项卡式窗口的内部布局。|  
|[CMFCBaseTabCtrl::RemoveAllTabs](#removealltabs)|从选项卡式窗口中移除所有选项卡。|  
|[CMFCBaseTabCtrl::RemoveTab](#removetab)|从选项卡式窗口中移除一个选项卡。|  
|[CMFCBaseTabCtrl::RenameTab](#renametab)||  
|[CMFCBaseTabCtrl::ResetImageList](#resetimagelist)|重置附加到选项卡式窗口的图像列表。|  
|[CMFCBaseTabCtrl::Serialize](#serialize)|从存档读取该对象或将该对象写入存档。 (重写[cobject:: Serialize](../../mfc/reference/cobject-class.md#serialize)。)|  
|[CMFCBaseTabCtrl::SetActiveTab](#setactivetab)|激活选项卡。|  
|[CMFCBaseTabCtrl::SetActiveTabColor](#setactivetabcolor)|设置当前活动选项卡的背景色。|  
|[CMFCBaseTabCtrl::SetActiveTabTextColor](#setactivetabtextcolor)|设置活动选项卡的文本颜色。|  
|[CMFCBaseTabCtrl::SetAutoColors](#setautocolors)|设置应用到自动配色模式中的选项卡控件颜色。|  
|[:: Setdockingbarwrapperrtc](#setdockingbarwrapperrtc)|设置用于不从派生的任何对象的包装类[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)。|  
|[CMFCBaseTabCtrl::SetDrawNoPrefix](#setdrawnoprefix)|启用和禁用绘制选项卡标签时前缀字符的处理。|  
|[CMFCBaseTabCtrl::SetImageList](#setimagelist)|设置图标图像列表。|  
|[CMFCBaseTabCtrl::SetLocation](#setlocation)||  
|[CMFCBaseTabCtrl::SetTabBkColor](#settabbkcolor)|设置指定选项卡的背景色。|  
|[CMFCBaseTabCtrl::SetTabBorderSize](#settabbordersize)|设置新的选项卡边框大小。|  
|[CMFCBaseTabCtrl::SetTabHicon](#settabhicon)|设置选项卡图标。|  
|[CMFCBaseTabCtrl::SetTabIcon](#settabicon)|设置选项卡图标 ID。|  
|[CMFCBaseTabCtrl::SetTabIconOnly](#settabicononly)|为指定选项卡启用和禁用“仅图标”模式。|  
|[CMFCBaseTabCtrl::SetTabLabel](#settablabel)|将选项卡标签设置为等于指定的字符串值。|  
|[CMFCBaseTabCtrl::SetTabsHeight](#settabsheight)||  
|[CMFCBaseTabCtrl::SetTabTextColor](#settabtextcolor)|为指定选项卡设置文本颜色。|  
|[CMFCBaseTabCtrl::SetTabsOrder](#settabsorder)|按照指定的顺序排列选项卡。|  
|[CMFCBaseTabCtrl::ShowTab](#showtab)|显示或隐藏指定的选项卡。|  
|[CMFCBaseTabCtrl::StartRenameTab](#startrenametab)||  
|[CMFCBaseTabCtrl::SwapTabs](#swaptabs)||  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCBaseTabCtrl::CreateWrapper](#createwrapper)|创建一个派生自包装[CWnd](../../mfc/reference/cwnd-class.md)不源自`CDockablePane`。 若要停靠 `CMFCBaseTabCtrl` 对象，则每个嵌入的控件必须具有停靠包装或派生自 `CDockablePane`。<br /><br /> 通过使用 `SetDockingBayWrapperRTC`设置包装的类。|  
  
### <a name="data-members"></a>数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCBaseTabCtrl::m_bActivateTabOnRightClick](#m_bactivatetabonrightclick)|指定是通过单击鼠标左键还是单击鼠标右键来选择选项卡。|  
|[CMFCBaseTabCtrl::m_bAutoDestroyWindow](#m_bautodestroywindow)|指定是否自动销毁选项卡中包含的窗格。|  
  
## <a name="remarks"></a>备注  
 `CMFCBaseTabCtrl` 类是抽象类。 因此，不能将它实例化。 若要创建选项卡式窗口，则必须从 `CMFCBaseTabCtrl`派生类。 MFC 库包含一些派生的类的示例，其中两个是[CMFCTabCtrl 类](../../mfc/reference/cmfctabctrl-class.md)和[CMFCOutlookBarTabCtrl 类](../../mfc/reference/cmfcoutlookbartabctrl-class.md)。  
  
 从 [!INCLUDE[vs_dev14](../../ide/includes/vs_dev14_md.md)] 开始，此类支持 Microsoft Active Accessibility。  
  
## <a name="customization-tips"></a>自定义提示  
 以下提示适用于`CMFCBaseTabCtrl Class`和从其继承的任何类︰  
  
-   如果启用可拆分选项卡，请勿保留指向选项卡式窗口的指针。 这些可拆分选项卡可以动态创建和销毁。 因此，指针可能会变为无效。  
  
-   可以配置选项卡控件，使用户可以通过使用鼠标动态移动选项卡控件上的选项卡。 此功能已内置于 `CMFCBaseTabCtrl` 类。 若要启用它，请调用[cmfcbasetabctrl:: Enabletabswap](#enabletabswap)。  
  
-   默认情况下，将选项卡添加到选项卡控件时，选项卡是可拆分的。 此外可以通过使用添加非可拆分的选项卡[cmfcbasetabctrl:: Addtab](#addtab)。 如果将 `bDetachable` 参数设置为 `FALSE`，则选项卡将不可拆分。 您还可以更改选项卡是否可拆分，通过调用方法[CMFCBaseTabCtrl::EnableTabDetach](#enabletabdetach)。  
  
-   派生自的对象[CWnd 类](../../mfc/reference/cwnd-class.md)可以置于可停靠控件条或可停靠选项卡。 要停靠整个控件，则必须使 `CWnd` 对象可停靠。 MFC 使用一个包装类实现此目的。 此包装类是[CDockablePaneAdapter 类](../../mfc/reference/cdockablepaneadapter-class.md)。 添加到可停靠控件条或可停靠选项卡上的任何 `CWnd` 对象将被包装到 `CDockablePaneAdapter` 对象中。 可以通过将 `m_bEnableWrapping` 对象的 `CMFCBaseTablCtrl` 参数设置为 `FALSE`来禁用自动包装。 您还可以更改您的应用程序使用的方法将用作包装器类[:: Setdockingbarwrapperrtc](#setdockingbarwrapperrtc)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxbasetabctrl.h  
  
##  <a name="a-nameaddicona--cmfcbasetabctrladdicon"></a><a name="addicon"></a>CMFCBaseTabCtrl::AddIcon  
 将图标添加到列表中的受保护的图标`CMap``m_mapAddedIcons`成员。  
  
```  
void AddIcon(
    HICON hIcon,  
    int iIcon);
```  
  
### <a name="parameters"></a>参数  
 [in] `hIcon`  
 指向要添加的图标的句柄。  
  
 [in] `iIcon`  
 在受保护的图标的从零开始索引`CImageList``m_Images`成员。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameaddtaba--cmfcbasetabctrladdtab"></a><a name="addtab"></a>Cmfcbasetabctrl:: Addtab  
 将一个新选项卡添加到选项卡控件。  
  
```  
virtual void AddTab(
    CWnd* pTabWnd,  
    LPCTSTR lpszTabLabel,  
    UINT uiImageId = (UINT)-1,,  
    BOOL bDetachable = TRUE);

 
virtual void AddTab(
    CWnd* pTabWnd,  
    UINT uiResTabLabel,  
    UINT uiImageId = (UINT)-1,  
    BOOL bDetachable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pTabWnd`  
 指向此方法表示为一个新选项卡的窗口的指针。  
  
 [in] `lpszTabLabel`  
 一个字符串，包含用于新选项卡的标签。  
  
 [in] `uiImageId`  
 从图像列表的图像 ID。 选项卡控件用作此图像图标的新选项卡。  
  
 [in] `uiResTabLabel`  
 标签的资源 ID。  
  
 [in] `bDetachable`  
 一个布尔型参数，用于确定新选项卡是否可拆分。  
  
### <a name="remarks"></a>备注  
 如果`pTabWnd`指向一个对象，不源自[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)并且如果`bDetachable`是`TRUE`，框架会自动创建的包装`pTabWnd`对象。 使用包装，可以`pTabWnd`可拆分的对象。 默认情况下，此包装属于实例[CDockablePaneAdapter 类](../../mfc/reference/cdockablepaneadapter-class.md)。 如果提供的默认包装功能不可接受，请使用[:: Setdockingbarwrapperrtc](#setdockingbarwrapperrtc)方法，以指定不同的包装器。  
  
##  <a name="a-nameapplyrestoredtabinfoa--cmfcbasetabctrlapplyrestoredtabinfo"></a><a name="applyrestoredtabinfo"></a>CMFCBaseTabCtrl::ApplyRestoredTabInfo  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bUseTabIndexes`  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameautodestroywindowa--cmfcbasetabctrlautodestroywindow"></a><a name="autodestroywindow"></a>CMFCBaseTabCtrl::AutoDestroyWindow  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void AutoDestroyWindow(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bAutoDestroy`  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namecalcrectedita--cmfcbasetabctrlcalcrectedit"></a><a name="calcrectedit"></a>CMFCBaseTabCtrl::CalcRectEdit  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void CalcRectEdit(CRect& rectEdit);
```  
  
### <a name="parameters"></a>参数  
 [in] `rectEdit`  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namecleanupa--cmfcbasetabctrlcleanup"></a><a name="cleanup"></a>CMFCBaseTabCtrl::CleanUp  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void CleanUp();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameclearimagelista--cmfcbasetabctrlclearimagelist"></a><a name="clearimagelist"></a>CMFCBaseTabCtrl::ClearImageList  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void ClearImageList();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namecreatewrappera--cmfcbasetabctrlcreatewrapper"></a><a name="createwrapper"></a>CMFCBaseTabCtrl::CreateWrapper  
 创建派生自的框架窗口的包装[CWnd 类](../../mfc/reference/cwnd-class.md)但不源自[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)。  
  
```  
virtual CWnd* CreateWrapper(
    CWnd* pWndToWrap,  
    LPCTSTR lpszTabLabel,  
    BOOL bDetachable);
```  
  
### <a name="parameters"></a>参数  
 [in] `pWndToWrap`  
 指向包装的框架窗口的指针。  
  
 [in] `lpszTabLabel`  
 一个字符串，包含窗口中的标签。  
  
 [in] `bDetachable`  
 一个布尔型参数，该值指示窗口是否可拆分。  
  
### <a name="return-value"></a>返回值  
 指向包装派生自`CDockablePane`类如果`CreateWrapper`成功创建了一个包装类`pWndToWrap`。 如果此方法失败，其形式返回`pWndToWrap`。  
  
### <a name="remarks"></a>备注  
 选项卡式的窗口可以将任何对象，派生自停靠`CWnd`。 但是，在使`CMFCBaseTabCtrl Class`对象可停靠，每个对象上的`CMFCBaseTabCtrl`必须是可拆分。 因此，`CMFCBaseTabCtrl`自动换行不从派生的任何对象`CDockablePane`。  
  
 默认情况下，`CMFCBaseTabCtrl`创建的实例[CDockablePaneAdapter 类](../../mfc/reference/cdockablepaneadapter-class.md)。 若要更改包装器的默认类，请调用[:: Setdockingbarwrapperrtc](#setdockingbarwrapperrtc)。  
  
 如果`pWndToWrap`派生自`CDockablePane`，此方法不会创建一个包装。 相反，它将失败并返回`pWndToWrap`。  
  
##  <a name="a-namedetachtaba--cmfcbasetabctrldetachtab"></a><a name="detachtab"></a>CMFCBaseTabCtrl::DetachTab  
 框架调用此方法以分离从选项卡控件的选项卡。  
  
```  
virtual BOOL DetachTab(
    AFX_DOCK_METHOD dockMethod,  
    int nTabNum = -1,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `dockMethod`  
 枚举的数据类型提供的[CBasePane 类](../../mfc/reference/cbasepane-class.md)。 此数据类型指定用于拆分选项卡的方法。  
  
 [in] `nTabNum`  
 选项卡要分离的从零开始索引。  
  
 [in] `bHide`  
 一个布尔型参数，该值指示框架是否应隐藏分离选项卡。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 如果选项卡指定`nTabNum`是可拆分，此函数将失败并返回`FALSE`。  
  
##  <a name="a-nameenableactivatelastactivea--cmfcbasetabctrlenableactivatelastactive"></a><a name="enableactivatelastactive"></a>CMFCBaseTabCtrl::EnableActivateLastActive  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void EnableActivateLastActive(BOOL bLastActive = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bLastActive`  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameenableautocolora--cmfcbasetabctrlenableautocolor"></a><a name="enableautocolor"></a>CMFCBaseTabCtrl::EnableAutoColor  
 控制在绘制一个选项卡时，框架是否使用自动背景色。  
  
```  
void EnableAutoColor(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 一个布尔型参数，用于确定框架是否使用自动颜色。  
  
### <a name="remarks"></a>备注  
 选项卡控件有几个预定义颜色的一个数组。 当框架使用自动颜色时，在一系列选项卡中的每个选项卡从此数组分配下一步的颜色。  
  
 默认情况下，库定义的颜色由确定自动颜色。 您可以通过调用提供一个自定义的颜色数组[CMFCBaseTabCtrl::SetAutoColors](#setautocolors)。  
  
##  <a name="a-nameenablecustomtooltipsa--cmfcbasetabctrlenablecustomtooltips"></a><a name="enablecustomtooltips"></a>CMFCBaseTabCtrl::EnableCustomToolTips  
 使选项卡控件的自定义工具提示。  
  
```  
BOOL EnableCustomToolTips(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 一个布尔值，确定是否使用自定义工具提示。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 `TRUE`；否则为 `FALSE`。  
  
### <a name="remarks"></a>备注  
 如果启用了自定义工具提示，选项卡控件将发送`AFX_WM_ON_GET_TAB_TOOLTIP`到主框架的消息。 如果您想要在您的应用程序中支持自定义工具提示，主框架窗口必须处理此方法，并提供自定义工具提示文本。 有关提供自定义工具提示文本的详细信息，请参阅[CMFCTabToolTipInfo 结构](../../mfc/reference/cmfctabtooltipinfo-structure.md)。  
  
##  <a name="a-nameenableinplaceedita--cmfcbasetabctrlenableinplaceedit"></a><a name="enableinplaceedit"></a>CMFCBaseTabCtrl::EnableInPlaceEdit  
 使你能够直接编辑用户选项卡标签。  
  
```  
virtual void EnableInPlaceEdit(BOOL bEnable) = 0;  
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 一个布尔型参数，用于指定是否启用直接编辑选项卡标签。  
  
### <a name="remarks"></a>备注  
 默认情况下，为选项卡控件禁用直接编辑选项卡标签。  
  
 您可以启用直接编辑选项卡上选项卡控件的子集。 若要执行此操作，重写该方法`CMFCBaseTabCtrl::StartRenameTab`。 `StartRenameTab`应返回一个非零值支持直接编辑选项卡标签的所有选项卡。  
  
 在`CMFCBaseTabCtrl Class`，此方法是纯虚函数，没有实现。 如果您从派生类`CMFCBaseTabCtrl`，您必须实现此函数。  
  
##  <a name="a-nameenabletabdetacha--cmfcbasetabctrlenabletabdetach"></a><a name="enabletabdetach"></a>CMFCBaseTabCtrl::EnableTabDetach  
 启用可拆分选项卡。  
  
```  
virtual BOOL EnableTabDetach(
    int iTab,  
    BOOL bEnable);
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 选项卡的从零开始索引。  
  
 [in] `bEnable`  
 一个布尔值，该值指示是否使可拆分的选项卡。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 `TRUE`；否则为 `FALSE`。  
  
##  <a name="a-nameenabletabswapa--cmfcbasetabctrlenabletabswap"></a><a name="enabletabswap"></a>Cmfcbasetabctrl:: Enabletabswap  
 使用户能够更改使用鼠标的 tab 键顺序。  
  
```  
void EnableTabSwap(BOOL bEnable);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 一个布尔值，该值指示是否启用选项卡上交换。  
  
### <a name="remarks"></a>备注  
 启用选项卡上交换后，用户可以拖动选项卡并更改其选项卡控件中的相对位置。  
  
##  <a name="a-nameensurevisiblea--cmfcbasetabctrlensurevisible"></a><a name="ensurevisible"></a>CMFCBaseTabCtrl::EnsureVisible  
 滚动选项卡，直到指定选项卡可见。  
  
```  
virtual BOOL EnsureVisible(int iTab);
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 选项卡的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此方法如果不起作用选项卡由`iTab`已经可见。  
  
 默认情况下，此方法不支持通过`CMFCBaseTabCtrl Class`。 您应在从派生的自定义类中实现此函数`CMFCBaseTabCtrl`如果该自定义选项卡控件支持选项卡上滚动。 此方法支持通过[CMFCTabCtrl 类](../../mfc/reference/cmfctabctrl-class.md)。  
  
##  <a name="a-nameenterdragmodea--cmfcbasetabctrlenterdragmode"></a><a name="enterdragmode"></a>CMFCBaseTabCtrl::EnterDragMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void EnterDragMode();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namefindtargetwnda--cmfcbasetabctrlfindtargetwnd"></a><a name="findtargetwnd"></a>CMFCBaseTabCtrl::FindTargetWnd  
 标识包含指定的点的窗格。  
  
```  
virtual CWnd* FindTargetWnd(const CPoint& pt) = 0;  
```  
  
### <a name="parameters"></a>参数  
 [in] `pt`  
 使用客户端区域的定义了一个点坐标[CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)对象。  
  
### <a name="return-value"></a>返回值  
 一个指向[CWnd](../../mfc/reference/cwnd-class.md)对象成功，否则为如果`NULL`。  
  
### <a name="remarks"></a>备注  
 在`CMFCBaseTabCtrl`类，此方法是纯虚函数︰ 如果您从派生类必须实现它`CMFCBaseTabCtrl`。  
  
##  <a name="a-namefirechangeactivetaba--cmfcbasetabctrlfirechangeactivetab"></a><a name="firechangeactivetab"></a>CMFCBaseTabCtrl::FireChangeActiveTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void FireChangeActiveTab(int nNewTab);
```  
  
### <a name="parameters"></a>参数  
 [in] `nNewTab`  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namefirechangingactivetaba--cmfcbasetabctrlfirechangingactivetab"></a><a name="firechangingactivetab"></a>CMFCBaseTabCtrl::FireChangingActiveTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL FireChangingActiveTab(int nNewTab);
```  
  
### <a name="parameters"></a>参数  
 [in] `nNewTab`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetactivetaba--cmfcbasetabctrlgetactivetab"></a><a name="getactivetab"></a>CMFCBaseTabCtrl::GetActiveTab  
 检索当前处于活动状态的选项卡的索引。  
  
```  
virtual int GetActiveTab() const;  
```  
  
### <a name="return-value"></a>返回值  
 活动选项卡; 的从零开始的索引如果没有活动的选项卡，则为-1。  
  
##  <a name="a-namegetactivetabcolora--cmfcbasetabctrlgetactivetabcolor"></a><a name="getactivetabcolor"></a>CMFCBaseTabCtrl::GetActiveTabColor  
 检索当前处于活动状态选项卡的背景色。  
  
```  
virtual COLORREF GetActiveTabColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，该值指定活动选项卡的背景色。  
  
### <a name="remarks"></a>备注  
 默认情况下，活动选项卡的背景色是`COLOR_WINDOW`。 可以使用该方法来更改活动选项卡的背景色[CMFCBaseTabCtrl::SetActiveTabColor](#setactivetabcolor)。  
  
##  <a name="a-namegetactivetabtextcolora--cmfcbasetabctrlgetactivetabtextcolor"></a><a name="getactivetabtextcolor"></a>CMFCBaseTabCtrl::GetActiveTabTextColor  
 检索活动选项卡的文本颜色。  
  
```  
virtual COLORREF GetActiveTabTextColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，该值指定活动选项卡的文本颜色。  
  
### <a name="remarks"></a>备注  
 默认情况下，活动选项卡的文本颜色为`COLOR_WINDOWTEXT`。 您可以使用该方法更改文本颜色[CMFCBaseTabCtrl::SetActiveTabTextColor](#setactivetabtextcolor)。  
  
##  <a name="a-namegetactivewnda--cmfcbasetabctrlgetactivewnd"></a><a name="getactivewnd"></a>CMFCBaseTabCtrl::GetActiveWnd  
 检索指向当前处于活动状态的选项卡窗口的指针。  
  
```  
virtual CWnd* GetActiveWnd() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向窗口的指针。  
  
##  <a name="a-namegetautocolorsa--cmfcbasetabctrlgetautocolors"></a><a name="getautocolors"></a>CMFCBaseTabCtrl::GetAutoColors  
 检索用于自动着色的颜色的数组。  
  
```  
const CArray<COLORREF,COLORREF>& GetAutoColors() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向数组的引用[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值[CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)对象将用于自动选项卡着色。  
  
### <a name="remarks"></a>备注  
 默认情况下，框架将初始化为库定义的颜色的颜色的数组。 您可以通过调用方法提供一个自定义的颜色数组[CMFCBaseTabCtrl::SetAutoColors](#setautocolors)。  
  
##  <a name="a-namegetfirstvisibletaba--cmfcbasetabctrlgetfirstvisibletab"></a><a name="getfirstvisibletab"></a>CMFCBaseTabCtrl::GetFirstVisibleTab  
 检索指向第一个可见选项卡。  
  
```  
virtual CWnd* GetFirstVisibleTab(int& iTabNum);

 
virtual CWnd* GetFirstVisibleTab(
    int iStartFrom,  
    int& iTabNum);
```  
  
### <a name="parameters"></a>参数  
 [out] `iTabNum`  
 对整数的引用。 此方法将写入此参数的第一个可见选项卡的从零开始索引。  
  
 [in] `iStartFrom`  
 第一个选项卡中，若要检查的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 第一个可见选项卡如果成功，则指向的指针否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 如果此方法将失败，则它写入到的值为-1 `iStartFrom`。  
  
 如果`iStartFrom`大于或等于在选项卡控件中，选项卡的数目`GetFirstVisibleTab`自动失败。  
  
##  <a name="a-namegetfirstvisibletabnuma--cmfcbasetabctrlgetfirstvisibletabnum"></a><a name="getfirstvisibletabnum"></a>CMFCBaseTabCtrl::GetFirstVisibleTabNum  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetFirstVisibleTabNum() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegethighlightedtaba--cmfcbasetabctrlgethighlightedtab"></a><a name="gethighlightedtab"></a>CMFCBaseTabCtrl::GetHighlightedTab  
 检索当前突出显示的选项卡的索引。  
  
```  
int GetHighlightedTab() const;  
```  
  
### <a name="return-value"></a>返回值  
 突出显示的选项卡的从零开始索引。  
  
##  <a name="a-namegetimagelista--cmfcbasetabctrlgetimagelist"></a><a name="getimagelist"></a>CMFCBaseTabCtrl::GetImageList  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual const CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetimagesizea--cmfcbasetabctrlgetimagesize"></a><a name="getimagesize"></a>CMFCBaseTabCtrl::GetImageSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetImageSize() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetlastvisibletaba--cmfcbasetabctrlgetlastvisibletab"></a><a name="getlastvisibletab"></a>CMFCBaseTabCtrl::GetLastVisibleTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CWnd* GetLastVisibleTab(int& iTabNum);
```  
  
### <a name="parameters"></a>参数  
 [in] `iTabNum`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegetlocationa--cmfcbasetabctrlgetlocation"></a><a name="getlocation"></a>CMFCBaseTabCtrl::GetLocation  
 检索的选项卡控件的选项卡区域部分的位置。  
  
```  
Location GetLocation() const;  
```  
  
### <a name="return-value"></a>返回值  
 选项卡区域的位置。  
  
### <a name="remarks"></a>备注  
 可能的选项卡区域位置值为`LOCATION_BOTTOM`和`LOCATION_TOP`。  
  
##  <a name="a-namegetmaxwindowsizea--cmfcbasetabctrlgetmaxwindowsize"></a><a name="getmaxwindowsize"></a>CMFCBaseTabCtrl::GetMaxWindowSize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual CSize GetMaxWindowSize() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegettabareaa--cmfcbasetabctrlgettabarea"></a><a name="gettabarea"></a>CMFCBaseTabCtrl::GetTabArea  
 检索的大小和选项卡控件的选项卡区域的位置。  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const = 0;  
```  
  
### <a name="parameters"></a>参数  
 [in] `rectTabAreaTop`  
 对 `CRect` 对象的引用。 `GetTabArea`使用此对象存储大小和顶部的选项卡区域的位置。  
  
 [in] `rectTabAreaBottom`  
 对 `CRect` 对象的引用。 `GetTabArea`使用此对象存储大小和底部的选项卡区域的位置。  
  
### <a name="remarks"></a>备注  
 之后`GetTabArea`返回时，`CRect`参数包含的大小和位置的选项卡区域在选项卡控件的工作区坐标。 在顶部或底部的选项卡控件没有选项卡区域是否`rectTabAreaTop`或`rectTabAreaBottom`为空。  
  
 在`CMFCBaseTabCtrl Class`，此方法是纯虚函数，没有实现。 如果您从派生类`CMFCBaseTabCtrl`，您必须实现此函数。  
  
##  <a name="a-namegettabbkcolora--cmfcbasetabctrlgettabbkcolor"></a><a name="gettabbkcolor"></a>CMFCBaseTabCtrl::GetTabBkColor  
 检索指定的选项卡的背景色。  
  
```  
virtual COLORREF GetTabBkColor(int iTab) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 选项卡的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 一个[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，该值指示指定的选项卡的背景色; 则为-1`iTab`超出范围。  
  
##  <a name="a-namegettabbordersizea--cmfcbasetabctrlgettabbordersize"></a><a name="gettabbordersize"></a>CMFCBaseTabCtrl::GetTabBorderSize  
 检索选项卡控件中的选项卡边框的大小。  
  
```  
virtual int GetTabBorderSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 选项卡边框，以像素为单位的大小。  
  
### <a name="remarks"></a>备注  
 选项卡边框的默认大小为三个像素。 您可以使用该方法更改此边框大小[CMFCBaseTabCtrl::SetTabBorderSize](#settabbordersize)。  
  
##  <a name="a-namegettabbyida--cmfcbasetabctrlgettabbyid"></a><a name="gettabbyid"></a>CMFCBaseTabCtrl::GetTabByID  
 检索基于选项卡 ID 的选项卡的索引  
  
```  
virtual int GetTabByID(int id) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `id`  
 一个选项卡上的 id。  
  
### <a name="return-value"></a>返回值  
 如果它找到，则选项卡的从零开始的索引如果没有找到该选项卡 ID，则为-1。  
  
### <a name="remarks"></a>备注  
 选项卡 Id 时自动分配到选项卡控件添加选项卡。  
  
##  <a name="a-namegettabclosebuttona--cmfcbasetabctrlgettabclosebutton"></a><a name="gettabclosebutton"></a>CMFCBaseTabCtrl::GetTabCloseButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CRect GetTabCloseButton() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegettabfromhwnda--cmfcbasetabctrlgettabfromhwnd"></a><a name="gettabfromhwnd"></a>CMFCBaseTabCtrl::GetTabFromHwnd  
 检索包含指定的 HWND 对象的选项卡的索引。  
  
```  
virtual int GetTabFromHwnd(HWND hwnd) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `hwnd`  
 窗口的句柄。  
  
### <a name="return-value"></a>返回值  
 如果成功，则该选项卡的从零开始的索引如果没有选项卡包含-1 `hwnd`。  
  
##  <a name="a-namegettabfrompointa--cmfcbasetabctrlgettabfrompoint"></a><a name="gettabfrompoint"></a>CMFCBaseTabCtrl::GetTabFromPoint  
 检索包含指定的点的选项卡。  
  
```  
virtual int GetTabFromPoint(CPoint& pt) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `pt`  
 选项卡控件的工作区坐标中的点。  
  
### <a name="return-value"></a>返回值  
 包含的选项卡的索引`pt`;-1，如果没有选项卡包含`pt`。  
  
##  <a name="a-namegettabfullwidtha--cmfcbasetabctrlgettabfullwidth"></a><a name="gettabfullwidth"></a>CMFCBaseTabCtrl::GetTabFullWidth  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetTabFullWidth(int iTab) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegettabhicona--cmfcbasetabctrlgettabhicon"></a><a name="gettabhicon"></a>CMFCBaseTabCtrl::GetTabHicon  
 返回与指定的选项卡关联 HICON。  
  
```  
virtual HICON GetTabHicon(int iTab) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 选项卡的的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 与选项卡标签，如果成功，则关联 HICON`NULL`没有 HICON 是否，或者该方法将失败。  
  
##  <a name="a-namegettabicona--cmfcbasetabctrlgettabicon"></a><a name="gettabicon"></a>CMFCBaseTabCtrl::GetTabIcon  
 检索与指定的选项卡关联的图标。  
  
```  
virtual UINT GetTabIcon(int iTab) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 选项卡的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 如果成功，则指定的选项卡图标 ID如果该索引无效，则为-1。  
  
### <a name="remarks"></a>备注  
 [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)对象存储在内部图标[CImageList](../../mfc/reference/cimagelist-class.md)对象。  
  
##  <a name="a-namegettabida--cmfcbasetabctrlgettabid"></a><a name="gettabid"></a>CMFCBaseTabCtrl::GetTabID  
 检索指定的选项卡索引的选项卡的 ID。  
  
```  
int GetTabID(int iTab) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 选项卡的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 ID 为选项卡或则为-1`iTab`超出范围。  
  
##  <a name="a-namegettablabela--cmfcbasetabctrlgettablabel"></a><a name="gettablabel"></a>CMFCBaseTabCtrl::GetTabLabel  
 检索的选项卡标签的文本。  
  
```  
virtual BOOL GetTabLabel(
    int iTab,  
    CString& strLabel) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 选项卡的从零开始索引。  
  
 [out] `strLabel`  
 对 `CString` 对象的引用。 此方法将存储在此参数中的选项卡的标签。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则，`FALSE`否则为。  
  
### <a name="remarks"></a>备注  
 如果该方法无效索引`iTab`无效。  
  
 当通过使用创建选项卡上设置的选项卡标签[cmfcbasetabctrl:: Addtab](#addtab)。 您还可以更改该标签在创建后使用方法[CMFCBaseTabCtrl::SetTabLabel](#settablabel)。  
  
##  <a name="a-namegettabrecta--cmfcbasetabctrlgettabrect"></a><a name="gettabrect"></a>CMFCBaseTabCtrl::GetTabRect  
 检索的大小和位置指定选项卡。  
  
```  
virtual BOOL GetTabRect(
    int iTab,  
    CRect& rect) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 选项卡的从零开始索引。  
  
 [out] `rect`  
 对 `CRect` 对象的引用。 此方法在此参数中存储的大小和位置选项卡。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则，`FALSE`如果 tab 键索引无效。  
  
##  <a name="a-namegettabsheighta--cmfcbasetabctrlgettabsheight"></a><a name="gettabsheight"></a>CMFCBaseTabCtrl::GetTabsHeight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual int GetTabsHeight() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegettabsnuma--cmfcbasetabctrlgettabsnum"></a><a name="gettabsnum"></a>CMFCBaseTabCtrl::GetTabsNum  
 检索选项卡控件中的选项卡的数目。  
  
```  
virtual int GetTabsNum() const;  
```  
  
### <a name="return-value"></a>返回值  
 选项卡控件中的选项卡的数目。  
  
##  <a name="a-namegettabsrecta--cmfcbasetabctrlgettabsrect"></a><a name="gettabsrect"></a>CMFCBaseTabCtrl::GetTabsRect  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void GetTabsRect(CRect& rect) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `rect`  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namegettabtextcolora--cmfcbasetabctrlgettabtextcolor"></a><a name="gettabtextcolor"></a>CMFCBaseTabCtrl::GetTabTextColor  
 检索指定的选项卡的文本颜色。  
  
```  
virtual COLORREF GetTabTextColor(int iTab) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 选项卡的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 一个[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)参数，该值指示指定的选项卡的文本颜色; 则为-1`iTab`超出范围。  
  
##  <a name="a-namegettabwnda--cmfcbasetabctrlgettabwnd"></a><a name="gettabwnd"></a>CMFCBaseTabCtrl::GetTabWnd  
 返回指向驻留在指定的选项卡窗格中的指针。  
  
```  
virtual CWnd* GetTabWnd(int iTab) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 选项卡的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 一个指向[CWnd](../../mfc/reference/cwnd-class.md)驻留在选项卡的对象，`iTab`指定。 `NULL`如果`iTab`是无效的。  
  
### <a name="remarks"></a>备注  
 返回的对象是指应用程序添加调用任何一个时[cmfcbasetabctrl:: Addtab](#addtab)或[cmfcbasetabctrl:: Inserttab](#inserttab)。  
  
 选项卡上的对象都具有一个包装，如果此方法将返回该对象的包装器。 包装有关详细信息，请参阅[CMFCBaseTabCtrl::CreateWrapper](#createwrapper)。 如果你想要访问而无需包装的直接对象的指针，使用方法[CMFCBaseTabCtrl::GetTabWndNoWrapper](#gettabwndnowrapper)。  
  
##  <a name="a-namegettabwndnowrappera--cmfcbasetabctrlgettabwndnowrapper"></a><a name="gettabwndnowrapper"></a>CMFCBaseTabCtrl::GetTabWndNoWrapper  
 返回指向驻留在一个选项卡的控件的指针，即使在控件有一个包装。  
  
```  
virtual CWnd* GetTabWndNoWrapper(int iTab) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 选项卡的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 一个指向[CWnd](../../mfc/reference/cwnd-class.md)驻留在指定的选项卡; 的对象`NULL`如果`iTab`是无效的。  
  
### <a name="remarks"></a>备注  
 此方法检索到的直接指针`CWnd`对象通过使用上述任一方法添加[cmfcbasetabctrl:: Addtab](#addtab)或[cmfcbasetabctrl:: Inserttab](#inserttab)。 `GetTabWndNoWrapper`将检索指向所添加的`CWnd`，即使该框架添加对象的包装器。 包装有关详细信息和[CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)，请参阅[CMFCBaseTabCtrl::CreateWrapper](#createwrapper)。  
  
 使用方法[CMFCBaseTabCtrl::GetTabWnd](#gettabwnd)如果不希望忽略包装类。  
  
##  <a name="a-namegettooltipctrla--cmfcbasetabctrlgettooltipctrl"></a><a name="gettooltipctrl"></a>CMFCBaseTabCtrl::GetToolTipCtrl  
 检索向工具提示 contorl 的引用。  
  
```  
CToolTipCtrl& GetToolTipCtrl() const;  
```  
  
### <a name="return-value"></a>返回值  
 对工具提示控件的引用。  
  
##  <a name="a-namegetvisibletabsnuma--cmfcbasetabctrlgetvisibletabsnum"></a><a name="getvisibletabsnum"></a>CMFCBaseTabCtrl::GetVisibleTabsNum  
 检索当前可见的选项卡的数目。  
  
```  
virtual int GetVisibleTabsNum() const;  
```  
  
### <a name="return-value"></a>返回值  
 可见选项卡的数目。  
  
##  <a name="a-namehasimagea--cmfcbasetabctrlhasimage"></a><a name="hasimage"></a>CMFCBaseTabCtrl::HasImage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL HasImage(int iTab) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namehidesingletaba--cmfcbasetabctrlhidesingletab"></a><a name="hidesingletab"></a>CMFCBaseTabCtrl::HideSingleTab  
 设置一个可见选项卡时隐藏选项卡控件的选项卡的选项。  
  
```  
virtual void HideSingleTab(BOOL bHide = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bHide`  
 一个布尔值，指定是否启用隐藏单个选项卡。  
  
### <a name="remarks"></a>备注  
 您的应用程序配置为隐藏单个选项卡，框架将自动显示选项卡，在第二个选项卡将添加到选项卡控件时。  
  
##  <a name="a-nameinserttaba--cmfcbasetabctrlinserttab"></a><a name="inserttab"></a>Cmfcbasetabctrl:: Inserttab  
 选项卡控件中插入一个选项卡。  
  
```  
Virtual void InsertTab(
    CWnd* pNewWnd,  
    LPCTSTR lpszTabLabel,  
    int nInsertAt,  
    UINT uiImageId = (UINT)-1,  
    BOOL bDetachable = TRUE);

 
virtual void InsertTab(
    CWnd* pNewWnd,  
    UINT uiResTabLabel,  
    int nInsertAt,  
    UINT uiImageId = (UINT)-1,  
    BOOL bDetachable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pNewWnd`  
 指向此方法将添加一个新选项卡为窗口的指针。  
  
 [in] `lpszTabLabel`  
 一个字符串，包含用于新选项卡的标签。  
  
 [in] `nInsertAt`  
 新选项卡的从零开始的索引。  
  
 [in] `uiImageId`  
 从图像列表的图像 ID。 选项卡控件用作此图像图标的新选项卡。  
  
 [in] `bDetachable`  
 一个布尔型参数，用于确定新选项卡是否可拆分。  
  
 [in] `uiResTabLabel`  
 标签的资源 ID。  
  
### <a name="remarks"></a>备注  
 如果该对象由`pNewWnd`不源自[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)并且如果`bDetachable`参数是`TRUE`，框架会创建新选项卡上的特殊包装器。 默认情况下，此包装属于实例[CDockablePaneAdapter 类](../../mfc/reference/cdockablepaneadapter-class.md)。 使用[:: Setdockingbarwrapperrtc](#setdockingbarwrapperrtc)方法来创建不同的包装类。 任何自定义包装类必须派生自`CDockablePaneAdapter`。  
  
##  <a name="a-nameinvalidatetaba--cmfcbasetabctrlinvalidatetab"></a><a name="invalidatetab"></a>CMFCBaseTabCtrl::InvalidateTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void InvalidateTab(int iTab);
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameisactivetabclosebuttona--cmfcbasetabctrlisactivetabclosebutton"></a><a name="isactivetabclosebutton"></a>CMFCBaseTabCtrl::IsActiveTabCloseButton  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsActiveTabCloseButton() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameisautocolora--cmfcbasetabctrlisautocolor"></a><a name="isautocolor"></a>CMFCBaseTabCtrl::IsAutoColor  
 确定选项卡控件是否处于 autocolor 模式。  
  
```  
BOOL IsAutoColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果选项卡控件在 autocolor 模式;`FALSE`否则为。  
  
### <a name="remarks"></a>备注  
 您可以通过启用或禁用 autocolor 模式使用[CMFCBaseTabCtrl::EnableAutoColor](#enableautocolor)方法。  
  
##  <a name="a-nameisautodestroywindowa--cmfcbasetabctrlisautodestroywindow"></a><a name="isautodestroywindow"></a>CMFCBaseTabCtrl::IsAutoDestroyWindow  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsAutoDestroyWindow() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameiscoloreda--cmfcbasetabctrliscolored"></a><a name="iscolored"></a>CMFCBaseTabCtrl::IsColored  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsColored() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameisdialogcontrola--cmfcbasetabctrlisdialogcontrol"></a><a name="isdialogcontrol"></a>CMFCBaseTabCtrl::IsDialogControl  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsDialogControl() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameisdrawnoprefixa--cmfcbasetabctrlisdrawnoprefix"></a><a name="isdrawnoprefix"></a>CMFCBaseTabCtrl::IsDrawNoPrefix  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsDrawNoPrefix() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameisflatframea--cmfcbasetabctrlisflatframe"></a><a name="isflatframe"></a>CMFCBaseTabCtrl::IsFlatFrame  
 指示在平面样式或 3D 样式是否呈现的帧的选项卡控件。  
  
```  
virtual BOOL IsFlatFrame() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果在平面样式; 中呈现的帧的选项卡控件`FALSE`如果了三维样式中呈现的帧。  
  
### <a name="remarks"></a>备注  
 使用[CMFCTabCtrl::SetFlatFrame](../../mfc/reference/cmfctabctrl-class.md#setflatframe)若要更改选项卡控件的框架的样式。  
  
 无法使用平面帧呈现，请使用 Outlook 样式的选项卡控件。 这包括[CMFCOutlookBarTabCtrl 类](../../mfc/reference/cmfcoutlookbartabctrl-class.md)和从该类派生的任何类。  
  
##  <a name="a-nameisflattaba--cmfcbasetabctrlisflattab"></a><a name="isflattab"></a>CMFCBaseTabCtrl::IsFlatTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsFlatTab() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameishidesingletaba--cmfcbasetabctrlishidesingletab"></a><a name="ishidesingletab"></a>CMFCBaseTabCtrl::IsHideSingleTab  
 确定是否只有一个选项卡选项卡控件是否隐藏选项卡标签。  
  
```  
virtual BOOL IsHideSingleTab() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果它包含一个选项卡; 时，选项卡控件隐藏选项卡标签否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 使用方法[CMFCBaseTabCtrl::HideSingleTab](#hidesingletab)以便只有一个选项卡时隐藏选项卡标签。  
  
##  <a name="a-nameisiconaddeda--cmfcbasetabctrlisiconadded"></a><a name="isiconadded"></a>CMFCBaseTabCtrl::IsIconAdded  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsIconAdded(
    HICON hIcon,  
    int& iIcon);
```  
  
### <a name="parameters"></a>参数  
 [in] `hIcon`  
 [in] `iIcon`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameisinplaceedita--cmfcbasetabctrlisinplaceedit"></a><a name="isinplaceedit"></a>CMFCBaseTabCtrl::IsInPlaceEdit  
 指示是否配置选项卡控件以使用户能够动态修改选项卡标签。  
  
```  
virtual BOOL IsInPlaceEdit() const;  
```  
  
### <a name="return-value"></a>返回值  
 非零，如果在就地编辑已启用否则为 0。  
  
### <a name="remarks"></a>备注  
 您可以启用或禁用就地编辑通过调用方法[CMFCBaseTabCtrl::EnableInPlaceEdit](#enableinplaceedit)。  
  
##  <a name="a-nameisleftrightroundeda--cmfcbasetabctrlisleftrightrounded"></a><a name="isleftrightrounded"></a>CMFCBaseTabCtrl::IsLeftRightRounded  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsLeftRightRounded() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameismditaba--cmfcbasetabctrlismditab"></a><a name="ismditab"></a>CMFCBaseTabCtrl::IsMDITab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsMDITab() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameisonenotestylea--cmfcbasetabctrlisonenotestyle"></a><a name="isonenotestyle"></a>CMFCBaseTabCtrl::IsOneNoteStyle  
 确定是否在 Microsoft OneNote 的样式显示选项卡。  
  
```  
virtual BOOL IsOneNoteStyle() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果在样式中的 Microsoft OneNote; 显示选项卡否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 调用方法[CMDIFrameWndEx::EnableMDITabs](../../mfc/reference/cmdiframewndex-class.md#enablemditabs)若要启用 Microsoft OneNote 样式。 您还可以启用这种样式，当您实例化[CMFCTabCtrl 类](../../mfc/reference/cmfctabctrl-class.md)︰ 只需向方法传递样式 STYLE_3D_ONENOTE [CMFCTabCtrl::Create](../../mfc/reference/cmfctabctrl-class.md#create)。  
  
 默认情况下，Microsoft OneNote 样式不支持在自定义类派生自`CMFCBaseTabCtrl Class`。 但是，支持在`CMFCTabCtrl`类。  
  
##  <a name="a-nameisptintabareaa--cmfcbasetabctrlisptintabarea"></a><a name="isptintabarea"></a>CMFCBaseTabCtrl::IsPtInTabArea  
 确定某个点是否在选项卡区域内。  
  
```  
virtual BOOL IsPtInTabArea(CPoint point) const = 0;  
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
 要测试的点。  
  
### <a name="return-value"></a>返回值  
 非零，如果点在选项卡区域;否则为 0。  
  
### <a name="remarks"></a>备注  
 在`CMFCBaseTabCtrl Class`，此方法是纯虚函数，没有实现。 如果您从派生类`CMFCBaseTabCtrl`，您必须实现此函数。  
  
##  <a name="a-nameistabclosebuttonhighlighteda--cmfcbasetabctrlistabclosebuttonhighlighted"></a><a name="istabclosebuttonhighlighted"></a>CMFCBaseTabCtrl::IsTabCloseButtonHighlighted  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsTabCloseButtonHighlighted() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameistabclosebuttonpresseda--cmfcbasetabctrlistabclosebuttonpressed"></a><a name="istabclosebuttonpressed"></a>CMFCBaseTabCtrl::IsTabCloseButtonPressed  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsTabCloseButtonPressed() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameistabdetachablea--cmfcbasetabctrlistabdetachable"></a><a name="istabdetachable"></a>CMFCBaseTabCtrl::IsTabDetachable  
 确定一个选项卡是否可拆分。  
  
```  
virtual BOOL IsTabDetachable(int iTab) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 要检查的选项卡从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果选项卡是可拆分。`FALSE`否则为。  
  
### <a name="remarks"></a>备注  
 若要使可拆分选项卡上，使用[CMFCBaseTabCtrl::EnableTabDetach](#enabletabdetach)。  
  
##  <a name="a-nameistabicononlya--cmfcbasetabctrlistabicononly"></a><a name="istabicononly"></a>CMFCBaseTabCtrl::IsTabIconOnly  
 确定选项卡标签是否包含只图标且没有文本。  
  
```  
virtual BOOL IsTabIconOnly(int iTab) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 选项卡的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果选项卡标签具有只图标;`FALSE`否则为。  
  
### <a name="remarks"></a>备注  
 若要在应用程序中显示仅图标设置选项卡，调用该方法[CMFCBaseTabCtrl::SetTabIconOnly](#settabicononly)。  
  
##  <a name="a-nameistabswapenableda--cmfcbasetabctrlistabswapenabled"></a><a name="istabswapenabled"></a>CMFCBaseTabCtrl::IsTabSwapEnabled  
 确定选项卡控件是否允许用户使用鼠标更改选项卡上的位置。  
  
```  
BOOL IsTabSwapEnabled() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果可以通过用户; 更改选项卡上的位置，则为非否则为 0。  
  
### <a name="remarks"></a>备注  
 默认情况下，用户无法更改选项卡控件中的选项卡的顺序。 使用[cmfcbasetabctrl:: Enabletabswap](#enabletabswap)方法，以启用此功能。  
  
##  <a name="a-nameistabvisiblea--cmfcbasetabctrlistabvisible"></a><a name="istabvisible"></a>CMFCBaseTabCtrl::IsTabVisible  
 指示指定的选项卡是否可见。  
  
```  
virtual BOOL IsTabVisible(int iTab) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 要检查的选项卡从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 如果指定的选项卡可见，则为非否则为 0。  
  
##  <a name="a-nameisvs2005stylea--cmfcbasetabctrlisvs2005style"></a><a name="isvs2005style"></a>CMFCBaseTabCtrl::IsVS2005Style  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL IsVS2005Style() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namembactivatetabonrightclicka--cmfcbasetabctrlmbactivatetabonrightclick"></a><a name="m_bactivatetabonrightclick"></a>CMFCBaseTabCtrl::m_bActivateTabOnRightClick  
 `m_bActivateTabOnRightClick`确定指示选项卡具有焦点时是否在用户通过使用鼠标右键单击选项卡标签。  
  
```  
BOOL m_bActivateTabOnRightClick;  
```  
  
### <a name="remarks"></a>备注  
 此数据成员的默认值是`FALSE`。  
  
##  <a name="a-namembautodestroywindowa--cmfcbasetabctrlmbautodestroywindow"></a><a name="m_bautodestroywindow"></a>CMFCBaseTabCtrl::m_bAutoDestroyWindow  
 `m_bAutoDestroyWindow`确定是否该框架自动销毁选项卡上的对象中删除选项卡时。  
  
```  
BOOL m_bAutoDestroyWindow;  
```  
  
### <a name="remarks"></a>备注  
 默认情况下，此成员是`FALSE`。  
  
##  <a name="a-namemovetaba--cmfcbasetabctrlmovetab"></a><a name="movetab"></a>CMFCBaseTabCtrl::MoveTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void MoveTab(
    int nSource,  
    int nDest);
```  
  
### <a name="parameters"></a>参数  
 [in] `nSource`  
 [in] `nDest`  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameonchangetabsa--cmfcbasetabctrlonchangetabs"></a><a name="onchangetabs"></a>CMFCBaseTabCtrl::OnChangeTabs  
 在控件的选项卡上的选项卡的数量的更改时，框架将调用此方法。  
  
```  
virtual void OnChangeTabs();
```  
  
### <a name="remarks"></a>备注  
 默认情况下，此方法没有任何效果。 重写此方法以在控件的选项卡上的选项卡的数量的更改时执行自定义代码。  
  
##  <a name="a-nameondropa--cmfcbasetabctrlondrop"></a><a name="ondrop"></a>CMFCBaseTabCtrl::OnDrop  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnDrop(
    COleDataObject*,
    DROPEFFECT,
    CPoint);
```  
  
### <a name="parameters"></a>参数  
 [in] `COleDataObject*`  
 [in] `DROPEFFECT`  
 [in] `CPoint`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameondragovera--cmfcbasetabctrlondragover"></a><a name="ondragover"></a>CMFCBaseTabCtrl::OnDragOver  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual DROPEFFECT OnDragOver(
    COleDataObject*,
    DWORD,
    CPoint);
```  
  
### <a name="parameters"></a>参数  
 [in] `COleDataObject*`  
 [in] `DWORD`  
 [in] `CPoint`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameondragleavea--cmfcbasetabctrlondragleave"></a><a name="ondragleave"></a>CMFCBaseTabCtrl::OnDragLeave  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnDragLeave();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameondragentera--cmfcbasetabctrlondragenter"></a><a name="ondragenter"></a>CMFCBaseTabCtrl::OnDragEnter  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual DROPEFFECT OnDragEnter(
    COleDataObject*,
    DWORD,
    CPoint);
```  
  
### <a name="parameters"></a>参数  
 [in] `COleDataObject*`  
 [in] `DWORD`  
 [in] `CPoint`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameonrenametaba--cmfcbasetabctrlonrenametab"></a><a name="onrenametab"></a>CMFCBaseTabCtrl::OnRenameTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnRenameTab(int, CString&);
```  
  
### <a name="parameters"></a>参数  
 [in] `int`  
 [in] `CString&`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namepretranslatemessagea--cmfcbasetabctrlpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCBaseTabCtrl::PreTranslateMessage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>参数  
 [in] `pMsg`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namerecalclayouta--cmfcbasetabctrlrecalclayout"></a><a name="recalclayout"></a>CMFCBaseTabCtrl::RecalcLayout  
 重新计算选项卡控件的内部布局。  
  
```  
virtual void RecalcLayout() = 0;  
```  
  
### <a name="remarks"></a>备注  
 在`CMFCBaseTabCtrl Class`，此方法是纯虚函数。 如果您从派生类`CMFCBaseTabCtrl`，您必须实现此函数。  
  
##  <a name="a-nameremovealltabsa--cmfcbasetabctrlremovealltabs"></a><a name="removealltabs"></a>CMFCBaseTabCtrl::RemoveAllTabs  
 从选项卡控件中移除所有选项卡。  
  
```  
virtual void RemoveAllTabs();
```  
  
### <a name="remarks"></a>备注  
 如果[CMFCBaseTabCtrl::m_bAutoDestroyWindow](#m_bautodestroywindow)是`TRUE`，该框架将删除所有[CWnd](../../mfc/reference/cwnd-class.md)对象附加到删除选项卡。  
  
##  <a name="a-nameremovetaba--cmfcbasetabctrlremovetab"></a><a name="removetab"></a>CMFCBaseTabCtrl::RemoveTab  
 从选项卡控件中移除一个选项卡。  
  
```  
virtual BOOL RemoveTab(
    int iTab,  
    BOOL bRecalcLayout = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 选项卡的从零开始索引。  
  
 [in] `bRecalcLayout`  
 一个布尔型参数，用于指定是否重新计算选项卡的布局。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果方法成功，则移除选项卡否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 如果[CMFCBaseTabCtrl::m_bAutoDestroyWindow](#m_bautodestroywindow)是`TRUE`，`RemoveTab`销毁[CWnd](../../mfc/reference/cwnd-class.md)与指定的选项卡相关联的对象。  
  
##  <a name="a-namerenametaba--cmfcbasetabctrlrenametab"></a><a name="renametab"></a>CMFCBaseTabCtrl::RenameTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL RenameTab();
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameresetimagelista--cmfcbasetabctrlresetimagelist"></a><a name="resetimagelist"></a>CMFCBaseTabCtrl::ResetImageList  
 实例的映像列表重置[CMFCBaseTabCtrl 类](../../mfc/reference/cmfcbasetabctrl-class.md)。  
  
```  
void ResetImageList();
```  
  
##  <a name="a-nameserializea--cmfcbasetabctrlserialize"></a><a name="serialize"></a>CMFCBaseTabCtrl::Serialize  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void Serialize(CArchive& ar);
```  
  
### <a name="parameters"></a>参数  
 [in] `ar`  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesetactivetaba--cmfcbasetabctrlsetactivetab"></a><a name="setactivetab"></a>CMFCBaseTabCtrl::SetActiveTab  
 激活指定的选项卡。  
  
```  
virtual BOOL SetActiveTab(int iTab) = 0;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 选项卡的从零开始索引。 `SetActiveTab`使具有此索引的选项卡处于活动状态。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 `TRUE`；否则为 `FALSE`。  
  
### <a name="remarks"></a>备注  
 在`CMFCBaseTabCtrl Class`，此方法是纯虚函数。 如果您从派生类`CMFCBaseTabCtrl`，您必须实现此函数。  
  
##  <a name="a-namesetactivetabcolora--cmfcbasetabctrlsetactivetabcolor"></a><a name="setactivetabcolor"></a>CMFCBaseTabCtrl::SetActiveTabColor  
 设置为活动选项卡的背景色。  
  
```  
virtual void SetActiveTabColor(COLORREF clr);
```  
  
### <a name="parameters"></a>参数  
 [in] `clr`  
 指定新的背景色。  
  
### <a name="remarks"></a>备注  
 该框架获得从活动选项卡的默认背景色[GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371)方法。  
  
##  <a name="a-namesetactivetabtextcolora--cmfcbasetabctrlsetactivetabtextcolor"></a><a name="setactivetabtextcolor"></a>CMFCBaseTabCtrl::SetActiveTabTextColor  
 设置活动选项卡的文本颜色。  
  
```  
virtual void SetActiveTabTextColor(COLORREF clr);
```  
  
### <a name="parameters"></a>参数  
 [in] `clr`  
 一个[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)参数，用于指定新的文本颜色。  
  
### <a name="remarks"></a>备注  
 默认情况下，该框架获得的文本颜色从[GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371)。 通过使用重写此默认颜色`SetActiveTabTextColor`方法。  
  
##  <a name="a-namesetautocolorsa--cmfcbasetabctrlsetautocolors"></a><a name="setautocolors"></a>CMFCBaseTabCtrl::SetAutoColors  
 设置自动配色模式中的框架将使用该选项卡控件的颜色。  
  
```  
void SetAutoColors(const CArray<COLORREF,COLORREF>& arColors);
```  
  
### <a name="parameters"></a>参数  
 [in] `arColors`  
 RGB 颜色的数组。  
  
### <a name="remarks"></a>备注  
 如果你提供一个自定义的颜色数组，则忽略颜色的默认值数组。 如果该参数`arColors`是空的框架将恢复为默认数组的颜色。  
  
 若要启用 autocolor 模式，请使用[CMFCBaseTabCtrl::EnableAutoColor](#enableautocolor)方法。  
  
##  <a name="a-namesetdockingbarwrapperrtca--cmfcbasetabctrlsetdockingbarwrapperrtc"></a><a name="setdockingbarwrapperrtc"></a>:: Setdockingbarwrapperrtc  
 设置用于不从派生的任何对象的包装类[CDockablePane 类](../../mfc/reference/cdockablepane-class.md)。  
  
```  
void SetDockingBarWrapperRTC(CRuntimeClass* pRTC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pRTC`  
 新的包装器类的运行时类信息。  
  
### <a name="remarks"></a>备注  
 您使用的方法向选项卡控件添加选项卡[cmfcbasetabctrl:: Addtab](#addtab)和[cmfcbasetabctrl:: Inserttab](#inserttab)。 当您添加一个选项卡时，该选项卡上的每个控件必须是可停靠。 不从派生的任何对象`CDockablePane`必须包装。 `AddTab`和`InsertTab`创建这些对象的包装器。 默认包装类是[CDockablePaneAdapter 类](../../mfc/reference/cdockablepaneadapter-class.md)。 该方法`SetDockingBarWrapperRTC`，您可以更改用作包装器类的类。 您提供的包装器类必须派生自`CDockablePaneAdapter`。  
  
##  <a name="a-namesetdrawnoprefixa--cmfcbasetabctrlsetdrawnoprefix"></a><a name="setdrawnoprefix"></a>CMFCBaseTabCtrl::SetDrawNoPrefix  
 启用和禁用选项卡标签中的前缀字符的处理。  
  
```  
void SetDrawNoPrefix(
    BOOL bNoPrefix,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bNoPrefix`  
 `TRUE`如果您想要处理前缀字符;否则为`FALSE`。  
  
 [in] `bRedraw`  
 `TRUE`如果您想要重绘选项卡式的窗口;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 前缀字符是 and 符 （&） 前面的助记键字符。  
  
##  <a name="a-namesetimagelista--cmfcbasetabctrlsetimagelist"></a><a name="setimagelist"></a>CMFCBaseTabCtrl::SetImageList  
 设置选项卡控件的图标图像列表。  
  
```  
virtual BOOL SetImageList(
    UINT uiID,  
    int cx = 15,  
    COLORREF clrTransp = RGB(255, 0, 255));  
  
virtual BOOL SetImageList(HIMAGELIST hImageList);
```  
  
### <a name="parameters"></a>参数  
 [in] `uiID`  
 位图的资源 id。 `SetImageList`从此资源中加载的图像列表。  
  
 [in] `cx`  
 以像素为单位的每个图像的宽度。  
  
 [in] `clrTransp`  
 一个[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)参数可指示该图像的透明色。  
  
 [in] `hImageList`  
 指向一个预加载的图像列表的句柄。  
  
### <a name="return-value"></a>返回值  
 如果此方法已成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 选项卡的标签旁边显示图标图像列表中的图像。 若要显示一个图标，必须指定的索引，当您调用[cmfcbasetabctrl:: Addtab](#addtab)。  
  
 `SetImageList`如果选项卡控件使用平面样式创建将失败。 如果框架无法加载所指示的图像则也会失败`uiID`。  
  
 此方法将重新计算选项卡，根据图像和文本大小的高度。  
  
##  <a name="a-namesetlocationa--cmfcbasetabctrlsetlocation"></a><a name="setlocation"></a>CMFCBaseTabCtrl::SetLocation  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void SetLocation(Location location);
```  
  
### <a name="parameters"></a>参数  
 [in] `location`  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesettabbkcolora--cmfcbasetabctrlsettabbkcolor"></a><a name="settabbkcolor"></a>CMFCBaseTabCtrl::SetTabBkColor  
 设置指定的选项卡的背景色。  
  
```  
virtual BOOL SetTabBkColor(
    int iTab,  
    COLORREF color = (COLORREF)-1);
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 选项卡的从零开始索引。  
  
 [in] `color`  
 要设置的颜色。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则，`FALSE`否则为。  
  
##  <a name="a-namesettabbordersizea--cmfcbasetabctrlsettabbordersize"></a><a name="settabbordersize"></a>CMFCBaseTabCtrl::SetTabBorderSize  
 设置选项卡控件的新边框大小。  
  
```  
virtual void SetTabBorderSize(
    int nTabBorderSize,  
    BOOL bRepaint = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `nTabBorderSize`  
 新的边框大小，以像素为单位。  
  
 [in] `bRepaint`  
 一个布尔型参数，该值指示框架是否重绘控件。  
  
##  <a name="a-namesettabhicona--cmfcbasetabctrlsettabhicon"></a><a name="settabhicon"></a>CMFCBaseTabCtrl::SetTabHicon  
 设置选项卡标签的图标。  
  
```  
virtual BOOL SetTabHicon(
    int iTab,  
    HICON hIcon);
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 选项卡的从零开始索引。 此方法更改此选项卡上的图标。  
  
 [in] `hIcon`  
 指向一个图标的句柄。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 `TRUE`；否则为 `FALSE`。  
  
##  <a name="a-namesettabicona--cmfcbasetabctrlsettabicon"></a><a name="settabicon"></a>CMFCBaseTabCtrl::SetTabIcon  
 设置选项卡上的图标。  
  
```  
virtual BOOL SetTabIcon(
    int iTab,  
    UINT uiIcon);
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 要更新的选项卡从零开始的索引。  
  
 [in] `uiIcon`  
 新建图标图标 ID。 此 ID 引用的内部[CImageList](../../mfc/reference/cimagelist-class.md)对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 `TRUE`；否则为 `FALSE`。  
  
##  <a name="a-namesettabicononlya--cmfcbasetabctrlsettabicononly"></a><a name="settabicononly"></a>CMFCBaseTabCtrl::SetTabIconOnly  
 启用特定的选项卡上显示的只是一个图标 （和没有文本标签）。  
  
```  
virtual BOOL SetTabIconOnly(
    int iTab,  
    BOOL bIconOnly = TRUE,  
    BOOL bShowTooltipAlways = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 若要更改选项卡的从零开始的索引。  
  
 [in] `bIconOnly`  
 一个布尔型参数，用于确定是否显示仅图标。  
  
 [in] `bShowTooltipAlways`  
 一个布尔型参数，用于确定框架是否显示工具提示显示仅图标的选项卡标签。  
  
### <a name="return-value"></a>返回值  
 如果成功，则为 `TRUE`；否则为 `FALSE`。  
  
### <a name="remarks"></a>备注  
 默认情况下，选项卡控件显示每个选项卡的图标和文本标签。  
  
##  <a name="a-namesettablabela--cmfcbasetabctrlsettablabel"></a><a name="settablabel"></a>CMFCBaseTabCtrl::SetTabLabel  
 设置选项卡标签的文本。  
  
```  
virtual BOOL SetTabLabel(
    int iTab,  
    const CString& strLabel);
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 要更新的选项卡从零开始的索引。  
  
 [in] `strLabel`  
 对一个包含新选项卡标签的文字字符串的引用。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值否则为 0。  
  
##  <a name="a-namesettabsheighta--cmfcbasetabctrlsettabsheight"></a><a name="settabsheight"></a>CMFCBaseTabCtrl::SetTabsHeight  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void SetTabsHeight();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-namesettabsordera--cmfcbasetabctrlsettabsorder"></a><a name="settabsorder"></a>CMFCBaseTabCtrl::SetTabsOrder  
 排列指定的顺序中的选项卡。  
  
```  
BOOL SetTabsOrder(const CArray<int,int>& arOrder);
```  
  
### <a name="parameters"></a>参数  
 [in] `arOrder`  
 定义新的 tab 键顺序的从零开始的索引数组。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果成功，则，`FAIL`否则为。  
  
### <a name="remarks"></a>备注  
 大小`arOrder`数组必须等于选项卡控件中选项卡的数目。  
  
##  <a name="a-namesettabtextcolora--cmfcbasetabctrlsettabtextcolor"></a><a name="settabtextcolor"></a>CMFCBaseTabCtrl::SetTabTextColor  
 设置特定的选项卡的文本颜色。  
  
```  
virtual BOOL SetTabTextColor(
    int iTab,  
    COLORREF color = (COLORREF)-1);
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 选项卡的从零开始索引。  
  
 [in] `color`  
 一个[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)参数，指示新的文本颜色。  
  
### <a name="return-value"></a>返回值  
 如果成功，则非零值否则为 0。  
  
##  <a name="a-nameshowtaba--cmfcbasetabctrlshowtab"></a><a name="showtab"></a>CMFCBaseTabCtrl::ShowTab  
 显示或隐藏指定的选项卡。  
  
```  
virtual BOOL ShowTab(
    int iTab,  
    BOOL bShow = TRUE,  
    BOOL bRecalcLayout = TRUE,  
    BOOL bActivate = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
 选项卡的索引，`ShowTab`将显示或隐藏。  
  
 [in] `bShow`  
 一个布尔型参数，该值指示是否显示选项卡。  
  
 [in] `bRecalcLayout`  
 一个布尔型参数，该值指示是否立即重新计算的窗口布局。  
  
 [in] `bActivate`  
 一个布尔型参数，该值指示是否选中选项卡指定`iTab`。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 该参数`bActivate`只适用于`bShow`是`TRUE`。 如果`bActivate`是`TRUE`并且如果`ShowTab`是成功的`ShowTab`将 AFX_WM_CHANGE_ACTIVE_TAB 将消息发送到选项卡窗口的父级。  
  
##  <a name="a-namestartrenametaba--cmfcbasetabctrlstartrenametab"></a><a name="startrenametab"></a>CMFCBaseTabCtrl::StartRenameTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL StartRenameTab(int iTab);
```  
  
### <a name="parameters"></a>参数  
 [in] `iTab`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameswaptabsa--cmfcbasetabctrlswaptabs"></a><a name="swaptabs"></a>CMFCBaseTabCtrl::SwapTabs  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void SwapTabs(
    int nFisrtTabID,  
    int nSecondTabID);
```  
  
### <a name="parameters"></a>参数  
 [in] `nFisrtTabID`  
 [in] `nSecondTabID`  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCTabCtrl 类](../../mfc/reference/cmfctabctrl-class.md)   
 [CMFCOutlookBarTabCtrl 类](../../mfc/reference/cmfcoutlookbartabctrl-class.md)

