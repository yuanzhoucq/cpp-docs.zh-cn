---
title: 克多克州类
ms.date: 11/04/2016
f1_keywords:
- CDockState
- AFXADV/CDockState
- AFXADV/CDockState::Clear
- AFXADV/CDockState::GetVersion
- AFXADV/CDockState::LoadState
- AFXADV/CDockState::SaveState
- AFXADV/CDockState::m_arrBarInfo
helpviewer_keywords:
- CDockState [MFC], Clear
- CDockState [MFC], GetVersion
- CDockState [MFC], LoadState
- CDockState [MFC], SaveState
- CDockState [MFC], m_arrBarInfo
ms.assetid: 09e7c10b-3abd-4cb2-ad36-42420fe6bc36
ms.openlocfilehash: 1c76bcda6465ca86b8da4778d3653cb23001b78b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375553"
---
# <a name="cdockstate-class"></a>克多克州类

在永久性内存（文件）中加载、卸载或清除一个或多个停靠控件条状态的序列化 `CObject` 类。

## <a name="syntax"></a>语法

```
class CDockState : public CObject
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDockState：清除](#clear)|清除停靠状态信息。|
|[CDockState：获取版本](#getversion)|检索存储条状态的版本号。|
|[CDockState：：加载状态](#loadstate)|从注册表或 检索状态信息。INI 文件。|
|[CDockState：：保存状态](#savestate)|将状态信息保存到注册表或 INI 文件。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[克多克州：m_arrBarInfo](#m_arrbarinfo)|指向存储的停靠状态信息的指针数组，每个控制栏有一个条目。|

## <a name="remarks"></a>备注

停靠状态包括条形的大小和位置，以及是否停靠。 检索存储的停靠状态时，`CDockState`检查条形图的位置，如果当前屏幕设置不可见，则`CDockState`缩放条形的位置，使其可见。 的主要目的是`CDockState`保持多个控制栏的整个状态，并允许保存该状态并将其加载到注册表，应用程序的 。INI 文件，或作为对象内容的一`CArchive`部分的二进制形式。

该栏可以是任何可停靠的控制栏，包括工具栏、状态栏或对话框栏。 `CDockState`对象通过`CArchive`对象写入和读取到文件或从文件读取。

[CFrameWnd：GetDockState](../../mfc/reference/cframewnd-class.md#getdockstate)检索所有帧窗口`CControlBar`对象的状态信息并将其放入对象中。 `CDockState` 然后，您可以使用`CDockState`[序列化](../../mfc/reference/cobject-class.md#serialize)或[CDockState：：：保存状态](#savestate)将对象的内容写入存储。 如果以后要还原框架窗口中控制栏的状态，则可以使用`Serialize`或[CDockState：LoadState](#loadstate)加载状态，然后使用[CFrameWnd：：SetDockState](../../mfc/reference/cframewnd-class.md#setdockstate)将保存的状态应用于帧窗口的控制栏。

有关停靠控制栏的详细信息，请参阅[文章"控件栏](../../mfc/control-bars.md)"、[工具栏：停靠和浮动](../../mfc/docking-and-floating-toolbars.md)，以及[框架窗口](../../mfc/frame-windows.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CDockState`

## <a name="requirements"></a>要求

**标题：** afxadv.h

## <a name="cdockstateclear"></a><a name="clear"></a>CDockState：清除

调用此函数以清除存储在对象中的所有`CDockState`停靠信息。

```
void Clear();
```

### <a name="remarks"></a>备注

这不仅包括柱线是否停靠，还包括条形的大小和位置以及它是否可见。

## <a name="cdockstategetversion"></a><a name="getversion"></a>CDockState：获取版本

调用此函数以检索存储的条形状态的版本号。

```
DWORD GetVersion();
```

### <a name="return-value"></a>返回值

如果存储的条形信息早于当前条形状态，则为 1;2 如果存储的条形信息与当前条形状态相同。

### <a name="remarks"></a>备注

版本支持使修订后的柱线能够添加新的持久属性，并且仍然能够检测和加载由早期版本的条形创建的持续状态。

## <a name="cdockstateloadstate"></a><a name="loadstate"></a>CDockState：：加载状态

调用此函数从注册表或 检索状态信息。INI 文件。

```
void LoadState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>参数

*lpsz配置文件名称*<br/>
指向一个空事件字符串，该字符串指定初始化文件中的节的名称或存储状态信息的 Windows 注册表中的键。

### <a name="remarks"></a>备注

配置文件名称是应用程序的 部分。INI 文件或包含条形的状态信息的注册表。 您可以将控件栏状态信息保存到注册表或 。INI 文件`SaveState`与 。

## <a name="cdockstatem_arrbarinfo"></a><a name="m_arrbarinfo"></a>克多克州：m_arrBarInfo

对象`CPtrArray`，它是指向在对象中保存状态信息的每个控件栏的存储控制栏信息的`CDockState`指针数组。

```
CPtrArray m_arrBarInfo;
```

## <a name="cdockstatesavestate"></a><a name="savestate"></a>CDockState：：保存状态

调用此函数以将状态信息保存到注册表或 。INI 文件。

```
void SaveState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>参数

*lpsz配置文件名称*<br/>
指向一个空事件字符串，该字符串指定初始化文件中的节的名称或存储状态信息的 Windows 注册表中的键。

### <a name="remarks"></a>备注

配置文件名称是应用程序的 部分。INI 文件或包含控制栏状态信息的注册表。 `SaveState`还保存当前屏幕大小。 可以从注册表或 检索控件栏信息。INI 文件`LoadState`与 。

## <a name="see-also"></a>另请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
