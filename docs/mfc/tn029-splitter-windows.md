---
title: "TN029： 拆分窗口 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.windows.splitter
dev_langs: C++
helpviewer_keywords:
- TN029
- splitter windows [MFC], about splitter windows
ms.assetid: 2c57ce99-2a3c-4eff-9cea-baccb13af075
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 95b7db2678c03b0508a1507567f8bedcf243cd4a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="tn029-splitter-windows"></a>TN029：拆分窗口
此注释描述 MFC [CSplitterWnd 类](../mfc/reference/csplitterwnd-class.md)，提供了窗口将拆分和管理其他窗格中窗口的大小调整。  
  
## <a name="splitter-styles"></a>拆分器样式  
 A`CSplitterWnd`支持两种不同样式的拆分 windows。  
  
 在"静态拆分条中，"拆分窗口在创建时创建窗格。 顺序和的窗格数永远不会更改。 拆分栏用于调整大小的不同窗格。 可以使用此样式在每个窗格中显示不同的视图类。 Visual c + + 图形编辑器和 Windows 文件管理器是使用此拆分器样式的程序的示例。 这种拆分窗口的样式不使用拆分框。  
  
 在"动态拆分条中，"其他窗格创建和销毁作为用户拆分和取消拆分新视图。 此拆分器启动时具有单个视图，并提供用户能够启动拆分的拆分框。 按一个方向拆分视图时，拆分窗口的动态创建一个新的视图对象。 此新视图对象表示的新窗格。 如果视图通过使用键盘界面拆分沿两个方向，拆分窗口将创建用于三个新窗格的三个新视图对象。 Active 拆分时，Windows 会将拆分器中显示为在窗格间拆分栏。 当用户删除拆分，但是直到拆分窗口本身的原始视图保持将被破坏，Windows 附加视图对象将销毁。 Microsoft Excel 和 Microsoft Word 都使用动态拆分器样式的应用程序的示例。  
  
 在创建这两种拆分窗口时，你必须指定行和列的拆分器将管理的最大数。 静态拆分器将创建要填充的所有行和列的窗格。 动态拆分器将创建仅的第一个窗格时`CSplitterWnd`创建。  
  
 你可以为静态拆分条中指定的窗格的最大数目是 16 行乘以 16 列。 建议的配置是：  
  
-   第 1 行 x 2 列： 通常具有不同的窗格  
  
-   2 行 x 1 列： 通常具有不同的窗格  
  
-   2 行 x 2 列： 通常具有类似的窗格  
  
 你可以为动态拆分器指定的窗格的最大数目是 2 行乘以 2 列。 建议的配置是：  
  
-   第 1 行 x 2 列： 纵栏表数据  
  
-   2 行 x 1 列： 为文本或其他数据  
  
-   2 行 x 2 列： 网格或表面向数据  
  
## <a name="splitter-examples"></a>拆分器示例  
 直接或间接，许多 MFC 示例程序使用拆分窗口。 MFC 常规示例[VIEWEX](../visual-cpp-samples.md)阐释了静态拆分条中，包括如何将拆分放入一个拆分器的几种用法。  
  
 ClassWizard 还可用于创建一个新的多个文档界面 (MDI) 子框架窗口类，其中包含拆分器窗口。 拆分窗口的详细信息，请参阅[多文档类型、 视图和框架窗口](../mfc/multiple-document-types-views-and-frame-windows.md)。  
  
## <a name="terminology-used-by-implementation"></a>通过实现使用的术语  
 下面是特定于拆分窗口的术语的列表：  
  
 `CSplitterWnd`：  
 提供的拆分窗格中的控件和行或列上的所有窗格间共享的滚动条的窗口。 从零开始的数字与指定行和列 (在第一个窗格中，行 = 0 和列 = 0)。  
  
 窗格中：  
 应用程序特定窗口，`CSplitterWnd`管理。 窗格中通常是一个对象，派生自[CView 类](../mfc/reference/cview-class.md)，但可以是任何[CWnd](../mfc/reference/cwnd-class.md)具有适当的子窗口 ID 的对象  
  
 若要使用`CWnd`-派生对象，则传递`RUNTIME_CLASS`对象与`CreateView`发挥如果已使用`CView`-派生类。 你的类必须使用`DECLARE_DYNCREATE`和`IMPLEMENT_DYNCREATE`因为框架将使用在运行时动态创建。 尽管没有大量的代码中但`CSplitterWnd`特定于`CView`类， [CObject::IsKindOf](../mfc/reference/cobject-class.md#iskindof)之前执行这些操作时始终使用。  
  
 拆分栏：  
 行和列的窗格之间放置一个控件。 它可能用于调整大小的行或列的窗格。  
  
 拆分框：  
 在动态控件`CSplitterWnd`可用来创建新行或列的窗格。 它位于顶部的垂直滚动条或水平滚动条的左侧。  
  
 拆分器交集：  
 垂直拆分条和水平拆分条的交集。 您可以拖动它以同时调整行和列的窗格的大小。  
  
## <a name="shared-scroll-bars"></a>共享的滚动条  
 `CSplitterWnd`类还支持共享的滚动条。 这些滚动栏控件是子级`CSplitterWnd`并将在拆分器的不同窗格与共享。  
  
 例如，在第 1 行 x 2 列窗口中，你可以指定 WS_VSCROLL 创建时`CSplitterWnd`。 Windows 创建特殊的滚动条控件的两个窗格之间共享。  
  
```  
[      ][      ][^]  
[pane00][pane01][|]  
[      ][      ][v]  
```  
  
 当用户将在滚动条`WM_VSCROLL`消息将发送到这两个视图。 如果其中任意一个视图设置滚动条的位置，则会将设置共享的滚动条。  
  
 请注意，共享的滚动条具有类似的视图对象最有用。 如果混合拆分中不同类型的视图，你可能需要编写特殊的代码来协调它们的滚动位置。 任何`CView`-派生类，该类使用`CWnd`如果它存在 Api 会将委托到共享的滚动条的滚动条。 `CScrollView`实现是一个示例`CView`支持的类共享滚动条。 不派生自的类`CView`，依赖于非控件滚动条的类或使用标准的 Windows 实现的类 (例如， `CEditView`) 不会使用的共享的滚动栏功能`CSplitterWnd`。  
  
## <a name="minimum-sizes"></a>最小大小  
 对于每个行中，没有最小行高度，并且为每个列没有小列宽。 满足此最低值保证窗格不太小，无法在完整的详细信息中显示。  
  
 静态拆分窗口，在初始的最小行高度和列的宽度为 0。 动态拆分窗口，在初始的最小行的高度和列宽度由设置`sizeMin`参数`CSplitterWnd::Create`函数。  
  
 你可以通过更改这些最小大小[CSplitterWnd::SetRowInfo](../mfc/reference/csplitterwnd-class.md#setrowinfo)和[CSplitterWnd::SetColumnInfo](../mfc/reference/csplitterwnd-class.md#setcolumninfo)函数。  
  
## <a name="actual-vs-ideal-sizes"></a>实际 vs。理想的大小  
 拆分器窗口中的窗格的布局取决于包含它们的帧的大小。 当用户调整大小时包含的帧，`CSplitterWnd`重新定位并调整窗格的大小，以使其适合以及可能。  
  
 用户可以手动设置行高度和列的宽度大小，或该程序可以通过使用设置的理想大小`CSplitterWnd`类。 实际大小可能会小于或大于在理想状态。 如果没有足够空间来显示理想大小，或如果没有太多右侧或底部拆分窗口的空白区域，Windows 会调整的实际大小。  
  
## <a name="custom-controls"></a>自定义控件  
 你可以重写许多功能，并提供自定义的行为和自定义的接口。 您可以重写此第一组提供拆分窗口的各种图形组件的备用图像。  
  
- `virtual void OnDrawSpltter(CDC* pDC, ESplitType nType, const CRect& rect);`  
  
- `virtual void OnInvertTracker(const CRect& rect);`  
  
 调用此函数可创建共享的滚动条控件。 你可以重写它来创建额外的控件的滚动条旁边。  
  
- `virtual BOOL CreateScrollBarCtrl(DWORD dwStyle, UINT nID);`  
  
 这些函数实现动态拆分窗口的逻辑。 您可以重写这些文件以提供更高级的拆分器逻辑。  
  
- `virtual void DeleteView(int row, int col);`  
  
- `virtual BOOL SplitRow(int cyBefore);`  
  
- `virtual BOOL SplitColumn(int cxBefore);`  
  
- `virtual void DeleteRow(int rowDelete);`  
  
- `virtual void DeleteColumn(int colDelete);`  
  
## <a name="cview-functionality"></a>CView 功能  
 `CView`类使用以下高级命令以将委派给`CSplitterWnd`实现。 这些命令是虚拟的因为标准`CView`实现不需要整个`CSplitterWnd`链接中的实现。 使用的应用程序`CView`但不是`CSplitterWnd`、`CSplitterWnd`实现将不会将链接到应用程序。  
  
 `virtual BOOL CanActivateNext(BOOL bPrev = FALSE);`  
 检查是否 ID_NEXT_PANE 或 ID_PREV_PANE 目前是可能的。  
  
 `virtual void ActivateNext(BOOL bPrev = FALSE);`  
 执行"下一步窗格"上一个窗格"的命令。  
  
 `virtual BOOL DoKeyboardSplit();`  
 执行键盘拆分命令，通常"窗口拆分"。  
  
## <a name="see-also"></a>请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)

