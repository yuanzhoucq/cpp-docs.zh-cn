---
title: CShellManager 类
ms.date: 11/04/2016
f1_keywords:
- CShellManager
- AFXSHELLMANAGER/CShellManager
- AFXSHELLMANAGER/CShellManager::CShellManager
- AFXSHELLMANAGER/CShellManager::BrowseForFolder
- AFXSHELLMANAGER/CShellManager::ConcatenateItem
- AFXSHELLMANAGER/CShellManager::CopyItem
- AFXSHELLMANAGER/CShellManager::CreateItem
- AFXSHELLMANAGER/CShellManager::FreeItem
- AFXSHELLMANAGER/CShellManager::GetItemCount
- AFXSHELLMANAGER/CShellManager::GetItemSize
- AFXSHELLMANAGER/CShellManager::GetNextItem
- AFXSHELLMANAGER/CShellManager::GetParentItem
- AFXSHELLMANAGER/CShellManager::ItemFromPath
helpviewer_keywords:
- CShellManager [MFC], CShellManager
- CShellManager [MFC], BrowseForFolder
- CShellManager [MFC], ConcatenateItem
- CShellManager [MFC], CopyItem
- CShellManager [MFC], CreateItem
- CShellManager [MFC], FreeItem
- CShellManager [MFC], GetItemCount
- CShellManager [MFC], GetItemSize
- CShellManager [MFC], GetNextItem
- CShellManager [MFC], GetParentItem
- CShellManager [MFC], ItemFromPath
ms.assetid: f15c4c1a-6fae-487d-9913-9b7369b33da0
ms.openlocfilehash: cc8aa9216fd0d4dcc169830fb745134ceb5c65fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318418"
---
# <a name="cshellmanager-class"></a>CShellManager 类

实现可使你使用指向标识符列表 (PIDL) 的指针的几种方法。

## <a name="syntax"></a>语法

```
class CShellManager : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C壳管理器：C壳管理器](#cshellmanager)|构造 `CShellManager` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CShell 管理器：：浏览文件夹](#browseforfolder)|显示一个对话框，使用户能够选择 shell 文件夹。|
|[CShellManager：串联项目](#concatenateitem)|连接两个 PidL。|
|[C壳管理器：复制项目](#copyitem)|创建新的 PIDL 并将随附的 PIDL 复制到它。|
|[CShell管理器：创建项目](#createitem)|创建指定大小的新 PIDL。|
|[CShellManager：免费项目](#freeitem)|删除提供的 PIDL。|
|[CShell管理器：获取项目计数](#getitemcount)|返回提供的 PIDL 中的项数。|
|[CShell 管理器：获取项目大小](#getitemsize)|返回提供的 PIDL 的大小。|
|[CShellManager：获取下一个项目](#getnextitem)|从 PIDL 返回下一个项。|
|[CShellManager：获取父项](#getparentitem)|检索提供的项的父项。|
|[CShell 管理器：项目从路径](#itemfrompath)|检索提供路径标识的项的 PIDL。|

## <a name="remarks"></a>备注

`CShellManager`类的方法都处理 L。 PIDL 是 shell 对象的唯一标识符。

不应手动创建`CShellManager`对象。 它将由应用程序的框架自动创建。 但是，您应该在应用程序的初始化过程中调用[CWinAppEx：：在](../../mfc/reference/cwinappex-class.md#initshellmanager)应用程序的初始化过程中调用 ItShellManager。 要获取指向应用程序的 shell 管理器的指针，请致电[CWinAppEx：：getShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CShellManager](../../mfc/reference/cshellmanager-class.md)

## <a name="requirements"></a>要求

**标题：** afxshell管理器.h

## <a name="cshellmanagerbrowseforfolder"></a><a name="browseforfolder"></a>CShell 管理器：：浏览文件夹

显示一个对话框，使用户能够选择 shell 文件夹。

```
BOOL BrowseForFolder(
    CString& strOutFolder,
    CWnd* pWndParent = NULL,
    LPCTSTR lplszInitialFolder = NULL,
    LPCTSTR lpszTitle = NULL,
    UINT ulFlags = BIF_RETURNONLYFSDIRS,
    LPINT piFolderImage = NULL);
```

### <a name="parameters"></a>参数

*斯特鲁特文件夹*<br/>
[出]用于存储所选文件夹的路径的方法使用的字符串。

*pwnd 父级*<br/>
[在]指向父窗口的指针。

*lplsz 初始文件夹*<br/>
[在]包含默认情况下显示对话框时选择的文件夹的字符串。

*lpszTitle*<br/>
[在]对话框的标题。

*ulFlags*<br/>
[在]标记指定对话框的选项。 有关详细说明，请参阅[BROWSEINFO。](/windows/win32/api/shlobj_core/ns-shlobj_core-browseinfow)

*皮皮文件夹图像*<br/>
[出]指向整数值的指针，该方法在其中写入所选文件夹的图像索引。

### <a name="return-value"></a>返回值

如果用户从对话框中选择文件夹，则非零;否则 0。

### <a name="remarks"></a>备注

调用此方法时，应用程序将创建并显示一个对话框，使用户能够选择文件夹。 该方法将文件夹的路径写入*strOutFolder*参数。

### <a name="example"></a>示例

下面的示例演示如何使用`CShellManager``CWinAppEx::GetShellManager`方法检索对对象的引用以及如何使用 方法。 `BrowseForFolder` 此代码段是[资源管理器示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_Explorer#6](../../mfc/reference/codesnippet/cpp/cshellmanager-class_1.cpp)]

## <a name="cshellmanagerconcatenateitem"></a><a name="concatenateitem"></a>CShellManager：串联项目

创建包含两个 PidL 的新列表。

```
LPITEMIDLIST ConcatenateItem(
    LPCITEMIDLIST pidl1,
    LPCITEMIDLIST pidl2);
```

### <a name="parameters"></a>参数

*皮德尔1*<br/>
[在]第一个项目。

*皮德尔2*<br/>
[在]第二个项目。

### <a name="return-value"></a>返回值

如果函数成功，则指向新项目列表的指针，否则为 NULL。

### <a name="remarks"></a>备注

此方法创建一个新的[ITEMIDLIST](/windows/win32/api/shtypes/ns-shtypes-itemidlist)大到足以包含*pidl1*和*pidl2*。 然后，它将*pidl1*和*pidl2*复制到新列表中。

## <a name="cshellmanagercopyitem"></a><a name="copyitem"></a>C壳管理器：复制项目

复制项目列表。

```
LPITEMIDLIST CopyItem(LPCITEMIDLIST pidlSource);
```

### <a name="parameters"></a>参数

*皮德尔来源*<br/>
[在]原始项列表。

### <a name="return-value"></a>返回值

指向新创建的项列表的指针（如果成功）;否则 NULL。

### <a name="remarks"></a>备注

新创建的项列表的大小与源项列表的大小相同。

## <a name="cshellmanagercreateitem"></a><a name="createitem"></a>CShell管理器：创建项目

创建新的 PIDL。

```
LPITEMIDLIST CreateItem(UINT cbSize);
```

### <a name="parameters"></a>参数

*cbSize*<br/>
[在]项列表的大小。

### <a name="return-value"></a>返回值

如果成功，指向已创建项列表的指针;否则 NULL。

## <a name="cshellmanagercshellmanager"></a><a name="cshellmanager"></a>C壳管理器：C壳管理器

构造 `CShellManager` 对象。

```
CShellManager();
```

### <a name="remarks"></a>备注

在大多数情况下，您不必直接创建 。 `CShellManager` 默认情况下，框架会为您创建一个。 要获取 指向 的`CShellManager`指针，请致电[CWinAppEx：：获取ShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager)。 如果手动创建一个`CShellManager`，则必须使用[CWinAppEx：：InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager)的方法初始化它。

## <a name="cshellmanagerfreeitem"></a><a name="freeitem"></a>CShellManager：免费项目

删除项目列表。

```
void FreeItem(LPITEMIDLIST pidl);
```

### <a name="parameters"></a>参数

*皮德尔*<br/>
[在]要删除的项目列表。

## <a name="cshellmanagergetitemcount"></a><a name="getitemcount"></a>CShell管理器：获取项目计数

返回项列表中的项数。

```
UINT GetItemCount(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>参数

*皮德尔*<br/>
[在]指向项列表的指针。

### <a name="return-value"></a>返回值

项列表中的项数。

## <a name="cshellmanagergetitemsize"></a><a name="getitemsize"></a>CShell 管理器：获取项目大小

返回项目列表的大小。

```
UINT GetItemSize(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>参数

*皮德尔*<br/>
[在]指向项列表的指针。

### <a name="return-value"></a>返回值

项列表的大小。

## <a name="cshellmanagergetnextitem"></a><a name="getnextitem"></a>CShellManager：获取下一个项目

从指向项标识符列表 （PIDL） 的指针检索下一个项。

```
LPITEMIDLIST GetNextItem(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>参数

*皮德尔*<br/>
[在]要迭代的项列表。

### <a name="return-value"></a>返回值

指向列表中下一个项目的指针。

### <a name="remarks"></a>备注

如果列表中没有更多的项，此方法将返回 NULL。

## <a name="cshellmanagergetparentitem"></a><a name="getparentitem"></a>CShellManager：获取父项

检索指向项标识符列表 （PIDL） 的指针的父级。

```
int GetParentItem(
    LPCITEMIDLIST lpidl,
    LPITEMIDLIST& lpidlParent);
```

### <a name="parameters"></a>参数

*尔比德尔*<br/>
[在]将检索其父项的 PIDL。

*lpidl 家长*<br/>
[出]对 PIDL 的引用，该方法将在其中存储结果。

### <a name="return-value"></a>返回值

父 PIDL 的级别。

### <a name="remarks"></a>备注

PIDL 的级别与桌面相关。 桌面 PIDL 被视为具有 0 的级别。

## <a name="cshellmanageritemfrompath"></a><a name="itemfrompath"></a>CShell 管理器：项目从路径

从字符串路径标识的项中检索指向项标识符列表 （PIDL） 的指针。

```
HRESULT ItemFromPath(
    LPCTSTR lpszPath,
    LPITEMIDLIST& pidl);
```

### <a name="parameters"></a>参数

*lpszPath*<br/>
[在]指定项路径的字符串。

*皮德尔*<br/>
[出]对 PIDL 的引用。 该方法使用此 PIDL 存储指向其返回值的指针。

### <a name="return-value"></a>返回值

如果成功，返回 NOERROR;OLE 定义的错误值。

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
