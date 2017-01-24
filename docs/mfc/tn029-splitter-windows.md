---
title: "TN029：拆分窗口 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.windows.splitter"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "拆分窗口, 关于拆分窗口"
  - "TN029"
ms.assetid: 2c57ce99-2a3c-4eff-9cea-baccb13af075
caps.latest.revision: 18
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN029：拆分窗口
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此注释说明 MFC [CSplitterWnd Class](../mfc/reference/csplitterwnd-class.md)，提供窗口分割和管理窗格窗口的大小。  
  
## 拆分样式  
 `CSplitterWnd` 支持拆分窗口的两个不同样式。  
  
 在“静态拆分”中，拆分窗口创建窗格。  窗格的顺序和数目永不更改。  拆分条用于调整窗格大小。  可以使用此样式显示每一个窗格的不同的视图类。  Visual C\+\+ 图形编辑器和Windows文件管理器是使用此拆分样式的示例。  此拆分窗口的样式不使用拆分框。  
  
 在“动态拆分“中，当用户拆分时，其他窗格被创建，非拆分时，则销毁。  此拆分以单个视图开始并为用户提供拆分框来启动拆分。  当视图被拆分为耽搁方向时，拆分窗口动态创建新的视图对象。  此新的视图对象表示新的窗格。  使用键盘接口，则视图拆分为两个方向，拆分窗口为三个新窗格创建三个新的视图对象。  在拆分激活时，窗口显示拆分框为在窗格之间的一个拆分栏。  当用户移除已拆分时，窗口销毁附加视图对象，但原始视图保持，直到销毁拆分窗口。  Microsoft Excel 和 Microsoft Word 使用的是动态拆分样式的应用程序示例。  
  
 当您创建其中一类拆分窗口时，必须指定拆分器管理的最大行数和列数。  静态拆分将创建窗格填充所有行和列。  在创建 `CSplitterWnd`时，动态拆分器将只创建第一个窗格。  
  
 可以指定的静态拆分窗格的最大数是16 行乘16 列。  建议的配置是：  
  
-   1 行 2 列：通常与不同的窗格  
  
-   2 行 1 列：通常与不同的窗格  
  
-   2 行 2 列：通常与相同的窗格  
  
 您可以为动态拆分窗格指定的最大数是 2 行乘 2 列。  建议的配置是：  
  
-   1 行 2 列：负责柱状数据  
  
-   x 2 行 1 列：对于文本或其他数据  
  
-   2 行 2 列：对于网格或表中的数据  
  
## 拆分示例  
 许多 MFC 示例程序中直接或间接使用拆分窗口。  MFC 泛型示例 [VIEWEX](../top/visual-cpp-samples.md) 阐释了静态拆分的多种用途，包括如何将在拆分中放置拆分器。  
  
 还可以使用类向导创建包含拆分窗口的新的多文档界面 \(MDI\) 的子框架窗口类。  有关拆分窗口的更多信息，请参见 [多文档类型、视图和框架窗口](../mfc/multiple-document-types-views-and-frame-windows.md)。  
  
## 实现使用的术语  
 这是一个拆分窗口的术语列表：  
  
 `CSplitterWnd`:  
 提供拆分窗格控件的窗口和在所有窗格或列之间共享的滚动条。  从零开始的数字分配行号和列号 \(第一个窗格的行为0，列为0\)。  
  
 窗格:  
 `CSplitterWnd` 管理程序特定的窗口。  窗格通常是从 [CView Class](../mfc/reference/cview-class.md)派生的对象，不过，可能具有相应的子窗口ID的 [CWnd](../mfc/reference/cwnd-class.md)对象  
  
 使用 `CWnd`的派生对象，如果使用 `CView`派生类，传递对象的 `RUNTIME_CLASS`给`CreateView` 的函数。  因为框架在运行时使用动态创建，必须使用 `DECLARE_DYNCREATE` 和 `IMPLEMENT_DYNCREATE`。  虽然`CView` 类有许多特定的 `CSplitterWnd` 代码，但在这些操作之前，经常使用 [CObject::IsKindOf](../Topic/CObject::IsKindOf.md)，。  
  
 拆分条：  
 放置在窗格行和列之间的控件。  它可能用于调整窗格行或列的大小。  
  
 拆分框：  
 可用于创建窗格的新行或新列的动态 `CSplitterWnd` 控件。  它位于垂直滚动条顶部或左侧水平滚动条的左边。  
  
 拆分交集：  
 垂直的拆分栏和一个水平拆分条的交集。  可以拖动它同时调整窗格行和列的大小。  
  
## 共享滚动条  
 `CSplitterWnd` 类还支持共享的滚动条。  这些滚动条控件是 `CSplitterWnd` 的子项，在拆分的不同窗格间共享。  
  
 例如，在创建 `CSplitterWnd`时，在 1 x 行 2 列的窗口，可以指定 WS\_VSCROLL。  窗口创建在两个窗格之间共享的特殊滚动条控件。  
  
```  
[      ][      ][^]  
[pane00][pane01][|]  
[      ][      ][v]  
```  
  
 当用户移动滚动条时，`WM_VSCROLL` 信息将发送到两个视图。  当任何视图设置滚动条的位置时，将设置共享滚动条。  
  
 注意共享滚动条是相同的视图对象最有用的办法。  如果混合视图的不同类型拆分，则可能必须编写特殊代码协调它们的滚动位置。  如果存在，任何使用`CWnd` 滚动条的 API 的`CView`派生类将委托给共享滚动条。  `CScrollView` 实现支持共享的滚动条的 `CView` 类的一个示例。  从 `CView`派生的类，不依赖于非控件滚动条或者使用 Windows 实现的类 \(例如，`CEditView`\)， 将不会使用 `CSplitterWnd`共享条滚动功能。  
  
## 最小大小  
 每行都有最小的行高，因此，每列具有最小的列宽。  至少保证窗格在详细信息中不是太小而无法显示。  
  
 对于静态拆分窗口，初始最小的行高和列宽为 0。  对于动态拆分窗口，初始最小的行高和列宽由 `CSplitterWnd::Create` 函数的 `sizeMin` 参数设置。  
  
 使用 [CSplitterWnd::SetRowInfo](../Topic/CSplitterWnd::SetRowInfo.md)和[CSplitterWnd::SetColumnInfo](../Topic/CSplitterWnd::SetColumnInfo.md) 函数更改最小大小。  
  
## 实际大小与理想大小比较  
 拆分窗口的窗格的布局依赖于包含它们的框架大小。  当用户调整包含的帧时，`CSplitterWnd` 将尽可能重新定位并调整窗格。  
  
 用户可以手动设置行高和列宽大小，或使用 `CSplitterWnd` 类设置理想的大小。  实际大小可以小或大于理想大小。  如果没有足够的空间查看需要的大小或者在拆分窗口的底部有多个空格，窗口将调整实际大小。  
  
## 自定义控件  
 可以用许多函数提供的自定义行为和自定义的接口。  您可以重写此设置为拆分窗口的各种图形组件提供可选方案。  
  
-   `virtual void OnDrawSpltter(CDC* pDC, ESplitType nType, const CRect& rect);`  
  
-   `virtual void OnInvertTracker(const CRect& rect);`  
  
 您调用此函数创建共享的滚动条控件。  可以重写它，创建滚动条控件的另一个控件。  
  
-   `virtual BOOL CreateScrollBarCtrl(DWORD dwStyle, UINT nID);`  
  
 这些函数实现动态拆分窗口的逻辑。  您可以重写这些函数，提供更高级拆分逻辑。  
  
-   `virtual void DeleteView(int row, int col);`  
  
-   `virtual BOOL SplitRow(int cyBefore);`  
  
-   `virtual BOOL SplitColumn(int cxBefore);`  
  
-   `virtual void DeleteRow(int rowDelete);`  
  
-   `virtual void DeleteColumn(int colDelete);`  
  
## CView 功能  
 `CView` 类使用以下高级命令,委托给 `CSplitterWnd` 实现。  由于这些命令是虚拟的，标准 `CView` 实现不要求整个 `CSplitterWnd` 实现的链接。  对于不使用 `CView`，但使用 `CSplitterWnd`的应用程序，`CSplitterWnd` 实现不会与应用程序链接。  
  
 `virtual BOOL CanActivateNext(BOOL bPrev = FALSE);`  
 检查 ID\_NEXT\_PANE 或 ID\_PREV\_PANE 是否为当前有效。  
  
 `virtual void ActivateNext(BOOL bPrev = FALSE);`  
 执行“下一个窗格”或“上一个窗格”命令。  
  
 `virtual BOOL DoKeyboardSplit();`  
 执行键盘拆分命令，通常是“窗口拆分”。  
  
## 请参阅  
 [按编号列出的技术说明](../mfc/technical-notes-by-number.md)   
 [按类别列出的技术说明](../mfc/technical-notes-by-category.md)