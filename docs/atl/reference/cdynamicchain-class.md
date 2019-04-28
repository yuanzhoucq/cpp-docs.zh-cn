---
title: CDynamicChain 类
ms.date: 11/04/2016
f1_keywords:
- CDynamicChain
- ATLWIN/ATL::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CallChain
- ATLWIN/ATL::CDynamicChain::RemoveChainEntry
- ATLWIN/ATL::CDynamicChain::SetChainEntry
helpviewer_keywords:
- message maps, chaining
- chaining message maps
- CDynamicChain class
ms.assetid: f084b2be-0e77-4836-973d-ae278a1e9da8
ms.openlocfilehash: 4b68198c17d7bd030b88bc78ad4de1367c914703
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258996"
---
# <a name="cdynamicchain-class"></a>CDynamicChain 类

此类提供了支持消息映射的动态链接的方法。

> [!IMPORTANT]
>  不能在 Windows 运行时中执行的应用程序中使用此类和其成员。

## <a name="syntax"></a>语法

```
class CDynamicChain
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CDynamicChain::CDynamicChain](#cdynamicchain)|构造函数。|
|[CDynamicChain:: ~ CDynamicChain](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CDynamicChain::CallChain](#callchain)|将定向到另一个对象的消息映射的 Windows 消息。|
|[CDynamicChain::RemoveChainEntry](#removechainentry)|从集合中移除消息映射条目。|
|[CDynamicChain::SetChainEntry](#setchainentry)|将消息映射条目添加到集合或修改的现有条目。|

## <a name="remarks"></a>备注

`CDynamicChain` 管理消息映射，启用 Windows 消息定向，在运行时，另一个对象的消息映射到的集合。

若要添加支持的消息映射的动态链接，请执行以下操作：

- 派生您的类从`CDynamicChain`。 在消息映射中指定[CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic)链接到另一个对象的默认消息映射宏。

- 你想要从链接到每个的类的派生[CMessageMap](../../atl/reference/cmessagemap-class.md)。 `CMessageMap` 允许对象来公开其消息映射到其他对象。

- 调用`CDynamicChain::SetChainEntry`以确定哪个对象和消息映射您希望链接到。

例如，假设您的类定义，如下所示：

[!code-cpp[NVC_ATL_Windowing#88](../../atl/codesnippet/cpp/cdynamicchain-class_1.h)]

然后客户端调用`CMyWindow::SetChainEntry`:

[!code-cpp[NVC_ATL_Windowing#89](../../atl/codesnippet/cpp/cdynamicchain-class_2.cpp)]

其中`chainedObj`是链接的对象，是派生自的类的实例`CMessageMap`。 现在，如果`myCtl`接收一条消息，未由`OnPaint`或`OnSetFocus`，窗口过程将定向到的消息`chainedObj`的默认消息映射。

有关消息映射链接的详细信息，请参阅[消息映射](../../atl/message-maps-atl.md)在文章"ATL 窗口类。"

## <a name="requirements"></a>要求

**标头：** atlwin.h

##  <a name="callchain"></a>  CDynamicChain::CallChain

将定向到另一个对象的消息映射的 Windows 消息。

```
BOOL CallChain(
    DWORD dwChainID,
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT& lResult);
```

### <a name="parameters"></a>参数

*dwChainID*<br/>
[in]使用链接的对象和其消息映射关联的唯一标识符。

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

### <a name="return-value"></a>返回值

如果消息已完全处理，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

有关调用的窗口过程`CallChain`，则必须指定[CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic)消息映射中的宏。 有关示例，请参阅[CDynamicChain](../../atl/reference/cdynamicchain-class.md)概述。

`CallChain` 要求对以前调用[SetChainEntry](#setchainentry)关联*dwChainID*值，该值具有对象并将其消息映射。

##  <a name="cdynamicchain"></a>  CDynamicChain::CDynamicChain

构造函数。

```
CDynamicChain();
```

##  <a name="dtor"></a>  CDynamicChain:: ~ CDynamicChain

析构函数。

```
~CDynamicChain();
```

### <a name="remarks"></a>备注

释放所有已分配的资源。

##  <a name="removechainentry"></a>  CDynamicChain::RemoveChainEntry

从集合中移除指定的消息映射。

```
BOOL RemoveChainEntry(DWORD dwChainID);
```

### <a name="parameters"></a>参数

*dwChainID*<br/>
[in]使用链接的对象和其消息映射关联的唯一标识符。 最初定义此值通过调用[SetChainEntry](#setchainentry)。

### <a name="return-value"></a>返回值

如果已成功从集合中移除的消息映射，则为 TRUE。 否则为 FALSE。

##  <a name="setchainentry"></a>  CDynamicChain::SetChainEntry

向集合添加指定的消息映射。

```
BOOL SetChainEntry(
    DWORD dwChainID,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);
```

### <a name="parameters"></a>参数

*dwChainID*<br/>
[in]使用链接的对象和其消息映射关联的唯一标识符。

*pObject*<br/>
[in]指向声明消息映射的链接对象的指针。 此对象必须派生自[CMessageMap](../../atl/reference/cmessagemap-class.md)。

*dwMsgMapID*<br/>
[in]消息映射中的链接对象的标识符。 默认值为 0，它标识使用声明的默认消息映射[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)。 若要指定备选的消息映射声明与[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)，将传递`msgMapID`。

### <a name="return-value"></a>返回值

如果已成功添加到集合中的消息映射，则为 TRUE。 否则为 FALSE。

### <a name="remarks"></a>备注

如果*dwChainID*集合中已经存在值，其关联的对象和消息映射由取代*pObject*并*dwMsgMapID*分别。 否则，添加新条目。

## <a name="see-also"></a>请参阅

[CWindowImpl 类](../../atl/reference/cwindowimpl-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
