---
title: CMFC 功能通信盒类
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::AddItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::DeleteItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::EnableDropDownListResize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::FindItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCount
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCurSel
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetDropDownHeight
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetIntermediateSize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItemData
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::HasEditBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::IsResizeDropDownList
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::OnSelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::RemoveAllItems
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SetDropDownHeight
helpviewer_keywords:
- CMFCRibbonComboBox [MFC], CMFCRibbonComboBox
- CMFCRibbonComboBox [MFC], AddItem
- CMFCRibbonComboBox [MFC], DeleteItem
- CMFCRibbonComboBox [MFC], EnableDropDownListResize
- CMFCRibbonComboBox [MFC], FindItem
- CMFCRibbonComboBox [MFC], GetCount
- CMFCRibbonComboBox [MFC], GetCurSel
- CMFCRibbonComboBox [MFC], GetDropDownHeight
- CMFCRibbonComboBox [MFC], GetIntermediateSize
- CMFCRibbonComboBox [MFC], GetItem
- CMFCRibbonComboBox [MFC], GetItemData
- CMFCRibbonComboBox [MFC], HasEditBox
- CMFCRibbonComboBox [MFC], IsResizeDropDownList
- CMFCRibbonComboBox [MFC], OnSelectItem
- CMFCRibbonComboBox [MFC], RemoveAllItems
- CMFCRibbonComboBox [MFC], SelectItem
- CMFCRibbonComboBox [MFC], SetDropDownHeight
ms.assetid: 9b29a6a4-cf17-4152-9b13-0bf90784b30d
ms.openlocfilehash: 5846b1c5590a756f0a0820583af3d0b159968ea2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375231"
---
# <a name="cmfcribboncombobox-class"></a>CMFC 功能通信盒类

类`CMFCRibbonComboBox`实现组合框控件，您可以将该控件添加到功能区栏、功能区面板或功能区弹出菜单中。

## <a name="syntax"></a>语法

```cpp
class CMFCRibbonComboBox : public CMFCRibbonEdit
```

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|名称|说明|
|----------|-----------------|
|[CMFC 剪彩组合盒：CMFC 剪彩组合盒](#cmfcribboncombobox)|构造 CMFC 功能组合博博盒对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFC 功能组合Box：添加项目](#additem)|将唯一项目追加到列表框。|
|[CMFC功能中心盒：:Delete项目](#deleteitem)|从列表框中删除指定的项目。|
|[CMFC 功能组合Box：：启用下拉列表重新调整大小](#enabledropdownlistresize)|指定列表框在下垂时是否可以更改大小。|
|[CMFC 功能通信包：：查找项目](#finditem)|返回列表框中与指定字符串匹配的第一项的索引。|
|[CMFC功能放大缩小字体功能 放大缩小字体功能](#getcount)|返回列表框中的项目数。|
|[CMFC功能放大缩小字体功能 放大缩小字体功能](#getcursel)|在列表框中获取当前选定项的索引。|
|[CMFC 功能通信框：：获取下降高度](#getdropdownheight)|下下列表框时获取列表框的高度。|
|[CMFC 功能组合Box：获取中间尺寸](#getintermediatesize)|返回在中间模式下显示的组合框的大小。|
|[CMFC 功能通信包：获取项目](#getitem)|返回与列表框中指定索引处的项关联的字符串。|
|[CMFC 功能通信包：获取项目数据](#getitemdata)|返回与列表框中指定索引处的项关联的数据。|
|[CMFC功能组合框：：已编辑盒](#haseditbox)|指示控件是否包含编辑框。|
|[CMFC 功能通信框：：重新调整下拉列表](#isresizedropdownlist)|指示列表框是否可以调整大小。|
|[CMFC 功能组合框：：在选择项目上](#onselectitem)|当用户在列表框中选择项时，由框架调用。|
|[CMFC 功能组合框：：删除所有项目](#removeallitems)|从列表框中删除所有项目并清除编辑框。|
|[CMFC 功能组合框：：选择项目](#selectitem)|在列表框中选择项目。|
|[CMFC 功能组合Box：：设置下拉高度](#setdropdownheight)|下下列表框时设置其高度。|

## <a name="remarks"></a>备注

功能区组合框由列表框与用户可以编辑的静态标签或标签组合而成。 创建功能区组合框时，必须指定所需的类型。

## <a name="example"></a>示例

下面的示例演示如何构造`CMFCRibbonComboBox`类的对象、将项添加到组合框中、在组合框中选择项以及向面板添加组合框。

[!code-cpp[NVC_MFC_RibbonApp#11](../../mfc/reference/codesnippet/cpp/cmfcribboncombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

## <a name="requirements"></a>要求

**标题：** afxribboncombox.h

## <a name="cmfcribboncomboboxadditem"></a><a name="additem"></a>CMFC 功能组合Box：添加项目

将唯一项目追加到列表框。

```cpp
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>参数

*lpszItem*<br/>
[在]要添加的项的字符串。

*dwData*<br/>
[在]与要添加的项关联的数据。

### <a name="return-value"></a>返回值

附加项的零基索引。

## <a name="cmfcribboncomboboxcmfcribboncombobox"></a><a name="cmfcribboncombobox"></a>CMFC 剪彩组合盒：CMFC 剪彩组合盒

构造 `CMFCRibbonComboBox` 对象。

```cpp
public:
CMFCRibbonComboBox(
    UINT nID,
    BOOL bHasEditBox=TRUE,
    Int nWidth=-1,
    LPCTSTR lpszLabel=NULL,
    Int nImage=-1);

protected:
CMFCRibbonComboBox();
```

### <a name="parameters"></a>参数

*nID*<br/>
[在]组合框的 ID。

*bHasEditBox*<br/>
[在]如果希望在控件中使用编辑框，则为 TRUE;否则。

*n 宽度*<br/>
[在]组合框的宽度（以像素为单位）;或 -1 表示默认宽度。

*lpszLabel*<br/>
[在]组合框的显示标签。

*n图像*<br/>
[在]组合框的小图像索引。

### <a name="remarks"></a>备注

默认宽度为 108 像素。

## <a name="cmfcribboncomboboxdeleteitem"></a><a name="deleteitem"></a>CMFC功能中心盒：:Delete项目

从列表框中删除指定的项目。

```cpp
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);

BOOL DeleteItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>参数

*iIndex*<br/>
[在]要删除的项的零基索引。

*dwData*<br/>
[在]与要删除的项关联的数据。

*lpszText*<br/>
[在]要删除的项的字符串。 如果有多个具有相同字符串的项，则删除第一个项。

### <a name="return-value"></a>返回值

如果指定的项已被删除，则为 TRUE;如果指定项目已被删除，则为 TRUE。否则，FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcribboncomboboxenabledropdownlistresize"></a><a name="enabledropdownlistresize"></a>CMFC 功能组合Box：：启用下拉列表重新调整大小

指定列表框在下垂时是否可以更改大小。

```cpp
void EnableDropDownListResize(BOOL bEnable=FALSE);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
[在]TRUE 以启用大小调整;FALSE 以禁用调整大小。

### <a name="remarks"></a>备注

启用调整大小后，列表框将更改大小以适合其显示的项目。

## <a name="cmfcribboncomboboxfinditem"></a><a name="finditem"></a>CMFC 功能通信包：：查找项目

返回列表框中与指定字符串匹配的第一项的索引。

```cpp
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>参数

*lpszText*<br/>
[在]列表框中项的字符串。

### <a name="return-value"></a>返回值

项的零基索引;或 -1，如果找不到该项目。

### <a name="remarks"></a>备注

## <a name="cmfcribboncomboboxgetcount"></a><a name="getcount"></a>CMFC功能放大缩小字体功能 放大缩小字体功能

返回列表框中的项目数。

```cpp
INT_PTR GetCount() const;
```

### <a name="return-value"></a>返回值

如果列表框不包含任何项，则列表框中的项目数为 0。

### <a name="remarks"></a>备注

## <a name="cmfcribboncomboboxgetcursel"></a><a name="getcursel"></a>CMFC功能放大缩小字体功能 放大缩小字体功能

在列表框中获取当前选定项的索引。

```cpp
int GetCurSel() const;
```

### <a name="return-value"></a>返回值

列表框中当前选定项的零基索引;或 -1，如果未选择项目。

## <a name="cmfcribboncomboboxgetdropdownheight"></a><a name="getdropdownheight"></a>CMFC 功能通信框：：获取下降高度

下下列表框时获取列表框的高度。

```cpp
int GetDropDownHeight();
```

### <a name="return-value"></a>返回值

列表框的高度（以像素为单位）。

### <a name="remarks"></a>备注

## <a name="cmfcribboncomboboxgetintermediatesize"></a><a name="getintermediatesize"></a>CMFC 功能组合Box：获取中间尺寸

返回在中间模式下显示的组合框的大小。

```cpp
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]指向组合框的设备上下文。

### <a name="return-value"></a>返回值

组合框的大小。

### <a name="remarks"></a>备注

返回的大小基于组合框显示小图像时的大小。

## <a name="cmfcribboncomboboxgetitem"></a><a name="getitem"></a>CMFC 功能通信包：获取项目

返回与列表框中指定索引处的项关联的字符串。

```cpp
LPCTSTR GetItem(int iIndex) const;
```

### <a name="parameters"></a>参数

*iIndex*<br/>
[在]列表框中项的零基索引。

### <a name="return-value"></a>返回值

指向与项关联的字符串的指针;否则，如果索引参数无效，或者索引参数为 -1，并且组合框中未选择任何项，则 NULL。

### <a name="remarks"></a>备注

## <a name="cmfcribboncomboboxgetitemdata"></a><a name="getitemdata"></a>CMFC 功能通信包：获取项目数据

返回与列表框中指定索引处的项关联的数据。

```cpp
DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>参数

*iIndex*<br/>
[在]列表框中项的零基索引。

### <a name="return-value"></a>返回值

与项关联的数据;如果项不存在，或者索引参数为 -1，并且列表框中没有选定项，则为 0。

## <a name="cmfcribboncomboboxhaseditbox"></a><a name="haseditbox"></a>CMFC功能组合框：：已编辑盒

指示控件是否包含编辑框。

```cpp
BOOL HasEditBox() const;
```

### <a name="return-value"></a>返回值

如果控件包含编辑框，则为 TRUE;如果控件包含编辑框。"否则，FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcribboncomboboxisresizedropdownlist"></a><a name="isresizedropdownlist"></a>CMFC 功能通信框：：重新调整下拉列表

指示列表框是否可以调整大小。

```cpp
BOOL IsResizeDropDownList() const;
```

### <a name="return-value"></a>返回值

如果列表框可以调整大小，则为 TRUE;否则 FALSE。 [CMFC 功能组合Box：：启用下拉列表重新调整大小](#enabledropdownlistresize)

### <a name="remarks"></a>备注

您可以使用[CMFC 功能区ComboBox：：启用下拉列表重新调整大小](#enabledropdownlistresize)的方法启用列表框调整大小。

## <a name="cmfcribboncomboboxonselectitem"></a><a name="onselectitem"></a>CMFC 功能组合框：：在选择项目上

当用户在列表框中选择项时，由框架调用。

```cpp
virtual void OnSelectItem(int nItem);
```

### <a name="parameters"></a>参数

*nItem*<br/>
[在]所选项的索引。

### <a name="remarks"></a>备注

如果要处理用户输入选择，则重写此方法。

## <a name="cmfcribboncomboboxremoveallitems"></a><a name="removeallitems"></a>CMFC 功能组合框：：删除所有项目

从列表框中删除所有项目并清除编辑框。

```cpp
void RemoveAllItems();
```

### <a name="remarks"></a>备注

## <a name="cmfcribboncomboboxselectitem"></a><a name="selectitem"></a>CMFC 功能组合框：：选择项目

在列表框中选择项目。

```cpp
BOOL SelectItem(int iIndex);
BOOL SelectItem(DWORD_PTR dwData);

BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>参数

*iIndex*<br/>
[在]列表框中项的零基索引。

*dwData*<br/>
[在]与列表框中的项目关联的数据。

*lpszText*<br/>
[在]列表框中项的字符串。

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfcribboncomboboxsetdropdownheight"></a><a name="setdropdownheight"></a>CMFC 功能组合Box：：设置下拉高度

下下列表框时设置其高度。

```cpp
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>参数

*nHeight*<br/>
[在]列表框的高度（以像素为单位）。

### <a name="remarks"></a>备注

默认高度为 150 像素。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonEdit 类](../../mfc/reference/cmfcribbonedit-class.md)
