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
ms.openlocfilehash: 0f6d940ca123483f381231e6d34d98eebe101bf7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212379"
---
# <a name="csplitterwnd-class"></a>CSplitterWnd 类

提供拆分窗口功能，此窗口包含多个窗格。

## <a name="syntax"></a>语法

```
class CSplitterWnd : public CWnd
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CSplitterWnd：： CSplitterWnd](#csplitterwnd)|调用构造 `CSplitterWnd` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[CSplitterWnd：： ActivateNext](#activatenext)|执行下一个窗格或上一个窗格命令。|
|[CSplitterWnd：： CanActivateNext](#canactivatenext)|检查当前是否可以查看下一个窗格或上一个窗格命令。|
|[CSplitterWnd：： Create](#create)|调用以创建动态拆分窗口并将其附加到 `CSplitterWnd` 对象。|
|[CSplitterWnd：： CreateScrollBarCtrl](#createscrollbarctrl)|创建共享滚动条控件。|
|[CSplitterWnd：： CreateStatic](#createstatic)|调用以创建静态拆分器窗口并将其附加到 `CSplitterWnd` 对象。|
|[CSplitterWnd：： CreateView](#createview)|调用在拆分器窗口中创建窗格。|
|[CSplitterWnd：:D eleteColumn](#deletecolumn)|从拆分器窗口中删除列。|
|[CSplitterWnd：:D eleteRow](#deleterow)|从拆分器窗口中删除一行。|
|[CSplitterWnd：:D eleteView](#deleteview)|从拆分器窗口中删除视图。|
|[CSplitterWnd：:D oKeyboardSplit](#dokeyboardsplit)|执行键盘拆分命令，通常为 "窗口拆分"。|
|[CSplitterWnd：:D oScroll](#doscroll)|执行拆分窗口的同步滚动。|
|[CSplitterWnd：:D oScrollBy](#doscrollby)|按给定的像素数滚动拆分窗口。|
|[CSplitterWnd：： GetActivePane](#getactivepane)|从框架中的焦点或活动视图确定活动窗格。|
|[CSplitterWnd：： GetColumnCount](#getcolumncount)|返回当前窗格列计数。|
|[CSplitterWnd：： GetColumnInfo](#getcolumninfo)|返回指定列的信息。|
|[CSplitterWnd：： GetPane](#getpane)|返回位于指定的行和列的窗格。|
|[CSplitterWnd：： GetRowCount](#getrowcount)|返回当前窗格行计数。|
|[CSplitterWnd：： GetRowInfo](#getrowinfo)|返回指定行的信息。|
|[CSplitterWnd：： GetScrollStyle](#getscrollstyle)|返回共享的滚动条样式。|
|[CSplitterWnd：： IdFromRowCol](#idfromrowcol)|返回位于指定的行和列的窗格的子窗口 ID。|
|[CSplitterWnd：： IsChildPane](#ischildpane)|调用以确定窗口当前是否为此拆分窗口的子窗格。|
|[CSplitterWnd：： IsTracking](#istracking)|确定当前是否正在移动拆分栏。|
|[CSplitterWnd：： RecalcLayout](#recalclayout)|调用以在调整行或列的大小时重新显示拆分窗口。|
|[CSplitterWnd：： SetActivePane](#setactivepane)|将窗格设置为框架中的活动窗格。|
|[CSplitterWnd：： SetColumnInfo](#setcolumninfo)|调用以设置指定的列信息。|
|[CSplitterWnd：： SetRowInfo](#setrowinfo)|调用以设置指定的行信息。|
|[CSplitterWnd：： SetScrollStyle](#setscrollstyle)|为拆分窗口的共享滚动条支持指定新的滚动条样式。|
|[CSplitterWnd：： SplitColumn](#splitcolumn)|指示框架窗口垂直拆分的位置。|
|[CSplitterWnd：： SplitRow](#splitrow)|指示框架窗口水平拆分的位置。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CSplitterWnd：： OnDraw](#ondraw)|由框架调用以绘制拆分器窗口。|
|[CSplitterWnd：： OnDrawSplitter](#ondrawsplitter)|呈现拆分窗口的图像。|
|[CSplitterWnd：： OnInvertTracker](#oninverttracker)|呈现拆分窗口的图像，使其与框架窗口的大小和形状相同。|

## <a name="remarks"></a>备注

窗格通常是特定于应用程序的对象，派生自[CView](../../mfc/reference/cview-class.md)，但它可以是具有相应子窗口 ID 的任意[CWnd](../../mfc/reference/cwnd-class.md)对象。

`CSplitterWnd`对象通常嵌入在父[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)对象中。 `CSplitterWnd`使用以下步骤创建对象：

1. `CSplitterWnd`在父框架中嵌入成员变量。

2. 重写父框架的[CFrameWnd：： OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)成员函数。

3. 在重写的中 `OnCreateClient` ，调用的[Create](#create)或[CreateStatic](#createstatic)成员函数 `CSplitterWnd` 。

调用 `Create` 成员函数以创建动态拆分窗口。 动态拆分窗口通常用于创建和滚动同一文档的多个单独窗格或视图。 框架自动创建拆分器的初始窗格;然后，当用户操作拆分窗口的控件时，框架会创建、调整和释放其他窗格。

调用时 `Create` ，需要指定最小行高和列宽，以确定窗格太小而无法完全显示的时间。 调用后 `Create` ，可以通过调用[SetColumnInfo](#setcolumninfo)和[SetRowInfo](#setrowinfo)成员函数来调整这些最小。

还可以使用 `SetColumnInfo` 和 `SetRowInfo` 成员函数为某一列设置 "理想" 宽度，并为行设置 "理想" 高度。 当框架显示拆分窗口时，它首先显示父框架，然后显示拆分窗口。 然后，框架根据其理想维度（从左上角到拆分窗口的工作区右下角），在列和行中布局窗格。

动态拆分窗口中的所有窗格都必须属于同一个类。 支持动态拆分窗口的熟悉的应用程序包括 Microsoft Word 和 Microsoft Excel。

使用 `CreateStatic` 成员函数创建静态拆分窗口。 用户只能更改静态拆分窗口中窗格的大小，而不能更改它们的编号或顺序。

创建静态拆分器时，必须专门创建静态拆分器的所有窗格。 请确保在父框架的成员函数返回之前创建所有窗格 `OnCreateClient` ，否则框架将不会正确显示窗口。

此 `CreateStatic` 成员函数自动初始化具有最小行高和列宽度0的静态拆分器。 调用之后 `Create` ，通过调用[SetColumnInfo](#setcolumninfo)和[SetRowInfo](#setrowinfo)成员函数调整这些最小。 在 `SetColumnInfo` `SetRowInfo` 您调用 `CreateStatic` 以指示所需的理想窗格维度后，还可以使用和。

静态拆分器的各个窗格通常属于不同的类。 有关静态拆分窗口的示例，请参阅图形编辑器和 Windows 文件管理器。

拆分窗口支持特殊的滚动条（除了窗格可能具有的滚动条）。 这些滚动条是对象的子项 `CSplitterWnd` ，并与窗格共享。

创建拆分器窗口时，将创建这些特殊的滚动条。 例如， `CSplitterWnd` 具有一行、两列和 WS_VSCROLL 样式的将显示两个窗格共享的垂直滚动条。 当用户移动滚动条时，WM_VSCROLL 的消息将发送到两个窗格中。 当窗格设置滚动条的位置时，将设置共享滚动条。

有关拆分窗口的详细信息，请参阅[技术说明 29](../../mfc/tn029-splitter-windows.md)。

有关如何创建动态拆分窗口的详细信息，请参阅：

- MFC 示例[自由曲线](../../overview/visual-cpp-samples.md)

- MFC 示例[VIEWEX](../../overview/visual-cpp-samples.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSplitterWnd`

## <a name="requirements"></a>要求

**标头：** afxext。h

## <a name="csplitterwndactivatenext"></a><a name="activatenext"></a>CSplitterWnd：： ActivateNext

由框架调用以执行下一个窗格或上一个窗格命令。

```
virtual void ActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>参数

*bPrev*<br/>
指示要激活哪个窗口。 对于 previous，为**TRUE** ;对于 "下一步" 为**FALSE** 。

### <a name="remarks"></a>备注

此成员函数是一个高级命令， [CView](../../mfc/reference/cview-class.md)类使用它来委托到 `CSplitterWnd` 实现。

## <a name="csplitterwndcanactivatenext"></a><a name="canactivatenext"></a>CSplitterWnd：： CanActivateNext

由框架调用，用于检查是否当前可以使用下一个窗格或上一个窗格命令。

```
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>参数

*bPrev*<br/>
指示要激活哪个窗口。 对于 previous，为**TRUE** ;对于 "下一步" 为**FALSE** 。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数是一个高级命令， [CView](../../mfc/reference/cview-class.md)类使用它来委托到 `CSplitterWnd` 实现。

## <a name="csplitterwndcreate"></a><a name="create"></a>CSplitterWnd：： Create

若要创建动态拆分窗口，请调用 `Create` 成员函数。

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

*pParentWnd*<br/>
拆分窗口的父框架窗口。

*nMaxRows*<br/>
拆分器窗口中的最大行数。 此值不能超过2。

*nMaxCols*<br/>
拆分器窗口中的最大列数。 此值不能超过2。

*sizeMin*<br/>
指定可显示窗格的最小大小。

*pContext*<br/>
指向[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)结构的指针。 在大多数情况下，这可能是传递到父框架窗口的*pContext* 。

*dwStyle*<br/>
指定窗口样式。

*nID*<br/>
窗口的子窗口 ID。 此 ID 可以 AFX_IDW_PANE_FIRST，除非拆分窗口嵌套在另一个拆分器窗口内。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

可以 `CSplitterWnd` 通过执行以下步骤，将嵌入[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)对象：

1. `CSplitterWnd`在父框架中嵌入成员变量。

1. 重写父框架的[CFrameWnd：： OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)成员函数。

1. `Create`从重写中调用成员函数 `OnCreateClient` 。

从父框架内创建拆分窗口时，将父框架的*pContext*参数传递到拆分器窗口。 否则，此参数可以为 NULL。

动态拆分窗口的初始最小行高和列宽由*sizeMin*参数设置。 这些最小确定窗格是否太小而无法完整显示，可以使用[SetRowInfo](#setrowinfo)和[SetColumnInfo](#setcolumninfo)成员函数进行更改。

有关动态拆分窗口的详细信息，请参阅文章[多文档类型、视图和框架窗口](../../mfc/multiple-document-types-views-and-frame-windows.md)、[技术说明 29](../../mfc/tn029-splitter-windows.md)和类概述中的 "拆分窗口" `CSplitterWnd` 。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#125](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]

## <a name="csplitterwndcreatescrollbarctrl"></a><a name="createscrollbarctrl"></a>CSplitterWnd：： CreateScrollBarCtrl

由框架调用以创建共享的滚动条控件。

```
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定窗口样式。

*nID*<br/>
窗口的子窗口 ID。 此 ID 可以 AFX_IDW_PANE_FIRST，除非拆分窗口嵌套在另一个拆分器窗口内。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

重写 `CreateScrollBarCtrl` 以包含滚动条旁边的额外控件。 默认行为是创建普通的 Windows 滚动条控件。

## <a name="csplitterwndcreatestatic"></a><a name="createstatic"></a>CSplitterWnd：： CreateStatic

若要创建静态拆分窗口，请调用 `CreateStatic` 成员函数。

```
virtual BOOL CreateStatic(
    CWnd* pParentWnd,
    int nRows,
    int nCols,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>参数

*pParentWnd*<br/>
拆分窗口的父框架窗口。

nRows**<br/>
行数。 此值不能超过16。

*nCols*<br/>
列数。 此值不能超过16。

*dwStyle*<br/>
指定窗口样式。

*nID*<br/>
窗口的子窗口 ID。 此 ID 可以 AFX_IDW_PANE_FIRST，除非拆分窗口嵌套在另一个拆分器窗口内。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

`CSplitterWnd`通常 `CFrameWnd` 通过执行以下步骤嵌入父对象或[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)对象：

1. `CSplitterWnd`在父框架中嵌入成员变量。

1. 重写父框架的 `OnCreateClient` 成员函数。

1. `CreateStatic`从重写的[CFrameWnd：： OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)中调用成员函数。

静态拆分窗口包含固定数量的窗格，通常来自不同的类。

创建静态拆分窗口时，必须同时创建其所有窗格。 [CreateView](#createview)成员函数通常用于实现此目的，但也可以创建其他 nonview 类。

静态拆分窗口的初始最小行高和列宽为0。 这些最小确定窗格太小而无法全部显示的时间，可以使用[SetRowInfo](#setrowinfo)和[SetColumnInfo](#setcolumninfo)成员函数进行更改。

若要向静态拆分器窗口添加滚动条，请将 WS_HSCROLL 和 WS_VSCROLL 样式添加到*dwStyle*。

有关静态拆分窗口的详细信息，请参阅文章[多文档类型、视图和框架窗口](../../mfc/multiple-document-types-views-and-frame-windows.md)、[技术说明 29](../../mfc/tn029-splitter-windows.md)和 `CSplitterWnd` 类概述。

## <a name="csplitterwndcreateview"></a><a name="createview"></a>CSplitterWnd：： CreateView

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

*总行*<br/>
指定要在其中放置新视图的拆分窗口行。

*col*<br/>
指定要在其中放置新视图的拆分窗口列。

*pViewClass*<br/>
指定新视图的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 。

*sizeInit*<br/>
指定新视图的初始大小。

*pContext*<br/>
一个指针，指向用于创建视图的创建上下文（通常是传递到父框架的重写[CFrameWnd：： OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)成员函数（在其中创建拆分窗口）的*pContext* 。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

在框架显示拆分器之前，必须先创建静态拆分器窗口的所有窗格。

当动态拆分窗口的用户拆分窗格、行或列时，框架还会调用此成员函数来创建新的窗格。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]

## <a name="csplitterwndcsplitterwnd"></a><a name="csplitterwnd"></a>CSplitterWnd：： CSplitterWnd

调用构造 `CSplitterWnd` 对象。

```
CSplitterWnd();
```

### <a name="remarks"></a>备注

`CSplitterWnd`按两个步骤构造对象。 首先，调用构造函数，该构造函数将创建 `CSplitterWnd` 对象，然后调用[Create](#create)成员函数，该函数创建拆分器窗口并将其附加 `CSplitterWnd` 到对象。

## <a name="csplitterwnddeletecolumn"></a><a name="deletecolumn"></a>CSplitterWnd：:D eleteColumn

从拆分器窗口中删除列。

```
virtual void DeleteColumn(int colDelete);
```

### <a name="parameters"></a>参数

*colDelete*<br/>
指定要删除的列。

### <a name="remarks"></a>备注

此成员函数由框架调用，用于实现动态拆分窗口（即，如果拆分窗口具有 SPLS_DYNAMIC_SPLIT 样式）的逻辑。 它可以自定义，以及虚拟函数[CreateView](#createview)，以实现更高级的动态拆分器。

## <a name="csplitterwnddeleterow"></a><a name="deleterow"></a>CSplitterWnd：:D eleteRow

从拆分器窗口中删除一行。

```
virtual void DeleteRow(int rowDelete);
```

### <a name="parameters"></a>参数

*rowDelete*<br/>
指定要删除的行。

### <a name="remarks"></a>备注

此成员函数由框架调用，用于实现动态拆分窗口（即，如果拆分窗口具有 SPLS_DYNAMIC_SPLIT 样式）的逻辑。 它可以自定义，以及虚拟函数[CreateView](#createview)，以实现更高级的动态拆分器。

## <a name="csplitterwnddeleteview"></a><a name="deleteview"></a>CSplitterWnd：:D eleteView

从拆分器窗口中删除视图。

```
virtual void DeleteView(
    int row,
    int col);
```

### <a name="parameters"></a>参数

*总行*<br/>
指定要在其上删除视图的拆分窗口行。

*col*<br/>
指定要在其上删除视图的拆分窗口列。

### <a name="remarks"></a>备注

如果正在删除活动视图，则下一个视图将变为活动状态。 默认实现假定视图将在[PostNcDestroy](../../mfc/reference/cwnd-class.md#postncdestroy)中自动删除。

此成员函数由框架调用，用于实现动态拆分窗口（即，如果拆分窗口具有 SPLS_DYNAMIC_SPLIT 样式）的逻辑。 它可以自定义，以及虚拟函数[CreateView](#createview)，以实现更高级的动态拆分器。

## <a name="csplitterwnddokeyboardsplit"></a><a name="dokeyboardsplit"></a>CSplitterWnd：:D oKeyboardSplit

执行键盘拆分命令，通常为 "窗口拆分"。

```
virtual BOOL DoKeyboardSplit();
```

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数是一个高级命令， [CView](../../mfc/reference/cview-class.md)类使用它来委托到 `CSplitterWnd` 实现。

## <a name="csplitterwnddoscroll"></a><a name="doscroll"></a>CSplitterWnd：:D oScroll

执行拆分窗口的同步滚动。

```
virtual BOOL DoScroll(
    CView* pViewFrom,
    UINT nScrollCode,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>参数

*pViewFrom*<br/>
指向滚动消息源自的视图的指针。

*nScrollCode*<br/>
指示用户滚动请求的滚动条代码。 此参数由两部分组成：一个低序位字节，用于确定水平滚动的类型和一个高序位字节，该字节确定垂直发生的滚动类型：

- SB_BOTTOM 向下滚动。

- SB_LINEDOWN 向下滚动一行。

- SB_LINEUP 向上滚动一行。

- SB_PAGEDOWN 向下滚动一页。

- SB_PAGEUP 向上滚动一页。

- SB_TOP 滚动到顶部。

*bDoScroll*<br/>
确定是否发生指定的滚动操作。 如果*bDoScroll*为 TRUE （也就是说，如果存在子窗口，并且拆分窗口具有滚动范围），则可能发生指定的滚动操作;如果*bDoScroll*为 FALSE （也就是说，如果不存在子窗口或拆分视图没有滚动范围），则不会发生滚动。

### <a name="return-value"></a>返回值

如果同步滚动发生，则为非零值;否则为0。

### <a name="remarks"></a>备注

此成员函数在视图收到滚动消息时由框架调用，以执行拆分窗口的同步滚动。 重写以在允许同步滚动之前要求用户进行操作。

## <a name="csplitterwnddoscrollby"></a><a name="doscrollby"></a>CSplitterWnd：:D oScrollBy

按给定的像素数滚动拆分窗口。

```
virtual BOOL DoScrollBy(
    CView* pViewFrom,
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>参数

*pViewFrom*<br/>
指向滚动消息源自的视图的指针。

*sizeScroll*<br/>
水平和垂直滚动的像素数。

*bDoScroll*<br/>
确定是否发生指定的滚动操作。 如果*bDoScroll*为 TRUE （也就是说，如果存在子窗口，并且拆分窗口具有滚动范围），则可能发生指定的滚动操作;如果*bDoScroll*为 FALSE （也就是说，如果不存在子窗口或拆分视图没有滚动范围），则不会发生滚动。

### <a name="return-value"></a>返回值

如果同步滚动发生，则为非零值;否则为0。

### <a name="remarks"></a>备注

此成员函数在响应滚动消息时由框架调用，以按*sizeScroll*所指示的量（以像素为单位）执行拆分窗口的同步滚动。 正值表示向下和向右滚动;负值指示向上和向左滚动。

重写以在允许滚动之前要求用户进行操作。

## <a name="csplitterwndgetactivepane"></a><a name="getactivepane"></a>CSplitterWnd：： GetActivePane

从框架中的焦点或活动视图确定活动窗格。

```
virtual CWnd* GetActivePane(
    int* pRow = NULL,
    int* pCol = NULL);
```

### <a name="parameters"></a>参数

*pRow*<br/>
指向的指针， **`int`** 用于检索活动窗格的行号。

*pCol*<br/>
指向的指针 **`int`** ，用于检索活动窗格的列号。

### <a name="return-value"></a>返回值

指向活动窗格的指针。 如果不存在活动窗格，则为 NULL。

### <a name="remarks"></a>备注

框架调用此成员函数来确定拆分器窗口中的活动窗格。 重写以在获取活动窗格之前要求用户执行操作。

## <a name="csplitterwndgetcolumncount"></a><a name="getcolumncount"></a>CSplitterWnd：： GetColumnCount

返回当前窗格列计数。

```
int GetColumnCount() const;
```

### <a name="return-value"></a>返回值

返回拆分器中列的当前数目。 对于静态拆分器，这也是最大列数。

## <a name="csplitterwndgetcolumninfo"></a><a name="getcolumninfo"></a>CSplitterWnd：： GetColumnInfo

返回指定列的信息。

```cpp
void GetColumnInfo(
    int col,
    int& cxCur,
    int& cxMin) const;
```

### <a name="parameters"></a>参数

*col*<br/>
指定列。

*cxCur*<br/>
对 **`int`** 要设置为当前列宽度的的引用。

*cxMin*<br/>
对的引用，它将 **`int`** 设置为当前的列最小宽度。

## <a name="csplitterwndgetpane"></a><a name="getpane"></a>CSplitterWnd：： GetPane

返回位于指定的行和列的窗格。

```
CWnd* GetPane(
    int row,
    int col) const;
```

### <a name="parameters"></a>参数

*总行*<br/>
指定一行。

*col*<br/>
指定列。

### <a name="return-value"></a>返回值

返回位于指定的行和列的窗格。 返回的窗格通常是一个[CView](../../mfc/reference/cview-class.md)派生类。

## <a name="csplitterwndgetrowcount"></a><a name="getrowcount"></a>CSplitterWnd：： GetRowCount

返回当前窗格行计数。

```
int GetRowCount() const;
```

### <a name="return-value"></a>返回值

返回拆分器窗口中的当前行数。 对于静态拆分窗口，这也是最大行数。

## <a name="csplitterwndgetrowinfo"></a><a name="getrowinfo"></a>CSplitterWnd：： GetRowInfo

返回指定行的信息。

```cpp
void GetRowInfo(
    int row,
    int& cyCur,
    int& cyMin) const;
```

### <a name="parameters"></a>参数

*总行*<br/>
指定一行。

*cyCur*<br/>
要 **`int`** 设置为行的当前高度（以像素为单位）的引用。

*cyMin*<br/>
要 **`int`** 设置为当前行的最小高度（以像素为单位）的引用。

### <a name="remarks"></a>备注

调用此成员函数以获取有关指定行的信息。 *CyCur*参数是用指定行的当前高度填充的，而*cyMin*则填充行的最小高度。

## <a name="csplitterwndgetscrollstyle"></a><a name="getscrollstyle"></a>CSplitterWnd：： GetScrollStyle

返回拆分窗口的共享滚动条样式。

```
DWORD GetScrollStyle() const;
```

### <a name="return-value"></a>返回值

如果成功，则为以下一种或多种 windows 样式标志：

- WS_HSCROLL 如果拆分器当前管理共享的水平滚动条，则为。

- WS_VSCROLL 如果拆分器当前管理共享垂直滚动条，则为。

如果为零，则拆分窗口当前不会管理任何共享的滚动条。

## <a name="csplitterwndidfromrowcol"></a><a name="idfromrowcol"></a>CSplitterWnd：： IdFromRowCol

获取位于指定行和列的窗格的子窗口 ID。

```
int IdFromRowCol(
    int row,
    int col) const;
```

### <a name="parameters"></a>参数

*总行*<br/>
指定拆分窗口行。

*col*<br/>
指定拆分窗口列。

### <a name="return-value"></a>返回值

窗格的子窗口 ID。

### <a name="remarks"></a>备注

此成员函数用于创建 nonviews 作为窗格，可以在窗格存在之前调用此函数。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]

## <a name="csplitterwndischildpane"></a><a name="ischildpane"></a>CSplitterWnd：： IsChildPane

确定*pWnd*当前是否为此拆分窗口的子窗格。

```
BOOL IsChildPane(
    CWnd* pWnd,
    int* pRow,
    int* pCol);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
指向要测试的[CWnd](../../mfc/reference/cwnd-class.md)对象的指针。

*pRow*<br/>
一个指针，指向要 **`int`** 在其中存储行号的。

*pCol*<br/>
一个指针，指向要 **`int`** 在其中存储列号的。

### <a name="return-value"></a>返回值

如果为非零值，则*pWnd*当前为此拆分窗口的子窗格，并且将使用窗格在拆分窗口中的位置填充*pRow*和*pCol* 。 如果*pWnd*不是此拆分窗口的子窗格，则返回0。

### <a name="remarks"></a>备注

在6.0 之前的 Visual C++ 版本中，此函数被定义为

`BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`

此版本现已过时，不应使用。

## <a name="csplitterwndistracking"></a><a name="istracking"></a>CSplitterWnd：： IsTracking

调用此成员函数以确定当前是否正在移动窗口中的拆分栏。

```
BOOL IsTracking();
```

### <a name="return-value"></a>返回值

如果拆分器操作正在进行，则为非零值;否则为0。

## <a name="csplitterwndondrawsplitter"></a><a name="ondrawsplitter"></a>CSplitterWnd：： OnDrawSplitter

呈现拆分窗口的图像。

```
virtual void OnDrawSplitter(
    CDC* pDC,
    ESplitType nType,
    const CRect& rect);
```

### <a name="parameters"></a>参数

*pDC*<br/>
一个指针，指向要在其中进行绘制的设备上下文。 如果*pDC*为 NULL，则该框架将调用[CWnd：： RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow) ，并且不绘制拆分窗口。

nType**<br/>
的值 `enum ESplitType` ，可以是下列值之一：

- `splitBox`拆分器拖动框。

- `splitBar`在两个拆分窗口之间显示的栏。

- `splitIntersection`拆分窗口的交集。 在 Windows 95/98 上运行时，不会调用此元素。

- `splitBorder`拆分窗口边框。

*rect*<br/>
对[CRect](../../atl-mfc-shared/reference/crect-class.md)对象的引用，该对象指定拆分窗口的大小和形状。

### <a name="remarks"></a>备注

此成员函数由框架调用，用于绘制和指定拆分器窗口的准确特性。 重写 `OnDrawSplitter` 用于拆分窗口的各种图形组件的图像的高级自定义。 默认图像与 Microsoft for Windows 或 Microsoft Windows 95/98 中的拆分器类似，拆分条的交集将混合在一起。

有关动态拆分窗口的详细信息，请参阅文章[多文档类型、视图和框架窗口](../../mfc/multiple-document-types-views-and-frame-windows.md)、[技术说明 29](../../mfc/tn029-splitter-windows.md)和类概述中的 "拆分窗口" `CSplitterWnd` 。

## <a name="csplitterwndoninverttracker"></a><a name="oninverttracker"></a>CSplitterWnd：： OnInvertTracker

呈现拆分窗口的图像，使其与框架窗口的大小和形状相同。

```
virtual void OnInvertTracker(const CRect& rect);
```

### <a name="parameters"></a>参数

*rect*<br/>
对 `CRect` 指定跟踪矩形的对象的引用。

### <a name="remarks"></a>备注

当调整拆分器的大小时，框架将调用此成员函数。 覆盖 `OnInvertTracker` 拆分器窗口的图像的高级自定义。 默认图像与 Microsoft for Windows 或 Microsoft Windows 95/98 中的拆分器类似，拆分条的交集将混合在一起。

有关动态拆分窗口的详细信息，请参阅文章[多文档类型、视图和框架窗口](../../mfc/multiple-document-types-views-and-frame-windows.md)、[技术说明 29](../../mfc/tn029-splitter-windows.md)和类概述中的 "拆分窗口" `CSplitterWnd` 。

## <a name="csplitterwndrecalclayout"></a><a name="recalclayout"></a>CSplitterWnd：： RecalcLayout

调用以在调整行或列的大小时重新显示拆分窗口。

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>备注

使用[SetRowInfo](#setrowinfo)和[SetColumnInfo](#setcolumninfo)成员函数调整行和列的大小时，调用此成员函数以正确重新显示拆分窗口。 如果在拆分窗口可见之前更改行和列的大小作为创建过程的一部分，则无需调用此成员函数。

每当用户调整拆分器窗口的大小或移动拆分时，框架都会调用此成员函数。

### <a name="example"></a>示例

  请参阅[CSplitterWnd：： SetColumnInfo](#setcolumninfo)的示例。

## <a name="csplitterwndsetactivepane"></a><a name="setactivepane"></a>CSplitterWnd：： SetActivePane

将窗格设置为框架中的活动窗格。

```
virtual void SetActivePane(
    int row,
    int col,
    CWnd* pWnd = NULL);
```

### <a name="parameters"></a>参数

*总行*<br/>
如果*pWnd*为 NULL，则在窗格中指定将处于活动状态的行。

*col*<br/>
如果*pWnd*为 NULL，则在窗格中指定将处于活动状态的列。

*pWnd*<br/>
一个指向 `CWnd` 对象的指针。 如果为 NULL，则由*row*和*col*指定的窗格设置为活动窗格。 如果不为 NULL，则指定设置为活动的窗格。

### <a name="remarks"></a>备注

当用户将焦点更改为框架窗口中的窗格时，框架会调用此成员函数以将窗格设置为活动状态。 您可以显式调用 `SetActivePane` 以将焦点更改到指定的视图。

通过提供行和列，**或**通过提供*pWnd*来指定窗格。

## <a name="csplitterwndsetcolumninfo"></a><a name="setcolumninfo"></a>CSplitterWnd：： SetColumnInfo

调用以设置指定的列信息。

```cpp
void SetColumnInfo(
    int col,
    int cxIdeal,
    int cxMin);
```

### <a name="parameters"></a>参数

*col*<br/>
指定拆分窗口列。

*cxIdeal*<br/>
指定拆分窗口列的理想宽度（以像素为单位）。

*cxMin*<br/>
指定拆分窗口列的最小宽度（以像素为单位）。

### <a name="remarks"></a>备注

调用此成员函数可为列设置新的最小宽度和理想宽度。 列最小值决定列太小以致无法完全显示的时间。

当框架显示拆分窗口时，它会根据其理想尺寸在列和行中布局窗格，从左上角到拆分窗口的工作区的右下角。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]

## <a name="csplitterwndsetrowinfo"></a><a name="setrowinfo"></a>CSplitterWnd：： SetRowInfo

调用以设置指定的行信息。

```cpp
void SetRowInfo(
    int row,
    int cyIdeal,
    int cyMin);
```

### <a name="parameters"></a>参数

*总行*<br/>
指定拆分窗口行。

*cyIdeal*<br/>
指定拆分窗口行的理想高度（以像素为单位）。

*cyMin*<br/>
指定拆分窗口行的最小高度（以像素为单位）。

### <a name="remarks"></a>备注

调用此成员函数可为行设置新的最小高度和理想高度。 行的最小值决定了行太小而无法完全显示的时间。

当框架显示拆分窗口时，它会根据其理想尺寸在列和行中布局窗格，从左上角到拆分窗口的工作区的右下角。

## <a name="csplitterwndsetscrollstyle"></a><a name="setscrollstyle"></a>CSplitterWnd：： SetScrollStyle

为拆分窗口的共享滚动条支持指定新的滚动样式。

```cpp
void SetScrollStyle(DWORD dwStyle);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
拆分窗口的共享滚动条支持的新滚动样式，可以是下列值之一：

- WS_HSCROLL 创建/显示水平共享的滚动条。

- WS_VSCROLL 创建/显示垂直共享的滚动条。

### <a name="remarks"></a>备注

创建滚动条后，即使在 `SetScrollStyle` 没有该样式的情况下调用，它也不会被销毁; 而是隐藏这些滚动条。 这样，滚动条就可保留其状态，即使隐藏它们也是如此。 调用后， `SetScrollStyle` 必须调用[RecalcLayout](#recalclayout) ，所有更改才会生效。

## <a name="csplitterwndsplitcolumn"></a><a name="splitcolumn"></a>CSplitterWnd：： SplitColumn

指示框架窗口垂直拆分的位置。

```
virtual BOOL SplitColumn(int cxBefore);
```

### <a name="parameters"></a>参数

*cxBefore*<br/>
发生拆分之前的位置（以像素为单位）。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

此成员函数在创建垂直拆分窗口时调用。 `SplitColumn`指示发生拆分的默认位置。

`SplitColumn`由框架调用以实现动态拆分窗口的逻辑（即，如果拆分窗口具有 SPLS_DYNAMIC_SPLIT 样式）。 它可以自定义，以及虚拟函数[CreateView](#createview)，以实现更高级的动态拆分器。

## <a name="csplitterwndsplitrow"></a><a name="splitrow"></a>CSplitterWnd：： SplitRow

指示框架窗口水平拆分的位置。

```
virtual BOOL SplitRow(int cyBefore);
```

### <a name="parameters"></a>参数

*cyBefore*<br/>
发生拆分之前的位置（以像素为单位）。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

当创建水平拆分器窗口时，将调用此成员函数。 `SplitRow`指示发生拆分的默认位置。

`SplitRow`由框架调用以实现动态拆分窗口的逻辑（即，如果拆分窗口具有 SPLS_DYNAMIC_SPLIT 样式）。 它可以自定义，以及虚拟函数[CreateView](#createview)，以实现更高级的动态拆分器。

## <a name="csplitterwndondraw"></a><a name="ondraw"></a>CSplitterWnd：： OnDraw

由框架调用以绘制拆分器窗口。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
一个指向设备上下文的指针。

### <a name="remarks"></a>备注

## <a name="see-also"></a>另请参阅

[MFC 示例 VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CView 类](../../mfc/reference/cview-class.md)<br/>
[CWnd 类](../../mfc/reference/cwnd-class.md)
