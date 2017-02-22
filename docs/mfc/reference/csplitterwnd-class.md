---
title: "CSplitterWnd Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSplitterWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSplitterWnd class"
  - "dynamic splitter windows"
  - "多个视图"
  - "拆分窗口"
  - "static splitter windows"
  - "视图, 每个框架有多个"
ms.assetid: fd0de258-6dbe-4552-9e47-a39de0471d51
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CSplitterWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供拆分窗口的功能，是窗口包含多个窗格。  
  
## 语法  
  
```  
class CSplitterWnd : public CWnd  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CSplitterWnd::CSplitterWnd](../Topic/CSplitterWnd::CSplitterWnd.md)|调用构造 `CSplitterWnd` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CSplitterWnd::ActivateNext](../Topic/CSplitterWnd::ActivateNext.md)|执行下一个窗格或个窗格命令。|  
|[CSplitterWnd::CanActivateNext](../Topic/CSplitterWnd::CanActivateNext.md)|检查下一个窗格或个窗格命令当前是否可能的。|  
|[CSplitterWnd::Create](../Topic/CSplitterWnd::Create.md)|调用创建动态拆分窗口并将其附加到 `CSplitterWnd` 对象。|  
|[CSplitterWnd::CreateScrollBarCtrl](../Topic/CSplitterWnd::CreateScrollBarCtrl.md)|创建一个共享滚动条控件。|  
|[CSplitterWnd::CreateStatic](../Topic/CSplitterWnd::CreateStatic.md)|调用创建静态拆分窗口并将其附加到 `CSplitterWnd` 对象。|  
|[CSplitterWnd::CreateView](../Topic/CSplitterWnd::CreateView.md)|调用创建窗格在拆分窗口。|  
|[CSplitterWnd::DeleteColumn](../Topic/CSplitterWnd::DeleteColumn.md)|从拆分窗口删除该列。|  
|[CSplitterWnd::DeleteRow](../Topic/CSplitterWnd::DeleteRow.md)|从拆分窗口删除行。|  
|[CSplitterWnd::DeleteView](../Topic/CSplitterWnd::DeleteView.md)|从拆分窗口delete视图。|  
|[CSplitterWnd::DoKeyboardSplit](../Topic/CSplitterWnd::DoKeyboardSplit.md)|执行键盘部件的命令，通常为“windows "拆分”。|  
|[CSplitterWnd::DoScroll](../Topic/CSplitterWnd::DoScroll.md)|performs同步拆分窗口滚动。|  
|[CSplitterWnd::DoScrollBy](../Topic/CSplitterWnd::DoScrollBy.md)|滚动由像素的许多拆分了窗口。|  
|[CSplitterWnd::GetActivePane](../Topic/CSplitterWnd::GetActivePane.md)|确定活动的窗格从重点或活动视图）。|  
|[CSplitterWnd::GetColumnCount](../Topic/CSplitterWnd::GetColumnCount.md)|返回当前窗格列计数。|  
|[CSplitterWnd::GetColumnInfo](../Topic/CSplitterWnd::GetColumnInfo.md)|返回有关指定列的信息。|  
|[CSplitterWnd::GetPane](../Topic/CSplitterWnd::GetPane.md)|返回窗格中指定的行和列。|  
|[CSplitterWnd::GetRowCount](../Topic/CSplitterWnd::GetRowCount.md)|返回当前窗格行数。|  
|[CSplitterWnd::GetRowInfo](../Topic/CSplitterWnd::GetRowInfo.md)|返回有关指定的行的信息。|  
|[CSplitterWnd::GetScrollStyle](../Topic/CSplitterWnd::GetScrollStyle.md)|返回共享滚动条样式。|  
|[CSplitterWnd::IdFromRowCol](../Topic/CSplitterWnd::IdFromRowCol.md)|返回窗格的子窗口ID在指定的行和列。|  
|[CSplitterWnd::IsChildPane](../Topic/CSplitterWnd::IsChildPane.md)|调用确定窗口当前是否此拆分窗口子窗格。|  
|[CSplitterWnd::IsTracking](../Topic/CSplitterWnd::IsTracking.md)|确定拆分栏当前是否正在移动。|  
|[CSplitterWnd::RecalcLayout](../Topic/CSplitterWnd::RecalcLayout.md)|调用调整行或列的大小之后重新显示拆分窗口。|  
|[CSplitterWnd::SetActivePane](../Topic/CSplitterWnd::SetActivePane.md)|设置窗格有效一个在框架。|  
|[CSplitterWnd::SetColumnInfo](../Topic/CSplitterWnd::SetColumnInfo.md)|调用将指定的列信息。|  
|[CSplitterWnd::SetRowInfo](../Topic/CSplitterWnd::SetRowInfo.md)|调用将指定的行信息。|  
|[CSplitterWnd::SetScrollStyle](../Topic/CSplitterWnd::SetScrollStyle.md)|为拆分窗口的共享滚动条指定新的滚动条样式支持。|  
|[CSplitterWnd::SplitColumn](../Topic/CSplitterWnd::SplitColumn.md)|指示框架窗口位置垂直拆分。|  
|[CSplitterWnd::SplitRow](../Topic/CSplitterWnd::SplitRow.md)|指示框架窗口位置水平拆分。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CSplitterWnd::OnDraw](../Topic/CSplitterWnd::OnDraw.md)|调用由框架绘制拆分窗口。|  
|[CSplitterWnd::OnDrawSplitter](../Topic/CSplitterWnd::OnDrawSplitter.md)|呈现拆分窗口的图像。|  
|[CSplitterWnd::OnInvertTracker](../Topic/CSplitterWnd::OnInvertTracker.md)|呈现拆分窗口的图像相同大小和形状与框架窗口。|  
  
## 备注  
 窗格通常是从派生 [CView](../../mfc/reference/cview-class.md)特定的对象，但是，它可以是具有适当的子窗口. ID的所有 [CWnd](../../mfc/reference/cwnd-class.md) 对象  
  
 `CSplitterWnd` 对象在父 [CFrameWnd](../../mfc/reference/cframewnd-class.md) 或 [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) 对象通常中。  使用下面的步骤，创建一 `CSplitterWnd` 对象:  
  
1.  嵌入一个 `CSplitterWnd` 成员变量在父级框架。  
  
2.  重写父级框架的 [CFrameWnd::OnCreateClient](../Topic/CFrameWnd::OnCreateClient.md) 成员函数。  
  
3.  从重写的 `OnCreateClient`的内部，请调用 `CSplitterWnd`的 [创建](../Topic/CSplitterWnd::Create.md) 或 [CreateStatic](../Topic/CSplitterWnd::CreateStatic.md) 成员函数。  
  
 调用 **Create** 成员函数创建动态拆分窗口。  动态拆分窗口通常用于创建和移动许多各个窗格，或视图，同一文档。  框架自动创建拆分的初始窗格;然后，当用户操作拆分窗口的控制器，结构创建，调整大小，并且处理其他的窗格。  
  
 当您调用 **Create**时，需要指定标识的最小行高度和列宽窗格时太小而无法完全显示。  在调用 **Create**之后，您可以通过调用 [SetColumnInfo](../Topic/CSplitterWnd::SetColumnInfo.md) 和 [SetRowInfo](../Topic/CSplitterWnd::SetRowInfo.md) 成员调整这些最小值功能。  
  
 以及使用 `SetColumnInfo` 和 `SetRowInfo` 成员函数上设置列的“理想的”宽度和“行的理想”高度。  当框架显示拆分窗口时，它首先显示父级框架，然后拆分窗口。  框架根据需要的维度然后计划列中的窗格和行工作，从左上角到拆分窗口的工作区的右下角。  
  
 在动态拆分窗口的所有窗格必须属于同一个类。  支持动态拆分窗口的熟悉应用程序包括Microsoft Word和Microsoft Excel。  
  
 使用 `CreateStatic` 成员函数创建静态拆分窗口。  用户可以更改窗格的大小仅在静态拆分窗口的，不包括数目或序列。  
  
 在创建静态拆分器时，必须明确地创建所有静态拆分窗格中。  请确保您创建所有窗格中，在父帧的 `OnCreateClient` 成员函数返回之前，或框架不会正确显示窗口。  
  
 `CreateStatic` 成员函数将自动初始化具有最低的行高度和列宽的一个静态拆分为0。  在调用 **Create**后，通过调用 [SetColumnInfo](../Topic/CSplitterWnd::SetColumnInfo.md) 和 [SetRowInfo](../Topic/CSplitterWnd::SetRowInfo.md) 成员调整这些最小值功能。  此外，在调用 `CreateStatic` 指示所需要的窗格维度后，请使用 `SetColumnInfo` 和 `SetRowInfo`。  
  
 一个静态拆分的各个窗格通常属于不同的选件类。  以静态拆分窗口的示例，请参见图形编辑器和Windows文件管理器。  
  
 拆分窗口支持特定滚动条\(除了窗格可以有\)滚动条外部。  这些滚动条是 `CSplitterWnd` 对象的子项和控件和共享。  
  
 在创建拆分窗口时，您创建这些特殊滚动条。  例如，`CSplitterWnd` 一行，两列和 **WS\_VSCROLL** 样式将显示由两个窗格共享的垂直滚动条。  当用户移动滚动条时，`WM_VSCROLL` 发送到两个窗格。  在窗格将滚动条位置时，共享滚动条设置。  
  
 有关拆分窗口的详细信息，请参见:  
  
-   [技术说明29](../../mfc/tn029-splitter-windows.md)  
  
-   知识库文章Q262024:HOWTO:使用CPropertySheet作为CSplitterWnd的子级  
  
 有关如何创建动态拆分窗口的更多信息，请参见:  
  
-   MFC示例 [scribble](../../top/visual-cpp-samples.md)  
  
-   MFC示例 [VIEWEX](../../top/visual-cpp-samples.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSplitterWnd`  
  
## 要求  
 **Header:** afxext.h  
  
## 请参阅  
 [MFC示例VIEWEX](../../top/visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)