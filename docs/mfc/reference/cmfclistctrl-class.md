---
title: "CMFCListCtrl 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCListCtrl
- AFXLISTCTRL/CMFCListCtrl
- AFXLISTCTRL/CMFCListCtrl::EnableMarkSortedColumn
- AFXLISTCTRL/CMFCListCtrl::EnableMultipleSort
- AFXLISTCTRL/CMFCListCtrl::GetHeaderCtrl
- AFXLISTCTRL/CMFCListCtrl::IsMultipleSort
- AFXLISTCTRL/CMFCListCtrl::OnCompareItems
- AFXLISTCTRL/CMFCListCtrl::OnGetCellBkColor
- AFXLISTCTRL/CMFCListCtrl::OnGetCellFont
- AFXLISTCTRL/CMFCListCtrl::OnGetCellTextColor
- AFXLISTCTRL/CMFCListCtrl::RemoveSortColumn
- AFXLISTCTRL/CMFCListCtrl::SetSortColumn
- AFXLISTCTRL/CMFCListCtrl::Sort
dev_langs: C++
helpviewer_keywords:
- CMFCListCtrl [MFC], EnableMarkSortedColumn
- CMFCListCtrl [MFC], EnableMultipleSort
- CMFCListCtrl [MFC], GetHeaderCtrl
- CMFCListCtrl [MFC], IsMultipleSort
- CMFCListCtrl [MFC], OnCompareItems
- CMFCListCtrl [MFC], OnGetCellBkColor
- CMFCListCtrl [MFC], OnGetCellFont
- CMFCListCtrl [MFC], OnGetCellTextColor
- CMFCListCtrl [MFC], RemoveSortColumn
- CMFCListCtrl [MFC], SetSortColumn
- CMFCListCtrl [MFC], Sort
ms.assetid: 50d16aee-138c-4f34-8690-cb75d544ef2e
caps.latest.revision: "29"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 770a1cec528355d6f7be7800ba1f77f2394bef79
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cmfclistctrl-class"></a>CMFCListCtrl 类
`CMFCListCtrl`类扩展的功能[CListCtrl 类](../../mfc/reference/clistctrl-class.md)通过支持的高级标头控件功能的类[CMFCHeaderCtrl 类](../../mfc/reference/cmfcheaderctrl-class.md)。  
  
## <a name="syntax"></a>语法  
  
```  
class CMFCListCtrl : public CListCtrl  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMFCListCtrl::EnableMarkSortedColumn](#enablemarksortedcolumn)|能够将标记具有不同的背景色的排序的列。|  
|[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)|使多个排序模式。|  
|[CMFCListCtrl::GetHeaderCtrl](#getheaderctrl)|返回对带下划线的标头控件的引用。|  
|[CMFCListCtrl::IsMultipleSort](#ismultiplesort)|检查列表控件是否在多个排序模式。|  
|[CMFCListCtrl::OnCompareItems](#oncompareitems)|它还必须对两个列表控件项进行比较时，由框架调用。|  
|[CMFCListCtrl::OnGetCellBkColor](#ongetcellbkcolor)|它必须确定各个单元格的背景色时由框架调用。|  
|[CMFCListCtrl::OnGetCellFont](#ongetcellfont)|它必须获取所绘制的单元格的字体时，由框架调用。|  
|[CMFCListCtrl::OnGetCellTextColor](#ongetcelltextcolor)|它必须确定各个单元格的文本颜色时，由框架调用。|  
|[CMFCListCtrl::RemoveSortColumn](#removesortcolumn)|从排序的列的列表中移除列排序。|  
|[CMFCListCtrl::SetSortColumn](#setsortcolumn)|设置当前排的序列和排序顺序。|  
|[CMFCListCtrl::Sort](#sort)|对列表控件进行排序。|  
  
## <a name="remarks"></a>备注  
 `CMFCListCtrl`提供到两个增强功能[CListCtrl 类](../../mfc/reference/clistctrl-class.md)类。 首先，它指示列排序是可用选项通过自动在标头中绘制排序箭头。 其次，它支持在同一时间对多个列进行排序的数据。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用各种方法`CMFCListCtrl`类。 该示例演示如何创建一个列表控件、 插入列、 插入项、 设置项的文本和设置列表控件的字体。 此代码片段属于[Visual Studio 演示示例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/cpp/cmfclistctrl-class_1.h)]  
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/cpp/cmfclistctrl-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListCtrl](../../mfc/reference/clistctrl-class.md)  
  
 [CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)  
  
## <a name="requirements"></a>惠?  
 **标头：** afxlistctrl.h  
  
##  <a name="enablemarksortedcolumn"></a>CMFCListCtrl::EnableMarkSortedColumn  
 将标记与不同的背景色排序的列。  
  
```  
void EnableMarkSortedColumn(
    BOOL bMark = TRUE,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bMark`  
 布尔参数可确定是否启用不同的背景色。  
  
 [in] `bRedraw`  
 布尔参数可确定是否要立即重绘控件。  
  
### <a name="remarks"></a>备注  
 `EnableMarkSortedColumn`使用方法`CDrawingManager::PixelAlpha`计算要使用的颜色已排序的列。 选取的颜色取决于正则背景色。  
  
##  <a name="enablemultiplesort"></a>CMFCListCtrl::EnableMultipleSort  
 启用按多个列进行排序的列表控件中的数据行。  
  
```  
void EnableMultipleSort(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 [in] `bEnable`  
 一个布尔值，指定是否启用多个列排序模式。  
  
### <a name="remarks"></a>备注  
 当你启用排序基于多个列时，列具有层次结构。 首先将按主列进行排序的数据行。 然后按优先级上基于每个后续列排序任何等效值。  
  
##  <a name="getheaderctrl"></a>CMFCListCtrl::GetHeaderCtrl  
 返回对标头控件的引用。  
  
```  
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```  
  
### <a name="return-value"></a>返回值  
 对基础的引用[CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)对象。  
  
### <a name="remarks"></a>备注  
 列表控件的标头控件是包含列标题的窗口。 它通常位于列的正上方。  
  
##  <a name="ismultiplesort"></a>CMFCListCtrl::IsMultipleSort  
 检查是否列表控件当前支持多个列排序。  
  
```  
BOOL IsMultipleSort() const;  
```  
  
### <a name="return-value"></a>返回值  
 `TRUE`如果列表控件支持多个排序;`FALSE`否则为。  
  
### <a name="remarks"></a>备注  
 当[CMFCListCtrl 类](../../mfc/reference/cmfclistctrl-class.md)支持多个排序，用户可以按多个列排序列表控件中的数据。 若要启用多个排序，调用[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)。  
  
##  <a name="oncompareitems"></a>CMFCListCtrl::OnCompareItems  
 它比较两个项时，框架将调用此方法。  
  
```  
virtual int OnCompareItems(
    LPARAM lParam1,  
    LPARAM lParam2,  
    int iColumn);
```  
  
### <a name="parameters"></a>参数  
 [in] `lParam1`  
 要比较的第一项。  
  
 [in] `lParam2`  
 要比较的第二项。  
  
 [in] `iColumn`  
 此方法对进行排序的列的索引。  
  
### <a name="return-value"></a>返回值  
 一个整数，指示两个项的相对位置。 负值表示，第一项应位于之前第二个，则正值表示第一项应遵循第二个，并为零表示两个项是等效项。  
  
### <a name="remarks"></a>备注  
 默认实现始终返回 0。 你必须重写此函数可提供一种排序算法。  
  
##  <a name="ongetcellbkcolor"></a>CMFCListCtrl::OnGetCellBkColor  
 它必须确定各个单元格的背景色时，框架将调用此方法。  
  
```  
virtual COLORREF OnGetCellBkColor(
    int nRow,  
    int nColumn);
```  
  
### <a name="parameters"></a>参数  
 [in] `nRow`  
 相关的单元的行。  
  
 [in] `nColumn`  
 相关的单元的列。  
  
### <a name="return-value"></a>返回值  
 A`COLOREF`值，该值指定单元格的背景色。  
  
### <a name="remarks"></a>备注  
 默认实现`OnGetCellBkColor`不使用提供的输入的参数，而是只需调用`GetBkColor`。 因此，默认情况下，整个列表控件将具有相同的背景色。 您可以重写`OnGetCellBkColor`派生的类将用单独的背景色的各个单元格标记中。  
  
##  <a name="ongetcellfont"></a>CMFCListCtrl::OnGetCellFont  
 当它获取对个别单元格的字体时，框架将调用此方法。  
  
```  
virtual HFONT OnGetCellFont(
    int nRow,  
    int nColumn,  
    DWORD dwData = 0);
```  
  
### <a name="parameters"></a>参数  
 [in] `nRow`  
 相关的单元的行。  
  
 [in] `nColumn`  
 相关的单元的列。  
  
 [in] `dwData`  
 用户定义的数据。 默认实现不使用此参数。  
  
### <a name="return-value"></a>返回值  
 指向用于对当前单元格的字体的句柄。  
  
### <a name="remarks"></a>备注  
 默认情况下，此方法返回`NULL`。 所有列表控件中单元格有相同的字体。 重写此方法，以便为不同的单元格提供不同的字体。  
  
##  <a name="ongetcelltextcolor"></a>CMFCListCtrl::OnGetCellTextColor  
 它必须确定各个单元格的文本颜色时，框架将调用此方法。  
  
```  
virtual COLORREF OnGetCellTextColor(
    int nRow,  
    int nColumn);
```  
  
### <a name="parameters"></a>参数  
 [in] `nRow`  
 相关的单元的行。  
  
 [in] `nColumn`  
 相关的单元的列。  
  
### <a name="return-value"></a>返回值  
 A`COLOREF`值，该值指定单元格的文本颜色。  
  
### <a name="remarks"></a>备注  
 默认情况下，此方法调用`GetTextColor`无论输入参数。 整个列表控件将具有相同的文本颜色。 您可以重写`OnGetCellTextColor`派生的类将用单独的文本颜色的各个单元格标记中。  
  
##  <a name="removesortcolumn"></a>CMFCListCtrl::RemoveSortColumn  
 从排序的列的列表中移除列排序。  
  
```  
void RemoveSortColumn(int iColumn);
```  
  
### <a name="parameters"></a>参数  
 [in] `iColumn`  
 要删除的列。  
  
### <a name="remarks"></a>备注  
 此方法从标头控件中删除列排序。 它调用[CMFCHeaderCtrl::RemoveSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn)。  
  
##  <a name="setsortcolumn"></a>CMFCListCtrl::SetSortColumn  
 设置当前排的序列和排序顺序。  
  
```  
void SetSortColumn(
    int iColumn,  
    BOOL bAscending = TRUE,  
    BOOL bAdd = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `iColumn`  
 要排序的列。  
  
 [in] `bAscending`  
 一个布尔值，指定的排序顺序。  
  
 [in] `bAdd`  
 一个布尔值，指定该方法是否将所指出的列添加`iColumn`到的列排序的列表。  
  
### <a name="remarks"></a>备注  
 此方法将到标头控件的输入的参数传递使用方法[CMFCHeaderCtrl::SetSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#setsortcolumn)。  
  
##  <a name="sort"></a>CMFCListCtrl::Sort  
 对列表控件进行排序。  
  
```  
virtual void Sort(
    int iColumn,  
    BOOL bAscending = TRUE,  
    BOOL bAdd = FALSE);
```  
  
### <a name="parameters"></a>参数  
 [in] `iColumn`  
 要排序的列。  
  
 [in] `bAscending`  
 一个布尔值，指定的排序顺序。  
  
 [in] `bAdd`  
 一个布尔值，指定此方法是否将所指出的列添加`iColumn`到的列排序的列表。  
  
## <a name="see-also"></a>请参阅  
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [类](../../mfc/reference/mfc-classes.md)   
 [CListCtrl 类](../../mfc/reference/clistctrl-class.md)
