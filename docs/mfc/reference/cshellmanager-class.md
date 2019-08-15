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
ms.openlocfilehash: 8151550dafdd1bdf8593d555008af387cf548bc8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502620"
---
# <a name="cshellmanager-class"></a>CShellManager 类

实现可使你使用指向标识符列表 (PIDL) 的指针的几种方法。

## <a name="syntax"></a>语法

```
class CShellManager : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CShellManager::CShellManager](#cshellmanager)|构造 `CShellManager` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CShellManager::BrowseForFolder](#browseforfolder)|显示一个对话框, 使用户能够选择 shell 文件夹。|
|[CShellManager::ConcatenateItem](#concatenateitem)|连接两个 Pidl。|
|[CShellManager::CopyItem](#copyitem)|创建新的 PIDL 并将提供的 PIDL 复制到其中。|
|[CShellManager::CreateItem](#createitem)|创建指定大小的新 PIDL。|
|[CShellManager::FreeItem](#freeitem)|删除提供的 PIDL。|
|[CShellManager::GetItemCount](#getitemcount)|返回所提供的 PIDL 中的项数。|
|[CShellManager::GetItemSize](#getitemsize)|返回所提供的 PIDL 的大小。|
|[CShellManager::GetNextItem](#getnextitem)|返回 PIDL 中的下一项。|
|[CShellManager::GetParentItem](#getparentitem)|检索所提供项的父项。|
|[CShellManager::ItemFromPath](#itemfrompath)|检索由提供的路径标识的项的 PIDL。|

## <a name="remarks"></a>备注

`CShellManager`类的方法均处理 pidl。 PIDL 是 shell 对象的唯一标识符。

不应手动创建`CShellManager`对象。 应用程序的框架会自动创建它。 但是, 你应在应用程序的初始化过程中调用[CWinAppEx:: InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager) 。 若要获取应用程序的 shell 管理器的指针, 请调用[CWinAppEx:: GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CShellManager](../../mfc/reference/cshellmanager-class.md)

## <a name="requirements"></a>要求

**标头:** afxshellmanager

##  <a name="browseforfolder"></a>  CShellManager::BrowseForFolder

显示一个对话框, 使用户能够选择 shell 文件夹。

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

*strOutFolder*<br/>
弄方法用来存储所选文件夹的路径的字符串。

*pWndParent*<br/>
中指向父窗口的指针。

*lplszInitialFolder*<br/>
中一个字符串, 其中包含在显示对话框时默认选择的文件夹。

*lpszTitle*<br/>
中对话框的标题。

*ulFlags*<br/>
中指定对话框选项的标志。 有关详细说明, 请参阅[BROWSEINFO](/windows/win32/api/shlobj_core/ns-shlobj_core-browseinfow) 。

*piFolderImage*<br/>
弄一个指向整数值的指针, 该方法在此位置写入所选文件夹的图像索引。

### <a name="return-value"></a>返回值

如果用户从对话框中选择一个文件夹, 则为非零值;否则为0。

### <a name="remarks"></a>备注

调用此方法时, 应用程序将创建并显示一个对话框, 使用户能够选择文件夹。 方法将文件夹的路径写入*strOutFolder*参数。

### <a name="example"></a>示例

下面的示例演示如何`CShellManager` `CWinAppEx::GetShellManager`使用方法检索对对象的引用`BrowseForFolder`以及如何使用方法。 此代码片段是[资源管理器示例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_Explorer#6](../../mfc/reference/codesnippet/cpp/cshellmanager-class_1.cpp)]

##  <a name="concatenateitem"></a>CShellManager::ConcatenateItem

创建包含两个 Pidl 的新列表。

```
LPITEMIDLIST ConcatenateItem(
    LPCITEMIDLIST pidl1,
    LPCITEMIDLIST pidl2);
```

### <a name="parameters"></a>参数

*pidl1*<br/>
中第一项。

*pidl2*<br/>
中第二项。

### <a name="return-value"></a>返回值

如果函数成功, 则为指向新项列表的指针; 否则为 NULL。

### <a name="remarks"></a>备注

此方法创建一个足以同时包含*pidl1*和*Pidl2*的新[ITEMIDLIST](/windows/win32/api/shtypes/ns-shtypes-itemidlist) 。 然后, 它会将*pidl1*和*pidl2*复制到新列表中。

##  <a name="copyitem"></a>CShellManager:: CopyItem

复制项列表。

```
LPITEMIDLIST CopyItem(LPCITEMIDLIST pidlSource);
```

### <a name="parameters"></a>参数

*pidlSource*<br/>
中原始项列表。

### <a name="return-value"></a>返回值

如果成功, 则为指向新创建的项列表的指针;否则为 NULL。

### <a name="remarks"></a>备注

新创建的项列表的大小与源项列表相同。

##  <a name="createitem"></a>CShellManager:: CreateItem

创建新的 PIDL。

```
LPITEMIDLIST CreateItem(UINT cbSize);
```

### <a name="parameters"></a>参数

*cbSize*<br/>
中项列表的大小。

### <a name="return-value"></a>返回值

如果成功, 则为指向已创建项列表的指针;否则为 NULL。

##  <a name="cshellmanager"></a>CShellManager::CShellManager

构造 `CShellManager` 对象。

```
CShellManager();
```

### <a name="remarks"></a>备注

在大多数情况下, 无需`CShellManager`直接创建。 默认情况下, 框架为你创建一个。 若要获取指向的`CShellManager`指针, 请调用[CWinAppEx:: GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager)。 如果`CShellManager`手动创建, 则必须使用方法[CWinAppEx:: InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager)对其进行初始化。

##  <a name="freeitem"></a>CShellManager::FreeItem

删除项列表。

```
void FreeItem(LPITEMIDLIST pidl);
```

### <a name="parameters"></a>参数

*pidl*<br/>
中要删除的项列表。

##  <a name="getitemcount"></a>  CShellManager::GetItemCount

返回项列表中的项数。

```
UINT GetItemCount(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>参数

*pidl*<br/>
中指向项列表的指针。

### <a name="return-value"></a>返回值

项列表中的项数。

##  <a name="getitemsize"></a>CShellManager::GetItemSize

返回项列表的大小。

```
UINT GetItemSize(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>参数

*pidl*<br/>
中指向项列表的指针。

### <a name="return-value"></a>返回值

项列表的大小。

##  <a name="getnextitem"></a>CShellManager::GetNextItem

检索指向项标识符列表 (PIDL) 的指针的下一项。

```
LPITEMIDLIST GetNextItem(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>参数

*pidl*<br/>
中要循环访问的项的列表。

### <a name="return-value"></a>返回值

指向列表中下一项的指针。

### <a name="remarks"></a>备注

如果列表中没有更多项, 则此方法返回 NULL。

##  <a name="getparentitem"></a>CShellManager::GetParentItem

检索指向项标识符列表 (PIDL) 的指针的父级。

```
int GetParentItem(
    LPCITEMIDLIST lpidl,
    LPITEMIDLIST& lpidlParent);
```

### <a name="parameters"></a>参数

*lpidl*<br/>
中将检索其父对象的 PIDL。

*lpidlParent*<br/>
弄对 PIDL 的引用, 方法将在其中存储结果。

### <a name="return-value"></a>返回值

父 PIDL 的级别。

### <a name="remarks"></a>备注

PIDL 的级别相对于桌面。 桌面 PIDL 的级别被视为0。

##  <a name="itemfrompath"></a>CShellManager::ItemFromPath

从字符串路径标识的项中检索指向项标识符列表 (PIDL) 的指针。

```
HRESULT ItemFromPath(
    LPCTSTR lpszPath,
    LPITEMIDLIST& pidl);
```

### <a name="parameters"></a>参数

*lpszPath*<br/>
中一个字符串, 指定项的路径。

*pidl*<br/>
弄对 PIDL 的引用。 方法使用此 PIDL 来存储指向其返回值的指针。

### <a name="return-value"></a>返回值

如果成功, 则返回 NOERROR;OLE 定义的错误值。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)
