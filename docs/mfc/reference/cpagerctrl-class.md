---
title: CPagerCtrl 类
ms.date: 11/04/2016
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
ms.openlocfilehash: b2c4f1ac99735953f4832226b840ced4ea4c509a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376966"
---
# <a name="cpagerctrl-class"></a>CPagerCtrl 类

`CPagerCtrl` 类用于包装 Windows 页导航控件，可以滚动此控件以查看所包含的不适合包含窗口的窗口。

## <a name="syntax"></a>语法

```
class CPagerCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CPagerCtrl：CPagerCtrl](#cpagerctrl)|构造 `CPagerCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CPagerCtrl：：创建](#create)|创建具有指定样式的寻呼器控件并将其附加到当前`CPagerCtrl`对象。|
|[CPagerCtrl：：创建Ex](#createex)|创建具有指定扩展样式的寻呼器控件，并将其附加到当前`CPagerCtrl`对象。|
|[CPagerCtrl：：前进鼠标](#forwardmouse)|启用或禁用将[WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove)消息转发到当前寻呼器控件中包含的窗口。|
|[CPagerCtrl：GetBkColor](#getbkcolor)|检索当前寻呼器控件的背景颜色。|
|[CPagerCtrl：：获取边界](#getborder)|检索当前寻呼机控件的边框大小。|
|[CPagerCtrl：获取按钮大小](#getbuttonsize)|检索当前寻呼机控件的按钮大小。|
|[CPagerCtrl：：获取按钮状态](#getbuttonstate)|检索当前寻呼机控件中指定按钮的状态。|
|[CPagerCtrl：：获取DropTarget](#getdroptarget)|检索当前寻呼机控件的[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)接口。|
|[CPagerCtrl：：获取ScrollPos](#getscrollpos)|检索当前寻呼器控件的滚动位置。|
|[CPagerCtrl：：按压键压沉](#isbuttondepressed)|指示当前寻呼机控件的指定按钮是否处于`pressed`状态。|
|[CPagerCtrl：：按键灰色](#isbuttongrayed)|指示当前寻呼机控件的指定按钮是否处于`grayed`状态。|
|[CPagerCtrl：：是按钮热](#isbuttonhot)|指示当前寻呼机控件的指定按钮是否处于`hot`状态。|
|[CPagerCtrl：：是按钮不可见](#isbuttoninvisible)|指示当前寻呼机控件的指定按钮是否处于`invisible`状态。|
|[CPagerCtrl：：正按钮正常](#isbuttonnormal)|指示当前寻呼机控件的指定按钮是否处于`normal`状态。|
|[CPagerCtrl：recalcsize](#recalcsize)|使当前寻呼机控件重新计算包含的窗口的大小。|
|[CPagerCtrl：setBkColor](#setbkcolor)|设置当前寻呼机控件的背景颜色。|
|[CPagerCtrl：：设置边框](#setborder)|设置当前寻呼机控件的边框大小。|
|[CPagerCtrl：：设置按钮大小](#setbuttonsize)|设置当前寻呼机控件的按钮大小。|
|[CPagerCtrl：：SetChild](#setchild)|设置当前寻呼机控件的包含窗口。|
|[CPagerCtrl：：设置ScrollPos](#setscrollpos)|设置当前寻呼器控件的滚动位置。|

## <a name="remarks"></a>备注

寻呼器控件是一个窗口，其中包含另一个线性窗口，并且大于包含的窗口，并使您能够将包含的窗口滚动到视图中。 寻呼机控件显示两个滚动按钮，当包含的窗口滚动到其最远的范围时，这些按钮会自动消失，否则重新出现。 您可以创建水平或垂直滚动的寻呼器控件。

例如，如果应用程序具有不够宽的工具栏来显示其所有项，则可以将工具栏分配给寻呼机控件，并且用户将能够向左或向右滚动工具栏以访问所有项。 微软 IE 浏览器版本 4.0（commctrl.dll 版本 4.71）引入了寻呼机控件。

类`CPagerCtrl`派生自[CWnd](../../mfc/reference/cwnd-class.md)类。 有关详细信息和寻呼器控件的插图，请参阅[寻呼器控件](/windows/win32/Controls/pager-controls)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPagerCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

## <a name="cpagerctrlcpagerctrl"></a><a name="cpagerctrl"></a>CPagerCtrl：CPagerCtrl

构造 `CPagerCtrl` 对象。

```
CPagerCtrl();
```

### <a name="remarks"></a>备注

使用[CPagerCtrl：：创建](#create)或[CPagerCtrl：createEx 方法](#createex)创建寻呼器控件并将其附加到`CPagerCtrl`对象。

## <a name="cpagerctrlcreate"></a><a name="create"></a>CPagerCtrl：：创建

创建具有指定样式的寻呼器控件并将其附加到当前`CPagerCtrl`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*dwStyle*|[在]要应用于控件[的窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)和[寻呼器控件样式](/windows/win32/Controls/pager-control-styles)的位组合 （OR）。|
|*矩形*|[在]对包含客户端坐标中控件的位置和大小的[RECT](/previous-versions/dd162897\(v=vs.85\))结构的引用。|
|*pparentwnd*|[在]指向[CWnd](../../mfc/reference/cwnd-class.md)对象的指针，该对象是控件的父窗口。 此参数不能为 NULL。|
|*nID*|[在]控件的 ID。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

要创建寻呼器控件，请声明`CPagerCtrl`变量，然后调用[CPagerCtrl：：创建](#create)或[CPagerCtrl：：创建](#createex)该变量上的Ex方法。

### <a name="example"></a>示例

下面的示例创建寻呼器控件，然后使用[CPagerCtrl：setChild](#setchild)方法将很长的按钮控件与寻呼机控件相关联。 然后，该示例使用[CPagerCtrl：：SetButtonSize](#setbuttonsize)方法将寻呼机控件的高度设置为 20 像素，使用[CPagerCtrl：setBorder](#setborder)方法将边框厚度设置为 1 像素。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlcreateex"></a><a name="createex"></a>CPagerCtrl：：创建Ex

创建具有指定扩展样式的寻呼器控件，并将其附加到当前`CPagerCtrl`对象。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*dwExStyle*|[在]要应用于控件的扩展样式的位组合。 有关详细信息，请参阅[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)函数的*dwExStyle*参数。|
|*dwStyle*|[在]要应用于控件[的窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)和[寻呼器控件样式](/windows/win32/Controls/pager-control-styles)的位组合 （OR）。|
|*矩形*|[在]对包含客户端坐标中控件的位置和大小的[RECT](/previous-versions/dd162897\(v=vs.85\))结构的引用。|
|*pparentwnd*|[在]指向[CWnd](../../mfc/reference/cwnd-class.md)对象的指针，该对象是控件的父窗口。 此参数不能为 NULL。|
|*nID*|[在]控件的 ID。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

要创建寻呼器控件，请声明`CPagerCtrl`变量，然后调用[CPagerCtrl：：创建](#create)或[CPagerCtrl：：创建](#createex)该变量上的Ex方法。

## <a name="cpagerctrlforwardmouse"></a><a name="forwardmouse"></a>CPagerCtrl：：前进鼠标

启用或禁用将[WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove)消息转发到当前寻呼器控件中包含的窗口。

```
void ForwardMouse(BOOL bForward);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*b 前进*|[在]TRUE 转发鼠标消息，或 FALSE 不转发鼠标消息。|

### <a name="remarks"></a>备注

此方法发送[PGM_FORWARDMOUSE](/windows/win32/Controls/pgm-forwardmouse)消息，这在 Windows SDK 中介绍。

## <a name="cpagerctrlgetborder"></a><a name="getborder"></a>CPagerCtrl：：获取边界

检索当前寻呼机控件的边框大小。

```
int GetBorder() const;
```

### <a name="return-value"></a>返回值

当前边框大小，以像素为单位。

### <a name="remarks"></a>备注

此方法发送[PGM_GETBORDER](/windows/win32/Controls/pgm-getborder)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

下面的示例使用[CPagerCtrl：：getBorder](#getborder)方法检索寻呼机控件边框的厚度。

[!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]

## <a name="cpagerctrlgetbkcolor"></a><a name="getbkcolor"></a>CPagerCtrl：GetBkColor

检索当前寻呼器控件的背景颜色。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>返回值

包含寻呼机控件的当前背景颜色的[COLORREF](/windows/win32/gdi/colorref)值。

### <a name="remarks"></a>备注

此方法发送[PGM_GETBKCOLOR](/windows/win32/Controls/pgm-getbkcolor)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

下面的示例使用[CPagerCtrl：：SetBkColor](#setbkcolor)方法将寻呼机控件的背景颜色设置为红色，[使用 CPagerCtrl：：getBkColor](#getbkcolor)方法确认已进行更改。

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

## <a name="cpagerctrlgetbuttonsize"></a><a name="getbuttonsize"></a>CPagerCtrl：获取按钮大小

检索当前寻呼机控件的按钮大小。

```
int GetButtonSize() const;
```

### <a name="return-value"></a>返回值

当前按钮大小，以像素为单位。

### <a name="remarks"></a>备注

此方法发送[PGM_GETBUTTONSIZE](/windows/win32/Controls/pgm-getbuttonsize)消息，这在 Windows SDK 中介绍。

如果寻呼机控件具有PGS_HORZ样式，则按钮大小确定寻呼机按钮的宽度，如果寻呼机控件具有PGS_VERT样式，则按钮大小将确定寻呼机按钮的高度。 有关详细信息，请参阅[寻呼器控件样式](/windows/win32/Controls/pager-control-styles)。

## <a name="cpagerctrlgetbuttonstate"></a><a name="getbuttonstate"></a>CPagerCtrl：：获取按钮状态

检索当前寻呼器控件中指定滚动按钮的状态。

```
DWORD GetButtonState(int iButton) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*iButton*|[在]指示检索状态的按钮。 如果寻呼机控制样式PGS_HORZ，请为左键指定PGB_TOPORLEFT，并为右侧按钮指定PGB_BOTTOMORRIGHT。 如果寻呼机控制样式为PGS_VERT，请为顶部按钮指定PGB_TOPORLEFT，并为底部按钮指定PGB_BOTTOMORRIGHT。 有关详细信息，请参阅[寻呼器控件样式](/windows/win32/Controls/pager-control-styles)。|

### <a name="return-value"></a>返回值

*iButton*参数指定的按钮的状态。 状态为PGF_INVISIBLE、PGF_NORMAL、PGF_GRAYED、PGF_DEPRESSED 或PGF_HOT。 有关详细信息，请参阅[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息的返回值部分。

### <a name="remarks"></a>备注

此方法发送[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息，这在 Windows SDK 中介绍。

## <a name="cpagerctrlgetdroptarget"></a><a name="getdroptarget"></a>CPagerCtrl：：获取DropTarget

检索当前寻呼机控件的[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)接口。

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>返回值

指向当前寻呼`IDropTarget`机控件的接口的指针。

### <a name="remarks"></a>备注

`IDropTarget`是您为支持应用程序中的拖放操作而实现的接口之一。

此方法发送[PGM_GETDROPTARGET](/windows/win32/Controls/pgm-getdroptarget)消息，这在 Windows SDK 中介绍。 此方法的调用方负责在不再需要接口时调用`Release` [IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)接口的成员。

## <a name="cpagerctrlgetscrollpos"></a><a name="getscrollpos"></a>CPagerCtrl：：获取ScrollPos

检索当前寻呼器控件的滚动位置。

```
int GetScrollPos() const;
```

### <a name="return-value"></a>返回值

当前滚动位置，以像素为单位测量。

### <a name="remarks"></a>备注

此方法发送[PGM_GETPOS](/windows/win32/Controls/pgm-getpos)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

下面的示例使用[CPagerCtrl：：getScrollPos](#getscrollpos)方法检索寻呼机控件的当前滚动位置。 如果寻呼机控件尚未滚动到零，则该示例使用[CPagerCtrl：：setScrollPos](#setscrollpos)方法将滚动位置设置为零。

[!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]

## <a name="cpagerctrlisbuttondepressed"></a><a name="isbuttondepressed"></a>CPagerCtrl：：按压键压沉

指示当前寻呼机控件的指定滚动按钮是否处于按下状态。

```
BOOL IsButtonDepressed(int iButton) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*iButton*|[在]指示检索状态的按钮。 如果寻呼机控制样式PGS_HORZ，请为左键指定PGB_TOPORLEFT，并为右侧按钮指定PGB_BOTTOMORRIGHT。 如果寻呼机控制样式为PGS_VERT，请为顶部按钮指定PGB_TOPORLEFT，并为底部按钮指定PGB_BOTTOMORRIGHT。 有关详细信息，请参阅[寻呼器控件样式](/windows/win32/Controls/pager-control-styles)。|

### <a name="return-value"></a>返回值

如果指定的按钮处于按下状态，则为 TRUE;如果指定的按钮处于按下状态。<否则，FALSE。

### <a name="remarks"></a>备注

此方法发送[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息，这在 Windows SDK 中介绍。 然后，它将测试返回的状态是否PGF_DEPRESSED。 有关详细信息，请参阅[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息的返回值部分。

## <a name="cpagerctrlisbuttongrayed"></a><a name="isbuttongrayed"></a>CPagerCtrl：：按键灰色

指示当前寻呼机控件的指定滚动按钮是否处于灰色状态。

```
BOOL IsButtonGrayed(int iButton) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*iButton*|[在]指示检索状态的按钮。 如果寻呼机控制样式PGS_HORZ，请为左键指定PGB_TOPORLEFT，并为右侧按钮指定PGB_BOTTOMORRIGHT。 如果寻呼机控制样式为PGS_VERT，请为顶部按钮指定PGB_TOPORLEFT，并为底部按钮指定PGB_BOTTOMORRIGHT。 有关详细信息，请参阅[寻呼器控件样式](/windows/win32/Controls/pager-control-styles)。|

### <a name="return-value"></a>返回值

如果指定的按钮处于灰色状态，则为 TRUE;如果指定的按钮处于灰色状态。<否则，FALSE。

### <a name="remarks"></a>备注

此方法发送[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息，这在 Windows SDK 中介绍。 然后，它将测试返回的状态是否PGF_GRAYED。 有关详细信息，请参阅[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息的返回值部分。

## <a name="cpagerctrlisbuttonhot"></a><a name="isbuttonhot"></a>CPagerCtrl：：是按钮热

指示当前寻呼机控件的指定滚动按钮是否处于热状态。

```
BOOL IsButtonHot(int iButton) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*iButton*|[在]指示检索状态的按钮。 如果寻呼机控制样式PGS_HORZ，请为左键指定PGB_TOPORLEFT，并为右侧按钮指定PGB_BOTTOMORRIGHT。 如果寻呼机控制样式为PGS_VERT，请为顶部按钮指定PGB_TOPORLEFT，并为底部按钮指定PGB_BOTTOMORRIGHT。 有关详细信息，请参阅[寻呼器控件样式](/windows/win32/Controls/pager-control-styles)。|

### <a name="return-value"></a>返回值

如果指定的按钮处于热状态，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法发送[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息，这在 Windows SDK 中介绍。 然后，它将测试返回的状态是否PGF_HOT。 有关详细信息，请参阅[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息的返回值部分。

## <a name="cpagerctrlisbuttoninvisible"></a><a name="isbuttoninvisible"></a>CPagerCtrl：：是按钮不可见

指示当前寻呼机控件的指定滚动按钮是否处于不可见状态。

```
BOOL IsButtonInvisible(int iButton) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*iButton*|[在]指示检索状态的按钮。 如果寻呼机控制样式PGS_HORZ，请为左键指定PGB_TOPORLEFT，并为右侧按钮指定PGB_BOTTOMORRIGHT。 如果寻呼机控制样式为PGS_VERT，请为顶部按钮指定PGB_TOPORLEFT，并为底部按钮指定PGB_BOTTOMORRIGHT。 有关详细信息，请参阅[寻呼器控件样式](/windows/win32/Controls/pager-control-styles)。|

### <a name="return-value"></a>返回值

如果指定的按钮处于不可见状态，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

当包含的窗口滚动到最远的范围时，Windows 使特定方向的滚动按钮不可见，因为进一步单击该按钮无法将更多包含的窗口带入视图。

此方法发送[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息，这在 Windows SDK 中介绍。 然后，它将测试返回的状态是否PGF_INVISIBLE。 有关详细信息，请参阅[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息的返回值部分。

### <a name="example"></a>示例

下面的示例使用[CPagerCtrl：：isButton 不可见](#isbuttoninvisible)方法来确定寻呼机控件的左右滚动按钮是否可见。

[!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]

## <a name="cpagerctrlisbuttonnormal"></a><a name="isbuttonnormal"></a>CPagerCtrl：：正按钮正常

指示当前寻呼机控件的指定滚动按钮是否处于正常状态。

```
BOOL IsButtonNormal(int iButton) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*iButton*|[在]指示检索状态的按钮。 如果寻呼机控制样式PGS_HORZ，请为左键指定PGB_TOPORLEFT，并为右侧按钮指定PGB_BOTTOMORRIGHT。 如果寻呼机控制样式为PGS_VERT，请为顶部按钮指定PGB_TOPORLEFT，并为底部按钮指定PGB_BOTTOMORRIGHT。 有关详细信息，请参阅[寻呼器控件样式](/windows/win32/Controls/pager-control-styles)。|

### <a name="return-value"></a>返回值

如果指定的按钮处于正常状态，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法发送[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息，这在 Windows SDK 中介绍。 然后，它将测试返回的状态是否PGF_NORMAL。 有关详细信息，请参阅[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息的返回值部分。

## <a name="cpagerctrlrecalcsize"></a><a name="recalcsize"></a>CPagerCtrl：recalcsize

使当前寻呼机控件重新计算包含的窗口的大小。

```
void RecalcSize();
```

### <a name="remarks"></a>备注

此方法发送[PGM_RECALCSIZE](/windows/win32/Controls/pgm-recalcsize)消息，这在 Windows SDK 中介绍。 因此，寻呼机控件发送[PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize)通知以获取包含窗口的可滚动维度。

### <a name="example"></a>示例

下面的示例使用[CPagerCtrl：：recalcsize](#recalcsize)方法请求当前寻呼机控件重新计算其大小。

[!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]

### <a name="example"></a>示例

下面的示例使用[消息反射](../../mfc/tn062-message-reflection-for-windows-controls.md)使寻呼机控件能够重新计算其自身大小，而不是要求控件的父对话框执行计算。 该示例从`MyPagerCtrl`[CPagerCtrl 类](../../mfc/reference/cpagerctrl-class.md)派生类，然后使用消息映射将[PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize)通知与`OnCalcsize`通知处理程序相关联。 在此示例中，通知处理程序将寻呼机控件的宽度和高度设置为固定值。

[!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]

## <a name="cpagerctrlsetbkcolor"></a><a name="setbkcolor"></a>CPagerCtrl：setBkColor

设置当前寻呼机控件的背景颜色。

```
COLORREF SetBkColor(COLORREF clrBk);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*clrBk*|[在]包含寻呼机控件的新背景颜色的[COLORREF](/windows/win32/gdi/colorref)值。|

### <a name="return-value"></a>返回值

包含寻呼机控件的上一个背景颜色的[COLORREF](/windows/win32/gdi/colorref)值。

### <a name="remarks"></a>备注

此方法发送[PGM_SETBKCOLOR](/windows/win32/Controls/pgm-setbkcolor)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

下面的示例使用[CPagerCtrl：：SetBkColor](#setbkcolor)方法将寻呼机控件的背景颜色设置为红色，[使用 CPagerCtrl：：getBkColor](#getbkcolor)方法确认已进行更改。

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

## <a name="cpagerctrlsetborder"></a><a name="setborder"></a>CPagerCtrl：：设置边框

设置当前寻呼机控件的边框大小。

```
int SetBorder(int iBorder);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*iBorder*|[在]新的边框大小，以像素为单位。 如果*iBorder*参数为负，则边框大小设置为零。|

### <a name="return-value"></a>返回值

以前的边框大小，以像素为单位。

### <a name="remarks"></a>备注

此方法发送[PGM_SETBORDER](/windows/win32/Controls/pgm-setborder)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

下面的示例创建寻呼器控件，然后使用[CPagerCtrl：setChild](#setchild)方法将很长的按钮控件与寻呼机控件相关联。 然后，该示例使用[CPagerCtrl：：SetButtonSize](#setbuttonsize)方法将寻呼机控件的高度设置为 20 像素，使用[CPagerCtrl：setBorder](#setborder)方法将边框厚度设置为 1 像素。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetbuttonsize"></a><a name="setbuttonsize"></a>CPagerCtrl：：设置按钮大小

设置当前寻呼机控件的按钮大小。

```
int SetButtonSize(int iButtonSize);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*iButtonSize*|[在]新的按钮大小，以像素为单位。|

### <a name="return-value"></a>返回值

以前的按钮大小，以像素为单位。

### <a name="remarks"></a>备注

此方法发送[PGM_SETBUTTONSIZE](/windows/win32/Controls/pgm-setpos)消息，这在 Windows SDK 中介绍。

如果寻呼机控件具有PGS_HORZ样式，则按钮大小确定寻呼机按钮的宽度，如果寻呼机控件具有PGS_VERT样式，则按钮大小将确定寻呼机按钮的高度。 默认按钮大小是滚动条宽度的四分之三，最小按钮大小为 12 像素。 有关详细信息，请参阅[寻呼器控件样式](/windows/win32/Controls/pager-control-styles)。

### <a name="example"></a>示例

下面的示例创建寻呼器控件，然后使用[CPagerCtrl：setChild](#setchild)方法将很长的按钮控件与寻呼机控件相关联。 然后，该示例使用[CPagerCtrl：：SetButtonSize](#setbuttonsize)方法将寻呼机控件的高度设置为 20 像素，使用[CPagerCtrl：setBorder](#setborder)方法将边框厚度设置为 1 像素。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetchild"></a><a name="setchild"></a>CPagerCtrl：：SetChild

设置当前寻呼机控件的包含窗口。

```
void SetChild(HWND hwndChild);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*霍恩德儿童*|[在]句柄要包含的窗口。|

### <a name="remarks"></a>备注

此方法发送[PGM_SETCHILD](/windows/win32/Controls/pgm-setchild)消息，这在 Windows SDK 中介绍。

此方法不更改包含窗口的父级，因此不更改它仅将窗口句柄分配给寻呼机控件进行滚动。 在大多数情况下，包含的窗口将是寻呼机控件的子窗口。

### <a name="example"></a>示例

下面的示例创建寻呼器控件，然后使用[CPagerCtrl：setChild](#setchild)方法将很长的按钮控件与寻呼机控件相关联。 然后，该示例使用[CPagerCtrl：：SetButtonSize](#setbuttonsize)方法将寻呼机控件的高度设置为 20 像素，使用[CPagerCtrl：setBorder](#setborder)方法将边框厚度设置为 1 像素。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

## <a name="cpagerctrlsetscrollpos"></a><a name="setscrollpos"></a>CPagerCtrl：：设置ScrollPos

设置当前寻呼器控件的滚动位置。

```
void SetScrollPos(int iPos);
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*Ipo*|[在]新的滚动位置，以像素为单位。|

### <a name="remarks"></a>备注

此方法发送[PGM_SETPOS](/windows/win32/Controls/pgm-setpos)消息，这在 Windows SDK 中介绍。

## <a name="see-also"></a>另请参阅

[CPagerCtrl 类](../../mfc/reference/cpagerctrl-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[寻呼机控件](/windows/win32/Controls/pager-controls)
