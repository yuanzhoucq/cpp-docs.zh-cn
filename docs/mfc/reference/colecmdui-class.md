---
title: COleCmdUI 类
ms.date: 07/24/2020
f1_keywords:
- COleCmdUI
- AFXDOCOBJ/COleCmdUI
- AFXDOCOBJ/COleCmdUI::COleCmdUI
- AFXDOCOBJ/COleCmdUI::Enable
- AFXDOCOBJ/COleCmdUI::SetCheck
- AFXDOCOBJ/COleCmdUI::SetText
helpviewer_keywords:
- COleCmdUI [MFC], COleCmdUI
- COleCmdUI [MFC], Enable
- COleCmdUI [MFC], SetCheck
- COleCmdUI [MFC], SetText
ms.assetid: a2d5ce08-6657-45d3-8673-2a9f32d50eec
ms.openlocfilehash: c21d9b504656e6bba5ca693e57958743bb1b8309
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233205"
---
# <a name="colecmdui-class"></a>COleCmdUI 类

实现 MFC 方法以更新与应用程序的 `IOleCommandTarget`驱动功能相关的用户界面对象的状态。

## <a name="syntax"></a>语法

```cpp
class COleCmdUI : public CCmdUI
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COleCmdUI::COleCmdUI](#colecmdui)|构造 `COleCmdUI` 对象。|

### <a name="public-methods"></a>公共方法

|“属性”|说明|
|----------|-----------------|
|[COleCmdUI：： Enable](#enable)|设置或清除 enable 命令标志。|
|[COleCmdUI::SetCheck](#setcheck)|设置开启/关闭切换命令的状态。|
|[COleCmdUI：： SetText](#settext)|返回命令的文本名称或状态字符串。|

## <a name="remarks"></a>备注

在未启用 DocObjects 的应用程序中，当用户在应用程序中查看菜单时，MFC 将处理 UPDATE_COMMAND_UI 利用通知。 为每个通知提供一个[CCmdUI](../../mfc/reference/ccmdui-class.md)对象，该对象可进行操作以反映特定命令的状态。 但是，如果为 DocObjects 启用了应用程序，则 MFC 将处理 UPDATE_OLE_COMMAND_UI 通知并分配 `COleCmdUI` 对象。

`COleCmdUI`允许 DocObject 接收源自其容器的用户界面的命令（如 FileNew、打开、打印等），并允许容器接收源自 DocObject 用户界面的命令。 虽然可 `IDispatch` 用于调度相同的命令，但 `IOleCommandTarget` 提供了更简单的查询和执行方法，因为它依赖于一组标准命令（通常不带参数），并且不涉及任何类型信息。 `COleCmdUI`可用于启用、更新和设置 DocObject 用户界面命令的其他属性。 如果要调用命令，请调用[COleServerDoc：： OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd)。

有关 DocObjects 的详细信息，请参阅[CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)和[CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CCmdUI](../../mfc/reference/ccmdui-class.md)

`COleCmdUI`

## <a name="requirements"></a>要求

**标头：** afxdocob

## <a name="colecmduicolecmdui"></a><a name="colecmdui"></a>COleCmdUI::COleCmdUI

构造 `COleCmdUI` 与特定用户界面命令关联的对象。

```cpp
COleCmdUI(
    OLECMD* rgCmds,
    ULONG cCmds,
    const GUID* m_pGroup);
```

### <a name="parameters"></a>参数

*rgCmds*<br/>
与给定 GUID 相关联的受支持命令的列表。 该 `OLECMD` 结构将命令与命令标志关联起来。

*cCmds*<br/>
*RgCmds*中的命令计数。

*pGroup*<br/>
指向标识一组命令的 GUID 的指针。

### <a name="remarks"></a>备注

`COleCmdUI`对象提供用于更新 DocObject 用户界面对象（如菜单项或控件条按钮）的编程接口。 可以通过对象启用、禁用、检查和/或清除用户界面对象 `COleCmdUI` 。

## <a name="colecmduienable"></a><a name="enable"></a>COleCmdUI：： Enable

调用此函数可将对象的命令标志设置 `COleCmdUI` 为 OLECOMDF_ENABLED，这会告诉接口命令可用并已启用，或者清除命令标志。

```cpp
virtual void Enable(BOOL bOn);
```

### <a name="parameters"></a>参数

*bOn*<br/>
指示是否 `COleCmdUI` 应启用或禁用与对象关联的命令。 非零启用命令;0禁用该命令。

## <a name="colecmduisetcheck"></a><a name="setcheck"></a>COleCmdUI::SetCheck

调用此函数可设置开启/关闭切换命令的状态。

```cpp
virtual void SetCheck(int nCheck);
```

### <a name="parameters"></a>参数

*n*<br/>
一个值，该值确定状态以设置开启/关闭切换命令。 值为：

|值|说明|
|-----------|-----------------|
|**1**|将命令设置为 on。|
|**2**|将命令设置为不确定;无法确定状态，因为此命令的属性处于相关选择的 "打开" 和 "关闭" 状态。|
|任何其他值|将命令设置为 off。|

## <a name="colecmduisettext"></a><a name="settext"></a>COleCmdUI：： SetText

调用此函数可返回命令的文本名称或状态字符串。

```cpp
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>参数

*lpszText*<br/>
指向要与命令一起使用的文本的指针。

## <a name="see-also"></a>另请参阅

[CCmdUI 类](../../mfc/reference/ccmdui-class.md)<br/>
[层次结构图](../../mfc/hierarchy-chart.md)
