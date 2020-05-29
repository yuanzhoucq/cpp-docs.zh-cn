---
title: CStatusBarCtrl 类
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
- AFXCMN/CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::Create
- AFXCMN/CStatusBarCtrl::CreateEx
- AFXCMN/CStatusBarCtrl::DrawItem
- AFXCMN/CStatusBarCtrl::GetBorders
- AFXCMN/CStatusBarCtrl::GetIcon
- AFXCMN/CStatusBarCtrl::GetParts
- AFXCMN/CStatusBarCtrl::GetRect
- AFXCMN/CStatusBarCtrl::GetText
- AFXCMN/CStatusBarCtrl::GetTextLength
- AFXCMN/CStatusBarCtrl::GetTipText
- AFXCMN/CStatusBarCtrl::IsSimple
- AFXCMN/CStatusBarCtrl::SetBkColor
- AFXCMN/CStatusBarCtrl::SetIcon
- AFXCMN/CStatusBarCtrl::SetMinHeight
- AFXCMN/CStatusBarCtrl::SetParts
- AFXCMN/CStatusBarCtrl::SetSimple
- AFXCMN/CStatusBarCtrl::SetText
- AFXCMN/CStatusBarCtrl::SetTipText
helpviewer_keywords:
- CStatusBarCtrl [MFC], CStatusBarCtrl
- CStatusBarCtrl [MFC], Create
- CStatusBarCtrl [MFC], CreateEx
- CStatusBarCtrl [MFC], DrawItem
- CStatusBarCtrl [MFC], GetBorders
- CStatusBarCtrl [MFC], GetIcon
- CStatusBarCtrl [MFC], GetParts
- CStatusBarCtrl [MFC], GetRect
- CStatusBarCtrl [MFC], GetText
- CStatusBarCtrl [MFC], GetTextLength
- CStatusBarCtrl [MFC], GetTipText
- CStatusBarCtrl [MFC], IsSimple
- CStatusBarCtrl [MFC], SetBkColor
- CStatusBarCtrl [MFC], SetIcon
- CStatusBarCtrl [MFC], SetMinHeight
- CStatusBarCtrl [MFC], SetParts
- CStatusBarCtrl [MFC], SetSimple
- CStatusBarCtrl [MFC], SetText
- CStatusBarCtrl [MFC], SetTipText
ms.assetid: 8504ad38-7b91-4746-aede-ac98886eb47b
ms.openlocfilehash: 57d040a7efd87d384e0aaa6275593bc91f38cc86
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753044"
---
# <a name="cstatusbarctrl-class"></a>CStatusBarCtrl 类

提供 Windows 公共状态栏控件的功能。

## <a name="syntax"></a>语法

```
class CStatusBarCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CStatusBarCtrl：CStatusBarCtrl](#cstatusbarctrl)|构造 `CStatusBarCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CStatusBarCtrl：创建](#create)|创建状态栏控件并将其附加到`CStatusBarCtrl`对象。|
|[CStatusBarCtrl：：创建Ex](#createex)|使用指定的 Windows 扩展样式创建状态栏控件，并将其附加到`CStatusBarCtrl`对象。|
|[CStatusBarCtrl：:D原始项目](#drawitem)|当所有者绘制状态栏控件的可视方面发生更改时调用。|
|[CStatusBarctrl：获取Borders](#getborders)|检索状态栏控件的水平和垂直边框的当前宽度。|
|[CStatusBarctrl：：GetIcon](#geticon)|检索当前状态栏控件中部件（也称为窗格）的图标。|
|[CStatusBarctrl：获取部件](#getparts)|检索状态栏控件中的零件计数。|
|[CStatusBarctrl：：获取 Rect](#getrect)|检索状态栏控件中零件的边界矩形。|
|[CStatusBarctrl：获取文本](#gettext)|从状态栏控件的给定部分检索文本。|
|[CStatusBarctrl：获取文本长度](#gettextlength)|从状态栏控件的给定部分检索文本的长度（以字符表示）。|
|[CStatusBarctrl：：获取提示文本](#gettiptext)|检索状态栏中窗格的工具提示文本。|
|[CStatusBarctrl：：简单](#issimple)|检查状态窗口控件以确定它是否处于简单模式。|
|[CStatusBarctrl：SetBkColor](#setbkcolor)|在状态栏中设置背景颜色。|
|[CStatusBarctrl：：SetIcon](#seticon)|设置状态栏中窗格的图标。|
|[CStatusBarctrl：setMinHeight](#setminheight)|设置状态条控件的绘图区域的最小高度。|
|[CStatusBarctrl：：设置部件](#setparts)|设置状态条控件中的零件数和每个零件右边缘的坐标。|
|[CStatusBarctrl：设置简单](#setsimple)|指定状态栏控件是显示简单文本还是显示以前调用`SetParts`设置的所有控件部件。|
|[CStatusBarctrl：：设置文本](#settext)|设置状态栏控件给定部分中的文本。|
|[CStatusBarctrl：：SetTipText](#settiptext)|设置状态栏中窗格的工具提示文本。|

## <a name="remarks"></a>备注

"状态栏控件"是一个水平窗口，通常显示在父窗口的底部，应用程序可以在其中显示各种状态信息。 状态栏控件可以划分为多个部分以显示多种类型的信息。

此控件（因此该`CStatusBarCtrl`类）仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 及更高版本下运行的程序。

有关 使用`CStatusBarCtrl`的详细信息，请参阅[控件](../../mfc/controls-mfc.md)[和使用 CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatusBarCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

## <a name="cstatusbarctrlcreate"></a><a name="create"></a>CStatusBarCtrl：创建

创建状态栏控件并将其附加到`CStatusBarCtrl`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定状态栏控件的样式。 应用 Windows SDK 中["通用控制样式](/windows/win32/Controls/common-control-styles)"中列出的状态栏控件样式的任意组合。 此参数必须包括WS_CHILD样式。 它还应包括WS_VISIBLE样式。

*矩形*<br/>
指定状态栏控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/windows/win32/api/windef/ns-windef-rect)结构。

*pparentwnd*<br/>
指定状态栏控件的父窗口，通常为`CDialog`。 值不得为 NULL。

*nID*<br/>
指定状态栏控件的 ID。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

在两个步骤`CStatusBarCtrl`中构造 一个。 首先调用构造函数，然后调用`Create`，这将创建状态栏控件并将其附加到`CStatusBarCtrl`对象。

状态窗口的默认位置位于父窗口的底部，但您可以指定CCS_TOP样式，使其显示在父窗口的工作区的顶部。 您可以指定SBARS_SIZEGRIP样式，以在状态窗口的右端包括大小调整夹。 不建议组合CCS_TOP和SBARS_SIZEGRIP样式，因为即使系统在状态窗口中绘制了大小调整夹点，也不起作用。

要创建具有扩展窗口样式的状态栏，请调用[CStatusBarCtrl：：createEx](#createex) `Create`而不是 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatusBarCtrl#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]

## <a name="cstatusbarctrlcreateex"></a><a name="createex"></a>CStatusBarCtrl：：创建Ex

创建控件（子窗口），并将其与`CStatusBarCtrl`对象关联。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwExStyle*<br/>
指定要创建的控件的扩展样式。 有关扩展 Windows 样式的列表，请参阅 Windows SDK 中[创建 WindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*参数。

*dwStyle*<br/>
指定状态栏控件的样式。 应用 Windows SDK 中["通用控制样式](/windows/win32/Controls/common-control-styles)"中列出的状态栏控件样式的任意组合。 此参数必须包括WS_CHILD样式。 它还应包括WS_VISIBLE样式。

*矩形*<br/>
对[RECT](/windows/win32/api/windef/ns-windef-rect)结构的引用，描述要创建的窗口的大小和位置，在*pParentWnd*的客户端坐标中。

*pparentwnd*<br/>
指向控件的父窗口的指针。

*nID*<br/>
控件的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用`CreateEx`而不是["创建](#create)"来应用扩展的 Windows 样式，该样式由 Windows 扩展样式前言**WS_EX_** 指定。

## <a name="cstatusbarctrlcstatusbarctrl"></a><a name="cstatusbarctrl"></a>CStatusBarCtrl：CStatusBarCtrl

构造 `CStatusBarCtrl` 对象。

```
CStatusBarCtrl();
```

## <a name="cstatusbarctrldrawitem"></a><a name="drawitem"></a>CStatusBarCtrl：:D原始项目

当所有者绘制状态栏控件的可视方面发生更改时，由框架调用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>参数

*lpDraw 项目已结*<br/>
指向[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)结构的长指针，其中包含有关所需绘图类型的信息。

### <a name="remarks"></a>备注

`DRAWITEMSTRUCT`结构`itemAction`的成员定义要执行的绘图操作。

默认情况下，此成员函数不执行任何操作。 重写此成员函数以实现所有者绘制对象的绘图`CStatusBarCtrl`。

应用程序应还原在此成员函数终止之前为*lpDrawItemStruct*中提供的显示上下文选择的所有图形设备接口 （GDI） 对象。

## <a name="cstatusbarctrlgetborders"></a><a name="getborders"></a>CStatusBarctrl：获取Borders

检索状态栏控件的水平和垂直边框以及矩形之间的空间的当前宽度。

```
BOOL GetBorders(int* pBorders) const;

BOOL GetBorders(
    int& nHorz,
    int& nVert,
    int& nSpacing) const;
```

### <a name="parameters"></a>参数

*pBorders*<br/>
包含三个元素的整数数组的地址。 第一个元素接收水平边框的宽度，第二个元素接收垂直边框的宽度，第三个元素接收矩形之间的边框宽度。

*恩霍兹*<br/>
引用接收水平边框宽度的整数。

*nVert*<br/>
引用接收垂直边框宽度的整数。

*n间距*<br/>
引用接收矩形之间边框宽度的整数。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

这些边框确定控件外边缘与控件中包含文本的矩形之间的间距。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatusBarCtrl#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]

## <a name="cstatusbarctrlgeticon"></a><a name="geticon"></a>CStatusBarctrl：：GetIcon

检索当前状态栏控件中部件（也称为窗格）的图标。

```
HICON GetIcon(int iPart) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*iPart*|[在]包含要检索的图标的零点索引。 如果此参数为 -1，则假定状态栏为简单模式状态栏。|

### <a name="return-value"></a>返回值

如果方法成功，则图标的句柄;否则，NULL。

### <a name="remarks"></a>备注

此方法发送[SB_GETICON](/windows/win32/Controls/sb-geticon)消息，这在 Windows SDK 中介绍。

状态栏控件由一行文本输出窗格组成，这些窗格也称为部件。 有关状态栏的详细信息，请参阅[MFC 中的状态栏实现](../../mfc/status-bar-implementation-in-mfc.md)和[设置 CStatusBarCtrl 对象的模式](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md)。

### <a name="example"></a>示例

以下代码示例定义用于访问当前状态栏`m_statusBar`控件的变量 。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]

### <a name="example"></a>示例

以下代码示例将图标复制到当前状态栏控件的两个窗格中。 在代码示例的早期版本中，我们创建了一个包含三个窗格的状态栏控件，然后将图标添加到第一个窗格中。 本示例从第一个窗格中检索图标，然后将其添加到第二个和第三个窗格中。

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]

## <a name="cstatusbarctrlgetparts"></a><a name="getparts"></a>CStatusBarctrl：获取部件

检索状态栏控件中的零件计数。

```
int GetParts(
    int nParts,
    int* pParts) const;
```

### <a name="parameters"></a>参数

*n部件*<br/>
要为其检索坐标的零件数。 如果此参数大于控件中的零件数，则消息仅检索现有零件的坐标。

*p部件*<br/>
整数数组的地址具有与*nParts*指定的零件数相同的元素数。 数组中的每个元素都接收相应零件右边缘的客户端坐标。 如果元素设置为 - 1，则该零件的右边缘位置将延伸到状态栏的右边缘。

### <a name="return-value"></a>返回值

控件中的零件数（如果成功）或零。

### <a name="remarks"></a>备注

此成员函数还检索给定零件数右边缘的坐标。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatusBarCtrl#3](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]

## <a name="cstatusbarctrlgetrect"></a><a name="getrect"></a>CStatusBarctrl：：获取 Rect

检索状态栏控件中零件的边界矩形。

```
BOOL GetRect(
    int nPane,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

*nPane*<br/>
要检索其边界矩形的零点的零索引。

*lpRect*<br/>
接收边界矩形的[RECT](/windows/win32/api/windef/ns-windef-rect)结构的地址。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatusBarCtrl#4](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]

## <a name="cstatusbarctrlgettext"></a><a name="gettext"></a>CStatusBarctrl：获取文本

从状态栏控件的给定部分检索文本。

```
CString GetText(
    int nPane,
    int* pType = NULL) const;

int GetText(
    LPCTSTR lpszText,
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>参数

*lpszText*<br/>
接收文本的缓冲区的地址。 此参数是一个 null 端接字符串。

*nPane*<br/>
从中检索文本的零索引。

*p类型*<br/>
指向接收类型信息的整数的指针。 类型可以是以下值之一：

- **0**用边框绘制文本以显示低于状态栏的平面。

- SBT_NOBORDERS文本绘制时没有边框。

- SBT_POPOUT使用边框绘制文本以显示高于状态栏的平面。

- SBT_OWNERDRAW如果文本具有SBT_OWNERDRAW绘图类型 *，pType*将收到此消息并返回与文本关联的 32 位值，而不是长度和操作类型。

### <a name="return-value"></a>返回值

包含当前文本的文本或[CString](../../atl-mfc-shared/reference/cstringt-class.md)的长度（以字符表示）。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatusBarCtrl#5](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]

## <a name="cstatusbarctrlgettextlength"></a><a name="gettextlength"></a>CStatusBarctrl：获取文本长度

从状态栏控件的给定部分检索文本的长度（以字符表示）。

```
int GetTextLength(
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>参数

*nPane*<br/>
从中检索文本的零索引。

*p类型*<br/>
指向接收类型信息的整数的指针。 类型可以是以下值之一：

- **0**用边框绘制文本以显示低于状态栏的平面。

- SBT_NOBORDERS文本绘制时没有边框。

- SBT_OWNERDRAW文本由父窗口绘制。

- SBT_POPOUT使用边框绘制文本以显示高于状态栏的平面。

### <a name="return-value"></a>返回值

文本的长度（以字符表示）。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatusBarCtrl#6](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]

## <a name="cstatusbarctrlgettiptext"></a><a name="gettiptext"></a>CStatusBarctrl：：获取提示文本

检索状态栏中窗格的工具提示文本。

```
CString GetTipText(int nPane) const;
```

### <a name="parameters"></a>参数

*nPane*<br/>
用于接收工具提示文本的状态栏窗格的零索引。

### <a name="return-value"></a>返回值

包含要在工具提示中使用的文本的[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象。

### <a name="remarks"></a>备注

此成员函数实现 win32 消息[SB_GETTIPTEXT](/windows/win32/Controls/sb-gettiptext)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatusBarCtrl#7](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]

## <a name="cstatusbarctrlissimple"></a><a name="issimple"></a>CStatusBarctrl：：简单

检查状态窗口控件以确定它是否处于简单模式。

```
BOOL IsSimple() const;
```

### <a name="return-value"></a>返回值

如果状态窗口控件处于简单模式，则非零;否则为零。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[的行为SB_ISSIMPLE](/windows/win32/Controls/sb-issimple)，如 Windows SDK 中所述。

## <a name="cstatusbarctrlsetbkcolor"></a><a name="setbkcolor"></a>CStatusBarctrl：SetBkColor

在状态栏中设置背景颜色。

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>参数

*铬*<br/>
指定新背景颜色的 COLORREF 值。 指定CLR_DEFAULT值，使状态栏使用其默认背景颜色。

### <a name="return-value"></a>返回值

表示上一个默认背景颜色的[COLORREF](/windows/win32/gdi/colorref)值。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[SB_SETBKCOLOR](/windows/win32/Controls/sb-setbkcolor)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatusBarCtrl#8](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]

## <a name="cstatusbarctrlseticon"></a><a name="seticon"></a>CStatusBarctrl：：SetIcon

设置状态栏中窗格的图标。

```
BOOL SetIcon(
    int nPane,
    HICON hIcon);
```

### <a name="parameters"></a>参数

*nPane*<br/>
将接收图标的窗格的零基索引。 如果此参数为 -1，则假定状态栏为简单状态栏。

*hIcon*<br/>
句柄到要设置的图标。 如果此值为 NULL，则图标将从零件中删除。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[SB_SETICON](/windows/win32/Controls/sb-seticon)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

  请参阅[CStatusBarCtrl 的示例：setBkColor](#setbkcolor)。

## <a name="cstatusbarctrlsetminheight"></a><a name="setminheight"></a>CStatusBarctrl：setMinHeight

设置状态条控件的绘图区域的最小高度。

```cpp
void SetMinHeight(int nMin);
```

### <a name="parameters"></a>参数

*nMin*<br/>
控件的最小高度（以像素为单位）。

### <a name="remarks"></a>备注

最小高度是*nMin*和两倍的宽度（以像素为单位）的状态栏控件的垂直边框的总和。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatusBarCtrl#9](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]

## <a name="cstatusbarctrlsetparts"></a><a name="setparts"></a>CStatusBarctrl：：设置部件

设置状态条控件中的零件数和每个零件右边缘的坐标。

```
BOOL SetParts(
    int nParts,
    int* pWidths);
```

### <a name="parameters"></a>参数

*n部件*<br/>
要设置的零件数。 零件数不能大于 255。

*pWidths*<br/>
整数数组的地址具有与*nParts*指定的零件相同的元素数。 数组中的每个元素指定相应零件右边缘的位置（在客户端坐标中）。 如果元素为 - 1，则该零件的右边缘位置将延伸到控件的右边缘。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatusBarCtrl#10](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]

## <a name="cstatusbarctrlsetsimple"></a><a name="setsimple"></a>CStatusBarctrl：设置简单

指定状态栏控件是显示简单文本还是显示以前调用[SetParts](#setparts)设置的所有控件部件。

```
BOOL SetSimple(BOOL bSimple = TRUE);
```

### <a name="parameters"></a>参数

*b 简单*<br/>
[在]显示类型标志。 如果此参数为 TRUE，则控件将显示简单文本;如果此参数为 TRUE，则控件将显示简单文本。如果是 FALSE，则显示多个部件。

### <a name="return-value"></a>返回值

始终返回 0。

### <a name="remarks"></a>备注

如果应用程序将状态栏控件从非简单更改为简单，反之亦然，系统将立即重绘该控件。

## <a name="cstatusbarctrlsettext"></a><a name="settext"></a>CStatusBarctrl：：设置文本

设置状态栏控件给定部分中的文本。

```
BOOL SetText(
    LPCTSTR lpszText,
    int nPane,
    int nType);
```

### <a name="parameters"></a>参数

*lpszText*<br/>
用于指定要设置的文本且以 Null 结尾的字符串的地址。 如果*nType*是SBT_OWNERDRAW，*则 lpszText*表示 32 位数据。

*nPane*<br/>
要设置部件的从零开始的索引。 如果此值为 255，则假定状态栏控件是仅具有一个部件的简单控件。

nType**<br/>
绘制操作的类型。 有关可能值的列表，请参阅[SB_SETTEXT消息](/windows/win32/Controls/sb-settext)。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

该消息使控件部分已更改无效，从而导致在控件下次收到WM_PAINT消息时显示新文本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatusBarCtrl#11](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]

## <a name="cstatusbarctrlsettiptext"></a><a name="settiptext"></a>CStatusBarctrl：：SetTipText

设置状态栏中窗格的工具提示文本。

```cpp
void SetTipText(
    int nPane,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>参数

*nPane*<br/>
用于接收工具提示文本的状态栏窗格的零索引。

*pssTip文本*<br/>
指向包含工具提示文本的字符串的指针。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[SB_SETTIPTEXT](/windows/win32/Controls/sb-settiptext)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatusBarCtrl#12](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]

## <a name="see-also"></a>另请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl 类](../../mfc/reference/ctoolbarctrl-class.md)
