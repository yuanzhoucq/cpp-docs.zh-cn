---
title: CMFCCmdUsageCount 类
ms.date: 11/04/2016
f1_keywords:
- CMFCCmdUsageCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::AddCmd
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::GetCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::HasEnoughInformation
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::IsFreqeuntlyUsedCmd
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::Reset
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::Serialize
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::SetOptions
helpviewer_keywords:
- CMFCCmdUsageCount [MFC], AddCmd
- CMFCCmdUsageCount [MFC], GetCount
- CMFCCmdUsageCount [MFC], HasEnoughInformation
- CMFCCmdUsageCount [MFC], IsFreqeuntlyUsedCmd
- CMFCCmdUsageCount [MFC], Reset
- CMFCCmdUsageCount [MFC], Serialize
- CMFCCmdUsageCount [MFC], SetOptions
ms.assetid: 9c33b783-37c0-43ea-9f31-3c75e246c841
ms.openlocfilehash: b4ad9a60831feb6fa1147ea3f8bcfd5c6badd06c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403797"
---
# <a name="cmfccmdusagecount-class"></a>CMFCCmdUsageCount 类

跟踪 Windows 消息，例如当用户从菜单选择项的使用的计数。

## <a name="syntax"></a>语法

```
class CMFCCmdUsageCount : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|||
|-|-|
|名称|描述|
|`CMFCCmdUsageCount::CMFCCmdUsageCount`|默认构造函数。|
|`CMFCCmdUsageCount::~CMFCCmdUsageCount`|析构函数。|

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|描述|
|[CMFCCmdUsageCount::AddCmd](#addcmd)|一个与给定命令关联的计数器递增。|
|[CMFCCmdUsageCount::GetCount](#getcount)|检索与给定的命令 ID 相关联的使用情况计数|
|[CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)|确定此对象是否具有收集跟踪数据的最小数量。|
|[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)|确定是否频繁使用给定的命令。|
|[CMFCCmdUsageCount::Reset](#reset)|清除所有命令的使用计数。|
|[CMFCCmdUsageCount::Serialize](#serialize)|从存档读取此对象或将其写入到存档。 （重写 [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)。）|
|[CMFCCmdUsageCount::SetOptions](#setoptions)|集的值共享`CMFCCmdUsageCount`类数据成员。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|名称|描述|
|`m_CmdUsage`|一个`CMap`将命令映射到其使用情况计数的对象。|
|`m_nMinUsagePercentage`|用于要经常使用的命令的最小使用率百分比。|
|`m_nStartCount`|开始计数器，它用于确定此对象是否具有收集跟踪数据的最小数量。|
|`m_nTotalUsage`|所有已跟踪的命令数。|

### <a name="remarks"></a>备注

`CMFCCmdUsageCount`类将每个数字的 Windows 消息标识符映射到一个 32 位无符号的整数的计数器。 `CMFCToolBar` 使用此类来显示常用工具栏项。 有关详细信息`CMFCToolBar`，请参阅[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)。

您可以保留`CMFCCmdUsageCount`类运行的应用程序之间的数据。 使用[CMFCCmdUsageCount::Serialize](#serialize)方法以序列化类成员数据和[CMFCCmdUsageCount::SetOptions](#setoptions)方法以设置共享的成员数据。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)

## <a name="requirements"></a>要求

**标头：** afxcmdusagecount.h

##  <a name="addcmd"></a>  CMFCCmdUsageCount::AddCmd

一个与给定命令关联的计数器递增。

```
void AddCmd(UINT uiCmd);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*uiCmd*|[in]指定命令计数器递增。|

### <a name="remarks"></a>备注

此方法将新条目添加到命令计数站点地图结构`m_CmdUsage`，如果该条目不存在。

在以下情况下该方法无效：

- 工具栏框架是在自定义模式 ( [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)方法返回一个非零值)。

- 该命令是指子菜单或菜单的分隔符 ( *uiCmd*等于 0 或-1)。

- *uiCmd*指的是标准命令 (全局`IsStandardCommand`函数返回非零值)。

##  <a name="getcount"></a>  CMFCCmdUsageCount::GetCount

检索与给定的命令 ID 相关联的使用情况计数

```
UINT GetCount(UINT uiCmd) const;
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*uiCmd*|[in]要检索命令计数器的 ID。|

### <a name="return-value"></a>返回值

与给定的命令 ID 相关联的使用情况计数

##  <a name="hasenoughinformation"></a>  CMFCCmdUsageCount::HasEnoughInformation

确定此对象是否已接收到最小数量的跟踪数据。

```
BOOL HasEnoughInformation() const;
```

### <a name="return-value"></a>返回值

如果此对象已收到最小数量的跟踪数据; 非零值否则为 0。

### <a name="remarks"></a>备注

如果此方法返回一个非零值的总计数`m_nTotalUsage`，所有已跟踪的命令是等于或大于初始计数， `m_nStartCount`。 默认情况下，框架将设置初始计数 0。 可以通过重写此值[CMFCCmdUsageCount::SetOptions](#setoptions)方法。

此方法可供[CMFCMenuBar::IsShowAllCommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands)以确定是否显示所有可用的菜单命令。

##  <a name="isfreqeuntlyusedcmd"></a>  CMFCCmdUsageCount::IsFreqeuntlyUsedCmd

确定是否频繁使用给定的命令。

```
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*uiCmd*|[in]指定要检查的命令。|

### <a name="return-value"></a>返回值

如果经常使用该命令; 非零值否则为 0。

### <a name="remarks"></a>备注

此方法返回 0，如果总命令的用法， `m_nTotalUsage`，为 0。 否则，此方法返回非零，如果指定的命令使用其中的百分比值大于最小的百分比， `m_nMinUsagePercentage`。 默认情况下，框架将最小百分比设置为 5。 可以通过重写此值[CMFCCmdUsageCount::SetOptions](#setoptions)方法。 如果最小百分比为 0，则此方法返回非零，如果指定的命令计数大于 0。

[CMFCToolBar::IsCommandRarelyUsed](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused)使用此方法来确定命令是否很少使用。

##  <a name="reset"></a>  CMFCCmdUsageCount::Reset

清除所有命令的使用计数。

```
void Reset();
```

### <a name="remarks"></a>备注

调用此方法以清除命令计数站点地图结构中的所有条目`m_CmdUsage`，以及重置总命令的用法， `m_nTotalUsage`、 计数器为 0。

##  <a name="serialize"></a>  CMFCCmdUsageCount::Serialize

从存档读取此对象或将其写入到存档。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*ar*|[in]一个`CArchive`要从 / 向序列化对象。|

### <a name="remarks"></a>备注

此方法序列化的命令计数映射结构`m_CmdUsage`，并总命令的用法， `m_nTotalUsage`、 计数器或指定的存档。

有关序列化示例，请参阅[序列化：将对象序列化为](../../mfc/serialization-serializing-an-object.md)。

##  <a name="setoptions"></a>  CMFCCmdUsageCount::SetOptions

集的值共享`CMFCCmdUsageCount`类数据成员。

```
static BOOL __stdcall SetOptions(
    UINT nStartCount,
    UINT nMinUsagePercentage);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|描述|
|*nStartCount*|[in]新初始计数为所有已跟踪的命令。|
|*nMinUsagePercentage*|[in]新的最小使用率百分比。|

### <a name="return-value"></a>返回值

如果该方法成功，FALSE 如果为 TRUE *nMinUsagePercentage*参数为大于或等于 100。

### <a name="remarks"></a>备注

此方法设置共享`CMFCCmdUsageCount`类数据成员`m_nStartCount`并`m_nMinUsagePercentage`到*nStartCount*并*nMinUsagePercentage*分别。 `m_nStartCount` 可供[CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)方法来确定此对象是否具有收集跟踪数据的最小数量。 `m_nMinUsagePercentage` 可供[将 Cmfccmdusagecount](#isfreqeuntlyusedcmd)方法，以确定是否频繁使用给定的命令。

在调试版本中此方法将生成断言失败如果*nMinUsagePercentage*参数为大于或等于 100。

## <a name="see-also"></a>请参阅

[层次结构图](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)
