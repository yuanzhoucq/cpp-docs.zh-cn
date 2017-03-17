---
title: "CMFCHeaderCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CMFCHeaderCtrl class
ms.assetid: 2f5fbf7b-5c75-42db-9216-640b1628f777
caps.latest.revision: 29
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
ms.openlocfilehash: c49ee61b6441e79a0c3c4c1aa133b4bce1578103
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcheaderctrl-class"></a>CListCtrl
`CMFCHeaderCtrl`类支持对标头控件中的多个列进行排序。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCHeaderCtrl : public CHeaderCtrl  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCHeaderCtrl::CMFCHeaderCtrl](#cmfcheaderctrl)|构造 `CMFCHeaderCtrl` 对象。|  
|`CMFCHeaderCtrl::~CMFCHeaderCtrl`|析构函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)|启用或禁用*多列排序*当前标头控件的模式。|  
|[CMFCHeaderCtrl::GetColumnState](#getcolumnstate)|指示某一列未排序，还是在升序或降序进行排序。|  
|[CMFCHeaderCtrl::GetSortColumn](#getsortcolumn)|检索标头控件中第一个排序的列的从零开始索引。|  
|`CMFCHeaderCtrl::GetThisClass`|由框架用于获取一个指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)程序与此类类型的对象。|  
|[CMFCHeaderCtrl::IsAscending](#isascending)|指示标头控件中的任何列按升序排序。|  
|[CMFCHeaderCtrl::IsDialogControl](#isdialogcontrol)|表示当前标头控件的父窗口是否是一个对话框。|  
|[CMFCHeaderCtrl::IsMultipleSort](#ismultiplesort)|该值指示当前的标头控件是否处于*多列排序*模式。|  
|[CMFCHeaderCtrl::RemoveSortColumn](#removesortcolumn)|从对列进行排序的列表中移除指定的列。|  
|[CMFCHeaderCtrl::SetSortColumn](#setsortcolumn)|标头控件中设置指定列的排序顺序。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCHeaderCtrl::OnDrawItem](#ondrawitem)|由框架用于绘制标头控件列调用。|  
|[CMFCHeaderCtrl::OnDrawSortArrow](#ondrawsortarrow)|由框架用于绘制排序箭头调用。|  
|[CMFCHeaderCtrl::OnFillBackground](#onfillbackground)|由框架来填充标头控件列的背景调用。|  
  
## <a name="example"></a>示例  
 下面的示例演示如何构造的对象`CMFCHeaderCtrl`类，以及如何启用*多列排序*当前标头控件的模式。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&24;](../../mfc/reference/codesnippet/cpp/cmfcheaderctrl-class_1.cpp)]  
  
## <a name="remarks"></a>备注  
 `CMFCHeaderCtrl`类绘制排序箭头对标头控件列来指示对列进行排序。 使用*多列排序*模式下，如果一组的父级列表控件中的列 ( [CMFCListCtrl 类](../../mfc/reference/cmfclistctrl-class.md)) 可以在同一时间进行排序。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)  
  
 [CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)  
  
## <a name="requirements"></a>要求  
 **标头︰** afxheaderctrl.h  
  
##  <a name="cmfcheaderctrl"></a>CMFCHeaderCtrl::CMFCHeaderCtrl  
 构造 `CMFCHeaderCtrl` 对象。  
  
```  
CMFCHeaderCtrl::CMFCHeaderCtrl()  
```  
  
### <a name="remarks"></a>备注  
 此构造函数初始化为指定值的以下成员变量︰  
  
|成员变量|值|  
|---------------------|-----------|  
|`m_bIsMousePressed`|`FALSE`|  
|`m_bMultipleSort`|`FALSE`|  
|`m_bAscending`|`TRUE`|  
|`m_nHighlightedItem`|-1|  
|`m_bTracked`|`FALSE`|  
|`m_bIsDlgControl`|`FALSE`|  
|`m_hFont`|`NULL`|  
  
##  <a name="enablemultiplesort"></a>CMFCHeaderCtrl::EnableMultipleSort  
 启用或禁用*多列排序*当前标头控件的模式。  
  
```  
void EnableMultipleSort(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 `TRUE`若要启用多个列排序模式;`FALSE`禁用多个列排序模式以及从排序的列的列表中删除任何列。 默认值为 `TRUE`。  
  
### <a name="remarks"></a>备注  
 此方法用于启用或禁用多个列排序模式。 如果标头控件是在多个列排序模式中两个或多个列可以参与排序。  
  
##  <a name="getcolumnstate"></a>CMFCHeaderCtrl::GetColumnState  
 指示列是否是未排序，或者按升序或降序排序。  
  
```  
int GetColumnState(int iColumn) const;  
```  
  
### <a name="parameters"></a>参数  
 [in] `iColumn`  
 列的从零开始的索引。  
  
### <a name="return-value"></a>返回值  
 一个值，指示指定的列的排序状态。 下表列出了可能的值︰  
  
|值|描述|  
|-----------|-----------------|  
|-1|按降序排序。|  
|0|不进行排序。|  
|1|按升序排序。|  
  
### <a name="remarks"></a>备注  
  
##  <a name="getsortcolumn"></a>CMFCHeaderCtrl::GetSortColumn  
 检索标头控件中第一个排序的列的从零开始索引。  
  
```  
int GetSortColumn() const;  
```  
  
### <a name="return-value"></a>返回值  
 排的序列，则为-1 如果找到未排序的列的索引。  
  
### <a name="remarks"></a>备注  
 如果标头控件位于*多列排序*模式，并且您编译该应用程序在调试模式下，此方法断言，并建议您在使用[CMFCHeaderCtrl::GetColumnState](#getcolumnstate)方法相反。 如果标头控件处于多个列排序模式，并且编译该应用程序以发布模式，则此方法返回-1。  
  
##  <a name="isascending"></a>CMFCHeaderCtrl::IsAscending  
 指示标头控件中的任何列按升序排序。  
  
```  
BOOL IsAscending() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果标头控件中的任何列按升序排序。否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法返回的值用于在标题控件项上显示相应的排序箭头。 使用[CMFCHeaderCtrl::SetSortColumn](#setsortcolumn)方法设置的排序顺序。  
  
##  <a name="isdialogcontrol"></a>CMFCHeaderCtrl::IsDialogControl  
 表示当前标头控件的父窗口是否是一个对话框。  
  
```  
BOOL IsDialogControl() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果当前的标头控件的父窗口对话框;否则为`FALSE`。  
  
##  <a name="ismultiplesort"></a>CMFCHeaderCtrl::IsMultipleSort  
 该值指示当前的标头控件是否处于*多列排序*模式。  
  
```  
BOOL IsMultipleSort() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果启用了多个列排序模式;否则为`FALSE`。  
  
### <a name="remarks"></a>备注  
 使用[CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)方法来启用或禁用多个列排序模式。 如果标头控件是在多个列排序模式中两个或多个列可以参与排序。  
  
##  <a name="ondrawitem"></a>CMFCHeaderCtrl::OnDrawItem  
 由框架用于绘制标头控件列调用。  
  
```  
virtual void OnDrawItem(
    CDC* pDC,  
    int iItem,  
    CRect rect,  
    BOOL bIsPressed,  
    BOOL bIsHighlighted);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `iItem`  
 要绘制的项的从零开始的索引。  
  
 [in] `rect`  
 要绘制的项的边框。  
  
 [in] `bIsPressed`  
 `TRUE`若要绘制项处于按下状态;否则为`FALSE`。  
  
 [in] `bIsHighlighted`  
 `TRUE`若要绘制突出显示的状态; 中的项否则为`FALSE`。  
  
##  <a name="ondrawsortarrow"></a>CMFCHeaderCtrl::OnDrawSortArrow  
 由框架用于绘制排序箭头调用。  
  
```  
virtual void OnDrawSortArrow(
    CDC* pDC,  
    CRect rectArrow);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
 [in] `rectArrow`  
 排序箭头的边框。  
  
##  <a name="onfillbackground"></a>CMFCHeaderCtrl::OnFillBackground  
 由框架来填充标头控件列的背景调用。  
  
```  
virtual void OnFillBackground(CDC* pDC);
```  
  
### <a name="parameters"></a>参数  
 [in] `pDC`  
 一个指向设备上下文的指针。  
  
### <a name="remarks"></a>备注  
  
##  <a name="removesortcolumn"></a>CMFCHeaderCtrl::RemoveSortColumn  
 从对列进行排序的列表中移除指定的列。  
  
```  
void RemoveSortColumn(int iColumn);
```  
  
### <a name="parameters"></a>参数  
 [in] `iColumn`  
 要删除的列的从零开始的索引。  
  
##  <a name="setsortcolumn"></a>CMFCHeaderCtrl::SetSortColumn  
 标头控件中设置指定列的排序顺序。  
  
```  
void SetSortColumn(
    int iColumn,  
    BOOL bAscending=TRUE,  
    BOOL bAdd=FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `iColumn`  
 标头控件列的从零开始索引。 如果此参数也不可小于零，此方法从对列进行排序的列表中删除所有列。  
  
 [in] `bAscending`  
 指定列的排序顺序，`iColumn`参数指定。 `TRUE`若要设置升序顺序;`FALSE`设置降序排序。 默认值为 `TRUE`。  
  
 [in] `bAdd`  
 `TRUE`对列的排序顺序设置`iColumn`参数指定。  
  
 如果当前的标头控件位于*多列排序*模式下，此方法将指定的列添加到对列进行排序的列表。 使用[CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)来设置多个列排序模式。  
  
 如果未设置多个列排序模式并且以调试模式编译此方法，该方法断言。 如果未设置多个列排序模式并且以发布模式编译此方法，此方法首先从排序的列的列表中删除所有列，然后将指定的列添加到列表。  
  
 `FALSE`为第一个从排序的列的列表中删除所有列，然后添加到列表的指定的列。 默认值为 `FALSE`。  
  
### <a name="remarks"></a>备注  
 此方法用于设置列的排序顺序。 如有必要，此方法会将列添加到对列进行排序的列表。 标头控件使用的排序顺序绘制点上移或下移一个排序箭头。  
  
## <a name="see-also"></a>另请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CMFCListCtrl 类](../../mfc/reference/cmfclistctrl-class.md)

