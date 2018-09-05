---
title: CSliderCtrl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6bd20852f1dfd278d4ae58cc6c67d6047579cd08
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693187"
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
|[CSliderCtrl::ClearSel](#clearsel)|清除滑块控件中的当前所选内容。|  
|[CSliderCtrl::ClearTics](#cleartics)|从滑块控件中删除当前刻度。|  
|[CSliderCtrl::Create](#create)|创建滑块控件，并将其附加到`CSliderCtrl`对象。|  
|[CSliderCtrl::CreateEx](#createex)|使用指定的 Windows 扩展样式创建滑块控件，并将其附加到`CSliderCtrl`对象。|  
|[CSliderCtrl::GetBuddy](#getbuddy)|检索到的给定位置的滑块控件合作者窗口的句柄。|  
|[CSliderCtrl::GetChannelRect](#getchannelrect)|检索滑块控件的通道的大小。|  
|[CSliderCtrl::GetLineSize](#getlinesize)|检索一个滑块控件的行大小。|  
|[CSliderCtrl::GetNumTics](#getnumtics)|检索滑块控件中刻度线的数目。|  
|[CSliderCtrl::GetPageSize](#getpagesize)|检索一个滑块控件的页大小。|  
|[CSliderCtrl::GetPos](#getpos)|检索当前滑块的位置。|  
|[CSliderCtrl::GetRange](#getrange)|检索一个滑块的最小和最大位置。|  
|[CSliderCtrl::GetRangeMax](#getrangemax)|检索一个滑块的最大位置。|  
|[CSliderCtrl::GetRangeMin](#getrangemin)|检索一个滑块的最小位置。|  
|[CSliderCtrl::GetSelection](#getselection)|检索当前所选内容的范围。|  
|[CSliderCtrl::GetThumbLength](#getthumblength)|检索当前的跟踪条控件中的滑块的长度。|  
|[CSliderCtrl::GetThumbRect](#getthumbrect)|检索滑块控件的滚动块的大小。|  
|[CSliderCtrl::GetTic](#gettic)|检索指定的刻度线的位置。|  
|[CSliderCtrl::GetTicArray](#getticarray)|检索刻度线的滑块控件的标记位置的数组。|  
|[CSliderCtrl::GetTicPos](#getticpos)|检索在客户端坐标中指定的刻度线的位置。|  
|[CSliderCtrl::GetToolTips](#gettooltips)|如果有，则检索到分配给滑块控件，该工具提示控件的句柄。|  
|[CSliderCtrl::SetBuddy](#setbuddy)|将窗口分配为滑块控件的合作者窗口。|  
|[CSliderCtrl::SetLineSize](#setlinesize)|设置滑块控件的行大小。|  
|[CSliderCtrl::SetPageSize](#setpagesize)|设置滑块控件的页大小。|  
|[CSliderCtrl::SetPos](#setpos)|设置当前滑块的位置。|  
|[CSliderCtrl::SetRange](#setrange)|设置滑块的最小和最大位置。|  
|[CSliderCtrl::SetRangeMax](#setrangemax)|设置滑块的最大位置。|  
|[CSliderCtrl::SetRangeMin](#setrangemin)|设置滑块的最小位置。|  
|[CSliderCtrl::SetSelection](#setselection)|设置当前选择的范围。|  
|[CSliderCtrl::SetThumbLength](#setthumblength)|设置当前的跟踪条控件中的滑块的长度。|  
|[CSliderCtrl::SetTic](#settic)|设置指定的刻度线的位置。|  
|[CSliderCtrl::SetTicFreq](#setticfreq)|设置刻度线的频率，每个滑块控件增量的标记。|  
|[CSliderCtrl::SetTipSide](#settipside)|位置跟踪条控件的工具提示控件使用。|  
|[CSliderCtrl::SetToolTips](#settooltips)|将工具提示控件分配给一个滑块控件。|  
  
## <a name="remarks"></a>备注  
 "滑块控件"（也称为跟踪条） 是一个窗口，其中包含一个滑块和可选刻度线。 当用户使用鼠标或箭头键移动滑块时，控件将发送通知消息来指示更改。  
  
 当您希望用户选择一个离散值或位于一个范围中的一组连续值时，滑动控件很有用。 例如，您可能使用滑块控件允许用户通过将滑块移动到给定刻度线来设置重复速率。  
  
 此控件 (并因此`CSliderCtrl`类) 仅适用于 Windows 95/98 和 Windows NT 版本 3.51 下运行的程序和更高版本。  
  
 在创建它时指定的增量移动滑块。 例如，如果您指定滑块应具有一系列五个，滑块只能占用 6 个位置： 在左侧和右侧的滑块控件和每个增量的范围中的一个位置的位置。 通常，这些位置中的每个位置将用一个刻度线标识。  
  
 使用构造函数创建一个滑块和`Create`成员函数的`CSliderCtrl`。 创建滑块控件后，可以使用中的成员函数`CSliderCtrl`更改许多其属性。 可进行的更改包括设置滑块的最小和最大位置、绘制刻度线、设置选择范围以及重新定位滑块。  
  
 有关使用的详细信息`CSliderCtrl`，请参阅[控件](../../mfc/controls-mfc.md)并[使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSliderCtrl`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcmn.h  
  
##  <a name="clearsel"></a>  CSliderCtrl::ClearSel  
 清除滑块控件中的当前所选内容。  
  
```  
void ClearSel(BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>参数  
 *bRedraw*  
 重绘标志。 如果此参数为 TRUE，滑块清除所选内容; 后重绘否则滑块不会重新绘制。  
  
##  <a name="cleartics"></a>  CSliderCtrl::ClearTics  
 从滑块控件中删除当前刻度。  
  
```  
void ClearTics(BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>参数  
 *bRedraw*  
 重绘标志。 如果此参数为 TRUE，滑块的刻度清除; 后重绘否则滑块不会重新绘制。  
  
##  <a name="create"></a>  CSliderCtrl::Create  
 创建滑块控件，并将其附加到`CSliderCtrl`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 *dwStyle*  
 指定滑块控件的样式。 应用的任意组合[滑块控件样式](/windows/desktop/Controls/trackbar-control-styles)Windows SDK，向控件中所述。  
  
 *rect*  
 指定滑块控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)结构。  
  
 *pParentWnd*  
 通常指定滑块控件的父窗口， `CDialog`。 它不能为 NULL。  
  
 *nID*  
 指定滑块控件的 id。  
  
### <a name="return-value"></a>返回值  
 如果初始化成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 构造`CSliderCtrl`中两个步骤。 首先，调用构造函数中，，然后调用`Create`，它创建滑块控件，并将其附加到`CSliderCtrl`对象。  
  
 具体取决于设置的值*dwStyle*，滑块控件可以具有垂直或水平方向。 它可以具有刻度任意一侧边，还是两者皆否。 此外可以用于指定一系列连续值。  
  
 若要将扩展的窗口样式应用于滑块控件，调用[CreateEx](#createex)而不是`Create`。  
  
##  <a name="createex"></a>  CSliderCtrl::CreateEx  
 创建控件 （子窗口），并将其与`CSliderCtrl`对象。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 *dwExStyle*  
 指定要创建的控件的扩展的样式。 扩展 Windows 样式的列表，请参阅*dwExStyle*参数[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) Windows SDK 中。  
  
 *dwStyle*  
 指定滑块控件的样式。 应用的任意组合[滑块控件样式](/windows/desktop/Controls/trackbar-control-styles)Windows SDK，向控件中所述。  
  
 *rect*  
 对引用[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)结构的结构描述的大小和窗口的工作区中创建的位置*pParentWnd*。  
  
 *pParentWnd*  
 指向控件的父级的窗口的指针。  
  
 *nID*  
 控件的子窗口 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 使用`CreateEx`而不是[创建](#create)若要将应用扩展的 Windows 样式，指定的 Windows 扩展的样式加**WS_EX_**。  
  
##  <a name="csliderctrl"></a>  CSliderCtrl::CSliderCtrl  
 构造 `CSliderCtrl` 对象。  
  
```  
CSliderCtrl();
```  
  
##  <a name="getbuddy"></a>  CSliderCtrl::GetBuddy  
 检索到的给定位置的滑块控件合作者窗口的句柄。  
  
```  
CWnd* GetBuddy(BOOL fLocation = TRUE) const;  
```  
  
### <a name="parameters"></a>参数  
 *fLocation*  
 一个布尔值，该值指示这两个合作者窗口句柄来检索。 可以是以下值之一：  
  
- TRUE 检索左侧的滑块合作者窗口的句柄。 如果滑块控件使用 TBS_VERT 样式，该消息将检索滑块上方的好友。  
  
- FALSE 检索右侧的滑块合作者窗口的句柄。 如果滑块控件使用 TBS_VERT 样式，该消息将检索到滑块下方的好友。  
  
### <a name="return-value"></a>返回值  
 一个指向[CWnd](../../mfc/reference/cwnd-class.md)对象，它是指定的位置在合作者窗口*fLocation*，或如果该位置不存在任何合作者窗口，则为 NULL。  
  
### <a name="remarks"></a>备注  
 此成员函数可实现 Win32 消息的行为[TBM_GETBUDDY](/windows/desktop/Controls/tbm-getbuddy)，如 Windows SDK 中所述。 滑块控件样式的说明，请参阅[Trackbar 控件样式](/windows/desktop/Controls/trackbar-control-styles)Windows SDK 中。  
  
##  <a name="getchannelrect"></a>  CSliderCtrl::GetChannelRect  
 检索的大小和位置的滑块控件的通道的边界矩形。  
  
```  
void GetChannelRect(LPRECT lprc) const;  
```  
  
### <a name="parameters"></a>参数  
 *lprc*  
 一个指向[CRect](../../atl-mfc-shared/reference/crect-class.md)函数返回时包含的大小和位置的通道对象的边框。  
  
### <a name="remarks"></a>备注  
 通道是通过将滑块移动和选择范围时，其中包含突出显示的区域。  
  
##  <a name="getlinesize"></a>  CSliderCtrl::GetLineSize  
 检索滑块控件的行的大小。  
  
```  
int GetLineSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 滑块控件的行的大小。  
  
### <a name="remarks"></a>备注  
 行大小会影响多少滑块移动 TB_LINEUP 和 TB_LINEDOWN 通知。 行大小的默认设置为 1。  
  
##  <a name="getnumtics"></a>  CSliderCtrl::GetNumTics  
 检索滑块控件中刻度线的数目。  
  
```  
UINT GetNumTics() const;  
```  
  
### <a name="return-value"></a>返回值  
 滑块控件中的刻度数。  
  
##  <a name="getpagesize"></a>  CSliderCtrl::GetPageSize  
 检索滑块控件的页的大小。  
  
```  
int GetPageSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 滑块控件的页的大小。  
  
### <a name="remarks"></a>备注  
 页面大小会影响多少滑块移动 TB_PAGEUP 和 TB_PAGEDOWN 通知。  
  
##  <a name="getpos"></a>  CSliderCtrl::GetPos  
 检索一个滑块控件中的当前位置的滑块。  
  
```  
int GetPos() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前位置。  
  
##  <a name="getrange"></a>  CSliderCtrl::GetRange  
 检索的最大和最小位置滑块滑块控件中。  
  
```  
void GetRange(
    int& nMin,  
    int& nMax) const;  
```  
  
### <a name="parameters"></a>参数  
 *nMin*  
 对一个整数，它接收的最小位置引用。  
  
 *最*  
 对一个整数，它接收的最大位置的引用。  
  
### <a name="remarks"></a>备注  
 此函数的值复制到引用的整数*nMin*并*最*。  
  
##  <a name="getrangemax"></a>  CSliderCtrl::GetRangeMax  
 检索滑块控件中的最大滑块位置。  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>返回值  
 控件的最大的位置。  
  
##  <a name="getrangemin"></a>  CSliderCtrl::GetRangeMin  
 检索滑块控件中的最小滑块位置。  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>返回值  
 控件的最小的位置。  
  
##  <a name="getselection"></a>  CSliderCtrl::GetSelection  
 检索滑块控件中当前所选内容的起始和结束位置。  
  
```  
void GetSelection(
    int& nMin,  
    int& nMax) const;  
```  
  
### <a name="parameters"></a>参数  
 *nMin*  
 对一个整数，它接收当前所选内容的起始位置的引用。  
  
 *最*  
 对一个整数，它接收当前所选内容的结束位置的引用。  
  
##  <a name="getthumblength"></a>  CSliderCtrl::GetThumbLength  
 检索当前的跟踪条控件中的滑块的长度。  
  
```  
int GetThumbLength() const;  
```  
  
### <a name="return-value"></a>返回值  
 滑块，以像素为单位的长度。  
  
### <a name="remarks"></a>备注  
 此方法将发送[TBM_GETTHUMBLENGTH](/windows/desktop/Controls/tbm-getthumblength)消息，Windows SDK 中所述。  
  
##  <a name="getthumbrect"></a>  CSliderCtrl::GetThumbRect  
 检索的大小和滑块控件中的滑块 （滚动块） 的边界矩形的位置。  
  
```  
void GetThumbRect(LPRECT lprc) const;  
```  
  
### <a name="parameters"></a>参数  
 *lprc*  
 一个指向`CRect`包含滑块的边框，当函数返回的对象。  
  
##  <a name="gettic"></a>  CSliderCtrl::GetTic  
 检索滑块控件中刻度线的位置。  
  
```  
int GetTic(int nTic) const;  
```  
  
### <a name="parameters"></a>参数  
 *nTic*  
 确定刻度的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 指定刻度线或-1，如果的位置*nTic*未指定的有效索引。  
  
##  <a name="getticarray"></a>  CSliderCtrl::GetTicArray  
 检索数组，其中包含一个滑块控件的刻度线的位置的地址。  
  
```  
DWORD* GetTicArray() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个数组，包含刻度线的滑块控件的标记位置的地址。  
  
##  <a name="getticpos"></a>  CSliderCtrl::GetTicPos  
 检索刻度线的滑块控件中的当前物理位置。  
  
```  
int GetTicPos(int nTic) const;  
```  
  
### <a name="parameters"></a>参数  
 *nTic*  
 确定刻度的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 物理位置，在客户端坐标中指定的刻度或-1，如果*nTic*未指定的有效索引。  
  
##  <a name="gettooltips"></a>  CSliderCtrl::GetToolTips  
 如果有，则检索到分配给滑块控件，该工具提示控件的句柄。  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)对象，或者如果未使用的工具提示，则为 NULL。 如果滑块控件不使用 TBS_TOOLTIPS 样式，返回值为 NULL。  
  
### <a name="remarks"></a>备注  
 此成员函数可实现 Win32 消息的行为[TBM_GETTOOLTIPS](/windows/desktop/Controls/tbm-gettooltips)，如 Windows SDK 中所述。 请注意，此成员函数返回`CToolTipCtrl`对象而不是控件的句柄。  
  
 滑块控件样式的说明，请参阅[Trackbar 控件样式](/windows/desktop/Controls/trackbar-control-styles)Windows SDK 中。  
  
##  <a name="setbuddy"></a>  CSliderCtrl::SetBuddy  
 将窗口分配为滑块控件的合作者窗口。  
  
```  
CWnd* SetBuddy(
    CWnd* pWndBuddy,  
    BOOL fLocation = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *pWndBuddy*  
 一个指向`CWnd`将设置为滑块控件的合作者的对象。  
  
 *fLocation*  
 值，该值指定要显示合作者窗口的位置。 此值可以是以下值之一：  
  
- TRUE 好友将显示向左跟踪条如果 trackbar 控件使用 TBS_HORZ 样式。 如果设定使用 TBS_VERT 样式，trackbar 控件上方会出现好友。  
  
- FALSE 好友将显示向右跟踪条如果 trackbar 控件使用 TBS_HORZ 样式。 如果设定使用 TBS_VERT 样式，好友的如下所示 trackbar 控件。  
  
### <a name="return-value"></a>返回值  
 一个指向[CWnd](../../mfc/reference/cwnd-class.md)了之前分配给该位置处的滑块控件的对象。  
  
### <a name="remarks"></a>备注  
 此成员函数可实现 Win32 消息的行为[TBM_SETBUDDY](/windows/desktop/Controls/tbm-setbuddy)，如 Windows SDK 中所述。 请注意，此成员函数使用指向`CWnd`对象，而不是为其返回值和参数的窗口句柄。  
  
 滑块控件样式的说明，请参阅[Trackbar 控件样式](/windows/desktop/Controls/trackbar-control-styles)Windows SDK 中。  
  
##  <a name="setlinesize"></a>  CSliderCtrl::SetLineSize  
 设置滑块控件的行的大小。  
  
```  
int SetLineSize(int nSize);
```  
  
### <a name="parameters"></a>参数  
 *nSize*  
 滑块控件的新行大小。  
  
### <a name="return-value"></a>返回值  
 以前的行大小。  
  
### <a name="remarks"></a>备注  
 行大小会影响多少滑块移动 TB_LINEUP 和 TB_LINEDOWN 通知。  
  
##  <a name="setpagesize"></a>  CSliderCtrl::SetPageSize  
 设置滑块控件的页大小。  
  
```  
int SetPageSize(int nSize);
```  
  
### <a name="parameters"></a>参数  
 *nSize*  
 新的滑块控件的页大小。  
  
### <a name="return-value"></a>返回值  
 以前的页面大小。  
  
### <a name="remarks"></a>备注  
 页面大小会影响多少滑块移动 TB_PAGEUP 和 TB_PAGEDOWN 通知。  
  
##  <a name="setpos"></a>  CSliderCtrl::SetPos  
 滑块控件中设置当前滑块的位置。  
  
```  
void SetPos(int nPos);
```  
  
### <a name="parameters"></a>参数  
 *nPos*  
 指定新的滑块位置。  
  
##  <a name="setrange"></a>  CSliderCtrl::SetRange  
 设置滑块控件中的滑块范围 （最小和最大位置）。  
  
```  
void SetRange(
    int nMin,  
    int nMax,  
    BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>参数  
 *nMin*  
 滑块的最小位置。  
  
 *最*  
 最大滑块的位置。  
  
 *bRedraw*  
 表示重绘的标志。 如果此参数为 TRUE，滑块设置范围; 后重绘否则滑块不会重新绘制。  
  
##  <a name="setrangemax"></a>  CSliderCtrl::SetRangeMax  
 滑块控件中的滑块设置的最大范围。  
  
```  
void SetRangeMax(
    int nMax,  
    BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>参数  
 *最*  
 最大滑块的位置。  
  
 *bRedraw*  
 表示重绘的标志。 如果此参数为 TRUE，滑块设置范围; 后重绘否则滑块不会重新绘制。  
  
##  <a name="setrangemin"></a>  CSliderCtrl::SetRangeMin  
 滑块控件中的滑块设置最小的范围。  
  
```  
void SetRangeMin(
    int nMin,  
    BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>参数  
 *nMin*  
 滑块的最小位置。  
  
 *bRedraw*  
 表示重绘的标志。 如果此参数为 TRUE，滑块设置范围; 后重绘否则滑块不会重新绘制。  
  
##  <a name="setselection"></a>  CSliderCtrl::SetSelection  
 设置滑块控件中当前所选内容的起始和结束位置。  
  
```  
void SetSelection(
    int nMin,  
    int nMax);
```  
  
### <a name="parameters"></a>参数  
 *nMin*  
 滑块的起始位置。  
  
 *最*  
 滑块的结束位置。  
  
##  <a name="setthumblength"></a>  CSliderCtrl::SetThumbLength  
 设置当前的跟踪条控件中的滑块的长度。  
  
```  
void SetThumbLength(int nLength);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*nLength*|滑块，以像素为单位的长度。|  
  
### <a name="remarks"></a>备注  
 此方法要求 trackbar 控件设置为[TBS_FIXEDLENGTH](/windows/desktop/Controls/trackbar-control-styles)样式。  
  
 此方法将发送[TBM_SETTHUMBLENGTH](/windows/desktop/Controls/tbm-setthumblength)消息，Windows SDK 中所述。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_sliderCtrl`，即用于访问当前的跟踪条控件。 该示例还定义一个变量， `thumbLength`，即用于存储跟踪条控件的 thumb 组件的默认长度。 在下一步的示例中使用这些变量。  
  
 [!code-cpp[NVC_MFC_CSliderCtrl_s1#1](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例设置两次其默认长度为跟踪条控件的 thumb 组件。  
  
 [!code-cpp[NVC_MFC_CSliderCtrl_s1#2](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]  
  
##  <a name="settic"></a>  CSliderCtrl::SetTic  
 滑块控件中设置刻度线的位置。  
  
```  
BOOL SetTic(int nTic);
```  
  
### <a name="parameters"></a>参数  
 *nTic*  
 刻度线的位置。 此参数必须指定正值。  
  
### <a name="return-value"></a>返回值  
 如果设置刻度; 非零值否则为 0。  
  
##  <a name="setticfreq"></a>  CSliderCtrl::SetTicFreq  
 设置使用的刻度线标记显示在一个滑块的频率。  
  
```  
void SetTicFreq(int nFreq);
```  
  
### <a name="parameters"></a>参数  
 *nFreq*  
 刻度线的频率。  
  
### <a name="remarks"></a>备注  
 例如，如果频率设置为 2，个滑块的范围中的每个其他增量显示刻度线标记。 默认设置为频率为 1 （即关联有刻度的范围中每个增量是）。  
  
 必须使用要使用此函数的 TBS_AUTOTICKS 样式来创建控件。 有关详细信息，请参阅[CSliderCtrl::Create](#create)。  
  
##  <a name="settipside"></a>  CSliderCtrl::SetTipSide  
 位置跟踪条控件的工具提示控件使用。  
  
```  
int SetTipSide(int nLocation);
```  
  
### <a name="parameters"></a>参数  
 *n 位置*  
 值，该值表示要显示工具提示控件的位置。 有关可能的值的列表，请参阅 Win32 消息[TBM_SETTIPSIDE](/windows/desktop/Controls/tbm-settipside)，如 Windows SDK 中所述。  
  
### <a name="return-value"></a>返回值  
 一个值，表示工具提示控件的上一位置。 返回的值等于的可能值之一*n 位置*。  
  
### <a name="remarks"></a>备注  
 Windows SDK 中所述，此成员函数实现 Win32 消息 TBM_SETTIPSIDE 的行为。 使用 TBS_TOOLTIPS 样式的滑块控件将显示工具提示。 滑块控件样式的说明，请参阅[Trackbar 控件样式](/windows/desktop/Controls/trackbar-control-styles)Windows SDK 中。  
  
##  <a name="settooltips"></a>  CSliderCtrl::SetToolTips  
 将工具提示控件分配给一个滑块控件。  
  
```  
void SetToolTips(CToolTipCtrl* pWndTip);
```  
  
### <a name="parameters"></a>参数  
 *pWndTip*  
 一个指向[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)对象，其中包含要用于滑块控件的工具提示。  
  
### <a name="remarks"></a>备注  
 此成员函数可实现 Win32 消息的行为[TBM_SETTOOLTIPS](/windows/desktop/Controls/tbm-settooltips)，如 Windows SDK 中所述。 使用 TBS_TOOLTIPS 样式创建滑块控件时，它会创建默认工具提示控件旁边的滑块，显示当前的滑块的位置显示。 滑块控件样式的说明，请参阅[Trackbar 控件样式](/windows/desktop/Controls/trackbar-control-styles)Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 CMNCTRL2](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [CProgressCtrl 类](../../mfc/reference/cprogressctrl-class.md)
