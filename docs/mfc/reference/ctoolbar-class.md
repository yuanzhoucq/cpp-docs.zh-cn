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
ms.openlocfilehash: cbb2d1bb797737a14e9728d339305bf9c371b543
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752211"
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
|[CToolBar：CToolBar](#ctoolbar)|构造 `CToolBar` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CToolbar：：命令索引](#commandtoindex)|返回具有给定命令 ID 的按钮的索引。|
|[CToolBar：：创建](#create)|创建 Windows 工具栏并将其附加到`CToolBar`对象。|
|[CToolBar：：创建Ex](#createex)|为`CToolBar`嵌入`CToolBarCtrl`对象创建具有其他样式的对象。|
|[CToolBar：获取按钮信息](#getbuttoninfo)|检索按钮的 ID、样式和图像编号。|
|[CToolBar：获取按钮样式](#getbuttonstyle)|检索按钮的样式。|
|[CToolBar：获取按钮文本](#getbuttontext)|检索将显示在按钮上的文本。|
|[CToolBar：获取项目ID](#getitemid)|在给定索引处返回按钮或分隔符的命令 ID。|
|[CToolBar：获取项目重新完成](#getitemrect)|检索给定索引处项的显示矩形。|
|[CToolBar：：获取工具栏](#gettoolbarctrl)|允许直接访问基础公共控件。|
|[CToolBar：：加载位图](#loadbitmap)|加载包含位图按钮图像的位图。|
|[CToolBar：：加载工具栏](#loadtoolbar)|加载使用资源编辑器创建的工具栏资源。|
|[CToolBar：：设置位图](#setbitmap)|设置位映射图像。|
|[CToolBar：：设置按钮信息](#setbuttoninfo)|设置按钮的 ID、样式和图像编号。|
|[CToolBar：设置按钮](#setbuttons)|设置位图中的按钮样式和按钮图像索引。|
|[CToolBar：设置按钮样式](#setbuttonstyle)|设置按钮的样式。|
|[CToolBar：：设置按钮文本](#setbuttontext)|设置将显示在按钮上的文本。|
|[CToolBar：：设置高度](#setheight)|设置工具栏的高度。|
|[CToolBar：：设置大小](#setsizes)|设置按钮的大小及其位图。|

## <a name="remarks"></a>备注

按钮可以像按钮、复选框按钮或单选按钮一样。 `CToolBar`对象通常是派生自类[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md)的帧窗口对象的嵌入成员。

[CToolBar：GetToolBarCtrl](#gettoolbarctrl)是 MFC 4.0 中新成员函数，允许您利用 Windows 通用控件对工具栏自定义和其他功能的支持。 `CToolBar`成员函数为您提供 Windows 公共控件的大部分功能;但是，当您调用`GetToolBarCtrl`时，您可以为您的工具栏提供更多 Windows 95/98 工具栏的特征。 调用`GetToolBarCtrl`时，它将返回对`CToolBarCtrl`对象的引用。 有关使用 Windows 常见控件设计工具栏的详细信息，请参阅[CToolBarCtrl。](../../mfc/reference/ctoolbarctrl-class.md) 有关常见控件的更多一般信息，请参阅 Windows SDK 中[的常见控件](/windows/win32/Controls/common-controls-intro)。

可视化C++为您提供了创建工具栏的两种方法。 要使用资源编辑器创建工具栏资源，请按照以下步骤操作：

1. 创建工具栏资源。

1. 构造 `CToolBar` 对象。

1. 调用["创建](#create)"（或[CreateEx](#createex)） 函数以创建 Windows 工具栏并将其附加到`CToolBar`对象。

1. 调用[LoadToolBar](#loadtoolbar)以加载工具栏资源。

否则，请执行以下步骤：

1. 构造 `CToolBar` 对象。

1. 调用["创建](#create)"（或[CreateEx](#createex)） 函数以创建 Windows 工具栏并将其附加到`CToolBar`对象。

1. 调用[LoadBitmap](#loadbitmap)以加载包含工具栏按钮图像的位图。

1. 调用[SetButtons](#setbuttons)以设置按钮样式，并将每个按钮与位图中的图像相关联。

工具栏中的所有按钮图像都取自一个位图，该位图必须为每个按钮包含一个图像。 所有图像的大小必须相同;默认值为 16 像素宽，高 15 像素。 图像必须并排在位图中。

函数`SetButtons`获取指向控件指示数组的指针和指定数组中元素数的整数。 该函数将每个按钮的 ID 设置到数组的相应元素的值，并为每个按钮分配一个图像索引，该索引指定按钮图像在位图中的位置。 如果数组元素的值ID_SEPARATOR，则不分配图像索引。

位图中图像的顺序通常是在屏幕上绘制图像的顺序，但您可以使用[SetButtonInfo](#setbuttoninfo)函数来更改图像顺序和绘图顺序之间的关系。

工具栏中的所有按钮大小都相同。 默认值为 24 x 22 像素，根据*Windows 界面软件设计指南*。 图像和按钮尺寸之间的任何附加空间都用于在图像周围形成边框。

每个按钮都有一个图像。 各种按钮状态和样式（按下、向上、向下、禁用、向下禁用和不确定）从该图像生成。 尽管位图可以是任何颜色，但您可以使用黑色和灰色阴影的图像获得最佳效果。

> [!WARNING]
> `CToolBar`支持最多 16 种颜色的位图。 将图像加载到工具栏编辑器中时，Visual Studio 会自动将图像转换为 16 色位图（如有必要），如果图像已转换，则显示警告消息。 如果使用具有 16 种颜色以上的图像（使用外部编辑器编辑图像），则应用程序可能会出乎意料地运行。

默认情况下，工具栏按钮会模仿按钮。 但是，工具栏按钮也可以模仿复选框按钮或单选按钮。 复选框按钮有三种状态：已选中、清除和不确定。 单选按钮只有两种状态：已选中并清除。

若要在不指向数组的情况下设置单个按钮或分隔符样式，请调用[GetButtonStyle](#getbuttonstyle)来检索该样式，然后调用[SetButtonStyle](#setbuttonstyle)而不是`SetButtons`。 `SetButtonStyle`当您想在运行时更改按钮的样式时，最有用。

要将文本指定在按钮上显示，请致电[GetButtonText](#getbuttontext)以检索显示在按钮上的文本，然后调用[SetButtonText](#setbuttontext)来设置文本。

要创建复选框按钮，请为其分配样式TBBS_CHECKBOX或在ON_UPDATE_COMMAND_UI处理程序中使用`CCmdUI`对象`SetCheck`的成员函数。 呼叫`SetCheck`将按钮转换为复选框按钮。 将`SetCheck`参数 0 表示未选中，1 表示选中，2 表示不确定。

要创建单选按钮，请从ON_UPDATE_COMMAND_UI处理程序调用[CCmdUI](../../mfc/reference/ccmdui-class.md)对象的[SetRadio](../../mfc/reference/ccmdui-class.md#setradio)成员函数。 为`SetRadio`未选中或未选中传递参数 0 或非零。 为了提供无线电组的互斥行为，您必须为组中的所有按钮ON_UPDATE_COMMAND_UI处理程序。

有关使用`CToolBar`的详细信息，请参阅文章[MFC 工具栏实现](../../mfc/mfc-toolbar-implementation.md)[和技术说明 31：控制栏](../../mfc/tn031-control-bars.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[C控制栏](../../mfc/reference/ccontrolbar-class.md)

`CToolBar`

## <a name="requirements"></a>要求

**标题：** afxext.h

## <a name="ctoolbarcommandtoindex"></a><a name="commandtoindex"></a>CToolbar：：命令索引

此成员函数返回第一个工具栏按钮的索引，从命令 ID 匹配`nIDFind`的位置 0 开始。

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>参数

*nIDFind*<br/>
工具栏按钮的命令 ID。

### <a name="return-value"></a>返回值

按钮的索引，如果没有按钮具有给定的命令 ID，则为 -1。

## <a name="ctoolbarcreate"></a><a name="create"></a>CToolBar：：创建

此成员函数创建 Windows 工具栏（子窗口），并将其与`CToolBar`对象关联。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,
    UINT nID = AFX_IDW_TOOLBAR);
```

### <a name="parameters"></a>参数

*pparentwnd*<br/>
指向工具栏的父窗口。

*dwStyle*<br/>
工具栏样式。 支持的其他工具栏样式包括：

- CBRS_TOP控制栏位于框架窗口的顶部。

- CBRS_BOTTOM控制栏位于框架窗口的底部。

- CBRS_NOALIGN调整父控件栏的大小时，不会重新定位。

- CBRS_TOOLTIPS控制栏显示工具提示。

- CBRS_SIZE_DYNAMIC控制栏是动态的。

- CBRS_SIZE_FIXED控制栏已固定。

- CBRS_FLOATING控制栏是浮动的。

- CBRS_FLYBY 状态栏显示有关按钮的信息。

- CBRS_HIDE_INPLACE控件栏不向用户显示。

*nID*<br/>
工具栏的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

它还将工具栏高度设置为默认值。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#179](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]

## <a name="ctoolbarcreateex"></a><a name="createex"></a>CToolBar：：创建Ex

调用此函数以创建 Windows 工具栏（子窗口），并将其与`CToolBar`对象关联。

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

*pparentwnd*<br/>
指向工具栏的父窗口。

*dwCtrl风格*<br/>
用于创建嵌入式[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)对象的其他样式。 默认情况下，此值设置为TBSTYLE_FLAT。 有关工具栏样式的完整列表，请参阅*dwStyle*。

*dwStyle*<br/>
工具栏样式。 有关适当样式的列表，请参阅 Windows SDK 中的[工具栏控件和按钮样式](/windows/win32/Controls/toolbar-control-and-button-styles)。

*rcBorders*<br/>
定义工具栏窗口边框宽度的[CRect](../../atl-mfc-shared/reference/crect-class.md)对象。 默认情况下，这些边框设置为 0，0，0，0，从而生成没有边框的工具栏窗口。

*nID*<br/>
工具栏的子窗口 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

它还将工具栏高度设置为默认值。

在`CreateEx`创建嵌入工具栏控件期间需要存在某些样式时，请使用 而不是[Create。](#create) 例如，将*dwCtrlStyle*设置为TBSTYLE_FLAT&#124;TBSTYLE_TRANSPARENT创建类似于 Internet Explorer 4 工具栏的工具栏。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocView#180](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]

## <a name="ctoolbarctoolbar"></a><a name="ctoolbar"></a>CToolBar：CToolBar

此成员函数构造对象`CToolBar`并设置默认大小。

```
CToolBar();
```

### <a name="remarks"></a>备注

调用["创建](#create)成员"函数以创建工具栏窗口。

## <a name="ctoolbargetbuttoninfo"></a><a name="getbuttoninfo"></a>CToolBar：获取按钮信息

此成员函数检索 nIndex 指定位置工具栏按钮或分隔符的控制 ID、样式和图像*索引。*

```cpp
void GetButtonInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& iImage) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要检索其信息的工具栏按钮或分隔符的索引。

*nID*<br/>
对设置为按钮的命令 ID 的 UINT 的引用。

*nStyle*<br/>
引用设置为按钮样式的 UINT。

*i图像*<br/>
引用设置为位图中按钮图像索引的整数。

### <a name="remarks"></a>备注

这些值分配给*nID、nStyle**nID*和*iImage*引用的变量。 图像索引是图像在位图中的位置，该位图包含所有工具栏按钮的图像。 第一个图像位于位置 0。

如果*nIndex*指定分隔符，则*iImage*设置为分隔符宽度（以像素为单位）。

## <a name="ctoolbargetbuttonstyle"></a><a name="getbuttonstyle"></a>CToolBar：获取按钮样式

调用此成员函数以检索工具栏上的按钮或分隔符的样式。

```
UINT GetButtonStyle(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要检索的工具栏按钮或分隔符样式的索引。

### <a name="return-value"></a>返回值

*nIndex*指定的按钮或分隔符的样式。

### <a name="remarks"></a>备注

按钮的样式确定按钮的显示方式以及按钮如何响应用户输入。 有关按钮样式的示例，请参阅[设置ButtonStyle。](#setbuttonstyle)

## <a name="ctoolbargetbuttontext"></a><a name="getbuttontext"></a>CToolBar：获取按钮文本

调用此成员函数以检索显示在按钮上的文本。

```
CString GetButtonText(int nIndex) const;

void GetButtonText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要检索的文本的索引。

*rString*<br/>
对包含要检索的文本的[CString](../../atl-mfc-shared/reference/cstringt-class.md)对象的引用。

### <a name="return-value"></a>返回值

包含`CString`按钮文本的对象。

### <a name="remarks"></a>备注

此成员函数的第二种形式使用字符串文本填充`CString`对象。

## <a name="ctoolbargetitemid"></a><a name="getitemid"></a>CToolBar：获取项目ID

此成员函数返回*nIndex*指定的按钮或分隔符的命令 ID。

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要检索其 ID 的项的索引。

### <a name="return-value"></a>返回值

*nIndex*指定的按钮或分隔符的命令 ID。

### <a name="remarks"></a>备注

分离器返回ID_SEPARATOR。

## <a name="ctoolbargetitemrect"></a><a name="getitemrect"></a>CToolBar：获取项目重新完成

此成员函数使用`RECT`*nIndex*指定的按钮或分隔符的坐标填充其地址包含在*lpRect*中的结构。

```
virtual void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要检索其矩形坐标的项的索引（按钮或分隔符）。

*lpRect*<br/>
将包含项坐标的[RECT](/windows/win32/api/windef/ns-windef-rect)结构的地址。

### <a name="remarks"></a>备注

坐标相对于工具栏的左上角以像素为单位。

用于`GetItemRect`获取要替换为组合框或其他控件的分隔符的坐标。

### <a name="example"></a>示例

  请参阅[CToolBar 的示例：设置大小](#setsizes)。

## <a name="ctoolbargettoolbarctrl"></a><a name="gettoolbarctrl"></a>CToolBar：：获取工具栏

此成员函数允许直接访问基础公共控件。

```
CToolBarCtrl& GetToolBarCtrl() const;
```

### <a name="return-value"></a>返回值

对 `CToolBarCtrl` 对象的引用。

### <a name="remarks"></a>备注

用于`GetToolBarCtrl`利用 Windows 工具栏通用控件的功能，并利用[CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md)提供的工具栏自定义支持。

有关使用常见控件的详细信息，请参阅 Windows SDK 中的"[控件](../../mfc/controls-mfc.md)"和["常见控件](/windows/win32/Controls/common-controls-intro)"一文。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCDocViewSDI#15](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]

## <a name="ctoolbarloadbitmap"></a><a name="loadbitmap"></a>CToolBar：：加载位图

调用此成员函数以加载 或`lpszResourceName``nIDResource`指定的位图。

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>参数

*lpsz 资源名称*<br/>
指向要加载的位图的资源名称的指针。

*nID资源*<br/>
要加载的位图的资源 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

位图应包含每个工具栏按钮的一个图像。 如果图像不是标准大小（16 像素宽，15 像素高），请调用[SetSizes](#setsizes)来设置按钮大小及其图像。

> [!WARNING]
> `CToolBar`支持最多 16 种颜色的位图。 将图像加载到工具栏编辑器中时，Visual Studio 会自动将图像转换为 16 色位图（如有必要），如果图像已转换，则显示警告消息。 如果使用具有 16 种颜色以上的图像（使用外部编辑器编辑图像），则应用程序可能会出乎意料地运行。

## <a name="ctoolbarloadtoolbar"></a><a name="loadtoolbar"></a>CToolBar：：加载工具栏

调用此成员函数以加载*lpszResourceName*或*nIDResource*指定的工具栏。

```
BOOL LoadToolBar(LPCTSTR lpszResourceName);
BOOL LoadToolBar(UINT nIDResource);
```

### <a name="parameters"></a>参数

*lpsz 资源名称*<br/>
指向要加载的工具栏的资源名称的指针。

*nID资源*<br/>
要加载的工具栏的资源 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

有关创建工具栏资源的详细信息，请参阅 中的[工具栏编辑器](../../windows/toolbar-editor.md)。

### <a name="example"></a>示例

  请参阅[CToolBar 的示例：：创建Ex](#createex)。

## <a name="ctoolbarsetbitmap"></a><a name="setbitmap"></a>CToolBar：：设置位图

调用此成员函数以设置工具栏的位图图像。

```
BOOL SetBitmap(HBITMAP hbmImageWell);
```

### <a name="parameters"></a>参数

*hbmImageWell*<br/>
与工具栏关联的位图图像的句柄。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

例如，在用户`SetBitmap`对更改按钮操作的文档执行操作后，调用更改位映射图像。

## <a name="ctoolbarsetbuttoninfo"></a><a name="setbuttoninfo"></a>CToolBar：：设置按钮信息

调用此成员函数以设置按钮的命令 ID、样式和图像编号。

```cpp
void SetButtonInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int iImage);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要为其设置信息的按钮或分隔符的零基索引。

*nID*<br/>
按钮的命令 ID 设置为的值。

*nStyle*<br/>
新的按钮样式。 支持以下按钮样式：

- TBBS_BUTTON标准按钮（默认）

- TBBS_SEPARATOR分离器

- TBBS_CHECKBOX 自动复选框按钮

- TBBS_GROUP 标记一组按钮的开始

- TBBS_CHECKGROUP 标记一组复选框按钮的开始

- TBBS_DROPDOWN 创建下拉列表按钮。

- TBBS_AUTOSIZE 按钮的宽度将根据按钮的文本而不是图像的大小进行计算。

- TBBS_NOPREFIX 按钮文本将没有与其关联的快捷键前缀。

*i图像*<br/>
位图中按钮图像的新索引。

### <a name="remarks"></a>备注

对于具有样式TBBS_SEPARATOR的分隔符，此函数将分隔符的宽度（以像素为单位）设置为存储在*iImage*中的值。

> [!NOTE]
> 您还可以使用*nStyle*参数设置按钮状态;但是，由于按钮状态由[ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui)处理程序控制，因此在下次空闲处理期间，`SetButtonInfo`您设置使用的任何状态都将丢失。 有关详细信息[，请参阅如何更新用户界面对象](../../mfc/how-to-update-user-interface-objects.md)和[TN031：控制栏](../../mfc/tn031-control-bars.md)。

有关位图图像和按钮的信息，请参阅[CToolBar](../../mfc/reference/ctoolbar-class.md)概述和[CToolBar：：LoadBitmap](#loadbitmap)。

## <a name="ctoolbarsetbuttons"></a><a name="setbuttons"></a>CToolBar：设置按钮

此成员函数将每个工具栏按钮的命令 ID 设置到数组*lpIDArray*的相应元素指定的值。

```
BOOL SetButtons(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>参数

*lpIDArray*<br/>
指向命令 ID 的数组的指针。 分配空按钮可以为 NULL。

*nIDCount*<br/>
*lpIDArray*指向的数组中的元素数。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

如果数组的元素具有值ID_SEPARATOR，则在工具栏的相应位置创建分隔符。 此函数还将每个按钮的样式设置为TBBS_BUTTON，每个分隔符的样式TBBS_SEPARATOR，并将图像索引分配给每个按钮。 图像索引指定按钮图像在位图中的位置。

不需要考虑位图中的分隔符，因为此函数不为分隔符分配图像索引。 如果工具栏在位置 0、1 和 3 处具有按钮，在位置 2 处有分隔符，则位图中位置 0、1 和 2 处的图像将分别分配给位置 0、1 和 3 处的按钮。

如果*lpIDArray*为 NULL，则此函数为*nIDCount*指定的项数分配空间。 使用[SetButtonInfo](#setbuttoninfo)设置每个项目的属性。

## <a name="ctoolbarsetbuttonstyle"></a><a name="setbuttonstyle"></a>CToolBar：设置按钮样式

调用此成员函数以设置按钮或分隔符的样式，或对按钮进行分组。

```cpp
void SetButtonStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要设置其信息的按钮或分隔符的索引。

*nStyle*<br/>
按钮样式。 支持以下按钮样式：

- TBBS_BUTTON标准按钮（默认）

- TBBS_SEPARATOR分离器

- TBBS_CHECKBOX 自动复选框按钮

- TBBS_GROUP 标记一组按钮的开始

- TBBS_CHECKGROUP 标记一组复选框按钮的开始

- TBBS_DROPDOWN 创建下拉列表按钮

- TBBS_AUTOSIZE按钮的宽度将根据按钮的文本（而不是图像的大小）计算

- TBBS_NOPREFIX 按钮文本将没有与其关联的快捷键前缀

### <a name="remarks"></a>备注

按钮的样式确定按钮的显示方式以及按钮如何响应用户输入。

在调用`SetButtonStyle`之前，调用[GetButtonStyle](#getbuttonstyle)成员函数来检索按钮或分隔符样式。

> [!NOTE]
> 您还可以使用*nStyle*参数设置按钮状态;但是，由于按钮状态由[ON_UPDATE_COMMAND_UI](message-map-macros-mfc.md#on_update_command_ui)处理程序控制，因此在下次空闲处理期间，`SetButtonStyle`您设置使用的任何状态都将丢失。 有关详细信息[，请参阅如何更新用户界面对象](../../mfc/how-to-update-user-interface-objects.md)和[TN031：控制栏](../../mfc/tn031-control-bars.md)。

## <a name="ctoolbarsetbuttontext"></a><a name="setbuttontext"></a>CToolBar：：设置按钮文本

调用此函数以设置按钮上的文本。

```
BOOL SetButtonText(
    int nIndex,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要设置其文本的按钮的索引。

*lpszText*<br/>
指向要在按钮上设置的文本。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="example"></a>示例

  请参阅[CToolBar 的示例：获取工具栏。](#gettoolbarctrl)

## <a name="ctoolbarsetheight"></a><a name="setheight"></a>CToolBar：：设置高度

此成员函数将工具栏的高度设置为*在 cyHeight*中指定的值（以像素为单位）。

```cpp
void SetHeight(int cyHeight);
```

### <a name="parameters"></a>参数

*赛高地*<br/>
工具栏的高度（以像素为单位）。

### <a name="remarks"></a>备注

调用[SetSizes](#setsizes)后，使用此成员函数覆盖标准工具栏高度。 如果高度太小，按钮将在底部被剪切。

如果未调用此功能，框架将使用按钮的大小来确定工具栏的高度。

## <a name="ctoolbarsetsizes"></a><a name="setsizes"></a>CToolBar：：设置大小

调用此成员函数将工具栏的按钮设置为大小按钮指定的*大小*（以像素为单位）。

```cpp
void SetSizes(
    SIZE sizeButton,
    SIZE sizeImage);
```

### <a name="parameters"></a>参数

*大小按钮*<br/>
每个按钮的大小（以像素为单位）。

*大小图像*<br/>
每个图像的大小（以像素为单位）。

### <a name="remarks"></a>备注

*sizeImage*参数必须包含工具栏位图中图像的大小（以像素为单位）。 *尺寸按钮*的尺寸必须足以容纳图像加上 7 像素的额外宽度和 6 像素的额外高度。 此功能还设置工具栏高度以适合按钮。

仅对未遵循*Windows 界面指南的软件设计*建议按钮和图像大小的工具栏调用此成员函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCListView#8](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]

## <a name="see-also"></a>另请参阅

[MFC 样品 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品 DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[MFC 样品对接](../../overview/visual-cpp-samples.md)<br/>
[CControlBar Class](../../mfc/reference/ccontrolbar-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl 类](../../mfc/reference/ctoolbarctrl-class.md)<br/>
[CControlBar Class](../../mfc/reference/ccontrolbar-class.md)
