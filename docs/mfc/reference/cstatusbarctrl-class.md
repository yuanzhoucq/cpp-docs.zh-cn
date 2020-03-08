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
ms.openlocfilehash: 8c33aa4d77eeeeca69e50dc63982ff4d7e8bd505
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865530"
---
# <a name="cstatusbarctrl-class"></a>CStatusBarCtrl 类

提供 Windows 公共状态栏控件的功能。

## <a name="syntax"></a>语法

```
class CStatusBarCtrl : public CWnd
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CStatusBarCtrl：： CStatusBarCtrl](#cstatusbarctrl)|构造 `CStatusBarCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CStatusBarCtrl：： Create](#create)|创建一个状态栏控件，并将其附加到 `CStatusBarCtrl` 的对象。|
|[CStatusBarCtrl：： CreateEx](#createex)|使用指定的 Windows 扩展样式创建一个状态栏控件，并将其附加到 `CStatusBarCtrl` 对象上。|
|[CStatusBarCtrl：:D rawItem](#drawitem)|当所有者描述的状态栏控件的可视方位更改时调用。|
|[CStatusBarCtrl：： GetBorders](#getborders)|检索状态栏控件的水平和垂直边框的当前宽度。|
|[CStatusBarCtrl：： GetIcon](#geticon)|检索当前状态栏控件中部分（也称为窗格）的图标。|
|[CStatusBarCtrl：： GetParts](#getparts)|检索状态栏控件中部分的计数。|
|[CStatusBarCtrl：： GetRect](#getrect)|检索状态栏控件中部件的边框。|
|[CStatusBarCtrl：： GetText](#gettext)|检索来自状态栏控件给定部分的文本。|
|[CStatusBarCtrl：： GetTextLength](#gettextlength)|检索状态栏控件给定部分中文本的长度（以字符为字符）。|
|[CStatusBarCtrl：： GetTipText](#gettiptext)|检索状态栏中窗格的工具提示文本。|
|[CStatusBarCtrl：： IsSimple](#issimple)|检查状态窗口控件以确定其是否处于简单模式。|
|[CStatusBarCtrl：： SetBkColor](#setbkcolor)|设置状态栏中的背景色。|
|[CStatusBarCtrl：： SetIcon](#seticon)|设置状态栏中窗格的图标。|
|[CStatusBarCtrl：： SetMinHeight](#setminheight)|设置状态栏控件的绘图区域的最小高度。|
|[CStatusBarCtrl：： SetParts](#setparts)|设置状态栏控件中的部件数以及每个部件的右边缘的坐标。|
|[CStatusBarCtrl：： SetSimple](#setsimple)|指定状态栏控件是显示简单文本还是显示通过先前对 `SetParts`的调用设置的所有控件部件。|
|[CStatusBarCtrl：： SetText](#settext)|设置状态栏控件给定部分中的文本。|
|[CStatusBarCtrl：： SetTipText](#settiptext)|设置状态栏中窗格的工具提示文本。|

## <a name="remarks"></a>备注

"状态栏控件" 是通常显示在父窗口底部的水平窗口，应用程序可在其中显示各种类型的状态信息。 状态栏控件可以分为多个部分，以显示多种类型的信息。

此控件（因此 `CStatusBarCtrl` 类）仅适用于在 Windows 95/98 和 Windows NT 版本3.51 及更高版本下运行的程序。

有关使用 `CStatusBarCtrl`的详细信息，请参阅[控件](../../mfc/controls-mfc.md)和[使用 CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatusBarCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

##  <a name="create"></a>CStatusBarCtrl：： Create

创建一个状态栏控件，并将其附加到 `CStatusBarCtrl` 的对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定状态栏控件的样式。 应用 Windows SDK 中[常见控件样式](/windows/win32/Controls/common-control-styles)中列出的任何状态栏控件样式组合。 此参数必须包括 WS_CHILD 样式。 它还应包括 WS_VISIBLE 样式。

*rect*<br/>
指定状态栏控件的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/previous-versions/dd162897\(v=vs.85\))结构。

*pParentWnd*<br/>
指定状态栏控件的父窗口，通常为 `CDialog`。 值不得为 NULL。

*nID*<br/>
指定状态栏控件的 ID。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

可以通过两个步骤构造 `CStatusBarCtrl`。 首先，调用构造函数，然后调用 `Create`，这将创建状态栏控件，并将其附加到 `CStatusBarCtrl` 对象。

状态窗口的默认位置沿父窗口的底部，但您可以指定 CCS_TOP 样式，使其显示在父窗口的工作区顶部。 可以指定 SBARS_SIZEGRIP 样式，以在状态窗口的右端包含大小调整手柄。 不建议结合使用 CCS_TOP 和 SBARS_SIZEGRIP 样式，因为即使系统在状态窗口中进行绘制，生成的大小调整手柄也不起作用。

若要创建具有扩展窗口样式的状态栏，请调用[CStatusBarCtrl：： CreateEx](#createex)而不是 `Create`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatusBarCtrl#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]

##  <a name="createex"></a>CStatusBarCtrl：： CreateEx

创建一个控件（子窗口）并将其与 `CStatusBarCtrl` 对象相关联。

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
指定正在创建的控件的扩展样式。 有关扩展 Windows 样式的列表，请参阅 Windows SDK 中[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*参数。

*dwStyle*<br/>
指定状态栏控件的样式。 应用 Windows SDK 中[常见控件样式](/windows/win32/Controls/common-control-styles)中列出的任何状态栏控件样式组合。 此参数必须包括 WS_CHILD 样式。 它还应包括 WS_VISIBLE 样式。

*rect*<br/>
对[矩形](/previous-versions/dd162897\(v=vs.85\))结构的引用，该结构描述要创建的窗口的大小和位置（以*pParentWnd*的工作区坐标表示）。

*pParentWnd*<br/>
指向作为控件的父级的窗口的指针。

*nID*<br/>
控件的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

使用 `CreateEx` 而不是[Create](#create)来应用扩展的 windows 样式，该样式由 Windows 扩展样式指定的前言**WS_EX_** 开头。

##  <a name="cstatusbarctrl"></a>CStatusBarCtrl：： CStatusBarCtrl

构造 `CStatusBarCtrl` 对象。

```
CStatusBarCtrl();
```

##  <a name="drawitem"></a>CStatusBarCtrl：:D rawItem

当所有者描述的状态栏控件的可视方位发生更改时由框架调用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>参数

*lpDrawItemStruct*<br/>
指向[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)结构的长指针，该指针包含所需绘图类型的相关信息。

### <a name="remarks"></a>备注

`DRAWITEMSTRUCT` 结构的 `itemAction` 成员定义要执行的绘图操作。

默认情况下，此成员函数不执行任何操作。 重写此成员函数以实现 `CStatusBarCtrl` 对象的所有者描述的绘图。

此成员函数终止之前，应用程序应还原为*lpDrawItemStruct*中提供的显示上下文选择的所有图形设备接口（GDI）对象。

##  <a name="getborders"></a>CStatusBarCtrl：： GetBorders

检索状态栏控件的当前宽度和矩形之间的空白宽度。

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

*nHorz*<br/>
对接收水平边框宽度的整数的引用。

*N）*<br/>
对接收垂直边框宽度的整数的引用。

*nSpacing*<br/>
引用一个整数，该整数接收矩形之间的边框宽度。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

这些边框确定控件外边缘与包含文本的控件中的矩形之间的间距。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatusBarCtrl#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]

##  <a name="geticon"></a>CStatusBarCtrl：： GetIcon

检索当前状态栏控件中部分（也称为窗格）的图标。

```
HICON GetIcon(int iPart) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*iPart*|中部分的从零开始的索引，它包含要检索的图标。 如果此参数为-1，则将状态栏视为简单模式状态栏。|

### <a name="return-value"></a>返回值

如果方法成功，则为图标的句柄;否则为 NULL。

### <a name="remarks"></a>备注

此方法发送 Windows SDK 中描述的[SB_GETICON](/windows/win32/Controls/sb-geticon)消息。

状态栏控件由一行文本输出窗格（也称为部件）组成。 有关状态栏的详细信息，请参阅[MFC 中的状态栏实现](../../mfc/status-bar-implementation-in-mfc.md)和[设置 CStatusBarCtrl 对象的模式](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md)。

### <a name="example"></a>示例

下面的代码示例定义了一个用于访问当前状态栏控件的变量 `m_statusBar`。 此变量将在下一个示例中使用。

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]

### <a name="example"></a>示例

下面的代码示例将一个图标复制到当前状态栏控件的两个窗格中。 在代码示例的前面部分中，我们创建了包含三个窗格的状态栏控件，然后将一个图标添加到第一个窗格。 此示例检索第一个窗格中的图标，然后将其添加到第二个和第三个窗格。

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]

##  <a name="getparts"></a>CStatusBarCtrl：： GetParts

检索状态栏控件中部分的计数。

```
int GetParts(
    int nParts,
    int* pParts) const;
```

### <a name="parameters"></a>参数

*nParts*<br/>
要为其检索坐标的部分数。 如果此参数大于控件中的部分数，则消息仅检索现有部分的坐标。

*pParts*<br/>
整数数组的地址，其元素数与*nParts*指定的部分数相同。 数组中的每个元素都接收相应部件右边缘的工作区坐标。 如果元素设置为-1，则该部件的右边缘的位置将扩展到状态栏的右边缘。

### <a name="return-value"></a>返回值

如果成功，则为控件中的部件数; 否则为零。

### <a name="remarks"></a>备注

此成员函数还检索给定数量的部分右边缘的坐标。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatusBarCtrl#3](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]

##  <a name="getrect"></a>CStatusBarCtrl：： GetRect

检索状态栏控件中部件的边框。

```
BOOL GetRect(
    int nPane,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

*nPane*<br/>
要检索其边框的部分的从零开始的索引。

*lpRect*<br/>
接收边框的[RECT](/previous-versions/dd162897\(v=vs.85\))结构的地址。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatusBarCtrl#4](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]

##  <a name="gettext"></a>CStatusBarCtrl：： GetText

检索来自状态栏控件给定部分的文本。

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
接收文本的缓冲区的地址。 此参数为以 null 值结束的字符串。

*nPane*<br/>
要从中检索文本的部分的从零开始的索引。

*pType*<br/>
指向接收类型信息的整数的指针。 类型可以是以下值之一：

- **0**用边框绘制文本，使其显示在状态栏的底部。

- SBT_NOBORDERS 绘制不带边框的文本。

- SBT_POPOUT 使用边框绘制文本，使其显示在状态栏上方。

- SBT_OWNERDRAW 如果文本具有 SBT_OWNERDRAW 绘制类型，则*pType*将接收此消息，并返回与文本关联的32位值，而不是长度和操作类型。

### <a name="return-value"></a>返回值

文本或包含当前文本的[CString](../../atl-mfc-shared/reference/cstringt-class.md)的长度（以字符为字符）。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatusBarCtrl#5](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]

##  <a name="gettextlength"></a>CStatusBarCtrl：： GetTextLength

检索状态栏控件给定部分文本的长度（以字符为字符）。

```
int GetTextLength(
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>参数

*nPane*<br/>
要从中检索文本的部分的从零开始的索引。

*pType*<br/>
指向接收类型信息的整数的指针。 类型可以是以下值之一：

- **0**用边框绘制文本，使其显示在状态栏的底部。

- SBT_NOBORDERS 绘制不带边框的文本。

- SBT_OWNERDRAW 父窗口绘制的文本。

- SBT_POPOUT 使用边框绘制文本，使其显示在状态栏上方。

### <a name="return-value"></a>返回值

文本的长度（以字符为字符）。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatusBarCtrl#6](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]

##  <a name="gettiptext"></a>CStatusBarCtrl：： GetTipText

检索状态栏中窗格的工具提示文本。

```
CString GetTipText(int nPane) const;
```

### <a name="parameters"></a>参数

*nPane*<br/>
用于接收工具提示文本的状态栏窗格的从零开始的索引。

### <a name="return-value"></a>返回值

一个[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，其中包含要在工具提示中使用的文本。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[SB_GETTIPTEXT](/windows/win32/Controls/sb-gettiptext)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatusBarCtrl#7](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]

##  <a name="issimple"></a>CStatusBarCtrl：： IsSimple

检查状态窗口控件以确定其是否处于简单模式。

```
BOOL IsSimple() const;
```

### <a name="return-value"></a>返回值

如果状态窗口控件处于简单模式，则为非零值;否则为零。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[SB_ISSIMPLE](/windows/win32/Controls/sb-issimple)的行为，如 Windows SDK 中所述。

##  <a name="setbkcolor"></a>CStatusBarCtrl：： SetBkColor

设置状态栏中的背景色。

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>参数

*回车*<br/>
指定新背景色的 COLORREF 值。 指定 CLR_DEFAULT 值以使状态栏使用其默认背景色。

### <a name="return-value"></a>返回值

一个[COLORREF](/windows/win32/gdi/colorref)值，该值表示以前的默认背景色。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[SB_SETBKCOLOR](/windows/win32/Controls/sb-setbkcolor)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatusBarCtrl#8](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]

##  <a name="seticon"></a>CStatusBarCtrl：： SetIcon

设置状态栏中窗格的图标。

```
BOOL SetIcon(
    int nPane,
    HICON hIcon);
```

### <a name="parameters"></a>参数

*nPane*<br/>
将接收图标的窗格的从零开始的索引。 如果此参数为-1，则将状态栏视为一个简单的状态栏。

*hIcon*<br/>
要设置的图标的句柄。 如果此值为 NULL，则从该部分中删除该图标。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[SB_SETICON](/windows/win32/Controls/sb-seticon)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

  请参阅[CStatusBarCtrl：： SetBkColor](#setbkcolor)的示例。

##  <a name="setminheight"></a>CStatusBarCtrl：： SetMinHeight

设置状态栏控件的绘图区域的最小高度。

```
void SetMinHeight(int nMin);
```

### <a name="parameters"></a>参数

*nMin*<br/>
控件的最小高度（以像素为单位）。

### <a name="remarks"></a>备注

最小高度是*nMin*与状态栏控件的垂直边框宽度（以像素为单位）的总和。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatusBarCtrl#9](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]

##  <a name="setparts"></a>CStatusBarCtrl：： SetParts

设置状态栏控件中的部件数以及每个部件的右边缘的坐标。

```
BOOL SetParts(
    int nParts,
    int* pWidths);
```

### <a name="parameters"></a>参数

*nParts*<br/>
要设置的部分数。 部分数不能大于255。

*pWidths*<br/>
整数数组的地址，其元素数与*nParts*指定的部分的元素数相同。 数组中的每个元素指定相应部件右边缘的位置（以工作区坐标表示）。 如果元素为-1，则该部件的右边缘的位置将扩展到控件的右边缘。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatusBarCtrl#10](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]

##  <a name="setsimple"></a>CStatusBarCtrl：： SetSimple

指定状态栏控件是显示简单文本还是显示通过之前对[SetParts](#setparts)的调用设置的所有控件部件。

```
BOOL SetSimple(BOOL bSimple = TRUE);
```

### <a name="parameters"></a>参数

*bSimple*<br/>
中显示类型标志。 如果此参数为 TRUE，则控件显示简单文本;如果它为 FALSE，则显示多个部件。

### <a name="return-value"></a>返回值

始终返回 0。

### <a name="remarks"></a>备注

如果你的应用程序将状态栏控件从 "非简单" 更改为 "简单"，反之亦然，系统会立即重绘控件。

##  <a name="settext"></a>CStatusBarCtrl：： SetText

设置状态栏控件给定部分中的文本。

```
BOOL SetText(
    LPCTSTR lpszText,
    int nPane,
    int nType);
```

### <a name="parameters"></a>参数

*lpszText*<br/>
用于指定要设置的文本且以 Null 结尾的字符串的地址。 如果 SBT_OWNERDRAW *n* ，则*lpszText*表示32位数据。

*nPane*<br/>
要设置部件的从零开始的索引。 如果此值为 255，则假定状态栏控件是仅具有一个部件的简单控件。

nType<br/>
绘制操作的类型。 有关可能值的列表，请参阅[SB_SETTEXT 消息](/windows/win32/Controls/sb-settext)。

### <a name="return-value"></a>返回值

如果成功，则不为零，否则为零。

### <a name="remarks"></a>备注

此消息会使控件中已更改的部分无效，导致控件下一次接收到 WM_PAINT 消息时显示新文本。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatusBarCtrl#11](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]

##  <a name="settiptext"></a>CStatusBarCtrl：： SetTipText

设置状态栏中窗格的工具提示文本。

```
void SetTipText(
    int nPane,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>参数

*nPane*<br/>
用于接收工具提示文本的状态栏窗格的从零开始的索引。

*pszTipText*<br/>
指向包含工具提示文本的字符串的指针。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[SB_SETTIPTEXT](/windows/win32/Controls/sb-settiptext)的行为，如 Windows SDK 中所述。

### <a name="example"></a>示例

[!code-cpp[NVC_MFC_CStatusBarCtrl#12](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]

## <a name="see-also"></a>另请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl 类](../../mfc/reference/ctoolbarctrl-class.md)
