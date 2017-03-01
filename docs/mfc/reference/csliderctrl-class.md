---
title: "CSliderCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSliderCtrl
dev_langs:
- C++
helpviewer_keywords:
- Windows common controls [C++], CSliderCtrl
- slider controls, CSliderCtrl class
- CSliderCtrl class, common controls
- CSliderCtrl class
ms.assetid: dd12b084-4eda-4550-a810-8f3cfb06b871
caps.latest.revision: 22
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
ms.openlocfilehash: 0d024c7d6670ff3b7a94b9657151e7bf1958d5f1
ms.lasthandoff: 02/24/2017

---
# <a name="csliderctrl-class"></a>CSliderCtrl 类
提供 Windows 公共滑块控件的功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CSliderCtrl : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CSliderCtrl::CSliderCtrl](#csliderctrl)|构造 `CSliderCtrl` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CSliderCtrl::ClearSel](#clearsel)|清除滑块控件中的当前所选内容。|  
|[CSliderCtrl::ClearTics](#cleartics)|从一个滑块控件中删除当前的刻度线。|  
|[CSliderCtrl::Create](#create)|创建滑块控件，并将其附加到`CSliderCtrl`对象。|  
|[CSliderCtrl::CreateEx](#createex)|创建与指定的 Windows 扩展样式的滑块控件，并将其附加到`CSliderCtrl`对象。|  
|[CSliderCtrl::GetBuddy](#getbuddy)|检索位于给定位置的滑块控件合作者窗口的句柄。|  
|[CSliderCtrl::GetChannelRect](#getchannelrect)|检索通道滑块控件的大小。|  
|[CSliderCtrl::GetLineSize](#getlinesize)|检索一个滑块控件的行大小。|  
|[CSliderCtrl::GetNumTics](#getnumtics)|检索滑块控件中的刻度的数。|  
|[CSliderCtrl::GetPageSize](#getpagesize)|检索一个滑块控件的页大小。|  
|[CSliderCtrl::GetPos](#getpos)|检索当前滑块的位置。|  
|[CSliderCtrl::GetRange](#getrange)|检索一个滑块的最小和最大位置。|  
|[CSliderCtrl::GetRangeMax](#getrangemax)|检索一个滑块的最大位置。|  
|[CSliderCtrl::GetRangeMin](#getrangemin)|检索一个滑块的最小位置。|  
|[CSliderCtrl::GetSelection](#getselection)|检索当前所选内容的范围。|  
|[CSliderCtrl::GetThumbLength](#getthumblength)|检索当前 trackbar 控件中的滑块的长度。|  
|[CSliderCtrl::GetThumbRect](#getthumbrect)|检索滑块控件的滚动块的大小。|  
|[CSliderCtrl::GetTic](#gettic)|检索指定的刻度线的位置。|  
|[CSliderCtrl::GetTicArray](#getticarray)|检索的滑块控件的刻度线位置的数组。|  
|[CSliderCtrl::GetTicPos](#getticpos)|检索工作区坐标中指定的刻度线的位置。|  
|[CSliderCtrl::GetToolTips](#gettooltips)|如果有的话，检索分配给滑块控件的工具提示控件的句柄。|  
|[CSliderCtrl::SetBuddy](#setbuddy)|将窗口分配为滑块控件与合作者窗口。|  
|[CSliderCtrl::SetLineSize](#setlinesize)|设置滑块控件的行大小。|  
|[CSliderCtrl::SetPageSize](#setpagesize)|设置滑块控件的页面大小。|  
|[CSliderCtrl::SetPos](#setpos)|设置滑块的当前位置。|  
|[CSliderCtrl::SetRange](#setrange)|设置滑块的最小和最大位置。|  
|[CSliderCtrl::SetRangeMax](#setrangemax)|设置滑块的最大位置。|  
|[CSliderCtrl::SetRangeMin](#setrangemin)|设置滑块的最小位置。|  
|[CSliderCtrl::SetSelection](#setselection)|设置当前选定项的范围。|  
|[CSliderCtrl::SetThumbLength](#setthumblength)|对于当前 trackbar 控件中设置滑块的长度。|  
|[CSliderCtrl::SetTic](#settic)|设置指定的刻度线的位置。|  
|[CSliderCtrl::SetTicFreq](#setticfreq)|设置刻度线的频率，每个滑块控件递增的标记。|  
|[CSliderCtrl::SetTipSide](#settipside)|位置工具提示控件使用 trackbar 控件。|  
|[CSliderCtrl::SetToolTips](#settooltips)|将工具提示控件分配给一个滑块控件。|  
  
## <a name="remarks"></a>备注  
 "滑块控件"(也称为 trackbar) 是一个包含滑块和可选刻度线的窗口。 当用户使用鼠标或箭头键移动滑块时，控件将发送通知消息来指示更改。  
  
 当您希望用户选择一个离散值或位于一个范围中的一组连续值时，滑动控件很有用。 例如，您可能使用滑块控件允许用户通过将滑块移动到给定刻度线来设置重复速率。  
  
 此控件 (并因此`CSliderCtrl`类) 仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 下运行的程序和更高版本。  
  
 在创建它时指定的增量移动滑块。 例如，如果您指定滑块应具有五个范围，滑块只能占用&6; 个位置︰ 在左侧的滑块控件和每个增量的范围中的一个位置的位置。 通常，这些位置中的每个位置将用一个刻度线标识。  
  
 通过使用构造函数创建一个滑块和**创建**成员函数`CSliderCtrl`。 一旦您已创建滑块控件，可以使用中的成员函数`CSliderCtrl`来更改许多其属性。 可进行的更改包括设置滑块的最小和最大位置、绘制刻度线、设置选择范围以及重新定位滑块。  
  
 有关详细信息使用`CSliderCtrl`，请参阅[控件](../../mfc/controls-mfc.md)和[使用 CSliderCtrl](../../mfc/using-csliderctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSliderCtrl`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcmn.h  
  
##  <a name="a-nameclearsela--csliderctrlclearsel"></a><a name="clearsel"></a>CSliderCtrl::ClearSel  
 清除滑块控件中的当前所选内容。  
  
```  
void ClearSel(BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `bRedraw`  
 重绘标志。 如果此参数为**TRUE**，清除所选内容后，重绘滑块; 否则滑块不重绘。  
  
##  <a name="a-nameclearticsa--csliderctrlcleartics"></a><a name="cleartics"></a>CSliderCtrl::ClearTics  
 从一个滑块控件中删除当前的刻度线。  
  
```  
void ClearTics(BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `bRedraw`  
 重绘标志。 如果此参数为**TRUE**，滑块在重绘的刻度线将被清除之后; 否则滑块不重绘。  
  
##  <a name="a-namecreatea--csliderctrlcreate"></a><a name="create"></a>CSliderCtrl::Create  
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
 指定滑块控件样式。 应用的任意组合[滑块控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760147)、 中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]，到控件。  
  
 `rect`  
 指定滑块控件的大小和位置。 它可为[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构。  
  
 `pParentWnd`  
 指定滑块控件的父窗口，通常`CDialog`。 它不能**NULL**。  
  
 `nID`  
 指定滑块控件的 id。  
  
### <a name="return-value"></a>返回值  
 如果初始化成功，则非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 您构造`CSliderCtrl`分两个步骤。 首先，调用构造函数中，，然后调用**创建**，它创建滑块控件，并将其附加到`CSliderCtrl`对象。  
  
 具体取决于设置的值`dwStyle`，滑块控件可具有垂直或水平方向。 它可以具有刻度线任一侧边，还是两者皆否。 它还可以用于指定一系列连续值。  
  
 若要将扩展的窗口样式应用于滑块控件，调用[CreateEx](#createex)而不是**创建**。  
  
##  <a name="a-namecreateexa--csliderctrlcreateex"></a><a name="createex"></a>CSliderCtrl::CreateEx  
 创建控件 （子窗口），并将其与相关联`CSliderCtrl`对象。  
  
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
 指定滑块控件样式。 应用的任意组合[滑块控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760147)、 中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]，到控件。  
  
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
  
##  <a name="a-namecsliderctrla--csliderctrlcsliderctrl"></a><a name="csliderctrl"></a>CSliderCtrl::CSliderCtrl  
 构造 `CSliderCtrl` 对象。  
  
```  
CSliderCtrl();
```  
  
##  <a name="a-namegetbuddya--csliderctrlgetbuddy"></a><a name="getbuddy"></a>CSliderCtrl::GetBuddy  
 检索位于给定位置的滑块控件合作者窗口的句柄。  
  
```  
CWnd* GetBuddy(BOOL fLocation = TRUE) const;  
```  
  
### <a name="parameters"></a>参数  
 `fLocation`  
 一个布尔值，该值指示这两个合作者窗口句柄来检索。 可以是以下值之一：  
  
- **TRUE**检索左侧的滑块合作者窗口的句柄。 如果滑块控件使用`TBS_VERT`样式，该消息将检索滑块上方好友。  
  
- **FALSE**检索右侧的滑块合作者窗口的句柄。 如果滑块控件使用`TBS_VERT`样式，该消息将检索滑块下方好友。  
  
### <a name="return-value"></a>返回值  
 一个指向[CWnd](../../mfc/reference/cwnd-class.md)对象，它是在指定的位置在合作者窗口`fLocation`，或**NULL**如果在该位置不存在任何合作者窗口。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TBM_GETBUDDY](http://msdn.microsoft.com/library/windows/desktop/bb760178)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 滑块控件样式的说明，请参阅[Trackbar 控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760147)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetchannelrecta--csliderctrlgetchannelrect"></a><a name="getchannelrect"></a>CSliderCtrl::GetChannelRect  
 检索的大小和位置的滑块控件的通道的绑定矩形。  
  
```  
void GetChannelRect(LPRECT lprc) const;  
```  
  
### <a name="parameters"></a>参数  
 `lprc`  
 一个指向[CRect](../../atl-mfc-shared/reference/crect-class.md)函数返回时包含的大小和位置的通道的对象的边框。  
  
### <a name="remarks"></a>备注  
 通道是通过滑块移动和选择范围时，它包含突出显示的区域。  
  
##  <a name="a-namegetlinesizea--csliderctrlgetlinesize"></a><a name="getlinesize"></a>CSliderCtrl::GetLineSize  
 检索一个滑块控件的行的大小。  
  
```  
int GetLineSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 滑块控件的行的大小。  
  
### <a name="remarks"></a>备注  
 行大小会影响多少滑块移对应**TB_LINEUP**和**TB_LINEDOWN**通知。 行大小的默认设置为 1。  
  
##  <a name="a-namegetnumticsa--csliderctrlgetnumtics"></a><a name="getnumtics"></a>CSliderCtrl::GetNumTics  
 检索滑块控件中的刻度的数。  
  
```  
UINT GetNumTics() const;  
```  
  
### <a name="return-value"></a>返回值  
 滑块控件中的刻度数。  
  
##  <a name="a-namegetpagesizea--csliderctrlgetpagesize"></a><a name="getpagesize"></a>CSliderCtrl::GetPageSize  
 检索滑块控件的页的大小。  
  
```  
int GetPageSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 滑块控件的页面的大小。  
  
### <a name="remarks"></a>备注  
 页面大小会影响多少滑块移对应**TB_PAGEUP**和**TB_PAGEDOWN**通知。  
  
##  <a name="a-namegetposa--csliderctrlgetpos"></a><a name="getpos"></a>CSliderCtrl::GetPos  
 检索滑块控件中的滑块的当前位置。  
  
```  
int GetPos() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前位置。  
  
##  <a name="a-namegetrangea--csliderctrlgetrange"></a><a name="getrange"></a>CSliderCtrl::GetRange  
 检索大和最小滑块位置中的滑块控件。  
  
```  
void GetRange(
    int& nMin,  
    int& nMax) const;  
```  
  
### <a name="parameters"></a>参数  
 `nMin`  
 对一个整数，它接收的最小位置的引用。  
  
 `nMax`  
 对一个整数，它接收的最大位置的引用。  
  
### <a name="remarks"></a>备注  
 此函数将值复制到引用的整数`nMin`和`nMax`。  
  
##  <a name="a-namegetrangemaxa--csliderctrlgetrangemax"></a><a name="getrangemax"></a>CSliderCtrl::GetRangeMax  
 检索滑块控件中的滑块的最大位置。  
  
```  
int GetRangeMax() const;  
```  
  
### <a name="return-value"></a>返回值  
 控件的最大位置。  
  
##  <a name="a-namegetrangemina--csliderctrlgetrangemin"></a><a name="getrangemin"></a>CSliderCtrl::GetRangeMin  
 检索滑块控件中的滑块的最小位置。  
  
```  
int GetRangeMin() const;  
```  
  
### <a name="return-value"></a>返回值  
 控件的最小位置。  
  
##  <a name="a-namegetselectiona--csliderctrlgetselection"></a><a name="getselection"></a>CSliderCtrl::GetSelection  
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
  
##  <a name="a-namegetthumblengtha--csliderctrlgetthumblength"></a><a name="getthumblength"></a>CSliderCtrl::GetThumbLength  
 检索当前 trackbar 控件中的滑块的长度。  
  
```  
int GetThumbLength() const;  
```  
  
### <a name="return-value"></a>返回值  
 滑块，以像素为单位的长度。  
  
### <a name="remarks"></a>备注  
 此方法可发送[TBM_GETTHUMBLENGTH](http://msdn.microsoft.com/library/windows/desktop/bb760201)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetthumbrecta--csliderctrlgetthumbrect"></a><a name="getthumbrect"></a>CSliderCtrl::GetThumbRect  
 检索的大小和滑块控件中的滑块 （缩略图） 的边框的位置。  
  
```  
void GetThumbRect(LPRECT lprc) const;  
```  
  
### <a name="parameters"></a>参数  
 `lprc`  
 一个指向`CRect`包含滑块的边框，当函数返回的对象。  
  
##  <a name="a-namegettica--csliderctrlgettic"></a><a name="gettic"></a>CSliderCtrl::GetTic  
 检索滑块控件中的刻度线的位置。  
  
```  
int GetTic(int nTic) const;  
```  
  
### <a name="parameters"></a>参数  
 `nTic`  
 确定刻度线的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 指定的刻度线或 – 1 如果位置`nTic`未指定的有效索引。  
  
##  <a name="a-namegetticarraya--csliderctrlgetticarray"></a><a name="getticarray"></a>CSliderCtrl::GetTicArray  
 检索数组，其中包含一个滑块控件的刻度线的位置的地址。  
  
```  
DWORD* GetTicArray() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个数组，包含滑块控件的刻度线位置的地址。  
  
##  <a name="a-namegetticposa--csliderctrlgetticpos"></a><a name="getticpos"></a>CSliderCtrl::GetTicPos  
 检索刻度线的滑块控件中的当前物理位置。  
  
```  
int GetTicPos(int nTic) const;  
```  
  
### <a name="parameters"></a>参数  
 `nTic`  
 确定刻度线的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 物理位置，在客户端坐标中，指定的刻度线或 – 1 如果`nTic`未指定的有效索引。  
  
##  <a name="a-namegettooltipsa--csliderctrlgettooltips"></a><a name="gettooltips"></a>CSliderCtrl::GetToolTips  
 如果有的话，检索分配给滑块控件的工具提示控件的句柄。  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)对象，或**NULL**工具提示是否不可用。 如果滑块控件不使用**TBS_TOOLTIPS**样式，则返回值是**NULL**。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TBM_GETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb760209)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 请注意，此成员函数返回`CToolTipCtrl`对象而不是控件的句柄。  
  
 滑块控件样式的说明，请参阅[Trackbar 控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760147)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetbuddya--csliderctrlsetbuddy"></a><a name="setbuddy"></a>CSliderCtrl::SetBuddy  
 将窗口分配为滑块控件与合作者窗口。  
  
```  
CWnd* SetBuddy(
    CWnd* pWndBuddy,  
    BOOL fLocation = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `pWndBuddy`  
 一个指向`CWnd`将设置为滑块控件的好友的对象。  
  
 `fLocation`  
 值，该值指定要显示在合作者窗口的位置。 此值可以是以下项之一︰  
  
- **TRUE**好友仅当使用 trackbar 控件将显示跟踪条的左侧`TBS_HORZ`样式。 如果跟踪条使用`TBS_VERT`样式，好友出现 trackbar 控件的上方。  
  
- **FALSE**好友仅当使用 trackbar 控件将显示跟踪条右侧`TBS_HORZ`样式。 如果跟踪条使用`TBS_VERT`样式，好友出现 trackbar 控件的下方。  
  
### <a name="return-value"></a>返回值  
 一个指向[CWnd](../../mfc/reference/cwnd-class.md)以前分配给该位置的滑块控件的对象。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TBM_SETBUDDY](http://msdn.microsoft.com/library/windows/desktop/bb760213)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 请注意，此成员函数使用指向指针`CWnd`对象，而不是为其返回值和参数的窗口句柄。  
  
 滑块控件样式的说明，请参阅[Trackbar 控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760147)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetlinesizea--csliderctrlsetlinesize"></a><a name="setlinesize"></a>CSliderCtrl::SetLineSize  
 设置滑块控件的行的大小。  
  
```  
int SetLineSize(int nSize);
```  
  
### <a name="parameters"></a>参数  
 `nSize`  
 滑块控件的新的行大小。  
  
### <a name="return-value"></a>返回值  
 以前的行大小。  
  
### <a name="remarks"></a>备注  
 行大小会影响多少滑块移对应**TB_LINEUP**和**TB_LINEDOWN**通知。  
  
##  <a name="a-namesetpagesizea--csliderctrlsetpagesize"></a><a name="setpagesize"></a>CSliderCtrl::SetPageSize  
 设置滑块控件的页面的大小。  
  
```  
int SetPageSize(int nSize);
```  
  
### <a name="parameters"></a>参数  
 `nSize`  
 滑块控件的新的页大小。  
  
### <a name="return-value"></a>返回值  
 以前的页面大小。  
  
### <a name="remarks"></a>备注  
 页面大小会影响多少滑块移对应**TB_PAGEUP**和**TB_PAGEDOWN**通知。  
  
##  <a name="a-namesetposa--csliderctrlsetpos"></a><a name="setpos"></a>CSliderCtrl::SetPos  
 滑块控件中的设置滑块的当前位置。  
  
```  
void SetPos(int nPos);
```  
  
### <a name="parameters"></a>参数  
 `nPos`  
 指定新的滑块位置。  
  
##  <a name="a-namesetrangea--csliderctrlsetrange"></a><a name="setrange"></a>CSliderCtrl::SetRange  
 滑块控件中的滑块设置的范围 （最小和最大位置）。  
  
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
 表示重绘的标志。 如果此参数为**TRUE**，滑块在重绘后设置范围; 否则滑块不重绘。  
  
##  <a name="a-namesetrangemaxa--csliderctrlsetrangemax"></a><a name="setrangemax"></a>CSliderCtrl::SetRangeMax  
 滑块控件中的滑块设置最大范围。  
  
```  
void SetRangeMax(
    int nMax,  
    BOOL bRedraw = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `nMax`  
 滑块的最大位置。  
  
 `bRedraw`  
 表示重绘的标志。 如果此参数为**TRUE**，滑块在重绘后设置范围; 否则滑块不重绘。  
  
##  <a name="a-namesetrangemina--csliderctrlsetrangemin"></a><a name="setrangemin"></a>CSliderCtrl::SetRangeMin  
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
 表示重绘的标志。 如果此参数为**TRUE**，滑块在重绘后设置范围; 否则滑块不重绘。  
  
##  <a name="a-namesetselectiona--csliderctrlsetselection"></a><a name="setselection"></a>CSliderCtrl::SetSelection  
 滑块控件中的设置为当前所选内容的起始和结束位置。  
  
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
  
##  <a name="a-namesetthumblengtha--csliderctrlsetthumblength"></a><a name="setthumblength"></a>CSliderCtrl::SetThumbLength  
 对于当前 trackbar 控件中设置滑块的长度。  
  
```  
void SetThumbLength(int nLength);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|[in] `nLength`|滑块，以像素为单位的长度。|  
  
### <a name="remarks"></a>备注  
 此方法要求将 trackbar 控件设置成[TBS_FIXEDLENGTH](http://msdn.microsoft.com/library/windows/desktop/bb760147)样式。  
  
 此方法可发送[TBM_SETTHUMBLENGTH](http://msdn.microsoft.com/library/windows/desktop/bb760234)消息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>示例  
 下面的代码示例定义变量， `m_sliderCtrl`，也就是说，用来访问当前 trackbar 控件。 该示例还定义一个变量， `thumbLength`，也就是说，用来存储 trackbar 控件 thumb 组件的默认长度。 在下一个示例中使用这些变量。  
  
 [!code-cpp[NVC_MFC_CSliderCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/csliderctrl-class_1.h)]  
  
### <a name="example"></a>示例  
 下面的代码示例将 trackbar 控件 thumb 组件设置为其默认长度的两倍。  
  
 [!code-cpp[NVC_MFC_CSliderCtrl_s&#1;&2;](../../mfc/reference/codesnippet/cpp/csliderctrl-class_2.cpp)]  
  
##  <a name="a-namesettica--csliderctrlsettic"></a><a name="settic"></a>CSliderCtrl::SetTic  
 滑块控件中的设置刻度线的位置。  
  
```  
BOOL SetTic(int nTic);
```  
  
### <a name="parameters"></a>参数  
 `nTic`  
 刻度线的位置。 此参数必须指定一个正的值。  
  
### <a name="return-value"></a>返回值  
 设置刻度线; 如果非零值否则为 0。  
  
##  <a name="a-namesetticfreqa--csliderctrlsetticfreq"></a><a name="setticfreq"></a>CSliderCtrl::SetTicFreq  
 设置刻度线与标记显示在一个滑块的频率。  
  
```  
void SetTicFreq(int nFreq);
```  
  
### <a name="parameters"></a>参数  
 *nFreq*  
 刻度线的频率。  
  
### <a name="remarks"></a>备注  
 例如，如果频率设置为 2，刻度线被显示在滑块的范围内的每个其他递增。 默认设置的频率 1 （即范围中的每个增量是刻度线与相关联）。  
  
 您必须创建此控件与`TBS_AUTOTICKS`样式，以使用此函数。 有关详细信息，请参阅[CSliderCtrl::Create](#create)。  
  
##  <a name="a-namesettipsidea--csliderctrlsettipside"></a><a name="settipside"></a>CSliderCtrl::SetTipSide  
 位置工具提示控件使用 trackbar 控件。  
  
```  
int SetTipSide(int nLocation);
```  
  
### <a name="parameters"></a>参数  
 `nLocation`  
 值，该值表示用于显示工具提示控件的位置。 有关可能的值的列表，请参阅的 Win32 消息[TBM_SETTIPSIDE](http://msdn.microsoft.com/library/windows/desktop/bb760240)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>返回值  
 一个表示工具提示控件的前一个位置的值。 返回的值等于的可能值之一`nLocation`。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息**TBM_SETTIPSIDE**，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 滑块控件，使用**TBS_TOOLTIPS**样式显示工具提示。 滑块控件样式的说明，请参阅[Trackbar 控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760147)中[!INCLUDE[winsdkshort](../../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。  
  
##  <a name="a-namesettooltipsa--csliderctrlsettooltips"></a><a name="settooltips"></a>CSliderCtrl::SetToolTips  
 将工具提示控件分配给一个滑块控件。  
  
```  
void SetToolTips(CToolTipCtrl* pWndTip);
```  
  
### <a name="parameters"></a>参数  
 `pWndTip`  
 一个指向[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)对象，其中包含要与滑块控件一起使用的工具提示。  
  
### <a name="remarks"></a>备注  
 此成员函数实现的行为的 Win32 消息[TBM_SETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb760242)，如中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 当滑块控件创建带有**TBS_TOOLTIPS**样式，它可创建显示滑块的当前位置的滑块旁边显示的默认工具提示控件。 滑块控件样式的说明，请参阅[Trackbar 控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760147)中[!INCLUDE[winsdkshort](../../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 CMNCTRL2](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CProgressCtrl 类](../../mfc/reference/cprogressctrl-class.md)

