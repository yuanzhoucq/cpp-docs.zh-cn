---
title: CJumpList 类
ms.date: 03/27/2019
f1_keywords:
- CJumpList
- AFXADV/CJumpList
- AFXADV/CJumpList::CJumpList
- AFXADV/CJumpList::AbortList
- AFXADV/CJumpList::AddDestination
- AFXADV/CJumpList::AddKnownCategory
- AFXADV/CJumpList::AddTask
- AFXADV/CJumpList::AddTasks
- AFXADV/CJumpList::AddTaskSeparator
- AFXADV/CJumpList::ClearAll
- AFXADV/CJumpList::ClearAllDestinations
- AFXADV/CJumpList::CommitList
- AFXADV/CJumpList::GetDestinationList
- AFXADV/CJumpList::GetMaxSlots
- AFXADV/CJumpList::GetRemovedItems
- AFXADV/CJumpList::InitializeList
- AFXADV/CJumpList::SetAppID
helpviewer_keywords:
- CJumpList [MFC], CJumpList
- CJumpList [MFC], AbortList
- CJumpList [MFC], AddDestination
- CJumpList [MFC], AddKnownCategory
- CJumpList [MFC], AddTask
- CJumpList [MFC], AddTasks
- CJumpList [MFC], AddTaskSeparator
- CJumpList [MFC], ClearAll
- CJumpList [MFC], ClearAllDestinations
- CJumpList [MFC], CommitList
- CJumpList [MFC], GetDestinationList
- CJumpList [MFC], GetMaxSlots
- CJumpList [MFC], GetRemovedItems
- CJumpList [MFC], InitializeList
- CJumpList [MFC], SetAppID
ms.assetid: d364d27e-f512-4b12-9872-c2a17c78ab1f
ms.openlocfilehash: 2e45e2e58bd51d36b6412940b7ed01aa119017ed
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754936"
---
# <a name="cjumplist-class"></a>CJumpList 类

A`CJumpList`是右键单击任务栏中的图标时显示的快捷方式列表。

## <a name="syntax"></a>语法

```
class CJumpList;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[跳转列表：：跳转列表](#cjumplist)|构造 `CJumpList` 对象。|
|[跳转列表：*跳转列表](#_dtorcjumplist)|销毁 `CJumpList` 对象。|

|名称|说明|
|----------|-----------------|
|[跳转列表：：中止列表](#abortlist)|在不提交的情况下中止列表生成事务。|
|[跳转列表：：添加目的地](#adddestination)|已重载。 将目标添加到列表中。|
|[跳转列表：：添加已知类别](#addknowncategory)|将已知类别追加到列表中。|
|[跳转列表：：添加任务](#addtask)|已重载。 将项添加到规范任务类别。|
|[跳转列表：：添加任务](#addtasks)|将项添加到规范任务类别。|
|[跳转列表：：添加任务分离器](#addtaskseparator)|在任务之间添加分隔符。|
|[跳转列表：清除所有](#clearall)|删除到目前为止已添加到当前实例`CJumpList`的所有任务和目标。|
|[跳转列表：清除所有目标](#clearalldestinations)|删除到目前为止已添加到当前实例`CJumpList`的所有目标。|
|[跳转列表：提交列表](#commitlist)|结束列表生成事务并将报告的列表提交到关联的存储（在这种情况下为注册表）。|
|[跳转列表：获取目的地列表](#getdestinationlist)|检索指向目标列表的接口指针。|
|[跳转列表：获取 MaxSlots](#getmaxslots)|检索最大项目数，包括可在调用应用程序的目标菜单中显示的类别标头。|
|[跳转列表：：获取删除的项目](#getremoveditems)|返回表示已删除目标的项数组。|
|[跳转列表：：初始化列表](#initializelist)|开始列表生成事务。|
|[跳转列表：：设置AppID](#setappid)|为要生成的列表设置应用程序用户模型 ID。|

## <a name="inheritance-hierarchy"></a>继承层次结构

[CJumpList](../../mfc/reference/cjumplist-class.md)

## <a name="requirements"></a>要求

**标题：** afxadv.h

## <a name="cjumplistcjumplist"></a><a name="_dtorcjumplist"></a>跳转列表：*跳转列表

销毁 `CJumpList` 对象。

```
~CJumpList();
```

## <a name="cjumplistabortlist"></a><a name="abortlist"></a>跳转列表：：中止列表

在不提交的情况下中止列表生成事务。

```cpp
void AbortList();
```

### <a name="remarks"></a>备注

调用此方法的效果与不调用`CJumpList``CommitList`销毁的效果相同。

## <a name="cjumplistadddestination"></a><a name="adddestination"></a>跳转列表：：添加目的地

将目标添加到列表中。

```
BOOL AddDestination(
    LPCTSTR lpcszCategoryName,
    LPCTSTR strDestinationPath);

BOOL AddDestination(
    LPCTSTR strCategoryName,
    IShellItem* pShellItem);

BOOL AddDestination(
    LPCTSTR strCategoryName,
    IShellLink* pShellLink);
```

### <a name="parameters"></a>参数

*lpcsz 类别名称*<br/>
指定类别名称。 如果指定的类别不存在，将创建该类别。

*串目标路径*<br/>
指定目标文件的路径。

*串名称*<br/>
指定类别名称。 如果指定的类别不存在，将创建该类别。

*p壳牌项目*<br/>
指定表示要添加目标的行壳项目。

*p壳牌链接*<br/>
指定表示要添加目标的 Shell 链接。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

内部实例`CJumpList`累积添加的目标，然后在 中`CommitList`提交它们。

## <a name="cjumplistaddknowncategory"></a><a name="addknowncategory"></a>跳转列表：：添加已知类别

将已知类别追加到列表中。

```
BOOL AddKnownCategory(KNOWNDESTCATEGORY category);
```

### <a name="parameters"></a>参数

*category*<br/>
指定已知的类别类型。 可以是KDC_RECENT，也可以是KDC_KNOWN。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

已知类别是我们将自动计算每个使用的应用程序的频繁和最近类别`SHAddToRecentDocs`（或在某些情况下间接使用它，因为 shell 会代表应用程序调用它）。

## <a name="cjumplistaddtask"></a><a name="addtask"></a>跳转列表：：添加任务

将项添加到规范任务类别。

```
BOOL AddTask(
    LPCTSTR strTargetExecutablePath,
    LPCTSTR strCommandLineArgs,
    LPCTSTR strTitle,
    LPCTSTR strIconLocation,
    int iIconIndex);

BOOL AddTask(IShellLink* pShellLink);
```

### <a name="parameters"></a>参数

*str目标可执行路径*<br/>
指定目标任务路径。

*斯特鲁茨线*<br/>
指定*strTarget 可执行路径*指定的可执行文件的命令行参数。

*斯特标题*<br/>
将在目标列表中显示的任务名称。

*串图标位置*<br/>
将在"目标列表"中以及标题中显示的图标的位置。

*iIconIndex*<br/>
图标索引。

*p壳牌链接*<br/>
表示要添加的任务的 Shell 链接。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

实例`CJumpList`将累积指定的任务，并在 期间`CommitList`将它们添加到目标列表。 任务项将显示在应用程序目标菜单底部的类别中。 此类别在 UI 中填充时优先于所有其他类别。

## <a name="cjumplistaddtasks"></a><a name="addtasks"></a>跳转列表：：添加任务

将项添加到规范任务类别。

```
BOOL AddTasks(IObjectArray* pObjectCollection);
```

### <a name="parameters"></a>参数

*pObject集合*<br/>
要添加的任务的集合。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

CJumpList 的实例累积指定的任务，并在 期间`CommitList`将它们添加到目标列表中。 任务项将显示在应用程序目标菜单底部的类别中。 此类别在 UI 中填充时优先于所有其他类别。

## <a name="cjumplistaddtaskseparator"></a><a name="addtaskseparator"></a>跳转列表：：添加任务分离器

在任务之间添加分隔符。

```
BOOL AddTaskSeparator();
```

### <a name="return-value"></a>返回值

如果成功，则非零，如果为非零，则为 0。

## <a name="cjumplistcjumplist"></a><a name="cjumplist"></a>跳转列表：：跳转列表

构造 `CJumpList` 对象。

```
CJumpList(BOOL bAutoCommit = TRUE);
```

### <a name="parameters"></a>参数

*bAuto提交*<br/>
如果此参数为 FALSE，则列表不会自动提交到析构函数中。

## <a name="cjumplistclearall"></a><a name="clearall"></a>跳转列表：清除所有

删除到目前为止已添加到当前实例`CJumpList`的所有任务和目标。

```cpp
void ClearAll();
```

### <a name="remarks"></a>备注

此方法清除和释放所有数据和内部接口。

## <a name="cjumplistclearalldestinations"></a><a name="clearalldestinations"></a>跳转列表：清除所有目标

删除到目前为止已添加到 CJumpList 当前实例的所有目标。

```cpp
void ClearAllDestinations();
```

### <a name="remarks"></a>备注

如果需要删除到目前为止在目标列表生成会话中添加的所有目标，然后再次添加其他目标，请调用此功能。 如果内部`ICustomDestinationList`已初始化，则它保持活动状态。

## <a name="cjumplistcommitlist"></a><a name="commitlist"></a>跳转列表：提交列表

结束列表生成事务并将报告的列表提交到关联的存储（本例中的注册表）。

```
BOOL CommitList();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

提交是原子的。 如果提交失败，将返回错误。  调用`CommitList`时，将清理当前已删除项的列表。 调用此方法将重置对象，使其没有活动的列表生成事务。 要更新列表，`BeginList`需要再次调用。

## <a name="cjumplistgetdestinationlist"></a><a name="getdestinationlist"></a>跳转列表：获取目的地列表

检索指向目标列表的接口指针。

```
ICustomDestinationList* GetDestinationList();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

如果跳转列表尚未初始化，或已提交或中止，则返回的值将为 NULL。

## <a name="cjumplistgetmaxslots"></a><a name="getmaxslots"></a>跳转列表：获取 MaxSlots

检索最大项目数，包括可在调用应用程序的目标菜单中显示的类别标头。

```
UINT GetMaxSlots() const;
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

应用程序只能报告多个项和类别标头，这些项目和类别标头组合到此值。 如果调用`AppendCategory`、`AppendKnownCategory`或`AddUserTasks`超过此号码，它们将返回失败。

## <a name="cjumplistgetremoveditems"></a><a name="getremoveditems"></a>跳转列表：：获取删除的项目

返回表示已删除目标的项数组。

```
IObjectArray* GetRemovedItems();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

在跳转列表的初始化过程中检索已删除的目标。 生成新目标列表时，应用程序应首先处理删除的目标列表，清除其跟踪数据，以访问删除的列表枚举器返回的任何项。 如果应用程序尝试提供当前调用启动`BeginList`的事务中刚刚删除的项，则重新添加该项的方法调用将失败，以确保应用程序遵守已删除的列表。

## <a name="cjumplistinitializelist"></a><a name="initializelist"></a>跳转列表：：初始化列表

开始列表生成事务。

```
BOOL InitializeList();
```

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

不需要显式调用此方法，除非您希望检索`ICustomDestinationList`指向 的指针，`GetDestinationList`使用 的`GetMaxSlots`可用插槽数或使用 或 使用`GetRemovedItems`的已删除项列表。

## <a name="cjumplistsetappid"></a><a name="setappid"></a>跳转列表：：设置AppID

为要生成的列表设置应用程序用户模型 ID。

```cpp
void SetAppID(LPCTSTR strAppID);
```

### <a name="parameters"></a>参数

*斯特雷帕维德*<br/>
指定应用程序用户模型 ID 的字符串。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
