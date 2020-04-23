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
ms.openlocfilehash: c6f5856e92c2aca1d23ee6a37b99ea9700ea6db0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753440"
---
# <a name="cmfcshelltreectrl-class"></a>CMFCShellTreeCtrl 类

该`CMFCShellTreeCtrl`类通过显示 Shell 项的层次结构来扩展[CTreeCtrl 类](../../mfc/reference/ctreectrl-class.md)功能。

有关详细信息，请参阅位于 Visual Studio 安装的**VC\\\\atlmfc src\\mfc**文件夹中的源代码。

## <a name="syntax"></a>语法

```
class CMFCShellTreeCtrl : public CTreeCtrl
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMFCShellTreeCtrl：：启用ShellContextMenu](#enableshellcontextmenu)|启用或禁用快捷菜单。|
|[CMFCShellTreeCtrl：：获取Flags](#getflags)|返回传递给[IShellFolder：：enum对象](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)的标志组合。|
|[CMFCShellTreeCtrl：获取项目路径](#getitempath)|检索项的路径。|
|[CMFCShellTreeCtrl：获取相关列表](#getrelatedlist)|返回指向[CMFCShellListCtrl 类](../../mfc/reference/cmfcshelllistctrl-class.md)对象的指针，该对象与此`CMFCShellTreeCtrl`对象一起使用以创建类似资源管理器的窗口。|
|[CMFCShelltreectrl：：在儿童通知](#onchildnotify)|当此窗口的父窗口收到应用于此窗口的通知消息时，此成员函数将调用它。 （覆盖[Cwnd：onChildNotify](../../mfc/reference/cwnd-class.md#onchildnotify).）|
|[CMFCShelltreectrl：ongetItemicon](#ongetitemicon)||
|[CMFCShelltreectrl：：在获取项目文本](#ongetitemtext)||
|[CMFC舍尔特里克：：刷新](#refresh)|刷新并重新绘制当前`CMFCShellTreeCtrl`对象。|
|[CMFCShellTreeCtrl：选择路径](#selectpath)|根据提供的 PIDL 或字符串路径选择适当的树控件项。|
|[CMFCShellTreeCtrl：：设置标志](#setflags)|设置标志以筛选树上下文（类似于 使用`IShellFolder::EnumObjects`的标志）。|
|[CMFCShellTreeCtrl：：设置相关列表](#setrelatedlist)|设置当前`CMFCShellTreeCtrl`对象和`CMFCShellListCtrl`对象之间的关系。|

## <a name="remarks"></a>备注

此类通过使程序`CTreeCtrl`在树中包括 Windows Shell 项来扩展类。 类可以与对象关联以创建`CMFCShellListCtrl`完整的资源管理器窗口。 然后，在树中选择项目将在关联的列表中显示 Windows 壳项的列表。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)

`CMFCShellTreeCtrl`

## <a name="requirements"></a>要求

**标题：** afxshelltreeCtrl.h

## <a name="example"></a>示例

下面的示例演示如何创建 `CMFCShellTreeCtrl` 类的对象。 此代码段是[资源管理器示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]

## <a name="cmfcshelltreectrlenableshellcontextmenu"></a><a name="enableshellcontextmenu"></a>CMFCShellTreeCtrl：：启用ShellContextMenu

启用快捷菜单。

```cpp
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
[在]指定是否启用快捷菜单的布尔。

## <a name="cmfcshelltreectrlgetflags"></a><a name="getflags"></a>CMFCShellTreeCtrl：：获取Flags

返回为[CMFCShellTreeCtrl 类](../../mfc/reference/cmfcshelltreectrl-class.md)对象设置的标志。

```
DWORD GetFlags() const;
```

### <a name="return-value"></a>返回值

指定当前设置的标志组合的 DWORD 值。

### <a name="remarks"></a>备注

在 中设置的标志`CMFCShellTreeCtrl`将发送到方法[IShellFolder：：：EnumObject，](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)每当刷新对象时。 您可以使用[CMFCShellTreeCtrl：：setFlags](#setflags)方法更改标志。

## <a name="cmfcshelltreectrlgetitempath"></a><a name="getitempath"></a>CMFCShellTreeCtrl：获取项目路径

检索[CMFCShellTreeCtrl 类](../../mfc/reference/cmfcshelltreectrl-class.md)中项的路径。

```
BOOL GetItemPath(
    CString& strPath,
    HTREEITEM htreeItem = NULL) const;
```

### <a name="parameters"></a>参数

*斯特路径*<br/>
[出]对字符串参数的引用。 方法将项的路径写入此参数。

*htreeItem*<br/>
[在]该方法检索此树控件项的路径。

### <a name="return-value"></a>返回值

如果成功，则非零;0 否则。

### <a name="remarks"></a>备注

如果此方法失败 *，strPath*包含空字符串。

如果不指定*hTreeItem，* 此方法将尝试获取当前选定项的字符串。 如果未选择任何项目，并且*hTreeItem*为 NULL，则此方法将失败。

## <a name="cmfcshelltreectrlgetrelatedlist"></a><a name="getrelatedlist"></a>CMFCShellTreeCtrl：获取相关列表

返回指向与此[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)对象关联的[CMFCShellListCtrl 类](../../mfc/reference/cmfcshelllistctrl-class.md)对象的指针。

```
CMFCShellListCtrl* GetRelatedList() const;
```

### <a name="return-value"></a>返回值

指向与此树控件`CMFCShellListCtrl`对象关联的对象的指针。

### <a name="remarks"></a>备注

通过将`CMFCShellListCtrl`对象与对象结合`CMFCShellTreeCtrl`使用，可以创建类似于资源管理器的窗口。 使用方法[CMFCShellTreeCtrl：：设置关联列表](#setrelatedlist)来关联这两个类。 关联后，框架会自动更新 更改中的`CMFCShellListCtrl``CMFCShellTreeCtrl`"如果"。

## <a name="cmfcshelltreectrlonchildnotify"></a><a name="onchildnotify"></a>CMFCShelltreectrl：：在儿童通知

```
virtual BOOL OnChildNotify(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* pLResult);
```

### <a name="parameters"></a>参数

[在]*消息*<br/>
[在]*wParam*<br/>
[在]*lParam*<br/>
[在]*pLResult*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcshelltreectrlongetitemicon"></a><a name="ongetitemicon"></a>CMFCShelltreectrl：ongetItemicon

```
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,
    BOOL bSelected);
```

### <a name="parameters"></a>参数

[在]*pItem*<br/>
[在]*b选定*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcshelltreectrlongetitemtext"></a><a name="ongetitemtext"></a>CMFCShelltreectrl：：在获取项目文本

```
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>参数

[在]*pItem*<br/>

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

## <a name="cmfcshelltreectrlrefresh"></a><a name="refresh"></a>CMFC舍尔特里克：：刷新

刷新并重新绘制[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)。

```cpp
void Refresh();
```

### <a name="remarks"></a>备注

调用此方法以刷新 中显示的项的层次结构`CMFCShellTreeCtrl`。

## <a name="cmfcshelltreectrlselectpath"></a><a name="selectpath"></a>CMFCShellTreeCtrl：选择路径

根据提供的路径选择[CMFCShellTreeCtrl 类](../../mfc/reference/cmfcshelltreectrl-class.md)中的项目。

```
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```

### <a name="parameters"></a>参数

*lpszPath*<br/>
[在]指定项路径的字符串。

*尔比德尔*<br/>
[在]指定项的 PIDL

### <a name="return-value"></a>返回值

S_OK如果成功;否则E_FAIL。

## <a name="cmfcshelltreectrlsetflags"></a><a name="setflags"></a>CMFCShellTreeCtrl：：设置标志

设置标志以筛选树上下文。

```cpp
void SetFlags(
    DWORD dwFlags,
    BOOL bRefresh = TRUE);
```

### <a name="parameters"></a>参数

dwFlags**<br/>
[在]要设置的标志。

*b 刷新*<br/>
[在]指定是否应立即刷新 的`CMFCShellTreeCtrl`布尔。

### <a name="remarks"></a>备注

将所有`CMFCShellTreeCtrl`设置的标志传递给[IShellfolder：：枚举对象](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)。 有关不同标志的值的详细信息，请参阅[IShellFolder：：枚举对象](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)。

## <a name="cmfcshelltreectrlsetrelatedlist"></a><a name="setrelatedlist"></a>CMFCShellTreeCtrl：：设置相关列表

将[CMFCShellListCtrl](../../mfc/reference/cmfcshelllistctrl-class.md)对象与[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)对象关联。

```cpp
void SetRelatedList(CMFCShellListCtrl* pShellList);
```

### <a name="parameters"></a>参数

*p壳列表*<br/>
[在]指向`CMFCShellListCtrl`对象的指针。

### <a name="remarks"></a>备注

此方法将 a`CMFCShellListCtrl`与`CMFCShellTreeCtrl`。 这些对象可以显示为类似于资源管理器的窗口：如果用户在 中选择 的对象`CMFCShellTreeCtrl`，则 中的`CMFCShellListCtrl`关联项将自动更新。

使用方法[CMFCShellTreeCtrl：获取相关列表](#getrelatedlist)来检索与`CMFCShellListCtrl`关联的`CMFCShellTreeCtrl`方法。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CTreeCtrl Class](../../mfc/reference/ctreectrl-class.md)<br/>
[CMFCShellListCtrl 类](../../mfc/reference/cmfcshelllistctrl-class.md)
