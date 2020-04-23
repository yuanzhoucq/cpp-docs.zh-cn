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
ms.openlocfilehash: 02b302ec38922128190a6f20ce2f156b52383b55
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752591"
---
# <a name="cmfccmdusagecount-class"></a>CMFCCmdUsageCount 类

跟踪 Windows 消息的使用计数，例如当用户从菜单中选择项目时。

## <a name="syntax"></a>语法

```
class CMFCCmdUsageCount : public CObject
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|||
|-|-|
|名称|说明|
|`CMFCCmdUsageCount::CMFCCmdUsageCount`|默认构造函数。|
|`CMFCCmdUsageCount::~CMFCCmdUsageCount`|析构函数。|

### <a name="public-methods"></a>公共方法

|||
|-|-|
|名称|说明|
|[CMFCCmd 使用计数：添加Cmd](#addcmd)|增加与给定命令关联的计数器的一个。|
|[CMFCCmd 使用计数：获取计数](#getcount)|检索与给定命令 ID 关联的使用计数。|
|[CMFCCmd 使用计数：：有足够信息](#hasenoughinformation)|确定此对象是否已收集最小数量的跟踪数据。|
|[CMFCCmd 使用计数： IsFreqeuntly使用Cmd](#isfreqeuntlyusedcmd)|确定是否经常使用给定命令。|
|[CMFCCmd 使用计数：重置](#reset)|清除所有命令的使用情况计数。|
|[CMFCCmd 使用计数：序列化](#serialize)|从存档中读取此对象或将其写入存档。 （重写 [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)。）|
|[CMFCCmd使用计数：：设置选项](#setoptions)|设置共享`CMFCCmdUsageCount`类数据成员的值。|

### <a name="data-members"></a>数据成员

|||
|-|-|
|名称|说明|
|`m_CmdUsage`|将`CMap`命令映射到其用法计数的对象。|
|`m_nMinUsagePercentage`|经常使用命令的最低使用百分比。|
|`m_nStartCount`|用于确定此对象是否已收集最小数量的跟踪数据的起始计数器。|
|`m_nTotalUsage`|所有跟踪命令的计数。|

### <a name="remarks"></a>备注

该`CMFCCmdUsageCount`类将每个数字 Windows 消息标识符映射到 32 位未签名的整数计数器。 `CMFCToolBar`使用此类显示常用工具栏项。 有关 的详细信息`CMFCToolBar`，请参阅[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)。

您可以在程序运行`CMFCCmdUsageCount`之间保留类数据。 使用[CMFCCmdUseCount：：序列化](#serialize)方法序列化类成员数据，使用[CMFCCmdUseCount：：SetOptions](#setoptions)方法设置共享成员数据。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CMFCCmd使用计数](../../mfc/reference/cmfccmdusagecount-class.md)

## <a name="requirements"></a>要求

**标题：** afxcmd 用法计数.h

## <a name="cmfccmdusagecountaddcmd"></a><a name="addcmd"></a>CMFCCmd 使用计数：添加Cmd

增加与给定命令关联的计数器的一个。

```cpp
void AddCmd(UINT uiCmd);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*乌伊Cmd*|[在]指定命令计数器以递增。|

### <a name="remarks"></a>备注

此方法向命令计数的地图结构添加新条目，`m_CmdUsage`如果该条目不存在。

在以下情况下，此方法不执行任何操作：

- 工具栏框架处于自定义模式[（CMFCToolBar：is自定义模式](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)方法返回非零值）。

- 该命令引用子菜单或菜单分隔符 *（uiCmd*等于 0 或 -1）。

- *uiCmd*引用标准命令（全局`IsStandardCommand`函数返回非零值）。

## <a name="cmfccmdusagecountgetcount"></a><a name="getcount"></a>CMFCCmd 使用计数：获取计数

检索与给定命令 ID 关联的使用计数。

```
UINT GetCount(UINT uiCmd) const;
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*乌伊Cmd*|[在]要检索的命令计数器的 ID。|

### <a name="return-value"></a>返回值

与给定命令 ID 关联的用法计数。

## <a name="cmfccmdusagecounthasenoughinformation"></a><a name="hasenoughinformation"></a>CMFCCmd 使用计数：：有足够信息

确定此对象是否已收到最小数量的跟踪数据。

```
BOOL HasEnoughInformation() const;
```

### <a name="return-value"></a>返回值

如果此对象已收到最小数量的跟踪数据，则非零;否则 0。

### <a name="remarks"></a>备注

如果所有跟踪命令的总计计数`m_nTotalUsage`等于或大于初始计数，`m_nStartCount`则此方法返回非零值。 默认情况下，框架设置初始计数 0。 您可以使用[CMFCCmd 使用计数：：设置选项](#setoptions)方法覆盖此值。

此方法由[CMFCMenuBar：：IsShowAllCommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands)用于确定是否显示所有可用的菜单命令。

## <a name="cmfccmdusagecountisfreqeuntlyusedcmd"></a><a name="isfreqeuntlyusedcmd"></a>CMFCCmd 使用计数： IsFreqeuntly使用Cmd

确定是否经常使用给定命令。

```
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*乌伊Cmd*|[在]指定要检查的命令。|

### <a name="return-value"></a>返回值

如果经常使用该命令，则非零;否则 0。

### <a name="remarks"></a>备注

如果总命令用法为 0，`m_nTotalUsage`则此方法返回 0。 否则，如果使用指定命令的百分比大于最小百分比，`m_nMinUsagePercentage`则此方法返回非零。 默认情况下，框架将最小百分比设置为 5。 您可以使用[CMFCCmd 使用计数：：设置选项](#setoptions)方法覆盖此值。 如果最小百分比为 0，则如果指定的命令计数大于 0，此方法将返回非零。

[CMFCToolBar：IsCommand很少使用](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused)此方法来确定是否很少使用命令。

## <a name="cmfccmdusagecountreset"></a><a name="reset"></a>CMFCCmd 使用计数：重置

清除所有命令的使用情况计数。

```cpp
void Reset();
```

### <a name="remarks"></a>备注

调用此方法以清除命令计数的映射结构中的所有条目，`m_CmdUsage`并将总命令用法重置为`m_nTotalUsage`0。

## <a name="cmfccmdusagecountserialize"></a><a name="serialize"></a>CMFCCmd 使用计数：序列化

从存档中读取此对象，或将其写入存档。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*ar*|[在]`CArchive`要序列化的对象。|

### <a name="remarks"></a>备注

此方法序列化命令计数的映射结构、`m_CmdUsage`和总命令用法，`m_nTotalUsage`从指定存档或到指定的存档。

有关序列化示例，请参阅[序列化：序列化对象](../../mfc/serialization-serializing-an-object.md)。

## <a name="cmfccmdusagecountsetoptions"></a><a name="setoptions"></a>CMFCCmd使用计数：：设置选项

设置共享`CMFCCmdUsageCount`类数据成员的值。

```
static BOOL __stdcall SetOptions(
    UINT nStartCount,
    UINT nMinUsagePercentage);
```

### <a name="parameters"></a>参数

|||
|-|-|
|参数|说明|
|*n 开始计数*|[在]所有跟踪命令的新初始计数。|
|*nMinUsage百分比*|[在]新的最小使用百分比。|

### <a name="return-value"></a>返回值

如果方法成功，则为 TRUE，如果*nMinUsage 百分比*参数大于或等于 100，则 FALSE。

### <a name="remarks"></a>备注

此方法分别设置`CMFCCmdUsageCount`共享类数据成员`m_nStartCount`和`m_nMinUsagePercentage` *nStartCount*和*nMinUsage 百分比*。 `m_nStartCount`[由 CMFCCmdUsageCount：：HasOfof 信息](#hasenoughinformation)方法用于确定此对象是否已收集最小数量的跟踪数据。 `m_nMinUsagePercentage`[由 CMFCCmdUsageCount 使用：IsFreqeuntly使用Cmd](#isfreqeuntlyusedcmd)方法来确定是否经常使用给定命令。

在调试生成中，如果*nMinUsage 百分比*参数大于或等于 100，此方法将生成断言失败。

## <a name="see-also"></a>请参阅

[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[类](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 类](../../mfc/reference/cmfctoolbar-class.md)
