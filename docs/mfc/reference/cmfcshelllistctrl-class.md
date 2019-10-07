---
title: CMFCShellListCtrl 类
ms.date: 11/04/2016
f1_keywords:
- CMFCShellListCtrl
- AFXSHELLLISTCTRL/CMFCShellListCtrl
- AFXSHELLLISTCTRL/CMFCShellListCtrl::DisplayFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::DisplayParentFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::EnableShellContextMenu
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentFolderName
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentItemIdList
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentShellFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetItemPath
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetItemTypes
- AFXSHELLLISTCTRL/CMFCShellListCtrl::IsDesktop
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnCompareItems
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnFormatFileDate
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnFormatFileSize
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnGetItemIcon
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnGetItemText
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnSetColumns
- AFXSHELLLISTCTRL/CMFCShellListCtrl::Refresh
- AFXSHELLLISTCTRL/CMFCShellListCtrl::SetItemTypes
helpviewer_keywords:
- CMFCShellListCtrl [MFC], DisplayFolder
- CMFCShellListCtrl [MFC], DisplayParentFolder
- CMFCShellListCtrl [MFC], EnableShellContextMenu
- CMFCShellListCtrl [MFC], GetCurrentFolder
- CMFCShellListCtrl [MFC], GetCurrentFolderName
- CMFCShellListCtrl [MFC], GetCurrentItemIdList
- CMFCShellListCtrl [MFC], GetCurrentShellFolder
- CMFCShellListCtrl [MFC], GetItemPath
- CMFCShellListCtrl [MFC], GetItemTypes
- CMFCShellListCtrl [MFC], IsDesktop
- CMFCShellListCtrl [MFC], OnCompareItems
- CMFCShellListCtrl [MFC], OnFormatFileDate
- CMFCShellListCtrl [MFC], OnFormatFileSize
- CMFCShellListCtrl [MFC], OnGetItemIcon
- CMFCShellListCtrl [MFC], OnGetItemText
- CMFCShellListCtrl [MFC], OnSetColumns
- CMFCShellListCtrl [MFC], Refresh
- CMFCShellListCtrl [MFC], SetItemTypes
ms.assetid: ad472958-5586-4c50-aadf-1844c30bf6e7
ms.openlocfilehash: 02d4883c6b5445515d891c5e76ccf10b6bb35bba
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504924"
---
# <a name="cmfcshelllistctrl-class"></a>CMFCShellListCtrl 类

`CMFCShellListCtrl`类提供 Windows 列表控件功能, 并通过包含显示 shell 项列表的功能进行扩展。

## <a name="syntax"></a>语法

```
class CMFCShellListCtrl : public CMFCListCtrl
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCShellListCtrl::DisplayFolder](#displayfolder)|显示所提供文件夹中包含的项的列表。|
|[CMFCShellListCtrl::DisplayParentFolder](#displayparentfolder)|显示作为当前显示文件夹的父文件夹的文件夹中包含的项的列表。|
|[CMFCShellListCtrl::EnableShellContextMenu](#enableshellcontextmenu)|启用或禁用快捷菜单。|
|[CMFCShellListCtrl::GetCurrentFolder](#getcurrentfolder)|检索当前文件夹的路径。|
|[CMFCShellListCtrl::GetCurrentFolderName](#getcurrentfoldername)|检索当前文件夹的名称。|
|[CMFCShellListCtrl::GetCurrentItemIdList](#getcurrentitemidlist)|返回当前列表控件项的 PIDL。|
|[CMFCShellListCtrl::GetCurrentShellFolder](#getcurrentshellfolder)|返回指向当前 Shell 文件夹的指针。|
|[CMFCShellListCtrl::GetItemPath](#getitempath)|返回项的文本路径。|
|[CMFCShellListCtrl::GetItemTypes](#getitemtypes)|返回列表控件显示的 Shell 项类型。|
|[CMFCShellListCtrl::IsDesktop](#isdesktop)|检查当前选择的文件夹是否为 "桌面" 文件夹。|
|[CMFCShellListCtrl::OnCompareItems](#oncompareitems)|框架在比较两个项时调用此方法。 (重写[CMFCListCtrl:: OnCompareItems](../../mfc/reference/cmfclistctrl-class.md#oncompareitems)。)|
|[CMFCShellListCtrl::OnFormatFileDate](#onformatfiledate)|当框架检索列表控件显示的文件日期时调用。|
|[CMFCShellListCtrl::OnFormatFileSize](#onformatfilesize)|在框架转换列表控件的文件大小时调用。|
|[CMFCShellListCtrl::OnGetItemIcon](#ongetitemicon)|在框架检索列表控件项的图标时调用。|
|[CMFCShellListCtrl::OnGetItemText](#ongetitemtext)|当框架转换列表控件项的文本时调用。|
|[CMFCShellListCtrl::OnSetColumns](#onsetcolumns)|在设置列的名称时由框架调用。|
|[CMFCShellListCtrl::Refresh](#refresh)|刷新并重新绘制列表控件。|
|[CMFCShellListCtrl::SetItemTypes](#setitemtypes)|设置列表控件显示的项的类型。|

## <a name="remarks"></a>备注

类通过使程序能够列出 Windows shell 项来扩展[CMFCListCtrl 类](../../mfc/reference/cmfclistctrl-class.md)的功能。 `CMFCShellListCtrl` 所使用的显示格式类似于 "资源管理器" 窗口的列表视图。

[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)对象可以与`CMFCShellListCtrl`对象相关联, 以创建完整的资源管理器窗口。 然后, 在中`CMFCShellTreeCtrl`选择一项将`CMFCShellListCtrl`导致对象列出选定项的内容。

## <a name="example"></a>示例

下面的示例演示如何创建`CMFCShellListCtrl`类的对象以及如何显示当前显示文件夹的父文件夹。 此代码片段是[资源管理器示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_Explorer#1](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#2](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_2.cpp)]
[!code-cpp[NVC_MFC_Explorer#3](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_3.cpp)]

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

`CMFCShellListCtrl`

## <a name="requirements"></a>要求

**标头:** afxshelllistCtrl

##  <a name="displayfolder"></a>  CMFCShellListCtrl::DisplayFolder

显示所提供文件夹中包含的项的列表。

```
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```

### <a name="parameters"></a>参数

*lpszPath*<br/>
中包含文件夹路径的字符串。

*lpItemInfo*<br/>
中指向`LPAFX_SHELLITEMINFO`结构的指针, 该结构描述要显示的文件夹。

### <a name="return-value"></a>返回值

如果成功, 则为 S_OK;否则为 E_FAIL。

##  <a name="displayparentfolder"></a>  CMFCShellListCtrl::DisplayParentFolder

更新[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象以显示当前显示文件夹的父文件夹。

```
virtual HRESULT DisplayParentFolder();
```

### <a name="return-value"></a>返回值

如果成功, 则为 S_OK;否则为 E_FAIL。

##  <a name="enableshellcontextmenu"></a>CMFCShellListCtrl::EnableShellContextMenu

启用快捷菜单。

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
中一个布尔值, 该值指定框架是否启用快捷菜单。

##  <a name="getcurrentfolder"></a>CMFCShellListCtrl::GetCurrentFolder

检索[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象中当前选定文件夹的路径。

```
BOOL GetCurrentFolder(CString& strPath) const;
```

### <a name="parameters"></a>参数

*strPath*<br/>
弄对字符串参数的引用, 其中方法将写入路径。

### <a name="return-value"></a>返回值

如果成功, 则为非零值;否则为0。

### <a name="remarks"></a>备注

如果中`CMFCShellListCtrl`未选择任何文件夹, 则此方法将失败。

##  <a name="getcurrentfoldername"></a>CMFCShellListCtrl::GetCurrentFolderName

检索[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象中当前选定文件夹的名称。

```
BOOL GetCurrentFolderName(CString& strName) const;
```

### <a name="parameters"></a>参数

*strName*<br/>
弄对字符串参数的引用, 其中方法会写入名称。

### <a name="return-value"></a>返回值

如果成功, 则为非零值;否则为0。

### <a name="remarks"></a>备注

如果中`CMFCShellListCtrl`未选择任何文件夹, 则此方法将失败。

##  <a name="getcurrentitemidlist"></a>CMFCShellListCtrl::GetCurrentItemIdList

返回当前选定项的 PIDL。

```
LPITEMIDLIST GetCurrentItemIdList() const;
```

### <a name="return-value"></a>返回值

当前项的 PIDL。

##  <a name="getcurrentshellfolder"></a>CMFCShellListCtrl::GetCurrentShellFolder

获取一个指针, 该指针指向[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象中当前选定的项。

```
const IShellFolder* GetCurrentShellFolder() const;
```

### <a name="return-value"></a>返回值

指向所选对象的[IShellFolder 接口](/windows/win32/api/shobjidl_core/nn-shobjidl_core-ishellfolder)的指针。

### <a name="remarks"></a>备注

如果当前未选择任何对象, 则此方法返回 NULL。

##  <a name="getitempath"></a>CMFCShellListCtrl::GetItemPath

检索项的路径。

```
BOOL GetItemPath(
    CString& strPath,
    int iItem) const;
```

### <a name="parameters"></a>参数

*strPath*<br/>
弄对接收路径的字符串的引用。

*iItem*<br/>
中列表项的索引。

### <a name="return-value"></a>返回值

如果成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

*IItem*提供的索引基于[CMFCShellListCtrl 类](../../mfc/reference/cmfcshelllistctrl-class.md)对象当前显示的项。

##  <a name="getitemtypes"></a>CMFCShellListCtrl::GetItemTypes

返回由[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象显示的项的类型。

```
SHCONTF GetItemTypes() const;
```

### <a name="return-value"></a>返回值

一个[SHCONTF](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf)值, 该值包含中`CMFCShellListCtrl`列出的项的类型。

### <a name="remarks"></a>备注

若要设置中`CMFCShellListCtrl`列出的项的类型, 请调用[CMFCShellListCtrl:: SetItemTypes](#setitemtypes)。

##  <a name="isdesktop"></a>CMFCShellListCtrl::IsDesktop

确定[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象中显示的文件夹是否为 "桌面" 文件夹。

```
BOOL IsDesktop() const;
```

### <a name="return-value"></a>返回值

如果显示的文件夹是桌面文件夹, 则为 TRUE;否则为 FALSE。

##  <a name="oncompareitems"></a>CMFCShellListCtrl::OnCompareItems

有关更多详细信息, 请参阅位于 Visual Studio 安装的**VC\\atlmfc\\src\\mfc**文件夹中的源代码。

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>参数

[in] *lParam1*<br/>
[in] *lParam2*<br/>
中*iColumn*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="onformatfiledate"></a>CMFCShellListCtrl::OnFormatFileDate

当框架必须将与对象关联的日期转换为字符串时, 框架会调用此方法。

```
virtual void OnFormatFileDate(
    const CTime& tmFile,
    CString& str);
```

### <a name="parameters"></a>参数

*tmFile*<br/>
中与文件关联的日期。

*str*<br/>
弄一个包含格式化文件日期的字符串。

### <a name="remarks"></a>备注

当[CMFCShellListCtrl 类](../../mfc/reference/cmfcshelllistctrl-class.md)对象显示与文件关联的日期时, 它必须将该日期转换为字符串格式。 `CMFCShellListCtrl`使用此方法进行该转换。 默认情况下, 此方法使用当前区域设置将日期格式设置为字符串。

##  <a name="onformatfilesize"></a>CMFCShellListCtrl::OnFormatFileSize

框架在将对象的大小转换为字符串时调用此方法。

```
virtual void OnFormatFileSize(
    long lFileSize,
    CString& str);
```

### <a name="parameters"></a>参数

*lFileSize*<br/>
中框架将显示的文件的大小。

*str*<br/>
弄一个包含格式化文件大小的字符串。

### <a name="remarks"></a>备注

当[CMFCShellListCtrl 类](../../mfc/reference/cmfcshelllistctrl-class.md)对象需要显示文件的大小时, 需要将文件大小转换为字符串格式。 `CMFCShellListCtrl`使用此方法进行该转换。 默认情况下, 此方法将文件大小从字节转换为 kb, 并使用当前区域设置将大小设置为字符串格式。

##  <a name="ongetitemicon"></a>CMFCShellListCtrl::OnGetItemIcon

框架调用此方法来检索与 shell 列表项关联的图标。

```
virtual int OnGetItemIcon(
    int iItem,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>参数

*iItem*<br/>
中项索引。

*pItem*<br/>
中描述该项的 LPAFX_SHELLITEMINFO 参数。

### <a name="return-value"></a>返回值

如果成功, 则为图标图像的索引;如果函数失败, 则为-1。

### <a name="remarks"></a>备注

图标图像索引基于 "系统映像" 列表。

默认情况下, 此方法依赖于*pItem*参数。 默认实现中不使用*iItem*的值。 您可以使用*iItem*来实现自定义行为。

##  <a name="ongetitemtext"></a>  CMFCShellListCtrl::OnGetItemText

当框架必须检索 shell 项的文本时, 框架会调用此方法。

```
virtual CString OnGetItemText(
    int iItem,
    int iColumn,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>参数

*iItem*<br/>
中项索引。

*iColumn*<br/>
中相关列。

*pItem*<br/>
中描述该项的 LPAFX_SHELLITEMINFO 参数。

### <a name="return-value"></a>返回值

一个`CString` , 其中包含与项关联的文本。

### <a name="remarks"></a>备注

对象中的`CMFCShellListCtrl`每一项都有一个或多个列中的文本。 当框架调用此方法时, 它将指定所需的列。 如果手动调用此函数, 则还必须指定所需的列。

默认情况下, 此方法依赖于*pItem*参数来确定要处理的项。 默认实现中不使用*iItem*的值。

##  <a name="onsetcolumns"></a>CMFCShellListCtrl::OnSetColumns

框架在设置列的名称时调用此方法。

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>备注

默认情况下, 框架在`CMFCShellListCtrl`对象中创建四个列。 这些列的名称为 "**名称**"、"**大小**"、"**类型**" 和 "**已修改**"。 您可以重写此方法以自定义列数和列名称。

##  <a name="refresh"></a>  CMFCShellListCtrl::Refresh

刷新并重新绘制[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象。

```
virtual HRESULT Refresh();
```

### <a name="return-value"></a>返回值

`S_OK`如果成功, 则为;否则为错误值。

### <a name="remarks"></a>备注

调用此方法可刷新由`CMFCShellListCtrl`对象显示的项的列表。

##  <a name="setitemtypes"></a>  CMFCShellListCtrl::SetItemTypes

设置[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象中列出的项的类型。

```
void SetItemTypes(SHCONTF nTypes);
```

### <a name="parameters"></a>参数

*nTypes*<br/>
中`CMFCShellListCtrl`对象支持的项类型的列表。

### <a name="remarks"></a>备注

有关项类型列表的详细信息, 请参阅[SHCONTF](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf)。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCListCtrl 类](../../mfc/reference/cmfclistctrl-class.md)<br/>
[CMFCShellTreeCtrl 类](../../mfc/reference/cmfcshelltreectrl-class.md)
