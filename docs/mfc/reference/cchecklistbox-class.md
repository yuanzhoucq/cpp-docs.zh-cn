---
title: "CCheckListBox 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- CCheckListBox class
- checklist boxes
ms.assetid: 1dd78438-00e8-441c-b36f-9c4f9ac0d019
caps.latest.revision: 26
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 2cce91e3b6cb6cdf6ec2f4564fcf5090a54c917f
ms.lasthandoff: 02/24/2017

---
# <a name="cchecklistbox-class"></a>CCheckListBox 类
提供 Windows 检查表框功能。  
  
## <a name="syntax"></a>语法  
  
```  
class CCheckListBox : public CListBox  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CCheckListBox::CCheckListBox](#cchecklistbox)|构造 `CCheckListBox` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CCheckListBox::Create](#create)|创建 Windows 检查表框，并将其附加到`CCheckListBox`对象。|  
|[CCheckListBox::DrawItem](#drawitem)|由框架在自绘列表框中更改的可视方位时调用。|  
|[CCheckListBox::Enable](#enable)|启用或禁用的检查表框项。|  
|[CCheckListBox::GetCheck](#getcheck)|获取该项的复选框的状态。|  
|[CCheckListBox::GetCheckStyle](#getcheckstyle)|获取控件的复选框的样式。|  
|[CCheckListBox::IsEnabled](#isenabled)|确定是否启用一个项。|  
|[CCheckListBox::MeasureItem](#measureitem)|创建具有一个所有者绘制样式的列表框时，由框架调用。|  
|[CCheckListBox::OnGetCheckPosition](#ongetcheckposition)|由框架以获取该项的复选框的位置调用。|  
|[CCheckListBox::SetCheck](#setcheck)|设置该项的复选框的状态。|  
|[CCheckListBox::SetCheckStyle](#setcheckstyle)|设置控件的复选框的样式。|  
  
## <a name="remarks"></a>备注  
 "清单框"显示文件名等项的列表。 在列表中的每个项都有它的用户可以选中或清除旁边的复选框。  
  
 `CCheckListBox`是只能为所有者描述控件，因为该列表包含多个文本字符串。 简单地说，检查表框包含文本字符串和复选框，但不是需要根本没有文本。 例如，你可以有一个复选框，每个项旁边的小位图的列表。  
  
 若要创建您自己的检查表框，必须派生您自己的类从`CCheckListBox`。 若要派生您自己的类编写派生的类的构造函数，然后调用**创建**。  
  
 如果你想要处理 Windows 通知消息发送到其父列表框中 (通常派生自该类[CDialog](../../mfc/reference/cdialog-class.md))，将消息映射条目和消息处理程序成员函数添加到每个消息的父类。  
  
 每个消息映射条目采用以下形式︰  
  
 **ON_**Notification **(**`id`, `memberFxn`**)**  
  
 其中`id`指定发送通知的控件的子窗口 ID 和`memberFxn`留下来处理通知的父成员函数的名称。  
  
 父元素的函数原型是，如下所示︰  
  
 **afx_msg** `void` `memberFxn` **( );**  
  
 仅具有一个适用于的消息映射条目**CCheckListBox** (请参阅有关的消息映射条目，但[CListBox](../../mfc/reference/clistbox-class.md)):  
  
- **ON_CLBN_CHKCHANGE**用户已更改的状态的项的复选框。  
  
 如果您检查表框是默认清单框 （默认大小复选框左侧的每个字符串列表），则可以使用默认值[CCheckListBox::DrawItem](#drawitem)绘制清单框。 否则，您必须重写[CListBox::CompareItem](../../mfc/reference/clistbox-class.md#compareitem)函数和[CCheckListBox::DrawItem](#drawitem)和[CCheckListBox::MeasureItem](#measureitem)函数。  
  
 从对话框模板或直接在代码中，可以创建一个检查表框。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CListBox](../../mfc/reference/clistbox-class.md)  
  
 `CCheckListBox`  
  
## <a name="requirements"></a>要求  
 **标头:** afxwin.h  
  
##  <a name="cchecklistbox"></a>CCheckListBox::CCheckListBox  
 构造 `CCheckListBox` 对象。  
  
```  
CCheckListBox();
```  
  
### <a name="remarks"></a>备注  
 您构造`CCheckListBox`在两个步骤中的对象。 先定义一个类派生自`CCheckListBox`，然后调用**创建**，其中初始化 Windows 检查表框并将其附加到`CCheckListBox`对象。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCControlLadenDialog #&60;](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]  
  
##  <a name="create"></a>CCheckListBox::Create  
 创建 Windows 检查表框，并将其附加到`CCheckListBox`对象。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>参数  
 `dwStyle`  
 指定的检查表框的样式。 该样式必须是**LBS_HASSTRINGS**和任一**LBS_OWNERDRAWFIXED** （列表中的所有项都均为同一高度） 或**LBS_OWNERDRAWVARIABLE** （高度不都是列表中的项）。 此样式可以与其他组合[列表框样式](../../mfc/reference/list-box-styles.md)除**LBS_USETABSTOPS**。  
  
 `rect`  
 指定的检查表框大小和位置。 可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](../../mfc/reference/rect-structure1.md)结构。  
  
 `pParentWnd`  
 指定检查表框的父窗口 (通常`CDialog`对象)。 它不能**NULL**。  
  
 `nID`  
 指定检查列表框控件 id。  
  
### <a name="return-value"></a>返回值  
 如果成功，则不为 0；否则为 0。  
  
### <a name="remarks"></a>备注  
 您构造`CCheckListBox`在两个步骤中的对象。 首先，定义派生自的类**CcheckListBox** ，然后调用**创建**，其中初始化 Windows 检查表框并将其附加到`CCheckListBox`。 请参阅[CCheckListBox::CCheckListBox](#cchecklistbox)有关的示例。  
  
 当**创建**执行时，Windows 将发送[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)， [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)， [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)，和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)检查列表框控件的消息。  
  
 默认情况下，通过处理这些消息的消息[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)， [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)， [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)，和[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成员函数中`CWnd`基类。 若要扩展的默认消息处理，添加消息映射到派生的类和重写前面的消息处理程序成员函数。 重写`OnCreate`，例如，若要为新类执行所需的初始化。  
  
 将应用以下[窗口样式](../../mfc/reference/window-styles.md)向检查表框控件︰  
  
- **WS_CHILD**始终  
  
- **WS_VISIBLE**通常  
  
- **WS_DISABLED**很少  
  
- **WS_VSCROLL**添加垂直滚动条  
  
- **WS_HSCROLL**若要添加水平滚动条  
  
- **WS_GROUP**控件组合  
  
- **WS_TABSTOP**以允许到此控件的 tab 键次序  
  
##  <a name="drawitem"></a>CCheckListBox::DrawItem  
 由框架在所有者绘制的检查表框中更改的可视方位时调用。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpDrawItemStruct`  
 指向长指针[DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md)结构，其中包含有关所需的绘图类型的信息。  
  
### <a name="remarks"></a>备注  
 **ItemAction**和**itemState**成员`DRAWITEMSTRUCT`结构定义要执行的绘制操作。  
  
 默认情况下，此函数绘制默认复选框列表中，包含字符串每个与一个默认大小的复选框左侧的列表。 复选框列表的大小是之一中指定[创建](#create)。  
  
 重写该成员函数以实现自绘检查表框不是默认情况下，例如检查表框不是字符串的列表、 高度可变的项或不在左侧的复选框的绘制。 应用程序应还原选择用于显示上下文中提供的所有图形设备接口 (GDI) 对象`lpDrawItemStruct`之前终止该成员函数。  
  
 如果检查表框项不是高度相同，检查表框样式 (中指定**创建**) 必须是**LBS_OWNERVARIABLE**，并且您必须重写[MeasureItem](#measureitem)函数。  
  
##  <a name="enable"></a>CCheckListBox::Enable  
 调用此函数可启用或禁用的检查表框项。  
  
```  
void Enable(
    int nIndex,  
    BOOL bEnabled = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 若要启用检查表框中项的索引。  
  
 `bEnabled`  
 指定是启用还是禁用该项目。  
  
##  <a name="getcheck"></a>CCheckListBox::GetCheck  
 检索指定的复选框的状态。  
  
```  
int GetCheck(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 一个复选框，在列表框中包含的从零开始索引。  
  
### <a name="return-value"></a>返回值  
 指定的复选框的状态。 下表列出可能的值。  
  
|值|说明|  
|-----------|-----------------|  
|`BST_CHECKED`|选中复选框。|  
|`BST_UNCHECKED`|未选中该复选框。|  
|`BST_INDETERMINATE`|复选框状态却不确定。|  
  
##  <a name="getcheckstyle"></a>CCheckListBox::GetCheckStyle  
 调用此函数可获取检查表框的样式。  
  
```  
UINT GetCheckStyle();
```  
  
### <a name="return-value"></a>返回值  
 控件的复选框的样式。  
  
### <a name="remarks"></a>备注  
 可能的样式的信息，请参阅[SetCheckStyle](#setcheckstyle)。  
  
##  <a name="isenabled"></a>CCheckListBox::IsEnabled  
 调用此函数可确定项是否已启用。  
  
```  
BOOL IsEnabled(int nIndex);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 项的索引。  
  
### <a name="return-value"></a>返回值  
 如果启用项，则非零值否则为 0。  
  
##  <a name="measureitem"></a>CCheckListBox::MeasureItem  
 创建一个具有非默认样式的检查表框时，由框架调用。  
  
```  
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```  
  
### <a name="parameters"></a>参数  
 `lpMeasureItemStruct`  
 指向长指针[MEASUREITEMSTRUCT](../../mfc/reference/measureitemstruct-structure.md)结构。  
  
### <a name="remarks"></a>备注  
 默认情况下，此成员函数没有任何影响。 重写该成员函数，并填写`MEASUREITEMSTRUCT`结构以通知 Windows 检查表框项的尺寸。 如果使用创建的检查表框[LBS_OWNERDRAWVARIABLE](../../mfc/reference/list-box-styles.md)样式，框架将调用此成员函数的列表框中的每一项。 否则，只有一次调用此成员。  
  
##  <a name="ongetcheckposition"></a>CCheckListBox::OnGetCheckPosition  
 框架调用此函数可在项中获取的位置和大小的复选框。  
  
```  
virtual CRect OnGetCheckPosition(
    CRect rectItem,  
    CRect rectCheckBox);
```  
  
### <a name="parameters"></a>参数  
 *rectItem*  
 位置和大小的列表项。  
  
 `rectCheckBox`  
 默认位置和项的复选框的大小。  
  
### <a name="return-value"></a>返回值  
 位置和项的复选框的大小。  
  
### <a name="remarks"></a>备注  
 默认实现只返回默认位置和复选框的大小 ( `rectCheckBox`)。 默认情况下，复选框中项的左上角对齐，但不将标准复选框大小。 可能想在右侧，复选框或希望放大或缩小的复选框的情况。 在这些情况下，重写`OnGetCheckPosition`更改复选框的位置和大小在该项内的。  
  
##  <a name="setcheck"></a>CCheckListBox::SetCheck  
 设置指定的复选框的状态。  
  
```  
void SetCheck(
    int nIndex,  
    int nCheck);
```  
  
### <a name="parameters"></a>参数  
 `nIndex`  
 一个复选框，在列表框中包含的从零开始索引。  
  
 `nCheck`  
 指定的复选框按钮的状态。 请参阅备注部分中有关可能的值。  
  
### <a name="remarks"></a>备注  
 下表列出的可能值为`nCheck`参数。  
  
|值|描述|  
|-----------|-----------------|  
|**BST_CHECKED**|选择指定复选框。|  
|**BST_UNCHECKED**|清除指定的复选框。|  
|**BST_INDETERMINATE**|指定的复选框状态设置为不确定。<br /><br /> 此状态下才可用的复选框样式是`BS_AUTO3STATE`或`BS_3STATE`。 有关详细信息，请参阅[按钮样式](../../mfc/reference/button-styles.md)。|  
  
##  <a name="setcheckstyle"></a>CCheckListBox::SetCheckStyle  
 调用此函数可在清单中设置的复选框的样式。  
  
```  
void SetCheckStyle(UINT nStyle);
```  
  
### <a name="parameters"></a>参数  
 `nStyle`  
 确定清单中的复选框的样式。  
  
### <a name="remarks"></a>备注  
 有效样式包括︰  
  
- **BS_CHECKBOX**  
  
- **BS_AUTOCHECKBOX**  
  
- **BS_AUTO3STATE**  
  
- **BS_3STATE**  
  
 这些样式的信息，请参阅[按钮样式](../../mfc/reference/button-styles.md)。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 示例 TSTCON](../../visual-cpp-samples.md)   
 [CListBox 类](../../mfc/reference/clistbox-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CListBox 类](../../mfc/reference/clistbox-class.md)

