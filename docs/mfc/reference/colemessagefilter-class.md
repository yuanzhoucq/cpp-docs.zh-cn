---
title: COleMessageFilter 类 |Microsoft 文档
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
ms.openlocfilehash: f758a3cc82d4f6cfcc28f89ae206a82b899c0042
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2018
ms.locfileid: "37037604"
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
|[COleMessageFilter::BeginBusyState](#beginbusystate)|将忙碌状态放置在应用程序。|  
|[COleMessageFilter::EnableBusyDialog](#enablebusydialog)|启用和禁用忙称为应用程序时，将出现的对话框。|  
|[COleMessageFilter::EnableNotRespondingDialog](#enablenotrespondingdialog)|启用和禁用时调用的应用程序未响应，将显示的对话框。|  
|[COleMessageFilter::EndBusyState](#endbusystate)|终止应用程序的繁忙状态。|  
|[COleMessageFilter::OnMessagePending](#onmessagepending)|正在进行的 OLE 调用时，由处理这些消息框架调用。|  
|[COleMessageFilter::Register](#register)|使用 OLE 系统 Dll 注册消息筛选器。|  
|[COleMessageFilter::Revoke](#revoke)|撤消向 OLE 系统 Dll 的消息筛选器的注册。|  
|[COleMessageFilter::SetBusyReply](#setbusyreply)|确定繁忙的应用程序的答复的 OLE 调用。|  
|[COleMessageFilter::SetMessagePendingDelay](#setmessagependingdelay)|确定应用程序等待 OLE 调用的响应的时长。|  
|[COleMessageFilter::SetRetryReply](#setretryreply)|确定繁忙的应用程序的调用应用程序的回复。|  
  
## <a name="remarks"></a>备注  
 `COleMessageFilter`类非常有用可视化编辑服务器和容器应用程序，以及 OLE 自动化应用程序。 对于服务器应用程序正被调用，此类可以用于使应用程序"忙"，以便从其他容器应用程序的传入调用取消连接，或者稍后重试。 此类还可用来确定在调用应用程序正在使用时，调用应用程序要执行的操作。  
  
 常见用法是服务器应用程序可通过调用[BeginBusyState](#beginbusystate)和[EndBusyState](#endbusystate)时它是很危险的文档或其他 OLE 辅助性对象，将其销毁。 这些调用都在[CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle)用户界面更新期间。  
  
 默认情况下，`COleMessageFilter`在初始化应用程序时分配对象。 可以使用检索[AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter)。  
  
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
 它与结合工作[EndBusyState](#endbusystate)来控制应用程序的繁忙状态。 该函数[SetBusyReply](#setbusyreply)确定繁忙时调用应用程序的应用程序的回复。  
  
 `BeginBusyState`和`EndBusyState`调用进行递增和递减，分别，确定应用程序是否繁忙的计数器。 例如，有两个调用到`BeginBusyState`和一个调用`EndBusyState`仍会导致繁忙状态。 若要取消繁忙状态需要调用`EndBusyState`相同次数`BeginBusyState`已调用。  
  
 默认情况下，框架进入忙状态在空闲处理，通过执行期间[CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle)。 虽然应用程序正在处理 ON_COMMANDUPDATEUI 通知，传入调用处理更高版本，空闲处理完成后。  
  
##  <a name="colemessagefilter"></a>  COleMessageFilter::COleMessageFilter  
 创建一个 `COleMessageFilter` 对象。  
  
```  
COleMessageFilter();
```  
  
##  <a name="enablebusydialog"></a>  COleMessageFilter::EnableBusyDialog  
 启用和禁用繁忙的对话框中，当消息挂起延迟过期时显示 (请参阅[SetRetryReply](#setretryreply)) 期间的 OLE 调用。  
  
```  
void EnableBusyDialog(BOOL bEnableBusy = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *bEnableBusy*  
 指定是否启用或禁用"忙"对话框。  
  
##  <a name="enablenotrespondingdialog"></a>  COleMessageFilter::EnableNotRespondingDialog  
 启用和禁用"未响应"对话框中，如果键盘或鼠标消息处于挂起状态，则显示在 OLE 过程调用和调用已超时。  
  
```  
void EnableNotRespondingDialog(BOOL bEnableNotResponding = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *bEnableNotResponding*  
 指定是否启用或禁用"未响应"对话框。  
  
##  <a name="endbusystate"></a>  COleMessageFilter::EndBusyState  
 调用此函数可结束繁忙状态。  
  
```  
virtual void EndBusyState();
```  
  
### <a name="remarks"></a>备注  
 它与结合工作[BeginBusyState](#beginbusystate)来控制应用程序的繁忙状态。 该函数[SetBusyReply](#setbusyreply)确定繁忙时调用应用程序的应用程序的回复。  
  
 `BeginBusyState`和`EndBusyState`调用进行递增和递减，分别，确定应用程序是否繁忙的计数器。 例如，有两个调用到`BeginBusyState`和一个调用`EndBusyState`仍会导致繁忙状态。 若要取消繁忙状态需要调用`EndBusyState`相同次数`BeginBusyState`已调用。  
  
 默认情况下，框架进入忙状态在空闲处理，通过执行期间[CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle)。 虽然应用程序正在处理 ON_UPDATE_COMMAND_UI 通知，空闲处理完成后处理的传入调用。  
  
##  <a name="onmessagepending"></a>  COleMessageFilter::OnMessagePending  
 正在进行的 OLE 调用时，由处理这些消息框架调用。  
  
```  
virtual BOOL OnMessagePending(const MSG* pMsg);
```  
  
### <a name="parameters"></a>参数  
 *pMsg*  
 一个指针，指向挂起消息。  
  
### <a name="return-value"></a>返回值  
 若成功，则为非零；否则为 0。  
  
### <a name="remarks"></a>备注  
 调用应用程序正在等待完成的调用，框架将调用`OnMessagePending`用一个指针指向挂起消息。 默认情况下，框架会将调度 WM_PAINT 消息以便窗口更新可以花很长时间的调用期间发生。  
  
 你必须通过调用注册消息筛选器[注册](#register)它就会被激活之前。  
  
##  <a name="register"></a>  COleMessageFilter::Register  
 使用 OLE 系统 Dll 注册消息筛选器。  
  
```  
BOOL Register();
```  
  
### <a name="return-value"></a>返回值  
 若成功，则为非零；否则为 0。  
  
### <a name="remarks"></a>备注  
 消息筛选器无任何影响，除非它系统 Dll 中注册。 通常，应用程序的初始化代码注册应用程序的消息筛选器。 通过调用终止程序之前，应撤消注册你的应用程序的任何其他消息的筛选器[撤消](#revoke)。  
  
 自动在初始化期间注册和吊销在终止框架的默认消息筛选器。  
  
##  <a name="revoke"></a>  COleMessageFilter::Revoke  
 撤消上一个注册通过调用执行[注册](#register)。  
  
```  
void Revoke();
```  
  
### <a name="remarks"></a>备注  
 在程序终止之前，应撤消消息筛选器。  
  
 默认消息筛选器，创建由框架自动注册，并还会自动吊销。  
  
##  <a name="setbusyreply"></a>  COleMessageFilter::SetBusyReply  
 此函数将应用程序的"繁忙答复。"  
  
```  
void SetBusyReply(SERVERCALL nBusyReply);
```  
  
### <a name="parameters"></a>参数  
 *nBusyReply*  
 取值范围为`SERVERCALL`COMPOBJ 中定义的枚举。H。 它可以具有以下值之一：  
  
- **SERVERCALL_ISHANDLED**应用程序可以接受调用，但在处理特定的调用可能会失败。  
  
- **SERVERCALL_REJECTED**应用程序可能永远不会将能够处理呼叫。  
  
- **SERVERCALL_RETRYLATER**应用程序处于临时状态在它无法处理调用。  
  
### <a name="remarks"></a>备注  
 [BeginBusyState](#beginbusystate)和[EndBusyState](#endbusystate)函数控制应用程序的繁忙状态。  
  
 当应用程序已通过调用忙`BeginBusyState`，它响应调用来自 OLE 系统 Dll 与由的最后一个设置一个值`SetBusyReply`。 调用应用程序使用此忙答复来确定要执行的操作。  
  
 默认情况下，繁忙的答复是**SERVERCALL_RETRYLATER**。 此答复导致调用应用程序尽可能快地重试调用。  
  
##  <a name="setmessagependingdelay"></a>  COleMessageFilter::SetMessagePendingDelay  
 确定调用应用程序调用应用程序，然后执行其他操作的响应，等待多长时间。  
  
```  
void SetMessagePendingDelay(DWORD nTimeout = 5000);
```  
  
### <a name="parameters"></a>参数  
 *nTimeout*  
 消息挂起延迟的毫秒数。  
  
### <a name="remarks"></a>备注  
 此函数可配合[SetRetryReply](#setretryreply)。  
  
##  <a name="setretryreply"></a>  COleMessageFilter::SetRetryReply  
 在从调用应用程序接收忙响应时，请确定调用应用程序的操作。  
  
```  
void SetRetryReply(DWORD nRetryReply = 0);
```  
  
### <a name="parameters"></a>参数  
 *nRetryReply*  
 重试之间的毫秒数。  
  
### <a name="remarks"></a>备注  
 在调用应用程序指示忙，调用应用程序可能会决定要等待，直到服务器不再正忙，立即，重试，或在指定时间间隔后重试。 它还可能决定完全取消调用。  
  
 调用方的响应控制由函数`SetRetryReply`和[SetMessagePendingDelay](#setmessagependingdelay)。 `SetRetryReply` 确定调用应用程序的给定调用的重试之间应等待多长时间。 `SetMessagePendingDelay` 确定多长时间调用应用程序服务器的响应前等待采取进一步操作。  
  
 通常是可接受和不需要更改的默认值。 框架就会重试调用每个*nRetryReply*直到调用经历或已过期的挂起的消息的延迟的毫秒。 值为 0， *nRetryReply*指定立即重试，和-1，则指定的调用的取消。  
  
 消息挂起延迟已过期时，OLE"忙对话框中"(请参阅[COleBusyDialog](../../mfc/reference/colebusydialog-class.md)) 将显示，以便用户可以选择取消或重试调用。 调用[EnableBusyDialog](#enablebusydialog)启用或禁用此对话框。  
  
 键盘或鼠标消息时挂起期间调用并调用已超时 （超出消息挂起延迟），将显示"未响应"对话框。 调用[EnableNotRespondingDialog](#enablenotrespondingdialog)启用或禁用此对话框。 通常的事务此状态指示出现了问题，并且用户获取耐心。  
  
 禁用对话框后，当前"重试答复"始终用于对繁忙的应用程序的调用。  
  
## <a name="see-also"></a>请参阅  
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)
