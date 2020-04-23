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
ms.openlocfilehash: 995d7d0db55889130e1cad9585b8fc87285ffd27
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754011"
---
# <a name="cmfctoolbarcomboboxbutton-class"></a>CMFCToolBarComboBoxButton 类

包含组合框控件 （ [CComboBox 类](../../mfc/reference/ccombobox-class.md)） 的工具栏按钮。

## <a name="syntax"></a>语法

```
class CMFCToolBarComboBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CMFCToolBarComBox按钮：CMFC工具栏按钮](#cmfctoolbarcomboboxbutton)|构造一个 `CMFCToolBarComboBoxButton`。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCToolBarComBox按钮：：添加项目](#additem)|将项目添加到组合框列表的末尾。|
|[CMFCToolBarComBox按钮：：添加排序项目](#addsorteditem)|将项目添加到组合框列表中。 列表中的项顺序由 指定`Compare`。|
|[CMFCToolBarComBox按钮：：比较](#compare)|比较两个项目。 调用以对`AddSortedItems`添加到组合框列表的项目进行排序。|
|[CMFCToolBarComBox按钮：：创建编辑](#createedit)|为组合框按钮创建新的编辑控件。|
|[CMFCToolBarComBox按钮：:Delete项目](#deleteitem)|从组合框列表中删除项目。|
|[CMFCToolBarComBox按钮：：查找项目](#finditem)|返回包含指定字符串的项的索引。|
|[CMFCToolBarComBox按钮：：获取](#getbycmd)|返回指向具有指定命令 ID 的组合框按钮的指针。|
|[CMFCToolBarComBox按钮：：获取康博盒](#getcombobox)|返回嵌入在组合框按钮中的组合框控件的指针。|
|[CMFCToolBarComBox按钮：：获取计数](#getcount)|返回组合框列表中的项目数。|
|[CMFCToolBarComBox按钮：：获取计数所有](#getcountall)|查找具有指定命令 ID 的组合框按钮。 返回该按钮的组合框列表中的项目数。|
|[CMFCToolBarComBox按钮：：获取CurSel](#getcursel)|返回组合框列表中所选项的索引。|
|[CMFCToolBarComBox按钮：：获取CurSelAll](#getcurselall)|查找具有指定命令 ID 的组合框按钮，并在该按钮的组合框列表中返回所选项的索引。|
|[CMFCToolBarComBox按钮：：获取编辑](#geteditctrl)|返回指向嵌入在组合框按钮中的编辑控件的指针。|
|[CMFCToolBarComBox按钮：：获取项目](#getitem)|返回与组合框列表中的指定索引关联的字符串。|
|[CMFCToolBarComBox按钮：：获取项目全部](#getitemall)|查找具有指定命令 ID 的组合框按钮，并返回该按钮的组合框列表中与索引关联的字符串。|
|[CMFCToolBarComBox按钮：：获取项目数据](#getitemdata)|返回与组合框列表中的指定索引关联的 32 位值。|
|[CMFCToolBarCombox按钮：获取项目数据全部](#getitemdataall)|查找具有指定命令 ID 的组合框按钮，并返回该按钮的组合框列表中与索引关联的 32 位值。|
|[CMFCToolBarComBox按钮：：获取项目数据PtrAll](#getitemdataptrall)|查找具有指定命令 ID 的组合框按钮。 检索在该按钮的组合框列表中关联的索引的 32 位值，并将 32 位值作为指针返回。|
|[CMFCToolBarComBox按钮：：获取文本](#gettext)|从组合框的编辑控件返回文本。|
|[CMFCToolBarComBox按钮：：获取文本全部](#gettextall)|查找具有指定命令 ID 的组合框按钮，并从该按钮的编辑控件返回文本。|
|[CMFCToolBarComBox按钮：：IsCenterVert](#iscentervert)|确定应用程序中的组合框按钮是居中还是与工具栏顶部对齐。|
|[CMFCToolBarComBox按钮：：是平模式](#isflatmode)|确定应用程序中的组合框按钮的外观是否平坦。|
|[CMFCToolBarComBox按钮：：删除所有项目](#removeallitems)|从列表框中删除所有项目，并编辑组合框控件。|
|[CMFCToolBarComBox按钮：：选择项目](#selectitem)|根据组合框中的索引、32 位值或字符串选择项，并通知组合框控件有关所选内容。|
|[CMFCToolBarComBox按钮：：选择项目全部](#selectitemall)|查找具有指定命令 ID 的组合框按钮。 调用`SelectItem`以根据该按钮的字符串、索引或 32 位值选择该按钮的组合框中的项。|
|[CMFCToolBarComBox按钮：：设置中心](#setcentervert)|指定应用程序中的组合框按钮是垂直居中还是与工具栏顶部对齐。|
|[CMFCToolBarCombox按钮：：设置下拉高度](#setdropdownheight)|设置下拉列表框的高度。|
|[CMFCToolBarComBox按钮：：设置平模式](#setflatmode)|指定应用程序中的组合框按钮的外观是否平坦。|

## <a name="remarks"></a>备注

要向工具栏添加组合框按钮，请按照以下步骤操作：

1. 在父级工具栏资源中保留该按钮的虚拟资源 ID。

2. 构造`CMFCToolBarComboBoxButton`对象。

3. 在处理AFX_WM_RESETTOOLBAR消息的消息处理程序中，使用[CMFCToolBar：：：替换Button，](../../mfc/reference/cmfctoolbar-class.md#replacebutton)将虚拟按钮替换为新的组合框按钮。

有关详细信息，请参阅[演练：将控件放在工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)。 有关组合框工具栏按钮的示例，请参阅示例项目 VisualStudioDemo。

## <a name="example"></a>示例

下面的示例演示了如何使用 `CMFCToolBarComboBoxButton` 类中的各种方法。 该示例演示如何启用编辑和组合框，设置应用程序中组合框按钮的垂直位置，在下放列表框时设置列表框的高度，设置应用程序中组合框按钮的平面样式外观，并在组合框按钮的编辑框中设置文本。 此代码段是[可视化工作室演示示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComBox按钮](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

## <a name="requirements"></a>要求

**标题：** afxtoolbarcombox 按钮.h

## <a name="cmfctoolbarcomboboxbuttonadditem"></a><a name="additem"></a>CMFCToolBarComBox按钮：：添加项目

将唯一项目追加到列表框。

```
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>参数

*lpszItem*<br/>
[在]要添加到列表框的项的文本。

*dwData*<br/>
[在]与要添加到列表框的项关联的数据。

### <a name="return-value"></a>返回值

列表框中最后一项的索引。

### <a name="remarks"></a>备注

对列表框样式进行排序时，请勿使用此方法。

如果项目文本已在列表框中，则新数据存储与现有项一起。 对该项目的搜索区分大小写。

## <a name="cmfctoolbarcomboboxbuttonaddsorteditem"></a><a name="addsorteditem"></a>CMFCToolBarComBox按钮：：添加排序项目

按[比较](#compare)方法定义的顺序将项添加到列表框。

```
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>参数

*lpszItem*<br/>
[在]要添加到列表框的项的文本。

*dwData*<br/>
[在]与要添加到列表框的项关联的数据。

### <a name="return-value"></a>返回值

添加到列表框的项的索引。

### <a name="remarks"></a>备注

使用此函数按特定顺序将项目添加到列表框。

## <a name="cmfctoolbarcomboboxbuttoncanbestretched"></a><a name="canbestretched"></a>CMFCToolBarComBox按钮：：可以拉伸

指示组合框按钮大小是否可以更改。

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>返回值

返回 TRUE。

## <a name="cmfctoolbarcomboboxbuttoncmfctoolbarcomboboxbutton"></a><a name="cmfctoolbarcomboboxbutton"></a>CMFCToolBarComBox按钮：CMFC工具栏按钮

构造[CMFCToolBarComBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)对象。

```
CMFCToolBarComboBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=CBS_DROPDOWNLIST,
    int iWidth=0);
```

### <a name="parameters"></a>参数

*uiID*<br/>
[在]新按钮的命令 ID。

*i图像*<br/>
[在]与新按钮关联的图像的图像索引。

*dwStyle*<br/>
[在]新按钮的样式。

*iWidth*<br/>
[在]新按钮的宽度（以像素为单位）。

### <a name="remarks"></a>备注

默认宽度为 150 像素。

有关工具栏按钮样式的列表，请参阅[工具栏控件样式](../../mfc/reference/toolbar-control-styles.md)

## <a name="cmfctoolbarcomboboxbuttoncleardata"></a><a name="cleardata"></a>CMFCToolBarComBox按钮：：清除数据

删除用户定义的数据。

```
virtual void ClearData();
```

### <a name="remarks"></a>备注

默认情况下，此方法不执行任何操作。 如果要删除任何用户定义的数据，请覆盖派生类中的此方法。

## <a name="cmfctoolbarcomboboxbuttoncompare"></a><a name="compare"></a>CMFCToolBarComBox按钮：：比较

比较两个字符串。

```
virtual int Compare(
    LPCTSTR lpszItem1,
    LPCTSTR lpszItem2);
```

### <a name="parameters"></a>参数

*lpszItem1*<br/>
[在]要比较的第一个字符串。

*lpszItem2*<br/>
[在]要比较的第二个字符串。

### <a name="return-value"></a>返回值

指示字符串之间的区分大小写字典关系的值。 下表列出了可能的值：

|“值”|说明|
|-----------|-----------------|
|\<0|第一个字符串小于第二个字符串。|
|0|第一个字符串等于第二个字符串。|
|>0|第一个字符串大于第二个字符串。|

### <a name="remarks"></a>备注

重写此方法以更改在列表框中排序项目的方式。

比较区分大小写。

此方法仅从[AddSortedItem](#addsorteditem)方法调用。

## <a name="cmfctoolbarcomboboxbuttoncopyfrom"></a><a name="copyfrom"></a>CMFCToolBarCombox按钮：：从复制

将指定的`CMFCToolBarComboBoxButton`状态复制到当前对象。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>参数

*src*<br/>
[在]源`CMFCToolBarComboBoxButton`对象。

## <a name="cmfctoolbarcomboboxbuttoncreatecombo"></a><a name="createcombo"></a>CMFCToolBarComBox按钮：：创建康博

为组合框按钮创建新组合框。

```
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>参数

*pwnd 父级*<br/>
[在]指向按钮的父窗口的指针。

*矩形*<br/>
[在]组合框的边界矩形。

### <a name="return-value"></a>返回值

如果方法成功，则指向新组合框的指针;否则，NULL。

## <a name="cmfctoolbarcomboboxbuttoncreateedit"></a><a name="createedit"></a>CMFCToolBarComBox按钮：：创建编辑

为组合框按钮创建新的编辑框。

```
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>参数

*pwnd 父级*<br/>
[在]指向按钮的父窗口的指针。

*矩形*<br/>
[在]新编辑框的边界矩形。

*dwEdit风格*<br/>
[在]控制新编辑框的样式。

### <a name="return-value"></a>返回值

如果方法成功，则指向新编辑框的指针;否则，NULL。

### <a name="remarks"></a>备注

当框架为组合框按钮创建新的编辑框时，它将调用此方法。 重写此方法以更改创建[CMFCToolBarCombox 编辑](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)的方式。

## <a name="cmfctoolbarcomboboxbuttondeleteitem"></a><a name="deleteitem"></a>CMFCToolBarComBox按钮：:Delete项目

从列表框中删除指定的项目。

```
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
[在]要删除的项目的文本。 如果有多个具有相同文本的项，则删除第一个项目。

### <a name="return-value"></a>返回值

如果项目已找到并成功删除，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

## <a name="cmfctoolbarcomboboxbuttonduplicatedata"></a><a name="duplicatedata"></a>CMFCToolBarComBox按钮：:D

复制用户定义的数据。

```
virtual void DuplicateData();
```

### <a name="remarks"></a>备注

默认情况下，此方法不执行任何操作。 如果要复制任何用户定义的数据，请覆盖派生类中的此方法。

## <a name="cmfctoolbarcomboboxbuttonenablewindow"></a><a name="enablewindow"></a>CMFCToolBarComBox按钮：：启用窗口

启用或禁用编辑和组合框。

```
virtual void EnableWindow(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
[在]TRUE 启用编辑和组合框;FALSE 以禁用编辑和组合框。

### <a name="remarks"></a>备注

禁用后，控件无法变为活动状态，并且无法接受用户输入。

## <a name="cmfctoolbarcomboboxbuttonexporttomenubutton"></a><a name="exporttomenubutton"></a>CMFCToolBarCombox按钮：：导出到菜单按钮

使用组合框按钮命令 ID 将字符串从应用程序字符串表复制到指定的菜单。

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>参数

*菜单按钮*<br/>
[出]引用菜单按钮。

### <a name="return-value"></a>返回值

始终为 TRUE。

## <a name="cmfctoolbarcomboboxbuttonfinditem"></a><a name="finditem"></a>CMFCToolBarComBox按钮：：查找项目

返回列表框中包含指定字符串的第一项的索引。

```
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>参数

*lpszText*<br/>
[在]要在列表框中搜索的文本。

### <a name="return-value"></a>返回值

项的索引;或CB_ERR（如果找不到该项目）。

### <a name="remarks"></a>备注

## <a name="cmfctoolbarcomboboxbuttongetbycmd"></a><a name="getbycmd"></a>CMFCToolBarComBox按钮：：获取

获取指向具有指定命令 ID 的组合框按钮的指针。

```
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,
    BOOL bIsFocus=FALSE);
```

### <a name="parameters"></a>参数

*乌伊Cmd*<br/>
[在]组合框按钮的命令 ID。

*bIsFocus*<br/>
[在]TRUE 仅搜索焦点按钮;FALSE 以搜索所有按钮。

### <a name="return-value"></a>返回值

指向组合框按钮的指针;或 NULL，如果找不到按钮。

### <a name="remarks"></a>备注

## <a name="cmfctoolbarcomboboxbuttongetcombobox"></a><a name="getcombobox"></a>CMFCToolBarComBox按钮：：获取康博盒

返回组合框按钮中组合框的指针。

```
CComboBox* GetComboBox() const;
```

### <a name="return-value"></a>返回值

如果方法成功，则指向[CComboBox 类](../../mfc/reference/ccombobox-class.md)对象的指针;否则 NULL。

### <a name="remarks"></a>备注

## <a name="cmfctoolbarcomboboxbuttongetcontextmenuid"></a><a name="getcontextmenuid"></a>CMFCToolBarComBox按钮：：获取上下文菜单ID

获取组合框按钮的快捷菜单资源 ID。

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>返回值

快捷菜单资源 ID。

## <a name="cmfctoolbarcomboboxbuttongetcount"></a><a name="getcount"></a>CMFCToolBarComBox按钮：：获取计数

返回列表框中的项目数。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>返回值

列表框中的项目数。

### <a name="remarks"></a>备注

## <a name="cmfctoolbarcomboboxbuttongetcountall"></a><a name="getcountall"></a>CMFCToolBarComBox按钮：：获取计数所有

获取具有指定命令 ID 的组合框按钮的列表框中的项目数。

```
static int GetCountAll(UINT uiCmd);
```

### <a name="parameters"></a>参数

*乌伊Cmd*<br/>
[在]组合框按钮的命令 ID。

### <a name="return-value"></a>返回值

列表框中的项目数;否则，如果未找到组合框按钮，则CB_ERR。

### <a name="remarks"></a>备注

## <a name="cmfctoolbarcomboboxbuttongetcursel"></a><a name="getcursel"></a>CMFCToolBarComBox按钮：：获取CurSel

在列表框中获取当前选定项的索引。

```
int GetCurSel() const;
```

### <a name="return-value"></a>返回值

列表框中当前选定项的索引;或未选择项目CB_ERR。

### <a name="remarks"></a>备注

列表框索引基于零。

## <a name="cmfctoolbarcomboboxbuttongetcurselall"></a><a name="getcurselall"></a>CMFCToolBarComBox按钮：：获取CurSelAll

在具有指定命令 ID 的组合框按钮的列表框中返回当前选定项的索引。

```
static int GetCurSelAll(UINT uiCmd);
```

### <a name="parameters"></a>参数

*乌伊Cmd*<br/>
[在]组合框按钮的命令 ID。

### <a name="return-value"></a>返回值

列表框中当前选定项的索引;否则，如果未选择任何项目或找不到组合框按钮，则CB_ERR。

### <a name="remarks"></a>备注

列表框索引基于零。

## <a name="cmfctoolbarcomboboxbuttongeteditctrl"></a><a name="geteditctrl"></a>CMFCToolBarComBox按钮：：获取编辑

在组合框按钮中返回指向编辑框的指针。

```
virtual CEdit* GetEditCtrl();
```

### <a name="return-value"></a>返回值

如果方法成功，则指向编辑框的指针;否则，NULL。

### <a name="remarks"></a>备注

## <a name="cmfctoolbarcomboboxbuttongethwnd"></a><a name="gethwnd"></a>CMFCToolBarComBox按钮：：GetHwnd

返回组合框的窗口句柄。

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>返回值

如果组合框未与窗口对象关联，则窗口句柄或 NULL。

## <a name="cmfctoolbarcomboboxbuttongetitem"></a><a name="getitem"></a>CMFCToolBarComBox按钮：：获取项目

返回与列表框中指定索引处的项关联的字符串。

```
LPCTSTR GetItem(int iIndex=-1) const;
```

### <a name="parameters"></a>参数

*iIndex*<br/>
[在]列表框中项的零基索引。

### <a name="return-value"></a>返回值

指向与项关联的字符串的指针;否则，如果索引参数无效，或者索引参数为 -1 且组合框中没有选定项，则 NULL。

### <a name="remarks"></a>备注

索引参数 -1 返回当前选择的项的字符串。

## <a name="cmfctoolbarcomboboxbuttongetitemall"></a><a name="getitemall"></a>CMFCToolBarComBox按钮：：获取项目全部

在具有指定命令 ID 的组合框按钮的列表框中返回与指定索引处的项目关联的字符串。

```
static LPCTSTR GetItemAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>参数

*乌伊Cmd*<br/>
[在]组合框按钮的命令 ID。

*iIndex*<br/>
[在]列表框中项的零基索引。

### <a name="return-value"></a>返回值

如果方法成功，则指向项字符串的指针;否则，如果索引无效，则 NULL，找不到组合框按钮，或者如果索引为 -1，并且组合框中没有选定项。

### <a name="remarks"></a>备注

索引值 -1 返回当前选择的项的字符串。

## <a name="cmfctoolbarcomboboxbuttongetitemdata"></a><a name="getitemdata"></a>CMFCToolBarComBox按钮：：获取项目数据

返回与列表框中特定索引处的项关联的数据。

```
DWORD_PTR GetItemData(int iIndex=-1) const;
```

### <a name="parameters"></a>参数

*iIndex*<br/>
[在]列表框中项的零基索引。

### <a name="return-value"></a>返回值

与项关联的数据;或 0，如果项目不存在。

### <a name="remarks"></a>备注

索引参数 -1 返回与当前选定项关联的数据。

## <a name="cmfctoolbarcomboboxbuttongetitemdataall"></a><a name="getitemdataall"></a>CMFCToolBarCombox按钮：获取项目数据全部

在具有特定命令 ID 的组合框按钮的列表框中返回与特定索引项关联的数据。

```
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>参数

*乌伊Cmd*<br/>
[在]组合框按钮的命令 ID。

*iIndex*<br/>
[在]列表框中项的零基索引。

### <a name="return-value"></a>返回值

如果方法成功，则与项关联的数据;否则，如果指定的索引无效，则为 0;如果未找到组合框按钮，则CB_ERR。

### <a name="remarks"></a>备注

索引参数 -1 返回与当前选定项关联的数据。

## <a name="cmfctoolbarcomboboxbuttongetitemdataptrall"></a><a name="getitemdataptrall"></a>CMFCToolBarComBox按钮：：获取项目数据PtrAll

在具有特定命令 ID 的组合框按钮的列表框中返回与特定索引项关联的数据。 此数据作为指针返回。

```
static void* GetItemDataPtrAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>参数

*乌伊Cmd*<br/>
[在]组合框按钮的命令 ID。

*iIndex*<br/>
[在]列表框中项的零基索引。

### <a name="return-value"></a>返回值

如果方法成功，则与项关联的指针;否则，如果发生错误，则为 -1;如果未找到组合框按钮，则为 NULL。

### <a name="remarks"></a>备注

## <a name="cmfctoolbarcomboboxbuttongetprompt"></a><a name="getprompt"></a>CMFCToolBarComBox按钮：：获取提示

返回组合框按钮的提示字符串。

```
virtual CString GetPrompt() const;
```

### <a name="return-value"></a>返回值

提示字符串。

### <a name="remarks"></a>备注

此方法当前未实现。

## <a name="cmfctoolbarcomboboxbuttongettext"></a><a name="gettext"></a>CMFCToolBarComBox按钮：：获取文本

获取编辑框中的文本。

```
LPCTSTR GetText() const;
```

### <a name="return-value"></a>返回值

编辑框中的文本。

### <a name="remarks"></a>备注

## <a name="cmfctoolbarcomboboxbuttongettextall"></a><a name="gettextall"></a>CMFCToolBarComBox按钮：：获取文本全部

获取具有指定命令 ID 的组合框按钮的编辑框中的文本。

```
static LPCTSTR GetTextAll(UINT uiCmd);
```

### <a name="parameters"></a>参数

*乌伊Cmd*<br/>
[在]特定组合框按钮的命令 ID。

### <a name="return-value"></a>返回值

如果方法成功，则编辑框中的文本;否则，NULL。

### <a name="remarks"></a>备注

## <a name="cmfctoolbarcomboboxbuttonhasfocus"></a><a name="hasfocus"></a>CMFCToolBarComBox按钮：：有焦点

指示组合框当前是否具有焦点。

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>返回值

如果组合框当前具有焦点，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

如果组合框的任何子窗口当前具有焦点，则此方法也会返回 TRUE。

## <a name="cmfctoolbarcomboboxbuttoniscentervert"></a><a name="iscentervert"></a>CMFCToolBarComBox按钮：：IsCenterVert

返回应用程序中组合框按钮的垂直位置。

```
static BOOL IsCenterVert();
```

### <a name="return-value"></a>返回值

如果按钮居中，则为 TRUE;如果按钮在顶部对齐，则 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfctoolbarcomboboxbuttonisflatmode"></a><a name="isflatmode"></a>CMFCToolBarComBox按钮：：是平模式

返回应用程序中组合框按钮的平面样式外观。

```
static BOOL IsFlatMode();
```

### <a name="return-value"></a>返回值

如果按钮具有平面样式，则为 TRUE;否则，FALSE。

### <a name="remarks"></a>备注

组合框按钮的默认平面样式为 FALSE。

## <a name="cmfctoolbarcomboboxbuttonisownerof"></a><a name="isownerof"></a>CMFCToolBarCombox按钮：所有者

指示指定的句柄是否与组合框按钮或其子控点之一相关联。

```
virtual BOOL IsOwnerOf(HWND hwnd);
```

### <a name="parameters"></a>参数

*霍恩德*<br/>
[在]窗口句柄。

### <a name="return-value"></a>返回值

如果手柄与组合框按钮或其一个子按钮一起被压缩，则为 TRUE;否则，FALSE。

## <a name="cmfctoolbarcomboboxbuttonisribbonbutton"></a><a name="isribbonbutton"></a>CMFCToolBarComBox按钮：：正带按钮

指示组合框按钮是否驻留在功能区面板上。

```
BOOL IsRibbonButton() const;
```

### <a name="return-value"></a>返回值

始终为 FALSE。

### <a name="remarks"></a>备注

默认情况下，此方法始终返回 FALSE，这意味着组合框按钮永远不会显示在功能区面板上。

## <a name="cmfctoolbarcomboboxbuttoniswindowvisible"></a><a name="iswindowvisible"></a>CMFCToolBarComBox按钮：：窗口可见

返回组合框按钮的可见性状态。

```
virtual BOOL IsWindowVisible();
```

### <a name="return-value"></a>返回值

组合框按钮的可见性状态。

## <a name="cmfctoolbarcomboboxbuttonnotifycommand"></a><a name="notifycommand"></a>CMFCToolBarComBox按钮：：通知命令

指示组合框按钮是否处理该消息。

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>参数

*iNotify代码*<br/>
[在]与命令关联的通知消息。

### <a name="return-value"></a>返回值

组合框按钮是否处理消息。

## <a name="cmfctoolbarcomboboxbuttononaddtocustomizepage"></a><a name="onaddtocustomizepage"></a>CMFCToolBarCombox按钮：：在"添加"上自定义页面

将按钮添加到 **"自定义"** 对话框时由框架调用。

```
virtual void OnAddToCustomizePage();
```

## <a name="cmfctoolbarcomboboxbuttononcalculatesize"></a><a name="oncalculatesize"></a>CMFCToolBarCombox按钮：：在计算尺寸上

由框架调用以计算按钮的大小。

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]显示组合框按钮的设备上下文。

*大小 默认*<br/>
[在]组合框按钮的默认大小。

*布霍兹*<br/>
[在]父工具栏的停靠状态。 当工具栏水平停靠时为 TRUE;当工具栏垂直停靠时为 FALSE。

### <a name="return-value"></a>返回值

包含`SIZE`组合框按钮的尺寸（以像素为单位）的结构。

## <a name="cmfctoolbarcomboboxbuttononchangeparentwnd"></a><a name="onchangeparentwnd"></a>CMFCToolBarCombox按钮：：打开更改家长

当组合框按钮插入到新的工具栏中时，由框架调用。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>参数

*pwnd 父级*<br/>
[在]指向新父工具栏的指针。

## <a name="cmfctoolbarcomboboxbuttononclick"></a><a name="onclick"></a>CMFCToolBarCombox按钮：：点击

当用户单击组合框按钮时由框架调用。

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
[在]指向组合框按钮的父窗口。

*bDelay*<br/>
[在]保留用于派生类。

### <a name="return-value"></a>返回值

如果方法处理事件，则为 TRUE;如果方法处理事件，则为 TRUE。否则，FALSE。

## <a name="cmfctoolbarcomboboxbuttononctlcolor"></a><a name="onctlcolor"></a>CMFCToolBarCombox按钮：：在CtlColor上

当用户更改父工具栏颜色以设置组合框按钮颜色时，由框架调用。

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]显示组合框按钮的设备上下文。

*nCtlColor*<br/>
[在]闲置。

### <a name="return-value"></a>返回值

处理框架用于绘制组合框按钮背景的画笔。

### <a name="remarks"></a>备注

此方法还设置组合框按钮文本颜色。

## <a name="cmfctoolbarcomboboxbuttonondraw"></a><a name="ondraw"></a>CMFCToolBarCombox按钮：：开拉

框架调用使用指定的样式和选项绘制组合框按钮。

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
[在]显示按钮的设备上下文。

*矩形*<br/>
[在]按钮的边界矩形。

*pImage*<br/>
[在]与按钮关联的图像的集合。

*布霍兹*<br/>
[在]父工具栏的停靠状态。 当工具栏水平停靠时为 TRUE;当工具栏垂直停靠时为 FALSE。

*b 定制模式*<br/>
[在]应用程序是否处于自定义模式。

*b 高光*<br/>
[在]是否绘制突出显示的组合框按钮。

*bDraw边框*<br/>
[在]是否使用边框绘制组合框按钮。

*b格雷禁用按钮*<br/>
[在]TRUE 以绘制带实线禁用的按钮;FALSE 用于使用禁用的图像集合。

## <a name="cmfctoolbarcomboboxbuttonondrawoncustomizelist"></a><a name="ondrawoncustomizelist"></a>CMFCToolBarCombox按钮：：在画上定制列表

由框架调用以在 **"自定义"** 对话框的 **"命令"** 窗格中绘制组合框按钮。

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>参数

*pDC*<br/>
[在]显示组合框按钮的设备上下文。

*矩形*<br/>
[在]组合框按钮的边界矩形。

*b选定*<br/>
[在]如果选择了组合框按钮，则为 TRUE;如果选择了组合框按钮，则为 TRUE。否则，FALSE。

### <a name="return-value"></a>返回值

组合框按钮的宽度（以像素为单位）。

## <a name="cmfctoolbarcomboboxbuttononglobalfontschanged"></a><a name="onglobalfontschanged"></a>CMFCToolBarCombox按钮：：在全局字体上更改

当应用程序字体更改时，框架调用以设置组合框按钮字体。

```
virtual void OnGlobalFontsChanged();
```

## <a name="cmfctoolbarcomboboxbuttononmove"></a><a name="onmove"></a>CMFCToolBarCombox按钮：：移动

框架调用以在父工具栏移动时更改组合框按钮的位置。

```
virtual void OnMove();
```

## <a name="cmfctoolbarcomboboxbuttononshow"></a><a name="onshow"></a>CMFCToolBarCombox按钮：：上展

当隐藏或显示组合框按钮时，由框架调用。

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>参数

*b显示*<br/>
[在]是隐藏还是显示组合框按钮。

## <a name="cmfctoolbarcomboboxbuttononsize"></a><a name="onsize"></a>CMFCToolBarCombox按钮：：打开尺寸

框架调用以在父工具栏更改大小时更改组合框按钮的大小。

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>参数

*iSize*<br/>
[在]组合框按钮的新宽度。

## <a name="cmfctoolbarcomboboxbuttononupdatetooltip"></a><a name="onupdatetooltip"></a>CMFCToolBarCombox按钮：：更新工具提示

当用户更改组合框按钮的工具提示时，由框架调用。

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>参数

*pwnd 父级*<br/>
[在]指向组合框按钮的父窗口。

*iButtonIndex*<br/>
[在]组合框按钮的 ID。

*wndToolTip*<br/>
[在]要与组合框按钮关联的工具提示。

*Str*<br/>
[在]工具提示文本。

### <a name="return-value"></a>返回值

如果方法处理事件，则为 TRUE;如果方法处理事件，则为 TRUE。否则，FALSE。

## <a name="cmfctoolbarcomboboxbuttonremoveallitems"></a><a name="removeallitems"></a>CMFCToolBarComBox按钮：：删除所有项目

从列表和编辑框中删除所有项目。

```cpp
void RemoveAllItems();
```

### <a name="remarks"></a>备注

从列表框中删除所有项目，并编辑组合框控件。

## <a name="cmfctoolbarcomboboxbuttonselectitem"></a><a name="selectitem"></a>CMFCToolBarComBox按钮：：选择项目

在列表框中选择项目。

```
BOOL SelectItem(
    int iIndex,
    BOOL bNotify=TRUE);

BOOL SelectItem(DWORD_PTR dwData);
BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>参数

*iIndex*<br/>
[在]列表框中项的零基索引。

*b 通知*<br/>
[在]TRUE 以通知所选内容的组合框按钮;否则 FALSE。

*dwData*<br/>
[在]与列表框中的项目关联的数据。

*lpszText*<br/>
[在]列表框中项的文本。

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfctoolbarcomboboxbuttonselectitemall"></a><a name="selectitemall"></a>CMFCToolBarComBox按钮：：选择项目全部

在具有指定命令 ID 的组合框按钮的列表框中选择项目。

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

*乌伊Cmd*<br/>
[在]包含列表框的组合框按钮的命令 ID。

*iIndex*<br/>
[在]列表框中项的零基索引。 值 -1 删除列表框中的任何当前选择并清除编辑框。

*dwData*<br/>
[在]列表框中项的数据。

*lpszText*<br/>
[在]列表框中项的文本。

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

## <a name="cmfctoolbarcomboboxbuttonserialize"></a><a name="serialize"></a>CMFCToolBarComBox按钮：序列化

从存档中读取此对象或将其写入存档。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>参数

*ar*<br/>
[进出]要`CArchive`序列化的对象。

### <a name="remarks"></a>备注

对象中的`CArchive`设置确定此方法是读取还是写入存档。

## <a name="cmfctoolbarcomboboxbuttonsetaccdata"></a><a name="setaccdata"></a>CMFCToolBarComBox按钮：：设置ACC数据

使用组合框按钮`CAccessibilityData`中的辅助功能数据填充指定对象。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>参数

*p 父级*<br/>
[在]组合框按钮的父窗口。

*数据*<br/>
[出]从`CAccessibilityData`组合框按钮接收辅助功能数据的对象。

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE;否则 FALSE。

## <a name="cmfctoolbarcomboboxbuttonsetcentervert"></a><a name="setcentervert"></a>CMFCToolBarComBox按钮：：设置中心

设置应用程序中组合框按钮的垂直位置。

```
static void SetCenterVert(BOOL bCenterVert=TRUE);
```

### <a name="parameters"></a>参数

*b中心弗特*<br/>
[在]TRUE 以将组合框按钮居中以工具栏为中心;FALSE 将组合框按钮对齐到工具栏顶部。

### <a name="remarks"></a>备注

默认情况下，组合框按钮与顶部对齐。

## <a name="cmfctoolbarcomboboxbuttonsetcontextmenuid"></a><a name="setcontextmenuid"></a>CMFCToolBarComBox按钮：：设置上下文菜单ID

设置组合框按钮的快捷菜单资源 ID。

```cpp
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>参数

*uiResID*<br/>
[在]快捷菜单资源 ID。

## <a name="cmfctoolbarcomboboxbuttonsetdropdownheight"></a><a name="setdropdownheight"></a>CMFCToolBarCombox按钮：：设置下拉高度

下下列表框时设置其高度。

```cpp
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>参数

*nHeight*<br/>
[在]列表框的高度（以像素为单位）。

### <a name="remarks"></a>备注

默认高度为 150 像素。

## <a name="cmfctoolbarcomboboxbuttonsetflatmode"></a><a name="setflatmode"></a>CMFCToolBarComBox按钮：：设置平模式

设置应用程序中组合框按钮的平面样式外观。

```
static void SetFlatMode(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>参数

*bFlat*<br/>
[在]对于平面样式的外观，TRUE;否则 FALSE。

### <a name="remarks"></a>备注

组合框按钮的默认平面样式为 FALSE。

## <a name="cmfctoolbarcomboboxbuttonsetstyle"></a><a name="setstyle"></a>CMFCToolBarComBox按钮：：设置样式

设置组合框按钮的指定样式，如果未禁用控件，则重新绘制该控件。

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>参数

*nStyle*<br/>
[在]工具栏样式的位组合 （OR）。

### <a name="remarks"></a>备注

有关工具栏按钮样式的列表，请参阅[工具栏控件样式](../../mfc/reference/toolbar-control-styles.md)

## <a name="cmfctoolbarcomboboxbuttonsettext"></a><a name="settext"></a>CMFCToolBarComBox按钮：：设置文本

在组合框按钮的编辑框中设置文本。

```cpp
void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>参数

*lpszText*<br/>
[在]指向包含编辑框文本的字符串的指针。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFC工具栏按钮类](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CComboBox 类](../../mfc/reference/ccombobox-class.md)<br/>
[CMFC工具栏：更换按钮](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[演练：将控件置于工具栏上](../../mfc/walkthrough-putting-controls-on-toolbars.md)
