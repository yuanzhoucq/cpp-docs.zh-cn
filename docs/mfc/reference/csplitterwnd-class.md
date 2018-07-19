---
title: CSplitterWnd 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f01452a2a8f8b4a50b9aa7723eb4ded24b3f3cc9
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2018
ms.locfileid: "39027919"
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
|[CSplitterWnd::ActivateNext](#activatenext)|执行下一窗格或上一窗格命令。|  
|[CSplitterWnd::CanActivateNext](#canactivatenext)|检查以查看是否当前可能下一窗格或上一窗格命令。|  
|[CSplitterWnd::Create](#create)|调用以创建动态拆分器窗口并将其附加到`CSplitterWnd`对象。|  
|[CSplitterWnd::CreateScrollBarCtrl](#createscrollbarctrl)|创建共享的滚动条控件。|  
|[CSplitterWnd::CreateStatic](#createstatic)|调用以创建一个静态拆分窗口，并将其附加到`CSplitterWnd`对象。|  
|[CSplitterWnd::CreateView](#createview)|若要在拆分器窗口中创建一个窗格的调用。|  
|[CSplitterWnd::DeleteColumn](#deletecolumn)|从拆分器窗口中删除列。|  
|[CSplitterWnd::DeleteRow](#deleterow)|从拆分器窗口中删除行。|  
|[CSplitterWnd::DeleteView](#deleteview)|从拆分器窗口中删除视图。|  
|[CSplitterWnd::DoKeyboardSplit](#dokeyboardsplit)|执行键盘拆分命令，通常"窗口拆分。"|  
|[CSplitterWnd::DoScroll](#doscroll)|执行拆分窗口同步滚动。|  
|[CSplitterWnd::DoScrollBy](#doscrollby)|给定的像素数目滚动拆分窗口。|  
|[CSplitterWnd::GetActivePane](#getactivepane)|确定活动窗格从焦点或活动视图的框架中。|  
|[CSplitterWnd::GetColumnCount](#getcolumncount)|返回当前窗格中列数。|  
|[CSplitterWnd::GetColumnInfo](#getcolumninfo)|返回指定的列信息。|  
|[CSplitterWnd::GetPane](#getpane)|返回位于指定的行和列的窗格。|  
|[CSplitterWnd::GetRowCount](#getrowcount)|返回当前窗格行计数。|  
|[CSplitterWnd::GetRowInfo](#getrowinfo)|返回指定行的信息。|  
|[CSplitterWnd::GetScrollStyle](#getscrollstyle)|返回共享的滚动条样式。|  
|[CSplitterWnd::IdFromRowCol](#idfromrowcol)|返回的子窗口的窗格中位于指定的行和列的 ID。|  
|[CSplitterWnd::IsChildPane](#ischildpane)|调用以确定是否在窗口当前为此拆分器窗口的一个子窗格。|  
|[CSplitterWnd::IsTracking](#istracking)|确定拆分条当前正在移动。|  
|[CSplitterWnd::RecalcLayout](#recalclayout)|若要在调整行或列大小之后重新显示在拆分器窗口的调用。|  
|[CSplitterWnd::SetActivePane](#setactivepane)|将窗格使处于活动状态的框架中的设置。|  
|[CSplitterWnd::SetColumnInfo](#setcolumninfo)|调用以设置指定的列信息。|  
|[CSplitterWnd::SetRowInfo](#setrowinfo)|用于设置指定的行信息的调用。|  
|[CSplitterWnd::SetScrollStyle](#setscrollstyle)|指定新的拆分器窗口的滚动条样式共享滚动条支持。|  
|[CSplitterWnd::SplitColumn](#splitcolumn)|指示框架窗口垂直拆分的位置。|  
|[CSplitterWnd::SplitRow](#splitrow)|指示框架窗口水平拆分的位置。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CSplitterWnd::OnDraw](#ondraw)|由框架调用以绘制拆分器窗口。|  
|[CSplitterWnd::OnDrawSplitter](#ondrawsplitter)|呈现拆分窗口的图像。|  
|[CSplitterWnd::OnInvertTracker](#oninverttracker)|呈现拆分窗口是相同的大小和形状一样的框架窗口的图像。|  
  
## <a name="remarks"></a>备注  
一个窗格，通常是特定于应用程序的对象派生自[CView](../../mfc/reference/cview-class.md)，但它可以是任何[CWnd](../../mfc/reference/cwnd-class.md)对象都有相应的子窗口 id。  
  
 一个`CSplitterWnd`对象通常会嵌入父级[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)对象。 创建`CSplitterWnd`对象使用以下步骤：  
  
 1. 嵌入`CSplitterWnd`父框架中的成员变量。  
  
 2.  重写父框架[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)成员函数。  
  
 3.  从中重写`OnCreateClient`，调用[创建](#create)或[CreateStatic](#createstatic)成员函数的`CSplitterWnd`。  
  
调用`Create`成员函数来创建动态拆分窗口。 动态拆分窗口通常用于创建和滚动的各个窗格或同一文档的视图。 框架会自动创建拆分器; 的初始窗格然后框架创建、 调整大小，并释放其他窗格，如用户运行拆分器窗口的控件。  
  
当您调用`Create`，指定最小行宽度和列宽度，以确定当窗格都太小，无法完全显示。 调用后`Create`，可以通过调用来调整这些最小值[SetColumnInfo](#setcolumninfo)并[SetRowInfo](#setrowinfo)成员函数。  
  
此外使用`SetColumnInfo`和`SetRowInfo`成员函数来设置列的"理想"宽度和"理想"行的高度。 当框架显示拆分器窗口时，它首先会显示与父框架，然后拆分器窗口。 Framework 然后布局中列和行根据其理想的维度，从左上方工作的拆分器窗口的工作区的右下角的窗格。  
  
动态拆分窗口中的所有窗格都必须属于同一个类。 熟悉支持动态拆分窗口的应用程序包括 Microsoft Word 和 Microsoft Excel。  
  
使用`CreateStatic`成员函数来创建一个静态拆分窗口。 用户可以更改仅在静态拆分器窗口中，其不编号或订单中的窗格的大小。  
  
具体而言，创建静态拆分器时，必须创建所有静态拆分的窗格。 请确保您创建父框架之前的所有窗格`OnCreateClient`成员函数返回，否则框架将不会正常显示窗口。  
  
`CreateStatic`成员函数将自动初始化静态拆分器与行最小宽度和列宽度为 0。 调用后`Create`，通过调用来调整这些最小值[SetColumnInfo](#setcolumninfo)并[SetRowInfo](#setrowinfo)成员函数。 此外使用`SetColumnInfo`并`SetRowInfo`调用后`CreateStatic`以指示所需的理想之选窗格维度。  
  
静态拆分器的各个窗格通常属于不同的类。 静态拆分窗口的示例，请参阅在图形编辑器和 Windows 文件管理器。  
  
拆分器窗口支持特殊的滚动条 （除了窗格可能具有的滚动条）。 这些滚动条是子级`CSplitterWnd`对象，并与窗格共享。  
  
创建拆分器窗口时创建这些特殊的滚动条。 例如，`CSplitterWnd`具有一行、 两个列，并且 WS_VSCROLL 样式将显示由两个窗格共享的垂直滚动条。 当用户移动滚动条时，WM_VSCROLL 消息发送到两个窗格。 当窗格设置滚动条位置时，请设置共享的滚动条。  
  
拆分窗口的详细信息，请参阅：  
  
 - [技术说明 29](../../mfc/tn029-splitter-windows.md)  
  
 - 知识库文章 Q262024： 如何： 使用 CPropertySheet 作为子 CSplitterWnd  
  
有关如何创建动态拆分窗口的详细信息，请参阅：  
  
 - MFC 示例[Scribble](../../visual-cpp-samples.md)  
  
 - MFC 示例[VIEWEX](../../visual-cpp-samples.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CSplitterWnd`  
  
## <a name="requirements"></a>要求  
 **标头：** afxext.h  
  
##  <a name="activatenext"></a>  CSplitterWnd::ActivateNext  
 由框架调用以执行下一窗格或上一窗格命令。  
  
```  
virtual void ActivateNext(BOOL bPrev = FALSE);
```  
  
### <a name="parameters"></a>参数  
 *bPrev*  
 指示要激活的窗口。 **TRUE**为上一;**FALSE**的下一步。  
  
### <a name="remarks"></a>备注  
 此成员函数是由一个高级别命令[CView](../../mfc/reference/cview-class.md)类将委派给`CSplitterWnd`实现。  
  
##  <a name="canactivatenext"></a>  CSplitterWnd::CanActivateNext  
 由框架调用以检查有下一窗格或上一窗格命令当前可能。  
  
```  
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```  
  
### <a name="parameters"></a>参数  
 *bPrev*  
 指示要激活的窗口。 **TRUE**为上一;**FALSE**的下一步。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数是由一个高级别命令[CView](../../mfc/reference/cview-class.md)类将委派给`CSplitterWnd`实现。  
  
##  <a name="create"></a>  CSplitterWnd::Create  
 若要创建动态拆分窗口，调用`Create`成员函数。  
  
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
 *pParentWnd*  
 拆分器窗口的父框架窗口。  
  
 *nMaxRows*  
 最大拆分器窗口中的行数。 此值不能超过 2。  
  
 *nMaxCols*  
 最大拆分器窗口中的列数。 此值不能超过 2。  
  
 *sizeMin*  
 指定一个窗格可能会显示的最小大小。  
  
 *pContext*  
 一个指向[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)结构。 在大多数情况下，这可以*pContext*传递到父框架窗口。  
  
 *dwStyle*  
 指定的窗口样式。  
  
 *nID*  
 窗口的子窗口 ID。 该 ID 可以是 AFX_IDW_PANE_FIRST，除非在另一个拆分器窗口中嵌套拆分器窗口。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 可以嵌入`CSplitterWnd`父命名空间中[CFrameWnd](../../mfc/reference/cframewnd-class.md)或[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)对象通过执行以下步骤：  
  
1.  嵌入`CSplitterWnd`父框架中的成员变量。  
  
2.  重写父框架[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)成员函数。  
  
3.  调用`Create`成员函数从中被重写的`OnCreateClient`。  
  
 创建拆分器窗口，从父范围内的时，传递与父框架*pContext*拆分器窗口的参数。 否则，此参数可以为 NULL。  
  
 设置动态拆分窗口的初始最小行宽度和列宽度*sizeMin*参数。 最小值，用于确定是否太小，无法完全显示一个窗格，可以更改与[SetRowInfo](#setrowinfo)并[SetColumnInfo](#setcolumninfo)成员函数。  
  
 动态拆分窗口的详细信息，请参阅"拆分器 Windows"一文中[多个文档类型、 视图和框架 Windows](../../mfc/multiple-document-types-views-and-frame-windows.md)，[技术注意 29](../../mfc/tn029-splitter-windows.md)，和`CSplitterWnd`类概述。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#125](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]  
  
##  <a name="createscrollbarctrl"></a>  CSplitterWnd::CreateScrollBarCtrl  
 由框架调用以创建共享的滚动条控件。  
  
```  
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 *dwStyle*  
 指定的窗口样式。  
  
 *nID*  
 窗口的子窗口 ID。 该 ID 可以是 AFX_IDW_PANE_FIRST，除非在另一个拆分器窗口中嵌套拆分器窗口。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 重写`CreateScrollBarCtrl`若要包括的滚动条旁边的额外控件。 默认行为是创建普通 Windows 滚动条控件。  
  
##  <a name="createstatic"></a>  CSplitterWnd::CreateStatic  
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
 *pParentWnd*  
 拆分器窗口的父框架窗口。  
  
 *nRows*  
 行数。 此值不能超过 16。  
  
 *nCols*  
 列数。 此值不能超过 16。  
  
 *dwStyle*  
 指定的窗口样式。  
  
 *nID*  
 窗口的子窗口 ID。 该 ID 可以是 AFX_IDW_PANE_FIRST，除非在另一个拆分器窗口中嵌套拆分器窗口。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 一个`CSplitterWnd`通常嵌入在父`CFrameWnd`或[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)对象通过执行以下步骤：  
  
1.  嵌入`CSplitterWnd`父框架中的成员变量。  
  
2.  重写父框架`OnCreateClient`成员函数。  
  
3.  调用`CreateStatic`成员函数从中重写[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)。  
  
 静态拆分窗口包含固定的数量的窗格中，通常从不同的类。  
  
 当创建静态拆分窗口时，您必须在同一时间创建所有窗格。 [CreateView](#createview)成员函数通常用于此目的，但您可以创建其他的 nonview 类。  
  
 静态拆分窗口的初始最小行宽度和列宽度为 0。 可以使用更改的最小值，确定何时太小，无法完全显示一个窗格，其中[SetRowInfo](#setrowinfo)并[SetColumnInfo](#setcolumninfo)成员函数。  
  
 若要将滚动条添加到静态拆分窗口中，将添加到 WS_HSCROLL 和 WS_VSCROLL 样式*dwStyle*。  
  
 请参阅本文中的"拆分器 Windows"[多个文档类型、 视图和框架 Windows](../../mfc/multiple-document-types-views-and-frame-windows.md)，[技术注意 29](../../mfc/tn029-splitter-windows.md)，和`CSplitterWnd`类概述有关静态拆分窗口的详细信息。  
  
##  <a name="createview"></a>  CSplitterWnd::CreateView  
 创建了静态拆分窗口的窗格。  
  
```  
virtual BOOL CreateView(
    int row,  
    int col,  
    CRuntimeClass* pViewClass,  
    SIZE sizeInit,  
    CCreateContext* pContext);
```  
  
### <a name="parameters"></a>参数  
 *行*  
 指定要在其中放置新视图的拆分器窗口一行。  
  
 *列号*  
 指定要在其中放置新视图的拆分器窗口中列。  
  
 *pViewClass*  
 指定[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)的新视图。  
  
 *sizeInit*  
 指定新视图的初始大小。  
  
 *pContext*  
 一个指向用于创建该视图创建上下文 (通常*pContext*传递到父框架重写[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)拆分器窗口是成员函数正在创建）。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 框架显示拆分器之前，必须创建静态拆分窗口的所有窗格。  
  
 该框架还会调用此成员函数以创建新窗格时动态拆分窗口的用户将拆分窗格、 行或列。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]  
  
##  <a name="csplitterwnd"></a>  CSplitterWnd::CSplitterWnd  
 调用以构造`CSplitterWnd`对象。  
  
```  
CSplitterWnd();
```  
  
### <a name="remarks"></a>备注  
 构造`CSplitterWnd`两个步骤中的对象。 首先，调用构造函数中，这会创建`CSplitterWnd`对象，，然后调用[创建](#create)成员函数，其创建拆分器窗口，并将其附加到`CSplitterWnd`对象。  
  
##  <a name="deletecolumn"></a>  CSplitterWnd::DeleteColumn  
 从拆分器窗口中删除列。  
  
```  
virtual void DeleteColumn(int colDelete);
```  
  
### <a name="parameters"></a>参数  
 *colDelete*  
 指定要删除的列。  
  
### <a name="remarks"></a>备注  
 此成员函数调用由框架来实现动态拆分窗口的逻辑 （即，如果拆分器窗口具有 SPLS_DYNAMIC_SPLIT 样式）。 它可以进行自定义，以及虚函数[CreateView](#createview)，从而实现更高级的动态拆分器。  
  
##  <a name="deleterow"></a>  CSplitterWnd::DeleteRow  
 从拆分器窗口中删除行。  
  
```  
virtual void DeleteRow(int rowDelete);
```  
  
### <a name="parameters"></a>参数  
 *行删除*  
 指定要删除的行。  
  
### <a name="remarks"></a>备注  
 此成员函数调用由框架来实现动态拆分窗口的逻辑 （即，如果拆分器窗口具有 SPLS_DYNAMIC_SPLIT 样式）。 它可以进行自定义，以及虚函数[CreateView](#createview)，从而实现更高级的动态拆分器。  
  
##  <a name="deleteview"></a>  CSplitterWnd::DeleteView  
 从拆分器窗口中删除视图。  
  
```  
virtual void DeleteView(
    int row,  
    int col);
```  
  
### <a name="parameters"></a>参数  
 *行*  
 指定要删除的视图的拆分器窗口一行。  
  
 *列号*  
 指定要删除的视图的拆分器窗口中列。  
  
### <a name="remarks"></a>备注  
 如果删除活动的视图时下, 一个视图将处于活动状态。 默认实现假设将自动在视图中删除[PostNcDestroy](../../mfc/reference/cwnd-class.md#postncdestroy)。  
  
 此成员函数调用由框架来实现动态拆分窗口的逻辑 （即，如果拆分器窗口具有 SPLS_DYNAMIC_SPLIT 样式）。 它可以进行自定义，以及虚函数[CreateView](#createview)，从而实现更高级的动态拆分器。  
  
##  <a name="dokeyboardsplit"></a>  CSplitterWnd::DoKeyboardSplit  
 执行键盘拆分命令，通常"窗口拆分。"  
  
```  
virtual BOOL DoKeyboardSplit();
```  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 此成员函数是由一个高级别命令[CView](../../mfc/reference/cview-class.md)类将委派给`CSplitterWnd`实现。  
  
##  <a name="doscroll"></a>  CSplitterWnd::DoScroll  
 执行拆分窗口同步滚动。  
  
```  
virtual BOOL DoScroll(
    CView* pViewFrom,  
    UINT nScrollCode,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *pViewFrom*  
 一个指向从其中产生滚动消息的视图。  
  
 *nScrollCode*  
 指示用户的滚动条代码的滚动请求。 此参数由两个部分组成： 确定的水平滚动发生的类型，低序位字节和高位字节，用于确定的垂直滚动发生类型：  
  
    - SB_BOTTOM 滚动到底部。  
      
    - SB_LINEDOWN 滚动行下移一行。  
      
    - SB_LINEUP 滚动行上移一行。  
      
    - 向下 SB_PAGEDOWN 滚动一页。  
      
    - 向上 SB_PAGEUP 滚动一页。  
      
    - SB_TOP 滚动到顶部。  
  
 *bDoScroll*  
 确定是否执行了指定的滚动操作。 如果*bDoScroll*为 TRUE （即，如果存在的子窗口，并且拆分窗口具有滚动范围），则指定滚动操作可能需要的位置; 如果*bDoScroll*为 FALSE （即，如果没有子窗口存在，或拆分视图具有无滚动范围)，则不会发生滚动。  
  
### <a name="return-value"></a>返回值  
 如果同步滚动发生; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 由框架来执行同步滚动拆分窗口的视图接收滚动消息时调用此成员函数。 重写以允许同步滚动之前，需要用户执行操作。  
  
##  <a name="doscrollby"></a>  CSplitterWnd::DoScrollBy  
 给定的像素数目滚动拆分窗口。  
  
```  
virtual BOOL DoScrollBy(
    CView* pViewFrom,  
    CSize sizeScroll,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *pViewFrom*  
 一个指向从其中产生滚动消息的视图。  
  
 *sizeScroll*  
 若要水平和垂直滚动的像素数。  
  
 *bDoScroll*  
 确定是否执行了指定的滚动操作。 如果*bDoScroll*为 TRUE （即，如果存在的子窗口，并且拆分窗口具有滚动范围），则指定滚动操作可能需要的位置; 如果*bDoScroll*为 FALSE （即，如果没有子窗口存在，或拆分视图具有无滚动范围)，则不会发生滚动。  
  
### <a name="return-value"></a>返回值  
 如果同步滚动发生; 非零值否则为 0。  
  
### <a name="remarks"></a>备注  
 响应滚动消息框架调用此成员函数、 执行同步滚动拆分窗口的数量，以像素为单位，为由*sizeScroll*。 正值指示向下和向右; 滚动负值表示向上和向左滚动。  
  
 重写以要求用户允许滚动之前执行操作。  
  
##  <a name="getactivepane"></a>  CSplitterWnd::GetActivePane  
 确定活动窗格从焦点或活动视图的框架中。  
  
```  
virtual CWnd* GetActivePane(
    int* pRow = NULL,  
    int* pCol = NULL);
```  
  
### <a name="parameters"></a>参数  
 *pRow*  
 一个指向**int**检索活动的窗格中的行号。  
  
 *pCol*  
 一个指向**int**检索活动的窗格中的列号。  
  
### <a name="return-value"></a>返回值  
 指向活动的窗格。 如果没有活动的窗格中存在，则为 NULL。  
  
### <a name="remarks"></a>备注  
 由框架可以确定活动窗格拆分器窗口中的调用此成员函数。 重写为需要用户执行操作之前获取活动的窗格。  
  
##  <a name="getcolumncount"></a>  CSplitterWnd::GetColumnCount  
 返回当前窗格中列数。  
  
```  
int GetColumnCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 在拆分器返回当前的列数。 对于静态拆分，这也将是最大列数。  
  
##  <a name="getcolumninfo"></a>  CSplitterWnd::GetColumnInfo  
 返回指定的列信息。  
  
```  
void GetColumnInfo(
    int col,  
    int& cxCur,  
    int& cxMin) const;  
```  
  
### <a name="parameters"></a>参数  
 *列号*  
 指定的列。  
  
 *cxCur*  
 对引用**int**设置为当前列的宽度。  
  
 *cxMin*  
 对引用**int**设置为列的当前最小宽度。  
  
##  <a name="getpane"></a>  CSplitterWnd::GetPane  
 返回位于指定的行和列的窗格。  
  
```  
CWnd* GetPane(
    int row,  
    int col) const;  
```  
  
### <a name="parameters"></a>参数  
 *行*  
 指定的行。  
  
 *列号*  
 指定的列。  
  
### <a name="return-value"></a>返回值  
 返回位于指定的行和列的窗格。 在返回的窗格中，通常[CView](../../mfc/reference/cview-class.md)-派生的类。  
  
##  <a name="getrowcount"></a>  CSplitterWnd::GetRowCount  
 返回当前窗格行计数。  
  
```  
int GetRowCount() const;  
```  
  
### <a name="return-value"></a>返回值  
 在拆分器窗口中返回当前的行数。 静态拆分窗口，这也将是最大行数。  
  
##  <a name="getrowinfo"></a>  CSplitterWnd::GetRowInfo  
 返回指定行的信息。  
  
```  
void GetRowInfo(
    int row,  
    int& cyCur,  
    int& cyMin) const;  
```  
  
### <a name="parameters"></a>参数  
 *行*  
 指定的行。  
  
 *cyCur*  
 引用**int**设置为以像素为单位的行的当前高度。  
  
 *cyMin*  
 引用**int**设置为以像素为单位的行的当前最小高度。  
  
### <a name="remarks"></a>备注  
 调用此成员函数以获取有关指定行的信息。 *CyCur*参数填充指定行的当前高度和*cyMin*填充行的最小高度。  
  
##  <a name="getscrollstyle"></a>  CSplitterWnd::GetScrollStyle  
 返回拆分器窗口的共享的滚动条样式。  
  
```  
DWORD GetScrollStyle() const;  
```  
  
### <a name="return-value"></a>返回值  
 一个或多个以下的窗口样式标志，如果成功，则：  
  
    - WS_HSCROLL 如果拆分器当前管理共享水平滚动条。  
      
    - WS_VSCROLL 如果拆分器当前管理共享垂直滚动条。  
  
 如果为零，拆分器窗口不会当前管理任何共享的滚动条。  
  
##  <a name="idfromrowcol"></a>  CSplitterWnd::IdFromRowCol  
 获取子窗口 ID 位于指定的行和列的窗格。  
  
```  
int IdFromRowCol(
    int row,  
    int col) const;  
```  
  
### <a name="parameters"></a>参数  
 *行*  
 指定的拆分器窗口中的一行。  
  
 *列号*  
 指定的拆分器窗口中列。  
  
### <a name="return-value"></a>返回值  
 在窗格子窗口 ID。  
  
### <a name="remarks"></a>备注  
 此成员函数用于创建为窗格 nonviews，并且可能会在调用之前窗格中存在。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]  
  
##  <a name="ischildpane"></a>  CSplitterWnd::IsChildPane  
 确定是否*pWnd*目前是此拆分器窗口的一个子窗格。  
  
```  
BOOL IsChildPane(
    CWnd* pWnd,  
    int* pRow,  
    int* pCol);
```  
  
### <a name="parameters"></a>参数  
 *pWnd*  
 一个指向[CWnd](../../mfc/reference/cwnd-class.md)要测试对象。  
  
 *pRow*  
 一个指向**int**用来存储行的行号。  
  
 *pCol*  
 一个指向**int**要在其中存储列号。  
  
### <a name="return-value"></a>返回值  
 如果非零， *pWnd*目前此拆分器窗口中，一个子窗格和*pRow*并*pCol*使用拆分器窗口中窗格的位置填充。 如果*pWnd*不是子窗格的拆分器窗口中，则返回 0。  
  
### <a name="remarks"></a>备注  
 在 Visual c + + 6.0 之前的版本，此函数被定义为  
  
 `BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`  
  
 此版本现已过时，不应使用。  
  
##  <a name="istracking"></a>  CSplitterWnd::IsTracking  
 调用此成员函数可确定在窗口中的拆分器栏当前正在移动。  
  
```  
BOOL IsTracking();
```  
  
### <a name="return-value"></a>返回值  
 如果拆分器操作正在进行中; 为非零值否则为 0。  
  
##  <a name="ondrawsplitter"></a>  CSplitterWnd::OnDrawSplitter  
 呈现拆分窗口的图像。  
  
```  
virtual void OnDrawSplitter(
    CDC* pDC,  
    ESplitType nType,  
    const CRect& rect);
```  
  
### <a name="parameters"></a>参数  
 *pDC*  
 指向要在其中绘制的设备上下文的指针。 如果*pDC*为 NULL，则[CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow)称为窗口中绘制的框架和任何拆分。  
  
 *n 类型*  
 值为`enum ESplitType`，可以是以下值之一：  
  
    - `splitBox` 拆分器拖动框。  
      
    - `splitBar` 显示两个拆分窗口之间的栏。  
      
    - `splitIntersection` 拆分窗口的交集。 在 Windows 95/98 上运行时不会调用此元素。  
      
    - `splitBorder` 拆分窗口边框。  
  
 *rect*  
 对引用[CRect](../../atl-mfc-shared/reference/crect-class.md)对象，它指定的大小和形状的拆分窗口。  
  
### <a name="remarks"></a>备注  
 此成员函数调用框架可绘制，并指定拆分器窗口的精确特征。 重写`OnDrawSplitter`的拆分器窗口的各种图形组件的图像的高级自定义项。 默认图像的类似于 Microsoft 适用于 Windows 或 Microsoft Windows 95、windows 98 中的拆分器在于拆分条的交集的混合在一起。  
  
 动态拆分窗口的详细信息，请参阅"拆分器 Windows"一文中[多个文档类型、 视图和框架 Windows](../../mfc/multiple-document-types-views-and-frame-windows.md)，[技术注意 29](../../mfc/tn029-splitter-windows.md)，和`CSplitterWnd`类概述。  
  
##  <a name="oninverttracker"></a>  CSplitterWnd::OnInvertTracker  
 呈现拆分窗口是相同的大小和形状一样的框架窗口的图像。  
  
```  
virtual void OnInvertTracker(const CRect& rect);
```  
  
### <a name="parameters"></a>参数  
 *rect*  
 引用`CRect`对象，指定跟踪矩形。  
  
### <a name="remarks"></a>备注  
 此成员函数在调整大小的拆分条过程由框架调用。 重写`OnInvertTracker`的拆分器窗口的图像的高级自定义项。 默认图像的类似于 Microsoft 适用于 Windows 或 Microsoft Windows 95、windows 98 中的拆分器在于拆分条的交集的混合在一起。  
  
 动态拆分窗口的详细信息，请参阅"拆分器 Windows"一文中[多个文档类型、 视图和框架 Windows](../../mfc/multiple-document-types-views-and-frame-windows.md)，[技术注意 29](../../mfc/tn029-splitter-windows.md)，和`CSplitterWnd`类概述。  
  
##  <a name="recalclayout"></a>  CSplitterWnd::RecalcLayout  
 若要在调整行或列大小之后重新显示在拆分器窗口的调用。  
  
```  
virtual void RecalcLayout();
```  
  
### <a name="remarks"></a>备注  
 调用此成员函数以正确地重新拆分器窗口显示后已调整行和列的大小随[SetRowInfo](#setrowinfo)并[SetColumnInfo](#setcolumninfo)成员函数。 如果拆分器窗口才会显示在创建过程的一部分更改行和列的大小，，不需要调用此成员函数。  
  
 每当用户调整拆分器窗口的大小或移动拆分时，框架将调用此成员函数。  
  
### <a name="example"></a>示例  
  有关示例，请参阅[CSplitterWnd::SetColumnInfo](#setcolumninfo)。  
  
##  <a name="setactivepane"></a>  CSplitterWnd::SetActivePane  
 将窗格使处于活动状态的框架中的设置。  
  
```  
virtual void SetActivePane(
    int row,  
    int col,  
    CWnd* pWnd = NULL);
```  
  
### <a name="parameters"></a>参数  
 *行*  
 如果*pWnd*为 NULL，在将处于活动状态的窗格中指定的一行。  
  
 *列号*  
 如果*pWnd*为 NULL，指定将处于活动状态的窗格中的列。  
  
 *pWnd*  
 一个指向`CWnd`对象。 如果为 NULL，指定在窗格*行*并*col*设置活动。 如果不为 NULL，指定设置活动的窗格。  
  
### <a name="remarks"></a>备注  
 此成员函数调用框架可将一个窗格设置为活动，当用户将焦点更改到框架窗口中的窗格。 您可以显式调用`SetActivePane`将焦点更改到指定的视图。  
  
 通过提供行和列中，指定窗格**或**通过提供*pWnd*。  
  
##  <a name="setcolumninfo"></a>  CSplitterWnd::SetColumnInfo  
 调用以设置指定的列信息。  
  
```  
void SetColumnInfo(
    int col,  
    int cxIdeal,  
    int cxMin);
```  
  
### <a name="parameters"></a>参数  
 *列号*  
 指定拆分器窗口中列。  
  
 *cxIdeal*  
 以像素为单位指定拆分器窗口中列的理想宽度。  
  
 *cxMin*  
 以像素为单位指定拆分器窗口中列的最小宽度。  
  
### <a name="remarks"></a>备注  
 调用此成员函数以设置新的最小宽度和列的理想宽度。 列最小值确定的列将太小，无法完全显示。  
  
 当框架显示拆分器窗口时，布局中列和行根据其理想的维度，从左上方工作的拆分器窗口的工作区的右下角的窗格。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]  
  
##  <a name="setrowinfo"></a>  CSplitterWnd::SetRowInfo  
 用于设置指定的行信息的调用。  
  
```  
void SetRowInfo(
    int row,  
    int cyIdeal,  
    int cyMin);
```  
  
### <a name="parameters"></a>参数  
 *行*  
 指定拆分器窗口行。  
  
 *cyIdeal*  
 以像素为单位指定拆分器窗口行的理想高度。  
  
 *cyMin*  
 以像素为单位指定拆分器窗口行的最小高度。  
  
### <a name="remarks"></a>备注  
 调用此成员函数以设置新的最小高度和行的理想高度。 行最小值确定当会太小，无法完全显示的行。  
  
 当框架显示拆分器窗口时，布局中列和行根据其理想的维度，从左上方工作的拆分器窗口的工作区的右下角的窗格。  
  
##  <a name="setscrollstyle"></a>  CSplitterWnd::SetScrollStyle  
 指定拆分器窗口的滚动新式共享滚动条支持。  
  
```  
void SetScrollStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>参数  
 *dwStyle*  
 拆分器窗口的滚动新式共享滚动条支持，可以是下列值之一：  
  
- WS_HSCROLL 创建/显示共享水平滚动条。  
  
- WS_VSCROLL 创建/显示垂直共享的滚动条。  
  
### <a name="remarks"></a>备注  
 创建的滚动条后不会销毁即使`SetScrollStyle`调用，但不该样式; 而是隐藏这些滚动条。 这允许滚动条以保持其状态，即使已将其隐藏。 在调用`SetScrollStyle`不必调用时会[RecalcLayout](#recalclayout)的所有更改才会生效。  
  
##  <a name="splitcolumn"></a>  CSplitterWnd::SplitColumn  
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
 创建垂直拆分器窗口时调用此成员函数。 `SplitColumn` 指示发生拆分的位置的默认位置。  
  
 `SplitColumn` 若要实现动态拆分窗口的逻辑 （即，如果拆分器窗口具有 SPLS_DYNAMIC_SPLIT 样式） 框架调用。 它可以进行自定义，以及虚函数[CreateView](#createview)，从而实现更高级的动态拆分器。  
  
##  <a name="splitrow"></a>  CSplitterWnd::SplitRow  
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
 创建水平拆分器窗口时调用此成员函数。 `SplitRow` 指示发生拆分的位置的默认位置。  
  
 `SplitRow` 若要实现动态拆分窗口的逻辑 （即，如果拆分器窗口具有 SPLS_DYNAMIC_SPLIT 样式） 框架调用。 它可以进行自定义，以及虚函数[CreateView](#createview)，从而实现更高级的动态拆分器。  
  
##  <a name="ondraw"></a>  CSplitterWnd::OnDraw  
 由框架调用以绘制拆分器窗口。  
  
```  
virtual void OnDraw(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 *pDC*  
 一个指向设备上下文的指针。  
  
### <a name="remarks"></a>备注  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 VIEWEX](../../visual-cpp-samples.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [CView 类](../../mfc/reference/cview-class.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)
