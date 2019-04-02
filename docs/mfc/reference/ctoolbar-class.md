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
ms.openlocfilehash: aa49ebed2d48d9818c2d39ae4894d8caf1fbbf81
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2019
ms.locfileid: "58773133"
---
# <a name="ctoolbar-class"></a>CToolBar 类

具有一行位图化按钮和可选分隔符的控件条。

## <a name="syntax"></a>语法

```
class CToolBar : public CControlBar
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CToolBar::CToolBar](#ctoolbar)|构造 `CToolBar` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CToolBar::CommandToIndex](#commandtoindex)|返回与给定的命令 ID 的按钮的索引|
|[CToolBar::Create](#create)|创建 Windows 工具栏并将其附加到`CToolBar`对象。|
|[CToolBar::CreateEx](#createex)|创建`CToolBar`具有其他样式的嵌入对象`CToolBarCtrl`对象。|
|[CToolBar::GetButtonInfo](#getbuttoninfo)|检索 ID、 样式和一个按钮的图像数。|
|[CToolBar::GetButtonStyle](#getbuttonstyle)|检索一个按钮的样式。|
|[CToolBar::GetButtonText](#getbuttontext)|检索将在按钮显示的文本。|
|[CToolBar::GetItemID](#getitemid)|返回按钮或分隔符中的给定索引处的命令的 ID。|
|[CToolBar::GetItemRect](#getitemrect)|检索给定索引处的项的显示矩形。|
|[CToolBar::GetToolBarCtrl](#gettoolbarctrl)|允许直接访问基础公共控件。|
|[CToolBar::LoadBitmap](#loadbitmap)|加载包含位图按钮图像的位图。|
|[CToolBar::LoadToolBar](#loadtoolbar)|加载使用资源编辑器创建工具栏资源。|
|[CToolBar::SetBitmap](#setbitmap)|设置一个位图化图像。|
|[CToolBar::SetButtonInfo](#setbuttoninfo)|设置 ID、 样式和一个按钮的图像数。|
|[CToolBar::SetButtons](#setbuttons)|设置按钮样式和的位图中的按钮图像的索引。|
|[CToolBar::SetButtonStyle](#setbuttonstyle)|将按钮样式设置。|
|[CToolBar::SetButtonText](#setbuttontext)|在按钮上设置将显示的文本。|
|[CToolBar::SetHeight](#setheight)|设置工具栏的高度。|
|[CToolBar::SetSizes](#setsizes)|设置按钮和其位图的大小。|

## <a name="remarks"></a>备注

这些按钮可以像普通按钮、 复选框按钮或单选按钮。 `CToolBar` 对象是通常嵌入的框架窗口对象派生自类成员[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)。

[CToolBar::GetToolBarCtrl](#gettoolbarctrl)，成员函数新增到 MFC 4.0，让您充分利用自定义工具栏和其他功能的 Windows 公共控件的支持。 `CToolBar` 成员函数为您提供的大多数 Windows 公共控件; 功能但是，在调用`GetToolBarCtrl`，您可以为您的工具栏甚至多个 Windows 95/98 工具栏的特征。 当您调用`GetToolBarCtrl`，它将返回到引用`CToolBarCtrl`对象。 请参阅[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)有关设计使用 Windows 公共控件的工具栏的详细信息。 有关公共控件的更多常规信息，请参阅[公共控件](/windows/desktop/Controls/common-controls-intro)Windows SDK 中。

Visual c + + 提供了两个方法，以创建工具栏。 若要创建工具栏资源使用资源编辑器，请执行以下步骤：

1. 创建工具栏资源。

1. 构造 `CToolBar` 对象。

1. 调用[创建](#create)(或[CreateEx](#createex)) 函数来创建 Windows 工具栏，并将其附加到`CToolBar`对象。

1. 调用[LoadToolBar](#loadtoolbar)加载工具栏资源。

否则，请执行以下步骤：

1. 构造 `CToolBar` 对象。

1. 调用[创建](#create)(或[CreateEx](#createex)) 函数来创建 Windows 工具栏，并将其附加到`CToolBar`对象。

1. 调用[LoadBitmap](#loadbitmap)加载包含工具栏按钮图像的位图。

1. 调用[SetButtons](#setbuttons)设置按钮样式并将每个按钮与在位图中的图像相关联。

在工具栏中的所有按钮图像是都来自一个位图，其中必须包含一个图像可查看每个按钮。 所有映像必须都是相同的大小;默认值为 16 像素宽、 高 15 像素。 映像必须在位图中的并排显示。

`SetButtons`函数将指针传递到的控件 Id 和一个整数，指定数组中的元素数的数组。 该函数将每个按钮的 ID 设置为数组的相应元素的值并将每个按钮分配图像索引，它指定在位图中的按钮的图像的位置。 如果数组元素具有值 ID_SEPARATOR，没有图像的索引分配。

在位图中图像的顺序通常是在其中绘制它们在屏幕上，但你可以使用的顺序[SetButtonInfo](#setbuttoninfo)函数可更改图像顺序和绘制顺序之间的关系。

在工具栏中的所有按钮都都具有相同大小。 根据所使用的默认值是 24 x 22 像素*面向软件设计 Windows 界面指南*。 图像和按钮尺寸之间的任何额外空间用于构成在图像周围的边框。

每个按钮有一个映像。 各种按钮状态，然后从该映像生成的样式 （按下向上、 向下键，已禁用、 已禁用，并不确定）。 虽然位图可在任何颜色，您可以获得最佳结果与中的黑色而种灰色底纹的图像。

> [!WARNING]
> `CToolBar` 支持最多包含 16 种颜色的位图。 当工具栏编辑器中加载图像时，Visual Studio 自动将图像转换为 16 色位图，如有必要，并显示一条警告消息，如果映像已转换。 如果具有多个 16 种颜色 （使用外部编辑器来编辑映像） 使用的映像，该应用程序可能会出现意外行为。

默认情况下，工具栏按钮模拟按键。 但是，复选框按钮或单选按钮，还可以模拟工具栏按钮。 复选框按钮有三种状态： 已检查、 已清除，并且不确定。 单选按钮都有只有两种状态： 选中和清除。

若要设置的单个按钮或分隔符样式不指向数组的情况下，调用[GetButtonStyle](#getbuttonstyle)来检索该样式，，然后调用[SetButtonStyle](#setbuttonstyle)而不是`SetButtons`。 `SetButtonStyle` 如果想要在运行时更改按钮的样式，则是最有用。

若要将分配要在按钮上显示的文本，请调用[GetButtonText](#getbuttontext)若要检索的文本以显示在按钮，然后调用[SetButtonText](#setbuttontext)以设置的文本。

若要创建的复选框按钮、 将其分配样式 TBBS_CHECKBOX 或使用`CCmdUI`对象的`SetCheck`ON_UPDATE_COMMAND_UI 处理程序中的成员函数。 调用`SetCheck`某个按钮将变成复选框按钮。 传递`SetCheck`参数为 0 的未选中，1 表示选中，或 2 的不确定。

若要创建一个单选按钮，调用[CCmdUI](../../mfc/reference/ccmdui-class.md)对象的[SetRadio](../../mfc/reference/ccmdui-class.md#setradio) ON_UPDATE_COMMAND_UI 处理程序中的成员函数。 传递`SetRadio`未选中或签入的非零值为 0 的参数。 为了提供单选按钮组的互斥行为，必须在组中具有所有按钮 ON_UPDATE_COMMAND_UI 处理的程序。

有关使用的详细信息`CToolBar`，请参阅文章[MFC 工具栏实现](../../mfc/mfc-toolbar-implementation.md)和[技术说明 31:控件条](../../mfc/tn031-control-bars.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CToolBar`

## <a name="requirements"></a>要求

**标头：** afxext.h

##  <a name="commandtoindex"></a>  CToolBar::CommandToIndex

此成员函数返回的第一个工具栏按钮，起始位置 0，其命令 ID 匹配的索引`nIDFind`。

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>参数

*nIDFind*<br/>
工具栏按钮的命令 ID。

### <a name="return-value"></a>返回值

该索引的按钮，则为-1 如果按钮没有给定的命令 id。

##  <a name="create"></a>  CToolBar::Create

此成员函数创建一个 Windows 工具栏 （子窗口），并将其与`CToolBar`对象。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>参数

*pParentWnd*<br/>
为工具栏的父窗口的指针。

*dwStyle*<br/>
Styl toolbar。 支持的其他工具栏样式是：

- CBRS_TOP 控件条是在框架窗口的顶部。

- CBRS_BOTTOM 控件条是在框架窗口的底部。

- 父级重设大小时，CBRS_NOALIGN 控件栏不会重新定位。

- CBRS_TOOLTIPS 控件栏会显示工具提示。

- CBRS_SIZE_DYNAMIC 控件栏是动态的。

- CBRS_SIZE_FIXED 控件条被固定。

- 浮动 CBRS_FLOATING 控件条。

- CBRS_FLYBY 状态栏会显示按钮的信息。

- 不会向用户显示 CBRS_HIDE_INPLACE 控件条。

*nID*<br/>
工具栏的子窗口 id。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

它还设置为默认值的工具栏高度。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]

##  <a name="createex"></a>  CToolBar::CreateEx

调用此函数可创建一个 Windows 工具栏 （子窗口），并将其与`CToolBar`对象。

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

### <a name="parameters"></a>参数

*pParentWnd*<br/>
为工具栏的父窗口的指针。

*dwCtrlStyle*<br/>
创建嵌入其他样式[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)对象。 默认情况下，此值设置为 TBSTYLE_FLAT。 Toolbar 样式的完整列表，请参阅*dwStyle*。

*dwStyle*<br/>
Styl toolbar。 请参阅[工具栏控件和按钮样式](/windows/desktop/Controls/toolbar-control-and-button-styles)Windows SDK for 适当样式的列表中。

*rcBorders*<br/>
一个[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，用于定义工具栏窗口边框的宽度。 默认情况下，从而产生与无边框工具栏窗口中将这些边框设 0,0,0,0。

*nID*<br/>
工具栏的子窗口 id。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

它还设置为默认值的工具栏高度。

使用`CreateEx`，而不是[创建](#create)，当需要 embedded 的工具条控件的创建期间提供特定的样式。 例如，设置*dwCtrlStyle* TBSTYLE_FLAT 到&#124;TBSTYLE_TRANSPARENT 创建类似于 Internet Explorer 4 工具栏的工具栏。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]

##  <a name="ctoolbar"></a>  CToolBar::CToolBar

此成员函数将构造`CToolBar`对象并设置默认大小。

```
CToolBar();
```

### <a name="remarks"></a>备注

调用[创建](#create)成员函数来创建工具栏窗口。

##  <a name="getbuttoninfo"></a>  CToolBar::GetButtonInfo

此成员函数检索控件 ID、 样式和工具栏按钮或分隔符，在指定的位置的映像索引*nIndex。*

```
void GetButtonInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& iImage) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
工具栏按钮或分隔符的信息是要检索的索引。

*nID*<br/>
设置按钮的命令 ID 为 uint 的引用。

*nStyle*<br/>
设置按钮的样式为 uint 的引用。

*iImage*<br/>
对一个整数，它设置为位图中的按钮的图像的索引引用。

### <a name="remarks"></a>备注

这些值分配给引用的变量*nID*， *nStyle*，并*iImage*。 映像索引是中包含的所有工具栏按钮的图像的位图图像的位置。 第一幅图像位于位置 0。

如果*nIndex*指定一个分隔符*iImage*设为以像素为单位的分隔符宽度。

##  <a name="getbuttonstyle"></a>  CToolBar::GetButtonStyle

调用此成员函数以检索按钮或在工具栏上的分隔符的样式。

```
UINT GetButtonStyle(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要检索的工具栏按钮或分隔符样式的索引。

### <a name="return-value"></a>返回值

按钮或由指定的分隔符的样式*nIndex*。

### <a name="remarks"></a>备注

确定按钮的样式的按钮的显示方式以及它如何响应用户输入。 请参阅[SetButtonStyle](#setbuttonstyle)有关按钮样式的示例。

##  <a name="getbuttontext"></a>  CToolBar::GetButtonText

调用此成员函数以检索在按钮显示的文本。

```
CString GetButtonText(int nIndex) const;

void GetButtonText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要检索的文本索引。

*rString*<br/>
对引用[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象，它将包含要检索的文本。

### <a name="return-value"></a>返回值

一个`CString`对象，其中包含的按钮文本。

### <a name="remarks"></a>备注

此成员的第二种形式函数填充`CString`具有字符串文本对象。

##  <a name="getitemid"></a>  CToolBar::GetItemID

此成员函数返回的命令 ID 的按钮或由指定的分隔符*nIndex*。

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要检索其 ID 的项的索引。

### <a name="return-value"></a>返回值

命令 ID 的按钮或由指定的分隔符*nIndex*。

### <a name="remarks"></a>备注

分隔符返回 ID_SEPARATOR。

##  <a name="getitemrect"></a>  CToolBar::GetItemRect

此成员函数将填充`RECT`结构中包含其地址*lpRect*的按钮或分隔符由指定的坐标*nIndex*。

```
virtual void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要从中检索其矩形坐标的项 （按钮或分隔符） 的索引。

*lpRect*<br/>
地址[RECT](/windows/desktop/api/windef/ns-windef-tagrect)结构，它将包含项目的坐标。

### <a name="remarks"></a>备注

坐标是工具栏的相对于左上角以像素为单位。

使用`GetItemRect`若要获取你想要替换为一个组合框或其他控件的分隔符的坐标。

### <a name="example"></a>示例

  有关示例，请参阅[CToolBar::SetSizes](#setsizes)。

##  <a name="gettoolbarctrl"></a>  CToolBar::GetToolBarCtrl

此成员函数允许直接访问基础公共控件。

```
CToolBarCtrl& GetToolBarCtrl() const;
```

### <a name="return-value"></a>返回值

对 `CToolBarCtrl` 对象的引用。

### <a name="remarks"></a>备注

使用`GetToolBarCtrl`充分利用 Windows 工具栏公共控件的功能并利用支持[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)提供用于自定义工具栏。

有关使用公共控件的详细信息，请参阅文章[控件](../../mfc/controls-mfc.md)并[公共控件](/windows/desktop/Controls/common-controls-intro)Windows SDK 中。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]

##  <a name="loadbitmap"></a>  CToolBar::LoadBitmap

调用此成员函数以加载指定的位图`lpszResourceName`或`nIDResource`。

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>参数

*lpszResourceName*<br/>
指向要加载的位图的资源名称。

*nIDResource*<br/>
资源 ID 的位图加载。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

位图应包含一个图像可查看每个工具栏按钮。 如果图像不是标准大小 （16 个像素宽和高 15 像素） 的调用[SetSizes](#setsizes)设置按钮大小和其映像。

> [!WARNING]
> `CToolBar` 支持最多包含 16 种颜色的位图。 当工具栏编辑器中加载图像时，Visual Studio 自动将图像转换为 16 色位图，如有必要，并显示一条警告消息，如果映像已转换。 如果具有多个 16 种颜色 （使用外部编辑器来编辑映像） 使用的映像，该应用程序可能会出现意外行为。

##  <a name="loadtoolbar"></a>  CToolBar::LoadToolBar

调用此成员函数以加载指定的工具栏*lpszResourceName*或*nIDResource*。

```
BOOL LoadToolBar(LPCTSTR lpszResourceName);
BOOL LoadToolBar(UINT nIDResource);
```

### <a name="parameters"></a>参数

*lpszResourceName*<br/>
为工具栏要加载的资源名称的指针。

*nIDResource*<br/>
资源 ID 工具栏的加载。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

请参阅[工具栏编辑器](../../windows/toolbar-editor.md)中有关创建工具栏资源的详细信息。

### <a name="example"></a>示例

  有关示例，请参阅[CToolBar::CreateEx](#createex)。

##  <a name="setbitmap"></a>  CToolBar::SetBitmap

调用此成员函数可设置工具栏的位图图像。

```
BOOL SetBitmap(HBITMAP hbmImageWell);
```

### <a name="parameters"></a>参数

*hbmImageWell*<br/>
与工具栏关联的位图的句柄。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

例如，调用`SetBitmap`用户更改按钮的操作的文档上执行的操作后更改位图化图像。

##  <a name="setbuttoninfo"></a>  CToolBar::SetButtonInfo

调用此成员函数可设置按钮的命令 ID、 样式和图像数。

```
void SetButtonInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int iImage);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
分隔符为设置信息的按钮的从零开始的索引。

*nID*<br/>
为其设置按钮的命令 ID 的值。

*nStyle*<br/>
新按钮样式。 支持以下按钮样式：

- TBBS_BUTTON 标准按键 （默认值）

- TBBS_SEPARATOR 分隔符

- TBBS_CHECKBOX 自动复选框按钮

- TBBS_GROUP 标记开头的一组按钮

- TBBS_CHECKGROUP 标记开头的一组复选框按钮

- TBBS_DROPDOWN 创建下拉列表按钮。

- 将计算按钮的宽度 TBBS_AUTOSIZE 基于不上图像的大小的按钮的文本。

- TBBS_NOPREFIX 按钮文本将不具有与之关联的加速器前缀。

*iImage*<br/>
位图中的按钮的图像的新索引。

### <a name="remarks"></a>备注

样式 TBBS_SEPARATOR 的分隔符为此函数设置分隔符的宽度 （像素） 中存储的值为*iImage*。

> [!NOTE]
>  您还可以设置使用的按钮状态*nStyle*参数; 但是，因为按钮状态由控制[ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui)处理程序中，任何状态使用设置`SetButtonInfo`都将丢失在下一步的空闲处理。 请参阅[如何更新用户界面对象](../../mfc/how-to-update-user-interface-objects.md)和[TN031:控件条](../../mfc/tn031-control-bars.md)有关详细信息。

位图图像和按钮的信息，请参阅[CToolBar](../../mfc/reference/ctoolbar-class.md)概述和[CToolBar::LoadBitmap](#loadbitmap)。

##  <a name="setbuttons"></a>  CToolBar::SetButtons

此成员函数将每个工具栏按钮的命令 ID 设置为指定数组的相应元素的值*lpIDArray*。

```
BOOL SetButtons(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>参数

*lpIDArray*<br/>
命令 Id 的数组的指针。 它可以为 NULL，以分配空的按钮。

*nIDCount*<br/>
指向数组中的元素数目*lpIDArray*。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

如果数组的元素具有值 ID_SEPARATOR，分隔符被创建工具栏的对应位置。 此函数还将每个按钮的样式设置为 TBBS_BUTTON 和每个分隔符样式应用到 TBBS_SEPARATOR，并将图像索引分配给每个按钮。 映像索引指定位图中的按钮的图像的位置。

不需要考虑的位图中的分隔符，因为此函数不会分配分隔符的图像索引。 如果您的工具栏按钮位于位置 0，1 和 3 和一个分隔符在位置 2，分别位于位置 0、 1 和 2 中为位图图像分配给各个按钮，在位置 0、 1 和 3，分别。

如果*lpIDArray*为 NULL，此函数为指定的项目数分配空间*nIDCount*。 使用[SetButtonInfo](#setbuttoninfo)以设置每个项的属性。

##  <a name="setbuttonstyle"></a>  CToolBar::SetButtonStyle

调用此成员函数可设置样式的按钮或分隔符，或对组按钮。

```
void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
按钮或分隔符的信息是要设置的索引。

*nStyle*<br/>
按钮样式。 支持以下按钮样式：

- TBBS_BUTTON 标准按键 （默认值）

- TBBS_SEPARATOR 分隔符

- TBBS_CHECKBOX 自动复选框按钮

- TBBS_GROUP 标记开头的一组按钮

- TBBS_CHECKGROUP 标记开头的一组复选框按钮

- TBBS_DROPDOWN 创建下拉列表按钮

- 将计算按钮的宽度 TBBS_AUTOSIZE 基于不上图像的大小的按钮的文本

- TBBS_NOPREFIX 按钮文本将不具有与之关联的加速器前缀

### <a name="remarks"></a>备注

确定按钮的样式的按钮的显示方式以及它如何响应用户输入。

然后再调用`SetButtonStyle`，调用[GetButtonStyle](#getbuttonstyle)成员函数以检索按钮或分隔符样式。

> [!NOTE]
>  您还可以设置使用的按钮状态*nStyle*参数; 但是，因为按钮状态由控制[ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui)处理程序中，任何状态使用设置`SetButtonStyle`都将丢失在下一步的空闲处理。 请参阅[如何更新用户界面对象](../../mfc/how-to-update-user-interface-objects.md)和[TN031:控件条](../../mfc/tn031-control-bars.md)有关详细信息。

##  <a name="setbuttontext"></a>  CToolBar::SetButtonText

调用此函数可设置上一个按钮的文本。

```
BOOL SetButtonText(
    int nIndex,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
其中的文本是设置的按钮的索引。

*lpszText*<br/>
指向要在按钮上设置的文本。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

  有关示例，请参阅[CToolBar::GetToolBarCtrl](#gettoolbarctrl)。

##  <a name="setheight"></a>  CToolBar::SetHeight

此成员函数设置的值，以像素为单位，在指定工具栏的高度*cyHeight*。

```
void SetHeight(int cyHeight);
```

### <a name="parameters"></a>参数

*cyHeight*<br/>
以像素为单位工具栏的高度。

### <a name="remarks"></a>备注

在调用[SetSizes](#setsizes)，使用此成员函数以重写的标准工具栏高度。 如果高度太小，将在底部剪辑按钮。

如果未调用此函数，该框架将使用按钮的大小来确定工具栏高度。

##  <a name="setsizes"></a>  CToolBar::SetSizes

调用此成员函数可设置的大小，以像素为单位，在指定工具栏的按钮*sizeButton*。

```
void SetSizes(
    SIZE sizeButton,
    SIZE sizeImage);
```

### <a name="parameters"></a>参数

*sizeButton*<br/>
以像素为单位的每个按钮的大小。

*sizeImage*<br/>
以像素为单位的每个图像的大小。

### <a name="remarks"></a>备注

*SizeImage*参数必须包含以像素为单位的工具栏的位图中图像的大小。 中的维度*sizeButton*必须足以容纳图像加 7 像素额外的宽度和高度额外的 6 个像素。 此函数还将设置工具栏的高度以适应这些按钮。

调用此成员函数仅对工具栏不遵循*面向软件设计 Windows 界面指南*大小的按钮和图像的建议。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]

## <a name="see-also"></a>请参阅

[MFC 示例 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[MFC 示例 DOCKTOOL](../../overview/visual-cpp-samples.md)<br/>
[CControlBar 类](../../mfc/reference/ccontrolbar-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl 类](../../mfc/reference/ctoolbarctrl-class.md)<br/>
[CControlBar 类](../../mfc/reference/ccontrolbar-class.md)
