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
ms.openlocfilehash: 519a376bdecc488a94eab65973e33d960ca50c8d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503026"
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
|[CPagerCtrl::Create](#create)|创建具有指定样式的页导航控件，并将其附加`CPagerCtrl`到当前对象。|
|[CPagerCtrl::CreateEx](#createex)|创建具有指定扩展样式的页导航控件，并将其附加`CPagerCtrl`到当前对象。|
|[CPagerCtrl::ForwardMouse](#forwardmouse)|启用或禁用将[WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove)消息转发到当前页导航控件中包含的窗口。|
|[CPagerCtrl::GetBkColor](#getbkcolor)|检索当前页导航控件的背景色。|
|[CPagerCtrl::GetBorder](#getborder)|检索当前页导航控件的边框大小。|
|[CPagerCtrl::GetButtonSize](#getbuttonsize)|检索当前页导航控件的按钮大小。|
|[CPagerCtrl::GetButtonState](#getbuttonstate)|检索当前页导航控件中指定按钮的状态。|
|[CPagerCtrl::GetDropTarget](#getdroptarget)|检索当前页导航控件的[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)接口。|
|[CPagerCtrl::GetScrollPos](#getscrollpos)|检索当前页导航控件的滚动位置。|
|[CPagerCtrl::IsButtonDepressed](#isbuttondepressed)|指示当前页导航控件`pressed`的指定按钮是否处于状态。|
|[CPagerCtrl::IsButtonGrayed](#isbuttongrayed)|指示当前页导航控件`grayed`的指定按钮是否处于状态。|
|[CPagerCtrl::IsButtonHot](#isbuttonhot)|指示当前页导航控件`hot`的指定按钮是否处于状态。|
|[CPagerCtrl::IsButtonInvisible](#isbuttoninvisible)|指示当前页导航控件`invisible`的指定按钮是否处于状态。|
|[CPagerCtrl::IsButtonNormal](#isbuttonnormal)|指示当前页导航控件`normal`的指定按钮是否处于状态。|
|[CPagerCtrl::RecalcSize](#recalcsize)|导致当前页导航控件重新计算所包含窗口的大小。|
|[CPagerCtrl::SetBkColor](#setbkcolor)|设置当前页导航控件的背景色。|
|[CPagerCtrl::SetBorder](#setborder)|设置当前页导航控件的边框大小。|
|[CPagerCtrl::SetButtonSize](#setbuttonsize)|设置当前页导航控件的按钮大小。|
|[CPagerCtrl::SetChild](#setchild)|为当前页导航控件设置包含的窗口。|
|[CPagerCtrl::SetScrollPos](#setscrollpos)|设置当前页导航控件的滚动位置。|

## <a name="remarks"></a>备注

页导航控件是一个窗口，其中包含另一个窗口，该窗口是线性的且大于包含窗口的窗口，并使您能够将包含的窗口滚动到视图中。 页导航控件显示两个滚动按钮，当包含的窗口滚动到最远的区时，它们会自动消失，否则将再次出现。 您可以创建一个水平或垂直滚动的页导航控件。

例如，如果您的应用程序所具有的工具栏宽度不足以显示其所有项，则可以将工具栏分配给页导航控件，用户将能够向左或向右滚动工具栏以访问所有项。 Microsoft Internet Explorer 版本4.0 （commctrl 版本4.71）引入了页导航控件。

类从 [CWnd](../../mfc/reference/cwnd-class.md) 类派生`CPagerCtrl`。 有关页导航控件的详细信息和说明，请参阅[页导航控件](/windows/win32/Controls/pager-controls)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPagerCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

##  <a name="cpagerctrl"></a>CPagerCtrl：： CPagerCtrl

构造 `CPagerCtrl` 对象。

```
CPagerCtrl();
```

### <a name="remarks"></a>备注

使用[CPagerCtrl：： create](#create)或[CPagerCtrl：： CreateEx](#createex)方法创建页导航控件，并将`CPagerCtrl`其附加到对象。

##  <a name="create"></a>CPagerCtrl：： Create

创建具有指定样式的页导航控件，并将其附加`CPagerCtrl`到当前对象。

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
|*dwStyle*|中要应用于控件的[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)和[页导航控件样式](/windows/win32/Controls/pager-control-styles)的按位组合（OR）。|
|*rect*|中对[矩形](/previous-versions/dd162897\(v=vs.85\))结构的引用，该结构包含控件在工作区坐标中的位置和大小。|
|*pParentWnd*|中指向[CWnd](../../mfc/reference/cwnd-class.md)对象的指针，该对象是控件的父窗口。 此参数不能为 NULL。|
|*nID*|中控件的 ID。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

若要创建页导航控件，请`CPagerCtrl`声明一个变量，然后在该变量上调用[CPagerCtrl：： create](#create)或[CPagerCtrl：： CreateEx](#createex)方法。

### <a name="example"></a>示例

下面的示例创建一个页导航控件，然后使用[CPagerCtrl：： SetChild](#setchild)方法将一个非常长的按钮控件与页导航控件相关联。 然后，该示例使用[CPagerCtrl：： SetButtonSize](#setbuttonsize)方法将页导航控件的高度设置为20个像素，并使用[CPagerCtrl：： SetBorder](#setborder)方法将 border 宽度设置为1个像素。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="createex"></a>CPagerCtrl：： CreateEx

创建具有指定扩展样式的页导航控件，并将其附加`CPagerCtrl`到当前对象。

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
|*dwExStyle*|中要应用于控件的扩展样式的按位组合。 有关详细信息，请参阅[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)函数的*dwExStyle*参数。|
|*dwStyle*|中要应用于控件的[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)和[页导航控件样式](/windows/win32/Controls/pager-control-styles)的按位组合（OR）。|
|*rect*|中对[矩形](/previous-versions/dd162897\(v=vs.85\))结构的引用，该结构包含控件在工作区坐标中的位置和大小。|
|*pParentWnd*|中指向[CWnd](../../mfc/reference/cwnd-class.md)对象的指针，该对象是控件的父窗口。 此参数不能为 NULL。|
|*nID*|中控件的 ID。|

### <a name="return-value"></a>返回值

如果此方法成功，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

若要创建页导航控件，请`CPagerCtrl`声明一个变量，然后在该变量上调用[CPagerCtrl：： create](#create)或[CPagerCtrl：： CreateEx](#createex)方法。

##  <a name="forwardmouse"></a>CPagerCtrl：： ForwardMouse

启用或禁用将[WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove)消息转发到当前页导航控件中包含的窗口。

```
void ForwardMouse(BOOL bForward);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*bForward*|中若要转发鼠标消息，则为 TRUE; 如果为 FALSE，则不转发鼠标消息。|

### <a name="remarks"></a>备注

此方法发送[PGM_FORWARDMOUSE](/windows/win32/Controls/pgm-forwardmouse)消息，如 Windows SDK 中所述。

##  <a name="getborder"></a>CPagerCtrl：： GetBorder

检索当前页导航控件的边框大小。

```
int GetBorder() const;
```

### <a name="return-value"></a>返回值

当前边框大小（以像素为单位）。

### <a name="remarks"></a>备注

此方法发送[PGM_GETBORDER](/windows/win32/Controls/pgm-getborder)消息，如 Windows SDK 中所述。

### <a name="example"></a>示例

下面的示例使用[CPagerCtrl：： GetBorder](#getborder)方法检索页导航控件边框的粗细。

[!code-cpp[NVC_MFC_CSplitButton_s2#5](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_2.cpp)]

##  <a name="getbkcolor"></a>CPagerCtrl：： GetBkColor

检索当前页导航控件的背景色。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>返回值

一个[COLORREF](/windows/win32/gdi/colorref)值，该值包含页导航控件的当前背景色。

### <a name="remarks"></a>备注

此方法发送[PGM_GETBKCOLOR](/windows/win32/Controls/pgm-getbkcolor)消息，如 Windows SDK 中所述。

### <a name="example"></a>示例

下面的示例使用[CPagerCtrl：： SetBkColor](#setbkcolor)方法将页导航控件的背景色设置为红色，并使用[CPagerCtrl：： GetBkColor](#getbkcolor)方法来确认是否进行了更改。

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

##  <a name="getbuttonsize"></a>CPagerCtrl：： GetButtonSize

检索当前页导航控件的按钮大小。

```
int GetButtonSize() const;
```

### <a name="return-value"></a>返回值

当前按钮大小，以像素为单位进行度量。

### <a name="remarks"></a>备注

此方法发送[PGM_GETBUTTONSIZE](/windows/win32/Controls/pgm-getbuttonsize)消息，如 Windows SDK 中所述。

如果页导航控件具有 PGS_HORZ 样式，则按钮大小将确定页导航按钮的宽度，如果页导航控件具有 PGS_VERT 样式，按钮大小将确定页导航按钮的高度。 有关详细信息，请参阅[页导航控件样式](/windows/win32/Controls/pager-control-styles)。

##  <a name="getbuttonstate"></a>CPagerCtrl：： GetButtonState

检索当前页导航控件中指定滚动按钮的状态。

```
DWORD GetButtonState(int iButton) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*iButton*|中指示要为其检索状态的按钮。 如果页导航控件样式为 PGS_HORZ，则为左按钮指定 PGB_TOPORLEFT，并为右按钮指定 PGB_BOTTOMORRIGHT。 如果页导航控件样式为 PGS_VERT，请为顶部按钮指定 PGB_TOPORLEFT，并为底部按钮指定 PGB_BOTTOMORRIGHT。 有关详细信息，请参阅[页导航控件样式](/windows/win32/Controls/pager-control-styles)。|

### <a name="return-value"></a>返回值

*IButton*参数指定的按钮的状态。 状态为 PGF_INVISIBLE、PGF_NORMAL、PGF_GRAYED、PGF_DEPRESSED 或 PGF_HOT。 有关详细信息，请参阅[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息的返回值部分。

### <a name="remarks"></a>备注

此方法发送[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息，如 Windows SDK 中所述。

##  <a name="getdroptarget"></a>  CPagerCtrl::GetDropTarget

检索当前页导航控件的[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)接口。

```
IDropTarget* GetDropTarget() const;
```

### <a name="return-value"></a>返回值

指向当前页导航`IDropTarget`控件的接口的指针。

### <a name="remarks"></a>备注

`IDropTarget`是为了支持应用程序中的拖放操作而实现的接口之一。

此方法发送[PGM_GETDROPTARGET](/windows/win32/Controls/pgm-getdroptarget)消息，如 Windows SDK 中所述。 此方法的调用方负责在不再需要接口`Release`时调用[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)接口的成员。

##  <a name="getscrollpos"></a>CPagerCtrl：： GetScrollPos

检索当前页导航控件的滚动位置。

```
int GetScrollPos() const;
```

### <a name="return-value"></a>返回值

当前滚动位置（以像素为单位）。

### <a name="remarks"></a>备注

此方法发送[PGM_GETPOS](/windows/win32/Controls/pgm-getpos)消息，如 Windows SDK 中所述。

### <a name="example"></a>示例

下面的示例使用[CPagerCtrl：： GetScrollPos](#getscrollpos)方法检索页导航控件的当前滚动位置。 如果页导航控件尚未滚动到零，则此示例将使用[CPagerCtrl：： SetScrollPos](#setscrollpos)方法将滚动位置设置为零。

[!code-cpp[NVC_MFC_CSplitButton_s2#7](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_4.cpp)]

##  <a name="isbuttondepressed"></a>CPagerCtrl：： IsButtonDepressed

指示当前页导航控件的指定滚动按钮是否处于按下状态。

```
BOOL IsButtonDepressed(int iButton) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*iButton*|中指示要为其检索状态的按钮。 如果页导航控件样式为 PGS_HORZ，则为左按钮指定 PGB_TOPORLEFT，并为右按钮指定 PGB_BOTTOMORRIGHT。 如果页导航控件样式为 PGS_VERT，请为顶部按钮指定 PGB_TOPORLEFT，并为底部按钮指定 PGB_BOTTOMORRIGHT。 有关详细信息，请参阅[页导航控件样式](/windows/win32/Controls/pager-control-styles)。|

### <a name="return-value"></a>返回值

如果指定按钮处于按下状态，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法发送[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息，如 Windows SDK 中所述。 然后测试返回的状态是否为 PGF_DEPRESSED。 有关详细信息，请参阅[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息的返回值部分。

##  <a name="isbuttongrayed"></a>CPagerCtrl：： IsButtonGrayed

指示当前页导航控件的指定滚动按钮是否处于灰色状态。

```
BOOL IsButtonGrayed(int iButton) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*iButton*|中指示要为其检索状态的按钮。 如果页导航控件样式为 PGS_HORZ，则为左按钮指定 PGB_TOPORLEFT，并为右按钮指定 PGB_BOTTOMORRIGHT。 如果页导航控件样式为 PGS_VERT，请为顶部按钮指定 PGB_TOPORLEFT，并为底部按钮指定 PGB_BOTTOMORRIGHT。 有关详细信息，请参阅[页导航控件样式](/windows/win32/Controls/pager-control-styles)。|

### <a name="return-value"></a>返回值

如果指定的按钮处于灰色状态，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法发送[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息，如 Windows SDK 中所述。 然后测试返回的状态是否为 PGF_GRAYED。 有关详细信息，请参阅[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息的返回值部分。

##  <a name="isbuttonhot"></a>CPagerCtrl：： IsButtonHot

指示当前页导航控件的指定滚动按钮是否处于热状态。

```
BOOL IsButtonHot(int iButton) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*iButton*|中指示要为其检索状态的按钮。 如果页导航控件样式为 PGS_HORZ，则为左按钮指定 PGB_TOPORLEFT，并为右按钮指定 PGB_BOTTOMORRIGHT。 如果页导航控件样式为 PGS_VERT，请为顶部按钮指定 PGB_TOPORLEFT，并为底部按钮指定 PGB_BOTTOMORRIGHT。 有关详细信息，请参阅[页导航控件样式](/windows/win32/Controls/pager-control-styles)。|

### <a name="return-value"></a>返回值

如果指定的按钮处于热状态，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法发送[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息，如 Windows SDK 中所述。 然后测试返回的状态是否为 PGF_HOT。 有关详细信息，请参阅[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息的返回值部分。

##  <a name="isbuttoninvisible"></a>CPagerCtrl：： IsButtonInvisible

指示当前页导航控件的指定滚动按钮是否处于不可见状态。

```
BOOL IsButtonInvisible(int iButton) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*iButton*|中指示要为其检索状态的按钮。 如果页导航控件样式为 PGS_HORZ，则为左按钮指定 PGB_TOPORLEFT，并为右按钮指定 PGB_BOTTOMORRIGHT。 如果页导航控件样式为 PGS_VERT，请为顶部按钮指定 PGB_TOPORLEFT，并为底部按钮指定 PGB_BOTTOMORRIGHT。 有关详细信息，请参阅[页导航控件样式](/windows/win32/Controls/pager-control-styles)。|

### <a name="return-value"></a>返回值

如果指定的按钮处于不可见状态，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

当包含的窗口滚动到最远的区时，Windows 使滚动按钮处于不可见的特定方向，因为再次单击此按钮无法将包含的窗口移到视图中。

此方法发送[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息，如 Windows SDK 中所述。 然后测试返回的状态是否为 PGF_INVISIBLE。 有关详细信息，请参阅[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息的返回值部分。

### <a name="example"></a>示例

下面的示例使用[CPagerCtrl：： IsButtonInvisible](#isbuttoninvisible)方法来确定页导航控件的左侧和右侧滚动按钮是否可见。

[!code-cpp[NVC_MFC_CSplitButton_s2#6](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_5.cpp)]

##  <a name="isbuttonnormal"></a>CPagerCtrl：： IsButtonNormal

指示当前页导航控件的指定滚动按钮是否处于正常状态。

```
BOOL IsButtonNormal(int iButton) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*iButton*|中指示要为其检索状态的按钮。 如果页导航控件样式为 PGS_HORZ，则为左按钮指定 PGB_TOPORLEFT，并为右按钮指定 PGB_BOTTOMORRIGHT。 如果页导航控件样式为 PGS_VERT，请为顶部按钮指定 PGB_TOPORLEFT，并为底部按钮指定 PGB_BOTTOMORRIGHT。 有关详细信息，请参阅[页导航控件样式](/windows/win32/Controls/pager-control-styles)。|

### <a name="return-value"></a>返回值

如果指定的按钮处于正常状态，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法发送[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息，如 Windows SDK 中所述。 然后测试返回的状态是否为 PGF_NORMAL。 有关详细信息，请参阅[PGM_GETBUTTONSTATE](/windows/win32/Controls/pgm-getbuttonstate)消息的返回值部分。

##  <a name="recalcsize"></a>  CPagerCtrl::RecalcSize

导致当前页导航控件重新计算所包含窗口的大小。

```
void RecalcSize();
```

### <a name="remarks"></a>备注

此方法发送[PGM_RECALCSIZE](/windows/win32/Controls/pgm-recalcsize)消息，如 Windows SDK 中所述。 因此，寻呼程序控件发送[PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize)通知以获取所包含的窗口的可滚动维度。

### <a name="example"></a>示例

下面的示例使用[CPagerCtrl：： RecalcSize](#recalcsize)方法请求当前页导航控件重新计算其大小。

[!code-cpp[NVC_MFC_CSplitButton_s2#3](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_6.cpp)]

### <a name="example"></a>示例

下面的示例使用[消息反射](../../mfc/tn062-message-reflection-for-windows-controls.md)来使页导航控件重新计算其大小，而不是要求控件的父对话框执行计算。 该示例`MyPagerCtrl`从[CPagerCtrl 类](../../mfc/reference/cpagerctrl-class.md)派生类，然后使用消息映射将[PGN_CALCSIZE](/windows/win32/Controls/pgn-calcsize)通知与`OnCalcsize`通知处理程序相关联。 在此示例中，通知处理程序将页导航控件的宽度和高度设置为固定值。

[!code-cpp[NVC_MFC_CSplitButton_s2#8](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_7.cpp)]

##  <a name="setbkcolor"></a>CPagerCtrl：： SetBkColor

设置当前页导航控件的背景色。

```
COLORREF SetBkColor(COLORREF clrBk);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*clrBk*|中一个[COLORREF](/windows/win32/gdi/colorref)值，该值包含页导航控件的新背景色。|

### <a name="return-value"></a>返回值

一个[COLORREF](/windows/win32/gdi/colorref)值，该值包含页导航控件之前的背景色。

### <a name="remarks"></a>备注

此方法发送[PGM_SETBKCOLOR](/windows/win32/Controls/pgm-setbkcolor)消息，如 Windows SDK 中所述。

### <a name="example"></a>示例

下面的示例使用[CPagerCtrl：： SetBkColor](#setbkcolor)方法将页导航控件的背景色设置为红色，并使用[CPagerCtrl：： GetBkColor](#getbkcolor)方法来确认是否进行了更改。

[!code-cpp[NVC_MFC_CSplitButton_s2#4](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_3.cpp)]

##  <a name="setborder"></a>  CPagerCtrl::SetBorder

设置当前页导航控件的边框大小。

```
int SetBorder(int iBorder);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*iBorder*|中新的边框大小，以像素为单位。 如果*iBorder*参数为负数，则将边框大小设置为零。|

### <a name="return-value"></a>返回值

上一边框大小，以像素为单位进行度量。

### <a name="remarks"></a>备注

此方法发送[PGM_SETBORDER](/windows/win32/Controls/pgm-setborder)消息，如 Windows SDK 中所述。

### <a name="example"></a>示例

下面的示例创建一个页导航控件，然后使用[CPagerCtrl：： SetChild](#setchild)方法将一个非常长的按钮控件与页导航控件相关联。 然后，该示例使用[CPagerCtrl：： SetButtonSize](#setbuttonsize)方法将页导航控件的高度设置为20个像素，并使用[CPagerCtrl：： SetBorder](#setborder)方法将 border 宽度设置为1个像素。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setbuttonsize"></a>CPagerCtrl：： SetButtonSize

设置当前页导航控件的按钮大小。

```
int SetButtonSize(int iButtonSize);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*iButtonSize*|中新的按钮大小，以像素为单位。|

### <a name="return-value"></a>返回值

先前的按钮大小，以像素为单位进行度量。

### <a name="remarks"></a>备注

此方法发送[PGM_SETBUTTONSIZE](/windows/win32/Controls/pgm-setpos)消息，如 Windows SDK 中所述。

如果页导航控件具有 PGS_HORZ 样式，则按钮大小将确定页导航按钮的宽度，如果页导航控件具有 PGS_VERT 样式，按钮大小将确定页导航按钮的高度。 默认按钮大小为滚动条宽度的三四分之三，最小按钮大小为12像素。 有关详细信息，请参阅[页导航控件样式](/windows/win32/Controls/pager-control-styles)。

### <a name="example"></a>示例

下面的示例创建一个页导航控件，然后使用[CPagerCtrl：： SetChild](#setchild)方法将一个非常长的按钮控件与页导航控件相关联。 然后，该示例使用[CPagerCtrl：： SetButtonSize](#setbuttonsize)方法将页导航控件的高度设置为20个像素，并使用[CPagerCtrl：： SetBorder](#setborder)方法将 border 宽度设置为1个像素。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setchild"></a>CPagerCtrl：： SetChild

为当前页导航控件设置包含的窗口。

```
void SetChild(HWND hwndChild);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*hwndChild*|中要包含的窗口的句柄。|

### <a name="remarks"></a>备注

此方法发送[PGM_SETCHILD](/windows/win32/Controls/pgm-setchild)消息，如 Windows SDK 中所述。

此方法不更改所包含窗口的父级;它仅向页导航控件分配一个窗口句柄以便进行滚动。 在大多数情况下，包含的窗口将是页导航控件的子窗口。

### <a name="example"></a>示例

下面的示例创建一个页导航控件，然后使用[CPagerCtrl：： SetChild](#setchild)方法将一个非常长的按钮控件与页导航控件相关联。 然后，该示例使用[CPagerCtrl：： SetButtonSize](#setbuttonsize)方法将页导航控件的高度设置为20个像素，并使用[CPagerCtrl：： SetBorder](#setborder)方法将 border 宽度设置为1个像素。

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/cpagerctrl-class_1.cpp)]

##  <a name="setscrollpos"></a>CPagerCtrl：： SetScrollPos

设置当前页导航控件的滚动位置。

```
void SetScrollPos(int iPos);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*iPos*|中新的滚动位置（以像素为单位）。|

### <a name="remarks"></a>备注

此方法发送[PGM_SETPOS](/windows/win32/Controls/pgm-setpos)消息，如 Windows SDK 中所述。

## <a name="see-also"></a>请参阅

[CPagerCtrl 类](../../mfc/reference/cpagerctrl-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[页导航控件](/windows/win32/Controls/pager-controls)
