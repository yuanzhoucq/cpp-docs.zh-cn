---
title: CMFCShellTreeCtrl 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCShellTreeCtrl
- AFXSHELLTREECTRL/CMFCShellTreeCtrl
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::EnableShellContextMenu
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetFlags
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetItemPath
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetRelatedList
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnChildNotify
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnGetItemIcon
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnGetItemText
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::Refresh
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SelectPath
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SetFlags
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SetRelatedList
dev_langs:
- C++
helpviewer_keywords:
- CMFCShellTreeCtrl [MFC], EnableShellContextMenu
- CMFCShellTreeCtrl [MFC], GetFlags
- CMFCShellTreeCtrl [MFC], GetItemPath
- CMFCShellTreeCtrl [MFC], GetRelatedList
- CMFCShellTreeCtrl [MFC], OnChildNotify
- CMFCShellTreeCtrl [MFC], OnGetItemIcon
- CMFCShellTreeCtrl [MFC], OnGetItemText
- CMFCShellTreeCtrl [MFC], Refresh
- CMFCShellTreeCtrl [MFC], SelectPath
- CMFCShellTreeCtrl [MFC], SetFlags
- CMFCShellTreeCtrl [MFC], SetRelatedList
ms.assetid: 3d1da715-9554-4ed7-968c-055c48146267
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05936d35829c2982e008cf45d3a76f622357f7dc
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077878"
---
# <a name="cmfcshelltreectrl-class"></a>CMFCShellTreeCtrl 类

`CMFCShellTreeCtrl`类用于扩展[CTreeCtrl 类](../../mfc/reference/ctreectrl-class.md)通过显示 Shell 项的层次结构的功能。

有关更多详细信息，请参阅中的源代码**VC\\atlmfc\\src\\mfc**的 Visual Studio 安装文件夹。
## <a name="syntax"></a>语法

```
class CMFCShellTreeCtrl : public CTreeCtrl
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCShellTreeCtrl::EnableShellContextMenu](#enableshellcontextmenu)|启用或禁用的快捷菜单。|
|[CMFCShellTreeCtrl::GetFlags](#getflags)|返回传递给的标志的组合[IShellFolder::EnumObjects](https://msdn.microsoft.com/library/windows/desktop/bb775066)。|
|[CMFCShellTreeCtrl::GetItemPath](#getitempath)|检索项的路径。|
|[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)|返回一个指向[CMFCShellListCtrl 类](../../mfc/reference/cmfcshelllistctrl-class.md)与这一起使用的对象`CMFCShellTreeCtrl`对象来创建类似于资源管理器的窗口。|
|[CMFCShellTreeCtrl::OnChildNotify](#onchildnotify)|接收应用于该窗口的通知消息时，将通过此窗口的父窗口调用此成员函数。 (重写[CWnd::OnChildNotify](../../mfc/reference/cwnd-class.md#onchildnotify)。)|
|[CMFCShellTreeCtrl::OnGetItemIcon](#ongetitemicon)||
|[CMFCShellTreeCtrl::OnGetItemText](#ongetitemtext)||
|[CMFCShellTreeCtrl::Refresh](#refresh)|刷新并重新绘制当前`CMFCShellTreeCtrl`对象。|
|[CMFCShellTreeCtrl::SelectPath](#selectpath)|选择相应的树控件项基于提供的 PIDL 或字符串路径。|
|[CMFCShellTreeCtrl::SetFlags](#setflags)|设置标志以筛选器树中上下文 (类似于使用的标志`IShellFolder::EnumObjects`)。|
|[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)|设置当前之间的关系`CMFCShellTreeCtrl`对象和一个`CMFCShellListCtrl`对象。|

## <a name="remarks"></a>备注

此类扩展`CTreeCtrl`通过启用程序以将 Windows Shell 项包含在树中的类。 此类可以与之关联`CMFCShellListCtrl`对象来创建完整的资源管理器窗口。 然后，在树中选择一项将显示 Windows Shell 项的列表的关联列表中。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)

`CMFCShellTreeCtrl`

## <a name="requirements"></a>要求

**标头：** afxshelltreeCtrl.h

## <a name="example"></a>示例

下面的示例演示如何创建 `CMFCShellTreeCtrl` 类的对象。 此代码片段属于[资源管理器示例](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]

##  <a name="enableshellcontextmenu"></a>  CMFCShellTreeCtrl::EnableShellContextMenu

启用的快捷菜单。

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
[in]一个布尔值，指定是否启用的快捷菜单。

##  <a name="getflags"></a>  CMFCShellTreeCtrl::GetFlags

返回为设置的标志[CMFCShellTreeCtrl 类](../../mfc/reference/cmfcshelltreectrl-class.md)对象。

```
DWORD GetFlags() const;
```

### <a name="return-value"></a>返回值

设置指定标志的组合当前为 DWORD 值。

### <a name="remarks"></a>备注

设置的标志`CMFCShellTreeCtrl`发送到方法[IShellFolder::EnumObjects](https://msdn.microsoft.com/library/windows/desktop/bb775066)每当刷新对象。 你可以使用的标志[CMFCShellTreeCtrl::SetFlags](#setflags)方法。

##  <a name="getitempath"></a>  CMFCShellTreeCtrl::GetItemPath

检索中的项的路径[CMFCShellTreeCtrl 类](../../mfc/reference/cmfcshelltreectrl-class.md)对象。

```
BOOL GetItemPath(
    CString& strPath,
    HTREEITEM htreeItem = NULL) const;
```

### <a name="parameters"></a>参数

*strPath*<br/>
[out]对字符串参数的引用。 该方法将写入此参数的项的路径。

*htreeItem*<br/>
[in]方法检索此树控件项的路径。

### <a name="return-value"></a>返回值

如果成功，则非零值否则为 0。

### <a name="remarks"></a>备注

如果此方法失败， *strPath*包含空字符串。

如果未指定*hTreeItem*，此方法尝试获取当前选定项的字符串。 如果未不选择任何项并*hTreeItem*为 NULL，此方法将失败。

##  <a name="getrelatedlist"></a>  CMFCShellTreeCtrl::GetRelatedList

返回一个指向[CMFCShellListCtrl 类](../../mfc/reference/cmfcshelllistctrl-class.md)对象，它是与此相关联[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)对象。

```
CMFCShellListCtrl* GetRelatedList() const;
```

### <a name="return-value"></a>返回值

一个指向`CMFCShellListCtrl`与此树控件对象相关联的对象。

### <a name="remarks"></a>备注

通过使用`CMFCShellListCtrl`对象一起使用`CMFCShellTreeCtrl`对象，可以创建一个类似于资源管理器的窗口。 使用方法[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)要关联两个类。 它们相关联后，框架会自动更新`CMFCShellListCtrl`如果在所选内容`CMFCShellTreeCtrl`更改。

##  <a name="onchildnotify"></a>  CMFCShellTreeCtrl::OnChildNotify

```
virtual BOOL OnChildNotify(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* pLResult);
```

### <a name="parameters"></a>参数

[in]*消息*<br/>
[in]*wParam*<br/>
[in]*lParam*<br/>
[in]*pLResult*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="ongetitemicon"></a>  CMFCShellTreeCtrl::OnGetItemIcon

```
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,
    BOOL bSelected);
```

### <a name="parameters"></a>参数

[in]*pItem*<br/>
[in]*bSelected*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="ongetitemtext"></a>  CMFCShellTreeCtrl::OnGetItemText

```
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>参数

[in]*pItem*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="refresh"></a>  CMFCShellTreeCtrl::Refresh

刷新并重新绘制[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)。

```
void Refresh();
```

### <a name="remarks"></a>备注

调用此方法来刷新中显示的项的层次结构`CMFCShellTreeCtrl`。

##  <a name="selectpath"></a>  CMFCShellTreeCtrl::SelectPath

选择中的项[CMFCShellTreeCtrl 类](../../mfc/reference/cmfcshelltreectrl-class.md)基于提供的路径。

```
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```

### <a name="parameters"></a>参数

*lpszPath*<br/>
[in]一个字符串，指定项的路径。

*lpidl*<br/>
[in]指定的项 PIDL

### <a name="return-value"></a>返回值

如果成功，则为 S_OK否则为 E_FAIL。

##  <a name="setflags"></a>  CMFCShellTreeCtrl::SetFlags

设置标志以筛选器树中上下文。

```
void SetFlags(
    DWORD dwFlags,
    BOOL bRefresh = TRUE);
```

### <a name="parameters"></a>参数

*dwFlags*<br/>
[in]要设置的标志。

*bRefresh*<br/>
[in]一个布尔值，指定是否`CMFCShellTreeCtrl`应立即进行刷新。

### <a name="remarks"></a>备注

`CMFCShellTreeCtrl`传递所有标志设置为[IShellFolder::EnumObjects](https://msdn.microsoft.com/library/windows/desktop/bb775066)。 有关不同的标志的值的详细信息，请参阅[IShellFolder::EnumObjects](https://msdn.microsoft.com/library/windows/desktop/bb775066)。

##  <a name="setrelatedlist"></a>  CMFCShellTreeCtrl::SetRelatedList

将相关联[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)对象。

```
void SetRelatedList(CMFCShellListCtrl* pShellList);
```

### <a name="parameters"></a>参数

*pShellList*<br/>
[in]一个指向`CMFCShellListCtrl`对象。

### <a name="remarks"></a>备注

此方法将相关联`CMFCShellListCtrl`与`CMFCShellTreeCtrl`。 这些对象可能显示为一个类似于资源管理器的窗口： 如果用户选择中的对象`CMFCShellTreeCtrl`、 关联中的项`CMFCShellListCtrl`将自动更新。

使用方法[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)检索`CMFCShellListCtrl`与关联`CMFCShellTreeCtrl`。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CTreeCtrl 类](../../mfc/reference/ctreectrl-class.md)<br/>
[CMFCShellListCtrl 类](../../mfc/reference/cmfcshelllistctrl-class.md)
