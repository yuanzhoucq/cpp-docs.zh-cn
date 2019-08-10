---
title: CMFCToolBarComboBoxButton 类
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddSortedItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::Compare
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CreateEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::DeleteItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::FindItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetByCmd
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetComboBox
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCount
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCountAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSel
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSelAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetEditCtrl
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemData
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataPtrAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetText
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetTextAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsFlatMode
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::RemoveAllItems
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetDropDownHeight
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetFlatMode
helpviewer_keywords:
- CMFCToolBarComboBoxButton [MFC], CMFCToolBarComboBoxButton
- CMFCToolBarComboBoxButton [MFC], AddItem
- CMFCToolBarComboBoxButton [MFC], AddSortedItem
- CMFCToolBarComboBoxButton [MFC], Compare
- CMFCToolBarComboBoxButton [MFC], CreateEdit
- CMFCToolBarComboBoxButton [MFC], DeleteItem
- CMFCToolBarComboBoxButton [MFC], FindItem
- CMFCToolBarComboBoxButton [MFC], GetByCmd
- CMFCToolBarComboBoxButton [MFC], GetComboBox
- CMFCToolBarComboBoxButton [MFC], GetCount
- CMFCToolBarComboBoxButton [MFC], GetCountAll
- CMFCToolBarComboBoxButton [MFC], GetCurSel
- CMFCToolBarComboBoxButton [MFC], GetCurSelAll
- CMFCToolBarComboBoxButton [MFC], GetEditCtrl
- CMFCToolBarComboBoxButton [MFC], GetItem
- CMFCToolBarComboBoxButton [MFC], GetItemAll
- CMFCToolBarComboBoxButton [MFC], GetItemData
- CMFCToolBarComboBoxButton [MFC], GetItemDataAll
- CMFCToolBarComboBoxButton [MFC], GetItemDataPtrAll
- CMFCToolBarComboBoxButton [MFC], GetText
- CMFCToolBarComboBoxButton [MFC], GetTextAll
- CMFCToolBarComboBoxButton [MFC], IsCenterVert
- CMFCToolBarComboBoxButton [MFC], IsFlatMode
- CMFCToolBarComboBoxButton [MFC], RemoveAllItems
- CMFCToolBarComboBoxButton [MFC], SelectItem
- CMFCToolBarComboBoxButton [MFC], SelectItemAll
- CMFCToolBarComboBoxButton [MFC], SetCenterVert
- CMFCToolBarComboBoxButton [MFC], SetDropDownHeight
- CMFCToolBarComboBoxButton [MFC], SetFlatMode
ms.assetid: 32fa39f7-8e4e-4f0a-a31d-7b540d969a6c
ms.openlocfilehash: 639a5f98ff4780bd26388796039e85b812621b36
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915972"
---
# <a name="cmfctoolbarcomboboxbutton-class"></a>CMFCToolBarComboBoxButton 类

包含组合框控件 ( [CComboBox 类](../../mfc/reference/ccombobox-class.md)) 的工具栏按钮。

## <a name="syntax"></a>语法

```
class CMFCToolBarComboBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton](#cmfctoolbarcomboboxbutton)|构造一个 `CMFCToolBarComboBoxButton`。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCToolBarComboBoxButton::AddItem](#additem)|向组合框列表的末尾添加一个项。|
|[CMFCToolBarComboBoxButton::AddSortedItem](#addsorteditem)|向组合框列表中添加一个项。 列表中项的顺序由`Compare`指定。|
|[CMFCToolBarComboBoxButton::Compare](#compare)|比较两个项。 调用以对`AddSortedItems`添加到组合框列表中的项进行排序。|
|[CMFCToolBarComboBoxButton::CreateEdit](#createedit)|为组合框按钮创建一个新的编辑控件。|
|[CMFCToolBarComboBoxButton::DeleteItem](#deleteitem)|删除组合框列表中的项。|
|[CMFCToolBarComboBoxButton::FindItem](#finditem)|返回包含指定字符串的项的索引。|
|[CMFCToolBarComboBoxButton::GetByCmd](#getbycmd)|使用指定的命令 ID 返回指向组合框按钮的指针。|
|[CMFCToolBarComboBoxButton::GetComboBox](#getcombobox)|返回一个指针, 该指针指向嵌入在组合框按钮中的组合框控件。|
|[CMFCToolBarComboBoxButton::GetCount](#getcount)|返回组合框列表中的项数。|
|[CMFCToolBarComboBoxButton::GetCountAll](#getcountall)|查找具有指定命令 ID 的组合框按钮。 返回该按钮的组合框列表中的项数。|
|[CMFCToolBarComboBoxButton::GetCurSel](#getcursel)|返回组合框列表中选定项的索引。|
|[CMFCToolBarComboBoxButton::GetCurSelAll](#getcurselall)|查找具有指定命令 ID 的组合框按钮, 并返回该按钮的组合框列表中选定项的索引。|
|[CMFCToolBarComboBoxButton::GetEditCtrl](#geteditctrl)|返回一个指针, 该指针指向嵌入在组合框按钮中的编辑控件。|
|[CMFCToolBarComboBoxButton::GetItem](#getitem)|返回与组合框列表中的指定索引关联的字符串。|
|[CMFCToolBarComboBoxButton::GetItemAll](#getitemall)|查找具有指定命令 ID 的组合框按钮, 并返回与该按钮组合框列表中的索引关联的字符串。|
|[CMFCToolBarComboBoxButton::GetItemData](#getitemdata)|返回与组合框列表中的指定索引相关联的32位值。|
|[CMFCToolBarComboBoxButton::GetItemDataAll](#getitemdataall)|查找具有指定命令 ID 的组合框按钮, 并返回与该按钮组合框列表中的索引关联的32位值。|
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](#getitemdataptrall)|查找具有指定命令 ID 的组合框按钮。 检索与该按钮的组合框列表中的索引关联的32位值, 并以指针形式返回32位值。|
|[CMFCToolBarComboBoxButton::GetText](#gettext)|返回组合框编辑控件中的文本。|
|[CMFCToolBarComboBoxButton::GetTextAll](#gettextall)|查找具有指定命令 ID 的组合框按钮, 并返回该按钮的编辑控件中的文本。|
|[CMFCToolBarComboBoxButton::IsCenterVert](#iscentervert)|确定应用程序中的组合框按钮是否居中或与工具栏的顶部对齐。|
|[CMFCToolBarComboBoxButton::IsFlatMode](#isflatmode)|确定应用程序中的组合框按钮是否具有平面外观。|
|[CMFCToolBarComboBoxButton::RemoveAllItems](#removeallitems)|从列表框中移除所有项, 并在组合框中编辑控件。|
|[CMFCToolBarComboBoxButton::SelectItem](#selectitem)|根据索引、32位值或字符串选择组合框中的项, 并通知组合框控件有关所选内容的信息。|
|[CMFCToolBarComboBoxButton::SelectItemAll](#selectitemall)|查找具有指定命令 ID 的组合框按钮。 调用`SelectItem`以根据其字符串、索引或32位值在该按钮的组合框中选择一项。|
|[CMFCToolBarComboBoxButton::SetCenterVert](#setcentervert)|指定应用程序中的组合框按钮是垂直居中还是与工具栏的顶部对齐。|
|[CMFCToolBarComboBoxButton::SetDropDownHeight](#setdropdownheight)|设置下拉列表框的高度。|
|[CMFCToolBarComboBoxButton::SetFlatMode](#setflatmode)|指定应用程序中的组合框按钮是否具有平面外观。|

## <a name="remarks"></a>备注

若要将组合框按钮添加到工具栏, 请执行以下步骤:

1. 在父级工具栏资源中保留该按钮的虚拟资源 ID。

2. `CMFCToolBarComboBoxButton`构造对象。

3. 在处理 AFX_WM_RESETTOOLBAR 消息的消息处理程序中, 使用[CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)将虚拟按钮替换为新组合框按钮。

有关详细信息，请参见[演练：将控件放置在](../../mfc/walkthrough-putting-controls-on-toolbars.md)工具栏上。 有关组合框工具栏按钮的示例, 请参阅示例项目 VisualStudioDemo。

## <a name="example"></a>示例

下面的示例演示了如何使用 `CMFCToolBarComboBoxButton` 类中的各种方法。 该示例演示如何启用编辑框和组合框, 设置应用程序中组合框按钮的垂直位置, 在下拉列表框时设置列表框的高度, 设置应用程序中组合框按钮的平面样式外观, 并设置组合框按钮的编辑框中的文本。 此代码片段是[Visual Studio 演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

## <a name="requirements"></a>要求

**标头:** afxtoolbarcomboboxbutton

##  <a name="additem"></a>CMFCToolBarComboBoxButton:: AddItem

将唯一项追加到列表框。

```
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>参数

*lpszItem*<br/>
中要添加到列表框中的项的文本。

*dwData*<br/>
中与要添加到列表框中的项关联的数据。

### <a name="return-value"></a>返回值

列表框中最后一项的索引。

### <a name="remarks"></a>备注

当对列表框样式进行排序时, 请不要使用此方法。

如果项文本已在列表框中, 则新数据将与现有项存储在一起。 项目的搜索区分大小写。

##  <a name="addsorteditem"></a>CMFCToolBarComboBoxButton::AddSortedItem

按[Compare](#compare)方法定义的顺序向列表框中添加一个项。

```
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>参数

*lpszItem*<br/>
中要添加到列表框中的项的文本。

*dwData*<br/>
中与要添加到列表框中的项关联的数据。

### <a name="return-value"></a>返回值

已添加到列表框中的项的索引。

### <a name="remarks"></a>备注

使用此函数可以按特定顺序向列表框中添加项。

##  <a name="canbestretched"></a>CMFCToolBarComboBoxButton::CanBeStretched

指示组合框按钮大小是否可以更改。

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>返回值

返回 TRUE。

##  <a name="cmfctoolbarcomboboxbutton"></a>CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton

构造[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)对象。

```
CMFCToolBarComboBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=CBS_DROPDOWNLIST,
    int iWidth=0);
```

### <a name="parameters"></a>参数

*uiID*<br/>
中新按钮的命令 ID。

*iImage*<br/>
中与 "新建" 按钮关联的图像的图像索引。

*dwStyle*<br/>
中新按钮的样式。

*iWidth*<br/>
中新按钮的宽度 (以像素为单位)。

### <a name="remarks"></a>备注

默认宽度为150像素。

有关工具栏按钮样式的列表, 请参阅[Toolbar 控件样式](../../mfc/reference/toolbar-control-styles.md)

##  <a name="cleardata"></a>CMFCToolBarComboBoxButton::ClearData

删除用户定义数据。

```
virtual void ClearData();
```

### <a name="remarks"></a>备注

默认情况下, 此方法不执行任何操作。 如果要删除任何用户定义的数据, 请在派生类中重写此方法。

##  <a name="compare"></a>  CMFCToolBarComboBoxButton::Compare

比较两个字符串。

```
virtual int Compare(
    LPCTSTR lpszItem1,
    LPCTSTR lpszItem2);
```

### <a name="parameters"></a>参数

*lpszItem1*<br/>
中要比较的第一个字符串。

*lpszItem2*<br/>
中要比较的第二个字符串。

### <a name="return-value"></a>返回值

一个值, 该值指示字符串之间区分大小写的字典关系。 下表列出了可能的值:

|值|描述|
|-----------|-----------------|
|\<0|第一个字符串小于第二个字符串。|
|0|第一个字符串等于第二个字符串。|
|>0|第一个字符串大于第二个字符串。|

### <a name="remarks"></a>备注

重写此方法可以更改列表框中项的排序方式。

比较区分大小写。

仅从[AddSortedItem](#addsorteditem)方法调用此方法。

##  <a name="copyfrom"></a>CMFCToolBarComboBoxButton:: CopyFrom

将指定`CMFCToolBarComboBoxButton`的状态复制到当前对象。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>参数

*src*<br/>
中源`CMFCToolBarComboBoxButton`对象。

##  <a name="createcombo"></a>  CMFCToolBarComboBoxButton::CreateCombo

为组合框按钮创建一个新组合框。

```
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>参数

*pWndParent*<br/>
中指向按钮的父窗口的指针。

*rect*<br/>
中组合框的边框。

### <a name="return-value"></a>返回值

如果方法成功, 则为指向新组合框的指针;否则为 NULL。

##  <a name="createedit"></a>CMFCToolBarComboBoxButton::CreateEdit

为组合框按钮创建一个新的编辑框。

```
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>参数

*pWndParent*<br/>
中指向按钮的父窗口的指针。

*rect*<br/>
中新编辑框的边框。

*dwEditStyle*<br/>
中新编辑框的控件样式。

### <a name="return-value"></a>返回值

如果方法成功, 则为指向新编辑框的指针;否则为 NULL。

### <a name="remarks"></a>备注

框架在为组合框按钮创建新的编辑框时调用此方法。 重写此方法以更改创建[CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)的方式。

##  <a name="deleteitem"></a>CMFCToolBarComboBoxButton::D eleteItem

从列表框中删除指定项。

```
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);
BOOL DeleteItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>参数

*iIndex*<br/>
中要删除的项的从零开始的索引。

*dwData*<br/>
中与要删除的项关联的数据。

*lpszText*<br/>
中要删除的项的文本。 如果有多个项目具有相同的文本, 则将删除第一项。

### <a name="return-value"></a>返回值

如果该项已定位并成功删除, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="duplicatedata"></a>  CMFCToolBarComboBoxButton::DuplicateData

复制用户定义数据。

```
virtual void DuplicateData();
```

### <a name="remarks"></a>备注

默认情况下, 此方法不执行任何操作。 如果要复制任何用户定义的数据, 请在派生类中重写此方法。

##  <a name="enablewindow"></a>CMFCToolBarComboBoxButton::EnableWindow

启用或禁用编辑框和组合框。

```
virtual void EnableWindow(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
中若要启用编辑框和组合框, 则为 TRUE;若要禁用编辑框和组合框, 则为 FALSE。

### <a name="remarks"></a>备注

禁用后, 控件将无法变为活动状态, 因此无法接受用户输入。

##  <a name="exporttomenubutton"></a>CMFCToolBarComboBoxButton::ExportToMenuButton

使用组合框按钮命令 ID 将字符串从应用程序字符串表复制到指定的菜单。

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>参数

*menuButton*<br/>
弄对菜单按钮的引用。

### <a name="return-value"></a>返回值

始终为 TRUE。

##  <a name="finditem"></a>CMFCToolBarComboBoxButton::FindItem

返回列表框中包含指定字符串的第一项的索引。

```
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>参数

*lpszText*<br/>
中要在列表框中搜索的文本。

### <a name="return-value"></a>返回值

项的索引;如果未找到该项, 则为 CB_ERR。

### <a name="remarks"></a>备注

##  <a name="getbycmd"></a>CMFCToolBarComboBoxButton::GetByCmd

获取一个指针, 该指针指向具有指定命令 ID 的组合框按钮。

```
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,
    BOOL bIsFocus=FALSE);
```

### <a name="parameters"></a>参数

*uiCmd*<br/>
中组合框按钮的命令 ID。

*bIsFocus*<br/>
中如果仅搜索焦点按钮, 则为 TRUE;若要搜索所有按钮, 则为 FALSE。

### <a name="return-value"></a>返回值

指向组合框按钮的指针;如果找不到此按钮, 则为 NULL。

### <a name="remarks"></a>备注

##  <a name="getcombobox"></a>CMFCToolBarComboBoxButton::GetComboBox

返回一个指针, 该指针指向组合框按钮中的组合框。

```
CComboBox* GetComboBox() const;
```

### <a name="return-value"></a>返回值

如果方法成功, 则为指向[CComboBox 类](../../mfc/reference/ccombobox-class.md)对象的指针;否则为 NULL。

### <a name="remarks"></a>备注

##  <a name="getcontextmenuid"></a>CMFCToolBarComboBoxButton::GetContextMenuID

获取组合框按钮的快捷菜单资源 ID。

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>返回值

快捷菜单资源 ID。

##  <a name="getcount"></a>CMFCToolBarComboBoxButton:: GetCount

返回列表框中的项数。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>返回值

列表框中的项数。

### <a name="remarks"></a>备注

##  <a name="getcountall"></a>CMFCToolBarComboBoxButton::GetCountAll

获取具有指定命令 ID 的组合框按钮的列表框中的项数。

```
static int GetCountAll(UINT uiCmd);
```

### <a name="parameters"></a>参数

*uiCmd*<br/>
中组合框按钮的命令 ID。

### <a name="return-value"></a>返回值

列表框中的项数;否则, 如果找不到组合框按钮, 则 CB_ERR。

### <a name="remarks"></a>备注

##  <a name="getcursel"></a>CMFCToolBarComboBoxButton::GetCurSel

获取列表框中当前选定项的索引。

```
int GetCurSel() const;
```

### <a name="return-value"></a>返回值

列表框中当前选定项的索引;如果未选择任何项, 则为 CB_ERR。

### <a name="remarks"></a>备注

列表框索引是从零开始的。

##  <a name="getcurselall"></a>CMFCToolBarComboBoxButton::GetCurSelAll

返回具有指定命令 ID 的组合框按钮的列表框中当前选定项的索引。

```
static int GetCurSelAll(UINT uiCmd);
```

### <a name="parameters"></a>参数

*uiCmd*<br/>
中组合框按钮的命令 ID。

### <a name="return-value"></a>返回值

列表框中当前选定项的索引;否则, 如果未选择任何项或未找到组合框按钮, 则为 CB_ERR。

### <a name="remarks"></a>备注

列表框索引是从零开始的。

##  <a name="geteditctrl"></a>CMFCToolBarComboBoxButton::GetEditCtrl

返回一个指针, 该指针指向组合框按钮中的编辑框。

```
virtual CEdit* GetEditCtrl();
```

### <a name="return-value"></a>返回值

如果方法成功, 则为指向编辑框的指针;否则为 NULL。

### <a name="remarks"></a>备注

##  <a name="gethwnd"></a>CMFCToolBarComboBoxButton::GetHwnd

返回组合框的窗口句柄。

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>返回值

窗口句柄; 如果组合框未与窗口对象关联, 则为 NULL。

##  <a name="getitem"></a>CMFCToolBarComboBoxButton:: GetItem

返回与列表框中指定索引处的项关联的字符串。

```
LPCTSTR GetItem(int iIndex=-1) const;
```

### <a name="parameters"></a>参数

*iIndex*<br/>
中列表框中项的从零开始的索引。

### <a name="return-value"></a>返回值

指向与项关联的字符串的指针;否则, 如果索引参数无效, 或者索引参数为-1, 并且组合框中没有选定项, 则为 NULL。

### <a name="remarks"></a>备注

索引参数-1 返回当前选定项的字符串。

##  <a name="getitemall"></a>CMFCToolBarComboBoxButton::GetItemAll

返回与组合框按钮的列表框中指定索引处的项关联的字符串, 该组合框具有指定的命令 ID。

```
static LPCTSTR GetItemAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>参数

*uiCmd*<br/>
中组合框按钮的命令 ID。

*iIndex*<br/>
中列表框中某项的从零开始的索引。

### <a name="return-value"></a>返回值

如果方法成功, 则为指向项字符串的指针; 否则为。否则, 如果索引无效, 则找不到组合框按钮; 如果 index 为-1, 并且组合框中没有选定项, 则为 NULL。

### <a name="remarks"></a>备注

如果索引值为-1, 则返回当前选定项的字符串。

##  <a name="getitemdata"></a>CMFCToolBarComboBoxButton:: GetItemData

返回与列表框中特定索引处的项关联的数据。

```
DWORD_PTR GetItemData(int iIndex=-1) const;
```

### <a name="parameters"></a>参数

*iIndex*<br/>
中列表框中某项的从零开始的索引。

### <a name="return-value"></a>返回值

与该项关联的数据;如果该项不存在, 则为0。

### <a name="remarks"></a>备注

如果索引参数为-1, 则返回与当前选定项关联的数据。

##  <a name="getitemdataall"></a>  CMFCToolBarComboBoxButton::GetItemDataAll

返回与组合框按钮的列表框中特定索引处的项相关联的数据, 该列表框具有特定的命令 ID。

```
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>参数

*uiCmd*<br/>
中组合框按钮的命令 ID。

*iIndex*<br/>
中列表框中某项的从零开始的索引。

### <a name="return-value"></a>返回值

如果方法成功, 则为与项关联的数据;否则, 如果指定的索引无效, 则为 0; 如果找不到组合框按钮, 则为 CB_ERR。

### <a name="remarks"></a>备注

如果索引参数为-1, 则返回与当前选定项关联的数据。

##  <a name="getitemdataptrall"></a>CMFCToolBarComboBoxButton::GetItemDataPtrAll

返回与组合框按钮的列表框中特定索引处的项相关联的数据, 该列表框具有特定的命令 ID。 此数据以指针形式返回。

```
static void* GetItemDataPtrAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>参数

*uiCmd*<br/>
中组合框按钮的命令 ID。

*iIndex*<br/>
中列表框中某项的从零开始的索引。

### <a name="return-value"></a>返回值

如果方法成功, 则为与项关联的指针;否则, 如果发生错误, 则为-1; 如果未找到组合框按钮, 则为 NULL。

### <a name="remarks"></a>备注

##  <a name="getprompt"></a>CMFCToolBarComboBoxButton::GetPrompt

返回组合框按钮的提示字符串。

```
virtual CString GetPrompt() const;
```

### <a name="return-value"></a>返回值

提示字符串。

### <a name="remarks"></a>备注

当前未实现此方法。

##  <a name="gettext"></a>CMFCToolBarComboBoxButton:: GetText

获取编辑框中的文本。

```
LPCTSTR GetText() const;
```

### <a name="return-value"></a>返回值

编辑框中的文本。

### <a name="remarks"></a>备注

##  <a name="gettextall"></a>CMFCToolBarComboBoxButton::GetTextAll

获取具有指定命令 ID 的组合框按钮的编辑框中的文本。

```
static LPCTSTR GetTextAll(UINT uiCmd);
```

### <a name="parameters"></a>参数

*uiCmd*<br/>
中特定组合框按钮的命令 ID。

### <a name="return-value"></a>返回值

如果方法成功, 则为编辑框中的文本;否则为 NULL。

### <a name="remarks"></a>备注

##  <a name="hasfocus"></a>CMFCToolBarComboBoxButton::HasFocus

指示组合框当前是否有焦点。

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>返回值

如果组合框当前具有焦点, 则为 TRUE; 否则为。否则为 FALSE。

### <a name="remarks"></a>备注

如果组合框的任何子窗口当前具有焦点, 此方法也会返回 TRUE。

##  <a name="iscentervert"></a>CMFCToolBarComboBoxButton::IsCenterVert

返回应用程序中组合框按钮的垂直位置。

```
static BOOL IsCenterVert();
```

### <a name="return-value"></a>返回值

如果按钮居中, 则为 TRUE;如果按钮在顶部对齐, 则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="isflatmode"></a>CMFCToolBarComboBoxButton::IsFlatMode

返回应用程序中组合框按钮的平面样式外观。

```
static BOOL IsFlatMode();
```

### <a name="return-value"></a>返回值

如果按钮具有平面样式, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

组合框按钮的默认平面样式为 FALSE。

##  <a name="isownerof"></a>  CMFCToolBarComboBoxButton::IsOwnerOf

指示指定的句柄是与组合框按钮相关联还是与它的一个子项关联。

```
virtual BOOL IsOwnerOf(HWND hwnd);
```

### <a name="parameters"></a>参数

*hwnd*<br/>
中窗口句柄。

### <a name="return-value"></a>返回值

如果该句柄与组合框按钮或其子控件之一关联, 则为 TRUE;否则为 FALSE。

##  <a name="isribbonbutton"></a>CMFCToolBarComboBoxButton::IsRibbonButton

指示组合框按钮是否位于功能区面板上。

```
BOOL IsRibbonButton() const;
```

### <a name="return-value"></a>返回值

始终为 FALSE。

### <a name="remarks"></a>备注

默认情况下, 此方法始终返回 FALSE, 这意味着在功能区面板上永远不会显示组合框按钮。

##  <a name="iswindowvisible"></a>CMFCToolBarComboBoxButton::IsWindowVisible

返回组合框按钮的可见性状态。

```
virtual BOOL IsWindowVisible();
```

### <a name="return-value"></a>返回值

组合框按钮的可见性状态。

##  <a name="notifycommand"></a>CMFCToolBarComboBoxButton::NotifyCommand

指示组合框按钮是否处理消息。

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>参数

*iNotifyCode*<br/>
中与命令关联的通知消息。

### <a name="return-value"></a>返回值

组合框按钮是否处理消息。

##  <a name="onaddtocustomizepage"></a>CMFCToolBarComboBoxButton::OnAddToCustomizePage

当按钮添加到 "**自定义**" 对话框时由框架调用。

```
virtual void OnAddToCustomizePage();
```

##  <a name="oncalculatesize"></a>  CMFCToolBarComboBoxButton::OnCalculateSize

由框架调用以计算按钮的大小。

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中显示组合框按钮的设备上下文。

*sizeDefault*<br/>
中组合框按钮的默认大小。

*bHorz*<br/>
中父工具栏的停靠状态。 如果工具栏水平停靠, 则为 TRUE; 如果工具栏垂直停靠, 则为 FALSE。

### <a name="return-value"></a>返回值

一个`SIZE`结构, 其中包含组合框按钮的尺寸 (以像素为单位)。

##  <a name="onchangeparentwnd"></a>CMFCToolBarComboBoxButton::OnChangeParentWnd

当组合框按钮插入新工具栏时由框架调用。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>参数

*pWndParent*<br/>
中指向新父工具栏的指针。

##  <a name="onclick"></a>CMFCToolBarComboBoxButton:: OnClick

当用户单击组合框按钮时由框架调用。

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
中指向组合框按钮的父窗口的指针。

*bDelay*<br/>
中保留以供在派生类中使用。

### <a name="return-value"></a>返回值

如果该方法处理事件, 则为 TRUE;否则为 FALSE。

##  <a name="onctlcolor"></a>  CMFCToolBarComboBoxButton::OnCtlColor

当用户更改父工具栏颜色以设置组合框按钮颜色时, 由框架调用。

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中显示组合框按钮的设备上下文。

*nCtlColor*<br/>
中用.

### <a name="return-value"></a>返回值

框架用于绘制组合框按钮背景的画笔的句柄。

### <a name="remarks"></a>备注

此方法还设置组合框按钮文本颜色。

##  <a name="ondraw"></a>  CMFCToolBarComboBoxButton::OnDraw

由框架调用, 用于通过使用指定的样式和选项绘制组合框按钮。

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    CMFCToolBarImages* pImages,
    BOOL bHorz = TRUE,
    BOOL bCustomizeMode = FALSE,
    BOOL bHighlight = FALSE,
    BOOL bDrawBorder = TRUE,
    BOOL bGrayDisabledButtons = TRUE);
```

### <a name="parameters"></a>参数

*Pdc*<br/>
中显示按钮的设备上下文。

*rect*<br/>
中按钮的边框。

*pImages*<br/>
中与按钮关联的图像的集合。

*bHorz*<br/>
中父工具栏的停靠状态。 如果工具栏水平停靠, 则为 TRUE; 如果工具栏垂直停靠, 则为 FALSE。

*bCustomizeMode*<br/>
中应用程序是否处于自定义模式。

*bHighlight*<br/>
中是否突出显示组合框按钮。

*bDrawBorder*<br/>
中是否绘制带有边框的组合框按钮。

*bGrayDisabledButtons*<br/>
中若要绘制已禁用底纹的按钮, 则为 TRUE;若为 FALSE, 则使用已禁用的图像集合。

##  <a name="ondrawoncustomizelist"></a>  CMFCToolBarComboBoxButton::OnDrawOnCustomizeList

由框架调用, 用于绘制 "**自定义**" 对话框的 "**命令**" 窗格中的组合框按钮。

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>参数

*pDC*<br/>
中显示组合框按钮的设备上下文。

*rect*<br/>
中组合框按钮的边框。

*bSelected*<br/>
中如果选中组合框按钮, 则为 TRUE;否则为 FALSE。

### <a name="return-value"></a>返回值

组合框按钮的宽度 (以像素为单位)。

##  <a name="onglobalfontschanged"></a>CMFCToolBarComboBoxButton::OnGlobalFontsChanged

当应用程序字体更改时, 由框架调用以设置组合框按钮字体。

```
virtual void OnGlobalFontsChanged();
```

##  <a name="onmove"></a>CMFCToolBarComboBoxButton::OnMove

当父工具栏移动时, 由框架调用以更改组合框按钮的位置。

```
virtual void OnMove();
```

##  <a name="onshow"></a>CMFCToolBarComboBoxButton::OnShow

当隐藏或显示组合框按钮时由框架调用。

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>参数

*bShow*<br/>
中是隐藏还是显示组合框按钮。

##  <a name="onsize"></a>CMFCToolBarComboBoxButton:: OnSize

当父工具栏更改大小时, 由框架调用以更改组合框按钮的大小。

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>参数

*iSize*<br/>
中组合框按钮的新宽度。

##  <a name="onupdatetooltip"></a>CMFCToolBarComboBoxButton::OnUpdateToolTip

当用户更改组合框按钮的工具提示时由框架调用。

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>参数

*pWndParent*<br/>
中指向组合框按钮的父窗口的指针。

*iButtonIndex*<br/>
中组合框按钮的 ID。

*wndToolTip*<br/>
中与组合框按钮关联的工具提示。

*str*<br/>
中工具提示文本。

### <a name="return-value"></a>返回值

如果该方法处理事件, 则为 TRUE;否则为 FALSE。

##  <a name="removeallitems"></a>  CMFCToolBarComboBoxButton::RemoveAllItems

删除列表和编辑框中的所有项。

```
void RemoveAllItems();
```

### <a name="remarks"></a>备注

从列表框中移除所有项, 并在组合框中编辑控件。

##  <a name="selectitem"></a>  CMFCToolBarComboBoxButton::SelectItem

选择列表框中的项。

```
BOOL SelectItem(
    int iIndex,
    BOOL bNotify=TRUE);

BOOL SelectItem(DWORD_PTR dwData);
BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>参数

*iIndex*<br/>
中列表框中某项的从零开始的索引。

*bNotify*<br/>
中若要通知选择的组合框按钮, 则为 TRUE;否则为 FALSE。

*dwData*<br/>
中与列表框中的项关联的数据。

*lpszText*<br/>
中列表框中的项的文本。

### <a name="return-value"></a>返回值

如果方法成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="selectitemall"></a>  CMFCToolBarComboBoxButton::SelectItemAll

选择具有指定命令 ID 的组合框按钮的列表框中的项。

```
static BOOL SelectItemAll(
    UINT uiCmd,
    int iIndex);

static BOOL SelectItemAll(
    UINT uiCmd,
    DWORD_PTR dwData);

static BOOL SelectItemAll(
    UINT uiCmd,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>参数

*uiCmd*<br/>
中包含列表框的组合框按钮的命令 ID。

*iIndex*<br/>
中列表框中项的从零开始的索引。 如果值为-1, 则删除列表框中的任何当前选择, 并清除编辑框。

*dwData*<br/>
中列表框中项的数据。

*lpszText*<br/>
中列表框中的项的文本。

### <a name="return-value"></a>返回值

如果方法成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

##  <a name="serialize"></a>CMFCToolBarComboBoxButton:: 串行化

从存档中读取此对象或将其写入存档。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>参数

*ar*<br/>
[in, out]要`CArchive`序列化的对象。

### <a name="remarks"></a>备注

对象中的`CArchive`设置确定此方法是读取还是写入存档。

##  <a name="setaccdata"></a>  CMFCToolBarComboBoxButton::SetACCData

使用组合框`CAccessibilityData`按钮中的可访问性数据填充指定的对象。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>参数

*pParent*<br/>
中组合框按钮的父窗口。

*data*<br/>
弄一个`CAccessibilityData`对象, 该对象接收组合框按钮中的辅助功能数据。

### <a name="return-value"></a>返回值

如果方法成功, 则为 TRUE;否则为 FALSE。

##  <a name="setcentervert"></a>CMFCToolBarComboBoxButton::SetCenterVert

设置应用程序中组合框按钮的垂直位置。

```
static void SetCenterVert(BOOL bCenterVert=TRUE);
```

### <a name="parameters"></a>参数

*bCenterVert*<br/>
中若要在工具栏中居中组合框按钮, 则为 TRUE;如果将组合框按钮与工具栏顶部对齐, 则为 FALSE。

### <a name="remarks"></a>备注

默认情况下, 组合框按钮与顶部对齐。

##  <a name="setcontextmenuid"></a>CMFCToolBarComboBoxButton::SetContextMenuID

设置组合框按钮的快捷菜单资源 ID。

```
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>参数

*uiResID*<br/>
中快捷菜单资源 ID。

##  <a name="setdropdownheight"></a>CMFCToolBarComboBoxButton::SetDropDownHeight

在下拉列表框时设置列表框的高度。

```
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>参数

*nHeight*<br/>
中列表框的高度 (以像素为单位)。

### <a name="remarks"></a>备注

默认高度为150像素。

##  <a name="setflatmode"></a>CMFCToolBarComboBoxButton::SetFlatMode

设置应用程序中组合框按钮的平面样式外观。

```
static void SetFlatMode(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>参数

*bFlat*<br/>
中对于平面样式外观, 为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

组合框按钮的默认平面样式为 FALSE。

##  <a name="setstyle"></a>CMFCToolBarComboBoxButton:: System.windows.forms.control.setstyle

为组合框按钮设置指定样式, 如果未禁用, 则重绘控件。

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>参数

*nStyle*<br/>
中工具栏样式的按位组合 (OR)。

### <a name="remarks"></a>备注

有关工具栏按钮样式的列表, 请参阅[Toolbar 控件样式](../../mfc/reference/toolbar-control-styles.md)

##  <a name="settext"></a>CMFCToolBarComboBoxButton:: SetText

设置组合框按钮的编辑框中的文本。

```
void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>参数

*lpszText*<br/>
中指向字符串的指针, 该字符串包含编辑框的文本。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton 类](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CComboBox 类](../../mfc/reference/ccombobox-class.md)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[演练：将控件添加到工具栏](../../mfc/walkthrough-putting-controls-on-toolbars.md)
