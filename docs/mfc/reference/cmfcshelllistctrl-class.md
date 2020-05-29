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
ms.openlocfilehash: 445556535217b0887a02227a0773c287911922a2
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753484"
---
# <a name="cmfcshelllistctrl-class"></a>CMFCShellListCtrl 类

该`CMFCShellListCtrl`类提供 Windows 列表控件功能，并通过包括显示 shell 项列表的功能来扩展它。

## <a name="syntax"></a>语法

```
class CMFCShellListCtrl : public CMFCListCtrl
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCShellListCtrl：:DisplayFolder](#displayfolder)|显示提供的文件夹中的项目列表。|
|[CMFCShellListCtrl：:D播放父文件夹](#displayparentfolder)|显示当前显示的文件夹的父级文件夹中包含的项目列表。|
|[CMFCShellListCtrl：：启用ShellContextMenu](#enableshellcontextmenu)|启用或禁用快捷菜单。|
|[CMFCShelllistCtrl：：获取当前文件夹](#getcurrentfolder)|检索当前文件夹的路径。|
|[CMFCShelllistCtrl：：获取当前文件夹名称](#getcurrentfoldername)|检索当前文件夹的名称。|
|[CMFCShelllistCtrl：获取当前项目 Id 列表](#getcurrentitemidlist)|返回当前列表控制项的 PIDL。|
|[CMFCShelllistCtrl：：获取当前舍尔贝](#getcurrentshellfolder)|返回指向当前 Shell 文件夹的指针。|
|[CMFCShelllistCtrl：获取项目路径](#getitempath)|返回项的文本路径。|
|[CMFCShelllistCtrl：获取项目类型](#getitemtypes)|返回列表控件显示的 Shell 项类型。|
|[CMFCShelllistCtrl：是桌面](#isdesktop)|检查当前选择的文件夹是否为桌面文件夹。|
|[CMFCShelllistctrl：：上比较项目](#oncompareitems)|框架在比较两个项目时调用此方法。 （覆盖[CMFCListCtrl：在比较项目](../../mfc/reference/cmfclistctrl-class.md#oncompareitems).）|
|[CMFCShelllistctrl：在格式文件日期](#onformatfiledate)|当框架检索列表控件显示的文件日期时调用。|
|[CMFCShelllistCtrl：在格式文件大小](#onformatfilesize)|当框架转换列表控件的文件大小时调用。|
|[CMFCShelllistctrl：ongetItemicon](#ongetitemicon)|当框架检索列表控件项的图标时调用。|
|[CMFCShelllistctrl：：在获取项目文本](#ongetitemtext)|当框架转换列表控件项的文本时调用。|
|[CMFCShelllistctrl：：打开列](#onsetcolumns)|框架在设置列的名称时调用它。|
|[CMFCShellListCtrl：：刷新](#refresh)|刷新并重新绘制列表控件。|
|[CMFCShelllistCtrl：：设置项目类型](#setitemtypes)|设置列表控件显示的项的类型。|

## <a name="remarks"></a>备注

该`CMFCShellListCtrl`类通过使程序能够列出 Windows 外壳项来扩展[CMFCListCtrl 类](../../mfc/reference/cmfclistctrl-class.md)的功能。 使用的显示格式类似于资源管理器窗口的列表视图。

[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)对象可以与对象关联以创建`CMFCShellListCtrl`完整的资源管理器窗口。 然后，在 中选择中的项`CMFCShellTreeCtrl`将导致`CMFCShellListCtrl`对象列出所选项的内容。

## <a name="example"></a>示例

下面的示例演示如何创建`CMFCShellListCtrl`类的对象以及如何显示当前显示的文件夹的父文件夹。 此代码段是[资源管理器示例](../../overview/visual-cpp-samples.md)的一部分。

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

**标题：** afxshelllistCtrl.h

## <a name="cmfcshelllistctrldisplayfolder"></a><a name="displayfolder"></a>CMFCShellListCtrl：:DisplayFolder

显示提供的文件夹中的项目列表。

```
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```

### <a name="parameters"></a>参数

*lpszPath*<br/>
[在]包含文件夹路径的字符串。

*lpItemInfo*<br/>
[在]指向要显示的`LPAFX_SHELLITEMINFO`文件夹的结构的指针。

### <a name="return-value"></a>返回值

S_OK如果成功;否则E_FAIL。

## <a name="cmfcshelllistctrldisplayparentfolder"></a><a name="displayparentfolder"></a>CMFCShellListCtrl：:D播放父文件夹

更新[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象以显示当前显示的文件夹的父文件夹。

```
virtual HRESULT DisplayParentFolder();
```

### <a name="return-value"></a>返回值

S_OK如果成功;否则E_FAIL。

## <a name="cmfcshelllistctrlenableshellcontextmenu"></a><a name="enableshellcontextmenu"></a>CMFCShellListCtrl：：启用ShellContextMenu

启用快捷菜单。

```cpp
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
[在]指定框架是否启用快捷菜单的布尔。

## <a name="cmfcshelllistctrlgetcurrentfolder"></a><a name="getcurrentfolder"></a>CMFCShelllistCtrl：：获取当前文件夹

检索[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象中当前选定文件夹的路径。

```
BOOL GetCurrentFolder(CString& strPath) const;
```

### <a name="parameters"></a>参数

*斯特路径*<br/>
[出]对字符串参数的引用，该方法在其中写入路径。

### <a name="return-value"></a>返回值

如果成功，则非零;0 否则。

### <a name="remarks"></a>备注

如果在 中未选择文件夹，`CMFCShellListCtrl`则此方法将失败。

## <a name="cmfcshelllistctrlgetcurrentfoldername"></a><a name="getcurrentfoldername"></a>CMFCShelllistCtrl：：获取当前文件夹名称

检索[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象中当前选定的文件夹的名称。

```
BOOL GetCurrentFolderName(CString& strName) const;
```

### <a name="parameters"></a>参数

*strName*<br/>
[出]对字符串参数的引用，该方法在其中写入名称。

### <a name="return-value"></a>返回值

如果成功，则非零;0 否则。

### <a name="remarks"></a>备注

如果在 中未选择文件夹，`CMFCShellListCtrl`则此方法将失败。

## <a name="cmfcshelllistctrlgetcurrentitemidlist"></a><a name="getcurrentitemidlist"></a>CMFCShelllistCtrl：获取当前项目 Id 列表

返回当前选定项的 PIDL。

```
LPITEMIDLIST GetCurrentItemIdList() const;
```

### <a name="return-value"></a>返回值

当前项的 PIDL。

## <a name="cmfcshelllistctrlgetcurrentshellfolder"></a><a name="getcurrentshellfolder"></a>CMFCShelllistCtrl：：获取当前舍尔贝

获取指向[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象中当前选定项的指针。

```
const IShellFolder* GetCurrentShellFolder() const;
```

### <a name="return-value"></a>返回值

指向所选对象的[IShellFolder 接口](/windows/win32/api/shobjidl_core/nn-shobjidl_core-ishellfolder)的指针。

### <a name="remarks"></a>备注

如果当前未选择任何对象，此方法将返回 NULL。

## <a name="cmfcshelllistctrlgetitempath"></a><a name="getitempath"></a>CMFCShelllistCtrl：获取项目路径

检索项目的路径。

```
BOOL GetItemPath(
    CString& strPath,
    int iItem) const;
```

### <a name="parameters"></a>参数

*斯特路径*<br/>
[出]对接收路径的字符串的引用。

*iItem*<br/>
[在]列表项的索引。

### <a name="return-value"></a>返回值

如果成功，则为 TRUE;否则。

### <a name="remarks"></a>备注

*iItem*提供的索引基于[CMFCShellListCtrl 类](../../mfc/reference/cmfcshelllistctrl-class.md)对象当前显示的项目。

## <a name="cmfcshelllistctrlgetitemtypes"></a><a name="getitemtypes"></a>CMFCShelllistCtrl：获取项目类型

返回[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象显示的项目类型。

```
SHCONTF GetItemTypes() const;
```

### <a name="return-value"></a>返回值

包含 中列出的项类型的[SHCONTF](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf)值`CMFCShellListCtrl`。

### <a name="remarks"></a>备注

要设置 中`CMFCShellListCtrl`列出的项的类型，请致电[CMFCShellListCtrl：：设置项目类型](#setitemtypes)。

## <a name="cmfcshelllistctrlisdesktop"></a><a name="isdesktop"></a>CMFCShelllistCtrl：是桌面

确定[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象中显示的文件夹是否为桌面文件夹。

```
BOOL IsDesktop() const;
```

### <a name="return-value"></a>返回值

如果显示的文件夹是桌面文件夹，则为 TRUE;如果显示的文件夹是桌面文件夹，则为 TRUE。否则。

## <a name="cmfcshelllistctrloncompareitems"></a><a name="oncompareitems"></a>CMFCShelllistctrl：：上比较项目

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>参数

[在]*lParam1*<br/>
[在]*lParam2*<br/>
[在]*iColumn*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcshelllistctrlonformatfiledate"></a><a name="onformatfiledate"></a>CMFCShelllistctrl：在格式文件日期

当必须将与对象关联的日期转换为字符串时，框架将调用此方法。

```
virtual void OnFormatFileDate(
    const CTime& tmFile,
    CString& str);
```

### <a name="parameters"></a>参数

*tmFile*<br/>
[在]与文件关联的日期。

*Str*<br/>
[出]包含格式化文件日期的字符串。

### <a name="remarks"></a>备注

当[CMFCShellListCtrl 类](../../mfc/reference/cmfcshelllistctrl-class.md)对象显示与文件关联的日期时，它必须将该日期转换为字符串格式。 `CMFCShellListCtrl`使用此方法进行该转换。 默认情况下，此方法使用当前区域设置将日期格式化为字符串。

## <a name="cmfcshelllistctrlonformatfilesize"></a><a name="onformatfilesize"></a>CMFCShelllistCtrl：在格式文件大小

当框架将对象的大小转换为字符串时，它将调用此方法。

```
virtual void OnFormatFileSize(
    long lFileSize,
    CString& str);
```

### <a name="parameters"></a>参数

*l文件尺寸*<br/>
[在]框架将显示的文件的大小。

*Str*<br/>
[出]包含格式化文件大小的字符串。

### <a name="remarks"></a>备注

当[CMFCShellListCtrl 类](../../mfc/reference/cmfcshelllistctrl-class.md)对象需要显示文件的大小时，它需要将文件大小转换为字符串格式。 `CMFCShellListCtrl`使用此方法进行该转换。 默认情况下，此方法将文件大小从字节转换为千字节，然后使用当前区域设置将大小格式化为字符串。

## <a name="cmfcshelllistctrlongetitemicon"></a><a name="ongetitemicon"></a>CMFCShelllistctrl：ongetItemicon

框架调用此方法以检索与 shell 列表项关联的图标。

```
virtual int OnGetItemIcon(
    int iItem,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>参数

*iItem*<br/>
[在]项索引。

*pItem*<br/>
[在]描述项的LPAFX_SHELLITEMINFO参数。

### <a name="return-value"></a>返回值

图标图像的索引（如果成功）;-1 如果函数失败。

### <a name="remarks"></a>备注

图标图像索引基于系统映像列表。

默认情况下，此方法依赖于*pItem*参数。 在默认实现中不使用*iItem*的值。 您可以使用*iItem*实现自定义行为。

## <a name="cmfcshelllistctrlongetitemtext"></a><a name="ongetitemtext"></a>CMFCShelllistctrl：：在获取项目文本

当必须检索 shell 项的文本时，框架将调用此方法。

```
virtual CString OnGetItemText(
    int iItem,
    int iColumn,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>参数

*iItem*<br/>
[在]项索引。

*iColumn*<br/>
[在]感兴趣的列。

*pItem*<br/>
[在]描述项的LPAFX_SHELLITEMINFO参数。

### <a name="return-value"></a>返回值

包含`CString`与项关联的文本的 。

### <a name="remarks"></a>备注

`CMFCShellListCtrl`对象中的每个项在一个或多个列中可能具有文本。 当框架调用此方法时，它指定它感兴趣的列。 如果手动调用此函数，则还必须指定您感兴趣的列。

默认情况下，此方法依赖于*pItem*参数来确定要处理的项。 在默认实现中不使用*iItem*的值。

## <a name="cmfcshelllistctrlonsetcolumns"></a><a name="onsetcolumns"></a>CMFCShelllistctrl：：打开列

框架在设置列的名称时调用此方法。

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>备注

默认情况下，框架在对象中创建四列`CMFCShellListCtrl`。 这些列的名称是**名称**、**大小**、**类型**和**已修改**。 可以重写此方法以自定义列数及其名称。

## <a name="cmfcshelllistctrlrefresh"></a><a name="refresh"></a>CMFCShellListCtrl：：刷新

刷新并重新绘制[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象。

```
virtual HRESULT Refresh();
```

### <a name="return-value"></a>返回值

`S_OK`如果成功;否则是错误值。

### <a name="remarks"></a>备注

调用此方法以刷新`CMFCShellListCtrl`对象显示的项目列表。

## <a name="cmfcshelllistctrlsetitemtypes"></a><a name="setitemtypes"></a>CMFCShelllistCtrl：：设置项目类型

设置[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象中列出的项的类型。

```cpp
void SetItemTypes(SHCONTF nTypes);
```

### <a name="parameters"></a>参数

*n 类型*<br/>
[在]`CMFCShellListCtrl`对象支持的项类型的列表。

### <a name="remarks"></a>备注

有关项类型列表的详细信息，请参阅[SHCONTF](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf)。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCListCtrl 类](../../mfc/reference/cmfclistctrl-class.md)<br/>
[CMFCShellTreeCtrl 类](../../mfc/reference/cmfcshelltreectrl-class.md)
