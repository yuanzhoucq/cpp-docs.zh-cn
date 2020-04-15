---
title: CRecentFileList 类
ms.date: 11/04/2016
f1_keywords:
- CRecentFileList
- AFXADV/CRecentFileList
- AFXADV/CRecentFileList::CRecentFileList
- AFXADV/CRecentFileList::Add
- AFXADV/CRecentFileList::GetDisplayName
- AFXADV/CRecentFileList::GetSize
- AFXADV/CRecentFileList::ReadList
- AFXADV/CRecentFileList::Remove
- AFXADV/CRecentFileList::UpdateMenu
- AFXADV/CRecentFileList::WriteList
helpviewer_keywords:
- CRecentFileList [MFC], CRecentFileList
- CRecentFileList [MFC], Add
- CRecentFileList [MFC], GetDisplayName
- CRecentFileList [MFC], GetSize
- CRecentFileList [MFC], ReadList
- CRecentFileList [MFC], Remove
- CRecentFileList [MFC], UpdateMenu
- CRecentFileList [MFC], WriteList
ms.assetid: a77f0524-7584-4582-849a-7e97b76d186e
ms.openlocfilehash: a2102c6a39c14c548828e57ad1c49de6a5bc03dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370899"
---
# <a name="crecentfilelist-class"></a>CRecentFileList 类

支持最近使用的 (MRU) 文件列表的控件。

## <a name="syntax"></a>语法

```
class CRecentFileList
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[最新文件列表："最新文件列表"](#crecentfilelist)|构造 `CRecentFileList` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[最新文件列表：：添加](#add)|将文件添加到 MRU 文件列表。|
|[最新文件列表：获取显示名称](#getdisplayname)|为 MRU 文件名的菜单显示提供显示名称。|
|[最新文件列表：获取 Size](#getsize)|检索 MRU 文件列表中的文件数。|
|[最新文件列表：阅读列表](#readlist)|从注册表或 读取 MRU 文件列表。INI 文件。|
|[最新文件列表：删除](#remove)|从 MRU 文件列表中删除文件。|
|[最新文件列表：更新菜单](#updatemenu)|更新 MRU 文件列表的菜单显示。|
|[最新文件列表：写入列表](#writelist)|从注册表或 写入 MRU 文件列表。INI 文件。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[最新文件列表：运算符\[\]](#operator_at)|返回`CString`给定位置的对象。|

## <a name="remarks"></a>备注

文件可以添加到 MRU 文件列表中或从中删除，文件列表可以从注册表或 写入 注册表或 。可以更新 INI 文件，并可以更新显示 MRU 文件列表的菜单。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CRecentFileList`

## <a name="requirements"></a>要求

**标题：** afxadv.h

## <a name="crecentfilelistadd"></a><a name="add"></a>最新文件列表：：添加

将文件添加到最近使用的 （MRU） 文件列表中。

```
virtual void Add(LPCTSTR lpszPathName);

virtual void Add(
    LPCTSTR lpszPathName,
    LPCTSTR lpszAppID);

void Add(
    IShellItem* pItem,
    LPCTSTR lpszAppID);

void Add(
    IShellLink* pLink,
    LPCTSTR lpszAppID);

void Add(
    PIDLIST_ABSOLUTE pidl,
    LPCTSTR lpszAppID);
```

### <a name="parameters"></a>参数

*lpszPath名称*<br/>
指定要添加到列表中的路径名称。

*lpszAppID*<br/>
为应用程序指定应用程序用户型号 ID。

*pItem*<br/>
指定要添加到列表中的指向壳项的指针。

*p链接*<br/>
指定要添加到列表中的指向 Shell 链接的指针。

*皮德尔*<br/>
指定应添加到最近文档文件夹的 shell 项的 IDLIST。

### <a name="remarks"></a>备注

文件名将添加到 MRU 列表的顶部。 如果 MRU 列表中已存在文件名，它将移动到顶部。

## <a name="crecentfilelistcrecentfilelist"></a><a name="crecentfilelist"></a>最新文件列表："最新文件列表"

构造 `CRecentFileList` 对象。

```
CRecentFileList(
    UINT nStart,
    LPCTSTR lpszSection,
    LPCTSTR lpszEntryFormat,
    int nSize,
    int nMaxDispLen = AFX_ABBREV_FILENAME_LEN);
```

### <a name="parameters"></a>参数

*n 开始*<br/>
MRU（最近使用）文件列表的菜单显示中编号的偏移量。

*lpsz节*<br/>
指向注册表或应用程序的 部分的名称。读取和/或写入 MRU 文件列表的 INI 文件。

*lpszentry格式*<br/>
指向用于存储在注册表或应用程序中的条目的名称的格式字符串。INI 文件。

*nSize*<br/>
MRU 文件列表中的文件的最大数量。

*nMaxDispLen*<br/>
MRU 文件列表中的文件名的菜单显示的最大长度（以字符表示）。

### <a name="remarks"></a>备注

*lpszEntryFormat*指向的格式字符串应包含"%d"，用于替换每个 MRU 项的索引。 例如，如果格式字符串是`"file%d"`，则条目将命名为`file0`、`file1`等。

## <a name="crecentfilelistgetdisplayname"></a><a name="getdisplayname"></a>最新文件列表：获取显示名称

获取 MRU 文件列表中文件的显示名称，用于 MRU 列表的菜单显示。

```
virtual BOOL GetDisplayName(
    CString& strName,
    int nIndex,
    LPCTSTR lpszCurDir,
    int nCurDir,
    BOOL bAtLeastName = TRUE) const;
```

### <a name="parameters"></a>参数

*strName*<br/>
其名称将显示在 MRU 文件的菜单列表中的文件的完整路径。

*nIndex*<br/>
MRU 文件列表中文件的基于零的索引。

*lpszCurdir*<br/>
保存当前目录的字符串。

*nCurDir*<br/>
当前目录字符串的长度。

*b 最小名称*<br/>
如果非零，则指示应返回文件的基本名称，即使它超过最大显示长度（作为*nMaxDispLen*参数传递给`CRecentFileList`构造函数）。

### <a name="return-value"></a>返回值

如果最近使用的 （MRU） 文件列表中的指定索引中没有文件名，**则 FALSE。**

### <a name="remarks"></a>备注

如果文件位于当前目录中，则函数将目录从显示屏上保留。 如果文件名太长，目录和扩展名将被删除。 如果文件名仍然太长，则显示名称将设置为空字符串，除非*bAtLeastName*是非零。

## <a name="crecentfilelistgetsize"></a><a name="getsize"></a>最新文件列表：获取 Size

检索 MRU 文件列表中的文件数。

```
int GetSize() const;
```

### <a name="return-value"></a>返回值

当前最近使用 （MRU） 文件列表中的文件数。

## <a name="crecentfilelistoperator--"></a><a name="operator_at"></a>C 最新文件列表：运算符 |

重载子标 （`[]`） 运算符返回`CString`*由 nIndex*中的零基索引指定的单个。

```
CString& operator[ ](int nindex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
s`CString`的`CString`零基索引。

## <a name="crecentfilelistreadlist"></a><a name="readlist"></a>最新文件列表：阅读列表

从注册表或应用程序的 读取最近使用 （MRU） 文件列表。INI 文件。

```
virtual void ReadList();
```

## <a name="crecentfilelistremove"></a><a name="remove"></a>最新文件列表：删除

从 MRU 文件列表中删除文件。

```
virtual void Remove(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要从最近使用的 （MRU） 文件列表中删除的文件的基于零的索引。

## <a name="crecentfilelistupdatemenu"></a><a name="updatemenu"></a>最新文件列表：更新菜单

更新 MRU 文件列表的菜单显示。

```
virtual void UpdateMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>参数

*pCmdUI*<br/>
指向[CCmdUI](../../mfc/reference/ccmdui-class.md)对象的指针，用于最近使用 （MRU） 文件列表菜单。

## <a name="crecentfilelistwritelist"></a><a name="writelist"></a>最新文件列表：写入列表

将最近使用的 （MRU） 文件列表写入注册表或应用程序的 。INI 文件。

```
virtual void WriteList();
```

## <a name="see-also"></a>另请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)
