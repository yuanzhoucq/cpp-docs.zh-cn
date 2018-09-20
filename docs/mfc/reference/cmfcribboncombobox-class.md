---
title: CMFCRibbonComboBox 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2681d5f54211ac2097dcae410ba69743af4b4690
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446142"
---
# <a name="cmfcribboncombobox-class"></a>CMFCRibbonComboBox 类

`CMFCRibbonComboBox`类实现可添加到功能区栏、 功能区面板或功能区弹出菜单的组合框控件。

## <a name="syntax"></a>语法

```
class CMFCRibbonComboBox : public CMFCRibbonEdit
```

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|name|描述|
|----------|-----------------|
|[CMFCRibbonComboBox::CMFCRibbonComboBox](#cmfcribboncombobox)|构造一个 CMFCRibbonComboBox 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCRibbonComboBox::AddItem](#additem)|将唯一的项追加到列表框。|
|[CMFCRibbonComboBox::DeleteItem](#deleteitem)|从列表框中删除指定的项。|
|[CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)|指定时它会下拉列表框是否可以更改大小。|
|[CMFCRibbonComboBox::FindItem](#finditem)|返回与指定的字符串匹配在列表框中的第一项的索引。|
|[CMFCRibbonComboBox::GetCount](#getcount)|在列表框中返回的项数。|
|[CMFCRibbonComboBox::GetCurSel](#getcursel)|获取列表框中当前选定项的索引。|
|[CMFCRibbonComboBox::GetDropDownHeight](#getdropdownheight)|列表框删除时，请获取列表框的高度。|
|[CMFCRibbonComboBox::GetIntermediateSize](#getintermediatesize)|返回在中间的模式下显示的组合框的大小。|
|[CMFCRibbonComboBox::GetItem](#getitem)|返回与列表框中指定索引处的项关联的字符串。|
|[CMFCRibbonComboBox::GetItemData](#getitemdata)|返回与列表框中指定索引处的项关联的数据。|
|[CMFCRibbonComboBox::HasEditBox](#haseditbox)|指示控件是否包含一个编辑框。|
|[CMFCRibbonComboBox::IsResizeDropDownList](#isresizedropdownlist)|指示可以调整大小的列表框。|
|[CMFCRibbonComboBox::OnSelectItem](#onselectitem)|当用户选择某个项的列表框中，由框架调用。|
|[CMFCRibbonComboBox::RemoveAllItems](#removeallitems)|从列表框中删除所有项，并清除编辑框。|
|[CMFCRibbonComboBox::SelectItem](#selectitem)|在列表框中选择一项。|
|[CMFCRibbonComboBox::SetDropDownHeight](#setdropdownheight)|向下拖放，请设置列表框的高度。|

## <a name="remarks"></a>备注

功能区组合框包含一个列表框，与静态标签或用户可以编辑的标签结合使用。 必须指定时创建功能区组合框中，你需要的类型。

## <a name="example"></a>示例

下面的示例演示如何构造的对象`CMFCRibbonComboBox`类，将项添加到组合框、 组合框中选择一个项并将组合框添加到面板。

[!code-cpp[NVC_MFC_RibbonApp#11](../../mfc/reference/codesnippet/cpp/cmfcribboncombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

## <a name="requirements"></a>要求

**标头：** afxribboncombobox.h

##  <a name="additem"></a>  CMFCRibbonComboBox::AddItem

将唯一的项追加到列表框。

```
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>参数

*lpszItem*<br/>
[in]要添加的项的字符串。

*dwData*<br/>
[in]与要添加的项关联的数据。

### <a name="return-value"></a>返回值

追加的项的从零开始索引。

##  <a name="cmfcribboncombobox"></a>  CMFCRibbonComboBox::CMFCRibbonComboBox

构造 `CMFCRibbonComboBox` 对象。

```
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
[in]组合框的 ID。

*bHasEditBox*<br/>
[in]如果你想在控件; 内的编辑框，则返回 TRUEFALSE 否则为。

*nWidth*<br/>
[in]以像素为单位; 组合框的宽度或-1 表示默认宽度。

*lpszLabel*<br/>
[in]组合框显示标签。

*nImage*<br/>
[in]组合框的小图像索引。

### <a name="remarks"></a>备注

默认宽度为 108 像素。

##  <a name="deleteitem"></a>  CMFCRibbonComboBox::DeleteItem

从列表框中删除指定的项。

```
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);

BOOL DeleteItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>参数

*iIndex*<br/>
[in]要删除的项的从零开始的索引。

*dwData*<br/>
[in]与要删除的项关联的数据。

*lpszText*<br/>
[in]要删除的项的字符串。 如果有多个具有相同的字符串项，则删除的第一项。

### <a name="return-value"></a>返回值

如果已删除指定的项，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="enabledropdownlistresize"></a>  CMFCRibbonComboBox::EnableDropDownListResize

指定时它会下拉列表框是否可以更改大小。

```
void EnableDropDownListResize(BOOL bEnable=FALSE);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
[in]为 true，则启用调整大小;如果为 FALSE 禁用重设大小。

### <a name="remarks"></a>备注

启用重设大小后，列表框将更改大小以适合其显示的项。

##  <a name="finditem"></a>  CMFCRibbonComboBox::FindItem

返回与指定的字符串匹配在列表框中的第一项的索引。

```
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>参数

*lpszText*<br/>
[in]列表框中的项的字符串。

### <a name="return-value"></a>返回值

项的从零开始的索引或如果未找到该项，则为-1。

### <a name="remarks"></a>备注

##  <a name="getcount"></a>  CMFCRibbonComboBox::GetCount

在列表框中返回的项数。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>返回值

在列表框中或如果在列表框不包含任何项，则为 0 的项目数。

### <a name="remarks"></a>备注

##  <a name="getcursel"></a>  CMFCRibbonComboBox::GetCurSel

获取列表框中当前选定项的索引。

```
int GetCurSel() const;
```

### <a name="return-value"></a>返回值

在列表框中; 当前选定项的从零开始的索引或如果未不选择任何项为-1。

##  <a name="getdropdownheight"></a>  CMFCRibbonComboBox::GetDropDownHeight

列表框删除时，请获取列表框的高度。

```
int GetDropDownHeight();
```

### <a name="return-value"></a>返回值

以像素为单位，列表框的高度。

### <a name="remarks"></a>备注

##  <a name="getintermediatesize"></a>  CMFCRibbonComboBox::GetIntermediateSize

返回在中间的模式下显示的组合框的大小。

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[in]组合框的设备上下文的指针。

### <a name="return-value"></a>返回值

组合框的大小。

### <a name="remarks"></a>备注

显示小图像时，返回的大小取决于组合框的大小。

##  <a name="getitem"></a>  CMFCRibbonComboBox::GetItem

返回与列表框中指定索引处的项关联的字符串。

```
LPCTSTR GetItem(int iIndex) const;
```

### <a name="parameters"></a>参数

*iIndex*<br/>
[in]列表框中的项的从零开始的索引。

### <a name="return-value"></a>返回值

指向与项; 关联的字符串的指针如果索引参数无效，或者如果索引参数为-1，并且没有组合框中选定项，否则为 NULL。

### <a name="remarks"></a>备注

##  <a name="getitemdata"></a>  CMFCRibbonComboBox::GetItemData

返回与列表框中指定索引处的项关联的数据。

```
DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>参数

*iIndex*<br/>
[in]列表框中的项的从零开始的索引。

### <a name="return-value"></a>返回值

与项关联的数据0 或如果该项不存在，或者索引参数为-1，在列表框中不存在选定的项。

##  <a name="haseditbox"></a>  CMFCRibbonComboBox::HasEditBox

指示控件是否包含一个编辑框。

```
BOOL HasEditBox() const;
```

### <a name="return-value"></a>返回值

如果控件包含一个编辑框中; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="isresizedropdownlist"></a>  CMFCRibbonComboBox::IsResizeDropDownList

指示可以调整大小的列表框。

```
BOOL IsResizeDropDownList() const;
```

### <a name="return-value"></a>返回值

如果可以调整大小的列表框; 则为 TRUE否则为 FALSE。 [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)

### <a name="remarks"></a>备注

可以让使用列表框大小调整[CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)方法。

##  <a name="onselectitem"></a>  CMFCRibbonComboBox::OnSelectItem

当用户选择某个项的列表框中，由框架调用。

```
virtual void OnSelectItem(int nItem);
```

### <a name="parameters"></a>参数

*nItem*<br/>
[in]选定的项的索引。

### <a name="remarks"></a>备注

如果你想要处理用户输入的选择重写此方法。

##  <a name="removeallitems"></a>  CMFCRibbonComboBox::RemoveAllItems

从列表框中删除所有项，并清除编辑框。

```
void RemoveAllItems();
```

### <a name="remarks"></a>备注

##  <a name="selectitem"></a>  CMFCRibbonComboBox::SelectItem

在列表框中选择一项。

```
BOOL SelectItem(int iIndex);
BOOL SelectItem(DWORD_PTR dwData);

BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>参数

*iIndex*<br/>
[in]列表框中的项的从零开始的索引。

*dwData*<br/>
[in]与列表框中的项关联的数据。

*lpszText*<br/>
[in]列表框中的项的字符串。

### <a name="return-value"></a>返回值

如果该方法成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="setdropdownheight"></a>  CMFCRibbonComboBox::SetDropDownHeight

向下拖放，请设置列表框的高度。

```
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>参数

*nHeight*<br/>
[in]以像素为单位，列表框的高度。

### <a name="remarks"></a>备注

默认高度为 150 像素。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonEdit 类](../../mfc/reference/cmfcribbonedit-class.md)
