---
title: "CSplitterWnd 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
- static splitter windows
- multiple views
- splitter windows
- views, multiple per frame
- dynamic splitter windows
- CSplitterWnd class
ms.assetid: fd0de258-6dbe-4552-9e47-a39de0471d51
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: d015aa604c5394ccbe8c7471b70c84763cc00a5b
ms.lasthandoff: 02/24/2017

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
|[CSplitterWnd::CSplitterWnd](#csplitterwnd)|调用以构造`CSplitterWnd`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CSplitterWnd::ActivateNext](#activatenext)|执行下一个窗格或上一个窗格的命令。|  
|[CSplitterWnd::CanActivateNext](#canactivatenext)|检查以查看是否当前可能的下一个窗格或上一个窗格的命令。|  
|[CSplitterWnd::Create](#create)|调用以创建动态拆分窗口，然后将其附加到`CSplitterWnd`对象。|  
|[CSplitterWnd::CreateScrollBarCtrl](#createscrollbarctrl)|创建共享的滚动条控件。|  
|[CSplitterWnd::CreateStatic](#createstatic)|调用创建静态拆分窗口，并将其附加到`CSplitterWnd`对象。|  
|[CSplitterWnd::CreateView](#createview)|若要在拆分器窗口中创建一个窗格的调用。|  
|[CSplitterWnd::DeleteColumn](#deletecolumn)|从拆分窗口中删除某一列。|  
|[CSplitterWnd::DeleteRow](#deleterow)|从拆分窗口中删除行。|  
|[CSplitterWnd::DeleteView](#deleteview)|从拆分器窗口中删除视图。|  
|[CSplitterWnd::DoKeyboardSplit](#dokeyboardsplit)|执行键盘拆分命令，通常"拆分窗口。"|  
|[CSplitterWnd::DoScroll](#doscroll)|执行同步滚动拆分窗口。|  
|[CSplitterWnd::DoScrollBy](#doscrollby)|滚动按给定数量的像素拆分窗口。|  
|[CSplitterWnd::GetActivePane](#getactivepane)|确定从焦点或框架中的活动视图活动窗格。|  
|[CSplitterWnd::GetColumnCount](#getcolumncount)|返回当前的窗格中列数。|  
|[CSplitterWnd::GetColumnInfo](#getcolumninfo)|返回指定的列信息。|  
|[CSplitterWnd::GetPane](#getpane)|返回位于指定的行和列的窗格。|  
|[CSplitterWnd::GetRowCount](#getrowcount)|返回当前窗格行计数。|  
|[CSplitterWnd::GetRowInfo](#getrowinfo)|返回指定行的信息。|  
|[CSplitterWnd::GetScrollStyle](#getscrollstyle)|返回共享的滚动条样式。|  
|[CSplitterWnd::IdFromRowCol](#idfromrowcol)|返回成员的子窗口 ID 在指定的行和列窗格。|  
|[CSplitterWnd::IsChildPane](#ischildpane)|若要确定窗口是否是当前该拆分器窗口的子窗格中的调用。|  
|[CSplitterWnd::IsTracking](#istracking)|确定当前移动拆分器栏。|  
|[CSplitterWnd::RecalcLayout](#recalclayout)|若要重新拆分器窗口中显示的行或列的大小调整后的调用。|  
|[CSplitterWnd::SetActivePane](#setactivepane)|设置可使处于活动状态的框架中的窗格。|  
|[CSplitterWnd::SetColumnInfo](#setcolumninfo)|调用以设置指定的列信息。|  
|[CSplitterWnd::SetRowInfo](#setrowinfo)|调用以设置指定的行信息。|  
|[CSplitterWnd::SetScrollStyle](#setscrollstyle)|指定拆分器窗口的滚动条新式共享滚动条支持。|  
|[CSplitterWnd::SplitColumn](#splitcolumn)|指示框架窗口垂直拆分的位置。|  
|[CSplitterWnd::SplitRow](#splitrow)|指示框架窗口水平拆分的位置。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CSplitterWnd::OnDraw](#ondraw)|由框架来绘制拆分器窗口中调用。|  
|[CSplitterWnd::OnDrawSplitter](#ondrawsplitter)|呈现拆分窗口的图像。|  
|[CSplitterWnd::OnInvertTracker](#oninverttracker)|呈现拆分窗口是相同的大小和形状一样的框架窗口的图像。|  
  
## <a name="remarks"></a>备注  
 一个窗格，通常是一个特定于应用程序对象派生自[CView](../../mfc/reference/cview-class.md)，但也可以是任何[CWnd](../../mfc/reference/cwnd-class.md)对象，它具有适当的子窗口 id。  
  
 一个`CSplitterWnd`对象通常会嵌入父[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)对象。 创建`CSplitterWnd`对象可以通过以下步骤︰  
  
1.  嵌入`CSplitterWnd`的父框架中的成员变量。  
  
2.  重写父框架[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)成员函数。  
  
3.  从中被重写`OnCreateClient`，调用[创建](#create)或[CreateStatic](#createstatic)成员函数`CSplitterWnd`。  
  
 调用**创建**成员函数来创建动态拆分窗口。 动态拆分窗口通常用于创建和滚动的各个窗格或同一文档的视图。 框架将自动创建拆分器; 初始窗格然后框架创建、 调整大小，并释放其他窗格根据用户的操作拆分器窗口的控件。  
  
 当您调用**创建**，否则不能确定何时将窗格过小以至于不能完全显示一个行最小宽度和列宽度。 在您调用之后**创建**，您可以调整这些最小值，通过调用[SetColumnInfo](#setcolumninfo)和[SetRowInfo](#setrowinfo)成员函数。  
  
 此外使用`SetColumnInfo`和`SetRowInfo`成员函数来设置列的"理想"宽度和"理想"行的高度。 当框架显示拆分器窗口中时，它首先会显示与父框架，然后拆分窗口。 框架然后布局中的列和行根据其理想的尺寸，拆分器窗口的工作区的右下角向左上角从工作窗格。  
  
 动态拆分窗口中的所有窗格都必须属于同一个类。 熟悉的应用程序支持动态拆分窗口包括 Microsoft Word 和 Microsoft Excel。  
  
 使用`CreateStatic`成员函数来创建一个静态拆分窗口。 用户可以更改仅在静态拆分窗口，其不编号或订单中的窗格的大小。  
  
 具体而言，在创建静态拆分时，必须创建所有静态拆分的窗格。 请确保您创建的父框架之前的所有窗格`OnCreateClient`成员函数将返回，否则无法正确显示在窗口框架将。  
  
 `CreateStatic`成员函数将自动初始化静态拆分器与行最小宽度和列宽度为 0。 在您调用之后**创建**，通过调用来调整这些最小值[SetColumnInfo](#setcolumninfo)和[SetRowInfo](#setrowinfo)成员函数。 此外使用`SetColumnInfo`和`SetRowInfo`调用后`CreateStatic`指示所需的理想之选窗格中的维度。  
  
 静态拆分的各个窗格通常属于不同的类。 静态拆分窗口的示例，请参阅图形编辑器和 Windows 文件管理器。  
  
 拆分器窗口中支持特殊的滚动条 （除了窗格可能具有的滚动条）。 这些滚动条是子级`CSplitterWnd`对象，并与窗格共享。  
  
 拆分器窗口时，您可以创建这些特殊的滚动条。 例如， `CSplitterWnd` ，其对应的一行、 两个列和**WS_VSCROLL**样式将显示两个窗格共享的垂直滚动条。 当用户移动滚动条`WM_VSCROLL`消息发送到两个窗格。 如果窗格窗格设置滚动条位置，请设置共享的滚动条。  
  
 拆分窗口的详细信息，请参阅︰  
  
- [技术说明 29](../../mfc/tn029-splitter-windows.md)  
  
-   知识库文章 Q262024︰ 如何︰ 使用 CPropertySheet 作为子 CSplitterWnd  
  
 有关如何创建动态拆分窗口的详细信息，请参阅︰  
  
-   MFC 示例[自由曲线](../../visual-cpp-samples.md)  
  
-   MFC 示例[VIEWEX](../../visual-cpp-samples.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSplitterWnd`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxext.h  
  
##  <a name="activatenext"></a>CSplitterWnd::ActivateNext  
 由框架执行下一个窗格或上一个窗格的命令调用。  
  
```  
virtual void ActivateNext(BOOL bPrev = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `bPrev`  
 指示要激活的窗口。 **TRUE**为上一个;**FALSE**为下一步。  
  
### <a name="remarks"></a>备注  
 此成员函数是通过使用一个较高的层次命令[CView](../../mfc/reference/cview-class.md)类若要委托给`CSplitterWnd`实现。  
  
##  <a name="canactivatenext"></a>CSplitterWnd::CanActivateNext  
 由框架后，若要检查的下一个窗格或上一个窗格命令当前可能调用。  
  
```  
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `bPrev`  
 指示要激活的窗口。 **TRUE**为上一个;**FALSE**为下一步。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数是通过使用一个较高的层次命令[CView](../../mfc/reference/cview-class.md)类若要委托给`CSplitterWnd`实现。  
  
##  <a name="create"></a>CSplitterWnd::Create  
 若要创建动态拆分窗口，请调用**创建**成员函数。  
  
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
 拆分器窗口的父框架窗口。  
  
 *nMaxRows*  
 最大拆分器窗口中的行数。 此值不能超过 2。  
  
 *nMaxCols*  
 最大拆分器窗口中的列数。 此值不能超过 2。  
  
 `sizeMin`  
 指定一个窗格可能会显示的最小大小。  
  
 `pContext`  
 一个指向[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)结构。 在大多数情况下，这可能是`pContext`传递到父框架窗口。  
  
 `dwStyle`  
 指定的窗口样式。  
  
 `nID`  
 窗口的子窗口 ID。 该 ID 可以是**AFX_IDW_PANE_FIRST**除非拆分窗口嵌套在另一个拆分器窗口的内部。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 您可以将嵌入`CSplitterWnd`的父文件夹中[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)对象通过采取以下步骤︰  
  
1.  嵌入`CSplitterWnd`的父框架中的成员变量。  
  
2.  重写父框架[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)成员函数。  
  
3.  调用**创建**中被重写成员函数`OnCreateClient`。  
  
 在创建从父范围内的拆分器窗口时，传递与父框架`pContext`拆分器窗口中的参数。 否则，此参数可以为**NULL**。  
  
 动态拆分窗口的初始行最小宽度和列宽度由设置`sizeMin`参数。 这些最小值，用于确定是否太小而无法完整地显示窗格中，可以更改与[SetRowInfo](#setrowinfo)和[SetColumnInfo](#setcolumninfo)成员函数。  
  
 动态拆分窗口的详细信息，请参阅"拆分窗口"文章中[多个文档类型、 视图和框架窗口](../../mfc/multiple-document-types-views-and-frame-windows.md)，[技术注意 29](../../mfc/tn029-splitter-windows.md)，与`CSplitterWnd`类的概述。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&125;](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]  
  
##  <a name="createscrollbarctrl"></a>CSplitterWnd::CreateScrollBarCtrl  
 由框架来创建共享的滚动条控件调用。  
  
```  
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 指定的窗口样式。  
  
 `nID`  
 窗口的子窗口 ID。 该 ID 可以是**AFX_IDW_PANE_FIRST**除非拆分窗口嵌套在另一个拆分器窗口的内部。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 重写`CreateScrollBarCtrl`包括额外的控件，旁边的滚动条。 默认行为是创建普通 Windows 滚动条控件。  
  
##  <a name="createstatic"></a>CSplitterWnd::CreateStatic  
 若要创建静态拆分窗口，请调用`CreateStatic`成员函数。  
  
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
 拆分器窗口的父框架窗口。  
  
 `nRows`  
 行数。 此值不能超过 16。  
  
 *nCols*  
 列数。 此值不能超过 16。  
  
 `dwStyle`  
 指定的窗口样式。  
  
 `nID`  
 窗口的子窗口 ID。 该 ID 可以是**AFX_IDW_PANE_FIRST**除非拆分窗口嵌套在另一个拆分器窗口的内部。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 一个`CSplitterWnd`通常会嵌入在父`CFrameWnd`或[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)对象通过采取以下步骤︰  
  
1.  嵌入`CSplitterWnd`的父框架中的成员变量。  
  
2.  重写父框架`OnCreateClient`成员函数。  
  
3.  调用`CreateStatic`中被重写成员函数[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)。  
  
 静态拆分窗口包含一个固定的数量的窗格中，通常从不同的类。  
  
 在创建静态拆分窗口时，您必须同时创建所有窗格。 [CreateView](#createview)成员函数通常用于此目的，但您可以创建其他的 nonview 类。  
  
 静态拆分窗口的初始行最小宽度和列宽度为 0。 这些最小值，用于确定何时太小而无法完整地显示窗格中，可以更改与[SetRowInfo](#setrowinfo)和[SetColumnInfo](#setcolumninfo)成员函数。  
  
 若要将滚动条添加到静态拆分窗口中，添加**WS_HSCROLL**和**WS_VSCROLL**样式`dwStyle`。  
  
 请参阅文章中的"拆分窗口"[多个文档类型、 视图和框架窗口](../../mfc/multiple-document-types-views-and-frame-windows.md)，[技术注意 29](../../mfc/tn029-splitter-windows.md)，与`CSplitterWnd`类概述有关静态拆分窗口的详细信息。  
  
##  <a name="createview"></a>CSplitterWnd::CreateView  
 创建静态拆分窗口窗格。  
  
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
 指定要在其中放置新视图的拆分器窗口一行。  
  
 `col`  
 指定要在其中放置新视图的拆分器窗口中列。  
  
 `pViewClass`  
 指定[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)的新视图。  
  
 *sizeInit*  
 指定新视图的初始大小。  
  
 `pContext`  
 指向用来创建该视图创建上下文的指针 (通常`pContext`传递到父框架重写[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)在其中创建拆分器窗口的成员函数)。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 之前，框架显示拆分器，必须创建静态拆分窗口的所有窗格。  
  
 框架还调用该成员函数以创建新窗格时动态拆分窗口的用户将拆分窗格、 行或列。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&4;](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]  
  
##  <a name="csplitterwnd"></a>CSplitterWnd::CSplitterWnd  
 调用以构造`CSplitterWnd`对象。  
  
```  
CSplitterWnd();
```  
  
### <a name="remarks"></a>备注  
 构造`CSplitterWnd`两个步骤中的对象。 首先，调用构造函数中，这将创建`CSplitterWnd`对象，然后再调用[创建](#create)成员函数，其创建拆分器窗口，并将其附加到`CSplitterWnd`对象。  
  
##  <a name="deletecolumn"></a>CSplitterWnd::DeleteColumn  
 从拆分窗口中删除某一列。  
  
```  
virtual void DeleteColumn(int colDelete);
```  
  
### <a name="parameters"></a>参数  
 *colDelete*  
 指定要删除的列。  
  
### <a name="remarks"></a>备注  
 此成员函数由框架调用以实现动态拆分窗口的逻辑 (即，如果拆分器窗口具有**SPLS_DYNAMIC_SPLIT**样式)。 对其进行定制，虚函数以及[CreateView](#createview)，从而实现更高级的动态拆分器。  
  
##  <a name="deleterow"></a>CSplitterWnd::DeleteRow  
 从拆分窗口中删除行。  
  
```  
virtual void DeleteRow(int rowDelete);
```  
  
### <a name="parameters"></a>参数  
 *行删除*  
 指定要删除的行。  
  
### <a name="remarks"></a>备注  
 此成员函数由框架调用以实现动态拆分窗口的逻辑 (即，如果拆分器窗口具有**SPLS_DYNAMIC_SPLIT**样式)。 对其进行定制，虚函数以及[CreateView](#createview)，从而实现更高级的动态拆分器。  
  
##  <a name="deleteview"></a>CSplitterWnd::DeleteView  
 从拆分器窗口中删除视图。  
  
```  
virtual void DeleteView(
    int row,  
    int col);
```  
  
### <a name="parameters"></a>参数  
 `row`  
 指定在要从中删除视图的拆分器窗口一行。  
  
 `col`  
 指定在要从中删除视图的拆分器窗口中列。  
  
### <a name="remarks"></a>备注  
 如果删除了活动视图下, 一个视图将变为活动状态。 默认实现假设该视图将自动删除在[PostNcDestroy](../../mfc/reference/cwnd-class.md#postncdestroy)。  
  
 此成员函数由框架调用以实现动态拆分窗口的逻辑 (即，如果拆分器窗口具有**SPLS_DYNAMIC_SPLIT**样式)。 对其进行定制，虚函数以及[CreateView](#createview)，从而实现更高级的动态拆分器。  
  
##  <a name="dokeyboardsplit"></a>CSplitterWnd::DoKeyboardSplit  
 执行键盘拆分命令，通常"拆分窗口。"  
  
```  
virtual BOOL DoKeyboardSplit();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数是通过使用一个较高的层次命令[CView](../../mfc/reference/cview-class.md)类若要委托给`CSplitterWnd`实现。  
  
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
 指示用户的滚动条代码的滚动请求。 此参数由两个部分组成︰ 低位字节，它确定滚动正在进行水平的类型和一个高序位字节，它确定滚动正在进行垂直的类型︰  
  
- **SB_BOTTOM**滚动到下的顺序。  
  
- **SB_LINEDOWN**向下滚动一行。  
  
- **SB_LINEUP**向上滚动一行。  
  
- **SB_PAGEDOWN**向下滚动一页。  
  
- **SB_PAGEUP**向上滚动一页。  
  
- **SB_TOP**滚动到顶部。  
  
 `bDoScroll`  
 确定是否执行了指定的滚动操作。 如果`bDoScroll`是**TRUE** （即，如果存在的子窗口，并在拆分窗口具有滚动范围），然后指定滚动操作可以发生; 如果`bDoScroll`是**FALSE** （即，如果不存在任何子窗口，或拆分视图有没有滚动范围），则不会发生滚动。  
  
### <a name="return-value"></a>返回值  
 如果同步的非零值会发生滚动;否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数是由框架调用以执行同步的滚动拆分窗口的视图接收滚动消息时。 重写以允许同步滚动之前都需要用户执行操作。  
  
##  <a name="doscrollby"></a>CSplitterWnd::DoScrollBy  
 滚动按给定数量的像素拆分窗口。  
  
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
 若要水平和垂直滚动的像素数。  
  
 bDoScroll  
 确定是否执行了指定的滚动操作。 如果`bDoScroll`是**TRUE** （即，如果存在的子窗口，并在拆分窗口具有滚动范围），然后指定滚动操作可以发生; 如果`bDoScroll`是**FALSE** （即，如果不存在任何子窗口，或拆分视图有没有滚动范围），则不会发生滚动。  
  
### <a name="return-value"></a>返回值  
 如果同步的非零值会发生滚动;否则为 0。  
  
### <a name="remarks"></a>备注  
 响应滚动消息中的框架调用此成员函数，则执行同步的拆分窗口滚动量，以像素为单位，由指示`sizeScroll`。 正值指示向下和向右; 滚动负值表示向上和向左滚动。  
  
 重写以要求在允许滚动之前由用户操作。  
  
##  <a name="getactivepane"></a>CSplitterWnd::GetActivePane  
 确定从焦点或框架中的活动视图活动窗格。  
  
```  
virtual CWnd* GetActivePane(
    int* pRow = NULL,  
    int* pCol = NULL);
```  
  
### <a name="parameters"></a>参数  
 `pRow`  
 一个指向**int**检索活动窗格中的行号。  
  
 `pCol`  
 一个指向**int**检索活动窗格中的列号。  
  
### <a name="return-value"></a>返回值  
 指针，指向 active 窗格中。 **NULL**如果没有活动的窗格中存在。  
  
### <a name="remarks"></a>备注  
 此成员函数是由框架调用以确定在拆分器窗口中活动窗格。 重写以要求用户采取措施，然后获取活动窗格。  
  
##  <a name="getcolumncount"></a>CSplitterWnd::GetColumnCount  
 返回当前的窗格中列数。  
  
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
 指定的列。  
  
 *cxCur*  
 对引用`int`将设置为列中的当前宽度。  
  
 `cxMin`  
 对引用`int`将设置为列中的当前最小宽度。  
  
##  <a name="getpane"></a>CSplitterWnd::GetPane  
 返回位于指定的行和列的窗格。  
  
```  
CWnd* GetPane(
    int row,  
    int col) const;  
```  
  
### <a name="parameters"></a>参数  
 `row`  
 指定的行。  
  
 `col`  
 指定的列。  
  
### <a name="return-value"></a>返回值  
 返回位于指定的行和列的窗格。 返回窗格中通常是[CView](../../mfc/reference/cview-class.md)的派生类。  
  
##  <a name="getrowcount"></a>CSplitterWnd::GetRowCount  
 返回当前窗格行计数。  
  
```  
int GetRowCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 在拆分器窗口中返回当前行数。 静态拆分窗口，这将是最大行数。  
  
##  <a name="getrowinfo"></a>CSplitterWnd::GetRowInfo  
 返回指定行的信息。  
  
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
 调用该成员函数以获取有关指定行的信息。 `cyCur`用指定的行的当前高度填充参数和`cyMin`填充行的最小高度。  
  
##  <a name="getscrollstyle"></a>CSplitterWnd::GetScrollStyle  
 返回拆分器窗口中的共享的滚动条样式。  
  
```  
DWORD GetScrollStyle() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个或多个以下的窗口样式标志，如果成功︰  
  
- **WS_HSCROLL**如果拆分器当前管理共享水平滚动条。  
  
- **WS_VSCROLL**如果拆分器当前管理共享的垂直滚动条。  
  
 如果为零，拆分器窗口中当前未管理任何共享的滚动条。  
  
##  <a name="idfromrowcol"></a>CSplitterWnd::IdFromRowCol  
 获取子窗口 ID 在指定的行和列窗格。  
  
```  
int IdFromRowCol(
    int row,  
    int col) const;  
```  
  
### <a name="parameters"></a>参数  
 `row`  
 指定的拆分器窗口中的一行。  
  
 `col`  
 指定的拆分器窗口中列。  
  
### <a name="return-value"></a>返回值  
 窗格中子窗口 ID。  
  
### <a name="remarks"></a>备注  
 此成员函数用于创建 nonviews 为窗格，可以在窗格中存在之前调用。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&5;](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]  
  
##  <a name="ischildpane"></a>CSplitterWnd::IsChildPane  
 确定是否`pWnd`目前该拆分器窗口的子窗格。  
  
```  
BOOL IsChildPane(
    CWnd* pWnd,  
    int* pRow,  
    int* pCol);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 一个指向[CWnd](../../mfc/reference/cwnd-class.md)要测试对象。  
  
 `pRow`  
 一个指向`int`要在其中存储行的行号。  
  
 `pCol`  
 一个指向`int`要在其中存储列号。  
  
### <a name="return-value"></a>返回值  
 如果非零，`pWnd`目前此拆分器窗口中，一个子窗格和`pRow`和`pCol`填充窗格中的拆分器窗口中的位置。 如果`pWnd`不是子窗格中的此拆分器窗口中，则返回 0。  
  
### <a name="remarks"></a>备注  
 在 Visual c + + 6.0 之前的版本，此函数被定义为  
  
 `BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`  
  
 此版本现已过时，不应使用。  
  
##  <a name="istracking"></a>CSplitterWnd::IsTracking  
 调用该成员函数以确定当前移动窗口中的拆分器栏。  
  
```  
BOOL IsTracking();
```  
  
### <a name="return-value"></a>返回值  
 如果拆分器操作正在进行中; 则为非否则为 0。  
  
##  <a name="ondrawsplitter"></a>CSplitterWnd::OnDrawSplitter  
 呈现拆分窗口的图像。  
  
```  
virtual void OnDrawSplitter(
    CDC* pDC,  
    ESplitType nType,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 指向要在其中绘制的设备上下文的指针。 如果`pDC`是**NULL**，然后[CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow)称为窗口中绘制的框架和不进行拆分。  
  
 `nType`  
 值为**枚举 ESplitType**，可以是以下项之一︰  
  
- **splitBox**拆分器拖动框。  
  
- `splitBar`在两个拆分窗口之间出现的栏。  
  
- **splitIntersection**拆分窗口的交集。 在 Windows 95/98 上运行时不会调用此元素。  
  
- **splitBorder**拆分窗口边框。  
  
 `rect`  
 对引用[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，它指定的大小和形状的拆分窗口。  
  
### <a name="remarks"></a>备注  
 此成员函数是由框架调用以绘制，并指定拆分器窗口中的具体特性。 重写`OnDrawSplitter`用于高级自定义的拆分器窗口中的各种图形组件图像。 默认图像的类似于 Microsoft 适用于 Windows 或 Microsoft Windows 95/98 中，在拆分器在于拆分栏的交集的混合在一起。  
  
 动态拆分窗口的详细信息，请参阅"拆分窗口"文章中[多个文档类型、 视图和框架窗口](../../mfc/multiple-document-types-views-and-frame-windows.md)，[技术注意 29](../../mfc/tn029-splitter-windows.md)，与`CSplitterWnd`类的概述。  
  
##  <a name="oninverttracker"></a>CSplitterWnd::OnInvertTracker  
 呈现拆分窗口是相同的大小和形状一样的框架窗口的图像。  
  
```  
virtual void OnInvertTracker(const CRect& rect);
```  
  
### <a name="parameters"></a>参数  
 `rect`  
 引用`CRect`对象，它指定跟踪矩形。  
  
### <a name="remarks"></a>备注  
 在拆分器的调整大小过程，框架调用此成员函数。 重写`OnInvertTracker`用于高级自定义的拆分器窗口中的图像。 默认图像的类似于 Microsoft 适用于 Windows 或 Microsoft Windows 95/98 中，在拆分器在于拆分栏的交集的混合在一起。  
  
 动态拆分窗口的详细信息，请参阅"拆分窗口"文章中[多个文档类型、 视图和框架窗口](../../mfc/multiple-document-types-views-and-frame-windows.md)，[技术注意 29](../../mfc/tn029-splitter-windows.md)，与`CSplitterWnd`类的概述。  
  
##  <a name="recalclayout"></a>CSplitterWnd::RecalcLayout  
 若要重新拆分器窗口中显示的行或列的大小调整后的调用。  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>备注  
 调用此成员函数以正确地重新拆分器窗口中显示后已调整行和列的大小随[SetRowInfo](#setrowinfo)和[SetColumnInfo](#setcolumninfo)成员函数。 如果拆分器窗口才会显示在创建过程的一部分更改行和列的大小，，不需要调用此成员函数。  
  
 每当用户调整拆分器窗口的大小或移动拆分时，框架将调用此成员函数。  
  
### <a name="example"></a>示例  
  请参阅示例[CSplitterWnd::SetColumnInfo](#setcolumninfo)。  
  
##  <a name="setactivepane"></a>CSplitterWnd::SetActivePane  
 设置可使处于活动状态的框架中的窗格。  
  
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
 一个指向`CWnd`对象。 如果**NULL**，窗格中指定的`row`和`col`设置活动。 如果不是**NULL**，指定设置活动窗格。  
  
### <a name="remarks"></a>备注  
 此成员函数是由框架调用以将一个窗格设置为活动，当用户将焦点更改到框架窗口中的窗格。 您可以显式调用`SetActivePane`将焦点更改到指定的视图。  
  
 通过提供行和列中，指定窗格**或**通过提供`pWnd`。  
  
##  <a name="setcolumninfo"></a>CSplitterWnd::SetColumnInfo  
 调用以设置指定的列信息。  
  
```  
void SetColumnInfo(
    int col,  
    int cxIdeal,  
    int cxMin);
```  
  
### <a name="parameters"></a>参数  
 `col`  
 指定的拆分器窗口中列。  
  
 *cxIdeal*  
 以像素为单位指定拆分器窗口中列的理想宽度。  
  
 `cxMin`  
 以像素为单位指定拆分器窗口中列的最小宽度。  
  
### <a name="remarks"></a>备注  
 调用该成员函数以设置新的最小宽度和列的理想宽度。 列最小值确定的列将过小以至于不能完全显示。  
  
 当框架显示拆分器窗口中时，布局中列和行根据其理想的尺寸，拆分器窗口的工作区的右下角向左上角从工作窗格。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing #&6;](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]  
  
##  <a name="setrowinfo"></a>CSplitterWnd::SetRowInfo  
 调用以设置指定的行信息。  
  
```  
void SetRowInfo(
    int row,  
    int cyIdeal,  
    int cyMin);
```  
  
### <a name="parameters"></a>参数  
 `row`  
 指定的拆分器窗口中的行。  
  
 *cyIdeal*  
 以像素为单位指定拆分器窗口行的理想高度。  
  
 `cyMin`  
 以像素为单位指定拆分器窗口行的最小高度。  
  
### <a name="remarks"></a>备注  
 调用该成员函数以设置新的最小高度和行的理想高度。 行最小值确定何时会过小以至于不能完全显示的行。  
  
 当框架显示拆分器窗口中时，布局中列和行根据其理想的尺寸，拆分器窗口的工作区的右下角向左上角从工作窗格。  
  
##  <a name="setscrollstyle"></a>CSplitterWnd::SetScrollStyle  
 指定拆分器窗口的滚动新式共享滚动条支持。  
  
```  
void SetScrollStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 拆分器窗口的滚动新式共享滚动条支持，可以是下列值之一︰  
  
- **WS_HSCROLL**创建/显示水平共享滚动条。  
  
- **WS_VSCROLL**创建/显示垂直共享滚动条。  
  
### <a name="remarks"></a>备注  
 创建一个滚动条后不会销毁即使`SetScrollStyle`称为如果不使用该样式; 而是在隐藏这些滚动条。 这允许滚动条以保持其状态，即使它们处于隐藏状态也是如此。 在调用`SetScrollStyle`不必调用时会[RecalcLayout](#recalclayout)的所有更改才会生效。  
  
##  <a name="splitcolumn"></a>CSplitterWnd::SplitColumn  
 指示框架窗口垂直拆分的位置。  
  
```  
virtual BOOL SplitColumn(int cxBefore);
```  
  
### <a name="parameters"></a>参数  
 *cxBefore*  
 以像素为单位，在其之前发生的拆分位置。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数调用时都会创建一个垂直拆分器窗口。 `SplitColumn`指示发生拆分的默认位置。  
  
 `SplitColumn`由框架调用以实现动态拆分窗口的逻辑 (即，如果拆分器窗口具有**SPLS_DYNAMIC_SPLIT**样式)。 对其进行定制，虚函数以及[CreateView](#createview)，从而实现更高级的动态拆分器。  
  
##  <a name="splitrow"></a>CSplitterWnd::SplitRow  
 指示框架窗口水平拆分的位置。  
  
```  
virtual BOOL SplitRow(int cyBefore);
```  
  
### <a name="parameters"></a>参数  
 *cyBefore*  
 以像素为单位，在其之前发生的拆分位置。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 创建水平拆分器窗口时，被调用该成员函数。 `SplitRow`指示发生拆分的默认位置。  
  
 `SplitRow`由框架调用以实现动态拆分窗口的逻辑 (即，如果拆分器窗口具有**SPLS_DYNAMIC_SPLIT**样式)。 对其进行定制，虚函数以及[CreateView](#createview)，从而实现更高级的动态拆分器。  
  
##  <a name="ondraw"></a>CSplitterWnd::OnDraw  
 由框架来绘制拆分器窗口中调用。  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 `pDC`  
 一个指向设备上下文的指针。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 VIEWEX](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CView 类](../../mfc/reference/cview-class.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)

