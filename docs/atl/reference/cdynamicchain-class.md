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
ms.openlocfilehash: 4a72b3b4308ed83dfdc4a2895a04d1fe9a177ce5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327032"
---
# <a name="cdynamicchain-class"></a>CDynamicChain 类

此类提供支持消息映射动态链接的方法。

> [!IMPORTANT]
> 此类及其成员不能在 Windows 运行时中执行的应用程序中使用。

## <a name="syntax"></a>语法

```
class CDynamicChain
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C动态链：C动态链](#cdynamicchain)|构造函数。|
|[C动态链：*C动态链](#dtor)|析构函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CDynamic链：呼叫链](#callchain)|将 Windows 消息定向到另一个对象的消息映射。|
|[CDynamic链：：删除链入口](#removechainentry)|从集合中删除消息映射条目。|
|[CDynamic链：：设置链入口](#setchainentry)|向集合添加消息映射条目或修改现有条目。|

## <a name="remarks"></a>备注

`CDynamicChain`管理消息映射的集合，使 Windows 消息在运行时定向到另一个对象的消息映射。

要添加对消息映射动态链接的支持，请执行以下操作：

- 从 派生类`CDynamicChain`从 。 在消息映射中，指定[CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic)宏以链接到另一个对象的默认消息映射。

- 派生要从[CMessageMap](../../atl/reference/cmessagemap-class.md)链接到的每个类。 `CMessageMap`允许对象将其消息映射公开给其他对象。

- 调用`CDynamicChain::SetChainEntry`以标识要链接到的对象和消息映射。

例如，假设您的类定义如下：

[!code-cpp[NVC_ATL_Windowing#88](../../atl/codesnippet/cpp/cdynamicchain-class_1.h)]

然后，客户端调用`CMyWindow::SetChainEntry`：

[!code-cpp[NVC_ATL_Windowing#89](../../atl/codesnippet/cpp/cdynamicchain-class_2.cpp)]

链接`chainedObj`对象的位置，是从 派生的类的实例`CMessageMap`。 现在，如果`myCtl`收到`OnPaint`或`OnSetFocus`未处理的消息，窗口过程将消息定向到`chainedObj`默认消息映射。

有关邮件映射链接的详细信息，请参阅文章"ATL 窗口类"中[的消息映射](../../atl/message-maps-atl.md)。

## <a name="requirements"></a>要求

**标题：** atlwin.h

## <a name="cdynamicchaincallchain"></a><a name="callchain"></a>CDynamic链：呼叫链

将 Windows 消息定向到另一个对象的消息映射。

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
[在]与链接对象及其消息映射关联的唯一标识符。

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

### <a name="return-value"></a>返回值

如果消息已完全处理，则为 TRUE;如果消息已完全处理，则为 TRUE。否则，FALSE。

### <a name="remarks"></a>备注

要调用`CallChain`窗口过程，必须在消息映射中指定[CHAIN_MSG_MAP_DYNAMIC](message-map-macros-atl.md#chain_msg_map_dynamic)宏。 例如，请参阅[CDynamicChain](../../atl/reference/cdynamicchain-class.md)概述。

`CallChain`需要对[SetChainEntry](#setchainentry)进行以前的调用，才能将*dwChainID*值与对象及其消息映射相关联。

## <a name="cdynamicchaincdynamicchain"></a><a name="cdynamicchain"></a>C动态链：C动态链

构造函数。

```
CDynamicChain();
```

## <a name="cdynamicchaincdynamicchain"></a><a name="dtor"></a>C动态链：*C动态链

析构函数。

```
~CDynamicChain();
```

### <a name="remarks"></a>备注

释放所有分配的资源。

## <a name="cdynamicchainremovechainentry"></a><a name="removechainentry"></a>CDynamic链：：删除链入口

从集合中删除指定的消息映射。

```
BOOL RemoveChainEntry(DWORD dwChainID);
```

### <a name="parameters"></a>参数

*dwChainID*<br/>
[在]与链接对象及其消息映射关联的唯一标识符。 您最初通过调用[SetChainEntry](#setchainentry)来定义此值。

### <a name="return-value"></a>返回值

如果消息映射从集合成功删除，则为 TRUE。 否则为 FALSE。

## <a name="cdynamicchainsetchainentry"></a><a name="setchainentry"></a>CDynamic链：：设置链入口

将指定的消息映射添加到集合中。

```
BOOL SetChainEntry(
    DWORD dwChainID,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);
```

### <a name="parameters"></a>参数

*dwChainID*<br/>
[在]与链接对象及其消息映射关联的唯一标识符。

*pObject*<br/>
[在]指向声明消息映射的链条对象的指针。 此对象必须派生自[CMessageMap](../../atl/reference/cmessagemap-class.md)。

*dwMsgMapID*<br/>
[在]链接对象中消息映射的标识符。 默认值为 0，它标识使用[BEGIN_MSG_MAP](message-map-macros-atl.md#begin_msg_map)声明的默认消息映射。 要指定使用[ALT_MSG_MAP（msgMapID）](message-map-macros-atl.md#alt_msg_map)声明的备用消息映射`msgMapID`，请通过 。

### <a name="return-value"></a>返回值

如果消息映射已成功添加到集合中，则为 TRUE。 否则为 FALSE。

### <a name="remarks"></a>备注

如果集合中已存在*dwChainID*值，则其关联的对象和消息映射将分别替换为*pObject*和*dwMsgMapID。* 否则，将添加新条目。

## <a name="see-also"></a>另请参阅

[CWindowImpl 类](../../atl/reference/cwindowimpl-class.md)<br/>
[类概述](../../atl/atl-class-overview.md)
