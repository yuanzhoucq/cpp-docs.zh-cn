---
title: CListCtrl
ms.date: 11/04/2016
f1_keywords:
- CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl::CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl::EnableMultipleSort
- AFXHEADERCTRL/CMFCHeaderCtrl::GetColumnState
- AFXHEADERCTRL/CMFCHeaderCtrl::GetSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::IsAscending
- AFXHEADERCTRL/CMFCHeaderCtrl::IsDialogControl
- AFXHEADERCTRL/CMFCHeaderCtrl::IsMultipleSort
- AFXHEADERCTRL/CMFCHeaderCtrl::RemoveSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::SetSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::OnDrawItem
- AFXHEADERCTRL/CMFCHeaderCtrl::OnDrawSortArrow
- AFXHEADERCTRL/CMFCHeaderCtrl::OnFillBackground
helpviewer_keywords:
- CMFCHeaderCtrl [MFC], CMFCHeaderCtrl
- CMFCHeaderCtrl [MFC], EnableMultipleSort
- CMFCHeaderCtrl [MFC], GetColumnState
- CMFCHeaderCtrl [MFC], GetSortColumn
- CMFCHeaderCtrl [MFC], IsAscending
- CMFCHeaderCtrl [MFC], IsDialogControl
- CMFCHeaderCtrl [MFC], IsMultipleSort
- CMFCHeaderCtrl [MFC], RemoveSortColumn
- CMFCHeaderCtrl [MFC], SetSortColumn
- CMFCHeaderCtrl [MFC], OnDrawItem
- CMFCHeaderCtrl [MFC], OnDrawSortArrow
- CMFCHeaderCtrl [MFC], OnFillBackground
ms.assetid: 2f5fbf7b-5c75-42db-9216-640b1628f777
ms.openlocfilehash: 86674e086da482e59b2711f5ba9154848ff05a6f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57269430"
---
# <a name="cmfcheaderctrl-class"></a>CListCtrl

`CMFCHeaderCtrl`类支持对标头控件中的多个列进行排序。

## <a name="syntax"></a>语法

```
class CMFCHeaderCtrl : public CHeaderCtrl
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCHeaderCtrl::CMFCHeaderCtrl](#cmfcheaderctrl)|构造 `CMFCHeaderCtrl` 对象。|
|`CMFCHeaderCtrl::~CMFCHeaderCtrl`|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)|启用或禁用*多个列的排序*当前标头控件模式。|
|[CMFCHeaderCtrl::GetColumnState](#getcolumnstate)|指示列是否未排序，或者按升序或降序顺序排序。|
|[CMFCHeaderCtrl::GetSortColumn](#getsortcolumn)|检索标头控件中第一个已排序的列的从零开始的索引。|
|`CMFCHeaderCtrl::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)与此类类型相关联的对象。|
|[CMFCHeaderCtrl::IsAscending](#isascending)|指示标头控件中的任何列按升序排序。|
|[CMFCHeaderCtrl::IsDialogControl](#isdialogcontrol)|指示当前的标头控件的父窗口是否是一个对话框。|
|[CMFCHeaderCtrl::IsMultipleSort](#ismultiplesort)|指示当前的标头控件是否处于*多个列的排序*模式。|
|[CMFCHeaderCtrl::RemoveSortColumn](#removesortcolumn)|从列进行排序的列表中删除指定的列。|
|[CMFCHeaderCtrl::SetSortColumn](#setsortcolumn)|设置标头控件中的指定列的排序顺序。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CMFCHeaderCtrl::OnDrawItem](#ondrawitem)|由框架调用以绘制标头控件列。|
|[CMFCHeaderCtrl::OnDrawSortArrow](#ondrawsortarrow)|由框架调用以绘制的排序箭头。|
|[CMFCHeaderCtrl::OnFillBackground](#onfillbackground)|由框架调用以填充标头控件列的背景。|

## <a name="example"></a>示例

下面的示例演示如何构造的对象`CMFCHeaderCtrl`类，以及如何启用*多个列的排序*当前标头控件模式。

[!code-cpp[NVC_MFC_RibbonApp#24](../../mfc/reference/codesnippet/cpp/cmfcheaderctrl-class_1.cpp)]

## <a name="remarks"></a>备注

`CMFCHeaderCtrl`类绘制指示对列进行排序的标头控件列的排序箭头。 使用*多个列的排序*模式下，如果一组的父列表控件中的列 ( [CMFCListCtrl 类](../../mfc/reference/cmfclistctrl-class.md)) 可以在同一时间进行排序。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)

[CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)

## <a name="requirements"></a>要求

**标头：** afxheaderctrl.h

##  <a name="cmfcheaderctrl"></a>  CMFCHeaderCtrl::CMFCHeaderCtrl

构造 `CMFCHeaderCtrl` 对象。

```
CMFCHeaderCtrl::CMFCHeaderCtrl()
```

### <a name="remarks"></a>备注

此构造函数初始化为指定值的以下成员变量：

|成员变量|值|
|---------------------|-----------|
|`m_bIsMousePressed`|false|
|`m_bMultipleSort`|false|
|`m_bAscending`|true|
|`m_nHighlightedItem`|-1|
|`m_bTracked`|false|
|`m_bIsDlgControl`|FALSE|
|`m_hFont`|NULL|

##  <a name="enablemultiplesort"></a>  CMFCHeaderCtrl::EnableMultipleSort

启用或禁用*多个列的排序*当前标头控件模式。

```
void EnableMultipleSort(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
[in]如果启用了多个列排序模式，则为若要禁用多个列排序模式，并从已排序的列的列表中删除任何列，则为 FALSE。 默认值为 TRUE。

### <a name="remarks"></a>备注

使用此方法启用或禁用多个列排序模式。 如果标头控件是在多个列排序模式中两个或多个列可以参与排序。

##  <a name="getcolumnstate"></a>  CMFCHeaderCtrl::GetColumnState

指示列是否是未排序，或者按升序或降序顺序排序。

```
int GetColumnState(int iColumn) const;
```

### <a name="parameters"></a>参数

*iColumn*<br/>
[in]列的从零开始的索引。

### <a name="return-value"></a>返回值

一个值，指示指定列的排序状态。 下表列出了可能的值：

|值|描述|
|-----------|-----------------|
|-1|按降序排序。|
|0|未排序。|
|1|按升序排序。|

### <a name="remarks"></a>备注

##  <a name="getsortcolumn"></a>  CMFCHeaderCtrl::GetSortColumn

检索标头控件中第一个已排序的列的从零开始的索引。

```
int GetSortColumn() const;
```

### <a name="return-value"></a>返回值

已排序的列或如果不找到任何已排序的列，则为-1 的索引。

### <a name="remarks"></a>备注

如果标头控件处于*多个列的排序*模式，并且您将应用程序编译在调试模式下，此方法断言，并建议您在使用[CMFCHeaderCtrl::GetColumnState](#getcolumnstate)方法相反。 如果标头控件在多个列排序模式中，并且编译零售模式中的应用程序，此方法将返回-1。

##  <a name="isascending"></a>  CMFCHeaderCtrl::IsAscending

指示标头控件中的任何列按升序排序。

```
BOOL IsAscending() const;
```

### <a name="return-value"></a>返回值

如果标头控件中的任何列按升序顺序; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法返回的值用于标题控件项上显示相应的排序箭头。 使用[CMFCHeaderCtrl::SetSortColumn](#setsortcolumn)方法设置的排序顺序。

##  <a name="isdialogcontrol"></a>  CMFCHeaderCtrl::IsDialogControl

指示当前的标头控件的父窗口是否是一个对话框。

```
BOOL IsDialogControl() const;
```

### <a name="return-value"></a>返回值

如果当前的标头控件的父窗口对话框; 则为 TRUE否则为 FALSE。

##  <a name="ismultiplesort"></a>  CMFCHeaderCtrl::IsMultipleSort

指示当前的标头控件是否处于*多个列的排序*模式。

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>返回值

如果启用多个列排序模式; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

使用[CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)方法启用或禁用多个列排序模式。 如果标头控件是在多个列排序模式中两个或多个列可以参与排序。

##  <a name="ondrawitem"></a>  CMFCHeaderCtrl::OnDrawItem

由框架调用以绘制标头控件列。

```
virtual void OnDrawItem(
    CDC* pDC,
    int iItem,
    CRect rect,
    BOOL bIsPressed,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]指向设备上下文的指针。

*iItem*<br/>
[in]要绘制的项的从零开始的索引。

*rect*<br/>
[in]要绘制的项的边框。

*bIsPressed*<br/>
[in]为 TRUE，则在按下状态，则绘制项否则为 FALSE。

*bIsHighlighted*<br/>
[in]为 TRUE，则绘制突出显示的状态; 中的项否则为 FALSE。

##  <a name="ondrawsortarrow"></a>  CMFCHeaderCtrl::OnDrawSortArrow

由框架调用以绘制的排序箭头。

```
virtual void OnDrawSortArrow(
    CDC* pDC,
    CRect rectArrow);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]指向设备上下文的指针。

*rectArrow*<br/>
[in]排序箭头的边框。

##  <a name="onfillbackground"></a>  CMFCHeaderCtrl::OnFillBackground

由框架调用以填充标头控件列的背景。

```
virtual void OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]指向设备上下文的指针。

### <a name="remarks"></a>备注

##  <a name="removesortcolumn"></a>  CMFCHeaderCtrl::RemoveSortColumn

从列进行排序的列表中删除指定的列。

```
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>参数

*iColumn*<br/>
[in]要删除的列的从零开始的索引。

##  <a name="setsortcolumn"></a>  CMFCHeaderCtrl::SetSortColumn

设置标头控件中的指定列的排序顺序。

```
void SetSortColumn(
    int iColumn,
    BOOL bAscending=TRUE,
    BOOL bAdd=FALSE);
```

### <a name="parameters"></a>参数

*iColumn*<br/>
[in]标头控件列的从零开始的索引。 如果此参数小于零，此方法从列进行排序的列表中删除所有列。

*bAscending*<br/>
[in]指定列的排序顺序的*iColumn*参数指定。 为 TRUE，则设置按升序顺序;为 FALSE，则设置按降序排序。 默认值为 TRUE。

*bAdd*<br/>
[in]如果为列的排序顺序设置*iColumn*参数指定。

如果当前的标头控件处于*多个列的排序*模式下，此方法将指定的列添加到对列进行排序的列表。 使用[CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)设置多个列排序模式。

如果未设置多个列排序模式和在调试模式下编译此方法，此方法断言。 如果未设置多个列排序模式，并且在零售模式下编译此方法，此方法首先从列表中的列进行排序，删除所有列，然后将指定的列添加到列表。

如果为 FALSE，则首先从列表中的列进行排序，删除所有列，然后将指定的列添加到列表。 默认值是 FALSE。

### <a name="remarks"></a>备注

此方法用于设置列的排序顺序。 如有必要，此方法将列添加到对列进行排序的列表。 标头控件使用的排序顺序绘制点向上或向下排序箭头。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCListCtrl 类](../../mfc/reference/cmfclistctrl-class.md)
