---
title: COleMessageFilter 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a35f73405340b1ad66b004efcab49ac4c569c560
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852128"
---
# <a name="colemessagefilter-class"></a>COleMessageFilter 类
管理 OLE 应用程序交互所需的并发。  
  
## <a name="syntax"></a>语法  
  
```  
class COleMessageFilter : public CCmdTarget  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[COleMessageFilter::COleMessageFilter](#colemessagefilter)|构造 `COleMessageFilter` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[COleMessageFilter::BeginBusyState](#beginbusystate)|让应用程序处于忙碌状态。|  
|[COleMessageFilter::EnableBusyDialog](#enablebusydialog)|启用和禁用时被调用的应用程序正在使用中，将显示的对话框。|  
|[COleMessageFilter::EnableNotRespondingDialog](#enablenotrespondingdialog)|启用和禁用时被调用的应用程序没有响应，将显示的对话框。|  
|[COleMessageFilter::EndBusyState](#endbusystate)|终止应用程序的繁忙状态。|  
|[COleMessageFilter::OnMessagePending](#onmessagepending)|在进行 OLE 调用时由框架来处理消息调用。|  
|[COleMessageFilter::Register](#register)|使用 OLE 系统 Dll 注册消息筛选器。|  
|[COleMessageFilter::Revoke](#revoke)|撤消向 OLE 系统 Dll 的消息筛选器的注册。|  
|[COleMessageFilter::SetBusyReply](#setbusyreply)|确定 OLE 调用繁忙的应用程序的回复。|  
|[COleMessageFilter::SetMessagePendingDelay](#setmessagependingdelay)|确定应用程序等待 OLE 调用的响应的时间长度。|  
|[COleMessageFilter::SetRetryReply](#setretryreply)|确定繁忙的应用程序调用应用程序的回复。|  
  
## <a name="remarks"></a>备注  
 `COleMessageFilter`类是可视化编辑服务器和容器应用程序，以及 OLE 自动化应用程序中很有用。 对于服务器应用程序正被调用，此类可用于使应用程序"忙"，以便从其他容器应用程序的传入呼叫取消连接，或者稍后重试。 此类还用于确定要被调用应用程序正在使用中时，调用应用程序要执行的操作。  
  
 常见的用法是用于服务器应用程序以调用[BeginBusyState](#beginbusystate)并[EndBusyState](#endbusystate)时它十分危险要销毁其他 OLE 可访问对象或文档。 这些调用中所做[CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle)用户界面更新期间。  
  
 默认情况下，`COleMessageFilter`初始化应用程序时分配对象。 可通过检索[AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter)。  
  
 这是一个高级的类;很少需要直接使用它。  
  
 有关详细信息，请参阅文章[服务器： 实现服务器](../../mfc/servers-implementing-a-server.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleMessageFilter`  
  
## <a name="requirements"></a>要求  
 **标头：** afxole.h  
  
##  <a name="beginbusystate"></a>  COleMessageFilter::BeginBusyState  
 调用此函数可开始繁忙状态。  
  
```  
virtual void BeginBusyState();
```  
  
### <a name="remarks"></a>备注  
 它结合工作[EndBusyState](#endbusystate)来控制应用程序的繁忙状态。 该函数[SetBusyReply](#setbusyreply)确定到忙时调用应用程序的应用程序的答复。  
  
 `BeginBusyState`和`EndBusyState`调用进行递增和递减分别，确定应用程序是否为忙的计数器。 例如，两次调用`BeginBusyState`和一个调用`EndBusyState`仍保持繁忙状态。 若要取消繁忙状态，必须调用`EndBusyState`同样次数`BeginBusyState`已调用。  
  
 默认情况下，该框架忙碌状态期间进入空闲处理，通过执行[CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle)。 虽然应用程序处理 ON_COMMANDUPDATEUI 通知，传入调用处理更高版本，空闲处理完成后。  
  
##  <a name="colemessagefilter"></a>  COleMessageFilter::COleMessageFilter  
 创建一个 `COleMessageFilter` 对象。  
  
```  
COleMessageFilter();
```  
  
##  <a name="enablebusydialog"></a>  COleMessageFilter::EnableBusyDialog  
 启用和禁用繁忙对话框的消息挂起延迟到期时显示 (请参阅[SetRetryReply](#setretryreply)) OLE 调用期间。  
  
```  
void EnableBusyDialog(BOOL bEnableBusy = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *bEnableBusy*  
 指定是启用还是禁用"忙"对话框。  
  
##  <a name="enablenotrespondingdialog"></a>  COleMessageFilter::EnableNotRespondingDialog  
 启用和禁用"未响应"对话框中，如果键盘或鼠标消息被挂起，则显示在 OLE 过程调用和调用已超时。  
  
```  
void EnableNotRespondingDialog(BOOL bEnableNotResponding = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *bEnableNotResponding*  
 指定是启用还是禁用"未响应"对话框。  
  
##  <a name="endbusystate"></a>  COleMessageFilter::EndBusyState  
 调用此函数以结束繁忙状态。  
  
```  
virtual void EndBusyState();
```  
  
### <a name="remarks"></a>备注  
 它结合工作[BeginBusyState](#beginbusystate)来控制应用程序的繁忙状态。 该函数[SetBusyReply](#setbusyreply)确定到忙时调用应用程序的应用程序的答复。  
  
 `BeginBusyState`和`EndBusyState`调用进行递增和递减分别，确定应用程序是否为忙的计数器。 例如，两次调用`BeginBusyState`和一个调用`EndBusyState`仍保持繁忙状态。 若要取消繁忙状态，必须调用`EndBusyState`同样次数`BeginBusyState`已调用。  
  
 默认情况下，该框架忙碌状态期间进入空闲处理，通过执行[CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle)。 而应用程序处理 ON_UPDATE_COMMAND_UI 通知，空闲处理完成后进行处理的传入呼叫。  
  
##  <a name="onmessagepending"></a>  COleMessageFilter::OnMessagePending  
 在进行 OLE 调用时由框架来处理消息调用。  
  
```  
virtual BOOL OnMessagePending(const MSG* pMsg);
```  
  
### <a name="parameters"></a>参数  
 *pMsg*  
 指向挂起消息。  
  
### <a name="return-value"></a>返回值  
 若成功，则为非零；否则为 0。  
  
### <a name="remarks"></a>备注  
 调用应用程序正在等待完成的调用，框架将调用`OnMessagePending`用一个指针指向挂起消息。 默认情况下，框架将调度 WM_PAINT 消息，以便窗口更新可以在需要很长时间的调用期间发生。  
  
 必须通过调用注册消息筛选器[注册](#register)它就会被激活之前。  
  
##  <a name="register"></a>  COleMessageFilter::Register  
 使用 OLE 系统 Dll 注册消息筛选器。  
  
```  
BOOL Register();
```  
  
### <a name="return-value"></a>返回值  
 若成功，则为非零；否则为 0。  
  
### <a name="remarks"></a>备注  
 除非它系统中注册的 Dll，则消息筛选器无效。 通常，应用程序的初始化代码注册应用程序的消息筛选器。 通过调用程序在终止之前，应撤消注册你的应用程序的任何其他消息的筛选器[撤消](#revoke)。  
  
 自动在初始化期间注册和撤消在终止时框架的默认消息筛选器。  
  
##  <a name="revoke"></a>  COleMessageFilter::Revoke  
 撤消上一个注册执行通过调用[注册](#register)。  
  
```  
void Revoke();
```  
  
### <a name="remarks"></a>备注  
 程序终止之前，应撤消消息筛选器。  
  
 默认消息筛选器，它是创建并由框架自动注册，也会自动吊销。  
  
##  <a name="setbusyreply"></a>  COleMessageFilter::SetBusyReply  
 此函数将设置应用程序的"繁忙答复。"  
  
```  
void SetBusyReply(SERVERCALL nBusyReply);
```  
  
### <a name="parameters"></a>参数  
 *nBusyReply*  
 从值`SERVERCALL`COMPOBJ 中定义的枚举。H. 它可以具有以下值之一：  
  
- SERVERCALL_ISHANDLED 应用程序可以接受的调用，但在处理特定的调用可能会失败。  
  
- SERVERCALL_REJECTED 应用程序可能永远不会将能够处理呼叫。  
  
- SERVERCALL_RETRYLATER 应用程序已暂时在其中它无法处理调用的状态。  
  
### <a name="remarks"></a>备注  
 [BeginBusyState](#beginbusystate)并[EndBusyState](#endbusystate)函数控制应用程序的繁忙状态。  
  
 当应用程序变得繁忙通过调用`BeginBusyState`，它调用 OLE 系统 Dll 从使用响应的最后一个设置确定的值`SetBusyReply`。 调用应用程序使用此忙答复来确定要执行的操作。  
  
 默认情况下，繁忙的答复是 SERVERCALL_RETRYLATER。 该回复消息会导致调用应用程序能够尽可能快地重试调用。  
  
##  <a name="setmessagependingdelay"></a>  COleMessageFilter::SetMessagePendingDelay  
 确定调用应用程序等待来自之前执行其他操作在被调用应用程序的响应的时间长度。  
  
```  
void SetMessagePendingDelay(DWORD nTimeout = 5000);
```  
  
### <a name="parameters"></a>参数  
 *nTimeout*  
 挂起的消息的延迟的毫秒数。  
  
### <a name="remarks"></a>备注  
 此函数与协同工作[SetRetryReply](#setretryreply)。  
  
##  <a name="setretryreply"></a>  COleMessageFilter::SetRetryReply  
 从被调用的应用程序接收忙响应时，请确定调用应用程序的操作。  
  
```  
void SetRetryReply(DWORD nRetryReply = 0);
```  
  
### <a name="parameters"></a>参数  
 *nRetryReply*  
 重试之间的毫秒数。  
  
### <a name="remarks"></a>备注  
 当被调用的应用程序指示它正忙时，调用应用程序可以等待，直到服务器不再处于繁忙状态，重试，或在指定时间间隔后重试。 它还可能决定完全取消呼叫。  
  
 功能控制调用方的响应`SetRetryReply`并[SetMessagePendingDelay](#setmessagependingdelay)。 `SetRetryReply` 确定调用应用程序的给定调用的重试之间应等待多长时间。 `SetMessagePendingDelay` 确定多长时间调用应用程序等待来自服务器的响应然后再采取进一步操作。  
  
 通常可接受和不需要更改的默认值。 Framework 重试调用每个*nRetryReply*直到调用经历或已过期的消息挂起延迟的毫秒。 值为 0， *nRetryReply*指定立即重试，和-1，则指定调用的取消。  
  
 挂起的消息的延迟已过期时，OLE"忙对话框中"(请参阅[COleBusyDialog](../../mfc/reference/colebusydialog-class.md)) 将显示，以便用户可以选择取消或重试调用。 调用[EnableBusyDialog](#enablebusydialog)启用或禁用此对话框。  
  
 当键盘或鼠标消息处于挂起状态期间调用和调用已超时 （已超过挂起的消息的延迟），将显示"未响应"对话框。 调用[EnableNotRespondingDialog](#enablenotrespondingdialog)启用或禁用此对话框。 通常此状态的事件指示出现了问题，并且，用户有了耐心。  
  
 禁用对话框后，当前"重试答复"始终用于对繁忙的应用程序的调用。  
  
## <a name="see-also"></a>请参阅  
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图表](../../mfc/hierarchy-chart.md)   
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)
