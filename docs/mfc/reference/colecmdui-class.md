---
title: COleCmdUI 类
ms.date: 09/12/2018
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
ms.openlocfilehash: 1b7a6b21a3ad778b4a5ca345b1aaf42875810e4e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376269"
---
# <a name="colecmdui-class"></a>COleCmdUI 类

实现 MFC 方法以更新与应用程序的 `IOleCommandTarget`驱动功能相关的用户界面对象的状态。

## <a name="syntax"></a>语法

```
class COleCmdUI : public CCmdUI
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COleCmdUI：COleCmdUI](#colecmdui)|构造 `COleCmdUI` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COleCmdUI：启用](#enable)|设置或清除启用命令标志。|
|[COleCmdUI：：设置检查](#setcheck)|设置开/关切换命令的状态。|
|[COleCmdUI：：设置文本](#settext)|返回命令的文本名称或状态字符串。|

## <a name="remarks"></a>备注

在未为 DocObjects 启用的应用程序中，当用户在应用程序中查看菜单时，MFC 会处理UPDATE_COMMAND_UI。 每个通知都给定一个[CCmdUI](../../mfc/reference/ccmdui-class.md)对象，可以对其进行操作以反映特定命令的状态。 但是，当为 DocObjects 启用应用程序时，MFC 会处理UPDATE_OLE_COMMAND_UI通知`COleCmdUI`并分配对象。

`COleCmdUI`允许 DocObject 接收源自其容器用户界面的命令（如 FileNew、Open、Print 等），并允许容器接收源自 DocObject 用户界面的命令。 尽管`IDispatch`可用于调度相同的命令，但提供了一种`IOleCommandTarget`更简单的查询和执行方法，因为它依赖于一组标准的命令（通常没有参数，并且不涉及类型信息）。 `COleCmdUI`可用于启用、更新和设置 DocObject 用户界面命令的其他属性。 当您要调用该命令时，请致电[COleServerDoc：：OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd)。

有关文档对象的详细信息，请参阅[CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)和[CDocObjectServer 项目](../../mfc/reference/cdocobjectserveritem-class.md)。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CmDUI](../../mfc/reference/ccmdui-class.md)

`COleCmdUI`

## <a name="requirements"></a>要求

**标题：** afxdocobj.h

## <a name="colecmduicolecmdui"></a><a name="colecmdui"></a>COleCmdUI：COleCmdUI

构造与特定`COleCmdUI`用户界面命令关联的对象。

```
COleCmdUI(
    OLECMD* rgCmds,
    ULONG cCmds,
    const GUID* m_pGroup);
```

### <a name="parameters"></a>参数

*rgCmds*<br/>
与给定 GUID 关联的受支持命令的列表。 结构`OLECMD`将命令与命令标志关联。

*cCmds*<br/>
*rgCmds*中命令的计数。

*p组*<br/>
指向标识一组命令的 GUID 的指针。

### <a name="remarks"></a>备注

该`COleCmdUI`对象提供用于更新 DocObject 用户界面对象的编程界面，如菜单项或控制栏按钮。 用户界面对象可以通过`COleCmdUI`该对象启用、禁用、检查和/或清除。

## <a name="colecmduienable"></a><a name="enable"></a>COleCmdUI：启用

调用此函数将`COleCmdUI`对象的命令标志设置为OLECOMDF_ENABLED，该标志告诉接口命令可用并启用，或者清除命令标志。

```
virtual void Enable(BOOL bOn);
```

### <a name="parameters"></a>参数

*邦*<br/>
指示应启用还是禁用与`COleCmdUI`对象关联的命令。 非零启用命令;0 禁用该命令。

## <a name="colecmduisetcheck"></a><a name="setcheck"></a>COleCmdUI：：设置检查

调用此函数以设置开/关切换命令的状态。

```
virtual void SetCheck(int nCheck);
```

### <a name="parameters"></a>参数

*n检查*<br/>
确定要设置开/关切换命令的状态的值。 值为：

|“值”|描述|
|-----------|-----------------|
|**1**|将命令设置为"打开"。|
|**2**|将命令设置为不确定;无法确定状态，因为此命令的属性在相关选择中处于开/关状态。|
|任何其他值|将命令设置为关闭。|

## <a name="colecmduisettext"></a><a name="settext"></a>COleCmdUI：：设置文本

调用此函数以返回命令的文本名称或状态字符串。

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>参数

*lpszText*<br/>
指向要与命令一起使用的文本的指针。

## <a name="see-also"></a>另请参阅

[CmDUI 类](../../mfc/reference/ccmdui-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)
