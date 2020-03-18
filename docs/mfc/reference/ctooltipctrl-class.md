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
ms.openlocfilehash: bf32671eb3535de1bf072e24bc642145e87c84ee
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426323"
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
|[CToolTipCtrl：： CToolTipCtrl](#ctooltipctrl)|构造 `CToolTipCtrl` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CToolTipCtrl：： Activate](#activate)|激活和停用工具提示控件。|
|[CToolTipCtrl：： AddTool](#addtool)|向工具提示控件注册工具。|
|[CToolTipCtrl：： AdjustRect](#adjustrect)|在工具提示控件的文本显示矩形及其窗口矩形之间转换。|
|[CToolTipCtrl：： Create](#create)|创建一个工具提示控件，并将其附加到 `CToolTipCtrl` 对象上。|
|[CToolTipCtrl：： CreateEx](#createex)|使用指定的 Windows 扩展样式创建一个工具提示控件，并将其附加到 `CToolTipCtrl` 的对象。|
|[CToolTipCtrl：:D elTool](#deltool)|从工具提示控件中删除工具。|
|[CToolTipCtrl：： GetBubbleSize](#getbubblesize)|检索工具提示的大小。|
|[CToolTipCtrl：： GetCurrentTool](#getcurrenttool)|检索当前 tooltip 控件显示的工具提示窗口的大小、位置和文本等信息。|
|[CToolTipCtrl：： GetDelayTime](#getdelaytime)|检索当前为工具提示控件设置的初始、弹出和 reshow 持续时间。|
|[CToolTipCtrl：： GetMargin](#getmargin)|检索为 "工具提示" 窗口设置的上、左、下边距和右边距。|
|[CToolTipCtrl：： GetMaxTipWidth](#getmaxtipwidth)|检索工具提示窗口的最大宽度。|
|[CToolTipCtrl：： GetText](#gettext)|检索工具提示控件为工具保留的文本。|
|[CToolTipCtrl：： GetTipBkColor](#gettipbkcolor)|检索工具提示窗口中的背景色。|
|[CToolTipCtrl：： GetTipTextColor](#gettiptextcolor)|检索工具提示窗口中的文本颜色。|
|[CToolTipCtrl：： GetTitle](#gettitle)|检索当前 tooltip 控件的标题。|
|[CToolTipCtrl：： GetToolCount](#gettoolcount)|检索由工具提示控件维护的工具的计数。|
|[CToolTipCtrl：： GetToolInfo](#gettoolinfo)|检索工具提示控件对工具维护的信息。|
|[CToolTipCtrl：： System.windows.media.visualtreehelper.hittest](#hittest)|测试一个点，以确定它是否位于给定工具的边框内。 如果是，则检索有关该工具的信息。|
|[CToolTipCtrl：:P op](#pop)|从视图中删除显示的 "工具提示" 窗口。|
|[CToolTipCtrl：:P opup](#popup)|使当前 ToolTip 控件以上一条鼠标消息的坐标显示。|
|[CToolTipCtrl：： RelayEvent](#relayevent)|将鼠标消息传递给工具提示控件进行处理。|
|[CToolTipCtrl：： SetDelayTime](#setdelaytime)|设置工具提示控件的初始、弹出和 reshow 持续时间。|
|[CToolTipCtrl：： SetMargin](#setmargin)|设置工具提示窗口的上、左、下和右边距。|
|[CToolTipCtrl：： SetMaxTipWidth](#setmaxtipwidth)|设置工具提示窗口的最大宽度。|
|[CToolTipCtrl：： SetTipBkColor](#settipbkcolor)|设置工具提示窗口中的背景色。|
|[CToolTipCtrl：： SetTipTextColor](#settiptextcolor)|设置工具提示窗口中的文本颜色。|
|[CToolTipCtrl：： SetTitle](#settitle)|向工具提示添加标准图标和标题字符串。|
|[CToolTipCtrl：： SetToolInfo](#settoolinfo)|设置工具提示为工具维护的信息。|
|[CToolTipCtrl：： SetToolRect](#settoolrect)|为工具设置新的边框。|
|[CToolTipCtrl：： SetWindowTheme](#setwindowtheme)|设置工具提示窗口的视觉样式。|
|[CToolTipCtrl：： Update](#update)|强制重新绘制当前工具。|
|[CToolTipCtrl：： UpdateTipText](#updatetiptext)|设置工具的工具提示文本。|

## <a name="remarks"></a>备注

"工具" 是窗口（如子窗口或控件）或窗口的工作区内的应用程序定义的矩形区域。 工具提示在大多数时间都是隐藏的，它仅在用户将光标置于工具上并在其上停留约半秒时间时显示。 工具提示显示在光标附近，当用户单击鼠标按钮或将光标移出该工具时消失。

`CToolTipCtrl` 提供了一种功能，用于控制工具提示的初始时间和持续时间、工具提示文本周围的边距宽度、工具提示窗口本身的宽度以及工具提示的背景和文本颜色。 一个工具提示控件可以提供多个工具的信息。

`CToolTipCtrl` 类提供了 Windows 公共工具提示控件的功能。 此控件（因此 `CToolTipCtrl` 类）仅适用于在 Windows 95/98 和 Windows NT 版本3.51 及更高版本下运行的程序。

有关启用工具提示的详细信息，请参阅[Windows 中不是从 CFrameWnd 派生的工具提示](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)。

有关使用 `CToolTipCtrl`的详细信息，请参阅[控件](../../mfc/controls-mfc.md)和[使用 CToolTipCtrl](../../mfc/using-ctooltipctrl.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CToolTipCtrl`

## <a name="requirements"></a>要求

**标头：** afxcmn.h

##  <a name="activate"></a>CToolTipCtrl：： Activate

调用此函数以激活或停用工具提示控件。

```
void Activate(BOOL bActivate);
```

### <a name="parameters"></a>parameters

*bActivate*<br/>
指定是否激活或停用工具提示控件。

### <a name="remarks"></a>备注

如果*bActivate*为 TRUE，则激活控件;如果为 FALSE，则停用它。

当工具提示控件处于活动状态时，当光标位于向控件注册的工具上时，将显示工具提示信息。如果它处于非活动状态，即使光标位于工具上，也不会显示工具提示信息。

### <a name="example"></a>示例

  请参阅[CPropertySheet：： GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)的示例。

##  <a name="addtool"></a>CToolTipCtrl：： AddTool

向工具提示控件注册工具。

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

### <a name="parameters"></a>parameters

*pWnd*<br/>
指向包含该工具的窗口的指针。

*nIDText*<br/>
包含工具文本的字符串资源的 ID。

*lpRectTool*<br/>
指向[矩形](/previous-versions/dd162897\(v=vs.85\))结构的指针，该结构包含该工具的边框的坐标。 坐标相对于由*pWnd*标识的窗口的工作区的左上角。

*nIDTool*<br/>
工具的 ID。

*lpszText*<br/>
指向工具的文本的指针。 如果此参数包含 LPSTR_TEXTCALLBACK 的值，TTN_NEEDTEXT 通知消息将跳到*pWnd*指向的窗口的父级。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

*LpRectTool*和*nIDTool*参数必须是有效的，或者，如果*LpRectTool*为 NULL，则*nIDTool*必须为0。

工具提示控件可以与多个工具相关联。 调用此函数可将工具注册到工具提示控件，以便在光标位于工具上时显示工具提示中存储的信息。

> [!NOTE]
>  不能使用 `AddTool`将工具提示设置为静态控件。

### <a name="example"></a>示例

  请参阅[CPropertySheet：： GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)的示例。

##  <a name="adjustrect"></a>CToolTipCtrl：： AdjustRect

在 tooltip 控件的文本显示矩形及其窗口矩形之间转换。

```
BOOL AdjustRect(
    LPRECT lprc,
    BOOL bLarger = TRUE);
```

### <a name="parameters"></a>parameters

*lprc*<br/>
指向[矩形](/previous-versions/dd162897\(v=vs.85\))结构的指针，该结构包含工具提示窗口矩形或文本显示矩形。

*bLarger*<br/>
如果为 TRUE，则使用*lprc*来指定文本显示矩形，并接收对应的窗口矩形。 如果为 FALSE，则使用*lprc*指定一个窗口矩形，并收到相应的文本显示矩形。

### <a name="return-value"></a>返回值

如果成功调整矩形，则为非零值;否则为0。

### <a name="remarks"></a>备注

此成员函数从其窗口矩形计算工具提示控件的文本显示矩形，或从显示指定文本显示矩形的工具提示窗口矩形计算。

此成员函数实现 Win32 消息[TTM_ADJUSTRECT](/windows/win32/Controls/ttm-adjustrect)的行为，如 Windows SDK 中所述。

##  <a name="create"></a>CToolTipCtrl：： Create

创建一个工具提示控件，并将其附加到 `CToolTipCtrl` 对象上。

```
virtual BOOL Create(CWnd* pParentWnd, DWORD dwStyle = 0);
```

### <a name="parameters"></a>parameters

*pParentWnd*<br/>
指定工具提示控件的父窗口，通常为 `CDialog`。 值不得为 NULL。

*dwStyle*<br/>
指定工具提示控件的样式。 有关详细信息，请参阅 "**备注**" 部分。

### <a name="return-value"></a>返回值

如果成功创建 `CToolTipCtrl` 对象，则为非零值;否则为0。

### <a name="remarks"></a>备注

可以通过两个步骤构造 `CToolTipCtrl`。 首先，调用构造函数来构造 `CToolTipCtrl` 对象，然后调用 `Create` 创建工具提示控件，并将其附加到 `CToolTipCtrl` 对象。

*DwStyle*参数可以是[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)的任意组合。 此外，工具提示控件具有两种类特定样式： TTS_ALWAYSTIP 和 TTS_NOPREFIX。

|Style|含义|
|-----------|-------------|
|TTS_ALWAYSTIP|指定当光标位于工具上时，无论工具提示控件的所有者窗口处于活动状态还是非活动状态，都将显示工具提示。 如果没有此样式，工具提示控件将在工具的所有者窗口处于活动状态时显示，而不是在处于不活动状态时显示。|
|TTS_NOPREFIX|此样式可防止系统从字符串中去除与号（&）字符。 如果工具提示控件没有 TTS_NOPREFIX 样式，则系统会自动提取 "&" 字符，这允许应用程序在工具提示控件中同时使用同一字符串作为菜单项和文本。|

工具提示控件具有 "WS_POPUP" 和 "WS_EX_TOOLWINDOW" 窗口样式，无论在创建控件时是否指定它们都是如此。

若要创建具有扩展 windows 样式的工具提示控件，请调用[CToolTipCtrl：： CreateEx](#createex)而不是 `Create`。

### <a name="example"></a>示例

  请参阅[CPropertySheet：： GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)的示例。

##  <a name="createex"></a>CToolTipCtrl：： CreateEx

创建一个控件（子窗口）并将其与 `CToolTipCtrl` 对象相关联。

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwStyle = 0,
    DWORD dwStyleEx = 0);
```

### <a name="parameters"></a>parameters

*pParentWnd*<br/>
指向作为控件的父级的窗口的指针。

*dwStyle*<br/>
指定工具提示控件的样式。 有关详细信息，请参阅[Create](#create)的 "**备注**" 部分。

*dwStyleEx*<br/>
指定正在创建的控件的扩展样式。 有关扩展 Windows 样式的列表，请参阅 Windows SDK 中[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*参数。

### <a name="return-value"></a>返回值

如果成功，则为非零; 否则为0。

### <a name="remarks"></a>备注

使用 `CreateEx` 而不是 `Create` 来应用扩展 Windows 样式，该样式由 Windows 扩展样式指定为在**WS_EX_** 。

##  <a name="ctooltipctrl"></a>CToolTipCtrl：： CToolTipCtrl

构造 `CToolTipCtrl` 对象。

```
CToolTipCtrl();
```

### <a name="remarks"></a>备注

构造对象之后必须调用 `Create`。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#74](../../mfc/codesnippet/cpp/ctooltipctrl-class_1.h)]

##  <a name="deltool"></a>CToolTipCtrl：:D elTool

从工具提示控件支持的工具集合中删除由*pWnd*和*nIDTool*指定的工具。

```
void DelTool(
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>parameters

*pWnd*<br/>
指向包含该工具的窗口的指针。

*nIDTool*<br/>
工具的 ID。

##  <a name="getbubblesize"></a>CToolTipCtrl：： GetBubbleSize

检索工具提示的大小。

```
CSize GetBubbleSize(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>parameters

*lpToolInfo*<br/>
指向工具提示的[TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa)结构的指针。

### <a name="return-value"></a>返回值

工具提示的大小。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TTM_GETBUBBLESIZE](/windows/win32/Controls/ttm-getbubblesize)的行为，如 Windows SDK 中所述。

##  <a name="getcurrenttool"></a>CToolTipCtrl：： GetCurrentTool

检索当前 tooltip 控件所显示的工具提示窗口的大小、位置和文本等信息。

```
BOOL GetCurrentTool(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>parameters

|参数|说明|
|---------------|-----------------|
|*lpToolInfo*|弄指向[TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa)结构的指针，该结构接收有关当前工具提示窗口的信息。|

### <a name="return-value"></a>返回值

如果成功检索信息，则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

此方法发送 Windows SDK 中描述的[TTM_GETCURRENTTOOL](/windows/win32/Controls/ttm-getcurrenttool)消息。

### <a name="example"></a>示例

下面的代码示例检索有关当前工具提示窗口的信息。

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#6](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_2.cpp)]

##  <a name="getdelaytime"></a>CToolTipCtrl：： GetDelayTime

检索当前为工具提示控件设置的初始、弹出和 reshow 持续时间。

```
int GetDelayTime(DWORD dwDuration) const;
```

### <a name="parameters"></a>parameters

*dwDuration*<br/>
指定将检索的持续时间值的标志。 此参数可以是下列值之一：

- TTDT_AUTOPOP 检索当指针在工具的边框内保持静止时，工具提示窗口保持可见的时间长度。

- TTDT_INITIAL 检索在工具提示窗口出现之前，指针必须在工具的边框内保持静止的时间长度。

- TTDT_RESHOW 检索当指针从一个工具移到另一个工具时，后续工具提示窗口出现的时间长度。

### <a name="return-value"></a>返回值

指定的延迟时间（以毫秒为单位）

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TTM_GETDELAYTIME](/windows/win32/Controls/ttm-getdelaytime)的行为，如 Windows SDK 中所述。

##  <a name="getmargin"></a>CToolTipCtrl：： GetMargin

检索为 "工具提示" 窗口设置的上、左、下边距和右边距。

```
void GetMargin(LPRECT lprc) const;
```

### <a name="parameters"></a>parameters

*lprc*<br/>
将接收边距信息的 `RECT` 结构的地址。 [RECT](/previous-versions/dd162897\(v=vs.85\))结构的成员未定义边界矩形。 在此消息中，结构成员解释如下：

|成员|表示|
|------------|--------------------|
|`top`|顶部边框和工具提示文本的顶部之间的距离（以像素为单位）。|
|`left`|左边框和提示文本的左端之间的距离（以像素为单位）。|
|`bottom`|下边框和笔尖文本底部之间的距离（以像素为单位）。|
|`right`|右边框和右端文本的右边缘之间的距离（以像素为单位）。|

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TTM_GETMARGIN](/windows/win32/Controls/ttm-getmargin)的行为，如 Windows SDK 中所述。

##  <a name="getmaxtipwidth"></a>CToolTipCtrl：： GetMaxTipWidth

检索工具提示窗口的最大宽度。

```
int GetMaxTipWidth() const;
```

### <a name="return-value"></a>返回值

工具提示窗口的最大宽度。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TTM_GETMAXTIPWIDTH](/windows/win32/Controls/ttm-getmaxtipwidth)的行为，如 Windows SDK 中所述。

##  <a name="gettext"></a>CToolTipCtrl：： GetText

检索工具提示控件为工具保留的文本。

```
void GetText(
    CString& str,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>parameters

*str*<br/>
对接收工具文本的 `CString` 对象的引用。

*pWnd*<br/>
指向包含该工具的窗口的指针。

*nIDTool*<br/>
工具的 ID。

### <a name="remarks"></a>备注

*PWnd*和*nIDTool*参数标识工具。 如果以前通过调用 `CToolTipCtrl::AddTool`向工具提示控件注册了该工具，则会为*str*参数引用的对象指定该工具的文本。

##  <a name="gettipbkcolor"></a>CToolTipCtrl：： GetTipBkColor

检索工具提示窗口中的背景色。

```
COLORREF GetTipBkColor() const;
```

### <a name="return-value"></a>返回值

一个表示背景色的[COLORREF](/windows/win32/gdi/colorref)值。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TTM_GETTIPBKCOLOR](/windows/win32/Controls/ttm-gettipbkcolor)的行为，如 Windows SDK 中所述。

##  <a name="gettiptextcolor"></a>CToolTipCtrl：： GetTipTextColor

检索工具提示窗口中的文本颜色。

```
COLORREF GetTipTextColor() const;
```

### <a name="return-value"></a>返回值

表示文本颜色的[COLORREF](/windows/win32/gdi/colorref)值。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TTM_GETTIPTEXTCOLOR](/windows/win32/Controls/ttm-gettiptextcolor)的行为，如 Windows SDK 中所述。

##  <a name="gettitle"></a>CToolTipCtrl：： GetTitle

检索当前 tooltip 控件的标题。

```
void GetTitle(PTTGETTITLE pttgt) const;
```

### <a name="parameters"></a>parameters

|参数|说明|
|---------------|-----------------|
|*pttgt*|弄指向[TTGETTITLE](/windows/win32/api/commctrl/ns-commctrl-ttgettitle)结构的指针，该结构包含 ToolTip 控件的相关信息。 此方法返回时， [TTGETTITLE](/windows/win32/api/commctrl/ns-commctrl-ttgettitle)结构的*pszTitle*成员指向标题的文本。|

### <a name="remarks"></a>备注

此方法发送 Windows SDK 中描述的[TTM_GETTITLE](/windows/win32/Controls/ttm-gettitle)消息。

##  <a name="gettoolcount"></a>CToolTipCtrl：： GetToolCount

检索向工具提示控件注册的工具的计数。

```
int GetToolCount() const;
```

### <a name="return-value"></a>返回值

向工具提示控件注册的工具的计数。

##  <a name="gettoolinfo"></a>CToolTipCtrl：： GetToolInfo

检索工具提示控件对工具维护的信息。

```
BOOL GetToolInfo(
    CToolInfo& ToolInfo,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>parameters

*ToolInfo*<br/>
对接收工具文本的 `TOOLINFO` 对象的引用。

*pWnd*<br/>
指向包含该工具的窗口的指针。

*nIDTool*<br/>
工具的 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

*CToolInfo*所引用的[TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa)结构的 `hwnd` 和 `uId` 成员标识该工具。 如果已通过对 `AddTool`的前一次调用向工具提示控件注册了该工具，则 `TOOLINFO` 结构将使用有关该工具的信息进行填充。

##  <a name="hittest"></a>CToolTipCtrl：： System.windows.media.visualtreehelper.hittest

测试一个点以确定它是否位于给定工具的边框内，如果是，则检索有关该工具的信息。

```
BOOL HitTest(
    CWnd* pWnd,
    CPoint pt,
    LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>parameters

*pWnd*<br/>
指向包含该工具的窗口的指针。

*pt*<br/>
指向 `CPoint` 对象的指针，该对象包含要测试的点的坐标。

*lpToolInfo*<br/>
指向[TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa)结构的指针，该结构包含有关该工具的信息。

### <a name="return-value"></a>返回值

如果命中测试信息指定的点在工具的边框内，则为非零值;否则为0。

### <a name="remarks"></a>备注

如果此函数返回一个非零值，则*lpToolInfo*所指向的结构将使用该点所在的矩形的工具中的信息进行填充。

`TTHITTESTINFO` 结构的定义如下所示：

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

   指定点在工具的边框中的坐标。

- `ti`

   有关该工具的信息。 有关 `TOOLINFO` 结构的详细信息，请参阅[CToolTipCtrl：： GetToolInfo](#gettoolinfo)。

##  <a name="pop"></a>CToolTipCtrl：:P op

从视图中删除显示的 "工具提示" 窗口。

```
void Pop();
```

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TTM_POP](/windows/win32/Controls/ttm-pop)的行为，如 Windows SDK 中所述。

##  <a name="popup"></a>CToolTipCtrl：:P opup

使当前 tooltip 控件以上一条鼠标消息的坐标显示。

```
void Popup();
```

### <a name="remarks"></a>备注

此方法发送 Windows SDK 中描述的[TTM_POPUP](/windows/win32/Controls/ttm-popup)消息。

### <a name="example"></a>示例

下面的代码示例显示 "工具提示" 窗口。

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#7](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_3.cpp)]

##  <a name="relayevent"></a>CToolTipCtrl：： RelayEvent

将鼠标消息传递给工具提示控件进行处理。

```
void RelayEvent(LPMSG lpMsg);
```

### <a name="parameters"></a>parameters

*lpMsg*<br/>
指向包含要中继的消息的[MSG](/windows/win32/api/winuser/ns-winuser-msg)结构的指针。

### <a name="remarks"></a>备注

工具提示控件仅处理以下消息，这些消息通过 `RelayEvent`发送给它：

|WM_LBUTTONDOWN|WM_MOUSEMOVE|
|---------------------|-------------------|
|WM_LBUTTONUP|WM_RBUTTONDOWN|
|WM_MBUTTONDOWN|WM_RBUTTONUP|
|WM_MBUTTONUP||

### <a name="example"></a>示例

  请参阅[CPropertySheet：： GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)的示例。

##  <a name="setdelaytime"></a>CToolTipCtrl：： SetDelayTime

设置工具提示控件的延迟时间。

```
void SetDelayTime(UINT nDelay);

void SetDelayTime(
    DWORD dwDuration,
    int iTime);
```

### <a name="parameters"></a>parameters

*nDelay*<br/>
指定新的延迟时间（以毫秒为单位）。

*dwDuration*<br/>
指定将检索的持续时间值的标志。 有关有效值的说明，请参阅[CToolTipCtrl：： GetDelayTime](#getdelaytime) 。

*iTime*<br/>
指定的延迟时间（以毫秒为单位）。

### <a name="remarks"></a>备注

延迟时间是在工具提示窗口出现之前游标必须在某个工具上保留的时间长度。 默认延迟时间为500毫秒。

##  <a name="setmargin"></a>CToolTipCtrl：： SetMargin

设置工具提示窗口的上、左、下和右边距。

```
void SetMargin(LPRECT lprc);
```

### <a name="parameters"></a>parameters

*lprc*<br/>
包含要设置的边距信息的 `RECT` 结构的地址。 `RECT` 结构的成员未定义边界矩形。 有关边距信息的说明，请参阅[CToolTipCtrl：： GetMargin](#getmargin) 。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TTM_SETMARGIN](/windows/win32/Controls/ttm-setmargin)的行为，如 Windows SDK 中所述。

##  <a name="setmaxtipwidth"></a>CToolTipCtrl：： SetMaxTipWidth

设置工具提示窗口的最大宽度。

```
int SetMaxTipWidth(int iWidth);
```

### <a name="parameters"></a>parameters

*iWidth*<br/>
要设置的最大工具提示窗口宽度。

### <a name="return-value"></a>返回值

之前的最大笔尖宽度。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TTM_SETMAXTIPWIDTH](/windows/win32/Controls/ttm-setmaxtipwidth)的行为，如 Windows SDK 中所述。

##  <a name="settipbkcolor"></a>CToolTipCtrl：： SetTipBkColor

设置工具提示窗口中的背景色。

```
void SetTipBkColor(COLORREF clr);
```

### <a name="parameters"></a>parameters

*clr*<br/>
新背景色。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TTM_SETTIPBKCOLOR](/windows/win32/Controls/ttm-settipbkcolor)的行为，如 Windows SDK 中所述。

##  <a name="settiptextcolor"></a>CToolTipCtrl：： SetTipTextColor

设置工具提示窗口中的文本颜色。

```
void SetTipTextColor(COLORREF clr);
```

### <a name="parameters"></a>parameters

*clr*<br/>
新的文本颜色。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TTM_SETTIPTEXTCOLOR](/windows/win32/Controls/ttm-settiptextcolor)的行为，如 Windows SDK 中所述。

##  <a name="settitle"></a>CToolTipCtrl：： SetTitle

向工具提示添加标准图标和标题字符串。

```
BOOL SetTitle(
    UINT uIcon,
    LPCTSTR lpstrTitle);
```

### <a name="parameters"></a>parameters

*uIcon*<br/>
请参阅 Windows SDK [TTM_SETTITLE](/windows/win32/Controls/ttm-settitle)中的*图标*。

*lpstrTitle*<br/>
指向标题字符串的指针。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数实现 Win32 消息[TTM_SETTITLE](/windows/win32/Controls/ttm-settitle)的行为，如 Windows SDK 中所述。

##  <a name="settoolinfo"></a>CToolTipCtrl：： SetToolInfo

设置工具提示为工具维护的信息。

```
void SetToolInfo(LPTOOLINFO lpToolInfo);
```

### <a name="parameters"></a>parameters

*lpToolInfo*<br/>
指向[TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa)结构的指针，该结构指定要设置的信息。

##  <a name="settoolrect"></a>CToolTipCtrl：： SetToolRect

为工具设置新的边框。

```
void SetToolRect(
    CWnd* pWnd,
    UINT_PTR nIDTool,
    LPCRECT lpRect);
```

### <a name="parameters"></a>parameters

*pWnd*<br/>
指向包含该工具的窗口的指针。

*nIDTool*<br/>
工具的 ID。

*lpRect*<br/>
指向指定新[边框的矩形结构的](/previous-versions/dd162897\(v=vs.85\))指针。

##  <a name="setwindowtheme"></a>CToolTipCtrl：： SetWindowTheme

设置工具提示窗口的视觉样式。

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>parameters

*pszSubAppName*<br/>
指向包含要设置的视觉样式的 Unicode 字符串的指针。

### <a name="return-value"></a>返回值

不使用返回值。

### <a name="remarks"></a>备注

此成员函数模拟[TTM_SETWINDOWTHEME](/windows/win32/Controls/ttm-setwindowtheme)消息的功能，如 Windows SDK 中所述。

##  <a name="update"></a>CToolTipCtrl：： Update

强制重新绘制当前工具。

```
void Update();
```

##  <a name="updatetiptext"></a>CToolTipCtrl：： UpdateTipText

更新此控件的工具的工具提示文本。

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

### <a name="parameters"></a>parameters

*lpszText*<br/>
指向工具的文本的指针。

*pWnd*<br/>
指向包含该工具的窗口的指针。

*nIDTool*<br/>
工具的 ID。

*nIDText*<br/>
包含工具文本的字符串资源的 ID。

## <a name="see-also"></a>另请参阅

[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CToolBar 类](../../mfc/reference/ctoolbar-class.md)
