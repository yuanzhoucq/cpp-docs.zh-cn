---
title: "COleIPFrameWndEx 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleIPFrameWndEx
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::AddDockSite
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::AddPane
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::AdjustDockingLayout
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::DockPane
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::DockPaneLeftOf
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::EnableAutoHidePanes
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::EnableDocking
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::EnablePaneMenu
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::GetActivePopup
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::GetContainerFrameWindow
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::GetDefaultResId
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::GetDockFrame
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::GetDockingManager
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::GetMainFrame
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::GetMenuBar
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::GetPane
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::GetTearOffBars
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::GetToolbarButtonToolTipText
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::InsertPane
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::IsMenuBarAvailable
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::IsPointNearDockSite
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::LoadFrame
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnCloseDockingPane
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnCloseMiniFrame
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnClosePopupMenu
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnCmdMsg
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnDrawMenuImage
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnDrawMenuLogo
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnMenuButtonToolHitTest
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnMoveMiniFrame
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnSetPreviewMode
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnShowCustomizePane
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnShowPanes
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnShowPopupMenu
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::OnTearOffMenu
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::PaneFromPoint
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::PreTranslateMessage
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::RecalcLayout
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::RemovePaneFromDockManager
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::SetDockState
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::SetupToolbarMenu
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::ShowPane
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::WinHelpA
- AFXOLEIPFRAMEWNDEX/COleIPFrameWndEx::InitUserToobars
dev_langs:
- C++
helpviewer_keywords:
- COleIPFrameWndEx class
ms.assetid: ebff1560-a1eb-4854-af00-95d4a192bd55
caps.latest.revision: 34
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
ms.openlocfilehash: 5eec8e3a9cc4ad71a1ee3de9f6d5f25cffef1242
ms.lasthandoff: 02/24/2017

---
# <a name="coleipframewndex-class"></a>COleIPFrameWndEx 类
`COleIPFrameWndEx` 类实现支持 MFC 的 OLE 容器。 必须为您的应用程序中派生就地框架窗口类`COleIPFrameWndEx`类，而不是从它派生[COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md)类。  
  
## <a name="syntax"></a>语法  
  
```  
class COleIPFrameWndEx : public COleIPFrameWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[COleIPFrameWndEx::AddDockSite](#adddocksite)||  
|[COleIPFrameWndEx::AddPane](#addpane)||  
|[COleIPFrameWndEx::AdjustDockingLayout](#adjustdockinglayout)||  
|[COleIPFrameWndEx::DockPane](#dockpane)||  
|[COleIPFrameWndEx::DockPaneLeftOf](#dockpaneleftof)|将一个窗格停靠到另一个窗格的左侧。|  
|[COleIPFrameWndEx::EnableAutoHidePanes](#enableautohidepanes)||  
|[COleIPFrameWndEx::EnableDocking](#enabledocking)||  
|[COleIPFrameWndEx::EnablePaneMenu](#enablepanemenu)||  
|[COleIPFrameWndEx::GetActivePopup](#getactivepopup)|返回一个指向当前显示的弹出菜单的指针。|  
|[COleIPFrameWndEx::GetContainerFrameWindow](#getcontainerframewindow)||  
|[COleIPFrameWndEx::GetDefaultResId](#getdefaultresid)|返回加载窗口时你指定的框架窗口的资源 ID。|  
|[COleIPFrameWndEx::GetDockFrame](#getdockframe)||  
|[COleIPFrameWndEx::GetDockingManager](#getdockingmanager)||  
|[COleIPFrameWndEx::GetMainFrame](#getmainframe)||  
|[COleIPFrameWndEx::GetMenuBar](#getmenubar)|返回一个指向附加到框架窗口的菜单栏对象的指针。|  
|[COleIPFrameWndEx::GetPane](#getpane)||  
|[COleIPFrameWndEx::GetTearOffBars](#gettearoffbars)|返回处于拖曳状态的窗格对象的列表。|  
|[COleIPFrameWndEx::GetToolbarButtonToolTipText](#gettoolbarbuttontooltiptext)|在显示按钮的工具提示之前由框架调用。|  
|[COleIPFrameWndEx::InsertPane](#insertpane)||  
|[COleIPFrameWndEx::IsMenuBarAvailable](#ismenubaravailable)|确定指向菜单栏对象的指针是否不是 `NULL`。|  
|[COleIPFrameWndEx::IsPointNearDockSite](#ispointneardocksite)||  
|[COleIPFrameWndEx::LoadFrame](#loadframe)|（重写 `COleIPFrameWnd::LoadFrame`。）|  
|[COleIPFrameWndEx::OnCloseDockingPane](#onclosedockingpane)||  
|[COleIPFrameWndEx::OnCloseMiniFrame](#oncloseminiframe)||  
|[COleIPFrameWndEx::OnClosePopupMenu](#onclosepopupmenu)|当活动的弹出菜单处理 WM_DESTROY 消息时由框架调用。|  
|[COleIPFrameWndEx::OnCmdMsg](#oncmdmsg)|（重写 `CFrameWnd::OnCmdMsg`。）|  
|[COleIPFrameWndEx::OnDrawMenuImage](#ondrawmenuimage)|当绘制与菜单项关联的图像时由框架调用。|  
|[COleIPFrameWndEx::OnDrawMenuLogo](#ondrawmenulogo)|由框架调用时[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)对象处理 WM_PAINT 消息。|  
|[COleIPFrameWndEx::OnMenuButtonToolHitTest](#onmenubuttontoolhittest)|由框架调用时[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)对象处理 WM_NCHITTEST 消息。|  
|[COleIPFrameWndEx::OnMoveMiniFrame](#onmoveminiframe)||  
|[COleIPFrameWndEx::OnSetPreviewMode](#onsetpreviewmode)|调用该成员函数以设置应用程序主框架窗口打印预览模式的流入和流出。 (重写[CFrameWnd::OnSetPreviewMode](../../mfc/reference/cframewnd-class.md#onsetpreviewmode)。)|  
|[COleIPFrameWndEx::OnShowCustomizePane](#onshowcustomizepane)||  
|[COleIPFrameWndEx::OnShowPanes](#onshowpanes)||  
|[COleIPFrameWndEx::OnShowPopupMenu](#onshowpopupmenu)|当激活弹出菜单时由框架调用。|  
|[COleIPFrameWndEx::OnTearOffMenu](#ontearoffmenu)|当激活带有拖曳栏的菜单时由框架调用。|  
|[COleIPFrameWndEx::PaneFromPoint](#panefrompoint)||  
|[COleIPFrameWndEx::PreTranslateMessage](#pretranslatemessage)|（重写 `COleIPFrameWnd::PreTranslateMessage`。）|  
|[COleIPFrameWndEx::RecalcLayout](#recalclayout)|（重写 `COleIPFrameWnd::RecalcLayout`。）|  
|[COleIPFrameWndEx::RemovePaneFromDockManager](#removepanefromdockmanager)||  
|[COleIPFrameWndEx::SetDockState](#setdockstate)|将指定的停靠状态应用于属于框架窗口的窗格。|  
|[COleIPFrameWndEx::SetupToolbarMenu](#setuptoolbarmenu)|通过搜索虚拟项并将其替换为指定的用户定义项修改工具栏对象。|  
|[COleIPFrameWndEx::ShowPane](#showpane)||  
|[COleIPFrameWndEx::WinHelpA](#winhelpa)|由框架调用以启动 WinHelp 应用程序或上下文帮助。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[COleIPFrameWndEx::InitUserToobars](#initusertoobars)|告知框架初始化一系列分配给用户定义的工具栏的控件 ID。|  
  
## <a name="example"></a>示例  
 下面的示例演示如何将 `COleIPFrameWndEx` 类的实例作为子类并重写其方法。 该示例演示如何重写 `OnDestory` 方法、 `RepositionFrame` 方法、 `RecalcLayout` 方法和 `CalcWindowRect` 方法。 此代码段属于[Word 板示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_WordPad #&1;](../../mfc/reference/codesnippet/cpp/coleipframewndex-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 [COleIPFrameWnd](../../mfc/reference/coleipframewnd-class.md)  
  
 [COleIPFrameWndEx](../../mfc/reference/coleipframewndex-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxoleipframewndex.h  
  
##  <a name="adddocksite"></a>COleIPFrameWndEx::AddDockSite  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void AddDockSite();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="addpane"></a>COleIPFrameWndEx::AddPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL AddPane(
    CBasePane* pControlBar,  
    BOOL bTail = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pControlBar`  
 [in] `bTail`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="adjustdockinglayout"></a>COleIPFrameWndEx::AdjustDockingLayout  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void AdjustDockingLayout(HDWP hdwp = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `hdwp`  
  
### <a name="remarks"></a>备注  
  
##  <a name="dockpane"></a>COleIPFrameWndEx::DockPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void DockPane(
    CBasePane* pBar,  
    UINT nDockBarID = 0,  
    LPCRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `pBar`  
 [in] `nDockBarID`  
 [in] `lpRect`  
  
### <a name="remarks"></a>备注  
  
##  <a name="dockpaneleftof"></a>COleIPFrameWndEx::DockPaneLeftOf  
 将一个窗格停靠到另一个窗格的左侧。  
  
```  
BOOL DockPaneLeftOf(
    CPane* pBar,  
    CPane* pLeftOf);
```  
  
### <a name="parameters"></a>参数  
 [in] `pBar`  
 指向停靠窗格中的指针。  
  
 [in] `pLeftOf`  
 指向用作源窗格中的指针。  
  
### <a name="return-value"></a>返回值  
 返回`TRUE`如果操作成功。 否则返回 `FALSE`。  
  
### <a name="remarks"></a>备注  
 调用此方法以停靠在预定义顺序中的多个窗格对象。 此方法由指定窗格停靠`pBar`左侧的指定窗格中`pLeftOf`。  
  
##  <a name="enableautohidepanes"></a>COleIPFrameWndEx::EnableAutoHidePanes  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL EnableAutoHidePanes(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwDockStyle`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="enabledocking"></a>COleIPFrameWndEx::EnableDocking  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL EnableDocking(DWORD dwDockStyle);
```  
  
### <a name="parameters"></a>参数  
 [in] `dwDockStyle`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="enablepanemenu"></a>COleIPFrameWndEx::EnablePaneMenu  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void EnablePaneMenu(
    BOOL bEnable,  
    UINT uiCustomizeCmd,  
    const CString& strCustomizeLabel,  
    UINT uiViewToolbarsMenuEntryID,  
    BOOL bContextMenuShowsToolbarsOnly = FALSE,  
    BOOL bViewMenuShowsToolbarsOnly = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 [in] `uiCustomizeCmd`  
 [in] `strCustomizeLabel`  
 [in] `uiViewToolbarsMenuEntryID`  
 [in] `bContextMenuShowsToolbarsOnly`  
 [in] `bViewMenuShowsToolbarsOnly`  
  
### <a name="remarks"></a>备注  
  
##  <a name="getactivepopup"></a>COleIPFrameWndEx::GetActivePopup  
 返回一个指向当前所显示的弹出菜单。  
  
```  
CMFCPopupMenu* GetActivePopup() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向 active 弹出菜单;否则为`NULL`。  
  
### <a name="remarks"></a>备注  
 使用此方法可获取的指针[CMFCPopupMenu 类](../../mfc/reference/cmfcpopupmenu-class.md)当前显示的对象。  
  
##  <a name="getcontainerframewindow"></a>COleIPFrameWndEx::GetContainerFrameWindow  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
COleCntrFrameWndEx* GetContainerFrameWindow();
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getdefaultresid"></a>COleIPFrameWndEx::GetDefaultResId  
 返回时的菜单资源 ID 指定的框架窗口加载菜单上的时间。  
  
```  
UINT GetDefaultResId() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果框架窗口没有菜单栏，请返回菜单上，则为 0 的资源 ID。  
  
### <a name="remarks"></a>备注  
 调用此函数可检索已的资源 ID 指定在框架窗口加载时的菜单资源调用`COleIPFrameWndEx::LoadFrame`。  
  
##  <a name="getdockframe"></a>COleIPFrameWndEx::GetDockFrame  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CFrameWnd* GetDockFrame();
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getdockingmanager"></a>COleIPFrameWndEx::GetDockingManager  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CDockingManager* GetDockingManager();
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getmainframe"></a>COleIPFrameWndEx::GetMainFrame  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CFrameWnd* GetMainFrame();
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="getmenubar"></a>COleIPFrameWndEx::GetMenuBar  
 返回一个指向附加到框架窗口的菜单栏对象的指针。  
  
```  
const CMFCMenuBar* GetMenuBar() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向菜单条对象的指针。  
  
### <a name="remarks"></a>备注  
 使用此函数来检索指向属于菜单条对象`COleIPFrameWndEx`对象。  
  
##  <a name="getpane"></a>COleIPFrameWndEx::GetPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CBasePane* GetPane(UINT nID);
```  
  
### <a name="parameters"></a>参数  
 [in] `nID`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="gettearoffbars"></a>COleIPFrameWndEx::GetTearOffBars  
 返回处于拖曳状态的窗格对象的列表。  
  
```  
const CObList& GetTearOffBars() const;  
```  
  
### <a name="return-value"></a>返回值  
 对引用`CObList`对象，其中包含指向的指针的集合[CBasePane 类](../../mfc/reference/cbasepane-class.md)-派生的对象。  
  
### <a name="remarks"></a>备注  
 `COleIPFrameWndEx`对象维护的拖曳菜单集合的列表作为[CBasePane 类](../../mfc/reference/cbasepane-class.md)-派生的对象。 使用此方法来检索到此列表的引用。  
  
##  <a name="gettoolbarbuttontooltiptext"></a>COleIPFrameWndEx::GetToolbarButtonToolTipText  
 在显示按钮的工具提示之前由框架调用。  
  
```  
virtual BOOL GetToolbarButtonToolTipText(
    CMFCToolBarButton* pButton,  
    CString& strTTText);
```  
  
### <a name="parameters"></a>参数  
 [in] `pButton`  
 指针，指向按钮。  
  
 [in] `strTTText`  
 指向指针的工具提示文本。  
  
### <a name="return-value"></a>返回值  
 默认实现将返回 0。  
  
### <a name="remarks"></a>备注  
 重写此函数可自定义工具栏按钮上的工具提示的显示。  
  
##  <a name="initusertoobars"></a>COleIPFrameWndEx::InitUserToobars  
 指定控件框架将分配给用户定义的工具栏的 Id 的范围。  
  
```  
void InitUserToolbars(
    LPCTSTR lpszRegEntry,   
    UINT uiUserToolbarFirst,   
    UINT uiUserToolbarLast)  
```  
  
### <a name="parameters"></a>参数  
 [in] `lpszRegEntry`  
 库存储用户工具栏设置的位置的注册表项。  
  
 [in] `uiUserToolbarFirst`  
 分配给第一个用户定义的工具栏的控件 ID。  
  
 [in] `uiUserToolbarLast`  
 分配给最后一个用户定义的工具栏上的控件 ID。  
  
### <a name="remarks"></a>备注  
 使用此函数来初始化用于分配给用户动态定义的工具栏的控件 Id 的范围。 参数`uiUserToolbarFirst`和`uiUserToolbarLast`定义允许的工具栏控件 Id 的范围。 若要禁用创建用户定义的工具栏，将设置`uiUserToolbarFirst`或`uiUserToolbarLast`为-1。  
  
##  <a name="insertpane"></a>COleIPFrameWndEx::InsertPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL InsertPane(
    CBasePane* pControlBar,  
    CBasePane* pTarget,  
    BOOL bAfter = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pControlBar`  
 [in] `pTarget`  
 [in] `bAfter`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="ismenubaravailable"></a>COleIPFrameWndEx::IsMenuBarAvailable  
 确定是否不是菜单栏中对象的指针`NULL`  
  
```  
BOOL IsMenuBarAvailable() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果框架窗口包含一个菜单栏; 返回非零值否则，返回 0。  
  
### <a name="remarks"></a>备注  
 调用此方法以确定是否在框架窗口维护一个非`NULL`其菜单条对象的指针。  
  
##  <a name="ispointneardocksite"></a>COleIPFrameWndEx::IsPointNearDockSite  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsPointNearDockSite(
    CPoint point,  
    DWORD& dwBarAlignment,  
    BOOL& bOuterEdge) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
 [in] `dwBarAlignment`  
 [in] `bOuterEdge`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="loadframe"></a>COleIPFrameWndEx::LoadFrame  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL LoadFrame(
    UINT nIDResource,  
    DWORD dwDefaultStyle = WS_OVERLAPPEDWINDOW | FWS_ADDTOTITLE,  
    CWnd* pParentWnd = NULL,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>参数  
 [in] `nIDResource`  
 [in] `dwDefaultStyle`  
 [in] `pParentWnd`  
 [in] `pContext`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="onclosedockingpane"></a>COleIPFrameWndEx::OnCloseDockingPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnCloseDockingPane(CDockablePane*);
```  
  
### <a name="parameters"></a>参数  
 [in] `CDockablePane*`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="oncloseminiframe"></a>COleIPFrameWndEx::OnCloseMiniFrame  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnCloseMiniFrame(CPaneFrameWnd*);
```  
  
### <a name="parameters"></a>参数  
 [in] `CPaneFrameWnd*`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="onclosepopupmenu"></a>COleIPFrameWndEx::OnClosePopupMenu  
 当活动的弹出菜单处理由框架调用`WM_DESTROY`消息。  
  
```  
virtual void OnClosePopupMenu(CMFCPopupMenu* pMenuPopup);
```  
  
### <a name="parameters"></a>参数  
 [in] `pMenuPopup`  
 指向弹出菜单对象的指针。  
  
### <a name="remarks"></a>备注  
 重写此方法以从接收通知`CMFCPopupMenu`对象在处理`WM_DESTROY`消息。  
  
##  <a name="oncmdmsg"></a>COleIPFrameWndEx::OnCmdMsg  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnCmdMsg(
    UINT nID,  
    int nCode,  
    void* pExtra,  
    AFX_CMDHANDLERINFO* pHandlerInfo);
```  
  
### <a name="parameters"></a>参数  
 [in] `nID`  
 [in] `nCode`  
 [in] `pExtra`  
 [in] `pHandlerInfo`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="ondrawmenuimage"></a>COleIPFrameWndEx::OnDrawMenuImage  
 在绘制菜单项与相关联的映像时，由框架调用。  
  
```  
virtual BOOL OnDrawMenuImage(
    CDC* pDC,  
    const CMFCToolBarMenuButton* pMenuButton,  
    const CRect& rectImage);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向设备上下文的指针。  
  
 [in] `pMenuButton`  
 指针，指向菜单按钮。  
  
 [in] `rectImage`  
 与该菜单项关联的图像。  
  
### <a name="return-value"></a>返回值  
 默认实现不执行任何操作，并且返回 0。  
  
### <a name="remarks"></a>备注  
 重写此方法，如果您想要自定义绘制属于拥有的菜单栏的菜单项的图像`COleIPFrameWndEx`-派生的对象。  
  
##  <a name="ondrawmenulogo"></a>COleIPFrameWndEx::OnDrawMenuLogo  
 由框架调用时[CMFCPopupMenu](../../mfc/reference/cmfcpopupmenu-class.md)对象进程`WM_PAINT`消息。  
  
```  
virtual void OnDrawMenuLogo(
    CDC* pDC,  
    CMFCPopupMenu* pMenu,  
    const CRect& rectLogo);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 指向设备上下文的指针。  
  
 [in] `pMenu`  
 指向弹出菜单对象指针。  
  
 [in] `rectLogo`  
 指针，指向要显示的徽标。  
  
### <a name="remarks"></a>备注  
 重写此方法以在菜单栏中拥有的与关联的弹出菜单上显示的徽标`COleIPFrameWndEx`-派生的对象。 默认实现不执行任何操作。  
  
##  <a name="onmenubuttontoolhittest"></a>COleIPFrameWndEx::OnMenuButtonToolHitTest  
 由框架调用时[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)对象进程`WM_NCHITTEST`消息。  
  
```  
virtual BOOL OnMenuButtonToolHitTest(
    CMFCToolBarButton* pButton,  
    TOOLINFO* pTI);
```  
  
### <a name="parameters"></a>参数  
 [] in pButton  
 指针，指向菜单按钮。  
  
 [] out pTI  
 指向 `TOOLINFO` 结构的指针。  
  
### <a name="return-value"></a>返回值  
 默认实现不执行任何操作，并且返回 0。 您的实现应返回非零值，如果它已满`pTI`参数。  
  
### <a name="remarks"></a>备注  
 重写此方法以提供有关特定菜单项的工具提示信息。  
  
##  <a name="onmoveminiframe"></a>COleIPFrameWndEx::OnMoveMiniFrame  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```  
  
### <a name="parameters"></a>参数  
 [in] `pFrame`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="onsetpreviewmode"></a>COleIPFrameWndEx::OnSetPreviewMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void OnSetPreviewMode(
    BOOL bPreview,  
    CPrintPreviewState* pState);
```  
  
### <a name="parameters"></a>参数  
 [in] `bPreview`  
 [in] `pState`  
  
### <a name="remarks"></a>备注  
  
##  <a name="onshowcustomizepane"></a>COleIPFrameWndEx::OnShowCustomizePane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnShowCustomizePane(
    CMFCPopupMenu* pMenuPane,  
    UINT uiToolbarID);
```  
  
### <a name="parameters"></a>参数  
 [in] `pMenuPane`  
 [in] `uiToolbarID`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="onshowpanes"></a>COleIPFrameWndEx::OnShowPanes  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL OnShowPanes(BOOL bShow);
```  
  
### <a name="parameters"></a>参数  
 [in] `bShow`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="onshowpopupmenu"></a>COleIPFrameWndEx::OnShowPopupMenu  
 由框架调用时将显示一个弹出菜单。  
  
```  
virtual BOOL OnShowPopupMenu(CMFCPopupMenu* pMenuPopup);
```  
  
### <a name="parameters"></a>参数  
 `[in] pMenuPopup`  
 指针，指向要显示的弹出菜单。  
  
### <a name="return-value"></a>返回值  
 默认实现不执行任何操作，并返回一个非零值。 您的实现应返回`FALSE`如果不能显示弹出菜单。  
  
### <a name="remarks"></a>备注  
 重写此方法以自定义显示一个弹出菜单。 例如，可以将菜单按钮更改为颜色菜单按钮，或初始化拖曳条。  
  
##  <a name="ontearoffmenu"></a>COleIPFrameWndEx::OnTearOffMenu  
 当用户选择具有拖曳栏菜单上，由框架调用。  
  
```  
virtual BOOL OnTearOffMenu(
    CMFCPopupMenu* pMenuPopup,  
    CPane* pBar);
```  
  
### <a name="parameters"></a>参数  
 [in] `pMenuPopup`  
 指向用户所选的弹出菜单的指针。  
  
 [in] `pBar`  
 一个指向承载菜单中的窗格。  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果您希望框架，以激活弹出菜单。否则为`FALSE`。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
 如果您想要自定义拖曳栏的安装程序，重写此函数。  
  
##  <a name="panefrompoint"></a>COleIPFrameWndEx::PaneFromPoint  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    bool bExactBar,  
    CRuntimeClass* pRTCBarType) const;  
  
CBasePane* PaneFromPoint(
    CPoint point,  
    int nSensitivity,  
    DWORD& dwAlignment,  
    CRuntimeClass* pRTCBarType) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `point`  
 [in] `nSensitivity`  
 [in] `bExactBar`  
 [in] `pRTCBarType`  
 [in] `dwAlignment`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="pretranslatemessage"></a>COleIPFrameWndEx::PreTranslateMessage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>参数  
 [in] `pMsg`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="recalclayout"></a>COleIPFrameWndEx::RecalcLayout  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual void RecalcLayout(BOOL bNotify = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bNotify`  
  
### <a name="remarks"></a>备注  
  
##  <a name="removepanefromdockmanager"></a>COleIPFrameWndEx::RemovePaneFromDockManager  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void RemovePaneFromDockManager(
    CBasePane* pControlBar,  
    BOOL bDestroy,  
    BOOL bAdjustLayout,  
    BOOL bAutoHide,  
    CBasePane* pBarReplacement);
```  
  
### <a name="parameters"></a>参数  
 [in] `pControlBar`  
 [in] `bDestroy`  
 [in] `bAdjustLayout`  
 [in] `bAutoHide`  
 [in] `pBarReplacement`  
  
### <a name="remarks"></a>备注  
  
##  <a name="setdockstate"></a>COleIPFrameWndEx::SetDockState  
 将指定的插接状态应用到属于框架窗口的窗格。  
  
```  
void SetDockState(const CDockState& state);
```  
  
### <a name="parameters"></a>参数  
 [in] `state`  
 指定的插接状态。  
  
### <a name="remarks"></a>备注  
 使用此函数可指定的新的插接状态的窗格，其中属于`COleIPFrameWndEx`对象。  
  
##  <a name="setuptoolbarmenu"></a>COleIPFrameWndEx::SetupToolbarMenu  
 通过搜索虚拟项并将其替换为指定的用户定义项修改工具栏对象。  
  
```  
void SetupToolbarMenu(
    CMenu& menu,  
    const UINT uiViewUserToolbarCmdFirst,  
    const UINT uiViewUserToolbarCmdLast);
```  
  
### <a name="parameters"></a>参数  
 [in] `menu`  
 对引用[CMenu](../../mfc/reference/cmenu-class.md)要修改对象。  
  
 [in] `uiViewUserToolbarCmdFirst`  
 指定用户定义的第一个命令。  
  
 [in] `uiViewUserToolbarCmdLast`  
 指定用户定义的最后一个命令。  
  
### <a name="remarks"></a>备注  
  
##  <a name="showpane"></a>COleIPFrameWndEx::ShowPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
void ShowPane(
    CBasePane* pBar,  
    BOOL bShow,  
    BOOL bDelay,  
    BOOL bActivate);
```  
  
### <a name="parameters"></a>参数  
 [in] `pBar`  
 [in] `bShow`  
 [in] `bDelay`  
 [in] `bActivate`  
  
### <a name="remarks"></a>备注  
  
##  <a name="winhelpa"></a>COleIPFrameWndEx::WinHelpA  
 由框架调用以启动 WinHelp 应用程序或上下文帮助。  
  
```  
virtual void WinHelp(
    DWORD dwData,  
    UINT nCmd = HELP_CONTEXT);
```  
  
### <a name="parameters"></a>参数  
 [in] dwData  
 根据由 `nCmd`指定的帮助类型的要求指定数据。  
  
 [in] `nCmd`  
 指定请求的帮助的类型。 有关可能值的列表和这些值是如何影响 `dwData` 参数的相关信息，请参阅 Windows SDK 中的 [WinHelp 函数](http://msdn.microsoft.com/library/windows/desktop/bb762267) 。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [Cframewndex 由类](../../mfc/reference/cframewndex-class.md)   
 [CMDIFrameWndEx 类](../../mfc/reference/cmdiframewndex-class.md)

