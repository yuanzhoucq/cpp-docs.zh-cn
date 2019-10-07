---
title: CMFCShellTreeCtrl 类
ms.date: 11/04/2016
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
ms.openlocfilehash: 97136342049a54d45af893962025f01eda4366d4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504910"
---
# <a name="cmfcshelltreectrl-class"></a>CMFCShellTreeCtrl 类

类通过显示 Shell 项的层次结构扩展[CTreeCtrl 类](../../mfc/reference/ctreectrl-class.md)的功能。 `CMFCShellTreeCtrl`

有关更多详细信息, 请参阅位于 Visual Studio 安装的**VC\\atlmfc\\src\\mfc**文件夹中的源代码。
## <a name="syntax"></a>语法

```
class CMFCShellTreeCtrl : public CTreeCtrl
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMFCShellTreeCtrl::EnableShellContextMenu](#enableshellcontextmenu)|启用或禁用快捷菜单。|
|[CMFCShellTreeCtrl::GetFlags](#getflags)|返回传递给[IShellFolder:: EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)的标志的组合。|
|[CMFCShellTreeCtrl::GetItemPath](#getitempath)|检索项的路径。|
|[CMFCShellTreeCtrl::GetRelatedList](#getrelatedlist)|返回一个指向[CMFCShellListCtrl 类](../../mfc/reference/cmfcshelllistctrl-class.md)对象的指针, 该对象与此`CMFCShellTreeCtrl`对象一起用于创建类似资源管理器的窗口。|
|[CMFCShellTreeCtrl::OnChildNotify](#onchildnotify)|此成员函数在收到应用于该窗口的通知消息时由该窗口的父窗口调用。 (重写[CWnd:: OnChildNotify](../../mfc/reference/cwnd-class.md#onchildnotify)。)|
|[CMFCShellTreeCtrl::OnGetItemIcon](#ongetitemicon)||
|[CMFCShellTreeCtrl::OnGetItemText](#ongetitemtext)||
|[CMFCShellTreeCtrl::Refresh](#refresh)|刷新并重新绘制当前`CMFCShellTreeCtrl`对象。|
|[CMFCShellTreeCtrl::SelectPath](#selectpath)|基于所提供的 PIDL 或字符串路径选择适当的树控件项。|
|[CMFCShellTreeCtrl::SetFlags](#setflags)|设置用于筛选树上下文的标志 (类似于使用`IShellFolder::EnumObjects`的标志)。|
|[CMFCShellTreeCtrl::SetRelatedList](#setrelatedlist)|设置当前`CMFCShellTreeCtrl`对象`CMFCShellListCtrl`和对象之间的关系。|

## <a name="remarks"></a>备注

此类通过使`CTreeCtrl`您的程序能够在树中包含 Windows Shell 项来扩展类。 此类可以与`CMFCShellListCtrl`对象相关联, 以创建完整的资源管理器窗口。 然后, 在树中选择一项将在关联列表中显示 Windows Shell 项的列表。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)

`CMFCShellTreeCtrl`

## <a name="requirements"></a>要求

**标头:** afxshelltreeCtrl

## <a name="example"></a>示例

下面的示例演示如何创建 `CMFCShellTreeCtrl` 类的对象。 此代码片段是[资源管理器示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]

##  <a name="enableshellcontextmenu"></a>CMFCShellTreeCtrl::EnableShellContextMenu

启用快捷菜单。

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
中一个布尔值, 指定是否启用快捷菜单。

##  <a name="getflags"></a>CMFCShellTreeCtrl:: GetFlags

返回为[CMFCShellTreeCtrl 类](../../mfc/reference/cmfcshelltreectrl-class.md)对象设置的标志。

```
DWORD GetFlags() const;
```

### <a name="return-value"></a>返回值

一个 DWORD 值, 指定当前设置的标志的组合。

### <a name="remarks"></a>备注

每次刷新对象时`CMFCShellTreeCtrl` , 将在中设置的标志发送到方法[IShellFolder:: EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects) 。 可以用[CMFCShellTreeCtrl:: SetFlags](#setflags)方法更改标志。

##  <a name="getitempath"></a>CMFCShellTreeCtrl::GetItemPath

检索[CMFCShellTreeCtrl 类](../../mfc/reference/cmfcshelltreectrl-class.md)对象中的项的路径。

```
BOOL GetItemPath(
    CString& strPath,
    HTREEITEM htreeItem = NULL) const;
```

### <a name="parameters"></a>参数

*strPath*<br/>
弄对字符串参数的引用。 方法将项的路径写入此参数。

*htreeItem*<br/>
中方法检索此树控件项的路径。

### <a name="return-value"></a>返回值

如果成功, 则为非零值;否则为0。

### <a name="remarks"></a>备注

如果此方法失败, *strPath*将包含空字符串。

如果未指定*hTreeItem*, 则此方法将尝试获取当前选定项的字符串。 如果未选择任何项并且*hTreeItem*为 NULL, 则此方法将失败。

##  <a name="getrelatedlist"></a>CMFCShellTreeCtrl::GetRelatedList

返回一个指向与此[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)对象关联的[CMFCShellListCtrl 类](../../mfc/reference/cmfcshelllistctrl-class.md)对象的指针。

```
CMFCShellListCtrl* GetRelatedList() const;
```

### <a name="return-value"></a>返回值

指向与此树`CMFCShellListCtrl`控件对象关联的对象的指针。

### <a name="remarks"></a>备注

通过将`CMFCShellListCtrl`对象`CMFCShellTreeCtrl`与对象一起使用, 你可以创建类似资源管理器的窗口。 使用方法[CMFCShellTreeCtrl:: SetRelatedList](#setrelatedlist)将两个类关联起来。 关联后, 框架会自动更新`CMFCShellListCtrl` , 前提是`CMFCShellTreeCtrl`更改了中的选定内容。

##  <a name="onchildnotify"></a>CMFCShellTreeCtrl:: OnChildNotify

```
virtual BOOL OnChildNotify(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* pLResult);
```

### <a name="parameters"></a>参数

中*消息*<br/>
[in] *wParam*<br/>
[in] *lParam*<br/>
中*pLResult*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="ongetitemicon"></a>CMFCShellTreeCtrl::OnGetItemIcon

```
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,
    BOOL bSelected);
```

### <a name="parameters"></a>参数

[in] *pItem*<br/>
中*bSelected*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="ongetitemtext"></a>  CMFCShellTreeCtrl::OnGetItemText

```
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>参数

[in] *pItem*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

##  <a name="refresh"></a>  CMFCShellTreeCtrl::Refresh

刷新并重新绘制[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)。

```
void Refresh();
```

### <a name="remarks"></a>备注

调用此方法以刷新中`CMFCShellTreeCtrl`显示的项的层次结构。

##  <a name="selectpath"></a>CMFCShellTreeCtrl::SelectPath

基于所提供的路径, 在[CMFCShellTreeCtrl 类](../../mfc/reference/cmfcshelltreectrl-class.md)中选择一个项。

```
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```

### <a name="parameters"></a>参数

*lpszPath*<br/>
中一个字符串, 指定项的路径。

*lpidl*<br/>
中指定项的 PIDL

### <a name="return-value"></a>返回值

如果成功, 则为 S_OK;否则为 E_FAIL。

##  <a name="setflags"></a>CMFCShellTreeCtrl::SetFlags

设置用于筛选树上下文的标志。

```
void SetFlags(
    DWORD dwFlags,
    BOOL bRefresh = TRUE);
```

### <a name="parameters"></a>参数

*dwFlags*<br/>
中要设置的标志。

*bRefresh*<br/>
中一个布尔值, 指定是否`CMFCShellTreeCtrl`应立即刷新。

### <a name="remarks"></a>备注

将`CMFCShellTreeCtrl`所有 set 标志传递给[IShellFolder:: EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)。 有关不同标志的值的详细信息, 请参阅[IShellFolder:: EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)。

##  <a name="setrelatedlist"></a>CMFCShellTreeCtrl::SetRelatedList

将[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象与[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)对象相关联。

```
void SetRelatedList(CMFCShellListCtrl* pShellList);
```

### <a name="parameters"></a>参数

*pShellList*<br/>
中指向`CMFCShellListCtrl`对象的指针。

### <a name="remarks"></a>备注

此方法将`CMFCShellListCtrl` `CMFCShellTreeCtrl`与相关联。 这些对象可能会显示为类似浏览器的窗口: 如果用户在`CMFCShellTreeCtrl`中选择对象, `CMFCShellListCtrl`将自动更新中的关联项。

使用方法[CMFCShellTreeCtrl:: GetRelatedList](#getrelatedlist)来检索与`CMFCShellListCtrl` `CMFCShellTreeCtrl`关联的。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CTreeCtrl 类](../../mfc/reference/ctreectrl-class.md)<br/>
[CMFCShellListCtrl 类](../../mfc/reference/cmfcshelllistctrl-class.md)
