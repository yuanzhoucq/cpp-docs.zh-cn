---
title: "CReBarCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
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
- CReBarCtrl [MFC], CReBarCtrl
- CReBarCtrl [MFC], BeginDrag
- CReBarCtrl [MFC], Create
- CReBarCtrl [MFC], CreateEx
- CReBarCtrl [MFC], DeleteBand
- CReBarCtrl [MFC], DragMove
- CReBarCtrl [MFC], EndDrag
- CReBarCtrl [MFC], GetBandBorders
- CReBarCtrl [MFC], GetBandCount
- CReBarCtrl [MFC], GetBandInfo
- CReBarCtrl [MFC], GetBandMargins
- CReBarCtrl [MFC], GetBarHeight
- CReBarCtrl [MFC], GetBarInfo
- CReBarCtrl [MFC], GetBkColor
- CReBarCtrl [MFC], GetColorScheme
- CReBarCtrl [MFC], GetDropTarget
- CReBarCtrl [MFC], GetExtendedStyle
- CReBarCtrl [MFC], GetImageList
- CReBarCtrl [MFC], GetPalette
- CReBarCtrl [MFC], GetRect
- CReBarCtrl [MFC], GetRowCount
- CReBarCtrl [MFC], GetRowHeight
- CReBarCtrl [MFC], GetTextColor
- CReBarCtrl [MFC], GetToolTips
- CReBarCtrl [MFC], HitTest
- CReBarCtrl [MFC], IDToIndex
- CReBarCtrl [MFC], InsertBand
- CReBarCtrl [MFC], MaximizeBand
- CReBarCtrl [MFC], MinimizeBand
- CReBarCtrl [MFC], MoveBand
- CReBarCtrl [MFC], PushChevron
- CReBarCtrl [MFC], RestoreBand
- CReBarCtrl [MFC], SetBandInfo
- CReBarCtrl [MFC], SetBandWidth
- CReBarCtrl [MFC], SetBarInfo
- CReBarCtrl [MFC], SetBkColor
- CReBarCtrl [MFC], SetColorScheme
- CReBarCtrl [MFC], SetExtendedStyle
- CReBarCtrl [MFC], SetImageList
- CReBarCtrl [MFC], SetOwner
- CReBarCtrl [MFC], SetPalette
- CReBarCtrl [MFC], SetTextColor
- CReBarCtrl [MFC], SetToolTips
- CReBarCtrl [MFC], SetWindowTheme
- CReBarCtrl [MFC], ShowBand
- CReBarCtrl [MFC], SizeToRect
ms.assetid: 154570d7-e48c-425d-8c7e-c64542bcb4cc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 592493a9eb554f0bdeecd291fdbe3ceb54c599c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
|[CReBarCtrl::BeginDrag](#begindrag)|Rebar 控件置于拖放模式。|  
|[CReBarCtrl::Create](#create)|创建 rebar 控件并将其附加到`CReBarCtrl`对象。|  
|[CReBarCtrl::CreateEx](#createex)|与指定的 Windows 扩展样式创建 rebar 控件并将其附加到`CReBarCtrl`对象。|  
|[CReBarCtrl::DeleteBand](#deleteband)|从 rebar 控件中删除带区。|  
|[CReBarCtrl::DragMove](#dragmove)|在调用后更新 rebar 控件中的拖动位置`BeginDrag`。|  
|[CReBarCtrl::EndDrag](#enddrag)|终止 rebar 控件的拖放操作。|  
|[CReBarCtrl::GetBandBorders](#getbandborders)|检索的带区的边框。|  
|[CReBarCtrl::GetBandCount](#getbandcount)|检索当前中 rebar 控件带区计数。|  
|[CReBarCtrl::GetBandInfo](#getbandinfo)|检索有关指定带区 rebar 控件中的信息。|  
|[CReBarCtrl::GetBandMargins](#getbandmargins)|检索一个带的边距。|  
|[CReBarCtrl::GetBarHeight](#getbarheight)|检索 rebar 控件的高度。|  
|[CReBarCtrl::GetBarInfo](#getbarinfo)|检索有关 rebar 控件和它所使用的图像列表的信息。|  
|[CReBarCtrl::GetBkColor](#getbkcolor)|检索 rebar 控件的默认背景色。|  
|[CReBarCtrl::GetColorScheme](#getcolorscheme)|检索[要添加的配色](http://msdn.microsoft.com/library/windows/desktop/bb775502)与 rebar 控件关联的结构。|  
|[CReBarCtrl::GetDropTarget](#getdroptarget)|检索 rebar 控件的`IDropTarget`接口指针。|  
|[CReBarCtrl::GetExtendedStyle](#getextendedstyle)|获取当前的 rebar 控件的扩展的样式。|  
|[CReBarCtrl::GetImageList](#getimagelist)|检索与 rebar 控件关联的图像列表。|  
|[CReBarCtrl::GetPalette](#getpalette)|检索 rebar 控件的当前调色板。|  
|[CReBarCtrl::GetRect](#getrect)|检索给定的分隔条的 rebar 控件的边框。|  
|[CReBarCtrl::GetRowCount](#getrowcount)|检索 rebar 控件中的带行的数。|  
|[CReBarCtrl::GetRowHeight](#getrowheight)|检索 rebar 控件中指定行的高度。|  
|[CReBarCtrl::GetTextColor](#gettextcolor)|检索 rebar 控件的默认文本颜色。|  
|[CReBarCtrl::GetToolTips](#gettooltips)|检索到任何与 rebar 控件关联的工具提示控件的句柄。|  
|[CReBarCtrl::HitTest](#hittest)|确定 rebar 带区的哪一部分位于给定点在屏幕上，如果 rebar 带区在该点存在。|  
|[CReBarCtrl::IDToIndex](#idtoindex)|将带标识符 (ID) 转换为 rebar 控件中的带索引。|  
|[CReBarCtrl::InsertBand](#insertband)|在 rebar 控件中插入新的带区。|  
|[CReBarCtrl::MaximizeBand](#maximizeband)|调整到最大尺寸 rebar 控件中的带。|  
|[CReBarCtrl::MinimizeBand](#minimizeband)|调整到其最小大小 rebar 控件中的带。|  
|[CReBarCtrl::MoveBand](#moveband)|将带区从一个索引移动到另一个。|  
|[CReBarCtrl::PushChevron](#pushchevron)|以编程方式将推送 v 形图标。|  
|[CReBarCtrl::RestoreBand](#restoreband)|调整到其理想大小 rebar 控件中的带。|  
|[CReBarCtrl::SetBandInfo](#setbandinfo)|Rebar 控件中设置的现有带的特征。|  
|[CReBarCtrl::SetBandWidth](#setbandwidth)|设置当前的 rebar 控件中的指定停靠带区的宽度。|  
|[CReBarCtrl::SetBarInfo](#setbarinfo)|设置 rebar 控件的特征。|  
|[CReBarCtrl::SetBkColor](#setbkcolor)|设置 rebar 控件的默认背景色。|  
|[CReBarCtrl::SetColorScheme](#setcolorscheme)|Rebar 控件上设置按钮的配色方案。|  
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
 在其中 rebar 控件所在的应用程序将分配到 rebar 带区的 rebar 控件中包含的子窗口。 子窗口是通常另一个常见的控件。  
  
 Rebar 控件包含一个或多个带区。 每个带区可以包含一个手柄栏、 位图、 文本标签和子窗口的组合。 带只能包含一个的每个这些项。  
  
 Rebar 控件可以在指定的背景位图上显示的子窗口。 可调整所有 rebar 控件带区除了使用的那些**RBBS_FIXEDSIZE**样式。 当重新定位或调整大小 rebar 控件带区时，rebar 控件将管理的大小和位置分配到该带区的子窗口。 若要调整大小或更改控件中的带区的顺序，单击并拖动带区的手柄栏。  
  
 下图显示一个具有三个带区的 rebar 控件：  
  
-   带区 0 包含平坦且透明工具栏控件。  
  
-   带 1 包含这两个透明标准和透明下拉列表中的按钮。  
  
-   带区 2 包含一个组合框和四个标准按钮。  
  
     ![Rebar 菜单示例](../../mfc/reference/media/vc4scc1.gif "vc4scc1")  
  
## <a name="rebar-control"></a>Rebar 控件  
 Rebar 控件支持：  
  
-   图像列表。  
  
-   消息处理。  
  
-   自定义绘制功能。  
  
-   各种控件样式，除了标准的窗口样式。 有关这些样式的列表，请参阅[Rebar 控件样式](http://msdn.microsoft.com/library/windows/desktop/bb774377)Windows SDK 中。  
  
 有关详细信息，请参阅[使用 CReBarCtrl](../../mfc/using-crebarctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CReBarCtrl`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxcmn.h  
  
##  <a name="begindrag"></a>CReBarCtrl::BeginDrag  
 实现的 Win32 消息行为[RB_BEGINDRAG](http://msdn.microsoft.com/library/windows/desktop/bb774429)，如 Windows SDK 中所述。  
  
```  
void BeginDrag(
    UINT uBand,  
    DWORD dwPos = (DWORD)-1);
```  
  
### <a name="parameters"></a>参数  
 `uBand`  
 拖放操作将影响的带区的从零开始索引。  
  
 `dwPos`  
 A`DWORD`值，该值包含起始鼠标坐标。 水平坐标包含在 LOWORD 并且 HIWORD 中包含的垂直坐标。 如果你通过`(DWORD)-1`，rebar 控件将使用上一次调用的控件的线程的鼠标位置**GetMessage**或**PeekMessage**。  
  
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
 指定应用于控件的 rebar 控件样式的组合。 请参阅[Rebar 控件样式](http://msdn.microsoft.com/library/windows/desktop/bb774377)Windows SDK for 支持样式的列表中。  
  
 `rect`  
 对引用[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，即的位置和大小的 rebar 控件。  
  
 `pParentWnd`  
 指向的指针[CWnd](../../mfc/reference/cwnd-class.md)是 rebar 控件的父窗口的对象。 它不能**NULL**。  
  
 `nID`  
 指定 rebar 控件的控件 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则创建对象时则不为否则为 0。  
  
### <a name="remarks"></a>备注  
 在两个步骤中创建 rebar 控件：  
  
1.  调用[CReBarCtrl](#crebarctrl)构造`CReBarCtrl`对象。  
  
2.  调用此成员函数，它创建 Windows rebar 控件并将其附加到`CReBarCtrl`对象。  
  
 当调用**创建**，常见的控件进行初始化。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl#3](../../mfc/reference/codesnippet/cpp/crebarctrl-class_1.cpp)]  
  
##  <a name="createex"></a>CReBarCtrl::CreateEx  
 创建控件 （子窗口），并将其与关联`CReBarCtrl`对象。  
  
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
 指定要创建的控件的扩展的样式。 扩展窗口样式的列表，请参阅`dwExStyle`参数[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) Windows SDK 中。  
  
 `dwStyle`  
 指定应用于控件的 rebar 控件样式的组合。 有关受支持的样式的列表，请参阅[Rebar 控件样式](http://msdn.microsoft.com/library/windows/desktop/bb774377)Windows SDK 中。  
  
 `rect`  
 对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构描述的大小和窗口在客户端坐标中创建的位置`pParentWnd`。  
  
 `pParentWnd`  
 指向控件的父级的窗口的指针。  
  
 `nID`  
 控件的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 使用`CreateEx`而不是[创建](#create)将扩展的窗口样式，指定的 Windows 扩展的样式加**WS_EX_**。  
  
##  <a name="crebarctrl"></a>CReBarCtrl::CReBarCtrl  
 创建一个 `CReBarCtrl` 对象。  
  
```  
CReBarCtrl();
```  
  
### <a name="example"></a>示例  
  请参阅示例[CReBarCtrl::Create](#create)。  
  
##  <a name="deleteband"></a>CReBarCtrl::DeleteBand  
 实现的 Win32 消息行为[RB_DELETEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774431)，如 Windows SDK 中所述。  
  
```  
BOOL DeleteBand(UINT uBand);
```  
  
### <a name="parameters"></a>参数  
 `uBand`  
 要删除的带区的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 非零，如果成功，则删除带区否则为零。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl#4](../../mfc/reference/codesnippet/cpp/crebarctrl-class_2.cpp)]  
  
##  <a name="dragmove"></a>CReBarCtrl::DragMove  
 实现的 Win32 消息行为[RB_DRAGMOVE](https://msdn.microsoft.com/library/bb774433.aspx)，如 Windows SDK 中所述。  
  
```  
void DragMove(DWORD dwPos = (DWORD)-1);
```  
  
### <a name="parameters"></a>参数  
 `dwPos`  
 A`DWORD`值，该值包含新的鼠标坐标。 水平坐标包含在 LOWORD 并且 HIWORD 中包含的垂直坐标。 如果你通过`(DWORD)-1`，rebar 控件将使用上一次调用的控件的线程的鼠标位置**GetMessage**或**PeekMessage**。  
  
##  <a name="enddrag"></a>CReBarCtrl::EndDrag  
 实现的 Win32 消息行为[RB_ENDDRAG](http://msdn.microsoft.com/library/windows/desktop/bb774435)，如 Windows SDK 中所述。  
  
```  
void EndDrag();
```  
  
##  <a name="getbandborders"></a>CReBarCtrl::GetBandBorders  
 实现的 Win32 消息行为[RB_GETBANDBORDERS](http://msdn.microsoft.com/library/windows/desktop/bb774437)，如 Windows SDK 中所述。  
  
```  
void GetBandBorders(
    UINT uBand,  
    LPRECT prc) const;  
```  
  
### <a name="parameters"></a>参数  
 `uBand`  
 将为其检索边框的带区的从零开始索引。  
  
 `prc`  
 指向的指针[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)将收到带边框的结构。 如果 rebar 控件具有**RBS_BANDBORDERS**样式，此结构的每个成员将接收的像素数，在相应的一端带，构成边框。 如果 rebar 控件不具有**RBS_BANDBORDERS**样式，仅此结构的左的成员接收有效信息。 Rebar 控件样式的说明，请参阅[Rebar 控件样式](http://msdn.microsoft.com/library/windows/desktop/bb774377)Windows SDK 中。  
  
##  <a name="getbandcount"></a>CReBarCtrl::GetBandCount  
 实现的 Win32 消息行为[RB_GETBANDCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb774439)，如 Windows SDK 中所述。  
  
```  
UINT GetBandCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 分配给控件的带区的数目。  
  
##  <a name="getbandinfo"></a>CReBarCtrl::GetBandInfo  
 实现的 Win32 消息行为[RB_GETBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774451) Windows SDK 中所述。  
  
```  
BOOL GetBandInfo(
    UINT uBand,  
    REBARBANDINFO* prbbi) const;  
```  
  
### <a name="parameters"></a>参数  
 `uBand`  
 将为其检索信息的带区的从零开始索引。  
  
 `prbbi`  
 指向的指针[REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393)接收带信息的结构。 必须设置`cbSize`到此结构的成员`sizeof(REBARBANDINFO)`并设置**fMask**到你想要在发送此消息之前检索的项的成员。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
##  <a name="getbandmargins"></a>CReBarCtrl::GetBandMargins  
 检索的带区的边距。  
  
```  
void GetBandMargins(PMARGINS pMargins);
```  
  
### <a name="parameters"></a>参数  
 *pMargins*  
 指向的指针[边距](http://msdn.microsoft.com/library/windows/desktop/bb773244)将接收信息的结构。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[RB_GETBANDMARGINS](http://msdn.microsoft.com/library/windows/desktop/bb774453)消息时，Windows SDK 中所述。  
  
##  <a name="getbarheight"></a>CReBarCtrl::GetBarHeight  
 检索 rebar 条的高度。  
  
```  
UINT GetBarHeight() const;  
```  
  
### <a name="return-value"></a>返回值  
 表示的高度，以像素为单位，该控件的值。  
  
##  <a name="getbarinfo"></a>CReBarCtrl::GetBarInfo  
 实现的 Win32 消息行为[RB_GETBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774457)，如 Windows SDK 中所述。  
  
```  
BOOL GetBarInfo(REBARINFO* prbi) const;  
```  
  
### <a name="parameters"></a>参数  
 `prbi`  
 指向的指针[REBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774395)将收到的 rebar 控制信息的结构。 必须设置`cbSize`到此结构的成员`sizeof(REBARINFO)`之前发送此消息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
##  <a name="getbkcolor"></a>CReBarCtrl::GetBkColor  
 实现的 Win32 消息行为[RB_GETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774459)，如 Windows SDK 中所述。  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 A **COLORREF**值，该值表示当前的默认背景色。  
  
##  <a name="getcolorscheme"></a>CReBarCtrl::GetColorScheme  
 检索[要添加的配色](http://msdn.microsoft.com/library/windows/desktop/bb775502)rebar 控件的结构。  
  
```  
BOOL GetColorScheme(COLORSCHEME* lpcs);
```  
  
### <a name="parameters"></a>参数  
 `lpcs`  
 指向的指针[要添加的配色](http://msdn.microsoft.com/library/windows/desktop/bb775502)结构，如 Windows SDK 中所述。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="remarks"></a>备注  
 **要添加的配色**结构包括按钮突出显示颜色和按钮阴影颜色。  
  
##  <a name="getdroptarget"></a>CReBarCtrl::GetDropTarget  
 实现的 Win32 消息行为[RB_GETDROPTARGET](http://msdn.microsoft.com/library/windows/desktop/bb774463)，如 Windows SDK 中所述。  
  
```  
IDropTarget* GetDropTarget() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向的指针[IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)接口。  
  
##  <a name="getextendedstyle"></a>CReBarCtrl::GetExtendedStyle  
 获取当前的 rebar 控件的扩展的样式。  
  
```  
DWORD GetExtendedStyle() const;  
```  
  
### <a name="return-value"></a>返回值  
 指示扩展的样式标志的按位组合 (OR)。 可能的标志是`RBS_EX_SPLITTER`和`RBS_EX_TRANSPARENT`。 有关详细信息，请参阅`dwMask`参数[CReBarCtrl::SetExtendedStyle](#setextendedstyle)方法。  
  
### <a name="remarks"></a>备注  
 此方法可发送[RB_GETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb774433)消息，Windows SDK 中介绍。  
  
##  <a name="getimagelist"></a>CReBarCtrl::GetImageList  
 获取`CImageList`与 rebar 控件关联的对象。  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向的指针[CImageList](../../mfc/reference/cimagelist-class.md)对象。 返回**NULL**如果任何图像列表不设置为该控件。  
  
### <a name="remarks"></a>备注  
 此成员函数使用存储在中的大小和掩码信息[REBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774395)结构，如 Windows SDK 中所述。  
  
##  <a name="getpalette"></a>CReBarCtrl::GetPalette  
 检索 rebar 控件的当前调色板。  
  
```  
CPalette* GetPalette() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向的指针[CPalette](../../mfc/reference/cpalette-class.md)对象，它指定 rebar 控件的当前调色板。  
  
### <a name="remarks"></a>备注  
 请注意，此成员函数使用`CPalette`对象作为其返回值，而非`HPALETTE`。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl#5](../../mfc/reference/codesnippet/cpp/crebarctrl-class_3.cpp)]  
  
##  <a name="getrect"></a>CReBarCtrl::GetRect  
 实现的 Win32 消息行为[RB_GETRECT](http://msdn.microsoft.com/library/windows/desktop/bb774469)，如 Windows SDK 中所述。  
  
```  
BOOL GetRect(
    UINT uBand,  
    LPRECT prc) const;  
```  
  
### <a name="parameters"></a>参数  
 `uBand`  
 在 rebar 控件带区的从零开始索引。  
  
 `prc`  
 指向的指针[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，它将接收 rebar 带区的边界。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl#6](../../mfc/reference/codesnippet/cpp/crebarctrl-class_4.cpp)]  
  
##  <a name="getrowcount"></a>CReBarCtrl::GetRowCount  
 实现的 Win32 消息行为[RB_GETROWCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb774471)，如 Windows SDK 中所述。  
  
```  
UINT GetRowCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 A **UINT**值，该值表示在控件中的带行数。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl#7](../../mfc/reference/codesnippet/cpp/crebarctrl-class_5.cpp)]  
  
##  <a name="getrowheight"></a>CReBarCtrl::GetRowHeight  
 实现的 Win32 消息行为[RB_GETROWHEIGHT](http://msdn.microsoft.com/library/windows/desktop/bb774473)，如 Windows SDK 中所述。  
  
```  
UINT GetRowHeight(UINT uRow) const;  
```  
  
### <a name="parameters"></a>参数  
 *uRow*  
 将具有检索其高度的带区的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 A **UINT**表示行高度，以像素为单位的值。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl#8](../../mfc/reference/codesnippet/cpp/crebarctrl-class_6.cpp)]  
  
##  <a name="gettextcolor"></a>CReBarCtrl::GetTextColor  
 实现的 Win32 消息行为[RB_GETTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774475)，如 Windows SDK 中所述。  
  
```  
COLORREF GetTextColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 A **COLORREF**值，该值表示当前的默认文本颜色。  
  
##  <a name="gettooltips"></a>CReBarCtrl::GetToolTips  
 实现的 Win32 消息行为[RB_GETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb774477)，如 Windows SDK 中所述。  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向的指针[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)对象。  
  
### <a name="remarks"></a>备注  
 请注意的 MFC 实现`GetToolTips`返回一个指向`CToolTipCtrl`，而非`HWND`。  
  
##  <a name="hittest"></a>CReBarCtrl::HitTest  
 实现的 Win32 消息行为[RB_HITTEST](http://msdn.microsoft.com/library/windows/desktop/bb774494)，如 Windows SDK 中所述。  
  
```  
int HitTest(RBHITTESTINFO* prbht);
```  
  
### <a name="parameters"></a>参数  
 *prbht*  
 指向的指针[RBHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb774391)结构。 发送消息前, **pt**此结构的成员必须初始化为将测试，在工作区坐标的点。  
  
### <a name="return-value"></a>返回值  
 在给定的时间，则为-1 如果没有 rebar 带区点位于带从零开始索引。  
  
##  <a name="idtoindex"></a>CReBarCtrl::IDToIndex  
 实现的 Win32 消息行为[RB_IDTOINDEX](http://msdn.microsoft.com/library/windows/desktop/bb774496)，如 Windows SDK 中所述。  
  
```  
int IDToIndex(UINT uBandID) const;  
```  
  
### <a name="parameters"></a>参数  
 *uBandID*  
 指定带区，应用程序定义的标识符传递中**wID**的成员[REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393)结构插入带区时。  
  
### <a name="return-value"></a>返回值  
 如果成功，相应的索引从零开始的带或否则为-1。 如果存在重复的带索引，则返回第一个。  
  
##  <a name="insertband"></a>CReBarCtrl::InsertBand  
 实现的 Win32 消息行为[RB_INSERTBAND](http://msdn.microsoft.com/library/windows/desktop/bb774498)，如 Windows SDK 中所述。  
  
```  
BOOL InsertBand(
    UINT uIndex,  
    REBARBANDINFO* prbbi);
```  
  
### <a name="parameters"></a>参数  
 *uIndex*  
 将插入带区的位置的位置的从零开始索引。 如果此参数设置为-1 时，控件将在最后一个位置添加新的带区。  
  
 `prbbi`  
 指向的指针[REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393)结构，它定义要插入的带区。 必须设置`cbSize`到此结构的成员`sizeof(REBARBANDINFO)`之前调用此函数。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl#9](../../mfc/reference/codesnippet/cpp/crebarctrl-class_7.cpp)]  
  
##  <a name="maximizeband"></a>CReBarCtrl::MaximizeBand  
 调整到最大尺寸 rebar 控件中的带。  
  
```  
void MaximizeBand(UINT uBand);
```  
  
### <a name="parameters"></a>参数  
 `uBand`  
 若要最大化的带区的从零开始索引。  
  
### <a name="remarks"></a>备注  
 实现的 Win32 消息行为[RB_MAXIMIZEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774500)与`fIdeal`设置为 0，Windows SDK 中所述。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl#10](../../mfc/reference/codesnippet/cpp/crebarctrl-class_8.cpp)]  
  
##  <a name="minimizeband"></a>CReBarCtrl::MinimizeBand  
 调整到其最小大小 rebar 控件中的带。  
  
```  
void MinimizeBand(UINT uBand);
```  
  
### <a name="parameters"></a>参数  
 `uBand`  
 若要将最小化的带区的从零开始索引。  
  
### <a name="remarks"></a>备注  
 实现的 Win32 消息行为[RB_MINIMIZEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774502)，如 Windows SDK 中所述。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl#11](../../mfc/reference/codesnippet/cpp/crebarctrl-class_9.cpp)]  
  
##  <a name="moveband"></a>CReBarCtrl::MoveBand  
 实现的 Win32 消息行为[RB_MOVEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774504)，如 Windows SDK 中所述。  
  
```  
BOOL MoveBand(
    UINT uFrom,  
    UINT uTo);
```  
  
### <a name="parameters"></a>参数  
 *uFrom*  
 要移动的带区的从零开始索引。  
  
 *uTo*  
 新的带位置的从零开始索引。 此参数值必须不会大于减一的带区的数目。 若要获取的带区数目，调用[GetBandCount](#getbandcount)。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
##  <a name="pushchevron"></a>CReBarCtrl::PushChevron  
 实现的 Win32 消息行为[RB_PUSHCHEVRON](http://msdn.microsoft.com/library/windows/desktop/bb774506)，如 Windows SDK 中所述。  
  
```  
void PushChevron(
    UINT uBand,  
    LPARAM lAppValue);
```  
  
### <a name="parameters"></a>参数  
 `uBand`  
 其 v 形图标是推送的带区的从零开始索引。  
  
 `lAppValue`  
 应用程序定义的 32 位值。 请参阅`lAppValue`中[RB_PUSHCHEVRON](http://msdn.microsoft.com/library/windows/desktop/bb774506) Windows SDK 中。  
  
##  <a name="restoreband"></a>CReBarCtrl::RestoreBand  
 调整到其理想大小 rebar 控件中的带。  
  
```  
void RestoreBand(UINT uBand);
```  
  
### <a name="parameters"></a>参数  
 `uBand`  
 若要最大化的带区的从零开始索引。  
  
### <a name="remarks"></a>备注  
 实现的 Win32 消息行为[RB_MAXIMIZEBAND](http://msdn.microsoft.com/library/windows/desktop/bb774500)与`fIdeal`设置为 1，Windows SDK 中所述。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl#12](../../mfc/reference/codesnippet/cpp/crebarctrl-class_10.cpp)]  
  
##  <a name="setbandinfo"></a>CReBarCtrl::SetBandInfo  
 实现的 Win32 消息行为[RB_SETBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774508)，如 Windows SDK 中所述。  
  
```  
BOOL SetBandInfo(
    UINT uBand,  
    REBARBANDINFO* prbbi);
```  
  
### <a name="parameters"></a>参数  
 `uBand`  
 若要接收新设置的带区的从零开始索引。  
  
 `prbbi`  
 指向[REBARBANDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774393)结构，它定义要插入的带区。 必须设置`cbSize`到此结构的成员`sizeof(REBARBANDINFO)`之前发送此消息。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl#13](../../mfc/reference/codesnippet/cpp/crebarctrl-class_11.cpp)]  
  
##  <a name="setbandwidth"></a>CReBarCtrl::SetBandWidth  
 设置当前的 rebar 控件中的指定停靠带区的宽度。  
  
```  
BOOL SetBandWidth(
    UINT uBand,   
    int cxWidth);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in] `uBand`|Rebar 带区的从零开始索引。|  
|[in] `cxWidth`|新的 rebar 带区，以像素为单位的宽度。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[RB_SETBANDWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb774511)消息，Windows SDK 中介绍。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_rebar`，即用于访问当前的 rebar 控件。 此变量将在下一个示例中使用。  
  
 [!code-cpp[NVC_MFC_CReBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/crebarctrl-class_12.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例设置每个 rebar 带区是相同的宽度。  
  
 [!code-cpp[NVC_MFC_CReBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/crebarctrl-class_13.cpp)]  
  
##  <a name="setbarinfo"></a>CReBarCtrl::SetBarInfo  
 实现的 Win32 消息行为[RB_SETBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774513)，如 Windows SDK 中所述。  
  
```  
BOOL SetBarInfo(REBARINFO* prbi);
```  
  
### <a name="parameters"></a>参数  
 `prbi`  
 指向的指针[REBARINFO](http://msdn.microsoft.com/library/windows/desktop/bb774395)结构，其中包含要设置的信息。 必须设置`cbSize`到此结构的成员`sizeof(REBARINFO)`发送此消息之前  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFC_CReBarCtrl#14](../../mfc/reference/codesnippet/cpp/crebarctrl-class_14.cpp)]  
  
##  <a name="setbkcolor"></a>CReBarCtrl::SetBkColor  
 实现的 Win32 消息行为[RB_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774515)，如 Windows SDK 中所述。  
  
```  
COLORREF SetBkColor(COLORREF clr);
```  
  
### <a name="parameters"></a>参数  
 `clr`  
 **COLORREF**值，该值表示新的默认背景色。  
  
### <a name="return-value"></a>返回值  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，该值表示的以前的默认背景色。  
  
### <a name="remarks"></a>备注  
 请参阅此主题有关何时设置背景色，以及如何设置默认值的详细信息。  
  
##  <a name="setcolorscheme"></a>CReBarCtrl::SetColorScheme  
 Rebar 控件上设置按钮的配色方案。  
  
```  
void SetColorScheme(const COLORSCHEME* lpcs);
```  
  
### <a name="parameters"></a>参数  
 `lpcs`  
 指向的指针[要添加的配色](http://msdn.microsoft.com/library/windows/desktop/bb775502)结构，如 Windows SDK 中所述。  
  
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
  
|参数|描述|  
|---------------|-----------------|  
|[in] `dwMask`|指定在哪些标志的标志的按位组合 (OR)`dwStyleEx`参数应用。 使用一个或多个以下值：<br /><br /> RBS_EX_SPLITTER： 默认情况下，显示拆分器底部水平模式下，在右侧中和垂直模式。<br /><br /> RBS_EX_TRANSPARENT： 转发[WM_ERASEBKGND](http://msdn.microsoft.com/library/windows/desktop/ms648055)消息发送到父窗口。|  
|[in] `dwStyleEx`|指定要应用的样式的标志的按位组合 (OR)。 若要设置样式，指定同一个中使用的标志`dwMask`参数。 若要重置样式，请指定二进制零。|  
  
### <a name="return-value"></a>返回值  
 以前的扩展的样式。  
  
### <a name="remarks"></a>备注  
 此方法可发送[RB_SETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb774519)消息，Windows SDK 中介绍。  
  
##  <a name="setimagelist"></a>CReBarCtrl::SetImageList  
 将图像列表分配到 rebar 控件。  
  
```  
BOOL SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>参数  
 `pImageList`  
 指向的指针[CImageList](../../mfc/reference/cimagelist-class.md)对象，其中包含要分配到 rebar 控件的图像列表。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为零，否则为零。  
  
##  <a name="setowner"></a>CReBarCtrl::SetOwner  
 实现的 Win32 消息行为[RB_SETPARENT](http://msdn.microsoft.com/library/windows/desktop/bb774522)，如 Windows SDK 中所述。  
  
```  
CWnd* SetOwner(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向的指针`CWnd`对象将设置为 rebar 控件的所有者。  
  
### <a name="return-value"></a>返回值  
 指向的指针[CWnd](../../mfc/reference/cwnd-class.md) rebar 控件的当前所有者的对象。  
  
### <a name="remarks"></a>备注  
 请注意，此成员函数使用指向`CWnd`rebar 控件的当前和所选所有者对象，而不是句柄到 windows。  
  
> [!NOTE]
>  此成员函数不会更改实际创建控件; 时设置的父类而它将通知消息发送到您指定的窗口。  
  
##  <a name="setpalette"></a>CReBarCtrl::SetPalette  
 实现的 Win32 消息行为[RB_SETPALETTE](http://msdn.microsoft.com/library/windows/desktop/bb774520)，如 Windows SDK 中所述。  
  
```  
CPalette* SetPalette(HPALETTE hPal);
```  
  
### <a name="parameters"></a>参数  
 *hPal*  
 `HPALETTE` ，指定新的 rebar 控件将使用的调色板。  
  
### <a name="return-value"></a>返回值  
 指向的指针[CPalette](../../mfc/reference/cpalette-class.md)对象，它指定 rebar 控件的以前的调色板。  
  
### <a name="remarks"></a>备注  
 请注意，此成员函数使用`CPalette`对象作为其返回值，而非`HPALETTE`。  
  
##  <a name="settextcolor"></a>CReBarCtrl::SetTextColor  
 实现的 Win32 消息行为[RB_SETTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774524)，如 Windows SDK 中所述。  
  
```  
COLORREF SetTextColor(COLORREF clr);
```  
  
### <a name="parameters"></a>参数  
 `clr`  
 A **COLORREF**值，该值表示新的文本颜色`CReBarCtrl`对象。  
  
### <a name="return-value"></a>返回值  
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)与关联的值，该值表示以前的文本颜色`CReBarCtrl`对象。  
  
### <a name="remarks"></a>备注  
 它可用于支持 rebar 控件中的文本颜色灵活性。  
  
##  <a name="settooltips"></a>CReBarCtrl::SetToolTips  
 将工具提示控件与 rebar 控件相关联。  
  
```  
void SetToolTips(CToolTipCtrl* pToolTip);
```  
  
### <a name="parameters"></a>参数  
 *pToolTip*  
 指向的指针[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)对象  
  
### <a name="remarks"></a>备注  
 必须销毁`CToolTipCtrl`对象都完成。  
  
##  <a name="setwindowtheme"></a>CReBarCtrl::SetWindowTheme  
 设置 rebar 控件的视觉样式。  
  
```  
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```  
  
### <a name="parameters"></a>参数  
 `pszSubAppName`  
 指向包含要设置的 rebar 视觉样式的 Unicode 字符串的指针。  
  
### <a name="return-value"></a>返回值  
 未使用返回的值。  
  
### <a name="remarks"></a>备注  
 此成员函数模拟的功能[RB_SETWINDOWTHEME](http://msdn.microsoft.com/library/windows/desktop/bb774530)消息时，Windows SDK 中所述。  
  
##  <a name="showband"></a>CReBarCtrl::ShowBand  
 实现的 Win32 消息行为[RB_SHOWBAND](http://msdn.microsoft.com/library/windows/desktop/bb774532)，如 Windows SDK 中所述。  
  
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
 实现的 Win32 消息行为[RB_SIZETORECT](http://msdn.microsoft.com/library/windows/desktop/bb774534)，如 Windows SDK 中所述。  
  
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
  
## <a name="see-also"></a>请参阅  
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)


