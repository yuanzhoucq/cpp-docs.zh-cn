---
title: CToolTipCtrl Class
ms.date: 11/04/2016
f1_keywords:
- CToolTipCtrl
- AFXCMN/CToolTipCtrl
- AFXCMN/CToolTipCtrl::CToolTipCtrl
- AFXCMN/CToolTipCtrl::Activate
- AFXCMN/CToolTipCtrl::AddTool
- AFXCMN/CToolTipCtrl::AdjustRect
- AFXCMN/CToolTipCtrl::Create
- AFXCMN/CToolTipCtrl::CreateEx
- AFXCMN/CToolTipCtrl::DelTool
- AFXCMN/CToolTipCtrl::GetBubbleSize
- AFXCMN/CToolTipCtrl::GetCurrentTool
- AFXCMN/CToolTipCtrl::GetDelayTime
- AFXCMN/CToolTipCtrl::GetMargin
- AFXCMN/CToolTipCtrl::GetMaxTipWidth
- AFXCMN/CToolTipCtrl::GetText
- AFXCMN/CToolTipCtrl::GetTipBkColor
- AFXCMN/CToolTipCtrl::GetTipTextColor
- AFXCMN/CToolTipCtrl::GetTitle
- AFXCMN/CToolTipCtrl::GetToolCount
- AFXCMN/CToolTipCtrl::GetToolInfo
- AFXCMN/CToolTipCtrl::HitTest
- AFXCMN/CToolTipCtrl::Pop
- AFXCMN/CToolTipCtrl::Popup
- AFXCMN/CToolTipCtrl::RelayEvent
- AFXCMN/CToolTipCtrl::SetDelayTime
- AFXCMN/CToolTipCtrl::SetMargin
- AFXCMN/CToolTipCtrl::SetMaxTipWidth
- AFXCMN/CToolTipCtrl::SetTipBkColor
- AFXCMN/CToolTipCtrl::SetTipTextColor
- AFXCMN/CToolTipCtrl::SetTitle
- AFXCMN/CToolTipCtrl::SetToolInfo
- AFXCMN/CToolTipCtrl::SetToolRect
- AFXCMN/CToolTipCtrl::SetWindowTheme
- AFXCMN/CToolTipCtrl::Update
- AFXCMN/CToolTipCtrl::UpdateTipText
helpviewer_keywords:
- CToolTipCtrl [MFC], CToolTipCtrl
- CToolTipCtrl [MFC], Activate
- CToolTipCtrl [MFC], AddTool
- CToolTipCtrl [MFC], AdjustRect
- CToolTipCtrl [MFC], Create
- CToolTipCtrl [MFC], CreateEx
- CToolTipCtrl [MFC], DelTool
- CToolTipCtrl [MFC], GetBubbleSize
- CToolTipCtrl [MFC], GetCurrentTool
- CToolTipCtrl [MFC], GetDelayTime
- CToolTipCtrl [MFC], GetMargin
- CToolTipCtrl [MFC], GetMaxTipWidth
- CToolTipCtrl [MFC], GetText
- CToolTipCtrl [MFC], GetTipBkColor
- CToolTipCtrl [MFC], GetTipTextColor
- CToolTipCtrl [MFC], GetTitle
- CToolTipCtrl [MFC], GetToolCount
- CToolTipCtrl [MFC], GetToolInfo
- CToolTipCtrl [MFC], HitTest
- CToolTipCtrl [MFC], Pop
- CToolTipCtrl [MFC], Popup
- CToolTipCtrl [MFC], RelayEvent
- CToolTipCtrl [MFC], SetDelayTime
- CToolTipCtrl [MFC], SetMargin
- CToolTipCtrl [MFC], SetMaxTipWidth
- CToolTipCtrl [MFC], SetTipBkColor
- CToolTipCtrl [MFC], SetTipTextColor
- CToolTipCtrl [MFC], SetTitle
- CToolTipCtrl [MFC], SetToolInfo
- CToolTipCtrl [MFC], SetToolRect
- CToolTipCtrl [MFC], SetWindowTheme
- CToolTipCtrl [MFC], Update
- CToolTipCtrl [MFC], UpdateTipText
ms.assetid: 8973f70c-b73a-46c7-908d-758f364b9a97
ms.openlocfilehash: fdf91549fd1b911de3af82bb940b92fe5e220b92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365106"
---
# <a name="ctooltipctrl-class"></a>CToolTipCtrl Class

封装“工具提示控件”功能，此控件是一个小型弹出窗口，显示说明应用程序中工具用途的单行文本。

## <a name="syntax"></a>语法

```
class CToolTipCtrl : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CToolTipctrl：：CToolTipCtrl](#ctooltipctrl)|构造 `CToolTipCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CToolTipCtrl：：激活](#activate)|激活并停用工具尖端控件。|
|[CToolTipctrl：：添加工具](#addtool)|使用工具尖端控件注册工具。|
|[CToolTipctrl：：调整](#adjustrect)|在工具提示控件的文本显示矩形及其窗口矩形之间进行转换。|
|[CToolTipCtrl：：创建](#create)|创建工具尖端控件并将其附加到`CToolTipCtrl`对象。|
|[CToolTipCtrl：：创建Ex](#createex)|使用指定的 Windows 扩展样式创建工具提示控件并将其附加到`CToolTipCtrl`对象。|
|[CToolTipCtrl：:DelTool](#deltool)|从工具尖端控件中删除工具。|
|[CToolTipctrl：：获取泡泡大小](#getbubblesize)|检索工具提示的大小。|
|[CToolTipCtrl：：获取电流工具](#getcurrenttool)|检索当前工具提示控件显示的工具提示窗口的大小、位置和文本等信息。|
|[CToolTipCtrl：：获取延迟时间](#getdelaytime)|检索当前为工具提示控件设置的初始、弹出窗口和重展持续时间。|
|[CToolTipctrl：：获取保证金](#getmargin)|检索为工具提示窗口设置的上边、左边、下和右边距。|
|[CToolTipctrl：：获取最大提示宽度](#getmaxtipwidth)|检索工具提示窗口的最大宽度。|
|[CToolTipctrl：：获取文本](#gettext)|检索工具尖端控件为工具维护的文本。|
|[CToolTipCtrl：：获取提示BkColor](#gettipbkcolor)|检索工具提示窗口中的背景颜色。|
|[CToolTipCtrl：：获取提示文本颜色](#gettiptextcolor)|检索工具提示窗口中的文本颜色。|
|[CToolTipCtrl：：获取标题](#gettitle)|检索当前工具提示控件的标题。|
|[CToolTipCtrl：：获取工具计数](#gettoolcount)|检索工具尖端控件维护的工具计数。|
|[CToolTipctrl：：获取工具信息](#gettoolinfo)|检索工具尖端控件维护的工具的信息。|
|[CToolTipctrl：hitTest](#hittest)|测试点以确定它是否在给定工具的边界矩形内。 如果是，则检索有关该工具的信息。|
|[CToolTipCtrl：:Pop](#pop)|从视图中删除显示的工具提示窗口。|
|[CToolTipCtrl：:P](#popup)|使当前 ToolTip 控件显示在最后一个鼠标消息的坐标处。|
|[CToolTipCtrl：：接力事件](#relayevent)|将鼠标消息传递到工具提示控件进行处理。|
|[CToolTipctrl：：设置延迟时间](#setdelaytime)|设置工具提示控件的初始、弹出窗口和重展持续时间。|
|[CToolTipctrl：：设置边缘](#setmargin)|设置工具尖端窗口的上边、左边、下和右边距。|
|[CToolTipctrl：：设置最大提示宽度](#setmaxtipwidth)|设置工具尖端窗口的最大宽度。|
|[CToolTipctrl：：SetTipBkColor](#settipbkcolor)|在工具提示窗口中设置背景颜色。|
|[CToolTipctrl：：设置提示文本颜色](#settiptextcolor)|在工具提示窗口中设置文本颜色。|
|[CToolTipctrl：：设置标题](#settitle)|将标准图标和标题字符串添加到工具提示。|
|[CToolTipctrl：：设置工具信息](#settoolinfo)|设置工具提示为工具维护的信息。|
|[CToolTipctrl：：设置工具重新](#settoolrect)|为工具设置新的边界矩形。|
|[CToolTipctrl：：设置窗口主题](#setwindowtheme)|设置工具提示窗口的视觉样式。|
|[CToolTipCtrl：：更新](#update)|强制重绘当前工具。|
|[CToolTipctrl：：更新提示文本](#updatetiptext)|设置工具的工具提示文本。|

## <a name="remarks"></a>备注

"工具"是窗口（如子窗口或控件）或窗口工作区中应用程序定义的矩形区域。 工具提示在大多数时间都是隐藏的，它仅在用户将光标置于工具上并在其上停留约半秒时间时显示。 工具提示显示在光标附近，当用户单击鼠标按钮或将光标移出工具时，工具提示将消失。

`CToolTipCtrl`提供用于控制工具提示的初始时间和持续时间、刀具尖端文本周围的边距宽度、工具提示窗口本身的宽度以及工具提示的背景和文本颜色的功能。 一个工具提示控件可以提供多个工具的信息。

`CToolTipCtrl` 类提供了 Windows 公共工具提示控件的功能。 此控件（因此类`CToolTipCtrl`）仅适用于在 Windows 95/98 和 Windows NT 版本 3.51 及更高版本下运行的程序。

有关启用工具提示的详细信息，请参阅[Windows 中的工具提示，而不是从 CFrameWnd 派生](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)的 。

有关 使用`CToolTipCtrl`的详细信息，请参阅[控件](../../mfc/controls-mfc.md)[和使用 CToolTipCtrl](../../mfc/using-ctooltipctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CToolTipCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

## <a name="ctooltipctrlactivate"></a><a name="activate"></a>CToolTipCtrl：：激活

调用此函数以激活或停用工具尖端控件。

```
void Activate(BOOL bActivate);
```

### <a name="parameters"></a>参数

*b 激活*<br/>
指定是激活还是停用工具尖端控件。

### <a name="remarks"></a>备注

如果 bActivate 为 TRUE，则该控件将激活;如果*bActivate*为 TRUE，则该控件将激活该控件。如果 FALSE，则将其停用。

当工具尖端控件处于活动状态时，当光标位于与控件一起注册的工具上时，将显示工具提示信息;当它处于非活动状态时，即使光标位于工具上，也不会显示工具提示信息。

### <a name="example"></a>示例

  请参阅[CPropertySheet 的示例：getTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)。

## <a name="ctooltipctrladdtool"></a><a name="addtool"></a>CToolTipctrl：：添加工具

使用工具尖端控件注册工具。

```
BOOL AddTool(
    CWnd* pWnd,
    UINT nIDText,
    LPCRECT lpRectTool = NULL,
    UINT_PTR nIDTool = 0);

BOOL AddTool(
    CWnd* pWnd,
    LPCTSTR lpszText = LPSTR_TEXTCALLBACK,
    LPCRECT lpRectTool = NULL,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
指向包含工具的窗口的指针。

*nIDText*<br/>
包含工具文本的字符串资源的 ID。

*lpRectTool*<br/>
指向包含工具边界矩形坐标的[RECT](/previous-versions/dd162897\(v=vs.85\))结构的指针。 坐标相对于*pWnd*标识的窗口的工作区的左上角。

*nIDTool*<br/>
工具的 ID。

*lpszText*<br/>
指向工具的文本的指针。 如果此参数包含值LPSTR_TEXTCALLBACK，TTN_NEEDTEXT通知消息将转到*pwnd*指向的窗口的父级。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

*lpRectTool*和*nIDTool*参数必须都有效，或者如果*lpRectTool*为 NULL，*则 nIDTool*必须为 0。

工具尖端控件可以与多个工具关联。 调用此函数以使用工具尖端控件注册工具，以便在光标位于工具上时显示工具提示中存储的信息。

> [!NOTE]
> 不能使用`AddTool`将工具提示设置为静态控件。

### <a name="example"></a>示例

  请参阅[CPropertySheet 的示例：getTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)。

## <a name="ctooltipctrladjustrect"></a><a name="adjustrect"></a>CToolTipctrl：：调整

在工具提示控件的文本显示矩形及其窗口矩形之间进行转换。

```
BOOL AdjustRect(
    LPRECT lprc,
    BOOL bLarger = TRUE);
```

### <a name="parameters"></a>参数

*利赫浦*<br/>
指向保存工具提示窗口矩形或文本显示矩形的[RECT](/previous-versions/dd162897\(v=vs.85\))结构的指针。

*b 更大*<br/>
如果为 TRUE，*则 lprc*用于指定文本显示矩形，并接收相应的窗口矩形。 如果 FALSE，*则 lprc*用于指定窗口矩形，并且它接收相应的文本显示矩形。

### <a name="return-value"></a>返回值

如果矩形已成功调整，则非零;否则 0。

### <a name="remarks"></a>备注

此成员函数从窗口矩形计算工具提示控件的文本显示矩形，或显示指定文本显示矩形所需的工具尖端窗口矩形。

此成员函数实现 Win32 消息[TTM_ADJUSTRECT](/windows/win32/Controls/ttm-adjustrect)的行为，如 Windows SDK 中所述。

## <a name="ctooltipctrlcreate"></a><a name="create"></a>CToolTipCtrl：：创建

创建工具尖端控件并将其附加到`CToolTipCtrl`对象。

```
virtual BOOL Create(CWnd* pParentWnd, DWORD dwStyle = 0);
```

### <a name="parameters"></a>参数

*pparentwnd*<br/>
指定工具提示控件的父窗口（通常为`CDialog`。 值不得为 NULL。

*dwStyle*<br/>
指定工具尖端控件的样式。 有关详细信息，请参阅**备注**部分。

### <a name="return-value"></a>返回值

如果成功创建对象`CToolTipCtrl`，则非零;否则 0。

### <a name="remarks"></a>备注

在两个步骤`CToolTipCtrl`中构造 一个。 首先，调用构造函数构造`CToolTipCtrl`对象，然后调用`Create`以创建工具提示控件并将其附加到`CToolTipCtrl`对象。

*dwStyle*参数可以是[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)的任意组合。 此外，工具提示控件具有两种特定于类的样式：TTS_ALWAYSTIP和TTS_NOPREFIX。

|样式|含义|
|-----------|-------------|
|TTS_ALWAYSTIP|指定光标位于工具上时将显示工具提示，而不考虑工具提示控件的所有者窗口是活动还是非活动。 如果没有此样式，工具头控件在工具的所有者窗口处于活动状态时显示，但在工具处于非活动状态时不会显示。|
|TTS_NOPREFIX|此样式可防止系统从字符串中剥离安培（&）字符。 如果工具提示控件没有TTS_NOPREFIX样式，系统会自动剥离 ampersand 字符，允许应用程序使用与菜单项和工具提示控件中的文本相同的字符串。|

工具提示控件具有WS_POPUP和WS_EX_TOOLWINDOW窗口样式，而不管在创建控件时是否指定它们。

要创建具有扩展窗口样式的工具提示控件，请致电[CToolTipCtrl：：createEx](#createex)而不是`Create`。

### <a name="example"></a>示例

  请参阅[CPropertySheet 的示例：getTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)。

## <a name="ctooltipctrlcreateex"></a><a name="createex"></a>CToolTipCtrl：：创建Ex

创建控件（子窗口）并将其与`CToolTipCtrl`对象关联。

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwStyle = 0,
    DWORD dwStyleEx = 0);
```

### <a name="parameters"></a>参数

*pparentwnd*<br/>
指向控件的父窗口的指针。

*dwStyle*<br/>
指定工具尖端控件的样式。 有关详细信息，请参阅["创建](#create)**"的备注**部分。

*dwStyleEx*<br/>
指定要创建的控件的扩展样式。 有关扩展 Windows 样式的列表，请参阅 Windows SDK 中[创建 WindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*参数。

### <a name="return-value"></a>返回值

如果成功，则为非零，否则为 0。

### <a name="remarks"></a>备注

使用`CreateEx`而不是`Create`应用扩展的 Windows 样式，由 Windows 扩展样式前言**WS_EX_** 指定。

## <a name="ctooltipctrlctooltipctrl"></a><a name="ctooltipctrl"></a>CToolTipctrl：：CToolTipCtrl

构造 `CToolTipCtrl` 对象。

```
CToolTipCtrl();
```

### <a name="remarks"></a>备注

构造对象后`Create`必须调用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#74](../../mfc/codesnippet/cpp/ctooltipctrl-class_1.h)]

## <a name="ctooltipctrldeltool"></a><a name="deltool"></a>CToolTipCtrl：:DelTool

从工具尖端控件支持的工具集合中删除*pWnd*和*nIDTool*指定的工具。

```
void DelTool(
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
指向包含工具的窗口的指针。

*nIDTool*<br/>
工具的 ID。

## <a name="ctooltipctrlgetbubblesize"></a><a name="getbubblesize"></a>CToolTipctrl：：获取泡泡大小

检索工具提示的大小。

```
CSize GetBubbleSize(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>参数

*lpToolInfo*<br/>
指向工具提示[TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa)结构的指针。

### <a name="return-value"></a>返回值

工具提示的大小。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TTM_GETBUBBLESIZE](/windows/win32/Controls/ttm-getbubblesize)的行为，如 Windows SDK 中所述。

## <a name="ctooltipctrlgetcurrenttool"></a><a name="getcurrenttool"></a>CToolTipCtrl：：获取电流工具

检索当前工具提示控件显示的工具提示窗口的大小、位置和文本等信息。

```
BOOL GetCurrentTool(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*lpToolInfo*|[出]指向接收有关当前工具提示窗口的信息的[TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa)结构的指针。|

### <a name="return-value"></a>返回值

如果信息被成功检索，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

此方法发送[TTM_GETCURRENTTOOL](/windows/win32/Controls/ttm-getcurrenttool)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

以下代码示例检索有关当前工具提示窗口的信息。

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#6](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_2.cpp)]

## <a name="ctooltipctrlgetdelaytime"></a><a name="getdelaytime"></a>CToolTipCtrl：：获取延迟时间

检索当前为工具提示控件设置的初始、弹出窗口和重展持续时间。

```
int GetDelayTime(DWORD dwDuration) const;
```

### <a name="parameters"></a>参数

*dwDuration*<br/>
指定将检索的持续时间值的标志。 此参数可以是以下值之一：

- TTDT_AUTOPOP 如果指针在工具的边界矩形内静止，则检索工具尖端窗口保持可见的时间长度。

- TTDT_INITIAL 检索指针必须在工具边界矩形内保持静止的时间长度，然后出现工具尖端窗口。

- TTDT_RESHOW检索后续工具提示窗口在指针从一个工具移动到另一个工具时显示所需的时间长度。

### <a name="return-value"></a>返回值

指定的延迟时间（以毫秒为单位）

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TTM_GETDELAYTIME](/windows/win32/Controls/ttm-getdelaytime)的行为，如 Windows SDK 中所述。

## <a name="ctooltipctrlgetmargin"></a><a name="getmargin"></a>CToolTipctrl：：获取保证金

检索为工具提示窗口设置的上边、左、下和右边距。

```
void GetMargin(LPRECT lprc) const;
```

### <a name="parameters"></a>参数

*利赫浦*<br/>
将接收保证金`RECT`信息的结构的地址。 [RECT](/previous-versions/dd162897\(v=vs.85\))结构的成员不定义边界矩形。 对于此消息，结构成员的解释如下：

|成员|表示|
|------------|--------------------|
|`top`|顶部边框与工具提示文本顶部之间的距离（以像素为单位）。|
|`left`|提示文本的左边框和左端之间的距离（以像素为单位）。|
|`bottom`|笔尖文本底部边框和底部之间的距离（以像素为单位）。|
|`right`|提示文本的右边框和右端之间的距离（以像素为单位）。|

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TTM_GETMARGIN](/windows/win32/Controls/ttm-getmargin)的行为，如 Windows SDK 中所述。

## <a name="ctooltipctrlgetmaxtipwidth"></a><a name="getmaxtipwidth"></a>CToolTipctrl：：获取最大提示宽度

检索工具提示窗口的最大宽度。

```
int GetMaxTipWidth() const;
```

### <a name="return-value"></a>返回值

工具尖端窗口的最大宽度。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[的行为TTM_GETMAXTIPWIDTH](/windows/win32/Controls/ttm-getmaxtipwidth)，如 Windows SDK 中所述。

## <a name="ctooltipctrlgettext"></a><a name="gettext"></a>CToolTipctrl：：获取文本

检索工具尖端控件为工具维护的文本。

```
void GetText(
    CString& str,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>参数

*Str*<br/>
对接收工具`CString`文本的对象的引用。

*pwnd*<br/>
指向包含工具的窗口的指针。

*nIDTool*<br/>
工具的 ID。

### <a name="remarks"></a>备注

*pWnd*和*nIDTool*参数标识工具。 如果该工具以前已通过以前调用`CToolTipCtrl::AddTool`在 工具尖端控件中注册，则*str*参数引用的对象将分配该工具的文本。

## <a name="ctooltipctrlgettipbkcolor"></a><a name="gettipbkcolor"></a>CToolTipCtrl：：获取提示BkColor

检索工具提示窗口中的背景颜色。

```
COLORREF GetTipBkColor() const;
```

### <a name="return-value"></a>返回值

表示背景颜色的[COLORREF](/windows/win32/gdi/colorref)值。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[的行为TTM_GETTIPBKCOLOR，](/windows/win32/Controls/ttm-gettipbkcolor)如 Windows SDK 中所述。

## <a name="ctooltipctrlgettiptextcolor"></a><a name="gettiptextcolor"></a>CToolTipCtrl：：获取提示文本颜色

检索工具提示窗口中的文本颜色。

```
COLORREF GetTipTextColor() const;
```

### <a name="return-value"></a>返回值

表示文本颜色的[COLORREF](/windows/win32/gdi/colorref)值。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TTM_GETTIPTEXTCOLOR](/windows/win32/Controls/ttm-gettiptextcolor)的行为，如 Windows SDK 中所述。

## <a name="ctooltipctrlgettitle"></a><a name="gettitle"></a>CToolTipCtrl：：获取标题

检索当前工具提示控件的标题。

```
void GetTitle(PTTGETTITLE pttgt) const;
```

### <a name="parameters"></a>参数

|参数|说明|
|---------------|-----------------|
|*普特格特*|[出]指向包含工具提示控件信息的[TTGETTITLE](/windows/win32/api/commctrl/ns-commctrl-ttgettitle)结构的指针。 当此方法返回时[，TTGETTITLE](/windows/win32/api/commctrl/ns-commctrl-ttgettitle)结构的*pszTitle*成员指向标题的文本。|

### <a name="remarks"></a>备注

此方法发送[TTM_GETTITLE](/windows/win32/Controls/ttm-gettitle)消息，这在 Windows SDK 中介绍。

## <a name="ctooltipctrlgettoolcount"></a><a name="gettoolcount"></a>CToolTipCtrl：：获取工具计数

检索使用工具尖端控件注册的工具的计数。

```
int GetToolCount() const;
```

### <a name="return-value"></a>返回值

使用工具尖端控件注册的工具计数。

## <a name="ctooltipctrlgettoolinfo"></a><a name="gettoolinfo"></a>CToolTipctrl：：获取工具信息

检索工具尖端控件维护的工具的信息。

```
BOOL GetToolInfo(
    CToolInfo& ToolInfo,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>参数

*工具信息*<br/>
对接收工具`TOOLINFO`文本的对象的引用。

*pwnd*<br/>
指向包含工具的窗口的指针。

*nIDTool*<br/>
工具的 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

`hwnd` *CToolInfo*引用的[TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa)结构和`uId`成员标识了该工具。 如果该工具已通过之前对 的`AddTool`调用在工具尖端控件中注册，则`TOOLINFO`结构将填充有关该工具的信息。

## <a name="ctooltipctrlhittest"></a><a name="hittest"></a>CToolTipctrl：hitTest

测试点以确定它是否在给定工具的边界矩形内，如果是，则检索有关该工具的信息。

```
BOOL HitTest(
    CWnd* pWnd,
    CPoint pt,
    LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>参数

*pwnd*<br/>
指向包含工具的窗口的指针。

*pt*<br/>
指向包含`CPoint`要测试的点的坐标的对象的指针。

*lpToolInfo*<br/>
指向包含工具信息的[TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa)结构的指针。

### <a name="return-value"></a>返回值

如果命中测试信息指定的点位于工具的边界矩形内，则非零;否则 0。

### <a name="remarks"></a>备注

如果此函数返回非零值，*则 lpToolInfo*指向的结构将填充有关其矩形中的刀具的信息。

结构`TTHITTESTINFO`的定义如下：

```cpp
typedef struct _TT_HITTESTINFO { // tthti
    HWND hwnd;   // handle of tool or window with tool
    POINT pt;    // client coordinates of point to test
    TOOLINFO ti; // receives information about the tool
} TTHITTESTINFO, FAR * LPHITTESTINFO;
```

- `hwnd`

   指定工具的句柄。

- `pt`

   如果点位于工具的边界矩形中，则指定点的坐标。

- `ti`

   有关该工具的信息。 有关结构的详细信息，`TOOLINFO`请参阅[CToolTipCtrl：：获取Toolinfo](#gettoolinfo)。

## <a name="ctooltipctrlpop"></a><a name="pop"></a>CToolTipCtrl：:Pop

从视图中删除显示的工具提示窗口。

```
void Pop();
```

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TTM_POP](/windows/win32/Controls/ttm-pop)的行为，如 Windows SDK 中所述。

## <a name="ctooltipctrlpopup"></a><a name="popup"></a>CToolTipCtrl：:P

使当前工具提示控件显示在最后一个鼠标消息的坐标处。

```
void Popup();
```

### <a name="remarks"></a>备注

此方法发送[TTM_POPUP](/windows/win32/Controls/ttm-popup)消息，这在 Windows SDK 中介绍。

### <a name="example"></a>示例

以下代码示例显示工具提示窗口。

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#7](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_3.cpp)]

## <a name="ctooltipctrlrelayevent"></a><a name="relayevent"></a>CToolTipCtrl：：接力事件

将鼠标消息传递到工具提示控件进行处理。

```
void RelayEvent(LPMSG lpMsg);
```

### <a name="parameters"></a>参数

*lpMsg*<br/>
指向包含要中继的消息的[MSG](/windows/win32/api/winuser/ns-winuser-msg)结构的指针。

### <a name="remarks"></a>备注

工具提示控件仅处理以下消息，这些消息通过 ：`RelayEvent`发送给它。

|WM_LBUTTONDOWN|WM_MOUSEMOVE|
|---------------------|-------------------|
|WM_LBUTTONUP|WM_RBUTTONDOWN|
|WM_MBUTTONDOWN|WM_RBUTTONUP|
|WM_MBUTTONUP||

### <a name="example"></a>示例

  请参阅[CPropertySheet 的示例：getTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)。

## <a name="ctooltipctrlsetdelaytime"></a><a name="setdelaytime"></a>CToolTipctrl：：设置延迟时间

设置工具尖端控件的延迟时间。

```
void SetDelayTime(UINT nDelay);

void SetDelayTime(
    DWORD dwDuration,
    int iTime);
```

### <a name="parameters"></a>参数

*nDelay*<br/>
指定新的延迟时间（以毫秒为单位）。

*dwDuration*<br/>
指定将检索的持续时间值的标志。 有关有效值的说明，请参阅[CToolTipCtrl：获取延迟时间](#getdelaytime)。

*iTime*<br/>
指定的延迟时间（以毫秒为单位）。

### <a name="remarks"></a>备注

延迟时间是光标在工具尖端窗口出现之前必须保留的时间长度。 默认延迟时间是 500 毫秒。

## <a name="ctooltipctrlsetmargin"></a><a name="setmargin"></a>CToolTipctrl：：设置边缘

设置工具尖端窗口的上边、左边、下和右边距。

```
void SetMargin(LPRECT lprc);
```

### <a name="parameters"></a>参数

*利赫浦*<br/>
包含要设置`RECT`的边距信息的结构的地址。 `RECT`结构的成员不定义边界矩形。 有关保证金信息的说明，请参阅[CToolTipCtrl：获取保证金](#getmargin)。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TTM_SETMARGIN](/windows/win32/Controls/ttm-setmargin)的行为，如 Windows SDK 中所述。

## <a name="ctooltipctrlsetmaxtipwidth"></a><a name="setmaxtipwidth"></a>CToolTipctrl：：设置最大提示宽度

设置工具尖端窗口的最大宽度。

```
int SetMaxTipWidth(int iWidth);
```

### <a name="parameters"></a>参数

*iWidth*<br/>
要设置的最大工具尖端窗口宽度。

### <a name="return-value"></a>返回值

上一个最大尖端宽度。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TTM_SETMAXTIPWIDTH](/windows/win32/Controls/ttm-setmaxtipwidth)的行为，如 Windows SDK 中所述。

## <a name="ctooltipctrlsettipbkcolor"></a><a name="settipbkcolor"></a>CToolTipctrl：：SetTipBkColor

在工具提示窗口中设置背景颜色。

```
void SetTipBkColor(COLORREF clr);
```

### <a name="parameters"></a>参数

*Clr*<br/>
新的背景颜色。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[的行为TTM_SETTIPBKCOLOR](/windows/win32/Controls/ttm-settipbkcolor)，如 Windows SDK 中所述。

## <a name="ctooltipctrlsettiptextcolor"></a><a name="settiptextcolor"></a>CToolTipctrl：：设置提示文本颜色

在工具提示窗口中设置文本颜色。

```
void SetTipTextColor(COLORREF clr);
```

### <a name="parameters"></a>参数

*Clr*<br/>
新的文本颜色。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TTM_SETTIPTEXTCOLOR](/windows/win32/Controls/ttm-settiptextcolor)的行为，如 Windows SDK 中所述。

## <a name="ctooltipctrlsettitle"></a><a name="settitle"></a>CToolTipctrl：：设置标题

将标准图标和标题字符串添加到工具提示。

```
BOOL SetTitle(
    UINT uIcon,
    LPCTSTR lpstrTitle);
```

### <a name="parameters"></a>参数

*uIcon*<br/>
请参阅 Windows SDK 中[TTM_SETTITLE](/windows/win32/Controls/ttm-settitle)中的*图标*。

*lpstrTitle*<br/>
指向标题字符串的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TTM_SETTITLE](/windows/win32/Controls/ttm-settitle)的行为，如 Windows SDK 中所述。

## <a name="ctooltipctrlsettoolinfo"></a><a name="settoolinfo"></a>CToolTipctrl：：设置工具信息

设置工具提示为工具维护的信息。

```
void SetToolInfo(LPTOOLINFO lpToolInfo);
```

### <a name="parameters"></a>参数

*lpToolInfo*<br/>
指向[TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa)结构的指针，用于指定要设置的信息。

## <a name="ctooltipctrlsettoolrect"></a><a name="settoolrect"></a>CToolTipctrl：：设置工具重新

为工具设置新的边界矩形。

```
void SetToolRect(
    CWnd* pWnd,
    UINT_PTR nIDTool,
    LPCRECT lpRect);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
指向包含工具的窗口的指针。

*nIDTool*<br/>
工具的 ID。

*lpRect*<br/>
指向指定新边界矩形的[RECT](/previous-versions/dd162897\(v=vs.85\))结构的指针。

## <a name="ctooltipctrlsetwindowtheme"></a><a name="setwindowtheme"></a>CToolTipctrl：：设置窗口主题

设置工具提示窗口的视觉样式。

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>参数

*pssSubApp名称*<br/>
指向 Unicode 字符串的指针，其中包含要设置的可视样式。

### <a name="return-value"></a>返回值

不使用返回值。

### <a name="remarks"></a>备注

此成员函数模拟[TTM_SETWINDOWTHEME](/windows/win32/Controls/ttm-setwindowtheme)消息的功能，如 Windows SDK 中所述。

## <a name="ctooltipctrlupdate"></a><a name="update"></a>CToolTipCtrl：：更新

强制重绘当前工具。

```
void Update();
```

## <a name="ctooltipctrlupdatetiptext"></a><a name="updatetiptext"></a>CToolTipctrl：：更新提示文本

更新此控件工具的工具提示文本。

```
void UpdateTipText(
    LPCTSTR lpszText,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);

void UpdateTipText(
    UINT nIDText,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>参数

*lpszText*<br/>
指向工具的文本的指针。

*pwnd*<br/>
指向包含工具的窗口的指针。

*nIDTool*<br/>
工具的 ID。

*nIDText*<br/>
包含工具文本的字符串资源的 ID。

## <a name="see-also"></a>另请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CToolBar 类](../../mfc/reference/ctoolbar-class.md)
