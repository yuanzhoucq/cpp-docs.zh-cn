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
ms.openlocfilehash: dc0e80e80d61104a4d8cb5f1cfd4e26a64c42249
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752742"
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
|[C支票列表框：C支票列表框](#cchecklistbox)|构造 `CCheckListBox` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C检查列表框：创建](#create)|创建 Windows 检查表框并将其附加到`CCheckListBox`对象。|
|[CCheckListBox：:D原始项目](#drawitem)|当所有者绘制列表框的可视方面发生更改时，由框架调用。|
|[CCheckListBox：启用](#enable)|启用或禁用清单框项。|
|[CCheckListBox：获取检查](#getcheck)|获取项目的状态复选框。|
|[CCheckListBox：获取检查样式](#getcheckstyle)|获取控件复选框的样式。|
|[CCheckListBox：已启用](#isenabled)|确定是否启用了项。|
|[CCheckListBox：测量项目](#measureitem)|创建具有所有者绘制样式的列表框时，由框架调用。|
|[CChecklistBox：：打开检查位置](#ongetcheckposition)|由框架调用以获取项目的位置复选框。|
|[CCheckListBox：设置检查](#setcheck)|设置项目的状态复选框。|
|[CCheckListBox：设置检查样式](#setcheckstyle)|设置控件复选框的样式。|

## <a name="remarks"></a>备注

"清单框"显示项目列表，如文件名。 列表中的每个项旁边都有一个复选框，用户可以选中或清除。

`CCheckListBox`仅适用于所有者绘制的控件，因为列表包含的比文本字符串多。 最简单的是，清单框包含文本字符串和复选框，但您根本不需要文本。 例如，您可以有一个小位图列表，每个项目旁边都有一个复选框。

要创建自己的清单框，必须从`CCheckListBox`派生您自己的类。 要派生自己的类，请为派生类编写一个构造函数，然后调用`Create`。

如果要处理列表框发送到其父项的 Windows 通知消息（通常是从[CDialog](../../mfc/reference/cdialog-class.md)派生的类），则为每个消息向父类添加消息映射条目和消息处理程序成员函数。

每个消息映射条目采用以下形式：

**打开\_**_通知_**（ID** _id_，_成员Fxn_ **）**

其中`id`指定发送通知的控件的子窗口 ID，以及`memberFxn`您为处理通知而编写的父成员函数的名称。

父函数原型如下所示：

`afx_msg void memberFxn();`

只有一个消息映射条目专门与`CCheckListBox`（但也看到[CListBox](../../mfc/reference/clistbox-class.md)的消息映射条目 ）：

- ON_CLBN_CHKCHANGE用户已更改项目的复选框的状态。

如果检查表框是默认检查表框（每个复选框左侧的默认大小复选框的字符串列表），则可以使用默认[CCheckListBox：:DrawItem](#drawitem)绘制检查表框。 否则，您必须覆盖[CListBox：比较项目](../../mfc/reference/clistbox-class.md#compareitem)功能和[CCheckListBox：:D原始项目和](#drawitem) [CCheckListBox：度量项目](#measureitem)函数。

可以从对话框模板或直接在代码中创建检查框。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CCheckListBox`

## <a name="requirements"></a>要求

**标头:** afxwin.h

## <a name="cchecklistboxcchecklistbox"></a><a name="cchecklistbox"></a>C支票列表框：C支票列表框

构造 `CCheckListBox` 对象。

```
CCheckListBox();
```

### <a name="remarks"></a>备注

分两步`CCheckListBox`构造对象。 首先定义派生自 的`CCheckListBox`类，然后`Create`调用 ，该类初始化 Windows 检查表框并将其`CCheckListBox`附加到对象。

### <a name="example"></a>示例

[!code-cpp[NVC_MFCControlLadenDialog#60](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]

## <a name="cchecklistboxcreate"></a><a name="create"></a>C检查列表框：创建

创建 Windows 检查表框并将其附加到`CCheckListBox`对象。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>参数

*dwStyle*<br/>
指定检查表框的样式。 样式必须LBS_HASSTRINGS，并且LBS_OWNERDRAWFIXED（列表中的所有项目都具有相同的高度）或LBS_OWNERDRAWVARIABLE（列表中的项目高度不同）。 此样式可以与其他[列表框样式](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)组合，但LBS_USETABSTOPS除外。

*矩形*<br/>
指定检查表框大小和位置。 可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)对象或[RECT](/windows/win32/api/windef/ns-windef-rect)结构。

*pparentwnd*<br/>
指定检查表框的父窗口（通常是`CDialog`对象）。 值不得为 NULL。

*nID*<br/>
指定检查表框的控制 ID。

### <a name="return-value"></a>返回值

如果成功，则不为 0；否则为 0。

### <a name="remarks"></a>备注

分两步`CCheckListBox`构造对象。 首先，定义派生的`CcheckListBox`类，然后调用`Create`，该类初始化 Windows 检查表框并将其附加到`CCheckListBox`。 有关示例，请参阅[CCheckListBox：CCheckListBox。](#cchecklistbox)

执行`Create`时，Windows 会将[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)WM_NCCREATE、WM_CREATE、WM_NCCALCSIZE 和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)消息发送到检查表框控件。 [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate) [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)

默认情况下，这些消息`CWnd`由基类中的[OnNcCreate、OnCreate、OnNcCalcsize](../../mfc/reference/cwnd-class.md#onnccreate)和[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成员函数处理。 [OnCreate](../../mfc/reference/cwnd-class.md#oncreate) [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize) 要扩展默认消息处理，请向派生类添加消息映射，并重写前面的消息处理程序成员函数。 例如`OnCreate`，重写以执行新类所需的初始化。

将以下[窗口样式](../../mfc/reference/styles-used-by-mfc.md#window-styles)应用于检查箱控件：

- WS_CHILD始终

- WS_VISIBLE 通常

- WS_DISABLED很少

- WS_VSCROLL 添加垂直滚动条

- WS_HSCROLL 添加水平滚动条

- WS_GROUP组控件

- WS_TABSTOP 允许选项卡到此控件

## <a name="cchecklistboxdrawitem"></a><a name="drawitem"></a>CCheckListBox：:D原始项目

当所有者绘制的检查表框的可视方面发生更改时，由框架调用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>参数

*lpDraw 项目已结*<br/>
指向[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)结构的长指针，其中包含有关所需绘图类型的信息。

### <a name="remarks"></a>备注

结构`itemAction``itemState`和`DRAWITEMSTRUCT`成员定义要执行的绘图操作。

默认情况下，此函数绘制一个默认复选框列表，该复选框列表由每个字符串列表组成，每个字符串列表左侧有一个默认大小的复选框。 复选框列表大小是在["创建](#create)"中指定的。

重写此成员函数以实现不默认的所有者绘制清单框的绘制，例如包含列表不是字符串、具有可变高项或未在左侧的复选框的检查表框。 应用程序应还原在此成员函数终止之前为*lpDrawItemStruct*中提供的显示上下文选择的所有图形设备接口 （GDI） 对象。

如果清单框项的高度不同，则清单框样式（在`Create`） 中指定必须**LBS_OWNERVARIABLE**，并且必须覆盖[度量项](#measureitem)函数。

## <a name="cchecklistboxenable"></a><a name="enable"></a>CCheckListBox：启用

调用此函数以启用或禁用检查表框项。

```cpp
void Enable(
    int nIndex,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要启用的检查表框项的索引。

*b 启用*<br/>
指定项目是启用还是禁用。

## <a name="cchecklistboxgetcheck"></a><a name="getcheck"></a>CCheckListBox：获取检查

检索指定复选框的状态。

```
int GetCheck(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
列表框中包含的复选框的零基索引。

### <a name="return-value"></a>返回值

指定复选框的状态。 下表列出了可能的值。

|“值”|说明|
|-----------|-----------------|
|BST_CHECKED|此复选框处于选中状态。|
|BST_UNCHECKED|未选中该复选框。|
|BST_INDETERMINATE|复选框状态不确定。|

## <a name="cchecklistboxgetcheckstyle"></a><a name="getcheckstyle"></a>CCheckListBox：获取检查样式

调用此函数获取清单框的样式。

```
UINT GetCheckStyle();
```

### <a name="return-value"></a>返回值

控件复选框的样式。

### <a name="remarks"></a>备注

有关可能样式的信息，请参阅[设置检查样式](#setcheckstyle)。

## <a name="cchecklistboxisenabled"></a><a name="isenabled"></a>CCheckListBox：已启用

调用此函数以确定是否启用了项。

```
BOOL IsEnabled(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
项的索引。

### <a name="return-value"></a>返回值

如果启用了项，则非零;否则 0。

## <a name="cchecklistboxmeasureitem"></a><a name="measureitem"></a>CCheckListBox：测量项目

创建具有非默认样式的检查表框时，由框架调用。

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>参数

*lp 测量项目结构*<br/>
指向[测量结构](/windows/win32/api/winuser/ns-winuser-measureitemstruct)的长指针。

### <a name="remarks"></a>备注

默认情况下，此成员函数不执行任何操作。 重写此成员函数并填写`MEASUREITEMSTRUCT`结构，以通知 Windows 检查表框项的尺寸。 如果使用[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)样式创建检查表框，则框架将针对列表框中的每个项目调用此成员函数。 否则，仅调用此成员一次。

## <a name="cchecklistboxongetcheckposition"></a><a name="ongetcheckposition"></a>CChecklistBox：：打开检查位置

框架调用此函数以获取项中复选框的位置和大小。

```
virtual CRect OnGetCheckPosition(
    CRect rectItem,
    CRect rectCheckBox);
```

### <a name="parameters"></a>参数

*rectItem*<br/>
列表项的位置和大小。

*rectCheckBox*<br/>
项目复选框的默认位置和大小。

### <a name="return-value"></a>返回值

项目的位置和大小复选框。

### <a name="remarks"></a>备注

默认实现仅返回复选框 （）`rectCheckBox`的默认位置和大小。 默认情况下，复选框在项目的左上角对齐，是标准复选框大小。 在某些情况下，您可能希望右侧的复选框，或者需要更大或更小的复选框。 在这些情况下，重写`OnGetCheckPosition`以更改物料中的复选框位置和大小。

## <a name="cchecklistboxsetcheck"></a><a name="setcheck"></a>CCheckListBox：设置检查

设置指定复选框的状态。

```cpp
void SetCheck(
    int nIndex,
    int nCheck);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
列表框中包含的复选框的零基索引。

*n检查*<br/>
指定复选框的按钮状态。 有关可能的值，请参阅备注部分。

### <a name="remarks"></a>备注

下表列出了*nCheck*参数的可能值。

|“值”|说明|
|-----------|-----------------|
|BST_CHECKED|选择指定的复选框。|
|BST_UNCHECKED|清除指定的复选框。|
|BST_INDETERMINATE|将指定的复选框状态设置为不确定。<br /><br /> 仅当复选框样式BS_AUTO3STATE或BS_3STATE时，此状态才可用。 有关详细信息，请参阅[按钮样式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。|

## <a name="cchecklistboxsetcheckstyle"></a><a name="setcheckstyle"></a>CCheckListBox：设置检查样式

调用此函数以在检查表框中设置复选框的样式。

```cpp
void SetCheckStyle(UINT nStyle);
```

### <a name="parameters"></a>参数

*nStyle*<br/>
确定检查表框中复选框的样式。

### <a name="remarks"></a>备注

有效样式包括：

- BS_CHECKBOX

- BS_AUTOCHECKBOX

- BS_AUTO3STATE

- BS_3STATE

有关这些样式的信息，请参阅[按钮样式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。

## <a name="see-also"></a>请参阅

[MFC 样品 TSTCON](../../overview/visual-cpp-samples.md)<br/>
[CListBox 类](../../mfc/reference/clistbox-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CListBox 类](../../mfc/reference/clistbox-class.md)
