---
title: "CSliderCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSliderCtrl
- AFXCMN/CSliderCtrl
- AFXCMN/CSliderCtrl::CSliderCtrl
- AFXCMN/CSliderCtrl::ClearSel
- AFXCMN/CSliderCtrl::ClearTics
- AFXCMN/CSliderCtrl::Create
- AFXCMN/CSliderCtrl::CreateEx
- AFXCMN/CSliderCtrl::GetBuddy
- AFXCMN/CSliderCtrl::GetChannelRect
- AFXCMN/CSliderCtrl::GetLineSize
- AFXCMN/CSliderCtrl::GetNumTics
- AFXCMN/CSliderCtrl::GetPageSize
- AFXCMN/CSliderCtrl::GetPos
- AFXCMN/CSliderCtrl::GetRange
- AFXCMN/CSliderCtrl::GetRangeMax
- AFXCMN/CSliderCtrl::GetRangeMin
- AFXCMN/CSliderCtrl::GetSelection
- AFXCMN/CSliderCtrl::GetThumbLength
- AFXCMN/CSliderCtrl::GetThumbRect
- AFXCMN/CSliderCtrl::GetTic
- AFXCMN/CSliderCtrl::GetTicArray
- AFXCMN/CSliderCtrl::GetTicPos
- AFXCMN/CSliderCtrl::GetToolTips
- AFXCMN/CSliderCtrl::SetBuddy
- AFXCMN/CSliderCtrl::SetLineSize
- AFXCMN/CSliderCtrl::SetPageSize
- AFXCMN/CSliderCtrl::SetPos
- AFXCMN/CSliderCtrl::SetRange
- AFXCMN/CSliderCtrl::SetRangeMax
- AFXCMN/CSliderCtrl::SetRangeMin
- AFXCMN/CSliderCtrl::SetSelection
- AFXCMN/CSliderCtrl::SetThumbLength
- AFXCMN/CSliderCtrl::SetTic
- AFXCMN/CSliderCtrl::SetTicFreq
- AFXCMN/CSliderCtrl::SetTipSide
- AFXCMN/CSliderCtrl::SetToolTips
dev_langs:
- C++
helpviewer_keywords:
- CSliderCtrl [MFC], CSliderCtrl
- CSliderCtrl [MFC], ClearSel
- CSliderCtrl [MFC], ClearTics
- CSliderCtrl [MFC], Create
- CSliderCtrl [MFC], CreateEx
- CSliderCtrl [MFC], GetBuddy
- CSliderCtrl [MFC], GetChannelRect
- CSliderCtrl [MFC], GetLineSize
- CSliderCtrl [MFC], GetNumTics
- CSliderCtrl [MFC], GetPageSize
- CSliderCtrl [MFC], GetPos
- CSliderCtrl [MFC], GetRange
- CSliderCtrl [MFC], GetRangeMax
- CSliderCtrl [MFC], GetRangeMin
- CSliderCtrl [MFC], GetSelection
- CSliderCtrl [MFC], GetThumbLength
- CSliderCtrl [MFC], GetThumbRect
- CSliderCtrl [MFC], GetTic
- CSliderCtrl [MFC], GetTicArray
- CSliderCtrl [MFC], GetTicPos
- CSliderCtrl [MFC], GetToolTips
- CSliderCtrl [MFC], SetBuddy
- CSliderCtrl [MFC], SetLineSize
- CSliderCtrl [MFC], SetPageSize
- CSliderCtrl [MFC], SetPos
- CSliderCtrl [MFC], SetRange
- CSliderCtrl [MFC], SetRangeMax
- CSliderCtrl [MFC], SetRangeMin
- CSliderCtrl [MFC], SetSelection
- CSliderCtrl [MFC], SetThumbLength
- CSliderCtrl [MFC], SetTic
- CSliderCtrl [MFC], SetTicFreq
- CSliderCtrl [MFC], SetTipSide
- CSliderCtrl [MFC], SetToolTips
ms.assetid: dd12b084-4eda-4550-a810-8f3cfb06b871
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2788777b9a5014790e094cf39871b3e4d40750fe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="csliderctrl-class"></a>CSliderCtrl 类
提供 Windows 公共滑块控件的功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CSliderCtrl : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CSliderCtrl::CSliderCtrl](#csliderctrl)|构造 `CSliderCtrl` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CSliderCtrl::ClearSel](#clearsel)|清除滑块控件中的当前的选择。|  
|[CSliderCtrl::ClearTics](#cleartics)|从滑块控件中移除当前的刻度线。|  
|[CSliderCtrl::Create](#create)|创建滑块控件，并将其附加到`CSliderCtrl`对象。|  
|[CSliderCtrl::CreateEx](#createex)|创建指定的 Windows 扩展样式的滑块控件，并将其附加到`CSliderCtrl`对象。|  
|[CSliderCtrl::GetBuddy](#getbuddy)|检索给定位置处的滑块控件合作者窗口的句柄。|  
|[CSliderCtrl::GetChannelRect](#getchannelrect)|检索滑块控件的通道的大小。|  
|[CSliderCtrl::GetLineSize](#getlinesize)|检索滑块控件的行大小。|  
|[CSliderCtrl::GetNumTics](#getnumtics)|检索滑块控件中的刻度的数。|  
|[CSliderCtrl::GetPageSize](#getpagesize)|检索滑块控件的页大小。|  
|[CSliderCtrl::GetPos](#getpos)|检索将滑块的当前位置。|  
|[CSliderCtrl::GetRange](#getrange)|检索滑块的最小和最大位置。|  
|[CSliderCtrl::GetRangeMax](#getrangemax)|检索滑块的最大位置。|  
|[CSliderCtrl::GetRangeMin](#getrangemin)|检索滑块的最小位置。|  
|[CSliderCtrl::GetSelection](#getselection)|检索当前所选内容的范围。|  
|[CSliderCtrl::GetThumbLength](#getthumblength)|检索当前 trackbar 控件中的滑块的长度。|  
|[CSliderCtrl::GetThumbRect](#getthumbrect)|检索滑块控件的滚动块的大小。|  
|[CSliderCtrl::GetTic](#gettic)|检索指定的刻度线的位置。|  
|[CSliderCtrl::GetTicArray](#getticarray)|检索的滑块控件的刻度线位置的数组。|  
|[CSliderCtrl::GetTicPos](#getticpos)|检索指定的刻度线，客户端坐标中的位置。|  
|[CSliderCtrl::GetToolTips](#gettooltips)|如果有的话，请检索分配给滑块控件的工具提示控件的句柄。|  
|[CSliderCtrl::SetBuddy](#setbuddy)|将窗口分配为合作者窗口的滑块控件。|  
|[CSliderCtrl::SetLineSize](#setlinesize)|设置滑块控件的行大小。|  
|[CSliderCtrl::SetPageSize](#setpagesize)|设置滑块控件的页大小。|  
|[CSliderCtrl::SetPos](#setpos)|设置滑块的当前位置。|  
|[CSliderCtrl::SetRange](#setrange)|设置滑块的最小和最大位置。|  
|[CSliderCtrl::SetRangeMax](#setrangemax)|设置滑块的最大位置。|  
|[CSliderCtrl::SetRangeMin](#setrangemin)|设置滑块的最小位置。|  
|[CSliderCtrl::SetSelection](#setselection)|设置当前所选内容的范围。|  
|[CSliderCtrl::SetThumbLength](#setthumblength)|设置当前的 trackbar 控件中的滑块的长度。|  
|[CSliderCtrl::SetTic](#settic)|设置指定的刻度线的位置。|  
|[CSliderCtrl::SetTicFreq](#setticfreq)|设置刻度线的频率，每个滑块控件递增的标记。|  
|[CSliderCtrl::SetTipSide](#settipside)|位置 trackbar 控件工具提示控件使用。|  
|[CSliderCtrl::SetToolTips](#settooltips)|将工具提示控件分配给滑块控件。|  
  
## <a name="remarks"></a>备注  
 "滑块控件"(也称为 trackbar) 是一个窗口，其中包含滑块和可选刻度线。 当用户移滑块，使用鼠标或箭头键时，控件将发送通知消息来指示更改。  
  
 当您希望用户选择一个离散值或位于一个范围中的一组连续值时，滑动控件很有用。 例如，您可能使用滑块控件允许用户通过将滑块移动到给定刻度线来设置重复速率。  
  
 此控件 (因此`CSliderCtrl`类) 仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 下运行的程序和更高版本。  
  
 在创建它时指定的增量移动滑块。 例如，如果您指定滑块应具有五个范围，滑块只能占用 6 个位置： 左侧的滑块控件和每个增量的范围中的一个位置的位置。 通常，这些位置中的每个位置将用一个刻度线标识。  
  
 通过使用构造函数创建滑块和**创建**成员函数`CSliderCtrl`。 在创建滑块控件，你可以使用中的成员函数`CSliderCtrl`更改许多其属性。 可进行的更改包括设置滑块的最小和最大位置、绘制刻度线、设置选择范围以及重新定位滑块。  
  
 有关详细信息使用`CSliderCtrl`，请参阅[控件](../../mfc/controls-mfc.md)和[使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSliderCtrl`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxcmn.h  
  
##  <a name="clearsel"></a>CSliderCtrl::ClearSel  
 清除滑块控件中的当前的选择。  
  
```  
void ClearSel(BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `bRedraw`  
 重绘标志。 如果此参数为**TRUE**，清除所选内容后，重绘滑块; 否则滑块不在重绘。  
  
##  <a name="cleartics"></a>CSliderCtrl::ClearTics  
 从滑块控件中移除当前的刻度线。  
  
```  
void ClearTics(BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `bRedraw`  
 重绘标志。 如果此参数为**TRUE**，刻度线清除后重绘滑块; 否则滑块不在重绘。  
  
##  <a name="create"></a>CSliderCtrl::Create  
 创建滑块控件，并将其附加到`CSliderCtrl`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 指定滑块控件的样式。 应用的任意组合[滑块控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760147)、 Windows SDK，到控件中所述。  
  
 `rect`  
 指定滑块控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构。  
  
 `pParentWnd`  
 通常指定滑块控件的父窗口`CDialog`。 它不能**NULL**。  
  
 `nID`  
 指定滑块控件的 id。  
  
### <a name="return-value"></a>返回值  
 如果初始化成功; 则为非 0否则为 0。  
  
### <a name="remarks"></a>备注  
 构造`CSliderCtrl`中两个步骤。 首先，调用的构造函数，然后调用**创建**，它创建滑块控件，并将其附加到`CSliderCtrl`对象。  
  
 具体取决于设置的值`dwStyle`，滑块控件可以具有垂直或水平方向。 它可以具有刻度线在任意一侧边，还是两者皆否。 此外可以用于指定的连续值范围。  
  
 若要将扩展的窗口样式应用于滑块控件，调用[CreateEx](#createex)而不是**创建**。  
  
##  <a name="createex"></a>CSliderCtrl::CreateEx  
 创建控件 （子窗口），并将其与关联`CSliderCtrl`对象。  
  
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
 指定滑块控件的样式。 应用的任意组合[滑块控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760147)、 Windows SDK，到控件中所述。  
  
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
  
##  <a name="csliderctrl"></a>CSliderCtrl::CSliderCtrl  
 构造 `CSliderCtrl` 对象。  
  
```  
CSliderCtrl();
```  
  
##  <a name="getbuddy"></a>CSliderCtrl::GetBuddy  
 检索给定位置处的滑块控件合作者窗口的句柄。  
  
```  
CWnd* GetBuddy(BOOL fLocation = TRUE) const;  
```  
  
### <a name="parameters"></a>参数  
 `fLocation`  
 一个布尔值，该值指示这两个合作者窗口句柄来检索。 可以是以下值之一：  
  
- **TRUE**检索左侧的滑块合作者窗口的句柄。 如果滑块控件使用`TBS_VERT`样式，该消息将检索滑块上面合作者。  
  
- **FALSE**检索右侧的滑块合作者窗口的句柄。 如果滑块控件使用`TBS_VERT`样式，该消息将检索滑块下方合作者。  
  
### <a name="return-value"></a>返回值  
 指向的指针[CWnd](../../mfc/reference/cwnd-class.md)合作者窗口通过指定的位置处的对象`fLocation`，或**NULL**如果没有合作者窗口存在在指定的位置。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[TBM_GETBUDDY](http://msdn.microsoft.com/library/windows/desktop/bb760178)，如 Windows SDK 中所述。 滑块控件样式的说明，请参阅[Trackbar 控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760147)Windows SDK 中。  
  
##  <a name="getchannelrect"></a>CSliderCtrl::GetChannelRect  
 检索的大小和位置的滑块控件的通道的绑定矩形。  
  
```  
void GetChannelRect(LPRECT lprc) const;  
```  
  
### <a name="parameters"></a>参数  
 `lprc`  
 指向的指针[CRect](../../atl-mfc-shared/reference/crect-class.md)在函数返回时包含的大小和位置的通道的对象的边框。  
  
### <a name="remarks"></a>备注  
 通道是通过将滑块移和选择范围时，其中包含突出显示的区域。  
  
##  <a name="getlinesize"></a>CSliderCtrl::GetLineSize  
 检索滑块控件的行的大小。  
  
```  
int GetLineSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 滑块控件的行的大小。  
  
### <a name="remarks"></a>备注  
 行大小会影响多少滑块移对应**TB_LINEUP**和**TB_LINEDOWN**通知。 行大小的默认设置为 1。  
  
##  <a name="getnumtics"></a>CSliderCtrl::GetNumTics  
 检索滑块控件中的刻度的数。  
  
```  
UINT GetNumTics() const;  
```  
  
### <a name="return-value"></a>返回值  
 滑块控件中的刻度数。  
  
##  <a name="getpagesize"></a>CSliderCtrl::GetPageSize  
 检索滑块控件的页的大小。  
  
```  
int GetPageSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 滑块控件的页面大小。  
  
### <a name="remarks"></a>备注  
 页大小会影响多少滑块移对应**TB_PAGEUP**和**TB_PAGEDOWN**通知。  
  
##  <a name="getpos"></a>CSliderCtrl::GetPos  
 检索将滑块的滑块控件中的当前位置。  
  
```  
int GetPos() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前位置。  
  
##  <a name="getrange"></a>CSliderCtrl::GetRange  
 检索的最大和最小职位滑块控件。  
  
```  
void GetRange(
    int& nMin,  
    int& nMax) const;  
```  
  
### <a name="parameters"></a>参数  
 `nMin`  
 对一个整数，它接收的最小位置引用。  
  
 `nMax`  
 对一个整数，它接收的最大位置引用。  
  
### <a name="remarks"></a>备注  
 此函数将值复制到引用的整数`nMin`和`nMax`。  
  
##  <a name="getrangemax"></a>CSliderCtrl::GetRangeMax  
 检索滑块控件中的滑块的最大位置。  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>返回值  
 控件的最大位置。  
  
##  <a name="getrangemin"></a>CSliderCtrl::GetRangeMin  
 检索滑块控件中的滑块的最小位置。  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>返回值  
 控件的最小位置。  
  
##  <a name="getselection"></a>CSliderCtrl::GetSelection  
 检索在滑块控件中当前所选内容的起始和结束位置。  
  
```  
void GetSelection(
    int& nMin,  
    int& nMax) const;  
```  
  
### <a name="parameters"></a>参数  
 `nMin`  
 对一个整数，它接收当前所选内容的起始位置的引用。  
  
 `nMax`  
 对一个整数，它接收当前所选内容的结束位置的引用。  
  
##  <a name="getthumblength"></a>CSliderCtrl::GetThumbLength  
 检索当前 trackbar 控件中的滑块的长度。  
  
```  
int GetThumbLength() const;  
```  
  
### <a name="return-value"></a>返回值  
 将滑块，以像素为单位的长度。  
  
### <a name="remarks"></a>备注  
 此方法可发送[TBM_GETTHUMBLENGTH](http://msdn.microsoft.com/library/windows/desktop/bb760201)消息，Windows SDK 中介绍。  
  
##  <a name="getthumbrect"></a>CSliderCtrl::GetThumbRect  
 检索的大小和滑块控件中的滑块 （滚动块） 的绑定矩形的位置。  
  
```  
void GetThumbRect(LPRECT lprc) const;  
```  
  
### <a name="parameters"></a>参数  
 `lprc`  
 指向的指针`CRect`对象，它在函数返回时包含滑块的绑定矩形。  
  
##  <a name="gettic"></a>CSliderCtrl::GetTic  
 检索刻度线的滑块控件中的位置。  
  
```  
int GetTic(int nTic) const;  
```  
  
### <a name="parameters"></a>参数  
 `nTic`  
 确定刻度线的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 指定的刻度线或 1 如果的位置`nTic`未指定的有效索引。  
  
##  <a name="getticarray"></a>CSliderCtrl::GetTicArray  
 检索一个数组，包含滑块控件的刻度线的位置的地址。  
  
```  
DWORD* GetTicArray() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个数组，包含滑块控件的刻度线位置的地址。  
  
##  <a name="getticpos"></a>CSliderCtrl::GetTicPos  
 检索刻度线的滑块控件中的当前物理位置。  
  
```  
int GetTicPos(int nTic) const;  
```  
  
### <a name="parameters"></a>参数  
 `nTic`  
 确定刻度线的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 物理位置，在客户端坐标中，指定的刻度线或 1 如果`nTic`未指定的有效索引。  
  
##  <a name="gettooltips"></a>CSliderCtrl::GetToolTips  
 如果有的话，请检索分配给滑块控件的工具提示控件的句柄。  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向的指针[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)对象，或**NULL**如果工具提示未被使用。 如果滑块控件不使用**TBS_TOOLTIPS**样式，则返回值是**NULL**。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[TBM_GETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb760209)，如 Windows SDK 中所述。 请注意，此成员函数返回`CToolTipCtrl`对象而不是控件的句柄。  
  
 滑块控件样式的说明，请参阅[Trackbar 控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760147)Windows SDK 中。  
  
##  <a name="setbuddy"></a>CSliderCtrl::SetBuddy  
 将窗口分配为合作者窗口的滑块控件。  
  
```  
CWnd* SetBuddy(
    CWnd* pWndBuddy,  
    BOOL fLocation = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `pWndBuddy`  
 指向的指针`CWnd`将作为滑块控件合作者设置的对象。  
  
 `fLocation`  
 值，该值指定在显示合作者窗口的位置。 此值可以是以下项之一：  
  
- **TRUE**合作者将跟踪条的左侧出现，如果 trackbar 控件使用`TBS_HORZ`样式。 如果使用 trackbar`TBS_VERT`合作者上方 trackbar 控件的样式。  
  
- **FALSE**合作者将显示跟踪条右侧如果 trackbar 控件使用`TBS_HORZ`样式。 如果使用 trackbar`TBS_VERT`合作者如下所示 trackbar 控件的样式。  
  
### <a name="return-value"></a>返回值  
 指向的指针[CWnd](../../mfc/reference/cwnd-class.md)之前分配给该位置的滑块控件的对象。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[TBM_SETBUDDY](http://msdn.microsoft.com/library/windows/desktop/bb760213)，如 Windows SDK 中所述。 请注意，此成员函数使用指向`CWnd`对象，而不是作为其返回值和参数的窗口句柄。  
  
 滑块控件样式的说明，请参阅[Trackbar 控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760147)Windows SDK 中。  
  
##  <a name="setlinesize"></a>CSliderCtrl::SetLineSize  
 设置滑块控件的行的大小。  
  
```  
int SetLineSize(int nSize);
```  
  
### <a name="parameters"></a>参数  
 `nSize`  
 滑块控件的新行大小。  
  
### <a name="return-value"></a>返回值  
 以前的行大小。  
  
### <a name="remarks"></a>备注  
 行大小会影响多少滑块移对应**TB_LINEUP**和**TB_LINEDOWN**通知。  
  
##  <a name="setpagesize"></a>CSliderCtrl::SetPageSize  
 设置滑块控件的页的大小。  
  
```  
int SetPageSize(int nSize);
```  
  
### <a name="parameters"></a>参数  
 `nSize`  
 滑块控件的新的页大小。  
  
### <a name="return-value"></a>返回值  
 以前的页面大小。  
  
### <a name="remarks"></a>备注  
 页大小会影响多少滑块移对应**TB_PAGEUP**和**TB_PAGEDOWN**通知。  
  
##  <a name="setpos"></a>CSliderCtrl::SetPos  
 滑块控件中的设置将滑块的当前位置。  
  
```  
void SetPos(int nPos);
```  
  
### <a name="parameters"></a>参数  
 `nPos`  
 指定新滚动条的位置。  
  
##  <a name="setrange"></a>CSliderCtrl::SetRange  
 滑块控件中的滑块设置范围 （最小和最大位置）。  
  
```  
void SetRange(
    int nMin,  
    int nMax,  
    BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `nMin`  
 滑块的最小位置。  
  
 `nMax`  
 滑块的最大位置。  
  
 `bRedraw`  
 重绘标志中。 如果此参数为**TRUE**，滑块在重绘后此范围被设置; 否则滑块不在重绘。  
  
##  <a name="setrangemax"></a>CSliderCtrl::SetRangeMax  
 滑块控件中的滑块设置的最大范围。  
  
```  
void SetRangeMax(
    int nMax,  
    BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `nMax`  
 滑块的最大位置。  
  
 `bRedraw`  
 重绘标志中。 如果此参数为**TRUE**，滑块在重绘后此范围被设置; 否则滑块不在重绘。  
  
##  <a name="setrangemin"></a>CSliderCtrl::SetRangeMin  
 滑块控件中的滑块设置最小的范围。  
  
```  
void SetRangeMin(
    int nMin,  
    BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `nMin`  
 滑块的最小位置。  
  
 `bRedraw`  
 重绘标志中。 如果此参数为**TRUE**，滑块在重绘后此范围被设置; 否则滑块不在重绘。  
  
##  <a name="setselection"></a>CSliderCtrl::SetSelection  
 滑块控件中的设置当前所选内容的起始和结束位置。  
  
```  
void SetSelection(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>参数  
 `nMin`  
 滑块的起始位置。  
  
 `nMax`  
 滑块的结束位置。  
  
##  <a name="setthumblength"></a>CSliderCtrl::SetThumbLength  
 设置当前的 trackbar 控件中的滑块的长度。  
  
```  
void SetThumbLength(int nLength);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in] `nLength`|将滑块，以像素为单位的长度。|  
  
### <a name="remarks"></a>备注  
 此方法要求 trackbar 控件设置为[TBS_FIXEDLENGTH](http://msdn.microsoft.com/library/windows/desktop/bb760147)样式。  
  
 此方法可发送[TBM_SETTHUMBLENGTH](http://msdn.microsoft.com/library/windows/desktop/bb760234)消息，Windows SDK 中介绍。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_sliderCtrl`，即用于访问当前 trackbar 控件。 该示例还定义一个变量， `thumbLength`，即用于存储 trackbar 控件水平滚动块组件的默认长度。 在下一步的示例中使用这些变量。  
  
 [!code-cpp[NVC_MFC_CSliderCtrl_s1#1](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例将 trackbar 控件水平滚动块组件设置为两次其默认长度。  
  
 [!code-cpp[NVC_MFC_CSliderCtrl_s1#2](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]  
  
##  <a name="settic"></a>CSliderCtrl::SetTic  
 滑块控件中的设置的刻度线的位置。  
  
```  
BOOL SetTic(int nTic);
```  
  
### <a name="parameters"></a>参数  
 `nTic`  
 刻度线的位置。 此参数必须指定是正数值。  
  
### <a name="return-value"></a>返回值  
 如果设置刻度线; 则为非 0否则为 0。  
  
##  <a name="setticfreq"></a>CSliderCtrl::SetTicFreq  
 设置与的刻度线显示在滑块的频率。  
  
```  
void SetTicFreq(int nFreq);
```  
  
### <a name="parameters"></a>参数  
 *nFreq*  
 刻度线的频率。  
  
### <a name="remarks"></a>备注  
 例如，如果频率设置为 2，刻度线被显示为滑块的范围中的每个其他递增。 默认设置为频率为 1 （即，与刻度线关联的范围中每个增量是）。  
  
 你必须创建与控件`TBS_AUTOTICKS`要使用此函数样式。 有关详细信息，请参阅[CSliderCtrl::Create](#create)。  
  
##  <a name="settipside"></a>CSliderCtrl::SetTipSide  
 位置 trackbar 控件工具提示控件使用。  
  
```  
int SetTipSide(int nLocation);
```  
  
### <a name="parameters"></a>参数  
 `nLocation`  
 表示在显示工具提示控件的位置的值。 有关可能的值的列表，请参阅 Win32 消息[TBM_SETTIPSIDE](http://msdn.microsoft.com/library/windows/desktop/bb760240)，如 Windows SDK 中所述。  
  
### <a name="return-value"></a>返回值  
 一个表示工具提示控件的前一个位置的值。 返回的值等于的可能值之一`nLocation`。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为**TBM_SETTIPSIDE**，如 Windows SDK 中所述。 滑块控件使用**TBS_TOOLTIPS**样式显示工具提示。 滑块控件样式的说明，请参阅[Trackbar 控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760147)Windows SDK 中。  
  
##  <a name="settooltips"></a>CSliderCtrl::SetToolTips  
 将工具提示控件分配给滑块控件。  
  
```  
void SetToolTips(CToolTipCtrl* pWndTip);
```  
  
### <a name="parameters"></a>参数  
 `pWndTip`  
 指向的指针[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)对象，其中包含用于与滑块控件的工具提示。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的 Win32 消息行为[TBM_SETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb760242)，如 Windows SDK 中所述。 与创建滑块控件时**TBS_TOOLTIPS**样式，它创建显示滑块的当前位置的滑块旁边显示的默认工具提示控件。 滑块控件样式的说明，请参阅[Trackbar 控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760147)Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 CMNCTRL2](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CProgressCtrl 类](../../mfc/reference/cprogressctrl-class.md)
