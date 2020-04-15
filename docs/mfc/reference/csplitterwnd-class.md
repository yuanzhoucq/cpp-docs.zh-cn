---
title: CSplitterWnd 类
ms.date: 11/04/2016
f1_keywords:
- CSplitterWnd
- AFXEXT/CSplitterWnd
- AFXEXT/CSplitterWnd::CSplitterWnd
- AFXEXT/CSplitterWnd::ActivateNext
- AFXEXT/CSplitterWnd::CanActivateNext
- AFXEXT/CSplitterWnd::Create
- AFXEXT/CSplitterWnd::CreateScrollBarCtrl
- AFXEXT/CSplitterWnd::CreateStatic
- AFXEXT/CSplitterWnd::CreateView
- AFXEXT/CSplitterWnd::DeleteColumn
- AFXEXT/CSplitterWnd::DeleteRow
- AFXEXT/CSplitterWnd::DeleteView
- AFXEXT/CSplitterWnd::DoKeyboardSplit
- AFXEXT/CSplitterWnd::DoScroll
- AFXEXT/CSplitterWnd::DoScrollBy
- AFXEXT/CSplitterWnd::GetActivePane
- AFXEXT/CSplitterWnd::GetColumnCount
- AFXEXT/CSplitterWnd::GetColumnInfo
- AFXEXT/CSplitterWnd::GetPane
- AFXEXT/CSplitterWnd::GetRowCount
- AFXEXT/CSplitterWnd::GetRowInfo
- AFXEXT/CSplitterWnd::GetScrollStyle
- AFXEXT/CSplitterWnd::IdFromRowCol
- AFXEXT/CSplitterWnd::IsChildPane
- AFXEXT/CSplitterWnd::IsTracking
- AFXEXT/CSplitterWnd::RecalcLayout
- AFXEXT/CSplitterWnd::SetActivePane
- AFXEXT/CSplitterWnd::SetColumnInfo
- AFXEXT/CSplitterWnd::SetRowInfo
- AFXEXT/CSplitterWnd::SetScrollStyle
- AFXEXT/CSplitterWnd::SplitColumn
- AFXEXT/CSplitterWnd::SplitRow
- AFXEXT/CSplitterWnd::OnDraw
- AFXEXT/CSplitterWnd::OnDrawSplitter
- AFXEXT/CSplitterWnd::OnInvertTracker
helpviewer_keywords:
- CSplitterWnd [MFC], CSplitterWnd
- CSplitterWnd [MFC], ActivateNext
- CSplitterWnd [MFC], CanActivateNext
- CSplitterWnd [MFC], Create
- CSplitterWnd [MFC], CreateScrollBarCtrl
- CSplitterWnd [MFC], CreateStatic
- CSplitterWnd [MFC], CreateView
- CSplitterWnd [MFC], DeleteColumn
- CSplitterWnd [MFC], DeleteRow
- CSplitterWnd [MFC], DeleteView
- CSplitterWnd [MFC], DoKeyboardSplit
- CSplitterWnd [MFC], DoScroll
- CSplitterWnd [MFC], DoScrollBy
- CSplitterWnd [MFC], GetActivePane
- CSplitterWnd [MFC], GetColumnCount
- CSplitterWnd [MFC], GetColumnInfo
- CSplitterWnd [MFC], GetPane
- CSplitterWnd [MFC], GetRowCount
- CSplitterWnd [MFC], GetRowInfo
- CSplitterWnd [MFC], GetScrollStyle
- CSplitterWnd [MFC], IdFromRowCol
- CSplitterWnd [MFC], IsChildPane
- CSplitterWnd [MFC], IsTracking
- CSplitterWnd [MFC], RecalcLayout
- CSplitterWnd [MFC], SetActivePane
- CSplitterWnd [MFC], SetColumnInfo
- CSplitterWnd [MFC], SetRowInfo
- CSplitterWnd [MFC], SetScrollStyle
- CSplitterWnd [MFC], SplitColumn
- CSplitterWnd [MFC], SplitRow
- CSplitterWnd [MFC], OnDraw
- CSplitterWnd [MFC], OnDrawSplitter
- CSplitterWnd [MFC], OnInvertTracker
ms.assetid: fd0de258-6dbe-4552-9e47-a39de0471d51
ms.openlocfilehash: 8c8ce90f5e36d6cdc2592233588bc3bd7bf2c9d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371696"
---
# <a name="csplitterwnd-class"></a>CSplitterWnd 类

提供拆分窗口功能，此窗口包含多个窗格。

## <a name="syntax"></a>语法

```
class CSplitterWnd : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CSplitterwnd：CSplitterwnd](#csplitterwnd)|调用以构造对象`CSplitterWnd`。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CSplitterwnd：：激活下一个](#activatenext)|执行"下一个窗格"或"上一个窗格"命令。|
|[CSplitterwnd：：可以激活下一个](#canactivatenext)|检查"下一个窗格"或"上一个窗格"命令当前是否可行。|
|[CSplitterwnd：：创建](#create)|调用以创建一个动态拆分器窗口并将其附加到`CSplitterWnd`对象。|
|[CSplitterwnd：：创建ScrollBarCtrl](#createscrollbarctrl)|创建共享滚动条控件。|
|[CSplitterwnd：：创建静态](#createstatic)|调用以创建静态拆分器窗口并将其附加到`CSplitterWnd`对象。|
|[CSplitterwnd：：创建视图](#createview)|调用以在拆分器窗口中创建窗格。|
|[CSplitterwnd：:DeleteColumn](#deletecolumn)|从拆分器窗口中删除列。|
|[CSplitterwnd：:DeleteRow](#deleterow)|从拆分器窗口中删除行。|
|[CSplitterwnd：:Delete查看](#deleteview)|从拆分器窗口中删除视图。|
|[CSplitterwnd：:Do键盘拆分](#dokeyboardsplit)|执行键盘拆分命令，通常为"窗口拆分"。|
|[CSplitterwnd：:DoScroll](#doscroll)|对拆分窗口执行同步滚动。|
|[CSplitterwnd：:DoScrollBy](#doscrollby)|按给定像素数滚动拆分窗口。|
|[CSplitterwnd：：获取活动窗格](#getactivepane)|从框架中的焦点视图或活动视图中确定活动窗格。|
|[CSplitterwnd：：获取纵队计数](#getcolumncount)|返回当前窗格列计数。|
|[CSplitterwnd：：获取纵队信息](#getcolumninfo)|返回指定列上的信息。|
|[CSplitterwnd：：GetPane](#getpane)|返回指定行和列处的窗格。|
|[CSplitterwnd：：获取罗计数](#getrowcount)|返回当前窗格行计数。|
|[CSplitterwnd：：获取罗信息](#getrowinfo)|返回指定行上的信息。|
|[CSplitterwnd：：获取滚动样式](#getscrollstyle)|返回共享滚动条样式。|
|[CSplitterwnd：：IdFromRowCol](#idfromrowcol)|在指定的行和列上返回窗格的子窗口 ID。|
|[CSplitterwnd：：IsChildPane](#ischildpane)|调用以确定窗口当前是否是此拆分器窗口的子窗格。|
|[CSplitterwnd：正在跟踪](#istracking)|确定当前是否正在移动拆分条。|
|[CSplitterwnd：recalclayout](#recalclayout)|在调整行或列大小后调用以重新显示拆分器窗口。|
|[CSplitterwnd：：设置活动窗格](#setactivepane)|将窗格设为框架中的活动窗格。|
|[CSplitterwnd：：SetColumninfo](#setcolumninfo)|调用以设置指定的列信息。|
|[CSplitterwnd：：SetRowInfo](#setrowinfo)|调用以设置指定的行信息。|
|[CSplitterwnd：：设置滚动样式](#setscrollstyle)|为拆分器窗口的共享滚动条支持指定新的滚动条样式。|
|[CSplitterwnd：：拆分柱](#splitcolumn)|指示框架窗口垂直拆分的位置。|
|[CSplitterwnd：：拆分行](#splitrow)|指示框架窗口水平拆分的位置。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[CSplitterwnd：：OnDraw](#ondraw)|由框架调用以绘制拆分器窗口。|
|[CSplitterwnd：：在牵引器上](#ondrawsplitter)|渲染拆分窗口的图像。|
|[CSplitterwnd：：上反转跟踪器](#oninverttracker)|渲染拆分窗口的图像的大小和形状与框架窗口相同。|

## <a name="remarks"></a>备注

窗格通常是从[CView](../../mfc/reference/cview-class.md)派生的应用程序特定对象，但它可以是具有适当子窗口 ID 的任何[CWnd](../../mfc/reference/cwnd-class.md)对象。

对象`CSplitterWnd`通常嵌入在父[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIChildwnd](../../mfc/reference/cmdichildwnd-class.md)对象中。 使用以下步骤`CSplitterWnd`创建对象：

1. 在`CSplitterWnd`父帧中嵌入成员变量。

2. 覆盖父帧的[CFrameWnd：：OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)成员函数。

3. 从重写`OnCreateClient`中，调用`CSplitterWnd`的[创建](#create)或[创建静态](#createstatic)成员函数。

调用`Create`成员函数以创建动态拆分器窗口。 动态拆分器窗口通常用于创建和滚动同一文档的多个单个窗格或视图。 框架会自动为拆分器创建初始窗格;但是，框架会自动为拆分器创建一个初始窗格。然后，当用户操作拆分器窗口的控件时，框架将创建、调整和释放其他窗格。

调用 时`Create`，指定最小行高度和列宽度，以确定窗格何时太小而无法完全显示。 调用`Create`后，可以通过调用[SetColumnInfo](#setcolumninfo)和[SetRowInfo](#setrowinfo)成员函数来调整这些最小值。

还使用`SetColumnInfo`和`SetRowInfo`成员函数为列设置"理想"宽度，为行设置"理想"高度。 当框架显示拆分器窗口时，它首先显示父框架，然后显示拆分器窗口。 然后，框架根据它们的理想尺寸以列和行的形式排列窗格，从拆分窗口工作区的左上角到右下角工作。

动态拆分器窗口中的所有窗格必须属于同一类。 支持动态拆分窗口的熟悉应用程序包括 Microsoft Word 和 Microsoft Excel。

使用`CreateStatic`成员函数创建静态拆分器窗口。 用户只能更改静态拆分器窗口中窗格的大小，而不能更改其数量或顺序。

创建静态拆分器时，必须专门创建所有静态拆分器的窗格。 请确保在父框架`OnCreateClient`的成员函数返回之前创建所有窗格，否则框架将不能正确显示窗口。

成员`CreateStatic`函数自动初始化最小行高度和列宽度为 0 的静态拆分器。 调用`Create`后，通过调用[SetColumnInfo](#setcolumninfo)和[SetRowInfo](#setrowinfo)成员函数来调整这些最小值。 还使用`SetColumnInfo`和`SetRowInfo`调用`CreateStatic`后指示所需的理想窗格尺寸。

静态拆分器的各个窗格通常属于不同的类。 有关静态拆分窗口的示例，请参阅图形编辑器和 Windows 文件管理器。

拆分窗口支持特殊的滚动条（除了窗格可能具有的滚动条）。 这些滚动条是对象的子级`CSplitterWnd`，并与窗格共享。

创建拆分窗口时，可以创建这些特殊的滚动条。 例如，具有一`CSplitterWnd`行、两列和WS_VSCROLL样式的将显示由两个窗格共享的垂直滚动条。 当用户移动滚动条时，WM_VSCROLL消息发送到两个窗格。 当窗格设置滚动条位置时，将设置共享滚动条。

有关拆分窗口的详细信息，请参阅[技术说明 29](../../mfc/tn029-splitter-windows.md)。

有关如何创建动态拆分器窗口的详细信息，请参阅：

- MFC 样品[涂鸦](../../overview/visual-cpp-samples.md)

- MFC 样品[VIEWEX](../../overview/visual-cpp-samples.md).

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSplitterWnd`

## <a name="requirements"></a>要求

**标题：** afxext.h

## <a name="csplitterwndactivatenext"></a><a name="activatenext"></a>CSplitterwnd：：激活下一个

由框架调用以执行"下一个窗格"或"上一个窗格"命令。

```
virtual void ActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>参数

*bPrev*<br/>
指示要激活的窗口。 **以前的 TRUE;****下一个为 FALSE。**

### <a name="remarks"></a>备注

此成员函数是[CView](../../mfc/reference/cview-class.md)类用来委派到实现的高级`CSplitterWnd`命令。

## <a name="csplitterwndcanactivatenext"></a><a name="canactivatenext"></a>CSplitterwnd：：可以激活下一个

由框架调用以查看当前是否可以使用"下一个窗格"或"上一个窗格"命令。

```
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>参数

*bPrev*<br/>
指示要激活的窗口。 **以前的 TRUE;****下一个为 FALSE。**

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数是[CView](../../mfc/reference/cview-class.md)类用来委派到实现的高级`CSplitterWnd`命令。

## <a name="csplitterwndcreate"></a><a name="create"></a>CSplitterwnd：：创建

要创建动态拆分器窗口，`Create`请调用成员函数。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    int nMaxRows,
    int nMaxCols,
    SIZE sizeMin,
    CCreateContext* pContext,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_HSCROLL | WS_VSCROLL | SPLS_DYNAMIC_SPLIT,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>参数

*pparentwnd*<br/>
拆分器窗口的父框架窗口。

*nMaxRows*<br/>
拆分器窗口中的最大行数。 此值不得超过 2。

*nMaxCols*<br/>
拆分器窗口中的最大列数。 此值不得超过 2。

*大小明*<br/>
指定窗格可以显示的最小大小。

*pContext*<br/>
指向[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)结构的指针。 在大多数情况下，这可以是传递给父帧窗口的*pContext。*

*dwStyle*<br/>
指定窗口样式。

*nID*<br/>
窗口的子窗口 ID。 除非拆分器窗口嵌套在另一个拆分器窗口中，否则可以AFX_IDW_PANE_FIRST ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

您可以通过执行以下步骤将`CSplitterWnd`嵌入父[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIChildwnd](../../mfc/reference/cmdichildwnd-class.md)对象：

1. 在`CSplitterWnd`父帧中嵌入成员变量。

1. 覆盖父帧的[CFrameWnd：：OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)成员函数。

1. 从重写`Create``OnCreateClient`中调用成员函数。

从父帧内创建拆分窗口时，将父帧的*pContext*参数传递给拆分器窗口。 否则，此参数可以是 NULL。

动态拆分器窗口的初始最小行高度和列宽度由*sizeMin*参数设置。 这些最小值决定了窗格是否太小而无法完整显示，可以使用[SetRowInfo](#setrowinfo)和[SetColumnInfo](#setcolumninfo)成员函数进行更改。

有关动态拆分窗口的详细信息，请参阅文章["多个文档类型"、"视图"和"框架窗口](../../mfc/multiple-document-types-views-and-frame-windows.md)"、"[技术说明 29"](../../mfc/tn029-splitter-windows.md)和`CSplitterWnd`"类概述"中的"拆分窗口"。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#125](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]

## <a name="csplitterwndcreatescrollbarctrl"></a><a name="createscrollbarctrl"></a>CSplitterwnd：：创建ScrollBarCtrl

由框架调用以创建共享滚动条控件。

```
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定窗口样式。

*nID*<br/>
窗口的子窗口 ID。 除非拆分器窗口嵌套在另一个拆分器窗口中，否则可以AFX_IDW_PANE_FIRST ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

覆盖`CreateScrollBarCtrl`以在滚动条旁边包含额外的控件。 默认行为是创建正常的 Windows 滚动条控件。

## <a name="csplitterwndcreatestatic"></a><a name="createstatic"></a>CSplitterwnd：：创建静态

要创建静态拆分器窗口，`CreateStatic`请调用成员函数。

```
virtual BOOL CreateStatic(
    CWnd* pParentWnd,
    int nRows,
    int nCols,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>参数

*pparentwnd*<br/>
拆分器窗口的父框架窗口。

nRows**<br/>
行数。 此值不得超过 16。

*n科尔斯*<br/>
列数。 此值不得超过 16。

*dwStyle*<br/>
指定窗口样式。

*nID*<br/>
窗口的子窗口 ID。 除非拆分器窗口嵌套在另一个拆分器窗口中，否则可以AFX_IDW_PANE_FIRST ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

通常`CSplitterWnd`通过执行以下步骤嵌入父`CFrameWnd`对象或[CMDIChildwnd](../../mfc/reference/cmdichildwnd-class.md)对象中：

1. 在`CSplitterWnd`父帧中嵌入成员变量。

1. 覆盖父帧的成员`OnCreateClient`函数。

1. 从重写`CreateStatic`的 CFrameWnd 中调用成员函数[：：OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)。

静态拆分器窗口包含固定数量的窗格，通常来自不同的类。

创建静态拆分器窗口时，必须同时创建其所有窗格。 [CreateView](#createview)成员函数通常用于此目的，但您也可以创建其他非视图类。

静态拆分器窗口的初始最小行高度和列宽度为 0。 这些最小值决定了窗格何时太小而无法完整显示，可以使用[SetRowInfo](#setrowinfo)和[SetColumnInfo](#setcolumninfo)成员函数进行更改。

要将滚动条添加到静态拆分器窗口，请将WS_HSCROLL和WS_VSCROLL样式添加到*dwStyle*。

有关静态拆分器窗口的详细信息，请参阅文章"[多个文档类型、视图和框架窗口](../../mfc/multiple-document-types-views-and-frame-windows.md)、[技术说明 29"](../../mfc/tn029-splitter-windows.md)中的`CSplitterWnd`"拆分窗口"。

## <a name="csplitterwndcreateview"></a><a name="createview"></a>CSplitterwnd：：创建视图

为静态拆分器窗口创建窗格。

```
virtual BOOL CreateView(
    int row,
    int col,
    CRuntimeClass* pViewClass,
    SIZE sizeInit,
    CCreateContext* pContext);
```

### <a name="parameters"></a>参数

*行*<br/>
指定放置新视图的拆分器窗口行。

*col*<br/>
指定放置新视图的拆分器窗口列。

*pView 类*<br/>
指定新视图的[CRuntimeClass。](../../mfc/reference/cruntimeclass-structure.md)

*尺寸 Init*<br/>
指定新视图的初始大小。

*pContext*<br/>
指向创建上下文的指针，用于创建视图（通常*pContext*传递到父帧的重写[CFrameWnd：：onCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)成员函数，其中正在创建拆分器窗口）。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

在框架显示拆分器之前，必须创建静态拆分器窗口的所有窗格。

当动态拆分器窗口的用户拆分窗格、行或列时，框架还会调用此成员函数创建新窗格。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]

## <a name="csplitterwndcsplitterwnd"></a><a name="csplitterwnd"></a>CSplitterwnd：CSplitterwnd

调用以构造对象`CSplitterWnd`。

```
CSplitterWnd();
```

### <a name="remarks"></a>备注

分两`CSplitterWnd`步构造对象。 首先调用构造函数，该构造函数创建`CSplitterWnd`对象，然后调用[Create](#create)成员函数，该函数创建拆分器窗口并将其附加到`CSplitterWnd`对象。

## <a name="csplitterwnddeletecolumn"></a><a name="deletecolumn"></a>CSplitterwnd：:DeleteColumn

从拆分器窗口中删除列。

```
virtual void DeleteColumn(int colDelete);
```

### <a name="parameters"></a>参数

*colDelete*<br/>
指定要删除的列。

### <a name="remarks"></a>备注

框架调用此成员函数以实现动态拆分器窗口的逻辑（即，如果拆分器窗口具有SPLS_DYNAMIC_SPLIT样式）。 它可以与虚拟函数[CreateView](#createview)一起自定义，以实现更高级的动态拆分器。

## <a name="csplitterwnddeleterow"></a><a name="deleterow"></a>CSplitterwnd：:DeleteRow

从拆分器窗口中删除行。

```
virtual void DeleteRow(int rowDelete);
```

### <a name="parameters"></a>参数

*行删除*<br/>
指定要删除的行。

### <a name="remarks"></a>备注

框架调用此成员函数以实现动态拆分器窗口的逻辑（即，如果拆分器窗口具有SPLS_DYNAMIC_SPLIT样式）。 它可以与虚拟函数[CreateView](#createview)一起自定义，以实现更高级的动态拆分器。

## <a name="csplitterwnddeleteview"></a><a name="deleteview"></a>CSplitterwnd：:Delete查看

从拆分器窗口中删除视图。

```
virtual void DeleteView(
    int row,
    int col);
```

### <a name="parameters"></a>参数

*行*<br/>
指定要删除视图的拆分器窗口行。

*col*<br/>
指定要删除视图的拆分器窗口列。

### <a name="remarks"></a>备注

如果正在删除活动视图，则下一个视图将变为活动状态。 默认实现假定视图将在[PostNc销毁](../../mfc/reference/cwnd-class.md#postncdestroy)中自动删除 。

框架调用此成员函数以实现动态拆分器窗口的逻辑（即，如果拆分器窗口具有SPLS_DYNAMIC_SPLIT样式）。 它可以与虚拟函数[CreateView](#createview)一起自定义，以实现更高级的动态拆分器。

## <a name="csplitterwnddokeyboardsplit"></a><a name="dokeyboardsplit"></a>CSplitterwnd：:Do键盘拆分

执行键盘拆分命令，通常为"窗口拆分"。

```
virtual BOOL DoKeyboardSplit();
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数是[CView](../../mfc/reference/cview-class.md)类用来委派到实现的高级`CSplitterWnd`命令。

## <a name="csplitterwnddoscroll"></a><a name="doscroll"></a>CSplitterwnd：:DoScroll

对拆分窗口执行同步滚动。

```
virtual BOOL DoScroll(
    CView* pViewFrom,
    UINT nScrollCode,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>参数

*pView 从*<br/>
指向滚动消息源自的视图的指针。

*nScrollCode*<br/>
指示用户滚动请求的滚动条代码。 此参数由两部分组成：一个低阶字节，它确定水平发生的滚动类型;高阶字节，确定垂直发生的滚动类型：

- SB_BOTTOM滚动到底部。

- SB_LINEDOWN向下滚动一行。

- SB_LINEUP向上滚动一行。

- SB_PAGEDOWN向下滚动一页。

- SB_PAGEUP向上滚动一页。

- SB_TOP滚动到顶部。

*b多卷*<br/>
确定是否执行指定的滚动操作。 如果*bDoScroll*为 TRUE（即，如果存在子窗口，并且拆分窗口具有滚动范围），则可以执行指定的滚动操作;如果存在子窗口，则可以执行指定的滚动操作。如果*bDoScroll*是 FALSE（即，如果不存在子窗口，或者拆分视图没有滚动范围），则不会发生滚动。

### <a name="return-value"></a>返回值

如果同步滚动发生，则非零;否则 0。

### <a name="remarks"></a>备注

框架将调用此成员函数，在视图收到滚动消息时执行拆分窗口的同步滚动。 在允许同步滚动之前，需要用户执行操作。

## <a name="csplitterwnddoscrollby"></a><a name="doscrollby"></a>CSplitterwnd：:DoScrollBy

按给定像素数滚动拆分窗口。

```
virtual BOOL DoScrollBy(
    CView* pViewFrom,
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>参数

*pView 从*<br/>
指向滚动消息源自的视图的指针。

*大小滚动*<br/>
要水平和垂直滚动的像素数。

*b多卷*<br/>
确定是否执行指定的滚动操作。 如果*bDoScroll*为 TRUE（即，如果存在子窗口，并且拆分窗口具有滚动范围），则可以执行指定的滚动操作;如果存在子窗口，则可以执行指定的滚动操作。如果*bDoScroll*是 FALSE（即，如果不存在子窗口，或者拆分视图没有滚动范围），则不会发生滚动。

### <a name="return-value"></a>返回值

如果同步滚动发生，则非零;否则 0。

### <a name="remarks"></a>备注

框架调用此成员函数以响应滚动消息，以按*大小 Scroll*指示的数量（以像素为单位）对拆分窗口执行同步滚动。 正值表示向下和向右滚动;负值表示向上和向左滚动。

在允许滚动之前，重写以需要用户执行操作。

## <a name="csplitterwndgetactivepane"></a><a name="getactivepane"></a>CSplitterwnd：：获取活动窗格

从框架中的焦点视图或活动视图中确定活动窗格。

```
virtual CWnd* GetActivePane(
    int* pRow = NULL,
    int* pCol = NULL);
```

### <a name="parameters"></a>参数

*pRow*<br/>
指向**int**的指针，用于检索活动窗格的行号。

*pCol*<br/>
指向**int**的指针，用于检索活动窗格的列号。

### <a name="return-value"></a>返回值

指向活动窗格的指针。 如果没有活动窗格，则 NULL。

### <a name="remarks"></a>备注

框架调用此成员函数以确定拆分器窗口中的活动窗格。 在获取活动窗格之前，重写以需要用户执行操作。

## <a name="csplitterwndgetcolumncount"></a><a name="getcolumncount"></a>CSplitterwnd：：获取纵队计数

返回当前窗格列计数。

```
int GetColumnCount() const;
```

### <a name="return-value"></a>返回值

返回拆分器中的当前列数。 对于静态拆分器，这也将是列的最大数量。

## <a name="csplitterwndgetcolumninfo"></a><a name="getcolumninfo"></a>CSplitterwnd：：获取纵队信息

返回指定列上的信息。

```
void GetColumnInfo(
    int col,
    int& cxCur,
    int& cxMin) const;
```

### <a name="parameters"></a>参数

*col*<br/>
指定列。

*cxCur*<br/>
要设置为列的当前宽度的**int**的引用。

*cxMin*<br/>
要设置为列的当前最小宽度的**int**的引用。

## <a name="csplitterwndgetpane"></a><a name="getpane"></a>CSplitterwnd：：GetPane

返回指定行和列处的窗格。

```
CWnd* GetPane(
    int row,
    int col) const;
```

### <a name="parameters"></a>参数

*行*<br/>
指定行。

*col*<br/>
指定列。

### <a name="return-value"></a>返回值

返回指定行和列处的窗格。 返回的窗格通常是[CView](../../mfc/reference/cview-class.md)派生类。

## <a name="csplitterwndgetrowcount"></a><a name="getrowcount"></a>CSplitterwnd：：获取罗计数

返回当前窗格行计数。

```
int GetRowCount() const;
```

### <a name="return-value"></a>返回值

返回拆分器窗口中的当前行数。 对于静态拆分器窗口，这也将是最大行数。

## <a name="csplitterwndgetrowinfo"></a><a name="getrowinfo"></a>CSplitterwnd：：获取罗信息

返回指定行上的信息。

```
void GetRowInfo(
    int row,
    int& cyCur,
    int& cyMin) const;
```

### <a name="parameters"></a>参数

*行*<br/>
指定行。

*cyCur*<br/>
要设置为以像素为单位的行的当前高度的**int**的引用。

*赛明*<br/>
要设置为以像素为单位的行的当前最小高度的**int**的引用。

### <a name="remarks"></a>备注

调用此成员函数以获取有关指定行的信息。 *cyCur*参数用指定行的当前高度填充 *，cyMin*填充该行的最小高度。

## <a name="csplitterwndgetscrollstyle"></a><a name="getscrollstyle"></a>CSplitterwnd：：获取滚动样式

返回拆分器窗口的共享滚动条样式。

```
DWORD GetScrollStyle() const;
```

### <a name="return-value"></a>返回值

如果成功，则一个或多个以下窗口样式标志：

- WS_HSCROLL 如果拆分器当前管理共享水平滚动条。

- WS_VSCROLL 如果拆分器当前管理共享垂直滚动条。

如果为零，拆分器窗口当前不管理任何共享滚动条。

## <a name="csplitterwndidfromrowcol"></a><a name="idfromrowcol"></a>CSplitterwnd：：IdFromRowCol

获取指定行和列窗格的子窗口 ID。

```
int IdFromRowCol(
    int row,
    int col) const;
```

### <a name="parameters"></a>参数

*行*<br/>
指定拆分器窗口行。

*col*<br/>
指定拆分器窗口列。

### <a name="return-value"></a>返回值

窗格的子窗口 ID。

### <a name="remarks"></a>备注

此成员函数用于将非视图创建为窗格，并可能在窗格存在之前调用。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]

## <a name="csplitterwndischildpane"></a><a name="ischildpane"></a>CSplitterwnd：：IsChildPane

确定*pWnd*当前是否是此拆分器窗口的子窗格。

```
BOOL IsChildPane(
    CWnd* pWnd,
    int* pRow,
    int* pCol);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
指向要测试的[CWnd](../../mfc/reference/cwnd-class.md)对象的指针。

*pRow*<br/>
指向要在其中存储行号的**int**的指针。

*pCol*<br/>
指向用于存储列编号的**int**的指针。

### <a name="return-value"></a>返回值

如果为非零 *，pWnd*当前是此拆分器窗口的子窗格 *，pRow*和*pCol*中填充了拆分器窗口中窗格的位置。 如果*pWnd*不是此拆分器窗口的子窗格，则返回 0。

### <a name="remarks"></a>备注

在 6.0 之前的 Visual C++ 版本中，此函数定义为

`BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`

此版本现已过时，不应使用。

## <a name="csplitterwndistracking"></a><a name="istracking"></a>CSplitterwnd：正在跟踪

调用此成员函数以确定窗口中的拆分器条当前是否正在移动。

```
BOOL IsTracking();
```

### <a name="return-value"></a>返回值

如果拆分器操作正在进行，则非零;否则 0。

## <a name="csplitterwndondrawsplitter"></a><a name="ondrawsplitter"></a>CSplitterwnd：：在牵引器上

渲染拆分窗口的图像。

```
virtual void OnDrawSplitter(
    CDC* pDC,
    ESplitType nType,
    const CRect& rect);
```

### <a name="parameters"></a>参数

*pDC*<br/>
指向要绘制的设备上下文的指针。 如果*pDC*为 NULL，则框架将调用[CWnd：：redrawWindow，](../../mfc/reference/cwnd-class.md#redrawwindow)并且不绘制拆分窗口。

nType**<br/>
的值`enum ESplitType`可以是以下值之一：

- `splitBox`拆分器拖动框。

- `splitBar`出现在两个拆分窗口之间的条形。

- `splitIntersection`拆分窗口的交点。 在 Windows 95/98 上运行时，不会调用此元素。

- `splitBorder`拆分窗口边框。

*矩形*<br/>
对[CRect](../../atl-mfc-shared/reference/crect-class.md)对象的引用，指定拆分窗口的大小和形状。

### <a name="remarks"></a>备注

框架调用此成员函数以绘制和指定拆分器窗口的确切特征。 覆盖`OnDrawSplitter`以高级自定义拆分器窗口的各种图形组件的图像。 默认影像类似于适用于 Windows 的 Microsoft Works 或 Microsoft Windows 95/98 中的拆分器，因为拆分器条的交点混合在一起。

有关动态拆分窗口的详细信息，请参阅文章["多个文档类型"、"视图"和"框架窗口](../../mfc/multiple-document-types-views-and-frame-windows.md)"、"[技术说明 29"](../../mfc/tn029-splitter-windows.md)和`CSplitterWnd`"类概述"中的"拆分窗口"。

## <a name="csplitterwndoninverttracker"></a><a name="oninverttracker"></a>CSplitterwnd：：上反转跟踪器

渲染拆分窗口的图像的大小和形状与框架窗口相同。

```
virtual void OnInvertTracker(const CRect& rect);
```

### <a name="parameters"></a>参数

*矩形*<br/>
引用指定跟踪`CRect`矩形的对象。

### <a name="remarks"></a>备注

在调整拆分器大小时，框架将调用此成员函数。 覆盖`OnInvertTracker`以高级自定义拆分器窗口的图像。 默认影像类似于适用于 Windows 的 Microsoft Works 或 Microsoft Windows 95/98 中的拆分器，因为拆分器条的交点混合在一起。

有关动态拆分窗口的详细信息，请参阅文章["多个文档类型"、"视图"和"框架窗口](../../mfc/multiple-document-types-views-and-frame-windows.md)"、"[技术说明 29"](../../mfc/tn029-splitter-windows.md)和`CSplitterWnd`"类概述"中的"拆分窗口"。

## <a name="csplitterwndrecalclayout"></a><a name="recalclayout"></a>CSplitterwnd：recalclayout

在调整行或列大小后调用以重新显示拆分器窗口。

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>备注

使用[SetRowInfo](#setrowinfo)和[SetColumnInfo](#setcolumninfo)成员函数调整行和列大小后，调用此成员函数以正确重新显示拆分器窗口。 如果在拆分器窗口可见之前更改行和列大小作为创建过程的一部分，则不必调用此成员函数。

每当用户调整拆分窗口的大小或移动拆分时，框架都会调用此成员函数。

### <a name="example"></a>示例

  请参阅[CSplitterWnd 的示例：：SetColumnInfo](#setcolumninfo)。

## <a name="csplitterwndsetactivepane"></a><a name="setactivepane"></a>CSplitterwnd：：设置活动窗格

将窗格设为框架中的活动窗格。

```
virtual void SetActivePane(
    int row,
    int col,
    CWnd* pWnd = NULL);
```

### <a name="parameters"></a>参数

*行*<br/>
如果*pWnd*为 NULL，则指定窗格中将处于活动状态的行。

*col*<br/>
如果*pWnd*为 NULL，则指定窗格中将处于活动状态的列。

*pwnd*<br/>
一个指向 `CWnd` 对象的指针。 如果为 NULL，*则行*和*col*指定的窗格将设置为活动。 如果不是 NULL，则指定设置为活动的窗格。

### <a name="remarks"></a>备注

当用户将焦点更改为框架窗口中的窗格时，框架将此成员函数设置为活动窗格。 您可以显式调用`SetActivePane`以将焦点更改为指定的视图。

通过提供行和列 **，或通过**提供*pWnd*来指定窗格。

## <a name="csplitterwndsetcolumninfo"></a><a name="setcolumninfo"></a>CSplitterwnd：：SetColumninfo

调用以设置指定的列信息。

```
void SetColumnInfo(
    int col,
    int cxIdeal,
    int cxMin);
```

### <a name="parameters"></a>参数

*col*<br/>
指定拆分器窗口列。

*cx理想*<br/>
指定以像素为单位的拆分窗口列的理想宽度。

*cxMin*<br/>
指定以像素为单位的拆分窗口列的最小宽度。

### <a name="remarks"></a>备注

调用此成员函数以设置列的新最小宽度和理想宽度。 列最小值确定列何时太小而无法完全显示。

当框架显示拆分器窗口时，它会根据它们的理想尺寸以列和行的形式排列窗格，从拆分窗口工作区的左上角到右下角工作。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]

## <a name="csplitterwndsetrowinfo"></a><a name="setrowinfo"></a>CSplitterwnd：：SetRowInfo

调用以设置指定的行信息。

```
void SetRowInfo(
    int row,
    int cyIdeal,
    int cyMin);
```

### <a name="parameters"></a>参数

*行*<br/>
指定拆分窗口行。

*赛理想*<br/>
指定以像素为单位的拆分窗口行的理想高度。

*赛明*<br/>
指定以像素为单位的拆分窗口行的最小高度。

### <a name="remarks"></a>备注

调用此成员函数以为行设置新的最小高度和理想高度。 行最小值确定行何时太小而无法完全显示。

当框架显示拆分器窗口时，它会根据它们的理想尺寸以列和行的形式排列窗格，从拆分窗口工作区的左上角到右下角工作。

## <a name="csplitterwndsetscrollstyle"></a><a name="setscrollstyle"></a>CSplitterwnd：：设置滚动样式

指定拆分窗口的共享滚动条支持的新滚动样式。

```
void SetScrollStyle(DWORD dwStyle);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
拆分窗口的共享滚动条支持的新滚动样式，可以是以下值之一：

- WS_HSCROLL 创建/显示水平共享滚动条。

- WS_VSCROLL 创建/显示垂直共享滚动条。

### <a name="remarks"></a>备注

创建滚动条后，即使调用没有该样式`SetScrollStyle`，也不会销毁它;相反，这些滚动条是隐藏的。 这允许滚动条保留其状态，即使它们处于隐藏状态。 调用`SetScrollStyle`后，必须调用[RecalcLayout，](#recalclayout)以便所有更改生效。

## <a name="csplitterwndsplitcolumn"></a><a name="splitcolumn"></a>CSplitterwnd：：拆分柱

指示框架窗口垂直拆分的位置。

```
virtual BOOL SplitColumn(int cxBefore);
```

### <a name="parameters"></a>参数

*cx 之前*<br/>
发生拆分的位置（以像素为单位）。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

创建垂直拆分器窗口时，将调用此成员函数。 `SplitColumn`指示发生拆分的默认位置。

`SplitColumn`框架调用实现动态拆分器窗口的逻辑（即，如果拆分器窗口具有SPLS_DYNAMIC_SPLIT样式）。 它可以与虚拟函数[CreateView](#createview)一起自定义，以实现更高级的动态拆分器。

## <a name="csplitterwndsplitrow"></a><a name="splitrow"></a>CSplitterwnd：：拆分行

指示框架窗口水平拆分的位置。

```
virtual BOOL SplitRow(int cyBefore);
```

### <a name="parameters"></a>参数

*cy 之前*<br/>
发生拆分的位置（以像素为单位）。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

创建水平拆分器窗口时，将调用此成员函数。 `SplitRow`指示发生拆分的默认位置。

`SplitRow`框架调用实现动态拆分器窗口的逻辑（即，如果拆分器窗口具有SPLS_DYNAMIC_SPLIT样式）。 它可以与虚拟函数[CreateView](#createview)一起自定义，以实现更高级的动态拆分器。

## <a name="csplitterwndondraw"></a><a name="ondraw"></a>CSplitterwnd：：OnDraw

由框架调用以绘制拆分器窗口。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
一个指向设备上下文的指针。

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[MFC 样品视图](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CView 类](../../mfc/reference/cview-class.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)
