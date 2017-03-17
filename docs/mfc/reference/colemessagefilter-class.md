---
title: "COleMessageFilter 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
- COleMessageFilter class
- OLE [C++], managing concurrency
- message filters [C++]
- OLE applications [C++], managing interactions
- OLE messages
- applications [OLE], managing interactions
- messages [C++], OLE
ms.assetid: b1fd1639-fac4-4fd0-bf17-15172deba13c
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: d91ed300bb6cade5d804fe4a74dfe6cc2e4384fe
ms.lasthandoff: 02/24/2017

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
|[COleMessageFilter::BeginBusyState](#beginbusystate)|将应用程序放入忙碌状态。|  
|[COleMessageFilter::EnableBusyDialog](#enablebusydialog)|启用和禁用忙称为应用程序时，将出现对话框。|  
|[COleMessageFilter::EnableNotRespondingDialog](#enablenotrespondingdialog)|启用和禁用称为应用程序没有响应时，将显示对话框。|  
|[COleMessageFilter::EndBusyState](#endbusystate)|终止应用程序的繁忙状态。|  
|[COleMessageFilter::OnMessagePending](#onmessagepending)|框架来处理消息由 OLE 调用正在进行时调用。|  
|[COleMessageFilter::Register](#register)|使用 OLE 系统 Dll 注册消息筛选器。|  
|[COleMessageFilter::Revoke](#revoke)|撤消向 OLE 系统 Dll 的消息筛选器的注册。|  
|[COleMessageFilter::SetBusyReply](#setbusyreply)|确定 OLE 调用的繁忙的应用程序的回复。|  
|[COleMessageFilter::SetMessagePendingDelay](#setmessagependingdelay)|确定应用程序等待 OLE 调用的响应的时长。|  
|[COleMessageFilter::SetRetryReply](#setretryreply)|确定繁忙的应用程序的调用应用程序的回复。|  
  
## <a name="remarks"></a>备注  
 `COleMessageFilter`类是在可视化编辑服务器和容器应用程序，以及 OLE 自动化应用程序中很有用。 对于服务器应用程序正被调用，此类可用于使应用程序"忙"，以便从其他容器应用程序的传入呼叫取消连接，或者稍后重试。 此类还用于确定在调用应用程序正在使用时，调用应用程序要执行的操作。  
  
 常见用法是服务器应用程序调用[BeginBusyState](#beginbusystate)和[EndBusyState](#endbusystate)时它是很危险的文档或其他 OLE 辅助性对象，将其销毁。 在进行这些调用[CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle)用户界面更新期间。  
  
 默认情况下，`COleMessageFilter`初始化应用程序时分配给对象。 可以通过检索[AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter)。  
  
 这是一个高级的类;您很少需要直接使用它。  
  
 有关详细信息，请参阅文章[服务器︰ 实现服务器](../../mfc/servers-implementing-a-server.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleMessageFilter`  
  
## <a name="requirements"></a>要求  
 **标头︰** afxole.h  
  
##  <a name="beginbusystate"></a>COleMessageFilter::BeginBusyState  
 调用此函数可开始忙碌状态。  
  
```  
virtual void BeginBusyState();
```  
  
### <a name="remarks"></a>备注  
 它与配合[EndBusyState](#endbusystate)来控制应用程序的繁忙状态。 该函数[SetBusyReply](#setbusyreply)确定忙时调用应用程序的应用程序的回复。  
  
 `BeginBusyState`和`EndBusyState`调用进行递增和递减分别确定应用程序是否为忙的计数器。 例如，两次调用`BeginBusyState`和一个调用`EndBusyState`仍会导致忙碌状态。 若要取消繁忙状态不必调用时会`EndBusyState`同样次数`BeginBusyState`已调用。  
  
 默认情况下，该框架忙碌状态在过程中进入由执行的空闲处理[CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle)。 尽管应用程序处理**ON_COMMANDUPDATEUI**空闲处理完成后，将更高版本，处理通知，传入呼叫。  
  
##  <a name="colemessagefilter"></a>COleMessageFilter::COleMessageFilter  
 创建一个 `COleMessageFilter` 对象。  
  
```  
COleMessageFilter();
```  
  
##  <a name="enablebusydialog"></a>COleMessageFilter::EnableBusyDialog  
 启用和禁用忙对话框中，当消息挂起延迟过期时显示该 (请参阅[SetRetryReply](#setretryreply)) OLE 呼叫期间。  
  
```  
void EnableBusyDialog(BOOL bEnableBusy = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *bEnableBusy*  
 指定是否启用或禁用"忙"对话框。  
  
##  <a name="enablenotrespondingdialog"></a>COleMessageFilter::EnableNotRespondingDialog  
 启用和禁用"未响应"对话框中，如果键盘或鼠标消息被挂起，则显示在 OLE 过程调用，并调用已超时。  
  
```  
void EnableNotRespondingDialog(BOOL bEnableNotResponding = TRUE);
```  
  
### <a name="parameters"></a>参数  
 *bEnableNotResponding*  
 指定是否启用或禁用"未响应"对话框。  
  
##  <a name="endbusystate"></a>COleMessageFilter::EndBusyState  
 调用此函数来结束忙碌状态。  
  
```  
virtual void EndBusyState();
```  
  
### <a name="remarks"></a>备注  
 它与配合[BeginBusyState](#beginbusystate)来控制应用程序的繁忙状态。 该函数[SetBusyReply](#setbusyreply)确定忙时调用应用程序的应用程序的回复。  
  
 `BeginBusyState`和`EndBusyState`调用进行递增和递减分别确定应用程序是否为忙的计数器。 例如，两次调用`BeginBusyState`和一个调用`EndBusyState`仍会导致忙碌状态。 若要取消繁忙状态不必调用时会`EndBusyState`同样次数`BeginBusyState`已调用。  
  
 默认情况下，该框架忙碌状态在过程中进入由执行的空闲处理[CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle)。 尽管应用程序处理`ON_UPDATE_COMMAND_UI`空闲处理完成后通知，传入呼叫进行处理。  
  
##  <a name="onmessagepending"></a>COleMessageFilter::OnMessagePending  
 框架来处理消息由 OLE 调用正在进行时调用。  
  
```  
virtual BOOL OnMessagePending(const MSG* pMsg);
```  
  
### <a name="parameters"></a>参数  
 `pMsg`  
 一个指针，指向挂起消息。  
  
### <a name="return-value"></a>返回值  
 若成功，则为非零；否则为 0。  
  
### <a name="remarks"></a>备注  
 当调用应用程序正在等待完成的调用时，框架将调用`OnMessagePending`用一个指针指向挂起消息。 默认情况下，框架将调度`WM_PAINT`消息，以便窗口都会更新可能会发生需要很长时间的调用。  
  
 您必须通过调用注册消息筛选器[注册](#register)它就会被激活之前。  
  
##  <a name="register"></a>COleMessageFilter::Register  
 使用 OLE 系统 Dll 注册消息筛选器。  
  
```  
BOOL Register();
```  
  
### <a name="return-value"></a>返回值  
 若成功，则为非零；否则为 0。  
  
### <a name="remarks"></a>备注  
 除非它系统中注册的 Dll，则一个消息筛选器无效。 通常，应用程序的初始化代码注册应用程序的消息筛选器。 通过调用终止程序之前，应撤消注册您的应用程序的任何其他消息的筛选器[撤消](#revoke)。  
  
 自动在初始化期间注册和撤消在终止框架的默认消息筛选器。  
  
##  <a name="revoke"></a>COleMessageFilter::Revoke  
 撤消上一个注册通过调用执行[注册](#register)。  
  
```  
void Revoke();
```  
  
### <a name="remarks"></a>备注  
 程序终止之前，应撤消一个消息筛选器。  
  
 默认消息筛选器，这是创建并由框架自动注册，也会自动吊销。  
  
##  <a name="setbusyreply"></a>COleMessageFilter::SetBusyReply  
 此函数将设置应用程序的"忙答复。"  
  
```  
void SetBusyReply(SERVERCALL nBusyReply);
```  
  
### <a name="parameters"></a>参数  
 *nBusyReply*  
 取值范围为`SERVERCALL`COMPOBJ 中定义的枚举。H。 它可以具有下列值之一︰  
  
- **SERVERCALL_ISHANDLED**应用程序可以接受的调用，但在处理特定的调用可能会失败。  
  
- **SERVERCALL_REJECTED**应用程序可能永远不会将能够处理呼叫。  
  
- **SERVERCALL_RETRYLATER**应用程序处于临时状态中它不能处理呼叫。  
  
### <a name="remarks"></a>备注  
 [BeginBusyState](#beginbusystate)和[EndBusyState](#endbusystate)函数控制应用程序的繁忙状态。  
  
 当应用程序进行了调用正忙于`BeginBusyState`，它调用 OLE 系统 Dll 从使用响应的最后一个设置确定的值`SetBusyReply`。 调用应用程序使用该繁忙的回复消息来确定要采取的操作。  
  
 默认情况下，是繁忙答复**SERVERCALL_RETRYLATER**。 该回复消息会导致调用应用程序能够尽可能快地重试调用。  
  
##  <a name="setmessagependingdelay"></a>COleMessageFilter::SetMessagePendingDelay  
 确定调用应用程序等待来自调用应用程序，然后执行进一步的操作的响应的时长。  
  
```  
void SetMessagePendingDelay(DWORD nTimeout = 5000);
```  
  
### <a name="parameters"></a>参数  
 `nTimeout`  
 挂起的消息的延迟的毫秒数。  
  
### <a name="remarks"></a>备注  
 此函数与协同工作[SetRetryReply](#setretryreply)。  
  
##  <a name="setretryreply"></a>COleMessageFilter::SetRetryReply  
 在从被调用的应用程序接收的繁忙响应时，请确定调用应用程序的操作。  
  
```  
void SetRetryReply(DWORD nRetryReply = 0);
```  
  
### <a name="parameters"></a>参数  
 `nRetryReply`  
 重试之间等待的毫秒数。  
  
### <a name="remarks"></a>备注  
 当被调用的应用程序将指示正忙时，可能会决定调用应用程序等待，直到服务器不再处于繁忙状态，以立即放弃重试，或在指定时间间隔后重试。 它还可能决定完全取消调用。  
  
 功能控制调用方的响应`SetRetryReply`和[SetMessagePendingDelay](#setmessagependingdelay)。 `SetRetryReply`确定调用应用程序的给定调用的重试之间应等待多长时间。 `SetMessagePendingDelay`确定多长时间调用应用程序等待来自服务器的响应之前采取进一步操作。  
  
 通常是可接受和不需要更改的默认值。 框架将重试该调用每个`nRetryReply`直到调用经历或已过期的挂起的消息的延迟 （毫秒)。 值为 0，`nRetryReply`指定对于立即重试，和 – 1，则指定在调用的取消。  
  
 消息挂起延迟已过期时，OLE"忙对话框中"(请参阅[COleBusyDialog](../../mfc/reference/colebusydialog-class.md)) 显示，以便用户可以选择取消或重试调用。 调用[EnableBusyDialog](#enablebusydialog)启用或禁用此对话框。  
  
 当键盘或鼠标消息处于挂起状态调用和调用过程已超时 （超出消息挂起延迟），将显示"未响应"对话框。 调用[EnableNotRespondingDialog](#enablenotrespondingdialog)启用或禁用此对话框。 通常此事务状态的指示出现了问题，并且，用户有了耐心。  
  
 当该对话框将被禁用时，当前"重试答复"始终用于对繁忙的应用程序的调用。  
  
## <a name="see-also"></a>另请参阅  
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CCmdTarget 类](../../mfc/reference/ccmdtarget-class.md)

