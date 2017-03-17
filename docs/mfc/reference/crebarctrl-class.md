---
title: "CReBarCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CReBarCtrl
- AFXCMN/CReBarCtrl
- AFXCMN/CReBarCtrl::CReBarCtrl
- AFXCMN/CReBarCtrl::BeginDrag
- AFXCMN/CReBarCtrl::Create
- AFXCMN/CReBarCtrl::CreateEx
- AFXCMN/CReBarCtrl::DeleteBand
- AFXCMN/CReBarCtrl::DragMove
- AFXCMN/CReBarCtrl::EndDrag
- AFXCMN/CReBarCtrl::GetBandBorders
- AFXCMN/CReBarCtrl::GetBandCount
- AFXCMN/CReBarCtrl::GetBandInfo
- AFXCMN/CReBarCtrl::GetBandMargins
- AFXCMN/CReBarCtrl::GetBarHeight
- AFXCMN/CReBarCtrl::GetBarInfo
- AFXCMN/CReBarCtrl::GetBkColor
- AFXCMN/CReBarCtrl::GetColorScheme
- AFXCMN/CReBarCtrl::GetDropTarget
- AFXCMN/CReBarCtrl::GetExtendedStyle
- AFXCMN/CReBarCtrl::GetImageList
- AFXCMN/CReBarCtrl::GetPalette
- AFXCMN/CReBarCtrl::GetRect
- AFXCMN/CReBarCtrl::GetRowCount
- AFXCMN/CReBarCtrl::GetRowHeight
- AFXCMN/CReBarCtrl::GetTextColor
- AFXCMN/CReBarCtrl::GetToolTips
- AFXCMN/CReBarCtrl::HitTest
- AFXCMN/CReBarCtrl::IDToIndex
- AFXCMN/CReBarCtrl::InsertBand
- AFXCMN/CReBarCtrl::MaximizeBand
- AFXCMN/CReBarCtrl::MinimizeBand
- AFXCMN/CReBarCtrl::MoveBand
- AFXCMN/CReBarCtrl::PushChevron
- AFXCMN/CReBarCtrl::RestoreBand
- AFXCMN/CReBarCtrl::SetBandInfo
- AFXCMN/CReBarCtrl::SetBandWidth
- AFXCMN/CReBarCtrl::SetBarInfo
- AFXCMN/CReBarCtrl::SetBkColor
- AFXCMN/CReBarCtrl::SetColorScheme
- AFXCMN/CReBarCtrl::SetExtendedStyle
- AFXCMN/CReBarCtrl::SetImageList
- AFXCMN/CReBarCtrl::SetOwner
- AFXCMN/CReBarCtrl::SetPalette
- AFXCMN/CReBarCtrl::SetTextColor
- AFXCMN/CReBarCtrl::SetToolTips
- AFXCMN/CReBarCtrl::SetWindowTheme
- AFXCMN/CReBarCtrl::ShowBand
- AFXCMN/CReBarCtrl::SizeToRect
dev_langs:
- C++
helpviewer_keywords:
- rebar controls, control bar
- rebar controls, CReBarCtrl class
- CReBarCtrl class
ms.assetid: 154570d7-e48c-425d-8c7e-c64542bcb4cc
caps.latest.revision: 23
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
ms.openlocfilehash: c1da4de2897c74e9cb25bc060033f4bd43159174
ms.lasthandoff: 02/24/2017

---
# <a name="crebarctrl-class"></a>CReBarCtrl 类
封装 Rebar 控件的功能，此控件是一个子窗口容器。  
  
## <a name="syntax"></a>语法  
  
```  
class CReBarCtrl : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CReBarCtrl::CReBarCtrl](#crebarctrl)|构造 `CReBarCtrl` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CReBarCtrl::BeginDrag](#begindrag)|将 rebar 控件放置到拖放模式。|  
|[CReBarCtrl::Create](#create)|创建 rebar 控件并将其附加到`CReBarCtrl`对象。|  
|[CReBarCtrl::CreateEx](#createex)|与指定的 Windows 扩展样式创建 rebar 控件，并将其附加到`CReBarCtrl`对象。|  
|[CReBarCtrl::DeleteBand](#deleteband)|删除从 rebar 控件带区。|  
|[CReBarCtrl::DragMove](#dragmove)|在调用后更新 rebar 控件中的拖动位置`BeginDrag`。|  
|[CReBarCtrl::EndDrag](#enddrag)|Rebar 控件的拖放操作将终止。|  
|[CReBarCtrl::GetBandBorders](#getbandborders)|检索一个带边框。|  
|[CReBarCtrl::GetBandCount](#getbandcount)|检索带区 rebar 控件中的当前的计数。|  
|[CReBarCtrl::GetBandInfo](#getbandinfo)|检索有关指定带区的 rebar 控件中的信息。|  
|[CReBarCtrl::GetBandMargins](#getbandmargins)|检索一个带的边距。|  
|[CReBarCtrl::GetBarHeight](#getbarheight)|检索 rebar 控件的高度。|  
|[CReBarCtrl::GetBarInfo](#getbarinfo)|检索有关 rebar 控件和它所使用的图像列表的信息。|  
|[CReBarCtrl::GetBkColor](#getbkcolor)|检索 rebar 控件的默认背景色。|  
|[CReBarCtrl::GetColorScheme](#getcolorscheme)|检索[要添加的配色](http://msdn.microsoft.com/library/windows/desktop/bb775502)与 rebar 控件关联的结构。|  
|[CReBarCtrl::GetDropTarget](#getdroptarget)|检索 rebar 控件的`IDropTarget`接口指针。|  
|[CReBarCtrl::GetExtendedStyle](#getextendedstyle)|获取当前的 rebar 控件的扩展的样式。|  
|[CReBarCtrl::GetImageList](#getimagelist)|检索与 rebar 控件关联的图像列表。|  
|[CReBarCtrl::GetPalette](#getpalette)|检索 rebar 控件的当前调色板。|  
|[CReBarCtrl::GetRect](#getrect)|检索给定带区的 rebar 控件中的绑定矩形。|  
|[CReBarCtrl::GetRowCount](#getrowcount)|检索 rebar 控件中的带行的数。|  
|[CReBarCtrl::GetRowHeight](#getrowheight)|检索 rebar 控件中指定行的高度。|  
|[CReBarCtrl::GetTextColor](#gettextcolor)|检索 rebar 控件的默认文本颜色。|  
|[CReBarCtrl::GetToolTips](#gettooltips)|检索与 rebar 控件相关联的所有工具提示控件的句柄。|  
|[CReBarCtrl::HitTest](#hittest)|确定如果 rebar 带区在该点存在的 rebar 带区的哪个部分是在屏幕上，给定时刻。|  
|[CReBarCtrl::IDToIndex](#idtoindex)|将带标识符 (ID) 转换为 rebar 控件中的带索引。|  
|[Crebarctrl:: Insertband](#insertband)|在 rebar 控件中插入新的带区。|  
|[CReBarCtrl::MaximizeBand](#maximizeband)|调整到最大尺寸 rebar 控件中的带。|  
|[CReBarCtrl::MinimizeBand](#minimizeband)|大小调整回其最小大小的 rebar 控件中的带。|  
|[CReBarCtrl::MoveBand](#moveband)|将带区从一个索引移到另一个。|  
|[CReBarCtrl::PushChevron](#pushchevron)|以编程方式将推送 v 形。|  
|[CReBarCtrl::RestoreBand](#restoreband)|大小调整回其理想大小 rebar 控件中的带。|  
|[CReBarCtrl::SetBandInfo](#setbandinfo)|Rebar 控件中设置现有带的特征。|  
|[CReBarCtrl::SetBandWidth](#setbandwidth)|对于当前的 rebar 控件中设置指定的停靠带区的宽度。|  
|[CReBarCtrl::SetBarInfo](#setbarinfo)|设置 rebar 控件的特征。|  
|[CReBarCtrl::SetBkColor](#setbkcolor)|设置 rebar 控件的默认背景色。|  
|[CReBarCtrl::SetColorScheme](#setcolorscheme)|在 rebar 控件上设置按钮的配色方案。|  
|[CReBarCtrl::SetExtendedStyle](#setextendedstyle)|设置当前的 rebar 控件的扩展的样式。|  
|[CReBarCtrl::SetImageList](#setimagelist)|设置 rebar 控件的图像列表。|  
|[CReBarCtrl::SetOwner](#setowner)|设置 rebar 控件的所有者窗口。|  
|[CReBarCtrl::SetPalette](#setpalette)|设置 rebar 控件的当前调色板。|  
|[CReBarCtrl::SetTextColor](#settextcolor)|设置 rebar 控件的默认文本颜色。|  
|[CReBarCtrl::SetToolTips](#settooltips)|将工具提示控件与 rebar 控件相关联。|  
|[CReBarCtrl::SetWindowTheme](#setwindowtheme)|设置 rebar 控件的视觉样式。|  
|[CReBarCtrl::ShowBand](#showband)|显示或隐藏 rebar 控件中的给定的带。|  
|[CReBarCtrl::SizeToRect](#sizetorect)|适合 rebar 控件与指定的矩形。|  
  
## <a name="remarks"></a>备注  
 在 rebar 控件所在的应用程序将分配到 rebar 带区的 rebar 控件所包含的子窗口。 子窗口是通常为另一公共控件。  
  
 Rebar 控件包含一个或多个带区。 每个带区可以包含一个手柄栏、 位图、 文本标签和子窗口的组合。 带区只能包含一个的每个项。  
  
 Rebar 控件可以在指定的背景位图上显示的子窗口。 所有的 rebar 控件带区的大小可以调整，除了那些使用**RBBS_FIXEDSIZE**样式。 当您重新定位或调整 rebar 控件带区的大小，rebar 控件管理的大小和位置分配到该带区的子窗口。 若要调整大小或更改的控件中的带区的顺序，单击并拖动带区的手柄栏。  
  
 下图显示了具有三个带区的 rebar 控件︰  
  
-   带区 0 包含平面、 透明工具栏控件。  
  
-   1 一个带区包含两个透明的标准和透明下拉按钮。  
  
-   2 一个带区包含一个组合框和四个标准按钮。  
  
     ![Rebar 菜单示例](../../mfc/reference/media/vc4scc1.gif "vc4scc1")  
  
## <a name="rebar-control"></a>Rebar 控件  
 Rebar 控件的支持︰  
  
-   图像列表。  
  
-   消息处理。  
  
-   自定义绘制功能。  
  
-   除了标准的窗口样式的控件样式多种。 有关这些样式的列表，请参阅[Rebar 控件样式](http://msdn.microsoft.com/library/windows/desktop/bb774377)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 有关详细信息，请参阅[使用 CReBarCtrl](../../mfc/using-crebarctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CReBarCtrl`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcmn.h  
  
##  <a name="begindrag"></a>CReBarCtrl::BeginDrag  
 实现的行为的 Win32 消息[RB_BEGINDRAG](http://msdn.microsoft.com/library/windows/desktop/bb774429)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
void BeginDrag(
    UINT uBand,  
    DWORD dwPos = (DWORD)-1);
```  
  
### <a name="parameters"></a>参数  
 `uBand`  
 拖放操作将影响的带区的从零开始索引。  
  
 `dwPos`  
 一个`DWORD`值，该值包含起始鼠标坐标。 水平坐标包含在 LOWORD 并且 HIWORD 中包含的垂直坐标。 如果您通过`(DWORD)-1`，rebar 控件将使用上一次调用控件的线程的鼠标位置**GetMessage**或**PeekMessage**。  
  
##  <a name="create"></a>CReBarCtrl::Create  
 创建 rebar 控件并将其附加到`CReBarCtrl`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 指定应用于控件的 rebar 控件样式的组合。 请参阅[Rebar 控件样式](http://msdn.microsoft.com/library/windows/desktop/bb774377)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]有关受支持的样式的列表。  
  
 `rect`  
 对引用[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它是位置和 rebar 控件的大小。  
  
 `pParentWnd`  
 一个指向[CWnd](../../mfc/reference/cwnd-class.md)是 rebar 控件的父窗口的对象。 它不能**NULL**。  
  
 `nID`  
 指定 rebar 控件的控件 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则创建对象时，非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 在两个步骤中创建 rebar 控件︰  
  
1.  调用[CReBarCtrl](#crebarctrl)构造`CReBarCtrl`对象。  
  
2.  调用此成员函数，它能创建 Windows rebar 控件并将其附加到`CReBarCtrl`对象。  
  
 当您调用**创建**，常见的控件进行了初始化。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl #&3;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_1.cpp)]  
  
##  <a name="createex"></a>CReBarCtrl::CreateEx  
 创建控件 （子窗口），并将其与相关联`CReBarCtrl`对象。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwExStyle`  
 指定要创建的控件的扩展的样式。 扩展窗口样式的列表，请参阅`dwExStyle`参数[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwStyle`  
 指定应用于控件的 rebar 控件样式的组合。 有关受支持的样式的列表，请参阅[Rebar 控件样式](http://msdn.microsoft.com/library/windows/desktop/bb774377)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `rect`  
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构的结构描述的大小和窗口，在中创建的工作区坐标位置`pParentWnd`。  
  
 `pParentWnd`  
 指向控件的父级的窗口的指针。  
  
 `nID`  
 控件的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 使用`CreateEx`而不是[创建](#create)应用扩展的窗口样式、 指定的 Windows 扩展的样式前言**WS_EX_**。  
  
##  <a name="crebarctrl"></a>CReBarCtrl::CReBarCtrl  
 创建一个 `CReBarCtrl` 对象。  
  
```  
CReBarCtrl();
```  
  
### <a name="example"></a>示例  
  请参阅示例[CReBarCtrl::Create](#create)。  
  
##  <a name="deleteband"></a>CReBarCtrl::DeleteBand  
 实现的行为的 Win32 消息[RB_DELETEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774431)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
BOOL DeleteBand(UINT uBand);
```  
  
### <a name="parameters"></a>参数  
 `uBand`  
 要删除的带区的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 非零，如果成功，则删除带区否则为零。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl #&4;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_2.cpp)]  
  
##  <a name="dragmove"></a>CReBarCtrl::DragMove  
 实现的行为的 Win32 消息[RB_DRAGMOVE](https://msdn.microsoft.com/library/bb774433.aspx)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
void DragMove(DWORD dwPos = (DWORD)-1);
```  
  
### <a name="parameters"></a>参数  
 `dwPos`  
 一个`DWORD`值，该值包含新的鼠标坐标。 水平坐标包含在 LOWORD 并且 HIWORD 中包含的垂直坐标。 如果您通过`(DWORD)-1`，rebar 控件将使用上一次调用控件的线程的鼠标位置**GetMessage**或**PeekMessage**。  
  
##  <a name="enddrag"></a>CReBarCtrl::EndDrag  
 实现的行为的 Win32 消息[RB_ENDDRAG](http://msdn.microsoft.com/library/windows/desktop/bb774435)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
void EndDrag();
```  
  
##  <a name="getbandborders"></a>CReBarCtrl::GetBandBorders  
 实现的行为的 Win32 消息[RB_GETBANDBORDERS](http://msdn.microsoft.com/library/windows/desktop/bb774437)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
void GetBandBorders(
    UINT uBand,  
    LPRECT prc) const;  
```  
  
### <a name="parameters"></a>参数  
 `uBand`  
 将为其检索边框的带区的从零开始索引。  
  
 `prc`  
 一个指向[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它将收到带边框。 如果 rebar 控件具有**RBS_BANDBORDERS**样式，此结构的每个成员将收到的像素数，在相应的一端带，构成边框。 如果 rebar 控件不具有**RBS_BANDBORDERS**样式，仅此结构的左侧的成员收到有效信息。 Rebar 控件样式的说明，请参阅[Rebar 控件样式](http://msdn.microsoft.com/library/windows/desktop/bb774377)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getbandcount"></a>CReBarCtrl::GetBandCount  
 实现的行为的 Win32 消息[RB_GETBANDCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb774439)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
UINT GetBandCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 分配给控件的带区的数目。  
  
##  <a name="getbandinfo"></a>CReBarCtrl::GetBandInfo  
 实现的行为的 Win32 消息[RB_GETBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774451)中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
BOOL GetBandInfo(
    UINT uBand,  
    REBARBANDINFO* prbbi) const;  
```  
  
### <a name="parameters"></a>参数  
 `uBand`  
 将为其检索信息的带区的从零开始索引。  
  
 `prbbi`  
 一个指向[REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393)接收带信息的结构。 必须设置`cbSize`到此结构的成员`sizeof(REBARBANDINFO)`并设置**fMask**到您想要发送此消息之前检索的项的成员。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
##  <a name="getbandmargins"></a>CReBarCtrl::GetBandMargins  
 检索的带区的边距。  
  
```  
void GetBandMargins(PMARGINS pMargins);
```  
  
### <a name="parameters"></a>参数  
 *pMargins*  
 一个指向[边距](http://msdn.microsoft.com/library/windows/desktop/bb773244)结构，它将会收到信息。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[RB_GETBANDMARGINS](http://msdn.microsoft.com/library/windows/desktop/bb774453)消息，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getbarheight"></a>CReBarCtrl::GetBarHeight  
 检索 rebar 栏的高度。  
  
```  
UINT GetBarHeight() const;  
```  
  
### <a name="return-value"></a>返回值  
 表示高度 （像素），该控件的值。  
  
##  <a name="getbarinfo"></a>CReBarCtrl::GetBarInfo  
 实现的行为的 Win32 消息[RB_GETBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774457)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
BOOL GetBarInfo(REBARINFO* prbi) const;  
```  
  
### <a name="parameters"></a>参数  
 `prbi`  
 一个指向[REBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774395)结构，它将会收到 rebar 控件的信息。 必须设置`cbSize`到此结构的成员`sizeof(REBARINFO)`发送此消息之前。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
##  <a name="getbkcolor"></a>CReBarCtrl::GetBkColor  
 实现的行为的 Win32 消息[RB_GETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774459)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个**COLORREF**值，该值表示当前的默认背景色。  
  
##  <a name="getcolorscheme"></a>CReBarCtrl::GetColorScheme  
 检索[要添加的配色](http://msdn.microsoft.com/library/windows/desktop/bb775502)rebar 控件的结构。  
  
```  
BOOL GetColorScheme(COLORSCHEME* lpcs);
```  
  
### <a name="parameters"></a>参数  
 `lpcs`  
 一个指向[要添加的配色](http://msdn.microsoft.com/library/windows/desktop/bb775502)结构，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 **要添加的配色**结构包括按钮突出显示颜色和按钮阴影颜色。  
  
##  <a name="getdroptarget"></a>CReBarCtrl::GetDropTarget  
 实现的行为的 Win32 消息[RB_GETDROPTARGET](http://msdn.microsoft.com/library/windows/desktop/bb774463)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
IDropTarget* GetDropTarget() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向[IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)接口。  
  
##  <a name="getextendedstyle"></a>CReBarCtrl::GetExtendedStyle  
 获取当前的 rebar 控件的扩展的样式。  
  
```  
DWORD GetExtendedStyle() const;  
```  
  
### <a name="return-value"></a>返回值  
 指示扩展的样式的标志的按位组合 (OR)。 可能的标志`RBS_EX_SPLITTER`和`RBS_EX_TRANSPARENT`。 有关详细信息，请参阅`dwMask`参数[CReBarCtrl::SetExtendedStyle](#setextendedstyle)方法。  
  
### <a name="remarks"></a>备注  
 此方法可发送[RB_GETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb774433)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getimagelist"></a>CReBarCtrl::GetImageList  
 获取`CImageList`与 rebar 控件关联的对象。  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向[CImageList](../../mfc/reference/cimagelist-class.md)对象。 返回**NULL**如果任何图像列表不设置为该控件。  
  
### <a name="remarks"></a>备注  
 此成员函数使用大小和掩码信息存储在[REBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774395)结构，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getpalette"></a>CReBarCtrl::GetPalette  
 检索 rebar 控件的当前调色板。  
  
```  
CPalette* GetPalette() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向[CPalette](../../mfc/reference/cpalette-class.md)对象，它指定 rebar 控件的当前调色板。  
  
### <a name="remarks"></a>备注  
 请注意，此成员函数使用`CPalette`对象作为其返回值，而不是以`HPALETTE`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl #&5;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_3.cpp)]  
  
##  <a name="getrect"></a>CReBarCtrl::GetRect  
 实现的行为的 Win32 消息[RB_GETRECT](http://msdn.microsoft.com/library/windows/desktop/bb774469)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
BOOL GetRect(
    UINT uBand,  
    LPRECT prc) const;  
```  
  
### <a name="parameters"></a>参数  
 `uBand`  
 在 rebar 控件带区的从零开始索引。  
  
 `prc`  
 一个指向[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它将接收 rebar 带区的边界。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl #&6;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_4.cpp)]  
  
##  <a name="getrowcount"></a>CReBarCtrl::GetRowCount  
 实现的行为的 Win32 消息[RB_GETROWCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb774471)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
UINT GetRowCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个**UINT**值，该值表示在控件中的带行数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl #&7;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_5.cpp)]  
  
##  <a name="getrowheight"></a>CReBarCtrl::GetRowHeight  
 实现的行为的 Win32 消息[RB_GETROWHEIGHT](http://msdn.microsoft.com/library/windows/desktop/bb774473)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
UINT GetRowHeight(UINT uRow) const;  
```  
  
### <a name="parameters"></a>参数  
 *uRow*  
 将具有检索窗体的高度的带区的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 一个**UINT**值，该值表示行高度，以像素为单位。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl #&8;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_6.cpp)]  
  
##  <a name="gettextcolor"></a>CReBarCtrl::GetTextColor  
 实现的行为的 Win32 消息[RB_GETTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774475)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
COLORREF GetTextColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个**COLORREF**值，该值表示当前的默认文本颜色。  
  
##  <a name="gettooltips"></a>CReBarCtrl::GetToolTips  
 实现的行为的 Win32 消息[RB_GETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb774477)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)对象。  
  
### <a name="remarks"></a>备注  
 请注意，MFC 实现`GetToolTips`返回一个指向`CToolTipCtrl`，而不是以`HWND`。  
  
##  <a name="hittest"></a>CReBarCtrl::HitTest  
 实现的行为的 Win32 消息[RB_HITTEST](http://msdn.microsoft.com/library/windows/desktop/bb774494)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
int HitTest(RBHITTESTINFO* prbht);
```  
  
### <a name="parameters"></a>参数  
 *prbht*  
 一个指向[RBHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb774391)结构。 发送消息前, **pt**此结构的成员必须初始化为将进行一对一测试，在工作区坐标的点。  
  
### <a name="return-value"></a>返回值  
 在给定的时间，则为-1 点处没有 rebar 带区时带内从零开始索引。  
  
##  <a name="idtoindex"></a>CReBarCtrl::IDToIndex  
 实现的行为的 Win32 消息[RB_IDTOINDEX](http://msdn.microsoft.com/library/windows/desktop/bb774496)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
int IDToIndex(UINT uBandID) const;  
```  
  
### <a name="parameters"></a>参数  
 *uBandID*  
 指定带区的应用程序定义的标识符传递**wID**的成员[REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393)带区插入时的结构。  
  
### <a name="return-value"></a>返回值  
 如果成功，相应的索引从零开始的带外或否则为-1。 如果存在重复带索引，则返回第一个。  
  
##  <a name="insertband"></a>Crebarctrl:: Insertband  
 实现的行为的 Win32 消息[RB_INSERTBAND](http://msdn.microsoft.com/library/windows/desktop/bb774498)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
BOOL InsertBand(
    UINT uIndex,  
    REBARBANDINFO* prbbi);
```  
  
### <a name="parameters"></a>参数  
 *uIndex*  
 插入带区的位置的位置的从零开始索引。 如果将此参数设置为-1，该控件将在最后一个位置添加新的带区。  
  
 `prbbi`  
 一个指向[REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393)结构，它定义要插入的带区。 必须设置`cbSize`到此结构的成员`sizeof(REBARBANDINFO)`之前调用此函数。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl #&9;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_7.cpp)]  
  
##  <a name="maximizeband"></a>CReBarCtrl::MaximizeBand  
 调整到最大尺寸 rebar 控件中的带。  
  
```  
void MaximizeBand(UINT uBand);
```  
  
### <a name="parameters"></a>参数  
 `uBand`  
 要最大化的带区的从零开始索引。  
  
### <a name="remarks"></a>备注  
 实现的行为的 Win32 消息[RB_MAXIMIZEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774500)与`fIdeal`中所述设置为 0， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl #&10;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_8.cpp)]  
  
##  <a name="minimizeband"></a>CReBarCtrl::MinimizeBand  
 大小调整回其最小大小的 rebar 控件中的带。  
  
```  
void MinimizeBand(UINT uBand);
```  
  
### <a name="parameters"></a>参数  
 `uBand`  
 要最小化的带区的从零开始索引。  
  
### <a name="remarks"></a>备注  
 实现的行为的 Win32 消息[RB_MINIMIZEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774502)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl #&11;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_9.cpp)]  
  
##  <a name="moveband"></a>CReBarCtrl::MoveBand  
 实现的行为的 Win32 消息[RB_MOVEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774504)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
BOOL MoveBand(
    UINT uFrom,  
    UINT uTo);
```  
  
### <a name="parameters"></a>参数  
 *uFrom*  
 要移动的带区的从零开始索引。  
  
 *uTo*  
 新的带位置的从零开始索引。 此参数值永远不能超过减一的带区的数目。 若要获取带区的数目，请调用[GetBandCount](#getbandcount)。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
##  <a name="pushchevron"></a>CReBarCtrl::PushChevron  
 实现的行为的 Win32 消息[RB_PUSHCHEVRON](http://msdn.microsoft.com/library/windows/desktop/bb774506)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
void PushChevron(
    UINT uBand,  
    LPARAM lAppValue);
```  
  
### <a name="parameters"></a>参数  
 `uBand`  
 带区的 v 形图标是可以被推送到的从零开始索引。  
  
 `lAppValue`  
 应用程序定义的 32 位值。 请参阅`lAppValue`中[RB_PUSHCHEVRON](http://msdn.microsoft.com/library/windows/desktop/bb774506)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="restoreband"></a>CReBarCtrl::RestoreBand  
 大小调整回其理想大小 rebar 控件中的带。  
  
```  
void RestoreBand(UINT uBand);
```  
  
### <a name="parameters"></a>参数  
 `uBand`  
 要最大化的带区的从零开始索引。  
  
### <a name="remarks"></a>备注  
 实现的行为的 Win32 消息[RB_MAXIMIZEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774500)与`fIdeal`中所述设置为 1， [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl #&12;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_10.cpp)]  
  
##  <a name="setbandinfo"></a>CReBarCtrl::SetBandInfo  
 实现的行为的 Win32 消息[RB_SETBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774508)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
BOOL SetBandInfo(
    UINT uBand,  
    REBARBANDINFO* prbbi);
```  
  
### <a name="parameters"></a>参数  
 `uBand`  
 若要接收新设置的带区的从零开始索引。  
  
 `prbbi`  
 指向[REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393)结构，它定义要插入的带区。 必须设置`cbSize`到此结构的成员`sizeof(REBARBANDINFO)`发送此消息之前。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl #&13;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_11.cpp)]  
  
##  <a name="setbandwidth"></a>CReBarCtrl::SetBandWidth  
 对于当前的 rebar 控件中设置指定的停靠带区的宽度。  
  
```  
BOOL SetBandWidth(
    UINT uBand,   
    int cxWidth);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `uBand`|Rebar 带区的从零开始索引。|  
|[in] `cxWidth`|新的 rebar 带区，以像素为单位的宽度。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[RB_SETBANDWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb774511)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_rebar`，也就是说，用来访问当前的 rebar 控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CReBarCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_12.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例设置每个 rebar 带区是相同的宽度。  
  
 [!code-cpp[NVC_MFC_CReBarCtrl_s&#1;&2;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_13.cpp)]  
  
##  <a name="setbarinfo"></a>CReBarCtrl::SetBarInfo  
 实现的行为的 Win32 消息[RB_SETBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774513)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
BOOL SetBarInfo(REBARINFO* prbi);
```  
  
### <a name="parameters"></a>参数  
 `prbi`  
 一个指向[REBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774395)结构，其中包含要设置的信息。 必须设置`cbSize`到此结构的成员`sizeof(REBARINFO)`发送此消息之前  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl #&14;](../../mfc/reference/codesnippet/cpp/crebarctrl-class_14.cpp)]  
  
##  <a name="setbkcolor"></a>CReBarCtrl::SetBkColor  
 实现的行为的 Win32 消息[RB_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774515)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
COLORREF SetBkColor(COLORREF clr);
```  
  
### <a name="parameters"></a>参数  
 `clr`  
 **COLORREF**值，该值表示新的默认背景色。  
  
### <a name="return-value"></a>返回值  
 一个[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，该值表示以前的默认背景色。  
  
### <a name="remarks"></a>备注  
 请参阅此主题有关何时可以设置背景色，以及如何将默认设置的详细信息。  
  
##  <a name="setcolorscheme"></a>CReBarCtrl::SetColorScheme  
 在 rebar 控件上设置按钮的配色方案。  
  
```  
void SetColorScheme(const COLORSCHEME* lpcs);
```  
  
### <a name="parameters"></a>参数  
 `lpcs`  
 一个指向[要添加的配色](http://msdn.microsoft.com/library/windows/desktop/bb775502)结构，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>备注  
 **要添加的配色**结构包括按钮突出显示颜色和按钮阴影颜色。  
  
##  <a name="setextendedstyle"></a>CReBarCtrl::SetExtendedStyle  
 设置当前的 rebar 控件的扩展的样式。  
  
```  
DWORD SetExtendedStyle(
    DWORD dwMask,   
    DWORD dwStyleEx);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `dwMask`|标志，用于指定在哪些标志的按位组合 (OR)`dwStyleEx`参数应用。 使用一个或多个下列值︰<br /><br /> RBS_EX_SPLITTER︰ 默认情况下，拆分器在显示底部采用水平模式，并向右在纵向模式下。<br /><br /> RBS_EX_TRANSPARENT︰ 转发[WM_ERASEBKGND](http://msdn.microsoft.com/library/windows/desktop/ms648055)消息发送到父窗口。|  
|[in] `dwStyleEx`|指定要应用的样式的标志的按位组合 (OR)。 若要设置样式，请指定中使用同一个标志`dwMask`参数。 若要重置一种样式，请指定二进制零。|  
  
### <a name="return-value"></a>返回值  
 以前的扩展的样式。  
  
### <a name="remarks"></a>备注  
 此方法可发送[RB_SETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb774519)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setimagelist"></a>CReBarCtrl::SetImageList  
 将图像列表分配到 rebar 控件。  
  
```  
BOOL SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>参数  
 `pImageList`  
 一个指向[CImageList](../../mfc/reference/cimagelist-class.md)对象，其中包含要分配到 rebar 控件的图像列表。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
##  <a name="setowner"></a>CReBarCtrl::SetOwner  
 实现的行为的 Win32 消息[RB_SETPARENT](http://msdn.microsoft.com/library/windows/desktop/bb774522)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
CWnd* SetOwner(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 一个指向`CWnd`对象设置为 rebar 控件的所有者。  
  
### <a name="return-value"></a>返回值  
 一个指向[CWnd](../../mfc/reference/cwnd-class.md) rebar 控件的当前所有者的对象。  
  
### <a name="remarks"></a>备注  
 请注意，此成员函数使用指向指针`CWnd`rebar 控件的当前和所选所有者对象而不是针对 windows 句柄。  
  
> [!NOTE]
>  此成员函数不会更改实际创建控件; 时设置的父级而是会向您指定的窗口发送通知消息。  
  
##  <a name="setpalette"></a>CReBarCtrl::SetPalette  
 实现的行为的 Win32 消息[RB_SETPALETTE](http://msdn.microsoft.com/library/windows/desktop/bb774520)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
CPalette* SetPalette(HPALETTE hPal);
```  
  
### <a name="parameters"></a>参数  
 *hPal*  
 `HPALETTE` ，它指定新的 rebar 控件将使用的调色板。  
  
### <a name="return-value"></a>返回值  
 一个指向[CPalette](../../mfc/reference/cpalette-class.md)对象，它指定 rebar 控件的以前的调色板。  
  
### <a name="remarks"></a>备注  
 请注意，此成员函数使用`CPalette`对象作为其返回值，而不是以`HPALETTE`。  
  
##  <a name="settextcolor"></a>CReBarCtrl::SetTextColor  
 实现的行为的 Win32 消息[RB_SETTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774524)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
COLORREF SetTextColor(COLORREF clr);
```  
  
### <a name="parameters"></a>参数  
 `clr`  
 一个**COLORREF**中的值，该值表示新的文本颜色`CReBarCtrl`对象。  
  
### <a name="return-value"></a>返回值  
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)与关联的值，该值表示前一种文本颜色`CReBarCtrl`对象。  
  
### <a name="remarks"></a>备注  
 它提供以支持在 rebar 控件中的文本颜色的灵活性。  
  
##  <a name="settooltips"></a>CReBarCtrl::SetToolTips  
 将工具提示控件与 rebar 控件相关联。  
  
```  
void SetToolTips(CToolTipCtrl* pToolTip);
```  
  
### <a name="parameters"></a>参数  
 *pToolTip*  
 一个指向[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)对象  
  
### <a name="remarks"></a>备注  
 您必须销毁`CToolTipCtrl`对象完成此操作使用它。  
  
##  <a name="setwindowtheme"></a>CReBarCtrl::SetWindowTheme  
 设置 rebar 控件的视觉样式。  
  
```  
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```  
  
### <a name="parameters"></a>参数  
 `pszSubAppName`  
 指向包含要设置的 rebar 视觉样式的 Unicode 字符串的指针。  
  
### <a name="return-value"></a>返回值  
 不使用返回的值。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[RB_SETWINDOWTHEME](http://msdn.microsoft.com/library/windows/desktop/bb774530)消息，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="showband"></a>CReBarCtrl::ShowBand  
 实现的行为的 Win32 消息[RB_SHOWBAND](http://msdn.microsoft.com/library/windows/desktop/bb774532)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
BOOL ShowBand(
    UINT uBand,  
    BOOL fShow = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `uBand`  
 在 rebar 控件带区的从零开始索引。  
  
 *fShow*  
 指示是否应显示还是隐藏带区。 如果此值为**TRUE**，将显示带区。 否则，将隐藏带区。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
##  <a name="sizetorect"></a>CReBarCtrl::SizeToRect  
 实现的行为的 Win32 消息[RB_SIZETORECT](http://msdn.microsoft.com/library/windows/desktop/bb774534)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
BOOL SizeToRect(CRect& rect);
```  
  
### <a name="parameters"></a>参数  
 `rect`  
 对引用[CRect](../../atl-mfc-shared/reference/crect-class.md)指定 rebar 控件的大小应调整到的矩形的对象。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 请注意，此成员函数使用`CRect`对象作为参数，而不是`RECT`结构。  
  
## <a name="see-also"></a>另请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)



