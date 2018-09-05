---
title: CPagerCtrl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CPagerCtrl
- AFXCMN/CPagerCtrl
- AFXCMN/CPagerCtrl::CPagerCtrl
- AFXCMN/CPagerCtrl::Create
- AFXCMN/CPagerCtrl::CreateEx
- AFXCMN/CPagerCtrl::ForwardMouse
- AFXCMN/CPagerCtrl::GetBkColor
- AFXCMN/CPagerCtrl::GetBorder
- AFXCMN/CPagerCtrl::GetButtonSize
- AFXCMN/CPagerCtrl::GetButtonState
- AFXCMN/CPagerCtrl::GetDropTarget
- AFXCMN/CPagerCtrl::GetScrollPos
- AFXCMN/CPagerCtrl::IsButtonDepressed
- AFXCMN/CPagerCtrl::IsButtonGrayed
- AFXCMN/CPagerCtrl::IsButtonHot
- AFXCMN/CPagerCtrl::IsButtonInvisible
- AFXCMN/CPagerCtrl::IsButtonNormal
- AFXCMN/CPagerCtrl::RecalcSize
- AFXCMN/CPagerCtrl::SetBkColor
- AFXCMN/CPagerCtrl::SetBorder
- AFXCMN/CPagerCtrl::SetButtonSize
- AFXCMN/CPagerCtrl::SetChild
- AFXCMN/CPagerCtrl::SetScrollPos
dev_langs:
- C++
helpviewer_keywords:
- CPagerCtrl [MFC], CPagerCtrl
- CPagerCtrl [MFC], Create
- CPagerCtrl [MFC], CreateEx
- CPagerCtrl [MFC], ForwardMouse
- CPagerCtrl [MFC], GetBkColor
- CPagerCtrl [MFC], GetBorder
- CPagerCtrl [MFC], GetButtonSize
- CPagerCtrl [MFC], GetButtonState
- CPagerCtrl [MFC], GetDropTarget
- CPagerCtrl [MFC], GetScrollPos
- CPagerCtrl [MFC], IsButtonDepressed
- CPagerCtrl [MFC], IsButtonGrayed
- CPagerCtrl [MFC], IsButtonHot
- CPagerCtrl [MFC], IsButtonInvisible
- CPagerCtrl [MFC], IsButtonNormal
- CPagerCtrl [MFC], RecalcSize
- CPagerCtrl [MFC], SetBkColor
- CPagerCtrl [MFC], SetBorder
- CPagerCtrl [MFC], SetButtonSize
- CPagerCtrl [MFC], SetChild
- CPagerCtrl [MFC], SetScrollPos
ms.assetid: 65ac58dd-4f5e-4b7e-b15c-e0d435a7e884
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b7fd978390a2b991da2bddedbab1c05497709d67
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43688138"
---
# <a name="cpagerctrl-class"></a>CPagerCtrl 类
`CPagerCtrl` 类用于包装 Windows 页导航控件，可以滚动此控件以查看所包含的不适合包含窗口的窗口。  
  
## <a name="syntax"></a>语法  
  
```  
class CPagerCtrl : public CWnd  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CPagerCtrl::CPagerCtrl](#cpagerctrl)|构造 `CPagerCtrl` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CPagerCtrl::Create](#create)|使用指定的样式创建的页导航控件，并将其附加到当前`CPagerCtrl`对象。|  
|[CPagerCtrl::CreateEx](#createex)|使用指定的扩展样式创建的页导航控件，并将其附加到当前`CPagerCtrl`对象。|  
|[CPagerCtrl::ForwardMouse](#forwardmouse)|启用或禁用转发[WM_MOUSEMOVE](/windows/desktop/inputdev/wm-mousemove)对包含在当前的页导航控件的窗口消息。|  
|[CPagerCtrl::GetBkColor](#getbkcolor)|检索当前的页导航控件的背景色。|  
|[CPagerCtrl::GetBorder](#getborder)|检索当前的页导航控件的边框大小。|  
|[CPagerCtrl::GetButtonSize](#getbuttonsize)|检索当前的页导航控件按钮大小。|  
|[CPagerCtrl::GetButtonState](#getbuttonstate)|检索当前的页导航控件中的指定按钮的状态。|  
|[CPagerCtrl::GetDropTarget](#getdroptarget)|检索[IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget)当前的页导航控件的接口。|  
|[CPagerCtrl::GetScrollPos](#getscrollpos)|检索当前的页导航控件的滚动位置。|  
|[CPagerCtrl::IsButtonDepressed](#isbuttondepressed)|指示当前的页导航控件指定的按钮是否处于`pressed`状态。|  
|[CPagerCtrl::IsButtonGrayed](#isbuttongrayed)|指示当前的页导航控件指定的按钮是否处于`grayed`状态。|  
|[CPagerCtrl::IsButtonHot](#isbuttonhot)|指示当前的页导航控件指定的按钮是否处于`hot`状态。|  
|[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)|指示当前的页导航控件指定的按钮是否处于`invisible`状态。|  
|[CPagerCtrl::IsButtonNormal](#isbuttonnormal)|指示当前的页导航控件指定的按钮是否处于`normal`状态。|  
|[CPagerCtrl::RecalcSize](#recalcsize)|导致当前的页导航控件，以重新计算包含窗口的大小。|  
|[CPagerCtrl::SetBkColor](#setbkcolor)|设置当前的页导航控件的背景色。|  
|[CPagerCtrl::SetBorder](#setborder)|设置当前的页导航控件的边框大小。|  
|[CPagerCtrl::SetButtonSize](#setbuttonsize)|设置当前的页导航控件按钮大小。|  
|[CPagerCtrl::SetChild](#setchild)|设置当前的页导航控件所包含的窗口。|  
|[CPagerCtrl::SetScrollPos](#setscrollpos)|设置当前的页导航控件的滚动位置。|  
  
## <a name="remarks"></a>备注  
 页导航控件是一个窗口，其中包含另一个是线性的和大于包含窗口，您要滚动到视图所包含的窗口的窗口。 页导航控件显示两个自动及其最远的范围内，消失时滚动所包含的窗口的滚动按钮，否则重新出现。 可以创建水平或垂直滚动的页导航控件。  
  
 例如，如果你的应用程序有一个不是足够宽，以显示其所有项的工具栏，您可以分配的页导航控件的工具栏和用户将能够向下滚动到左侧或右侧，若要访问的所有项工具栏。 Microsoft Internet Explorer 版本 4.0 （commctrl.dll 版本 4.71） 引入了页导航控件。  
  
 `CPagerCtrl`类派生自[CWnd](../../mfc/reference/cwnd-class.md)类。 有关详细信息和的页导航控件的说明，请参阅[页导航控件](/windows/desktop/Controls/pager-controls)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CPagerCtrl`  
  
## <a name="requirements"></a>要求  
 **标头：** afxcmn.h  
  
##  <a name="cpagerctrl"></a>  CPagerCtrl::CPagerCtrl  
 构造 `CPagerCtrl` 对象。  
  
```  
CPagerCtrl();
```  
  
### <a name="remarks"></a>备注  
 使用[CPagerCtrl::Create](#create)或[CPagerCtrl::CreateEx](#createex)方法创建的页导航控件并将其附加到`CPagerCtrl`对象。  
  
##  <a name="create"></a>  CPagerCtrl::Create  
 使用指定的样式创建的页导航控件，并将其附加到当前`CPagerCtrl`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,   
    const RECT& rect,   
    CWnd* pParentWnd,   
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*dwStyle*|按位组合 (OR)[的窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)并[页导航控件样式](/windows/desktop/Controls/pager-control-styles)要应用于该控件。|  
|[in]*rect*|对引用[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)结构，其中包含的位置和大小的工作区坐标中的控件。|  
|[in]*pParentWnd*|一个指向[CWnd](../../mfc/reference/cwnd-class.md)是控件的父窗口的对象。 此参数不能为 NULL。|  
|[in]*nID*|控件的 ID。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 若要创建的页导航控件，声明`CPagerCtrl`变量，然后调用[CPagerCtrl::Create](#create)或[CPagerCtrl::CreateEx](#createex)该变量上的方法。  
  
### <a name="example"></a>示例  
 以下示例创建的页导航控件，然后使用[CPagerCtrl::SetChild](#setchild)方法能够很长的按钮控件相关联的页导航控件。 该示例然后使用[CPagerCtrl::SetButtonSize](#setbuttonsize)方法以将页导航控件的高度设置为 20 像素，并且[CPagerCtrl::SetBorder](#setborder)方法设置为 1 个像素的边框粗细。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="createex"></a>  CPagerCtrl::CreateEx  
 使用指定的扩展样式创建的页导航控件，并将其附加到当前`CPagerCtrl`对象。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,   
    DWORD dwStyle,   
    const RECT& rect,   
    CWnd* pParentWnd,   
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*dwExStyle*|若要应用于控件的扩展样式的按位组合。 有关详细信息，请参阅*dwExStyle*的参数[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa)函数。|  
|[in]*dwStyle*|按位组合 (OR)[的窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)并[页导航控件样式](/windows/desktop/Controls/pager-control-styles)要应用于该控件。|  
|[in]*rect*|对引用[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)结构，其中包含的位置和大小的工作区坐标中的控件。|  
|[in]*pParentWnd*|一个指向[CWnd](../../mfc/reference/cwnd-class.md)是控件的父窗口的对象。 此参数不能为 NULL。|  
|[in]*nID*|控件的 ID。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 若要创建的页导航控件，声明`CPagerCtrl`变量，然后调用[CPagerCtrl::Create](#create)或[CPagerCtrl::CreateEx](#createex)该变量上的方法。  
  
##  <a name="forwardmouse"></a>  CPagerCtrl::ForwardMouse  
 启用或禁用转发[WM_MOUSEMOVE](/windows/desktop/inputdev/wm-mousemove)对包含在当前的页导航控件的窗口消息。  
  
```  
void ForwardMouse(BOOL bForward);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*bForward*|为 true，则正向鼠标消息或 FALSE 以转发鼠标消息。|  
  
### <a name="remarks"></a>备注  
 此方法将发送[PGM_FORWARDMOUSE](/windows/desktop/Controls/pgm-forwardmouse)消息，Windows SDK 中所述。  
  
##  <a name="getborder"></a>  CPagerCtrl::GetBorder  
 检索当前的页导航控件的边框大小。  
  
```  
int GetBorder() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前的边框大小，以像素度量。  
  
### <a name="remarks"></a>备注  
 此方法将发送[PGM_GETBORDER](/windows/desktop/Controls/pgm-getborder)消息，Windows SDK 中所述。  
  
### <a name="example"></a>示例  
 下面的示例使用[CPagerCtrl::GetBorder](#getborder)方法来检索页导航控件的边框的粗细。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]  
  
##  <a name="getbkcolor"></a>  CPagerCtrl::GetBkColor  
 检索当前的页导航控件的背景色。  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个[COLORREF](/windows/desktop/gdi/colorref)值，该值包含页导航控件的当前背景色。  
  
### <a name="remarks"></a>备注  
 此方法将发送[PGM_GETBKCOLOR](/windows/desktop/Controls/pgm-getbkcolor)消息，Windows SDK 中所述。  
  
### <a name="example"></a>示例  
 下面的示例使用[CPagerCtrl::SetBkColor](#setbkcolor)方法以设置页导航控件的背景色为红色，并[CPagerCtrl::GetBkColor](#getbkcolor)方法来确认已进行了更改。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]  
  
##  <a name="getbuttonsize"></a>  CPagerCtrl::GetButtonSize  
 检索当前的页导航控件按钮大小。  
  
```  
int GetButtonSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前的按钮大小，以像素度量。  
  
### <a name="remarks"></a>备注  
 此方法将发送[PGM_GETBUTTONSIZE](/windows/desktop/Controls/pgm-getbuttonsize)消息，Windows SDK 中所述。  
  
 如果页导航控件具有 PGS_HORZ 样式，该按钮的大小确定页导航按钮的宽度和如果页导航控件具有 PGS_VERT 样式，该按钮的大小确定页导航按钮的高度。 有关详细信息，请参阅[页导航控件样式](/windows/desktop/Controls/pager-control-styles)。  
  
##  <a name="getbuttonstate"></a>  CPagerCtrl::GetButtonState  
 检索当前的页导航控件中的指定的滚动按钮的状态。  
  
```  
DWORD GetButtonState(int iButton) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*iButton*|指示要检索其状态的按钮。 如果页导航控件样式 PGS_HORZ，为右侧的按钮的左键和 PGB_BOTTOMORRIGHT 指定 PGB_TOPORLEFT。 如果页导航控件样式，PGS_VERT 指定 PGB_TOPORLEFT 顶部按钮和 PGB_BOTTOMORRIGHT 底部按钮。 有关详细信息，请参阅[页导航控件样式](/windows/desktop/Controls/pager-control-styles)。|  
  
### <a name="return-value"></a>返回值  
 指定的按钮的状态*iButton*参数。 状态为 PGF_INVISIBLE、 PGF_NORMAL、 PGF_GRAYED、 PGF_DEPRESSED 或 PGF_HOT。 有关详细信息，请参阅的返回值部分[PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate)消息。  
  
### <a name="remarks"></a>备注  
 此方法将发送[PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate)消息，Windows SDK 中所述。  
  
##  <a name="getdroptarget"></a>  CPagerCtrl::GetDropTarget  
 检索[IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget)当前的页导航控件的接口。  
  
```  
IDropTarget* GetDropTarget() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个指向`IDropTarget`当前的页导航控件的接口。  
  
### <a name="remarks"></a>备注  
 `IDropTarget` 是一个接口到实现应用程序中支持拖放操作。  
  
 此方法将发送[PGM_GETDROPTARGET](/windows/desktop/Controls/pgm-getdroptarget)消息，Windows SDK 中所述。 此方法的调用方负责调用`Release`的成员[IDropTarget](/windows/desktop/api/oleidl/nn-oleidl-idroptarget)时不再需要该接口的接口。  
  
##  <a name="getscrollpos"></a>  CPagerCtrl::GetScrollPos  
 检索当前的页导航控件的滚动位置。  
  
```  
int GetScrollPos() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前的滚动位置，以像素度量。  
  
### <a name="remarks"></a>备注  
 此方法将发送[PGM_GETPOS](/windows/desktop/Controls/pgm-getpos)消息，Windows SDK 中所述。  
  
### <a name="example"></a>示例  
 下面的示例使用[CPagerCtrl::GetScrollPos](#getscrollpos)方法来检索当前的页导航控件的滚动位置。 如果页导航控件没有浏览为零，最左侧的位置，该示例使用[CPagerCtrl::SetScrollPos](#setscrollpos)方法将滚动位置设置为零。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]  
  
##  <a name="isbuttondepressed"></a>  CPagerCtrl::IsButtonDepressed  
 指示是否当前的页导航控件的指定的滚动按钮处于按下状态。  
  
```  
BOOL IsButtonDepressed(int iButton) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*iButton*|指示要检索其状态的按钮。 如果页导航控件样式 PGS_HORZ，为右侧的按钮的左键和 PGB_BOTTOMORRIGHT 指定 PGB_TOPORLEFT。 如果页导航控件样式，PGS_VERT 指定 PGB_TOPORLEFT 顶部按钮和 PGB_BOTTOMORRIGHT 底部按钮。 有关详细信息，请参阅[页导航控件样式](/windows/desktop/Controls/pager-control-styles)。|  
  
### <a name="return-value"></a>返回值  
 如果指定的按钮处于按下状态，则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 此方法将发送[PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate)消息，Windows SDK 中所述。 然后，它测试是否返回的状态为 PGF_DEPRESSED。 有关详细信息，请参阅的返回值部分[PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate)消息。  
  
##  <a name="isbuttongrayed"></a>  CPagerCtrl::IsButtonGrayed  
 指示当前的页导航控件的指定的滚动按钮是否处于灰显状态。  
  
```  
BOOL IsButtonGrayed(int iButton) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*iButton*|指示要检索其状态的按钮。 如果页导航控件样式 PGS_HORZ，为右侧的按钮的左键和 PGB_BOTTOMORRIGHT 指定 PGB_TOPORLEFT。 如果页导航控件样式，PGS_VERT 指定 PGB_TOPORLEFT 顶部按钮和 PGB_BOTTOMORRIGHT 底部按钮。 有关详细信息，请参阅[页导航控件样式](/windows/desktop/Controls/pager-control-styles)。|  
  
### <a name="return-value"></a>返回值  
 如果指定的按钮灰显状态，则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 此方法将发送[PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate)消息，Windows SDK 中所述。 然后，它测试是否返回的状态为 PGF_GRAYED。 有关详细信息，请参阅的返回值部分[PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate)消息。  
  
##  <a name="isbuttonhot"></a>  CPagerCtrl::IsButtonHot  
 指示当前的页导航控件的指定的滚动按钮是否处于热状态。  
  
```  
BOOL IsButtonHot(int iButton) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*iButton*|指示要检索其状态的按钮。 如果页导航控件样式 PGS_HORZ，为右侧的按钮的左键和 PGB_BOTTOMORRIGHT 指定 PGB_TOPORLEFT。 如果页导航控件样式，PGS_VERT 指定 PGB_TOPORLEFT 顶部按钮和 PGB_BOTTOMORRIGHT 底部按钮。 有关详细信息，请参阅[页导航控件样式](/windows/desktop/Controls/pager-control-styles)。|  
  
### <a name="return-value"></a>返回值  
 如果指定的按钮处于热状态，则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 此方法将发送[PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate)消息，Windows SDK 中所述。 然后，它测试是否返回的状态为 PGF_HOT。 有关详细信息，请参阅的返回值部分[PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate)消息。  
  
##  <a name="isbuttoninvisible"></a>  CPagerCtrl::IsButtonInvisible  
 指示当前的页导航控件的指定的滚动按钮是否处于不可见状态。  
  
```  
BOOL IsButtonInvisible(int iButton) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*iButton*|指示要检索其状态的按钮。 如果页导航控件样式 PGS_HORZ，为右侧的按钮的左键和 PGB_BOTTOMORRIGHT 指定 PGB_TOPORLEFT。 如果页导航控件样式，PGS_VERT 指定 PGB_TOPORLEFT 顶部按钮和 PGB_BOTTOMORRIGHT 底部按钮。 有关详细信息，请参阅[页导航控件样式](/windows/desktop/Controls/pager-control-styles)。|  
  
### <a name="return-value"></a>返回值  
 如果指定的按钮不可见状态，则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 Windows 会使滚动按钮以特定方向不可见时所包含的窗口滚动到其最远的区，因为单击更多按钮不能将多个所包含窗口放入视图。  
  
 此方法将发送[PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate)消息，Windows SDK 中所述。 然后，它测试是否返回的状态为 PGF_INVISIBLE。 有关详细信息，请参阅的返回值部分[PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate)消息。  
  
### <a name="example"></a>示例  
 下面的示例使用[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)方法，以确定是否页导航控件左边缘和右滚动按钮是可见的。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]  
  
##  <a name="isbuttonnormal"></a>  CPagerCtrl::IsButtonNormal  
 指示当前的页导航控件的指定的滚动按钮是否处于正常状态。  
  
```  
BOOL IsButtonNormal(int iButton) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*iButton*|指示要检索其状态的按钮。 如果页导航控件样式 PGS_HORZ，为右侧的按钮的左键和 PGB_BOTTOMORRIGHT 指定 PGB_TOPORLEFT。 如果页导航控件样式，PGS_VERT 指定 PGB_TOPORLEFT 顶部按钮和 PGB_BOTTOMORRIGHT 底部按钮。 有关详细信息，请参阅[页导航控件样式](/windows/desktop/Controls/pager-control-styles)。|  
  
### <a name="return-value"></a>返回值  
 如果指定的按钮处于正常状态，则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 此方法将发送[PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate)消息，Windows SDK 中所述。 然后，它测试是否返回的状态为 PGF_NORMAL。 有关详细信息，请参阅的返回值部分[PGM_GETBUTTONSTATE](/windows/desktop/Controls/pgm-getbuttonstate)消息。  
  
##  <a name="recalcsize"></a>  CPagerCtrl::RecalcSize  
 导致当前的页导航控件，以重新计算包含窗口的大小。  
  
```  
void RecalcSize();
```  
  
### <a name="remarks"></a>备注  
 此方法将发送[PGM_RECALCSIZE](/windows/desktop/Controls/pgm-recalcsize)消息，Windows SDK 中所述。 因此，页导航控件将发送[PGN_CALCSIZE](/windows/desktop/Controls/pgn-calcsize)通知以获取包含窗口的可滚动维数。  
  
### <a name="example"></a>示例  
 下面的示例使用[CPagerCtrl::RecalcSize](#recalcsize)方法来请求当前的页导航控件，重新计算其大小。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]  
  
### <a name="example"></a>示例  
 下面的示例使用[消息反射](../../mfc/tn062-message-reflection-for-windows-controls.md)以便重新计算它自身的大小而不是请求来执行计算的控件的父对话框的页导航控件。 该示例从`MyPagerCtrl`类派生[CPagerCtrl 类](../../mfc/reference/cpagerctrl-class.md)，然后使用消息映射将关联[PGN_CALCSIZE](/windows/desktop/Controls/pgn-calcsize)通知`OnCalcsize`通知处理程序。 在此示例中，通知处理程序将宽度和页导航控件的高度设置为固定值。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]  
  
##  <a name="setbkcolor"></a>  CPagerCtrl::SetBkColor  
 设置当前的页导航控件的背景色。  
  
```  
COLORREF SetBkColor(COLORREF clrBk);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*clrBk*|一个[COLORREF](/windows/desktop/gdi/colorref)值，该值包含新的页导航控件的背景色。|  
  
### <a name="return-value"></a>返回值  
 一个[COLORREF](/windows/desktop/gdi/colorref)值，该值包含页导航控件的上一个背景色。  
  
### <a name="remarks"></a>备注  
 此方法将发送[PGM_SETBKCOLOR](/windows/desktop/Controls/pgm-setbkcolor)消息，Windows SDK 中所述。  
  
### <a name="example"></a>示例  
 下面的示例使用[CPagerCtrl::SetBkColor](#setbkcolor)方法以设置页导航控件的背景色为红色，并[CPagerCtrl::GetBkColor](#getbkcolor)方法来确认已进行了更改。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]  
  
##  <a name="setborder"></a>  CPagerCtrl::SetBorder  
 设置当前的页导航控件的边框大小。  
  
```  
int SetBorder(int iBorder);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*iBorder*|新边框的大小，以像素度量。 如果*iBorder*参数为负，则边框大小设置为零。|  
  
### <a name="return-value"></a>返回值  
 以前的边框大小，以像素度量。  
  
### <a name="remarks"></a>备注  
 此方法将发送[PGM_SETBORDER](/windows/desktop/Controls/pgm-setborder)消息，Windows SDK 中所述。  
  
### <a name="example"></a>示例  
 以下示例创建的页导航控件，然后使用[CPagerCtrl::SetChild](#setchild)方法能够很长的按钮控件相关联的页导航控件。 该示例然后使用[CPagerCtrl::SetButtonSize](#setbuttonsize)方法以将页导航控件的高度设置为 20 像素，并且[CPagerCtrl::SetBorder](#setborder)方法设置为 1 个像素的边框粗细。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="setbuttonsize"></a>  CPagerCtrl::SetButtonSize  
 设置当前的页导航控件按钮大小。  
  
```  
int SetButtonSize(int iButtonSize);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*iButtonSize*|新按钮的大小，以像素度量。|  
  
### <a name="return-value"></a>返回值  
 上一个按钮大小，以像素度量。  
  
### <a name="remarks"></a>备注  
 此方法将发送[PGM_SETBUTTONSIZE](/windows/desktop/Controls/pgm-setpos)消息，Windows SDK 中所述。  
  
 如果页导航控件具有 PGS_HORZ 样式，该按钮的大小确定页导航按钮的宽度和如果页导航控件具有 PGS_VERT 样式，该按钮的大小确定页导航按钮的高度。 默认按钮大小为四分之三的滚动条的宽度，最小按钮大小为 12 像素。 有关详细信息，请参阅[页导航控件样式](/windows/desktop/Controls/pager-control-styles)。  
  
### <a name="example"></a>示例  
 以下示例创建的页导航控件，然后使用[CPagerCtrl::SetChild](#setchild)方法能够很长的按钮控件相关联的页导航控件。 该示例然后使用[CPagerCtrl::SetButtonSize](#setbuttonsize)方法以将页导航控件的高度设置为 20 像素，并且[CPagerCtrl::SetBorder](#setborder)方法设置为 1 个像素的边框粗细。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="setchild"></a>  CPagerCtrl::SetChild  
 设置当前的页导航控件所包含的窗口。  
  
```  
void SetChild(HWND hwndChild);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*hwndChild*|要包含窗口句柄。|  
  
### <a name="remarks"></a>备注  
 此方法将发送[PGM_SETCHILD](/windows/desktop/Controls/pgm-setchild)消息，Windows SDK 中所述。  
  
 此方法不会更改所包含的窗口; 的父它仅分配到页导航控件中滚动的窗口句柄。 在大多数情况下，包含的窗口将在页导航控件的子窗口。  
  
### <a name="example"></a>示例  
 以下示例创建的页导航控件，然后使用[CPagerCtrl::SetChild](#setchild)方法能够很长的按钮控件相关联的页导航控件。 该示例然后使用[CPagerCtrl::SetButtonSize](#setbuttonsize)方法以将页导航控件的高度设置为 20 像素，并且[CPagerCtrl::SetBorder](#setborder)方法设置为 1 个像素的边框粗细。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="setscrollpos"></a>  CPagerCtrl::SetScrollPos  
 设置当前的页导航控件的滚动位置。  
  
```  
void SetScrollPos(int iPos);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*iPos*|新的滚动位置，以像素度量。|  
  
### <a name="remarks"></a>备注  
 此方法将发送[PGM_SETPOS](/windows/desktop/Controls/pgm-setpos)消息，Windows SDK 中所述。  
  
## <a name="see-also"></a>请参阅  
 [CPagerCtrl 类](../../mfc/reference/cpagerctrl-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [页导航控件](/windows/desktop/Controls/pager-controls)



