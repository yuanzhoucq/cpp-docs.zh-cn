---
title: CCheckListBox 类
ms.date: 11/04/2016
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
ms.openlocfilehash: f8c725ea30754a42ce3045f1160b7a09c4481e39
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507348"
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
|[CCheckListBox::Create](#create)|创建 Windows 清单对话框, 并将其附加到`CCheckListBox`对象。|
|[CCheckListBox::DrawItem](#drawitem)|当所有者描述列表框的视觉方面发生变化时, 由框架调用。|
|[CCheckListBox::Enable](#enable)|启用或禁用清单框项。|
|[CCheckListBox::GetCheck](#getcheck)|获取项的复选框的状态。|
|[CCheckListBox::GetCheckStyle](#getcheckstyle)|获取控件的复选框的样式。|
|[CCheckListBox::IsEnabled](#isenabled)|确定项是否已启用。|
|[CCheckListBox::MeasureItem](#measureitem)|当创建具有所有者描述样式的列表框时, 由框架调用。|
|[CCheckListBox::OnGetCheckPosition](#ongetcheckposition)|由框架调用以获取项的复选框的位置。|
|[CCheckListBox::SetCheck](#setcheck)|设置项的复选框的状态。|
|[CCheckListBox::SetCheckStyle](#setcheckstyle)|设置控件的复选框的样式。|

## <a name="remarks"></a>备注

"清单" 框显示项的列表, 如文件名。 列表中的每一项都有一个复选框, 用户可以选中或清除该复选框。

`CCheckListBox`仅适用于所有者描述的控件, 因为该列表包含多个文本字符串。 最简单的情况是, 检查表框中包含文本字符串和复选框, 但不需要有文本。 例如, 你可能有一个小位图列表, 每个项旁边有一个复选框。

若要创建自己的清单框, 您必须从派生您自己`CCheckListBox`的类。 若要派生你自己的类, 请编写派生类的构造函数, `Create`然后调用。

如果要将列表框发送的 Windows 通知消息处理到其父级 (通常是派生自[CDialog](../../mfc/reference/cdialog-class.md)的类), 请将消息映射项和消息处理程序成员函数添加到每条消息的父类。

每个消息映射项都采用以下形式:

**开启\_** _通知_ **(** _id_, _memberFxn_ **)**

其中`id` , 指定发送通知的控件的子窗口 ID, `memberFxn`是您编写的用于处理通知的父成员函数的名称。

父的函数原型如下所示:

`afx_msg void memberFxn();`

只有一条消息映射项是特别适用于`CCheckListBox`的 (但请参阅[CListBox](../../mfc/reference/clistbox-class.md)的消息映射项):

- ON_CLBN_CHKCHANGE 用户已更改项的复选框的状态。

如果您的检查列表框是默认的检查表框 (每个字符串左侧都有默认大小的复选框), 则您可以使用默认的[CCheckListBox::D rawitem](#drawitem)来绘制该清单框。 否则, 必须重写[CListBox:: CompareItem](../../mfc/reference/clistbox-class.md#compareitem)函数和[CCheckListBox::D rawitem](#drawitem)和[CCheckListBox:: MeasureItem](#measureitem)函数。

你可以从对话框模板或直接在代码中创建清单框。

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

可以通过`CCheckListBox`两个步骤构造对象。 首先定义一个派生自`CCheckListBox`的类, 然后调用`Create`, 它初始化 Windows 清单框`CCheckListBox`并将其附加到对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#60](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]

##  <a name="create"></a>CCheckListBox:: Create

创建 Windows 清单对话框, 并将其附加到`CCheckListBox`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定检查表框的样式。 样式必须为 LBS_HASSTRINGS, 或者 LBS_OWNERDRAWFIXED (列表中的所有项的高度相同) 或 LBS_OWNERDRAWVARIABLE (列表中的项的高度不同)。 此样式可以与其他[列表框样式](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)组合, 但 LBS_USETABSTOPS 除外。

*rect*<br/>
指定检查表框的大小和位置。 可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/windows/win32/api/windef/ns-windef-rect)结构。

*pParentWnd*<br/>
指定检查表框的父窗口 (通常为`CDialog`对象)。 它不能为 NULL。

*nID*<br/>
指定检查表框的控件 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

可以通过`CCheckListBox`两个步骤构造对象。 首先, 定义派生自`CcheckListBox`的类, 然后调用`Create`, 它初始化 Windows 清单框`CCheckListBox`并将其附加到。 有关示例, 请参阅[CCheckListBox:: CCheckListBox](#cchecklistbox) 。

执行`Create`时, Windows 会将[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)、 [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)、 [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)消息发送到 "清单" 框控件。

默认情况下, 将`CWnd`通过基类中的[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)、 [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)、 [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)和[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成员函数来处理这些消息。 若要扩展默认消息处理, 请将消息映射添加到派生类, 并重写前面的消息处理程序成员函数。 例如`OnCreate`, 重写, 为新类执行所需的初始化。

将以下[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)应用于检查表框控件:

- WS_CHILD

- WS_VISIBLE 通常

- WS_DISABLED 极少

- 添加垂直滚动条的 WS_VSCROLL

- WS_HSCROLL 添加水平滚动条

- WS_GROUP 到分组控件

- 允许 tab 键到此控件的 WS_TABSTOP

##  <a name="drawitem"></a>CCheckListBox::D rawItem

当所有者描述的检查表框的视觉方面发生变化时, 由框架调用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>参数

*lpDrawItemStruct*<br/>
指向[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)结构的长指针, 该指针包含所需绘图类型的相关信息。

### <a name="remarks"></a>备注

结构的`itemState`和成员定义要执行的绘图操作。 `itemAction` `DRAWITEMSTRUCT`

默认情况下, 此函数将绘制一个默认复选框列表, 其中包含一个字符串列表, 其中每个字符串的左侧都有默认大小的复选框。 复选框列表大小是在[Create](#create)中指定的大小。

重写此成员函数以实现默认情况下不是默认值的所有者描述的检查表框的绘图, 例如, 列表中不包含字符串的列表框、可变高度项或不在左侧的复选框。 应用程序应还原在此成员函数终止之前为*lpDrawItemStruct*中提供的显示上下文选择的所有图形设备接口 (GDI) 对象。

如果检查表框项的高度不同, 则检查表框样式 (在中`Create`指定) 必须是 * * LBS_OWNERVARIABLE, 必须重写[MeasureItem](#measureitem)函数。

##  <a name="enable"></a>CCheckListBox:: Enable

调用此函数可启用或禁用清单框项。

```
void Enable(
    int nIndex,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要启用的检查表框项的索引。

*bEnabled*<br/>
指定是启用还是禁用项。

##  <a name="getcheck"></a>CCheckListBox::GetCheck

检索指定复选框的状态。

```
int GetCheck(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
列表框中包含的复选框的从零开始的索引。

### <a name="return-value"></a>返回值

指定复选框的状态。 下表列出了可能的值。

|值|描述|
|-----------|-----------------|
|BST_CHECKED|复选框处于选中状态。|
|BST_UNCHECKED|不选中该复选框。|
|BST_INDETERMINATE|复选框状态为 "不确定"。|

##  <a name="getcheckstyle"></a>CCheckListBox::GetCheckStyle

调用此函数可获取清单框的样式。

```
UINT GetCheckStyle();
```

### <a name="return-value"></a>返回值

控件的复选框的样式。

### <a name="remarks"></a>备注

有关可能样式的信息, 请参阅[SetCheckStyle](#setcheckstyle)。

##  <a name="isenabled"></a>CCheckListBox:: IsEnabled

调用此函数可确定项是否已启用。

```
BOOL IsEnabled(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
项的索引。

### <a name="return-value"></a>返回值

如果启用该项, 则为非零值;否则为0。

##  <a name="measureitem"></a>CCheckListBox::MeasureItem

当创建具有非默认样式的清单框时由框架调用。

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>参数

*lpMeasureItemStruct*<br/>
指向[MEASUREITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-measureitemstruct)结构的长指针。

### <a name="remarks"></a>备注

默认情况下, 此成员函数不执行任何操作。 重写此成员函数并填充`MEASUREITEMSTRUCT`结构以通知 Windows 核对清单项的维度。 如果创建具有[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式的清单框, 框架将为列表框中的每个项调用此成员函数。 否则, 此成员只调用一次。

##  <a name="ongetcheckposition"></a>CCheckListBox::OnGetCheckPosition

框架调用此函数以获取项中的复选框的位置和大小。

```
virtual CRect OnGetCheckPosition(
    CRect rectItem,
    CRect rectCheckBox);
```

### <a name="parameters"></a>参数

*rectItem*<br/>
列表项的位置和大小。

*rectCheckBox*<br/>
项的复选框的默认位置和大小。

### <a name="return-value"></a>返回值

项的复选框的位置和大小。

### <a name="remarks"></a>备注

默认实现仅返回复选框 (`rectCheckBox`) 的默认位置和大小。 默认情况下, 复选框在项的左上角对齐, 并且是标准的复选框大小。 在某些情况下, 可能需要右侧的复选框, 或者需要更大或更小的复选框。 在这些情况下, `OnGetCheckPosition`重写将更改项内的复选框的位置和大小。

##  <a name="setcheck"></a>CCheckListBox::SetCheck

设置指定复选框的状态。

```
void SetCheck(
    int nIndex,
    int nCheck);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
列表框中包含的复选框的从零开始的索引。

*nCheck*<br/>
指定复选框的按钮状态。 有关可能的值, 请参阅备注部分。

### <a name="remarks"></a>备注

下表列出了*n*参数的可能值。

|值|描述|
|-----------|-----------------|
|BST_CHECKED|选中指定的复选框。|
|BST_UNCHECKED|清除指定的复选框。|
|BST_INDETERMINATE|将指定的复选框状态设置为 "不确定"。<br /><br /> 仅当复选框样式为 "BS_AUTO3STATE" 或 "BS_3STATE" 时, 此状态才可用。 有关详细信息, 请参阅[按钮样式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。|

##  <a name="setcheckstyle"></a>CCheckListBox::SetCheckStyle

调用此函数可设置清单框中复选框的样式。

```
void SetCheckStyle(UINT nStyle);
```

### <a name="parameters"></a>参数

*nStyle*<br/>
确定检查表框中复选框的样式。

### <a name="remarks"></a>备注

有效的样式包括:

- BS_CHECKBOX

- BS_AUTOCHECKBOX

- BS_AUTO3STATE

- BS_3STATE

有关这些样式的信息, 请参阅[按钮样式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。

## <a name="see-also"></a>请参阅

[MFC 示例 TSTCON](../../overview/visual-cpp-samples.md)<br/>
[CListBox 类](../../mfc/reference/clistbox-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[CListBox 类](../../mfc/reference/clistbox-class.md)
