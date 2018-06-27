---
title: CCheckListBox 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CCheckListBox
- AFXWIN/CCheckListBox
- AFXWIN/CCheckListBox::CCheckListBox
- AFXWIN/CCheckListBox::Create
- AFXWIN/CCheckListBox::DrawItem
- AFXWIN/CCheckListBox::Enable
- AFXWIN/CCheckListBox::GetCheck
- AFXWIN/CCheckListBox::GetCheckStyle
- AFXWIN/CCheckListBox::IsEnabled
- AFXWIN/CCheckListBox::MeasureItem
- AFXWIN/CCheckListBox::OnGetCheckPosition
- AFXWIN/CCheckListBox::SetCheck
- AFXWIN/CCheckListBox::SetCheckStyle
dev_langs:
- C++
helpviewer_keywords:
- CCheckListBox [MFC], CCheckListBox
- CCheckListBox [MFC], Create
- CCheckListBox [MFC], DrawItem
- CCheckListBox [MFC], Enable
- CCheckListBox [MFC], GetCheck
- CCheckListBox [MFC], GetCheckStyle
- CCheckListBox [MFC], IsEnabled
- CCheckListBox [MFC], MeasureItem
- CCheckListBox [MFC], OnGetCheckPosition
- CCheckListBox [MFC], SetCheck
- CCheckListBox [MFC], SetCheckStyle
ms.assetid: 1dd78438-00e8-441c-b36f-9c4f9ac0d019
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 998a2124d80a03946df1cfeeb4a0223ccbf55b24
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "36956562"
---
# <a name="cchecklistbox-class"></a>CCheckListBox 类
提供 Windows 检查表框功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CCheckListBox : public CListBox  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CCheckListBox::CCheckListBox](#cchecklistbox)|构造 `CCheckListBox` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CCheckListBox::Create](#create)|创建 Windows 检查表框并将其附加到`CCheckListBox`对象。|  
|[CCheckListBox::DrawItem](#drawitem)|由框架的所有者描述列表框中更改的可视方面时调用。|  
|[CCheckListBox::Enable](#enable)|启用或禁用检查列表框项。|  
|[CCheckListBox::GetCheck](#getcheck)|获取项的复选框的状态。|  
|[CCheckListBox::GetCheckStyle](#getcheckstyle)|获取控件的复选框的样式。|  
|[CCheckListBox::IsEnabled](#isenabled)|确定是否启用一个项。|  
|[CCheckListBox::MeasureItem](#measureitem)|创建具有所有者绘制样式的列表框时，由框架调用。|  
|[CCheckListBox::OnGetCheckPosition](#ongetcheckposition)|由框架调用以获取项的复选框的位置。|  
|[CCheckListBox::SetCheck](#setcheck)|设置项的复选框的状态。|  
|[CCheckListBox::SetCheckStyle](#setcheckstyle)|设置控件的复选框的样式。|  
  
## <a name="remarks"></a>备注  
 "清单框"显示项，例如文件名的列表。 在列表中的每个项都有它的用户可以选中或清除旁的复选框。  
  
 `CCheckListBox` 是仅为所有者描述的控件，因为列表包含多个文本字符串。 简单地说，检查表框包含文本字符串和复选框，但不是需要有文本。 例如，你可以每个项旁边的复选框的小位图的列表。  
  
 若要创建你自己的检查表框，必须派生您自己的类从`CCheckListBox`。 若要派生您自己的类，编写为派生的类构造函数，然后调用`Create`。  
  
 如果你想要处理 Windows 通知消息发送到其父列表框 (通常从派生的类[CDialog](../../mfc/reference/cdialog-class.md))，将消息映射条目和消息处理程序成员函数添加到每条消息的父类。  
  
 每个消息映射条目采用以下形式：  
  
 **ON_** 通知 **(**`id`， `memberFxn` **)**  
  
 其中`id`指定发送通知的控件的子窗口 ID 和`memberFxn`是父成员函数编写以处理通知的名称。  
  
 父元素的函数原型如下所示：  
  
 **afx_msg** `void` `memberFxn` **（);**  
  
 没有专门针对有关只有一个消息映射条目`CCheckListBox`(但另请参阅的消息映射项[CListBox](../../mfc/reference/clistbox-class.md)):  
  
- **ON_CLBN_CHKCHANGE**用户已更改的状态的项的复选框。  
  
 如果你的清单框是默认检查表框 （具有每个左侧的默认大小复选框的字符串的列表），则可以使用默认值[CCheckListBox::DrawItem](#drawitem)绘制检查表框。 否则，你必须重写[CListBox::CompareItem](../../mfc/reference/clistbox-class.md#compareitem)函数和[CCheckListBox::DrawItem](#drawitem)和[CCheckListBox::MeasureItem](#measureitem)函数。  
  
 从对话框模板或直接在代码中，可以创建一个清单框。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListBox](../../mfc/reference/clistbox-class.md)  
  
 `CCheckListBox`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="cchecklistbox"></a>  CCheckListBox::CCheckListBox  
 构造 `CCheckListBox` 对象。  
  
```  
CCheckListBox();
```  
  
### <a name="remarks"></a>备注  
 构造`CCheckListBox`两个步骤中的对象。 首先定义派生自的类`CCheckListBox`，然后调用`Create`，其中初始化 Windows 检查表框并将其附加到`CCheckListBox`对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog#60](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]  
  
##  <a name="create"></a>  CCheckListBox::Create  
 创建 Windows 检查表框并将其附加到`CCheckListBox`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 *dwStyle*  
 指定的检查表框的样式。 样式必须是**LBS_HASSTRINGS**和任一**LBS_OWNERDRAWFIXED** （列表中的所有项都均为同一高度） 或**LBS_OWNERDRAWVARIABLE** （列表中的项都属于不同的高度）。 可以与其他组合此样式[列表框样式](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)除**LBS_USETABSTOPS**。  
  
 *rect*  
 指定的检查表框大小和位置。 可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](../../mfc/reference/rect-structure1.md)结构。  
  
 *pParentWnd*  
 指定检查表框的父窗口 (通常`CDialog`对象)。 它不能**NULL**。  
  
 *nID*  
 指定检查表框的控件 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 构造`CCheckListBox`两个步骤中的对象。 首先，定义派生自的类`CcheckListBox`，然后调用`Create`，其中初始化 Windows 检查表框并将其附加到`CCheckListBox`。 请参阅[CCheckListBox::CCheckListBox](#cchecklistbox)有关的示例。  
  
 当`Create`执行 Windows 发送[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)， [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)， [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)，和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)用于检查列表框控件的消息。  
  
 默认情况下，通过处理这些消息的消息[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)， [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)， [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)，和[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成员函数在`CWnd`基类。 若要扩展的默认消息处理，添加消息映射到你的派生的类和重写前面的消息处理程序成员函数。 重写`OnCreate`，例如，若要为新类执行所需的初始化。  
  
 将应用以下[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)向清单框控件：  
  
- **WS_CHILD**始终  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
- **WS_VSCROLL**添加垂直滚动条  
  
- **WS_HSCROLL**添加水平滚动条  
  
- **WS_GROUP**与组控件  
  
- **WS_TABSTOP**以允许 tab 键移到此控件  
  
##  <a name="drawitem"></a>  CCheckListBox::DrawItem  
 由框架在所有者绘制清单框中更改的可视方面时调用。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>参数  
 *lpDrawItemStruct*  
 指向的长指针[DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md)结构，其中包含有关所需的绘图的类型的信息。  
  
### <a name="remarks"></a>备注  
 **ItemAction**和**itemState**的成员`DRAWITEMSTRUCT`结构定义要执行的绘制操作。  
  
 默认情况下，此函数绘制包含的字符串每个与左侧的默认大小复选框列表的默认复选框列表。 复选框列表的大小是之一中指定[创建](#create)。  
  
 重写该成员函数以实现的不是默认值，如清单框不是字符串的列表、 高度可变的项，或不在左侧的复选框的所有者描述清单框的绘制。 应用程序应还原选择的显示上下文中提供的所有图形设备接口 (GDI) 对象*lpDrawItemStruct*之前的此成员函数终止。  
  
 清单框项不是高度相同，如果清单框样式 (中指定`Create`) 必须是**LBS_OWNERVARIABLE**，且必须重写[MeasureItem](#measureitem)函数。  
  
##  <a name="enable"></a>  CCheckListBox::Enable  
 调用此函数可启用或禁用检查列表框项。  
  
```  
void Enable(
    int nIndex,  
    BOOL bEnabled = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *nIndex*  
 要启用的清单框项的索引。  
  
 *bEnabled*  
 指定项是启用还是禁用。  
  
##  <a name="getcheck"></a>  CCheckListBox::GetCheck  
 检索指定的复选框的状态。  
  
```  
int GetCheck(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 *nIndex*  
 一个复选框，列表框中包含的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 指定的复选框的状态。 下表列出可能的值。  
  
|“值”|描述|  
|-----------|-----------------|  
|`BST_CHECKED`|选中复选框。|  
|`BST_UNCHECKED`|未选中复选框。|  
|`BST_INDETERMINATE`|复选框状态是不确定的。|  
  
##  <a name="getcheckstyle"></a>  CCheckListBox::GetCheckStyle  
 调用此函数可获取清单框的样式。  
  
```  
UINT GetCheckStyle();
```  
  
### <a name="return-value"></a>返回值  
 控件的复选框的样式。  
  
### <a name="remarks"></a>备注  
 有关可能的样式信息，请参阅[SetCheckStyle](#setcheckstyle)。  
  
##  <a name="isenabled"></a>  CCheckListBox::IsEnabled  
 调用此函数可确定是否启用了一项。  
  
```  
BOOL IsEnabled(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 *nIndex*  
 项的索引。  
  
### <a name="return-value"></a>返回值  
 如果启用了项; 则为非 0否则为 0。  
  
##  <a name="measureitem"></a>  CCheckListBox::MeasureItem  
 创建一个具有非默认样式清单框时，由框架调用。  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>参数  
 *lpMeasureItemStruct*  
 指向的长指针[MEASUREITEMSTRUCT](../../mfc/reference/measureitemstruct-structure.md)结构。  
  
### <a name="remarks"></a>备注  
 默认情况下，此成员函数没有任何影响。 重写该成员函数，并填写`MEASUREITEMSTRUCT`结构以通知 Windows 检查表框项的维数。 如果使用清单框中创建了[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式，框架会调用此成员函数为列表框中的每个项。 否则，此成员是只能调用一次。  
  
##  <a name="ongetcheckposition"></a>  CCheckListBox::OnGetCheckPosition  
 框架调用此函数可在项中获取的位置和大小的复选框。  
  
```  
virtual CRect OnGetCheckPosition(
    CRect rectItem,  
    CRect rectCheckBox);
```  
  
### <a name="parameters"></a>参数  
 *rectItem*  
 位置和大小的列表项。  
  
 *rectCheckBox*  
 默认位置和大小的项的复选框。  
  
### <a name="return-value"></a>返回值  
 位置和大小的项的复选框。  
  
### <a name="remarks"></a>备注  
 默认实现将仅返回的默认位置和大小的复选框 ( `rectCheckBox`)。 默认情况下，复选框在某一项的左上角对齐，并且是标准的复选框大小。 可能情况下你想在右侧，复选框或希望放大或缩小的复选框。 在这些情况下，重写`OnGetCheckPosition`若要更改的复选框位置和项内的大小。  
  
##  <a name="setcheck"></a>  CCheckListBox::SetCheck  
 设置指定的复选框的状态。  
  
```  
void SetCheck(
    int nIndex,  
    int nCheck);
```  
  
### <a name="parameters"></a>参数  
 *nIndex*  
 一个复选框，列表框中包含的从零开始索引。  
  
 *n 检查*  
 指定的复选框按钮状态。 请参阅备注部分有关可能的值。  
  
### <a name="remarks"></a>备注  
 下表列出可能值*n 检查*参数。  
  
|“值”|描述|  
|-----------|-----------------|  
|**BST_CHECKED**|选择指定的复选框。|  
|**BST_UNCHECKED**|清除指定的复选框。|  
|**BST_INDETERMINATE**|将指定的复选框状态设置为不确定。<br /><br /> 此状态只为时可用的复选框样式`BS_AUTO3STATE`或`BS_3STATE`。 有关详细信息，请参阅[按钮样式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。|  
  
##  <a name="setcheckstyle"></a>  CCheckListBox::SetCheckStyle  
 调用此函数可在清单中设置的复选框的样式。  
  
```  
void SetCheckStyle(UINT nStyle);
```  
  
### <a name="parameters"></a>参数  
 *nStyle*  
 确定在清单中的复选框的样式。  
  
### <a name="remarks"></a>备注  
 有效样式包括：  
  
- **BS_CHECKBOX**  
  
- **BS_AUTOCHECKBOX**  
  
- **BS_AUTO3STATE**  
  
- **BS_3STATE**  
  
 有关这些样式的信息，请参阅[按钮样式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例 TSTCON](../../visual-cpp-samples.md)   
 [CListBox 类](../../mfc/reference/clistbox-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CListBox 类](../../mfc/reference/clistbox-class.md)
