---
title: COleMessageFilter 类
ms.date: 11/04/2016
f1_keywords:
- COleMessageFilter
- AFXOLE/COleMessageFilter
- AFXOLE/COleMessageFilter::COleMessageFilter
- AFXOLE/COleMessageFilter::BeginBusyState
- AFXOLE/COleMessageFilter::EnableBusyDialog
- AFXOLE/COleMessageFilter::EnableNotRespondingDialog
- AFXOLE/COleMessageFilter::EndBusyState
- AFXOLE/COleMessageFilter::OnMessagePending
- AFXOLE/COleMessageFilter::Register
- AFXOLE/COleMessageFilter::Revoke
- AFXOLE/COleMessageFilter::SetBusyReply
- AFXOLE/COleMessageFilter::SetMessagePendingDelay
- AFXOLE/COleMessageFilter::SetRetryReply
helpviewer_keywords:
- COleMessageFilter [MFC], COleMessageFilter
- COleMessageFilter [MFC], BeginBusyState
- COleMessageFilter [MFC], EnableBusyDialog
- COleMessageFilter [MFC], EnableNotRespondingDialog
- COleMessageFilter [MFC], EndBusyState
- COleMessageFilter [MFC], OnMessagePending
- COleMessageFilter [MFC], Register
- COleMessageFilter [MFC], Revoke
- COleMessageFilter [MFC], SetBusyReply
- COleMessageFilter [MFC], SetMessagePendingDelay
- COleMessageFilter [MFC], SetRetryReply
ms.assetid: b1fd1639-fac4-4fd0-bf17-15172deba13c
ms.openlocfilehash: f6db5f012aedf08edd87980e304e181295bfb953
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374913"
---
# <a name="colemessagefilter-class"></a>COleMessageFilter 类

管理 OLE 应用程序交互所需的并发。

## <a name="syntax"></a>语法

```
class COleMessageFilter : public CCmdTarget
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[COle消息过滤器：COle消息过滤器](#colemessagefilter)|构造 `COleMessageFilter` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[COle消息过滤器：：开始忙州](#beginbusystate)|将应用程序置于忙状态。|
|[COle 消息筛选器：：启用忙对话](#enablebusydialog)|启用并禁用被调用应用程序忙时出现的对话框。|
|[COle 消息筛选器：：启用不响应对话框](#enablenotrespondingdialog)|启用并禁用被调用应用程序未响应时出现的对话框。|
|[COle消息过滤器：结束忙州](#endbusystate)|终止应用程序的忙状态。|
|[COle消息过滤器：打开消息挂起](#onmessagepending)|框架调用以在 OLE 调用进行时处理消息。|
|[COle消息过滤器：：注册](#register)|将消息筛选器注册到 OLE 系统 DLL。|
|[COle 消息筛选器：撤销](#revoke)|撤消消息筛选器在 OLE 系统 DLL 中的注册。|
|[COle消息过滤器：：设置忙回复](#setbusyreply)|确定繁忙的应用程序对 OLE 呼叫的回复。|
|[COle消息筛选器：：设置消息挂起延迟](#setmessagependingdelay)|确定应用程序等待响应 OLE 调用的时间。|
|[COle 消息筛选器：：设置重试回复](#setretryreply)|确定调用应用程序对繁忙应用程序的回复。|

## <a name="remarks"></a>备注

该`COleMessageFilter`类在可视化编辑服务器和容器应用程序以及 OLE 自动化应用程序中非常有用。 对于正在调用的服务器应用程序，此类可用于使应用程序"繁忙"，以便取消或稍后重试来自其他容器应用程序的传入调用。 此类还可用于确定调用应用程序在调用应用程序繁忙时要执行的操作。

常见用法是服务器应用程序调用[BeginBusyState](#beginbusystate)和[endBusyState，](#endbusystate)当文档或其他 OLE 可访问对象被销毁时，将是危险的。 这些调用在[CWinApp 中进行：在用户界面更新期间处于空闲状态](../../mfc/reference/cwinapp-class.md#onidle)。

默认情况下，在初始`COleMessageFilter`化应用程序时分配对象。 它可以通过[AfxOleGet消息过滤器](application-control.md#afxolegetmessagefilter)检索。

这是一个高级类;你很少需要直接使用它。

有关详细信息，请参阅文章["服务器：实现服务器](../../mfc/servers-implementing-a-server.md)"。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleMessageFilter`

## <a name="requirements"></a>要求

**标题：** afxole.h

## <a name="colemessagefilterbeginbusystate"></a><a name="beginbusystate"></a>COle消息过滤器：：开始忙州

调用此函数以开始忙状态。

```
virtual void BeginBusyState();
```

### <a name="remarks"></a>备注

它与[EndBusyState](#endbusystate)协同工作，以控制应用程序的忙状态。 函数[SetBusyReply](#setbusyreply)确定应用程序在忙时对调用应用程序的回复。

和`BeginBusyState``EndBusyState`调用增量和递减，分别一个计数器，用于确定应用程序是否繁忙。 例如，对的`BeginBusyState`两个调用和一个`EndBusyState`调用仍然会导致忙状态。 要取消忙状态，必须调用`EndBusyState`相同次数`BeginBusyState`的调用。

默认情况下，框架在空闲处理期间进入忙状态，由[CWinApp 执行：：onIdle](../../mfc/reference/cwinapp-class.md#onidle)。 当应用程序正在处理ON_COMMANDUPDATEUI通知时，传入呼叫将在空闲处理完成后稍后处理。

## <a name="colemessagefiltercolemessagefilter"></a><a name="colemessagefilter"></a>COle消息过滤器：COle消息过滤器

创建一个 `COleMessageFilter` 对象。

```
COleMessageFilter();
```

## <a name="colemessagefilterenablebusydialog"></a><a name="enablebusydialog"></a>COle 消息筛选器：：启用忙对话

启用并禁用忙对话框，该对话框在消息挂起的延迟过期时显示（请参阅 OLE 调用期间的[SetRetryReply）。](#setretryreply)

```
void EnableBusyDialog(BOOL bEnableBusy = TRUE);
```

### <a name="parameters"></a>参数

*bEnableBusy*<br/>
指定"忙"对话框是启用还是禁用。

## <a name="colemessagefilterenablenotrespondingdialog"></a><a name="enablenotrespondingdialog"></a>COle 消息筛选器：：启用不响应对话框

启用并禁用"未响应"对话框，如果 OLE 呼叫期间键盘或鼠标消息挂起且呼叫超时，则会显示该对话框。

```
void EnableNotRespondingDialog(BOOL bEnableNotResponding = TRUE);
```

### <a name="parameters"></a>参数

*b 启用不响应*<br/>
指定"未响应"对话框是启用还是禁用。

## <a name="colemessagefilterendbusystate"></a><a name="endbusystate"></a>COle消息过滤器：结束忙州

调用此函数以结束忙状态。

```
virtual void EndBusyState();
```

### <a name="remarks"></a>备注

它与[BeginBusyState](#beginbusystate)协同工作，以控制应用程序的忙状态。 函数[SetBusyReply](#setbusyreply)确定应用程序在忙时对调用应用程序的回复。

和`BeginBusyState``EndBusyState`调用增量和递减，分别一个计数器，用于确定应用程序是否繁忙。 例如，对的`BeginBusyState`两个调用和一个`EndBusyState`调用仍然会导致忙状态。 要取消忙状态，必须调用`EndBusyState`相同次数`BeginBusyState`的调用。

默认情况下，框架在空闲处理期间进入忙状态，由[CWinApp 执行：：onIdle](../../mfc/reference/cwinapp-class.md#onidle)。 当应用程序正在处理ON_UPDATE_COMMAND_UI通知时，传入呼叫将在空闲处理完成后处理。

## <a name="colemessagefilteronmessagepending"></a><a name="onmessagepending"></a>COle消息过滤器：打开消息挂起

框架调用以在 OLE 调用进行时处理消息。

```
virtual BOOL OnMessagePending(const MSG* pMsg);
```

### <a name="parameters"></a>参数

*pMsg*<br/>
指向挂起消息的指针。

### <a name="return-value"></a>返回值

若成功，则为非零；否则为 0。

### <a name="remarks"></a>备注

当调用应用程序等待调用完成时，框架使用指向挂起消息的指针调用`OnMessagePending`。 默认情况下，框架调度WM_PAINT消息，以便在需要很长时间的调用期间进行窗口更新。

您必须通过调用注册来注册邮件筛选器，然后才能激活该[筛选器](#register)。

## <a name="colemessagefilterregister"></a><a name="register"></a>COle消息过滤器：：注册

将消息筛选器注册到 OLE 系统 DLL。

```
BOOL Register();
```

### <a name="return-value"></a>返回值

若成功，则为非零；否则为 0。

### <a name="remarks"></a>备注

除非消息筛选器已注册到系统 DLL，否则该筛选器无效。 通常，应用程序的初始化代码注册应用程序的消息筛选器。 应用程序注册的任何其他消息筛选器都应在程序终止之前通过调用[Revoke](#revoke)终止。

框架的默认消息筛选器在初始化期间自动注册，并在终止时撤消。

## <a name="colemessagefilterrevoke"></a><a name="revoke"></a>COle 消息筛选器：撤销

撤销以前由呼叫[注册执行的注册](#register)。

```
void Revoke();
```

### <a name="remarks"></a>备注

应在程序终止之前吊销消息筛选器。

由框架自动创建和注册的默认消息筛选器也会自动吊销。

## <a name="colemessagefiltersetbusyreply"></a><a name="setbusyreply"></a>COle消息过滤器：：设置忙回复

此函数设置应用程序的"忙答复"。

```
void SetBusyReply(SERVERCALL nBusyReply);
```

### <a name="parameters"></a>参数

*nBusy回复*<br/>
枚举中`SERVERCALL`的值，在 COMPOBJ 中定义。H。 它可以具有以下任一值：

- SERVERCALL_ISHANDLED 应用程序可以接受呼叫，但在处理特定呼叫时可能失败。

- SERVERCALL_REJECTED 应用程序可能永远无法处理呼叫。

- SERVERCALL_RETRYLATER 应用程序暂时处于无法处理呼叫的状态。

### <a name="remarks"></a>备注

[BeginBusyState](#beginbusystate)和[EndBusyState](#endbusystate)函数控制应用程序的忙状态。

当应用程序忙于调用`BeginBusyState`时，它将响应来自 OLE 系统 DLL 的调用，其值由 最后一`SetBusyReply`个设置确定。 调用应用程序使用此繁忙的答复来确定要执行的操作。

默认情况下，繁忙的回复是SERVERCALL_RETRYLATER。 此答复导致调用应用程序尽快重试呼叫。

## <a name="colemessagefiltersetmessagependingdelay"></a><a name="setmessagependingdelay"></a>COle消息筛选器：：设置消息挂起延迟

确定调用应用程序等待来自被调用应用程序的响应的时间，然后再执行进一步操作。

```
void SetMessagePendingDelay(DWORD nTimeout = 5000);
```

### <a name="parameters"></a>参数

*n超时*<br/>
消息挂起延迟的毫秒数。

### <a name="remarks"></a>备注

此函数与[SetRetryReply 协同](#setretryreply)工作。

## <a name="colemessagefiltersetretryreply"></a><a name="setretryreply"></a>COle 消息筛选器：：设置重试回复

确定调用应用程序在收到来自被调用应用程序的繁忙响应时的操作。

```
void SetRetryReply(DWORD nRetryReply = 0);
```

### <a name="parameters"></a>参数

*nRetry回复*<br/>
重试之间的毫秒数。

### <a name="remarks"></a>备注

当被调用的应用程序指示它处于繁忙状态时，调用应用程序可能会决定等待服务器不再繁忙、立即重试或在指定间隔后重试。 它还可能决定完全取消呼叫。

调用方的响应由函数`SetRetryReply`和[SetMessagePendingDelay](#setmessagependingdelay)控制。 `SetRetryReply`确定调用应用程序应在重试给定调用之间等待多长时间。 `SetMessagePendingDelay`确定调用应用程序等待来自服务器的响应的时间，然后再执行进一步操作。

通常默认值是可以接受的，不需要更改。 框架每隔*nretry 回复*毫秒重试呼叫，直到呼叫通过或消息挂起延迟已过期。 *nRetryReply*的值为 0 指定立即重试，- 1 指定取消呼叫。

当消息挂起延迟过期时，将显示 OLE"忙对话框"（请参阅[COleBusyDialog），](../../mfc/reference/colebusydialog-class.md)以便用户可以选择取消或重试呼叫。 调用[启用忙忙对话框](#enablebusydialog)以启用或禁用此对话框。

当键盘或鼠标消息在呼叫期间挂起且呼叫超时（超过消息挂起延迟）时，将显示"未响应"对话框。 调用[启用不响应对话框](#enablenotrespondingdialog)以启用或禁用此对话框。 通常，这种情况表明出现问题，用户越来越不耐烦。

禁用对话框后，当前"重试答复"始终用于调用繁忙的应用程序。

## <a name="see-also"></a>另请参阅

[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)<br/>
[层次结构图表](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)
