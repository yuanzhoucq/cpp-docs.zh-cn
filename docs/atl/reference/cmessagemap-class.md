---
title: CMessageMap 类
ms.date: 11/04/2016
f1_keywords:
- CMessageMap
- ATLWIN/ATL::CMessageMap
- ATLWIN/ATL::CMessageMap::ProcessWindowMessage
helpviewer_keywords:
- CMessageMap class
- message maps, ATL
- ATL, message handlers
ms.assetid: 1f97bc16-a8a0-4cf0-b90f-1778813a5c8e
ms.openlocfilehash: a822f36d6b6fd49301d8240324e27f0ad9ce52e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326723"
---
# <a name="cmessagemap-class"></a>CMessageMap 类

此类允许对象的消息映射由另一个对象访问。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class ATL_NO_VTABLE CMessageMap
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CMessageMap：:P窗口消息](#processwindowmessage)|访问派生类中`CMessageMap`的消息映射。|

## <a name="remarks"></a>备注

`CMessageMap`是一个抽象基类，允许对象的消息映射被另一个对象访问。 为了使对象公开其消息映射，其类必须派生自`CMessageMap`。

ATL`CMessageMap`用于支持包含的窗口和动态消息映射链接。 例如，任何包含[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)对象的类都必须派生自`CMessageMap`。 以下代码取自[SUBEDIT](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)示例。 通过[CComControl，](../../atl/reference/ccomcontrol-class.md)`CAtlEdit`类自动派生自`CMessageMap`。

[!code-cpp[NVC_ATL_Windowing#90](../../atl/codesnippet/cpp/cmessagemap-class_1.h)]

因为包含的窗口 将在`m_EditCtrl`包含类中使用消息映射，`CAtlEdit`派生自`CMessageMap`。

有关消息映射的详细信息，请参阅文章"ATL 窗口类"中[的消息映射](../../atl/message-maps-atl.md)。

## <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="cmessagemapprocesswindowmessage"></a><a name="processwindowmessage"></a>CMessageMap：:P窗口消息

访问*dwMsgMapID*在`CMessageMap`派生类中标识的消息映射。

```
virtual BOOL ProcessWindowMessage(
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT& lResult,
    DWORD dwMsgMapID) = 0;
```

### <a name="parameters"></a>参数

*hwnd*<br/>
[在]接收消息的窗口的句柄。

*乌姆斯格*<br/>
[在]发送到窗口的消息。

*wParam*<br/>
[在]其他特定于消息的信息。

*lParam*<br/>
[在]其他特定于消息的信息。

*lResult*<br/>
[出]消息处理的结果。

*dwMsgMapID*<br/>
[在]将处理消息的消息映射的标识符。 默认消息映射（使用[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)声明）由 0 标识。 使用[ALT_MSG_MAP （msgMapID）](message-map-macros-atl.md#alt_msg_map)声明的替代消息映射由 标识`msgMapID`。

### <a name="return-value"></a>返回值

如果消息已完全处理，则为 TRUE;如果消息已完全处理，则为 TRUE。否则，FALSE。

### <a name="remarks"></a>备注

由[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)对象的窗口过程或动态链接到消息映射的对象的窗口过程调用。

## <a name="see-also"></a>另请参阅

[CDynamicChain 类](../../atl/reference/cdynamicchain-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP（msgMapID）](message-map-macros-atl.md#alt_msg_map)<br/>
[类概述](../../atl/atl-class-overview.md)
