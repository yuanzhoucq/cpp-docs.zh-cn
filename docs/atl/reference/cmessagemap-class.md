---
title: CMessageMap 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CMessageMap
- ATLWIN/ATL::CMessageMap
- ATLWIN/ATL::CMessageMap::ProcessWindowMessage
dev_langs:
- C++
helpviewer_keywords:
- CMessageMap class
- message maps, ATL
- ATL, message handlers
ms.assetid: 1f97bc16-a8a0-4cf0-b90f-1778813a5c8e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f09347fdfaaf20e465e5be05ce446dfec449526
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024380"
---
# <a name="cmessagemap-class"></a>CMessageMap 类

此类允许对象的消息映射为另一个对象的访问权限。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
class ATL_NO_VTABLE CMessageMap
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CMessageMap::ProcessWindowMessage](#processwindowmessage)|访问消息映射中的`CMessageMap`-派生的类。|

## <a name="remarks"></a>备注

`CMessageMap` 是一个抽象基类，允许对象的消息映射来访问另一个对象。 为了使对象公开其消息映射，它的类必须派生自`CMessageMap`。

使用 ATL`CMessageMap`到支持包含 windows 和动态消息映射链接。 例如，任何类包含[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)对象必须派生自`CMessageMap`。 以下代码摘自[SUBEDIT](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)示例。 通过[CComControl](../../atl/reference/ccomcontrol-class.md)，则`CAtlEdit`类自动派生`CMessageMap`。

[!code-cpp[NVC_ATL_Windowing#90](../../atl/codesnippet/cpp/cmessagemap-class_1.h)]

因为包含的窗口中， `m_EditCtrl`，将使用消息映射中包含的类，`CAtlEdit`派生自`CMessageMap`。

有关消息映射的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)在文章"ATL 窗口类。"

## <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="processwindowmessage"></a>  CMessageMap::ProcessWindowMessage

访问由标识的消息映射*dwMsgMapID*中`CMessageMap`-派生的类。

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

*hWnd*<br/>
[in]接收消息的窗口句柄。

*uMsg*<br/>
[in]发送到窗口的消息。

*wParam*<br/>
[in]其他特定于消息的信息。

*lParam*<br/>
[in]其他特定于消息的信息。

*lResult*<br/>
[out]消息处理的结果。

*dwMsgMapID*<br/>
[in]将处理该消息的消息映射的标识符。 使用默认消息映射声明[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)，由 0。 使用替换消息映射声明[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)，由`msgMapID`。

### <a name="return-value"></a>返回值

如果该消息完全处理; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

调用的窗口过程[CContainedWindow](../../atl/reference/ccontainedwindowt-class.md)对象或对象的动态链接到的消息映射。

## <a name="see-also"></a>请参阅

[CDynamicChain 类](../../atl/reference/cdynamicchain-class.md)<br/>
[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)<br/>
[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)<br/>
[类概述](../../atl/atl-class-overview.md)
