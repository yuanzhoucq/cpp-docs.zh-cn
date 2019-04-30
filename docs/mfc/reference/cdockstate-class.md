---
title: CDockState 类
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
ms.openlocfilehash: b8c4b80d7182795d8919adb64491d506325976ef
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391174"
---
# <a name="cdockstate-class"></a>CDockState 类

在永久性内存（文件）中加载、卸载或清除一个或多个停靠控件条状态的序列化 `CObject` 类。

## <a name="syntax"></a>语法

```
class CDockState : public CObject
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDockState::Clear](#clear)|清除停靠状态信息。|
|[CDockState::GetVersion](#getversion)|检索存储的版本号栏状态。|
|[CDockState::LoadState](#loadstate)|检索状态信息从注册表或。INI 文件。|
|[CDockState::SaveState](#savestate)|将状态信息保存到注册表或 INI 文件。|

### <a name="public-data-members"></a>公共数据成员

|名称|描述|
|----------|-----------------|
|[CDockState::m_arrBarInfo](#m_arrbarinfo)|指向存储的指针数组停靠包含与每个控件条的一个项的状态信息。|

## <a name="remarks"></a>备注

停靠状态包括大小和位置的栏和停靠。 当检索存储停靠状态，`CDockState`检查栏的位置和栏不可用与当前屏幕设置，`CDockState`缩放栏的位置以使其可见。 主要目的`CDockState`是用于保存多个控件条的整个状态，并允许该状态保存和加载到注册表中，应用程序的。INI 文件，或以二进制形式的一部分`CArchive`对象的内容。

栏可以是任何可停靠控件栏，其中包括工具栏、 状态栏或对话栏。 `CDockState` 编写和读取，或者通过文件中读取对象`CArchive`对象。

[CFrameWnd::GetDockState](../../mfc/reference/cframewnd-class.md#getdockstate)检索框架窗口的状态信息`CControlBar`对象，并将其放`CDockState`对象。 然后可以写入的内容`CDockState`到存储使用对象[Serialize](../../mfc/reference/cobject-class.md#serialize)或[CDockState::SaveState](#savestate)。 如果以后想要还原在框架窗口控件条的状态，可以加载的状态与`Serialize`或[CDockState::LoadState](#loadstate)，然后使用[CFrameWnd::SetDockState](../../mfc/reference/cframewnd-class.md#setdockstate)应用已保存状态设置为框架窗口的控件条。

停靠控件条的详细信息，请参阅文章[控件条](../../mfc/control-bars.md)，[工具栏：停靠和浮动](../../mfc/docking-and-floating-toolbars.md)，并[帧 Windows](../../mfc/frame-windows.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CDockState`

## <a name="requirements"></a>要求

**标头：** afxadv.h

##  <a name="clear"></a>  CDockState::Clear

调用此函数可清除所有停靠的信息存储在`CDockState`对象。

```
void Clear();
```

### <a name="remarks"></a>备注

这包括不仅是否栏固定，但条形图的大小和位置，无论可见。

##  <a name="getversion"></a>  CDockState::GetVersion

调用此函数可检索存储的版本号栏状态。

```
DWORD GetVersion();
```

### <a name="return-value"></a>返回值

1，如果存储的条信息是早于当前状态; 栏2 个如果存储的条信息是与当前相同栏状态。

### <a name="remarks"></a>备注

版本支持，修改后的栏，以添加新的持久性属性，仍将能够检测并加载栏的早期版本创建的持久性状态。

##  <a name="loadstate"></a>  CDockState::LoadState

调用此函数可从注册表中检索状态信息或。INI 文件。

```
void LoadState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>参数

*lpszProfileName*<br/>
指向以 null teminated 字符串，初始化文件或状态信息都存储在 Windows 注册表项中指定的节名称。

### <a name="remarks"></a>备注

配置文件名称是在应用程序的部分。INI 文件或注册表中包含的栏的状态信息。 可以将控制条状态信息保存到注册表或。使用的 INI 文件`SaveState`。

##  <a name="m_arrbarinfo"></a>  CDockState::m_arrBarInfo

一个`CPtrArray`对象，它是指向已保存状态信息在每个控件条的存储的控件栏信息的指针的数组`CDockState`对象。

```
CPtrArray m_arrBarInfo;
```

##  <a name="savestate"></a>  CDockState::SaveState

调用此函数可将状态信息保存到注册表或。INI 文件。

```
void SaveState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>参数

*lpszProfileName*<br/>
指向以 null teminated 字符串，初始化文件或状态信息都存储在 Windows 注册表项中指定的节名称。

### <a name="remarks"></a>备注

配置文件名称是在应用程序的部分。INI 文件或注册表，其中包含控件条状态信息。 `SaveState` 此外将保存当前的屏幕大小。 可以从注册表检索控件条信息或。使用的 INI 文件`LoadState`。

## <a name="see-also"></a>请参阅

[CObject 类](../../mfc/reference/cobject-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
