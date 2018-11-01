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
ms.openlocfilehash: 996a9052d71df4aed54fa4f922b4d4ffff8f1c14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453867"
---
# <a name="crecentfilelist-class"></a>CRecentFileList 类

支持最近使用的 (MRU) 文件列表的控件。

## <a name="syntax"></a>语法

```
class CRecentFileList
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CRecentFileList::CRecentFileList](#crecentfilelist)|构造 `CRecentFileList` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CRecentFileList::Add](#add)|将文件添加到 MRU 文件列表。|
|[CRecentFileList::GetDisplayName](#getdisplayname)|提供的 MRU 文件名的菜单显示的显示名称。|
|[CRecentFileList::GetSize](#getsize)|检索 MRU 文件列表中的文件数。|
|[CRecentFileList::ReadList](#readlist)|从注册表中读取 MRU 文件列表或。INI 文件。|
|[CRecentFileList::Remove](#remove)|从 MRU 文件列表中删除文件。|
|[CRecentFileList::UpdateMenu](#updatemenu)|更新菜单显示的 MRU 文件列表。|
|[CRecentFileList::WriteList](#writelist)|从注册表写入 MRU 文件列表或。INI 文件。|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CRecentFileList::operator]](#operator_at)|返回`CString`给定位置处的对象。|

## <a name="remarks"></a>备注

可以添加到文件，或将其从 MRU 文件列表中删除，可以读取或写入注册表的文件列表或。可以更新 INI 文件，并显示 MRU 文件列表的菜单。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CRecentFileList`

## <a name="requirements"></a>要求

**标头：** afxadv.h

##  <a name="add"></a>  CRecentFileList::Add

将文件添加到最近使用 (过的 MRU) 文件列表。

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

*lpszPathName*<br/>
指定要添加到列表的路径名。

*lpszAppID*<br/>
指定应用程序的应用程序用户模型 ID。

*pItem*<br/>
指定要添加到列表的 Shell 项的指针。

*pLink*<br/>
指定要添加到列表的 Shell 链接指向的指针。

*pidl*<br/>
指定应添加到最近的文档文件夹的 shell 项 IDLIST。

### <a name="remarks"></a>备注

文件名称将添加到 MRU 列表的顶部。 如果在 MRU 列表中已存在的文件的名称，则它将移动到顶部。

##  <a name="crecentfilelist"></a>  CRecentFileList::CRecentFileList

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
在菜单上显示的 MRU （最近使用） 文件列表编号的偏移量。

*lpszSection*<br/>
指向的注册表或应用程序的部分的名称。其中 MRU 文件列表是读取和/或写入 INI 文件。

*lpszEntryFormat*<br/>
指向要用于存储在注册表或应用程序中的条目的名称的格式字符串。INI 文件。

*nSize*<br/>
MRU 文件列表中的文件的最大数目。

*nMaxDispLen*<br/>
最大长度 （以字符为单位，可用于在 MRU 文件列表中的文件名的菜单显示）。

### <a name="remarks"></a>备注

指向格式字符串*lpszEntryFormat*应包含"%d"，这将用于替换每个 MRU 项的索引。 例如，如果格式字符串`"file%d"`则将命名为条目`file0`， `file1`，依次类推。

##  <a name="getdisplayname"></a>  CRecentFileList::GetDisplayName

获取在 MRU 文件列表中，在菜单上显示的 MRU 列表中使用的文件的显示名称。

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
要在的 MRU 文件菜单列表中显示其名称的文件的完整路径。

*nIndex*<br/>
MRU 文件列表中的文件的从零开始的索引。

*lpszCurDir*<br/>
保持当前目录的字符串。

*nCurDir*<br/>
当前目录字符串的长度。

*bAtLeastName*<br/>
如果非零值，指示应返回文件的基名称，即使它超出了最大显示长度 (作为传递*nMaxDispLen*参数`CRecentFileList`构造函数)。

### <a name="return-value"></a>返回值

**FALSE**如果没有任何文件名中指定索引处最近使用 (过的 MRU) 文件列表中。

### <a name="remarks"></a>备注

如果该文件位于当前目录中，函数将保留关闭显示器的目录。 如果文件名太长，目录和扩展将被去除。 如果文件名仍然太长，显示名称设置为空字符串中，除非*bAtLeastName*为非零值。

##  <a name="getsize"></a>  CRecentFileList::GetSize

检索 MRU 文件列表中的文件数。

```
int GetSize() const;
```

### <a name="return-value"></a>返回值

在当前的文件数最近使用 (过的 MRU) 文件列表。

##  <a name="operator_at"></a>  CRecentFileList::operator]

重载的下标 (`[]`) 运算符返回单个`CString`中从零开始的索引指定*nIndex*。

```
CString& operator[ ](int nindex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
从零开始的索引`CString`中的一组`CString`s。

##  <a name="readlist"></a>  CRecentFileList::ReadList

读取最近使用的 (MRU) 从注册表或应用程序的文件列表。INI 文件。

```
virtual void ReadList();
```

##  <a name="remove"></a>  CRecentFileList::Remove

从 MRU 文件列表中删除文件。

```
virtual void Remove(int nIndex);
```

### <a name="parameters"></a>参数

*nIndex*<br/>
要从最近使用 (过的 MRU) 文件列表中删除的文件的从零开始索引。

##  <a name="updatemenu"></a>  CRecentFileList::UpdateMenu

更新菜单显示的 MRU 文件列表。

```
virtual void UpdateMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>参数

*pCmdUI*<br/>
一个指向[CCmdUI](../../mfc/reference/ccmdui-class.md)最近使用 (过的 MRU) 文件列表菜单的对象。

##  <a name="writelist"></a>  CRecentFileList::WriteList

将写入最近使用的 (MRU) 文件列表到注册表或应用程序。INI 文件。

```
virtual void WriteList();
```

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)

