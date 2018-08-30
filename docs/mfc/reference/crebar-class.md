---
title: CReBar 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CReBar
- AFXEXT/CReBar
- AFXEXT/CReBar::AddBar
- AFXEXT/CReBar::Create
- AFXEXT/CReBar::GetReBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- CReBar [MFC], AddBar
- CReBar [MFC], Create
- CReBar [MFC], GetReBarCtrl
ms.assetid: c1ad2720-1d33-4106-8e4e-80aa84f93559
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 61601baca7a91d76f473281184c335cc5277f815
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43201849"
---
# <a name="crebar-class"></a>CReBar 类
提供 Rebar 控件的布局、持久性和状态信息的控件条。  
  
## <a name="syntax"></a>语法  
  
```  
class CReBar : public CControlBar  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CReBar::AddBar](#addbar)|向 rebar 带区。|  
|[CReBar::Create](#create)|创建 rebar 控件，并将其附加到`CReBar`对象。|  
|[Crebar:: Getrebarctrl](#getrebarctrl)|允许直接访问基础公共控件。|  
  
## <a name="remarks"></a>备注  
 Rebar 对象可以包含各种子窗口，通常为其他控件，包括编辑框、工具栏和列表框。 Rebar 对象可以在指定位图上显示其子窗口。 你的应用程序可以自动调整大小 rebar，或用户可以通过单击或拖动其手柄栏来手动调整 rebar。  
  
 ![Rebarmenu 示例](../../mfc/reference/media/vc4sc61.gif "vc4sc61")  
  
## <a name="rebar-control"></a>Rebar 控件  
 Rebar 对象的行为类似于工具栏对象。 Rebar 控件使用单击和拖动机制来调整其带区的大小。 Rebar 控件可以包含一个或多个带区，每个带区都有手柄栏、位图、文本标签和子窗口的任意组合。 但是，带区不可包含多个子窗口。  
  
 `CReBar` 使用[CReBarCtrl](../../mfc/reference/crebarctrl-class.md)类以提供其实现。 您可以访问通过 rebar 控件[GetReBarCtrl](#getrebarctrl)以充分利用该控件的自定义选项。 Rebar 控件有关的详细信息，请参阅`CReBarCtrl`。 使用 rebar 控件的详细信息，请参阅[使用 CReBarCtrl](../../mfc/using-crebarctrl.md)。  
  
> [!CAUTION]
>  Rebar 和 rebar 控件对象不支持 MFC 控件条停靠。 如果`CRebar::EnableDocking`将断言应用程序的调用。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CReBar`  
  
## <a name="requirements"></a>要求  
 **标头：** afxext.h  
  
##  <a name="addbar"></a>  CReBar::AddBar  
 调用此成员函数以向 rebar 带区。  
  
```  
BOOL AddBar(
    CWnd* pBar,  
    LPCTSTR pszText = NULL,  
    CBitmap* pbmp = NULL,  
    DWORD dwStyle = RBBS_GRIPPERALWAYS | RBBS_FIXEDBMP);

 
BOOL AddBar(
    CWnd* pBar,  
    COLORREF clrFore,  
    COLORREF clrBack,  
    LPCTSTR pszText = NULL,  
    DWORD dwStyle = RBBS_GRIPPERALWAYS);
```  
  
### <a name="parameters"></a>参数  
 *pBar*  
 一个指向`CWnd`是要插入到 rebar 的子窗口的对象。 引用的对象必须具有 WS_CHILD。  
  
 *lpszText*  
 指向包含要在 rebar 上显示的文本的字符串的指针。 默认情况下为 NULL。 中包含的文本*lpszText*不属于的子窗口; 它位于 rebar 本身上。  
  
 *pbmp*  
 一个指向`CBitmap`rebar 背景上显示的对象。 默认情况下为 NULL。  
  
 *dwStyle*  
 一个 dword 值，包含的样式应用于 rebar。 请参阅`fStyle`函数在 Win32 结构中的说明[REBARBANDINFO](/windows/desktop/api/commctrl/ns-commctrl-tagrebarbandinfoa)有关带样式的完整列表。  
  
 *clrFore*  
 一个 COLORREF 值，该值表示 rebar 的前景色。  
  
 *clrBack*  
 一个 COLORREF 值，该值表示 rebar 的背景色。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl#1](../../mfc/reference/codesnippet/cpp/crebar-class_1.cpp)]  
  
##  <a name="create"></a>  CReBar::Create  
 调用此成员函数来创建 rebar 控件。  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = RBS_BANDBORDERS,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,  
    UINT nID = AFX_IDW_REBAR);
```  
  
### <a name="parameters"></a>参数  
 *pParentWnd*  
 指向`CWnd`其 Windows 窗口是状态栏的父对象。 通常情况下您的框架窗口。  
  
 *dwCtrlStyle*  
 Rebar 控件样式。 默认情况下，RBS_BANDBORDERS，其中显示了窄行来分隔相邻 rebar 控件中的带区。 请参阅[Rebar 控件样式](/windows/desktop/Controls/rebar-control-styles)Windows SDK for 样式的列表中。  
  
 *dwStyle*  
 Rebar 的窗口样式。  
  
 *nID*  
 Rebar 的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CReBar::AddBar](#addbar)。  
  
##  <a name="getrebarctrl"></a>  Crebar:: Getrebarctrl  
 此成员函数允许直接访问基础公共控件。  
  
```  
CReBarCtrl& GetReBarCtrl() const;  
```  
  
### <a name="return-value"></a>返回值  
 对引用[CReBarCtrl](../../mfc/reference/crebarctrl-class.md)对象。  
  
### <a name="remarks"></a>备注  
 调用此成员函数以充分利用 Windows rebar 公共控件中自定义你 rebar 的功能。 当您调用`GetReBarCtrl`，它返回引用对象到`CReBarCtrl`对象，以便可以使用任何一个的成员函数集。  
  
 有关使用详细信息`CReBarCtrl`若要自定义你 rebar，请参阅[使用 CReBarCtrl](../../mfc/using-crebarctrl.md)。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl#2](../../mfc/reference/codesnippet/cpp/crebar-class_2.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 MFCIE](../../visual-cpp-samples.md)   
 [CControlBar 类](../../mfc/reference/ccontrolbar-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)



