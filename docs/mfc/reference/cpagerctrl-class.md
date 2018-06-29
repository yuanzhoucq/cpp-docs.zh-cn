---
title: CPagerCtrl 类 |Microsoft 文档
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
ms.openlocfilehash: ad0d928f7190d3908c41560c7fb106e3024ebc6e
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079637"
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
|[CPagerCtrl::Create](#create)|创建指定样式的页导航控件，并将其附加到当前`CPagerCtrl`对象。|  
|[CPagerCtrl::CreateEx](#createex)|指定的扩展样式创建的页导航控件，并将其附加到当前`CPagerCtrl`对象。|  
|[CPagerCtrl::ForwardMouse](#forwardmouse)|启用或禁用转发[WM_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616)对包含在当前的页导航控件的窗口消息。|  
|[CPagerCtrl::GetBkColor](#getbkcolor)|检索当前的页导航控件的背景色。|  
|[CPagerCtrl::GetBorder](#getborder)|检索当前的页导航控件的边框大小。|  
|[CPagerCtrl::GetButtonSize](#getbuttonsize)|检索当前的页导航控件的该按钮的大小。|  
|[CPagerCtrl::GetButtonState](#getbuttonstate)|检索当前的页导航控件中的指定按钮的状态。|  
|[CPagerCtrl::GetDropTarget](#getdroptarget)|检索[IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)当前页导航控件接口。|  
|[CPagerCtrl::GetScrollPos](#getscrollpos)|检索当前的页导航控件的滚动位置。|  
|[CPagerCtrl::IsButtonDepressed](#isbuttondepressed)|该值指示当前的页导航控件的指定的按钮是否处于`pressed`状态。|  
|[CPagerCtrl::IsButtonGrayed](#isbuttongrayed)|该值指示当前的页导航控件的指定的按钮是否处于`grayed`状态。|  
|[CPagerCtrl::IsButtonHot](#isbuttonhot)|该值指示当前的页导航控件的指定的按钮是否处于`hot`状态。|  
|[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)|该值指示当前的页导航控件的指定的按钮是否处于`invisible`状态。|  
|[CPagerCtrl::IsButtonNormal](#isbuttonnormal)|该值指示当前的页导航控件的指定的按钮是否处于`normal`状态。|  
|[CPagerCtrl::RecalcSize](#recalcsize)|导致当前的页导航控件，以重新计算包含窗口的大小。|  
|[CPagerCtrl::SetBkColor](#setbkcolor)|设置当前的页导航控件的背景色。|  
|[CPagerCtrl::SetBorder](#setborder)|设置当前的页导航控件的边框大小。|  
|[CPagerCtrl::SetButtonSize](#setbuttonsize)|设置当前的页导航控件的按钮大小。|  
|[CPagerCtrl::SetChild](#setchild)|设置当前的页导航控件包含的窗口。|  
|[CPagerCtrl::SetScrollPos](#setscrollpos)|设置当前的页导航控件的滚动位置。|  
  
## <a name="remarks"></a>备注  
 页导航控件是一个窗口，其中包含另一个是线性的和大于包含的窗口中，并使你能够滚动到视图中包含的窗口的窗口。 页导航控件显示两个其最远的范围内，自动消失时滚动包含的窗口的滚动按钮，并且否则重新出现。 你可以创建水平或垂直滚动的页导航控件。  
  
 例如，如果你的应用程序有一个不是宽度不足以显示其所有项的工具栏，您可以分配的页导航控件的工具栏和用户将能够向下滚动到左侧或右侧，若要访问的所有项工具栏。 Microsoft Internet Explorer 版本 4.0 （commctrl.dll 版本 4.71） 引入了页导航控件。  
  
 `CPagerCtrl`类派生自[CWnd](../../mfc/reference/cwnd-class.md)类。 有关详细信息和举例说明的页导航控件，请参阅[页导航控件](http://msdn.microsoft.com/library/windows/desktop/bb760855)。  
  
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
 创建指定样式的页导航控件，并将其附加到当前`CPagerCtrl`对象。  
  
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
|[in]*dwStyle*|按位组合 (OR)[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)和[页导航控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760859)要应用于控件。|  
|[in]*rect*|对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，其中包含的位置和大小的客户端坐标中的控件。|  
|[in]*pParentWnd*|指向的指针[CWnd](../../mfc/reference/cwnd-class.md)是控件的父窗口的对象。 此参数不能为`NULL`。|  
|[in]*nID*|控件的 ID。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 若要创建的页导航控件，声明`CPagerCtrl`变量，然后调用[CPagerCtrl::Create](#create)或[CPagerCtrl::CreateEx](#createex)该变量上的方法。  
  
### <a name="example"></a>示例  
 下面的示例将创建的页导航控件，然后使用[CPagerCtrl::SetChild](#setchild)方法要很长的按钮控件相关联的页导航控件。 然后该示例使用[CPagerCtrl::SetButtonSize](#setbuttonsize)方法将页导航控件的高度设置为 20 像素，和[CPagerCtrl::SetBorder](#setborder)方法设置为 1 个像素的边框粗细。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="createex"></a>  CPagerCtrl::CreateEx  
 指定的扩展样式创建的页导航控件，并将其附加到当前`CPagerCtrl`对象。  
  
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
|[in]*dwExStyle*|若要应用于控件的扩展样式按位组合。 有关详细信息，请参阅*dwExStyle*参数[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)函数。|  
|[in]*dwStyle*|按位组合 (OR)[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)和[页导航控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760859)要应用于控件。|  
|[in]*rect*|对引用[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)结构，其中包含的位置和大小的客户端坐标中的控件。|  
|[in]*pParentWnd*|指向的指针[CWnd](../../mfc/reference/cwnd-class.md)是控件的父窗口的对象。 此参数不能为`NULL`。|  
|[in]*nID*|控件的 ID。|  
  
### <a name="return-value"></a>返回值  
 如果此方法成功，则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 若要创建的页导航控件，声明`CPagerCtrl`变量，然后调用[CPagerCtrl::Create](#create)或[CPagerCtrl::CreateEx](#createex)该变量上的方法。  
  
##  <a name="forwardmouse"></a>  CPagerCtrl::ForwardMouse  
 启用或禁用转发[WM_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616)对包含在当前的页导航控件的窗口消息。  
  
```  
void ForwardMouse(BOOL bForward);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*bForward*|`true` 若要将鼠标消息转发或`false`不转发鼠标消息。|  
  
### <a name="remarks"></a>备注  
 此方法可发送[PGM_FORWARDMOUSE](http://msdn.microsoft.com/library/windows/desktop/bb760867)消息，Windows SDK 中介绍。  
  
##  <a name="getborder"></a>  CPagerCtrl::GetBorder  
 检索当前的页导航控件的边框大小。  
  
```  
int GetBorder() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前的边框大小，以像素度量。  
  
### <a name="remarks"></a>备注  
 此方法可发送[PGM_GETBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760869)消息，Windows SDK 中介绍。  
  
### <a name="example"></a>示例  
 下面的示例使用[CPagerCtrl::GetBorder](#getborder)方法来检索页导航控件的边框的粗细。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]  
  
##  <a name="getbkcolor"></a>  CPagerCtrl::GetBkColor  
 检索当前的页导航控件的背景色。  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>返回值  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)值，该值包含当前页导航控件的背景色。  
  
### <a name="remarks"></a>备注  
 此方法可发送[PGM_GETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760868)消息，Windows SDK 中介绍。  
  
### <a name="example"></a>示例  
 下面的示例使用[CPagerCtrl::SetBkColor](#setbkcolor)方法以将页导航控件的背景色设置为红色，和[CPagerCtrl::GetBkColor](#getbkcolor)方法确认而进行了更改。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]  
  
##  <a name="getbuttonsize"></a>  CPagerCtrl::GetButtonSize  
 检索当前的页导航控件的该按钮的大小。  
  
```  
int GetButtonSize() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前的按钮大小，以像素度量。  
  
### <a name="remarks"></a>备注  
 此方法可发送[PGM_GETBUTTONSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760870)消息，Windows SDK 中介绍。  
  
 如果页导航控件具有`PGS_HORZ`样式，该按钮的大小确定导航按钮的宽度和页导航控件是否`PGS_VERT`样式，该按钮的大小确定页导航按钮的高度。 有关详细信息，请参阅[页导航控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760859)。  
  
##  <a name="getbuttonstate"></a>  CPagerCtrl::GetButtonState  
 检索当前的页导航控件中的指定的滚动按钮的状态。  
  
```  
DWORD GetButtonState(int iButton) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*iButton*|指示为其检索状态的按钮。 如果页导航控件样式`PGS_HORZ`，指定`PGB_TOPORLEFT`左侧的按钮和`PGB_BOTTOMORRIGHT`的右侧的按钮。 如果页导航控件样式`PGS_VERT`，指定`PGB_TOPORLEFT`顶部的按钮和`PGB_BOTTOMORRIGHT`底部按钮。 有关详细信息，请参阅[页导航控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760859)。|  
  
### <a name="return-value"></a>返回值  
 指定按钮的状态*iButton*参数。 状态可以是`PGF_INVISIBLE`， `PGF_NORMAL`， `PGF_GRAYED`， `PGF_DEPRESSED`，或`PGF_HOT`。 有关详细信息，请参阅的返回值部分[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)消息。  
  
### <a name="remarks"></a>备注  
 此方法可发送[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)消息，Windows SDK 中介绍。  
  
##  <a name="getdroptarget"></a>  CPagerCtrl::GetDropTarget  
 检索[IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)当前页导航控件接口。  
  
```  
IDropTarget* GetDropTarget() const;  
```  
  
### <a name="return-value"></a>返回值  
 指向的指针`IDropTarget`当前页导航控件接口。  
  
### <a name="remarks"></a>备注  
 `IDropTarget` 是一个接口到实现支持应用程序中的拖放操作。  
  
 此方法可发送[PGM_GETDROPTARGET](http://msdn.microsoft.com/library/windows/desktop/bb760872)消息，Windows SDK 中介绍。 此方法的调用方负责调用`Release`的成员[IDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms679679)接口时不再需要接口。  
  
##  <a name="getscrollpos"></a>  CPagerCtrl::GetScrollPos  
 检索当前的页导航控件的滚动位置。  
  
```  
int GetScrollPos() const;  
```  
  
### <a name="return-value"></a>返回值  
 当前的滚动位置，以像素度量。  
  
### <a name="remarks"></a>备注  
 此方法可发送[PGM_GETPOS](http://msdn.microsoft.com/library/windows/desktop/bb760874)消息，Windows SDK 中介绍。  
  
### <a name="example"></a>示例  
 下面的示例使用[CPagerCtrl::GetScrollPos](#getscrollpos)方法来检索当前页导航控件的滚动位置。 如果为零，最左边的位置，不已滚动页导航控件的示例使用[CPagerCtrl::SetScrollPos](#setscrollpos)方法将滚动位置设置为零。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]  
  
##  <a name="isbuttondepressed"></a>  CPagerCtrl::IsButtonDepressed  
 指示是否当前的页导航控件的指定的滚动按钮处于按下状态。  
  
```  
BOOL IsButtonDepressed(int iButton) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*iButton*|指示为其检索状态的按钮。 如果页导航控件样式`PGS_HORZ`，指定`PGB_TOPORLEFT`左侧的按钮和`PGB_BOTTOMORRIGHT`的右侧的按钮。 如果页导航控件样式`PGS_VERT`，指定`PGB_TOPORLEFT`顶部的按钮和`PGB_BOTTOMORRIGHT`底部按钮。 有关详细信息，请参阅[页导航控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760859)。|  
  
### <a name="return-value"></a>返回值  
 `true` 如果指定的按钮处于按下状态;否则为`false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)消息，Windows SDK 中介绍。 然后，它测试是否返回的状态为`PGF_DEPRESSED`。 有关详细信息，请参阅的返回值部分[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)消息。  
  
##  <a name="isbuttongrayed"></a>  CPagerCtrl::IsButtonGrayed  
 指示当前的页导航控件的指定的滚动按钮是否显示为灰色状态。  
  
```  
BOOL IsButtonGrayed(int iButton) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*iButton*|指示为其检索状态的按钮。 如果页导航控件样式`PGS_HORZ`，指定`PGB_TOPORLEFT`左侧的按钮和`PGB_BOTTOMORRIGHT`的右侧的按钮。 如果页导航控件样式`PGS_VERT`，指定`PGB_TOPORLEFT`顶部的按钮和`PGB_BOTTOMORRIGHT`底部按钮。 有关详细信息，请参阅[页导航控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760859)。|  
  
### <a name="return-value"></a>返回值  
 `true` 如果指定的按钮处于灰显状态;否则为`false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)消息，Windows SDK 中介绍。 然后，它测试是否返回的状态为`PGF_GRAYED`。 有关详细信息，请参阅的返回值部分[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)消息。  
  
##  <a name="isbuttonhot"></a>  CPagerCtrl::IsButtonHot  
 指示当前的页导航控件的指定的滚动按钮是否处于热状态。  
  
```  
BOOL IsButtonHot(int iButton) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*iButton*|指示为其检索状态的按钮。 如果页导航控件样式`PGS_HORZ`，指定`PGB_TOPORLEFT`左侧的按钮和`PGB_BOTTOMORRIGHT`的右侧的按钮。 如果页导航控件样式`PGS_VERT`，指定`PGB_TOPORLEFT`顶部的按钮和`PGB_BOTTOMORRIGHT`底部按钮。 有关详细信息，请参阅[页导航控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760859)。|  
  
### <a name="return-value"></a>返回值  
 `true` 如果指定的按钮处于热状态;否则为`false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)消息，Windows SDK 中介绍。 然后，它测试是否返回的状态为`PGF_HOT`。 有关详细信息，请参阅的返回值部分[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)消息。  
  
##  <a name="isbuttoninvisible"></a>  CPagerCtrl::IsButtonInvisible  
 指示当前的页导航控件的指定的滚动按钮是否处于可见状态。  
  
```  
BOOL IsButtonInvisible(int iButton) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*iButton*|指示为其检索状态的按钮。 如果页导航控件样式`PGS_HORZ`，指定`PGB_TOPORLEFT`左侧的按钮和`PGB_BOTTOMORRIGHT`的右侧的按钮。 如果页导航控件样式`PGS_VERT`，指定`PGB_TOPORLEFT`顶部的按钮和`PGB_BOTTOMORRIGHT`底部按钮。 有关详细信息，请参阅[页导航控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760859)。|  
  
### <a name="return-value"></a>返回值  
 `true` 如果指定的按钮处于可见状态;否则为`false`。  
  
### <a name="remarks"></a>备注  
 Windows 使滚动按钮按特定方向不可见时包含的窗口滚动到其最远的范围，因为单击按钮进一步不能将多个包含窗口放入视图。  
  
 此方法可发送[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)消息，Windows SDK 中介绍。 然后，它测试是否返回的状态为`PGF_INVISIBLE`。 有关详细信息，请参阅的返回值部分[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)消息。  
  
### <a name="example"></a>示例  
 下面的示例使用[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)方法来确定是否页导航控件的左和向右滚动按钮都可见。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]  
  
##  <a name="isbuttonnormal"></a>  CPagerCtrl::IsButtonNormal  
 该值指示当前的页导航控件的指定的滚动按钮是否处于正常状态。  
  
```  
BOOL IsButtonNormal(int iButton) const;  
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*iButton*|指示为其检索状态的按钮。 如果页导航控件样式`PGS_HORZ`，指定`PGB_TOPORLEFT`左侧的按钮和`PGB_BOTTOMORRIGHT`的右侧的按钮。 如果页导航控件样式`PGS_VERT`，指定`PGB_TOPORLEFT`顶部的按钮和`PGB_BOTTOMORRIGHT`底部按钮。 有关详细信息，请参阅[页导航控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760859)。|  
  
### <a name="return-value"></a>返回值  
 `true` 如果指定的按钮处于正常状态;否则为`false`。  
  
### <a name="remarks"></a>备注  
 此方法可发送[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)消息，Windows SDK 中介绍。 然后，它测试是否返回的状态为`PGF_NORMAL`。 有关详细信息，请参阅的返回值部分[PGM_GETBUTTONSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760871)消息。  
  
##  <a name="recalcsize"></a>  CPagerCtrl::RecalcSize  
 导致当前的页导航控件，以重新计算包含窗口的大小。  
  
```  
void RecalcSize();
```  
  
### <a name="remarks"></a>备注  
 此方法可发送[PGM_RECALCSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760876)消息，Windows SDK 中介绍。 因此，页导航控件将发送[PGN_CALCSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760864)通知以获取包含窗口的可滚动尺寸。  
  
### <a name="example"></a>示例  
 下面的示例使用[CPagerCtrl::RecalcSize](#recalcsize)方法来请求当前的页导航控件，重新计算其大小。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]  
  
### <a name="example"></a>示例  
 下面的示例使用[消息反射](../../mfc/tn062-message-reflection-for-windows-controls.md)以启用要重新计算其自身的大小而无需控件的父对话框来执行计算的页导航控件。 该示例从`MyPagerCtrl`类[CPagerCtrl 类](../../mfc/reference/cpagerctrl-class.md)，然后使用消息映射将关联[PGN_CALCSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760864)通知`OnCalcsize`通知处理程序。 在此示例中，通知处理程序设置为固定值的宽度和高度的页导航控件。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]  
  
##  <a name="setbkcolor"></a>  CPagerCtrl::SetBkColor  
 设置当前的页导航控件的背景色。  
  
```  
COLORREF SetBkColor(COLORREF clrBk);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*clrBk*|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)包含新的页导航控件的背景色的值。|  
  
### <a name="return-value"></a>返回值  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)包含以前的背景颜色的页导航控件的值。  
  
### <a name="remarks"></a>备注  
 此方法可发送[PGM_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760878)消息，Windows SDK 中介绍。  
  
### <a name="example"></a>示例  
 下面的示例使用[CPagerCtrl::SetBkColor](#setbkcolor)方法以将页导航控件的背景色设置为红色，和[CPagerCtrl::GetBkColor](#getbkcolor)方法确认而进行了更改。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]  
  
##  <a name="setborder"></a>  CPagerCtrl::SetBorder  
 设置当前的页导航控件的边框大小。  
  
```  
int SetBorder(int iBorder);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*iBorder*|新的边框大小，以像素度量。 如果*iBorder*参数是负数，边框大小设置为零。|  
  
### <a name="return-value"></a>返回值  
 以前的边框大小，以像素度量。  
  
### <a name="remarks"></a>备注  
 此方法可发送[PGM_SETBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760880)消息，Windows SDK 中介绍。  
  
### <a name="example"></a>示例  
 下面的示例将创建的页导航控件，然后使用[CPagerCtrl::SetChild](#setchild)方法要很长的按钮控件相关联的页导航控件。 然后该示例使用[CPagerCtrl::SetButtonSize](#setbuttonsize)方法将页导航控件的高度设置为 20 像素，和[CPagerCtrl::SetBorder](#setborder)方法设置为 1 个像素的边框粗细。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="setbuttonsize"></a>  CPagerCtrl::SetButtonSize  
 设置当前的页导航控件的按钮大小。  
  
```  
int SetButtonSize(int iButtonSize);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*iButtonSize*|该新按钮的大小，以像素度量。|  
  
### <a name="return-value"></a>返回值  
 先前按钮的大小，以像素度量。  
  
### <a name="remarks"></a>备注  
 此方法可发送[PGM_SETBUTTONSIZE](http://msdn.microsoft.com/library/windows/desktop/bb760886)消息，Windows SDK 中介绍。  
  
 如果页导航控件具有`PGS_HORZ`样式，该按钮的大小确定导航按钮的宽度和页导航控件是否`PGS_VERT`样式，该按钮的大小确定页导航按钮的高度。 该默认按钮的大小是在滚动条的宽度的四分之三和最小按钮大小为 12 像素。 有关详细信息，请参阅[页导航控件样式](http://msdn.microsoft.com/library/windows/desktop/bb760859)。  
  
### <a name="example"></a>示例  
 下面的示例将创建的页导航控件，然后使用[CPagerCtrl::SetChild](#setchild)方法要很长的按钮控件相关联的页导航控件。 然后该示例使用[CPagerCtrl::SetButtonSize](#setbuttonsize)方法将页导航控件的高度设置为 20 像素，和[CPagerCtrl::SetBorder](#setborder)方法设置为 1 个像素的边框粗细。  
  
 [!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]  
  
##  <a name="setchild"></a>  CPagerCtrl::SetChild  
 设置当前的页导航控件包含的窗口。  
  
```  
void SetChild(HWND hwndChild);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|[in]*hwndChild*|要包含窗口的句柄。|  
  
### <a name="remarks"></a>备注  
 此方法可发送[PGM_SETCHILD](http://msdn.microsoft.com/library/windows/desktop/bb760884)消息，Windows SDK 中介绍。  
  
 此方法不会更改所包含的窗口; 的父它仅分配到的页导航控件的滚动的窗口句柄。 在大多数情况下，包含窗口将页导航控件的子窗口。  
  
### <a name="example"></a>示例  
 下面的示例将创建的页导航控件，然后使用[CPagerCtrl::SetChild](#setchild)方法要很长的按钮控件相关联的页导航控件。 然后该示例使用[CPagerCtrl::SetButtonSize](#setbuttonsize)方法将页导航控件的高度设置为 20 像素，和[CPagerCtrl::SetBorder](#setborder)方法设置为 1 个像素的边框粗细。  
  
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
 此方法可发送[PGM_SETPOS](http://msdn.microsoft.com/library/windows/desktop/bb760886)消息，Windows SDK 中介绍。  
  
## <a name="see-also"></a>请参阅  
 [CPagerCtrl 类](../../mfc/reference/cpagerctrl-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [页导航控件](http://msdn.microsoft.com/library/windows/desktop/bb760855)



