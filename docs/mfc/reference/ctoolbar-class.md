---
title: CToolBar 类
ms.date: 11/04/2016
f1_keywords:
- CToolBar
- AFXEXT/CToolBar
- AFXEXT/CToolBar::CToolBar
- AFXEXT/CToolBar::CommandToIndex
- AFXEXT/CToolBar::Create
- AFXEXT/CToolBar::CreateEx
- AFXEXT/CToolBar::GetButtonInfo
- AFXEXT/CToolBar::GetButtonStyle
- AFXEXT/CToolBar::GetButtonText
- AFXEXT/CToolBar::GetItemID
- AFXEXT/CToolBar::GetItemRect
- AFXEXT/CToolBar::GetToolBarCtrl
- AFXEXT/CToolBar::LoadBitmap
- AFXEXT/CToolBar::LoadToolBar
- AFXEXT/CToolBar::SetBitmap
- AFXEXT/CToolBar::SetButtonInfo
- AFXEXT/CToolBar::SetButtons
- AFXEXT/CToolBar::SetButtonStyle
- AFXEXT/CToolBar::SetButtonText
- AFXEXT/CToolBar::SetHeight
- AFXEXT/CToolBar::SetSizes
helpviewer_keywords:
- CToolBar [MFC], CToolBar
- CToolBar [MFC], CommandToIndex
- CToolBar [MFC], Create
- CToolBar [MFC], CreateEx
- CToolBar [MFC], GetButtonInfo
- CToolBar [MFC], GetButtonStyle
- CToolBar [MFC], GetButtonText
- CToolBar [MFC], GetItemID
- CToolBar [MFC], GetItemRect
- CToolBar [MFC], GetToolBarCtrl
- CToolBar [MFC], LoadBitmap
- CToolBar [MFC], LoadToolBar
- CToolBar [MFC], SetBitmap
- CToolBar [MFC], SetButtonInfo
- CToolBar [MFC], SetButtons
- CToolBar [MFC], SetButtonStyle
- CToolBar [MFC], SetButtonText
- CToolBar [MFC], SetHeight
- CToolBar [MFC], SetSizes
ms.assetid: e868da26-5e07-4607-9651-e2f863ad9059
ms.openlocfilehash: 4977cbe0b749724f999d6d7089d46f12d1e2963e
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426821"
---
# <a name="ctoolbar-class"></a>CToolBar 类

具有一行位图化按钮和可选分隔符的控件条。

## <a name="syntax"></a>语法

```
class CToolBar : public CControlBar
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CToolBar：： CToolBar](#ctoolbar)|构造 `CToolBar` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CToolBar：： CommandToIndex](#commandtoindex)|使用给定的命令 ID 返回按钮的索引。|
|[CToolBar：： Create](#create)|创建 Windows 工具栏，并将其附加到 `CToolBar` 对象上。|
|[CToolBar：： CreateEx](#createex)|使用嵌入的 `CToolBarCtrl` 对象创建具有其他样式的 `CToolBar` 对象。|
|[CToolBar：： GetButtonInfo](#getbuttoninfo)|检索按钮的 ID、样式和图像号。|
|[CToolBar：： GetButtonStyle](#getbuttonstyle)|检索按钮的样式。|
|[CToolBar：： GetButtonText](#getbuttontext)|检索将在按钮上显示的文本。|
|[CToolBar：： GetItemID](#getitemid)|返回给定索引处的按钮或分隔符的命令 ID。|
|[CToolBar：： GetItemRect](#getitemrect)|检索给定索引处的项的显示矩形。|
|[CToolBar：： GetToolBarCtrl](#gettoolbarctrl)|允许直接访问基础公共控件。|
|[CToolBar：： LoadBitmap](#loadbitmap)|加载包含位图按钮图像的位图。|
|[CToolBar：： LoadToolBar](#loadtoolbar)|加载使用资源编辑器创建的工具栏资源。|
|[CToolBar：： SetBitmap](#setbitmap)|设置位图图像。|
|[CToolBar：： SetButtonInfo](#setbuttoninfo)|设置按钮的 ID、样式和图像号。|
|[CToolBar：： SetButtons](#setbuttons)|在位图内设置按钮样式和按钮图像的索引。|
|[CToolBar：： SetButtonStyle](#setbuttonstyle)|设置按钮的样式。|
|[CToolBar：： SetButtonText](#setbuttontext)|设置将在按钮上显示的文本。|
|[CToolBar：： SetHeight](#setheight)|设置工具栏的高度。|
|[CToolBar：： SetSizes](#setsizes)|设置按钮及其位图的大小。|

## <a name="remarks"></a>备注

按钮可以像普通按钮、复选框按钮或单选按钮一样操作。 `CToolBar` 对象通常是从类[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)派生的框架窗口对象的嵌入成员。

使用[CToolBar：： GetToolBarCtrl](#gettoolbarctrl)（MFC 4.0 的一种新成员函数），可以利用 Windows 公共控件对工具栏自定义和其他功能的支持。 `CToolBar` 成员函数可为你带来许多 Windows 公共控件的功能;但是，在调用 `GetToolBarCtrl`时，可以为工具栏更多地指定 Windows 95/98 工具栏的特性。 调用 `GetToolBarCtrl`时，它将返回对 `CToolBarCtrl` 对象的引用。 有关使用 Windows 公共控件设计工具栏的详细信息，请参阅[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) 。 有关公共控件的更多常规信息，请参阅 Windows SDK 中的[公共控件](/windows/win32/Controls/common-controls-intro)。

视觉C++对象提供了两种方法来创建工具栏。 若要使用资源编辑器创建工具栏资源，请执行以下步骤：

1. 创建工具栏资源。

1. 构造 `CToolBar` 对象。

1. 调用[create](#create) （或[CreateEx](#createex)）函数创建 Windows 工具栏，并将其附加到 `CToolBar` 的对象。

1. 调用[LoadToolBar](#loadtoolbar)以加载工具栏资源。

否则，请执行以下步骤：

1. 构造 `CToolBar` 对象。

1. 调用[create](#create) （或[CreateEx](#createex)）函数创建 Windows 工具栏，并将其附加到 `CToolBar` 的对象。

1. 调用[LoadBitmap](#loadbitmap)以加载包含工具栏按钮图像的位图。

1. 调用[SetButtons](#setbuttons)设置按钮样式，并将每个按钮与位图中的图像关联。

工具栏中的所有按钮图像均来自一个位图，其中每个按钮都必须包含一个图像。 所有映像的大小必须相同;默认值为16像素宽，15像素高。 图像必须在位图中并行。

`SetButtons` 函数采用指向控件 Id 的数组和一个整数的指针，该数组指定数组中元素的数目。 函数将每个按钮的 ID 设置为数组中相应元素的值，并为每个按钮分配一个图像索引，该索引指定按钮的图像在位图中的位置。 如果数组元素的值 ID_SEPARATOR，则不会分配任何图像索引。

位图中图像的顺序通常是在屏幕上绘制图像的顺序，但你可以使用[SetButtonInfo](#setbuttoninfo)函数更改图像顺序和绘制顺序之间的关系。

工具栏中的所有按钮的大小都相同。 根据*软件设计的 Windows 界面准则*，默认值为 24 x 22 像素。 图像和按钮尺寸之间的任何额外空间用于形成图像周围的边框。

每个按钮都有一个图像。 将从该图像生成各种按钮状态和样式（按下、向上、向下、已禁用、已禁用、已禁用）。 尽管位图可以是任意颜色，但你可以通过黑白图像和灰色阴影获得最佳结果。

> [!WARNING]
> `CToolBar` 支持最多具有16种颜色的位图。 在将图像加载到工具栏编辑器时，Visual Studio 会自动将图像转换为16色位图（如有必要），并在图像转换后显示警告消息。 如果你使用的图像的颜色超过16个（使用外部编辑器来编辑图像），则应用程序可能会意外地表现。

默认情况下，工具栏按钮模拟普通按钮。 但是，工具栏按钮还可以模拟复选框按钮或单选按钮。 复选框按钮具有三种状态：选中、已清除和不确定。 单选按钮只有两种状态：已选中并已清除。

若要设置单个按钮或分隔符样式而不指向数组，请调用[GetButtonStyle](#getbuttonstyle)来检索样式，然后调用[SetButtonStyle](#setbuttonstyle)而不是 `SetButtons`。 如果要在运行时更改按钮的样式，`SetButtonStyle` 最为有用。

若要指定要在按钮上显示的文本，请调用[GetButtonText](#getbuttontext)来检索要在按钮上显示的文本，然后调用[SetButtonText](#setbuttontext)以设置文本。

若要创建复选框按钮，请向其分配样式 TBBS_CHECKBOX 或在 ON_UPDATE_COMMAND_UI 处理程序中使用 `CCmdUI` 对象的 `SetCheck` 成员函数。 调用 `SetCheck` 会将按钮转换为复选框按钮。 传递 `SetCheck` 参数0表示未选中，1表示选中，2表示不确定。

若要创建单选按钮，请从 ON_UPDATE_COMMAND_UI 处理程序调用[CCmdUI](../../mfc/reference/ccmdui-class.md)对象的[SetRadio](../../mfc/reference/ccmdui-class.md#setradio)成员函数。 如果选中，则将 `SetRadio` 参数0表示未选中或非零。 为了提供单选组的相互排斥行为，您必须对组中的所有按钮具有 ON_UPDATE_COMMAND_UI 处理程序。

有关使用 `CToolBar`的详细信息，请参阅文章[MFC 工具栏实现](../../mfc/mfc-toolbar-implementation.md)和[技术说明31：控件条](../../mfc/tn031-control-bars.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CToolBar`

## <a name="requirements"></a>要求

**标头：** afxext。h

##  <a name="commandtoindex"></a>CToolBar：： CommandToIndex

此成员函数返回第一个工具栏按钮的索引，从位置0开始，其命令 ID 与 `nIDFind`匹配。

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>parameters

*nIDFind*<br/>
工具栏按钮的命令 ID。

### <a name="return-value"></a>返回值

按钮的索引; 如果没有给定的命令 ID，则为-1。

##  <a name="create"></a>CToolBar：： Create

此成员函数创建 Windows 工具栏（子窗口），并将其与 `CToolBar` 对象相关联。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>parameters

*pParentWnd*<br/>
指向作为工具栏父级的窗口的指针。

*dwStyle*<br/>
工具栏样式。 支持的其他工具栏样式包括：

- CBRS_TOP 控件条位于框架窗口的顶部。

- CBRS_BOTTOM 控件条位于框架窗口的底部。

- 调整父级大小时，不会重新定位 CBRS_NOALIGN 控件条。

- CBRS_TOOLTIPS 控件条显示工具提示。

- CBRS_SIZE_DYNAMIC 控件条是动态的。

- CBRS_SIZE_FIXED 控制条是固定的。

- CBRS_FLOATING 控件条浮动。

- CBRS_FLYBY 状态栏显示有关按钮的信息。

- 不向用户显示 CBRS_HIDE_INPLACE 控件条。

*nID*<br/>
工具栏的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

它还将工具栏高度设置为默认值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]

##  <a name="createex"></a>CToolBar：： CreateEx

调用此函数可创建 Windows 工具栏（子窗口），并将其与 `CToolBar` 对象相关联。

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = TBSTYLE_FLAT,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_ALIGN_TOP,
    CRect rcBorders = CRect(
    0,
    0,
    0,
    0),
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>parameters

*pParentWnd*<br/>
指向作为工具栏父级的窗口的指针。

*dwCtrlStyle*<br/>
用于创建嵌入[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)对象的其他样式。 默认情况下，此值设置为 TBSTYLE_FLAT。 有关工具栏样式的完整列表，请参阅*dwStyle*。

*dwStyle*<br/>
工具栏样式。 有关适当样式的列表，请参阅 Windows SDK 中的[工具栏控件和按钮样式](/windows/win32/Controls/toolbar-control-and-button-styles)。

*rcBorders*<br/>
一个[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，该对象定义工具栏窗口边框的宽度。 默认情况下，这些边框设置为0，0，0，0，从而导致工具栏窗口不包含边框。

*nID*<br/>
工具栏的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

它还将工具栏高度设置为默认值。

如果在创建嵌入的工具栏控件期间需要提供某些样式，请使用 `CreateEx`，而不是[创建](#create)。 例如，将*dwCtrlStyle*设置为 TBSTYLE_FLAT &#124; TBSTYLE_TRANSPARENT 创建与 Internet Explorer 4 工具栏类似的工具栏。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]

##  <a name="ctoolbar"></a>CToolBar：： CToolBar

此成员函数构造 `CToolBar` 对象并设置默认大小。

```
CToolBar();
```

### <a name="remarks"></a>备注

调用[create](#create)成员函数以创建工具栏窗口。

##  <a name="getbuttoninfo"></a>CToolBar：： GetButtonInfo

此成员函数在 NIndex 指定的位置检索工具栏按钮或分隔符的控件 ID、样式和图像索引 *。*

```
void GetButtonInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& iImage) const;
```

### <a name="parameters"></a>parameters

*nIndex*<br/>
要检索其信息的工具栏按钮或分隔符的索引。

*nID*<br/>
对 UINT 的引用，该 UINT 设置为按钮的命令 ID。

*nStyle*<br/>
对设置为按钮样式的 UINT 的引用。

*iImage*<br/>
引用设置为位图中按钮图像的索引的整数。

### <a name="remarks"></a>备注

这些值将分配给*nID*、 *nStyle*和*iImage*所引用的变量。 图像索引是图像在包含所有工具栏按钮图像的位图中的位置。 第一个图像的位置为0。

如果*nIndex*指定了分隔符，则*iImage*将设置为分隔符宽度（以像素为单位）。

##  <a name="getbuttonstyle"></a>CToolBar：： GetButtonStyle

调用此成员函数以检索工具栏上的按钮或分隔符的样式。

```
UINT GetButtonStyle(int nIndex) const;
```

### <a name="parameters"></a>parameters

*nIndex*<br/>
要检索的工具栏按钮或分隔符样式的索引。

### <a name="return-value"></a>返回值

*NIndex*指定的按钮或分隔符的样式。

### <a name="remarks"></a>备注

按钮的样式确定按钮的显示方式以及它如何响应用户输入。 有关按钮样式的示例，请参阅[SetButtonStyle](#setbuttonstyle) 。

##  <a name="getbuttontext"></a>CToolBar：： GetButtonText

调用此成员函数以检索按钮上显示的文本。

```
CString GetButtonText(int nIndex) const;

void GetButtonText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>parameters

*nIndex*<br/>
要检索的文本的索引。

*rString*<br/>
对[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象的引用，该对象将包含要检索的文本。

### <a name="return-value"></a>返回值

一个包含按钮文本的 `CString` 对象。

### <a name="remarks"></a>备注

此成员函数的第二种形式使用字符串文本填充 `CString` 对象。

##  <a name="getitemid"></a>CToolBar：： GetItemID

此成员函数返回*nIndex*指定的按钮或分隔符的命令 ID。

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>parameters

*nIndex*<br/>
要检索其 ID 的项的索引。

### <a name="return-value"></a>返回值

*NIndex*指定的按钮或分隔符的命令 ID。

### <a name="remarks"></a>备注

分隔符返回 ID_SEPARATOR。

##  <a name="getitemrect"></a>CToolBar：： GetItemRect

此成员函数将*lpRect*中包含的地址与*nIndex*指定的按钮或分隔符坐标一起填充的 `RECT` 结构。

```
virtual void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>parameters

*nIndex*<br/>
要检索其矩形坐标的项（按钮或分隔符）的索引。

*lpRect*<br/>
将包含项坐标的[RECT](/windows/win32/api/windef/ns-windef-rect)结构的地址。

### <a name="remarks"></a>备注

坐标以像素为单位，相对于工具栏的左上角。

使用 `GetItemRect` 获取要替换为组合框或其他控件的分隔符的坐标。

### <a name="example"></a>示例

  请参阅[CToolBar：： SetSizes](#setsizes)的示例。

##  <a name="gettoolbarctrl"></a>CToolBar：： GetToolBarCtrl

此成员函数允许直接访问基础公共控件。

```
CToolBarCtrl& GetToolBarCtrl() const;
```

### <a name="return-value"></a>返回值

对 `CToolBarCtrl` 对象的引用。

### <a name="remarks"></a>备注

使用 `GetToolBarCtrl` 利用 Windows 工具栏公共控件的功能，并利用支持[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)为工具栏自定义提供的功能。

有关使用公共控件的详细信息，请参阅文章 Windows SDK 中的[控件](../../mfc/controls-mfc.md)和[公共控件](/windows/win32/Controls/common-controls-intro)。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]

##  <a name="loadbitmap"></a>CToolBar：： LoadBitmap

调用此成员函数以加载 `lpszResourceName` 或 `nIDResource`指定的位图。

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>parameters

*lpszResourceName*<br/>
一个指针，指向要加载的位图的资源名称。

*nIDResource*<br/>
要加载的位图的资源 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

位图应为每个工具栏按钮包含一个图像。 如果图像的大小不是标准大小（16像素宽，高15像素），请调用[SetSizes](#setsizes)来设置按钮大小和图像。

> [!WARNING]
> `CToolBar` 支持最多具有16种颜色的位图。 在将图像加载到工具栏编辑器时，Visual Studio 会自动将图像转换为16色位图（如有必要），并在图像转换后显示警告消息。 如果你使用的图像的颜色超过16个（使用外部编辑器来编辑图像），则应用程序可能会意外地表现。

##  <a name="loadtoolbar"></a>CToolBar：： LoadToolBar

调用此成员函数以加载*lpszResourceName*或*nIDResource*指定的工具栏。

```
BOOL LoadToolBar(LPCTSTR lpszResourceName);
BOOL LoadToolBar(UINT nIDResource);
```

### <a name="parameters"></a>parameters

*lpszResourceName*<br/>
一个指针，指向要加载的工具栏的资源名称。

*nIDResource*<br/>
要加载的工具栏的资源 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

有关创建工具栏资源的详细信息，请参阅中的[工具栏编辑器](../../windows/toolbar-editor.md)。

### <a name="example"></a>示例

  请参阅[CToolBar：： CreateEx](#createex)的示例。

##  <a name="setbitmap"></a>CToolBar：： SetBitmap

调用此成员函数以设置工具栏的位图图像。

```
BOOL SetBitmap(HBITMAP hbmImageWell);
```

### <a name="parameters"></a>parameters

*hbmImageWell*<br/>
与工具栏关联的位图图像的句柄。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

例如，在用户对更改按钮操作的文档执行操作后，调用 `SetBitmap` 更改位图图像。

##  <a name="setbuttoninfo"></a>CToolBar：： SetButtonInfo

调用此成员函数以设置按钮的命令 ID、样式和图像编号。

```
void SetButtonInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int iImage);
```

### <a name="parameters"></a>parameters

*nIndex*<br/>
要为其设置信息的按钮或分隔符的从零开始的索引。

*nID*<br/>
按钮的命令 ID 设置为的值。

*nStyle*<br/>
新的按钮样式。 支持以下按钮样式：

- TBBS_BUTTON 标准按键（默认值）

- TBBS_SEPARATOR 分隔符

- TBBS_CHECKBOX 自动复选框按钮

- TBBS_GROUP 标记一组按钮的开头

- TBBS_CHECKGROUP 标记一组复选框按钮的开头

- TBBS_DROPDOWN 创建下拉列表按钮。

- TBBS_AUTOSIZE 按钮的宽度将根据按钮的文本而不是图像的大小进行计算。

- TBBS_NOPREFIX 按钮文本将没有关联的加速器前缀。

*iImage*<br/>
位图中按钮图像的新索引。

### <a name="remarks"></a>备注

对于具有 TBBS_SEPARATOR 样式的分隔符，此函数将分隔符的宽度（以像素为单位）设置为存储在*iImage*中的值。

> [!NOTE]
>  还可以使用*nStyle*参数设置按钮状态;不过，由于按钮状态由[ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui)处理程序控制，因此使用 `SetButtonInfo` 设置的任何状态都将在下一次空闲处理过程中丢失。 有关详细信息，请参阅[如何更新用户界面对象](../../mfc/how-to-update-user-interface-objects.md)和[TN031：控件条](../../mfc/tn031-control-bars.md)。

有关位图图像和按钮的详细信息，请参阅[CToolBar](../../mfc/reference/ctoolbar-class.md)概述 and [CToolBar：： LoadBitmap](#loadbitmap)。

##  <a name="setbuttons"></a>CToolBar：： SetButtons

此成员函数将每个工具栏按钮的命令 ID 设置为数组*lpIDArray*的相应元素所指定的值。

```
BOOL SetButtons(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>parameters

*lpIDArray*<br/>
指向命令 Id 的数组的指针。 它可以为 NULL，以分配空按钮。

*nIDCount*<br/>
*LpIDArray*指向的数组中的元素数。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

如果数组的元素具有 ID_SEPARATOR 的值，则会在工具栏的相应位置创建分隔符。 此函数还将每个按钮的样式设置为 TBBS_BUTTON，每个分隔符的样式为 TBBS_SEPARATOR，并为每个按钮指定一个图像索引。 图像索引指定按钮图像在位图中的位置。

不需要考虑位图中的分隔符，因为此函数不为分隔符分配图像索引。 如果工具栏上的按钮的位置为0、1和3，并且位置为2，则位图中位置0、1和2的图像将分别分配给位置分别为0、1和3的按钮。

如果*lpIDArray*为 NULL，则此函数为*nIDCount*所指定的项数分配空间。 使用[SetButtonInfo](#setbuttoninfo)设置每个项的属性。

##  <a name="setbuttonstyle"></a>CToolBar：： SetButtonStyle

调用此成员函数以设置按钮或分隔符的样式，或设置为组按钮。

```
void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>parameters

*nIndex*<br/>
要设置其信息的按钮或分隔符的索引。

*nStyle*<br/>
按钮样式。 支持以下按钮样式：

- TBBS_BUTTON 标准按键（默认值）

- TBBS_SEPARATOR 分隔符

- TBBS_CHECKBOX 自动复选框按钮

- TBBS_GROUP 标记一组按钮的开头

- TBBS_CHECKGROUP 标记一组复选框按钮的开头

- TBBS_DROPDOWN 创建下拉列表按钮

- TBBS_AUTOSIZE 按钮的宽度将根据按钮的文本而不是图像的大小进行计算

- TBBS_NOPREFIX 按钮文本将没有关联的加速器前缀

### <a name="remarks"></a>备注

按钮的样式确定按钮的显示方式以及它如何响应用户输入。

在调用 `SetButtonStyle`之前，调用[GetButtonStyle](#getbuttonstyle)成员函数以检索按钮或分隔符样式。

> [!NOTE]
>  还可以使用*nStyle*参数设置按钮状态;不过，由于按钮状态由[ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui)处理程序控制，因此使用 `SetButtonStyle` 设置的任何状态都将在下一次空闲处理过程中丢失。 有关详细信息，请参阅[如何更新用户界面对象](../../mfc/how-to-update-user-interface-objects.md)和[TN031：控件条](../../mfc/tn031-control-bars.md)。

##  <a name="setbuttontext"></a>CToolBar：： SetButtonText

调用此函数可设置按钮上的文本。

```
BOOL SetButtonText(
    int nIndex,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>parameters

*nIndex*<br/>
要设置其文本的按钮的索引。

*lpszText*<br/>
指向要在按钮上设置的文本。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

  请参阅[CToolBar：： GetToolBarCtrl](#gettoolbarctrl)的示例。

##  <a name="setheight"></a>CToolBar：： SetHeight

此成员函数将工具栏的高度设置为*cyHeight*中指定的值（以像素为单位）。

```
void SetHeight(int cyHeight);
```

### <a name="parameters"></a>parameters

*cyHeight*<br/>
工具栏的高度（以像素为单位）。

### <a name="remarks"></a>备注

调用[SetSizes](#setsizes)后，使用此成员函数替代标准工具栏高度。 如果高度太小，按钮将在底部进行裁剪。

如果未调用此函数，则框架将使用按钮的大小来确定工具栏的高度。

##  <a name="setsizes"></a>CToolBar：： SetSizes

调用此成员函数以将工具栏按钮设置为在*sizeButton*中指定的大小（以像素为单位）。

```
void SetSizes(
    SIZE sizeButton,
    SIZE sizeImage);
```

### <a name="parameters"></a>parameters

*sizeButton*<br/>
每个按钮的大小（以像素为单位）。

*sizeImage*<br/>
每个图像的大小（以像素为单位）。

### <a name="remarks"></a>备注

*SizeImage*参数必须包含工具栏位图中图像的大小（以像素为单位）。 *SizeButton*中的维度必须足以容纳图像并增加7像素宽和6像素高度。 此函数还将工具栏高度设置为适合这些按钮。

仅对不遵循针对按钮和图像大小的*软件设计建议的 Windows 界面指南*的工具栏调用此成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 示例 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 DOCKTOOL](../../overview/visual-cpp-samples.md)<br/>
[CControlBar Class](../../mfc/reference/ccontrolbar-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl 类](../../mfc/reference/ctoolbarctrl-class.md)<br/>
[CControlBar Class](../../mfc/reference/ccontrolbar-class.md)
