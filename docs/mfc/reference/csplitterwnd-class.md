---
title: "CSplitterWnd 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 706425dd8d729937d310da9cc2f09eac8ec1ad57
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
|[CSplitterWnd::CSplitterWnd](#csplitterwnd)|调用以构造`CSplitterWnd`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CSplitterWnd::ActivateNext](#activatenext)|执行下一个窗格或上一个窗格的命令。|  
|[CSplitterWnd::CanActivateNext](#canactivatenext)|检查以确定是否当前可能的下一个窗格或上一个窗格的命令。|  
|[CSplitterWnd::Create](#create)|调用以创建动态拆分窗口，然后将其附加到`CSplitterWnd`对象。|  
|[CSplitterWnd::CreateScrollBarCtrl](#createscrollbarctrl)|创建共享的滚动条控件。|  
|[CSplitterWnd::CreateStatic](#createstatic)|调用要创建静态拆分窗口，并将其附加到`CSplitterWnd`对象。|  
|[CSplitterWnd::CreateView](#createview)|若要在拆分窗口创建窗格的调用。|  
|[CSplitterWnd::DeleteColumn](#deletecolumn)|拆分器窗口中删除某一列。|  
|[CSplitterWnd::DeleteRow](#deleterow)|从拆分器窗口中删除行。|  
|[CSplitterWnd::DeleteView](#deleteview)|从拆分器窗口中删除视图。|  
|[CSplitterWnd::DoKeyboardSplit](#dokeyboardsplit)|执行键盘拆分命令，通常"窗口拆分。"|  
|[CSplitterWnd::DoScroll](#doscroll)|执行同步滚动拆分窗口。|  
|[CSplitterWnd::DoScrollBy](#doscrollby)|滚动拆分窗口按给定数量的像素。|  
|[CSplitterWnd::GetActivePane](#getactivepane)|确定活动窗格从焦点或框架中的活动视图。|  
|[CSplitterWnd::GetColumnCount](#getcolumncount)|返回当前窗格中列数。|  
|[CSplitterWnd::GetColumnInfo](#getcolumninfo)|返回指定的列信息。|  
|[CSplitterWnd::GetPane](#getpane)|返回在指定的行和列的窗格。|  
|[CSplitterWnd::GetRowCount](#getrowcount)|返回当前窗格行计数。|  
|[CSplitterWnd::GetRowInfo](#getrowinfo)|返回有关指定的行信息。|  
|[CSplitterWnd::GetScrollStyle](#getscrollstyle)|返回共享的滚动条样式。|  
|[CSplitterWnd::IdFromRowCol](#idfromrowcol)|返回子窗口 ID 在指定的行和列的窗格。|  
|[CSplitterWnd::IsChildPane](#ischildpane)|若要确定窗口是否是当前该拆分器窗口的子窗格中的调用。|  
|[CSplitterWnd::IsTracking](#istracking)|确定当前移动拆分栏。|  
|[CSplitterWnd::RecalcLayout](#recalclayout)|若要重新拆分窗口显示行或列大小调整后的调用。|  
|[CSplitterWnd::SetActivePane](#setactivepane)|将窗格使处于活动状态的帧中的设置。|  
|[CSplitterWnd::SetColumnInfo](#setcolumninfo)|用于设置指定的列信息的调用。|  
|[CSplitterWnd::SetRowInfo](#setrowinfo)|用于设置指定的行信息的调用。|  
|[CSplitterWnd::SetScrollStyle](#setscrollstyle)|指定拆分窗口的滚动条新式共享滚动条支持。|  
|[CSplitterWnd::SplitColumn](#splitcolumn)|指示框架窗口垂直拆分的位置。|  
|[CSplitterWnd::SplitRow](#splitrow)|指示框架窗口水平拆分的位置。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CSplitterWnd::OnDraw](#ondraw)|由框架调用以绘制拆分窗口。|  
|[CSplitterWnd::OnDrawSplitter](#ondrawsplitter)|将拆分窗口的图像的渲染。|  
|[CSplitterWnd::OnInvertTracker](#oninverttracker)|呈现拆分窗口是相同的大小和形状一样的框架窗口的图像。|  
  
## <a name="remarks"></a>备注  
 窗格中通常是一个应用程序特定对象，派生自[CView](../../mfc/reference/cview-class.md)，但它可以是任何[CWnd](../../mfc/reference/cwnd-class.md)具有适当的子窗口 ID 的对象  
  
 A`CSplitterWnd`对象通常会嵌入父[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)对象。 创建`CSplitterWnd`对象使用以下步骤：  
  
1.  嵌入`CSplitterWnd`成员变量中的父框架。  
  
2.  重写的父框架[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)成员函数。  
  
3.  从中重写`OnCreateClient`，调用[创建](#create)或[CreateStatic](#createstatic)成员函数`CSplitterWnd`。  
  
 调用**创建**成员函数来创建动态拆分窗口。 动态拆分窗口通常用于创建和滚动大量的各个窗格或同一文档的视图。 框架会自动创建的初始窗格拆分器;然后框架创建、 调整大小，并释放的其他窗格，如用户的操作拆分窗口的控件。  
  
 当调用**创建**，指定确定何时将窗格太小而无法完全显示一个最小行高度和列宽度。 调用后**创建**，你可以通过调用来调整这些最小值[SetColumnInfo](#setcolumninfo)和[SetRowInfo](#setrowinfo)成员函数。  
  
 此外使用`SetColumnInfo`和`SetRowInfo`成员函数来设置列"理想"宽度和行"理想"高度。 当框架显示拆分窗口时，它首先显示的父框架，然后拆分窗口。 框架然后是根据其理想的尺寸，处理从左上角到右下角的拆分器窗口工作区的行和列中的窗格布局。  
  
 动态拆分窗口中的所有窗格都必须属于相同的类。 熟悉支持动态拆分窗口的应用程序包括 Microsoft Word 和 Microsoft Excel。  
  
 使用`CreateStatic`成员函数来创建一个静态拆分窗口。 用户可以更改仅在静态拆分窗口，而不其编号或订单中的窗格的大小。  
  
 在创建静态拆分时，你必须专门创建所有静态拆分的窗格。 请确保你创建的父框架之前的所有窗格`OnCreateClient`成员函数返回时或该框架将不会正确显示窗口。  
  
 `CreateStatic`成员函数可以自动初始化静态拆分最小行高度和列宽度为 0。 调用后**创建**，调整这些最小值通过调用[SetColumnInfo](#setcolumninfo)和[SetRowInfo](#setrowinfo)成员函数。 此外使用`SetColumnInfo`和`SetRowInfo`调用后`CreateStatic`以指示所需的理想的窗格中的维度。  
  
 静态拆分的单个窗格通常属于不同的类。 静态拆分窗口的示例，请参阅图形编辑器和 Windows 文件管理器。  
  
 拆分窗口支持 （脱离窗格可能具有的滚动条） 的特殊的滚动条。 这些滚动条是子级`CSplitterWnd`对象，并与窗格共享。  
  
 在创建拆分窗口时，你可以创建这些特殊的滚动条。 例如，`CSplitterWnd`具有一行、 两个列和**WS_VSCROLL**样式将显示垂直滚动条所共享的两个窗格。 当用户将在滚动条`WM_VSCROLL`消息发送到这两个窗格。 当窗格设置滚动条位置时，设置共享的滚动条。  
  
 拆分窗口的详细信息，请参阅：  
  
- [技术说明 29](../../mfc/tn029-splitter-windows.md)  
  
-   知识库文章 Q262024： 如何： 使用 CPropertySheet 作为子 CSplitterWnd  
  
 有关如何创建动态拆分窗口的详细信息，请参阅：  
  
-   MFC 示例[Scribble](../../visual-cpp-samples.md)  
  
-   MFC 示例[VIEWEX](../../visual-cpp-samples.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSplitterWnd`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxext.h  
  
##  <a name="activatenext"></a>CSplitterWnd::ActivateNext  
 由框架调用以执行下一个窗格或上一个窗格的命令。  
  
```  
virtual void ActivateNext(BOOL bPrev = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `bPrev`  
 指示要激活的窗口。 **TRUE**为以前;**FALSE**的下一步。  
  
### <a name="remarks"></a>备注  
 此成员函数是一个高级别的命令，可供[CView](../../mfc/reference/cview-class.md)类若要委托给`CSplitterWnd`实现。  
  
##  <a name="canactivatenext"></a>CSplitterWnd::CanActivateNext  
 由框架调用以检查下一个窗格或上一个窗格命令当前可能。  
  
```  
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `bPrev`  
 指示要激活的窗口。 **TRUE**为以前;**FALSE**的下一步。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数是一个高级别的命令，可供[CView](../../mfc/reference/cview-class.md)类若要委托给`CSplitterWnd`实现。  
  
##  <a name="create"></a>CSplitterWnd::Create  
 若要创建动态拆分窗口，调用**创建**成员函数。  
  
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
 `pParentWnd`  
 拆分窗口的父框架窗口。  
  
 *nMaxRows*  
 最大拆分器窗口中的行数。 此值不能超过 2。  
  
 *nMaxCols*  
 最大拆分器窗口中的列数。 此值不能超过 2。  
  
 `sizeMin`  
 指定一个窗格可能会显示的最小大小。  
  
 `pContext`  
 指向的指针[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)结构。 在大多数情况下，这可能是`pContext`传递到父框架窗口。  
  
 `dwStyle`  
 指定的窗口样式。  
  
 `nID`  
 窗口的子窗口 ID。 该 ID 可以是**AFX_IDW_PANE_FIRST**除非拆分窗口的嵌套在另一个拆分器窗口的内部。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 您可以将嵌入`CSplitterWnd`的父文件夹中[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)对象执行以下步骤：  
  
1.  嵌入`CSplitterWnd`成员变量中的父框架。  
  
2.  重写的父框架[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)成员函数。  
  
3.  调用**创建**从中重写的成员函数`OnCreateClient`。  
  
 创建从在父范围内的产生拆分器窗口时, 传递的父框架`pContext`拆分窗口的参数。 否则，此参数可以是**NULL**。  
  
 动态拆分窗口的初始最小行高度和列宽度由`sizeMin`参数。 这些最小值，用于确定是否太小，无法显示在其整个窗格中，可以更改与[SetRowInfo](#setrowinfo)和[SetColumnInfo](#setcolumninfo)成员函数。  
  
 有关动态拆分窗口的详细信息，请参阅"拆分窗口"中文章[多文档类型、 视图和框架窗口](../../mfc/multiple-document-types-views-and-frame-windows.md)，[技术注意 29](../../mfc/tn029-splitter-windows.md)，和`CSplitterWnd`类概述。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#125](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]  
  
##  <a name="createscrollbarctrl"></a>CSplitterWnd::CreateScrollBarCtrl  
 由框架调用以创建共享的滚动条控件。  
  
```  
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 指定的窗口样式。  
  
 `nID`  
 窗口的子窗口 ID。 该 ID 可以是**AFX_IDW_PANE_FIRST**除非拆分窗口的嵌套在另一个拆分器窗口的内部。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 重写`CreateScrollBarCtrl`若要包括的滚动条旁边的额外控件。 默认行为是创建正常 Windows 滚动条控件。  
  
##  <a name="createstatic"></a>CSplitterWnd::CreateStatic  
 若要创建静态拆分窗口，调用`CreateStatic`成员函数。  
  
```  
virtual BOOL CreateStatic(
    CWnd* pParentWnd,  
    int nRows,  
    int nCols,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,  
    UINT nID = AFX_IDW_PANE_FIRST);
```  
  
### <a name="parameters"></a>参数  
 `pParentWnd`  
 拆分窗口的父框架窗口。  
  
 `nRows`  
 行数。 此值不能超过 16。  
  
 *nCols*  
 列数。 此值不能超过 16。  
  
 `dwStyle`  
 指定的窗口样式。  
  
 `nID`  
 窗口的子窗口 ID。 该 ID 可以是**AFX_IDW_PANE_FIRST**除非拆分窗口的嵌套在另一个拆分器窗口的内部。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 A`CSplitterWnd`通常会嵌入在父`CFrameWnd`或[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)对象执行以下步骤：  
  
1.  嵌入`CSplitterWnd`成员变量中的父框架。  
  
2.  重写的父框架`OnCreateClient`成员函数。  
  
3.  调用`CreateStatic`从中重写的成员函数[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)。  
  
 静态拆分窗口包含固定的数量的窗格，通常从不同的类。  
  
 在创建静态拆分窗口时，你必须在同一时间创建所有窗格。 [对 CreateView](#createview)成员函数通常用于此目的，但你可以创建其他的 nonview 类。  
  
 静态拆分窗口的初始最小行高度和列宽度为 0。 这些最小值，这些扩展名决定了太小，无法显示在其整个窗格中时，可以更改与[SetRowInfo](#setrowinfo)和[SetColumnInfo](#setcolumninfo)成员函数。  
  
 若要添加到静态拆分窗口的滚动条，添加**WS_HSCROLL**和**WS_VSCROLL**样式`dwStyle`。  
  
 请参阅本文中的"拆分窗口"[多文档类型、 视图和框架窗口](../../mfc/multiple-document-types-views-and-frame-windows.md)，[技术注意 29](../../mfc/tn029-splitter-windows.md)，和`CSplitterWnd`类概述有关静态拆分窗口的详细信息。  
  
##  <a name="createview"></a>CSplitterWnd::CreateView  
 创建静态拆分窗口的窗格。  
  
```  
virtual BOOL CreateView(
    int row,  
    int col,  
    CRuntimeClass* pViewClass,  
    SIZE sizeInit,  
    CCreateContext* pContext);
```  
  
### <a name="parameters"></a>参数  
 `row`  
 指定要在其中放置新视图的拆分器窗口行。  
  
 `col`  
 指定要在其中放置新视图的拆分器窗口列。  
  
 `pViewClass`  
 指定[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)的新视图。  
  
 *sizeInit*  
 指定新视图的初始大小。  
  
 `pContext`  
 一个指向用于创建视图创建上下文 (通常`pContext`传入的父框架重写[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)在其中创建拆分窗口的成员函数)。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 框架显示拆分器之前，必须创建静态拆分窗口的所有窗格。  
  
 框架还会调用此成员函数来创建新窗格时动态拆分窗口的用户将拆分窗格、 行或列。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]  
  
##  <a name="csplitterwnd"></a>CSplitterWnd::CSplitterWnd  
 调用以构造`CSplitterWnd`对象。  
  
```  
CSplitterWnd();
```  
  
### <a name="remarks"></a>备注  
 构造`CSplitterWnd`两个步骤中的对象。 首先，调用的构造函数，这将创建`CSplitterWnd`对象，，然后调用[创建](#create)成员函数，其创建拆分器窗口，并将其附加到`CSplitterWnd`对象。  
  
##  <a name="deletecolumn"></a>CSplitterWnd::DeleteColumn  
 拆分器窗口中删除某一列。  
  
```  
virtual void DeleteColumn(int colDelete);
```  
  
### <a name="parameters"></a>参数  
 *colDelete*  
 指定要删除的列。  
  
### <a name="remarks"></a>备注  
 由框架实现动态拆分窗口的逻辑调用此成员函数 (即，如果拆分窗口具有**SPLS_DYNAMIC_SPLIT**样式)。 它可以进行自定义，以及虚拟函数[对 CreateView](#createview)，以实现更高级的动态拆分器。  
  
##  <a name="deleterow"></a>CSplitterWnd::DeleteRow  
 从拆分器窗口中删除行。  
  
```  
virtual void DeleteRow(int rowDelete);
```  
  
### <a name="parameters"></a>参数  
 *行删除*  
 指定要删除的行。  
  
### <a name="remarks"></a>备注  
 由框架实现动态拆分窗口的逻辑调用此成员函数 (即，如果拆分窗口具有**SPLS_DYNAMIC_SPLIT**样式)。 它可以进行自定义，以及虚拟函数[对 CreateView](#createview)，以实现更高级的动态拆分器。  
  
##  <a name="deleteview"></a>CSplitterWnd::DeleteView  
 从拆分器窗口中删除视图。  
  
```  
virtual void DeleteView(
    int row,  
    int col);
```  
  
### <a name="parameters"></a>参数  
 `row`  
 指定用于删除视图的拆分器窗口行。  
  
 `col`  
 指定用于删除视图的拆分器窗口列。  
  
### <a name="remarks"></a>备注  
 如果正在删除活动的视图，下一步视图将处于活动状态。 默认实现假设该视图将自动删除在[PostNcDestroy](../../mfc/reference/cwnd-class.md#postncdestroy)。  
  
 由框架实现动态拆分窗口的逻辑调用此成员函数 (即，如果拆分窗口具有**SPLS_DYNAMIC_SPLIT**样式)。 它可以进行自定义，以及虚拟函数[对 CreateView](#createview)，以实现更高级的动态拆分器。  
  
##  <a name="dokeyboardsplit"></a>CSplitterWnd::DoKeyboardSplit  
 执行键盘拆分命令，通常"窗口拆分。"  
  
```  
virtual BOOL DoKeyboardSplit();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数是一个高级别的命令，可供[CView](../../mfc/reference/cview-class.md)类若要委托给`CSplitterWnd`实现。  
  
##  <a name="doscroll"></a>CSplitterWnd::DoScroll  
 执行同步滚动拆分窗口。  
  
```  
virtual BOOL DoScroll(
    CView* pViewFrom,  
    UINT nScrollCode,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `pViewFrom`  
 指向滚动消息所源自的视图的指针。  
  
 `nScrollCode`  
 指示的用户的滚动条代码的滚动请求。 此参数由两个部分组成： 低序位字节，用于确定滚动正在进行水平的类型，并确定的一种滚动发生垂直高序位字节：  
  
- **SB_BOTTOM**滚动到下的顺序。  
  
- **SB_LINEDOWN**向下滚动一行。  
  
- **SB_LINEUP**向上滚动一行。  
  
- **SB_PAGEDOWN**向下滚动一页。  
  
- **SB_PAGEUP**向上滚动一页。  
  
- **SB_TOP**滚动到顶部。  
  
 `bDoScroll`  
 确定是否执行了指定滚动操作。 如果`bDoScroll`是**TRUE** （即，如果存在子窗口，并在拆分窗口具有滚动范围），然后指定滚动操作可能需要的位置; 如果`bDoScroll`是**FALSE** （即，如果没有子窗口存在，或者拆分视图具有任何滚动范围），然后滚动不会发生。  
  
### <a name="return-value"></a>返回值  
 发生滚动如果同步的则为非 0;否则为 0。  
  
### <a name="remarks"></a>备注  
 由框架执行同步滚动拆分窗口的视图接收滚动消息时调用此成员函数。 重写以同步滚动允许之前需要用户执行操作。  
  
##  <a name="doscrollby"></a>CSplitterWnd::DoScrollBy  
 滚动拆分窗口按给定数量的像素。  
  
```  
virtual BOOL DoScrollBy(
    CView* pViewFrom,  
    CSize sizeScroll,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `pViewFrom`  
 指向滚动消息所源自的视图的指针。  
  
 `sizeScroll`  
 水平和垂直滚动的像素数。  
  
 bDoScroll  
 确定是否执行了指定滚动操作。 如果`bDoScroll`是**TRUE** （即，如果存在子窗口，并在拆分窗口具有滚动范围），然后指定滚动操作可能需要的位置; 如果`bDoScroll`是**FALSE** （即，如果没有子窗口存在，或者拆分视图具有任何滚动范围），然后滚动不会发生。  
  
### <a name="return-value"></a>返回值  
 发生滚动如果同步的则为非 0;否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数调用中滚动消息响应的框架，则执行同步拆分窗口的滚动量，以像素为单位，由`sizeScroll`。 正值指示滚动向下和向右;负值表示向上和向左滚动。  
  
 重写以要求在允许滚动之前由用户操作。  
  
##  <a name="getactivepane"></a>CSplitterWnd::GetActivePane  
 确定活动窗格从焦点或框架中的活动视图。  
  
```  
virtual CWnd* GetActivePane(
    int* pRow = NULL,  
    int* pCol = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pRow`  
 指向的指针**int**检索活动窗格的行号。  
  
 `pCol`  
 指向的指针**int**检索活动窗格中的列号。  
  
### <a name="return-value"></a>返回值  
 指向活动窗格的指针。 **NULL**如果没有活动的窗格中存在。  
  
### <a name="remarks"></a>备注  
 此成员函数调用由框架确定拆分器窗口中的活动窗格中。 重写以要求用户在获取活动窗格之前的操作。  
  
##  <a name="getcolumncount"></a>CSplitterWnd::GetColumnCount  
 返回当前窗格中列数。  
  
```  
int GetColumnCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 在拆分器返回当前的列数。 对于静态拆分，这也将是最大列数。  
  
##  <a name="getcolumninfo"></a>CSplitterWnd::GetColumnInfo  
 返回指定的列信息。  
  
```  
void GetColumnInfo(
    int col,  
    int& cxCur,  
    int& cxMin) const;  
```  
  
### <a name="parameters"></a>参数  
 `col`  
 指定一列。  
  
 *cxCur*  
 对引用`int`将设置为列的当前宽度。  
  
 `cxMin`  
 对引用`int`将设置为列的当前最小宽度。  
  
##  <a name="getpane"></a>CSplitterWnd::GetPane  
 返回在指定的行和列的窗格。  
  
```  
CWnd* GetPane(
    int row,  
    int col) const;  
```  
  
### <a name="parameters"></a>参数  
 `row`  
 指定的行。  
  
 `col`  
 指定一列。  
  
### <a name="return-value"></a>返回值  
 返回在指定的行和列的窗格。 返回窗格中通常是[CView](../../mfc/reference/cview-class.md)-派生类。  
  
##  <a name="getrowcount"></a>CSplitterWnd::GetRowCount  
 返回当前窗格行计数。  
  
```  
int GetRowCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 返回在拆分器窗口中的当前行数。 静态拆分窗口，这将是最大行数。  
  
##  <a name="getrowinfo"></a>CSplitterWnd::GetRowInfo  
 返回有关指定的行信息。  
  
```  
void GetRowInfo(
    int row,  
    int& cyCur,  
    int& cyMin) const;  
```  
  
### <a name="parameters"></a>参数  
 `row`  
 指定的行。  
  
 `cyCur`  
 引用`int`将设置为以像素为单位的行的当前高度。  
  
 `cyMin`  
 引用`int`将设置为以像素为单位的行的当前最小高度。  
  
### <a name="remarks"></a>备注  
 调用此成员函数以获取有关指定行的信息。 `cyCur`参数填充的指定行的当前高度和`cyMin`填入行的最小高度。  
  
##  <a name="getscrollstyle"></a>CSplitterWnd::GetScrollStyle  
 返回拆分窗口的共享的滚动条样式。  
  
```  
DWORD GetScrollStyle() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个或多个以下的窗口样式标志，如果成功：  
  
- **WS_HSCROLL**如果拆分器当前管理共享水平滚动条。  
  
- **WS_VSCROLL**如果拆分器当前管理共享的垂直滚动条。  
  
 如果为零，拆分窗口的当前未管理任何共享的滚动条。  
  
##  <a name="idfromrowcol"></a>CSplitterWnd::IdFromRowCol  
 获取子窗口在指定的行和列的窗格中的 ID。  
  
```  
int IdFromRowCol(
    int row,  
    int col) const;  
```  
  
### <a name="parameters"></a>参数  
 `row`  
 指定的拆分器窗口的行。  
  
 `col`  
 指定的拆分器窗口列。  
  
### <a name="return-value"></a>返回值  
 窗格中子窗口 ID。  
  
### <a name="remarks"></a>备注  
 此成员函数用于创建 nonviews 作为窗格，并可以在窗格中存在之前调用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]  
  
##  <a name="ischildpane"></a>CSplitterWnd::IsChildPane  
 确定是否`pWnd`目前此拆分器窗口的子窗格。  
  
```  
BOOL IsChildPane(
    CWnd* pWnd,  
    int* pRow,  
    int* pCol);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向的指针[CWnd](../../mfc/reference/cwnd-class.md)要测试的对象。  
  
 `pRow`  
 指向的指针`int`要在其中存储行号。  
  
 `pCol`  
 指向的指针`int`要在其中存储列号。  
  
### <a name="return-value"></a>返回值  
 如果不为零，`pWnd`目前此拆分器窗口中，子窗格和`pRow`和`pCol`使用窗格的拆分器窗口中的位置填充。 如果`pWnd`不是子窗格中的此拆分器窗口中，则返回 0。  
  
### <a name="remarks"></a>备注  
 在 Visual c + + 6.0 之前的版本，此函数已定义为  
  
 `BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`  
  
 此版本现在已过时，不应使用。  
  
##  <a name="istracking"></a>CSplitterWnd::IsTracking  
 调用此成员函数可确定当前移动窗口中的拆分栏。  
  
```  
BOOL IsTracking();
```  
  
### <a name="return-value"></a>返回值  
 如果拆分器操作正在进行; 则为非 0否则为 0。  
  
##  <a name="ondrawsplitter"></a>CSplitterWnd::OnDrawSplitter  
 将拆分窗口的图像的渲染。  
  
```  
virtual void OnDrawSplitter(
    CDC* pDC,  
    ESplitType nType,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指向在其中进行绘制的设备上下文的指针。 如果`pDC`是**NULL**，然后[CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow)称为绘制窗口框架和不进行拆分。  
  
 `nType`  
 值为**枚举 ESplitType**，这可以是以下之一：  
  
- **splitBox**拆分器拖动框。  
  
- `splitBar`显示两个拆分窗口之间的栏。  
  
- **splitIntersection**拆分窗口的交集。 在 Windows 95/98 上运行时不会调用此元素。  
  
- **splitBorder**拆分窗口边框。  
  
 `rect`  
 对引用[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，它指定的大小和形状的拆分窗口。  
  
### <a name="remarks"></a>备注  
 由框架，绘制，并指定确切的拆分窗口调用此成员函数。 重写`OnDrawSplitter`的各种图形组件拆分窗口的图像的高级自定义项。 默认图像的类似于在 Microsoft 适用于 Windows 或 Microsoft Windows 95/98，拆分，在于的交集的拆分栏混合在一起。  
  
 有关动态拆分窗口的详细信息，请参阅"拆分窗口"中文章[多文档类型、 视图和框架窗口](../../mfc/multiple-document-types-views-and-frame-windows.md)，[技术注意 29](../../mfc/tn029-splitter-windows.md)，和`CSplitterWnd`类概述。  
  
##  <a name="oninverttracker"></a>CSplitterWnd::OnInvertTracker  
 呈现拆分窗口是相同的大小和形状一样的框架窗口的图像。  
  
```  
virtual void OnInvertTracker(const CRect& rect);
```  
  
### <a name="parameters"></a>参数  
 `rect`  
 引用`CRect`对象，它指定跟踪矩形。  
  
### <a name="remarks"></a>备注  
 在拆分条的调整大小过程中由框架调用此成员函数。 重写`OnInvertTracker`的拆分器窗口的图像的高级自定义项。 默认图像的类似于在 Microsoft 适用于 Windows 或 Microsoft Windows 95/98，拆分，在于的交集的拆分栏混合在一起。  
  
 有关动态拆分窗口的详细信息，请参阅"拆分窗口"中文章[多文档类型、 视图和框架窗口](../../mfc/multiple-document-types-views-and-frame-windows.md)，[技术注意 29](../../mfc/tn029-splitter-windows.md)，和`CSplitterWnd`类概述。  
  
##  <a name="recalclayout"></a>CSplitterWnd::RecalcLayout  
 若要重新拆分窗口显示行或列大小调整后的调用。  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>备注  
 调用此成员函数以正确重新显示拆分窗口之后将调整行和列的大小、, [SetRowInfo](#setrowinfo)和[SetColumnInfo](#setcolumninfo)成员函数。 如果拆分窗口才会显示在创建过程的一部分中更改了行和列的大小，，不需要调用此成员函数。  
  
 每当用户将拆分器窗口大小调整或移动拆分时，框架将调用此成员函数。  
  
### <a name="example"></a>示例  
  请参阅示例[CSplitterWnd::SetColumnInfo](#setcolumninfo)。  
  
##  <a name="setactivepane"></a>CSplitterWnd::SetActivePane  
 将窗格使处于活动状态的帧中的设置。  
  
```  
virtual void SetActivePane(
    int row,  
    int col,  
    CWnd* pWnd = NULL);
```  
  
### <a name="parameters"></a>参数  
 `row`  
 如果`pWnd`是**NULL**，在将处于活动状态窗格中指定的行。  
  
 `col`  
 如果`pWnd`是**NULL**，指定将处于活动状态的窗格中的列。  
  
 `pWnd`  
 指向的指针`CWnd`对象。 如果**NULL**，由指定的窗格`row`和`col`设置活动视图。 如果不是**NULL**，指定设置活动窗格。  
  
### <a name="remarks"></a>备注  
 由框架时用户将焦点更改到在框架窗口内的窗格为活动状态设置窗格中调用此成员函数。 你可以明确地调用`SetActivePane`要将焦点更改到指定的视图。  
  
 通过提供行和列中，指定窗格**或**通过提供`pWnd`。  
  
##  <a name="setcolumninfo"></a>CSplitterWnd::SetColumnInfo  
 用于设置指定的列信息的调用。  
  
```  
void SetColumnInfo(
    int col,  
    int cxIdeal,  
    int cxMin);
```  
  
### <a name="parameters"></a>参数  
 `col`  
 指定的拆分器窗口列。  
  
 *cxIdeal*  
 以像素为单位指定拆分器窗口中列的理想宽度。  
  
 `cxMin`  
 以像素为单位指定拆分器窗口中列的最小宽度。  
  
### <a name="remarks"></a>备注  
 调用此成员函数以设置新的最小宽度和列的理想宽度。 列最小值确定该列将太小而无法完全显示。  
  
 当框架显示拆分窗口时，它是布局根据其理想的尺寸，处理从左上角到右下角的拆分器窗口工作区的行和列中的窗格。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]  
  
##  <a name="setrowinfo"></a>CSplitterWnd::SetRowInfo  
 用于设置指定的行信息的调用。  
  
```  
void SetRowInfo(
    int row,  
    int cyIdeal,  
    int cyMin);
```  
  
### <a name="parameters"></a>参数  
 `row`  
 指定的拆分器窗口的行。  
  
 *cyIdeal*  
 以像素为单位指定拆分器窗口行的理想高度。  
  
 `cyMin`  
 以像素为单位指定拆分器窗口行最小高度。  
  
### <a name="remarks"></a>备注  
 调用此成员函数以设置新的最小高度和行的理想高度。 行最小值确定当会太小而无法完全显示的行。  
  
 当框架显示拆分窗口时，它是布局根据其理想的尺寸，处理从左上角到右下角的拆分器窗口工作区的行和列中的窗格。  
  
##  <a name="setscrollstyle"></a>CSplitterWnd::SetScrollStyle  
 指定拆分窗口的滚动新式共享滚动条支持。  
  
```  
void SetScrollStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 拆分窗口的滚动新式共享滚动条支持，可以是以下值之一：  
  
- **WS_HSCROLL**创建/显示水平共享滚动条。  
  
- **WS_VSCROLL**创建/显示垂直共享滚动条。  
  
### <a name="remarks"></a>备注  
 滚动条创建后不会销毁即使`SetScrollStyle`称为如果不使用该样式; 而是在隐藏这些滚动条。 这允许滚动条来保留其状态，即使它们处于隐藏状态。 在调用`SetScrollStyle`需要调用[RecalcLayout](#recalclayout)的所有更改才会生效。  
  
##  <a name="splitcolumn"></a>CSplitterWnd::SplitColumn  
 指示框架窗口垂直拆分的位置。  
  
```  
virtual BOOL SplitColumn(int cxBefore);
```  
  
### <a name="parameters"></a>参数  
 *cxBefore*  
 以像素为单位，在其之前发生拆分的位置。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 创建垂直拆分器窗口时调用此成员函数。 `SplitColumn`指示发生拆分的位置的默认位置。  
  
 `SplitColumn`由框架实现动态拆分窗口的逻辑调用 (即，如果拆分窗口具有**SPLS_DYNAMIC_SPLIT**样式)。 它可以进行自定义，以及虚拟函数[对 CreateView](#createview)，以实现更高级的动态拆分器。  
  
##  <a name="splitrow"></a>CSplitterWnd::SplitRow  
 指示框架窗口水平拆分的位置。  
  
```  
virtual BOOL SplitRow(int cyBefore);
```  
  
### <a name="parameters"></a>参数  
 *cyBefore*  
 以像素为单位，在其之前发生拆分的位置。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 创建水平拆分器窗口时调用此成员函数。 `SplitRow`指示发生拆分的位置的默认位置。  
  
 `SplitRow`由框架实现动态拆分窗口的逻辑调用 (即，如果拆分窗口具有**SPLS_DYNAMIC_SPLIT**样式)。 它可以进行自定义，以及虚拟函数[对 CreateView](#createview)，以实现更高级的动态拆分器。  
  
##  <a name="ondraw"></a>CSplitterWnd::OnDraw  
 由框架调用以绘制拆分窗口。  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 一个指向设备上下文的指针。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 VIEWEX](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CView 类](../../mfc/reference/cview-class.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)
