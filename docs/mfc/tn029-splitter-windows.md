---
title: TN029： 拆分器 Windows |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.windows.splitter
dev_langs:
- C++
helpviewer_keywords:
- TN029
- splitter windows [MFC], about splitter windows
ms.assetid: 2c57ce99-2a3c-4eff-9cea-baccb13af075
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 24556d7a331a74936631eef4fec2e293126cdbab
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379510"
---
# <a name="tn029-splitter-windows"></a>TN029：拆分窗口

此注释描述 MFC [CSplitterWnd 类](../mfc/reference/csplitterwnd-class.md)，这样将拆分窗口，并管理其他窗格窗口的大小调整。

## <a name="splitter-styles"></a>拆分器样式

一个`CSplitterWnd`支持两种不同样式的拆分窗口。

在"静态拆分条中，"拆分器窗口创建窗格时创建它。 顺序和窗格数永远不会更改。 拆分条用于调整大小的不同窗格。 此样式可用于在每个窗格中显示不同的视图类。 Visual c + + 图形编辑器和 Windows 文件管理器是使用此拆分器样式的程序的示例。 这种样式的拆分器窗口中不使用拆分器框。

在"动态拆分条中，"其他窗格创建和销毁作为用户拆分和取消拆分新视图。 此拆分器首先的单一视图，并提供了该用户启动拆分的拆分器框。 当在一个方向拆分视图时，拆分器窗口动态创建一个新的视图对象。 此新的视图对象表示新窗格。 如果该视图通过使用键盘界面拆分两个方向，拆分器窗口将创建三个新的视图对象的三个新窗格。 拆分处于活动状态，而 Windows 将拆分器中显示为窗格之间拆分栏。 用户删除拆分，但直到拆分器窗口本身该原始视图会一直被销毁时，Windows 会销毁附加视图对象。 使用动态拆分器样式的应用程序的示例 Microsoft Excel 和 Microsoft Word。

在创建这两种拆分器窗口时，必须指定最大行数和拆分器将管理的列。 静态拆分器将创建要填充的行和列的窗格。 动态拆分器将创建仅在第一个窗格时`CSplitterWnd`创建。

窗格可以为静态拆分条中指定的最大数目为 16 个列的 16 行。 建议的设置包括：

- 第 1 行 x 2 列： 通常具有不同的窗格

- 2 行 x 1 列： 通常具有不同的窗格

- 2 行 x 2 列： 通常具有类似的窗格

你可以为动态拆分条中指定的窗格的最大数目为 2 行 2 列。 建议的设置包括：

- 第 1 行 x 2 列： 纵栏表数据

- 2 行 x 1 列： 对文本或其他数据

- 2 行 x 2 列： 网格或表的面向数据

## <a name="splitter-examples"></a>拆分器示例

直接或间接地，许多 MFC 示例程序使用拆分窗口。 MFC 常规示例[VIEWEX](../visual-cpp-samples.md)说明了几种静态拆分条中，包括如何将拆分器放在拆分器的用法。

类向导还可用于创建新的多文档界面 (MDI) 子框架窗口类，其中包含拆分器窗口。 拆分窗口的详细信息，请参阅[多个文档类型、 视图和框架 Windows](../mfc/multiple-document-types-views-and-frame-windows.md)。

## <a name="terminology-used-by-implementation"></a>实现使用的术语

下面是特定于拆分窗口的术语的列表：

`CSplitterWnd`： 一个提供的拆分窗格的控件和所有窗格对行或列之间共享的滚动条的窗口。 从零开始的数字与指定行和列 (在第一个窗格中，行 = 0 且列 = 0)。

窗格中： 一个特定于应用程序窗口的`CSplitterWnd`管理。 一个窗格，通常是一个对象，派生自[CView 类](../mfc/reference/cview-class.md)，但可以是任何[CWnd](../mfc/reference/cwnd-class.md)对象都有相应的子窗口 id。

若要使用`CWnd`-派生对象，请将传递到对象的 RUNTIME_CLASS`CreateView`函数，您会像使用`CView`-派生的类。 您的类必须使用 DECLARE_DYNCREATE 和 IMPLEMENT_DYNCREATE，因为框架使用在运行时动态创建。 尽管有很多中的代码`CSplitterWnd`这是特定于`CView`类， [CObject::IsKindOf](../mfc/reference/cobject-class.md#iskindof)之前执行这些操作时始终使用。

拆分条： 行和列的窗格之间放置一个控件。 它可能用于调整大小的行或列的窗格。

拆分器中： 控件中动态`CSplitterWnd`可用来创建新行或列的窗格。 它位于顶部或左侧的水平滚动条的垂直滚动条。

拆分器交集： 垂直拆分条和水平拆分条的交集。 您可以拖动它以同时调整行和列的窗格的大小。

## <a name="shared-scroll-bars"></a>共享的滚动条

`CSplitterWnd`类还支持共享的滚动条。 这些滚动栏控件是子级`CSplitterWnd`和拆分器中共享使用不同的窗格。

例如，在第 1 行 x 2 列窗口中，您可以指定 WS_VSCROLL 创建时`CSplitterWnd`。 Windows 创建特殊的滚动条控件的两个窗格之间共享。

```
[      ][      ][^]
[pane00][pane01][|]
[      ][      ][v]
```

当用户移动滚动条时，WM_VSCROLL 消息将发送到这两个视图中。 当任一视图设置滚动条的位置时，共享的滚动条将被设置。

请注意，共享的滚动条具有类似的视图对象最有用。 如果混合使用拆分器中不同类型的视图，您可能需要写入特殊代码，以协调其滚动位置。 任何`CView`的派生类，该类使用`CWnd`Api 将如果它存在，则委托给共享的滚动条的滚动条。 `CScrollView`实现是一种`CView`类支持共享滚动条。 不派生自类`CView`，依赖于非控件滚动条的类或使用标准的 Windows 实现的类 (例如， `CEditView`) 不会使用的共享的滚动条功能`CSplitterWnd`。

## <a name="minimum-sizes"></a>最小大小

每个行是最小行高，并且每个列没有最小列宽度。 此最小值可保证不太小，无法显示完整的详细信息窗格。

对于静态拆分窗口中，初始最小行宽度和列宽度为 0。 动态拆分窗口中，初始行最小行高和列宽设置*sizeMin*参数的`CSplitterWnd::Create`函数。

可以使用来更改这些最小大小[CSplitterWnd::SetRowInfo](../mfc/reference/csplitterwnd-class.md#setrowinfo)并[CSplitterWnd::SetColumnInfo](../mfc/reference/csplitterwnd-class.md#setcolumninfo)函数。

## <a name="actual-vs-ideal-sizes"></a>实际 vs。理想的大小

拆分器窗口中窗格的布局取决于包含它们的帧的大小。 当用户调整将包含在帧`CSplitterWnd`重新定位和调整窗格大小，以便它们以及可能的组合。

用户可以手动设置行宽度和列宽度大小，或者该程序可以通过使用设置的理想大小`CSplitterWnd`类。 实际大小可能会小于或大于理想。 如果没有足够的空间来显示理想的大小或没有太多右侧或底部的拆分器窗口的空白区域，Windows 会调整的实际大小。

## <a name="custom-controls"></a>自定义控件

您可以重写很多函数以提供自定义的行为和自定义的界面。 您可以重写此第一组提供的拆分器窗口的各种图形组件的备用图像。

- `virtual void OnDrawSpltter(CDC* pDC, ESplitType nType, const CRect& rect);`

- `virtual void OnInvertTracker(const CRect& rect);`

调用此函数可创建共享的滚动条控件。 可以重写它以创建额外的控件，旁边的滚动条。

- `virtual BOOL CreateScrollBarCtrl(DWORD dwStyle, UINT nID);`

这些函数实现动态拆分窗口的逻辑。 您可以覆盖这些文件以提供更高级的拆分器逻辑。

- `virtual void DeleteView(int row, int col);`

- `virtual BOOL SplitRow(int cyBefore);`

- `virtual BOOL SplitColumn(int cxBefore);`

- `virtual void DeleteRow(int rowDelete);`

- `virtual void DeleteColumn(int colDelete);`

## <a name="cview-functionality"></a>CView 功能

`CView`类使用以下高级别命令以便委派给`CSplitterWnd`实现。 这些命令是虚拟的因为标准`CView`实现不需要整个`CSplitterWnd`中链接的实现。 使用的应用程序`CView`而非`CSplitterWnd`，则`CSplitterWnd`实现链接将不会与应用程序。

- `virtual BOOL CanActivateNext(BOOL bPrev = FALSE);`

   检查是否当前可能 ID_NEXT_PANE 或 ID_PREV_PANE。

- `virtual void ActivateNext(BOOL bPrev = FALSE);`

   执行"下一窗格"上一窗格"命令。

- `virtual BOOL DoKeyboardSplit();`

   执行键盘拆分命令，通常"窗口拆分"。

## <a name="see-also"></a>请参阅

[按编号列出的技术说明](../mfc/technical-notes-by-number.md)<br/>
[按类别列出的技术说明](../mfc/technical-notes-by-category.md)

