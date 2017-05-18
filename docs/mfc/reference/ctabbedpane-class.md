---
title: "CTabbedPane 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTabbedPane
- AFXTABBEDPANE/CTabbedPane
- AFXTABBEDPANE/CTabbedPane::DetachPane
- AFXTABBEDPANE/CTabbedPane::EnableTabAutoColor
- AFXTABBEDPANE/CTabbedPane::FloatTab
- AFXTABBEDPANE/CTabbedPane::GetTabArea
- AFXTABBEDPANE/CTabbedPane::GetTabWnd
- AFXTABBEDPANE/CTabbedPane::HasAutoHideMode
- AFXTABBEDPANE/CTabbedPane::IsTabLocationBottom
- AFXTABBEDPANE/CTabbedPane::ResetTabs
- AFXTABBEDPANE/CTabbedPane::SetTabAutoColors
- AFXTABBEDPANE/CTabbedPane::m_bTabsAlwaysTop
- AFXTABBEDPANE/CTabbedPane::m_pTabWndRTC
dev_langs:
- C++
helpviewer_keywords:
- CTabbedPane class
ms.assetid: f4dc5215-b789-4f2d-8c62-477aceda3578
caps.latest.revision: 27
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
ms.openlocfilehash: 70377d6be8ef4ec957c7270e501022107d4b093c
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="ctabbedpane-class"></a>CTabbedPane 类
利用可拆分的选项卡实现窗格的功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CTabbedPane : public CBaseTabbedPane  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|`CTabbedPane::CTabbedPane`|默认构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CTabbedPane::DetachPane](#detachpane)|(重写[CBaseTabbedPane::DetachPane](../../mfc/reference/cbasetabbedpane-class.md#detachpane)。)|  
|[CTabbedPane::EnableTabAutoColor](#enabletabautocolor)|启用或禁用自动选项卡着色。|  
|[CTabbedPane::FloatTab](#floattab)|仅当窗格中当前驻留在拆离的选项卡中时浮动窗格。 (重写[CBaseTabbedPane::FloatTab](../../mfc/reference/cbasetabbedpane-class.md#floattab)。)|  
|[CTabbedPane::GetTabArea](#gettabarea)|返回选项卡区域在选项卡式窗口中的大小和位置。|  
|[CTabbedPane::GetTabWnd](#gettabwnd)||  
|[CTabbedPane::HasAutoHideMode](#hasautohidemode)|确定选项卡式窗格是否可以切换为自动隐藏模式。 (重写[CBaseTabbedPane::HasAutoHideMode](../../mfc/reference/cbasetabbedpane-class.md#hasautohidemode)。)|  
|[CTabbedPane::IsTabLocationBottom](#istablocationbottom)|确定选项卡是否位于窗口的底部。|  
|[CTabbedPane::ResetTabs](#resettabs)|将所有选项卡式窗格重置为默认状态。|  
|[CTabbedPane::SetTabAutoColors](#settabautocolors)|设置可以在自动颜色功能启用时可用的自定义颜色列表。|  
  
### <a name="data-members"></a>数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CTabbedPane::m_bTabsAlwaysTop](#m_btabsalwaystop)|选项卡在应用程序中的的默认位置。|  
|[CTabbedPane::m_pTabWndRTC](#m_ptabwndrtc)|自定义 `CMFCTabCtrl`-派生对象的运行时类信息。|  
  
## <a name="remarks"></a>备注  
 当用户通过将一个窗格指向第二个窗格的标题的方式来附加到另一个窗格，框架自动创建此类的实例。 由框架创建的所有选项卡式窗格都具有值为 -1 的 ID。  
  
 若要指定而不是 Outlook 样式的选项卡的常规选项卡，请将传递`AFX_CBRS_REGULAR_TABS`到样式[CDockablePane::CreateEx](../../mfc/reference/cdockablepane-class.md#createex)方法。  
  
 如果你使用可拆离的选项卡创建一个选项卡式窗格，该窗格可能会被框架自动销毁，因此，你不应该存储该指针。 若要获取对选项卡式窗格的指针，请调用 `CBasePane::GetParentTabbedPane` 方法。  
  
## <a name="example"></a>示例  
 我们在此示例中创建了一个 `CTabbedPane` 对象。 接下来，我们使用[CBaseTabbedPane::AddTab](../../mfc/reference/cbasetabbedpane-class.md#addtab)要附加的其他选项卡。  
  
```  
CTabbedPane* pTabbededBar = new CTabbedPane (TRUE);

if (!pTabbededBar->Create (_T(""),
    this,
    CRect (0,
    0,
    200,
    200),  
    TRUE, 
 (UINT) -1,  
    WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS |  
    WS_CLIPCHILDREN | CBRS_LEFT |    
    CBRS_FLOAT_MULTI)) 
{  
    TRACE0("Failed to create Solution Explorer bar\n");

    return FALSE;      // fail to create  
}  
 
pTabbededBar->AddTab (&m_wndClassView);
pTabbededBar->AddTab (&m_wndResourceView);

pTabbededBar->AddTab (&m_wndFileView);
pTabbededBar->EnableDocking(CBRS_ALIGN_ANY);

DockPane(pTabbededBar);
```  
  
## <a name="example"></a>示例  
 若要创建选项卡式的控件条对象的另一种方法是使用[CDockablePane::AttachToTabWnd](../../mfc/reference/cdockablepane-class.md#attachtotabwnd)。 `AttachToTabWnd`方法动态地创建使用运行时类信息设置的选项卡式的窗格对象[CDockablePane::SetTabbedPaneRTC](../../mfc/reference/cdockablepane-class.md#settabbedpanertc)。  
  
 在此示例中，我们动态地创建了一个选项卡式窗格，附加这两个选项卡，并使第二个选项不可拆离。  
  
```  
DockPane(&m_wndClassView);

CTabbedPane* pTabbedBar = NULL;  
m_wndResourceView.AttachToTabWnd (&m_wndClassView,
    DM_SHOW,
    TRUE,  
 (CDockablePane**) &pTabbedBar);

m_wndFileView.AttachToTabWnd (pTabbedBar,
    DM_SHOW,
    TRUE,  
 (CDockablePane**) &pTabbedBar);

pTabbedBar->GetUnderlyingWindow ()->EnableTabDetach (1,
    FALSE);
```  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md)  
  
 [CPane](../../mfc/reference/cpane-class.md)  
  
 [CDockablePane](../../mfc/reference/cdockablepane-class.md)  
  
 [CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)  
  
 [CTabbedPane](../../mfc/reference/ctabbedpane-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxTabbedPane.h  
  
##  <a name="detachpane"></a>CTabbedPane::DetachPane  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL DetachPane(
    CWnd* pBar,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pBar`  
 [in] `bHide`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="enabletabautocolor"></a>CTabbedPane::EnableTabAutoColor  
 启用或禁用自动选项卡着色。  
  
```  
static void EnableTabAutoColor(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE`若要启用自动着色的选项卡。否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此静态方法用于启用或禁用自动着色的应用程序中的所有选项卡式窗格中的选项卡。 启用此功能后，由它自己的颜色填充每个选项卡。 您可以找到的用于通过调用颜色选项卡的颜色列表[CMFCBaseTabCtrl::GetAutoColors](../../mfc/reference/cmfcbasetabctrl-class.md#getautocolors)方法。  
  
 您可以指定将通过调用使用选项卡的颜色的列表[CTabbedPane::SetTabAutoColors](#settabautocolors)。  
  
 默认情况下，禁用此选项。  
  
##  <a name="floattab"></a>CTabbedPane::FloatTab  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL FloatTab(
    CWnd* pBar,  
    int nTabID,  
    AFX_DOCK_METHOD dockMethod,  
    BOOL bHide = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `pBar`  
 [in] `nTabID`  
 [in] `dockMethod`  
 [in] `bHide`  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="gettabarea"></a>CTabbedPane::GetTabArea  
 返回选项卡式窗口中的大小和选项卡区域的位置。  
  
```  
virtual void GetTabArea(
    CRect& rectTabAreaTop,  
    CRect& rectTabAreaBottom) const;  
```  
  
### <a name="parameters"></a>参数  
 [out] `rectTabAreaTop`  
 包含的大小和位置，在屏幕坐标中的顶级选项卡区域。  
  
 [out] `rectTabAreaBottom`  
 包含的大小和位置，在屏幕坐标中的选项卡区域底部。  
  
### <a name="remarks"></a>备注  
 框架调用此方法以确定如何将用户正在拖动窗格停靠。 当用户将一个窗格拖到目标窗格中的选项卡区域中时，框架会尝试将其添加为目标窗格中的新选项卡。 否则，它尝试将窗格停靠到的目标窗格中，这涉及创建一个新的窗格中容器与窗格分隔符分隔两个窗格一侧。  
  
 重写此方法在`CTabbedPane`的派生类来更改此行为。  
  
##  <a name="gettabwnd"></a>CTabbedPane::GetTabWnd  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCTabCtrl* GetTabWnd() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="hasautohidemode"></a>CTabbedPane::HasAutoHideMode  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL HasAutoHideMode() const;  
```  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
  
##  <a name="istablocationbottom"></a>CTabbedPane::IsTabLocationBottom  
 确定选项卡是否位于窗口的底部。  
  
```  
virtual BOOL IsTabLocationBottom() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果选项卡区域位于底部的选项卡式窗口;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="m_btabsalwaystop"></a>CTabbedPane::m_bTabsAlwaysTop  
 选项卡在应用程序中的的默认位置。  
  
```  
AFX_IMPORT_DATA static BOOL m_bTabsAlwaysTop;  
```  
  
### <a name="remarks"></a>备注  
 此静态成员设置为`TRUE`以强制应用程序将显示在选项卡式窗格顶部中的所有选项卡。  
  
 在创建选项卡式窗格中之前，必须设置此值。  
  
 默认值为 `FALSE`。  
  
##  <a name="m_ptabwndrtc"></a>CTabbedPane::m_pTabWndRTC  
 自定义 `CMFCTabCtrl`-派生对象的运行时类信息。  
  
```  
AFX_IMPORT_DATA static CRuntimeClass* m_pTabWndRTC;  
```  
  
### <a name="remarks"></a>备注  
 将此静态成员变量设置为指向运行时类信息的`CMFCTabCtrl`-如果您使用的在选项卡式窗格内的自定义选项卡式的窗口派生的对象。  
  
##  <a name="resettabs"></a>CTabbedPane::ResetTabs  
 将所有选项卡式窗格重置为默认状态。  
  
```  
static void ResetTabs();
```  
  
### <a name="remarks"></a>备注  
 调用此方法，以还原为其默认状态的所有选项卡式的窗格。 在调用时，此方法将重置的边框大小和自动颜色状态的所有选项卡式窗格。  
  
##  <a name="settabautocolors"></a>CTabbedPane::SetTabAutoColors  
 设置启用自动的颜色特征时使用的自定义颜色的列表。  
  
```  
static void SetTabAutoColors(const CArray<COLORREF, COLORREF>& arColors);
```  
  
### <a name="parameters"></a>参数  
 [in] `arColors`  
 包含要设置的颜色数组。  
  
### <a name="remarks"></a>备注  
 使用此方法自定义的启用自动的颜色特征时使用的颜色列表。 这是一个静态函数，并且会影响您的应用程序中的所有选项卡式的窗格。  
  
 使用[CTabbedPane::EnableTabAutoColor](#enabletabautocolor)若要启用或禁用自动颜色功能。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CDockablePane 类](../../mfc/reference/cdockablepane-class.md)   
 [CBaseTabbedPane 类](../../mfc/reference/cbasetabbedpane-class.md)   
 [CMFCOutlookBar 类](../../mfc/reference/cmfcoutlookbar-class.md)

