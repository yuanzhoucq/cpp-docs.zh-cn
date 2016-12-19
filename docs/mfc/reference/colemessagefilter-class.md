---
title: "COleMessageFilter Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "COleMessageFilter"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "应用程序 [OLE], managing interactions"
  - "COleMessageFilter class"
  - "message filters [C++]"
  - "消息 [C++], OLE"
  - "OLE [C++], managing concurrency"
  - "OLE 应用程序 [C++], managing interactions"
  - "OLE messages"
ms.assetid: b1fd1639-fac4-4fd0-bf17-15172deba13c
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COleMessageFilter Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

管理OLE应用程序的交互所需的并发。  
  
## 语法  
  
```  
class COleMessageFilter : public CCmdTarget  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[COleMessageFilter::COleMessageFilter](../Topic/COleMessageFilter::COleMessageFilter.md)|构造 `COleMessageFilter` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[COleMessageFilter::BeginBusyState](../Topic/COleMessageFilter::BeginBusyState.md)|在该忙状态使应用程序。|  
|[COleMessageFilter::EnableBusyDialog](../Topic/COleMessageFilter::EnableBusyDialog.md)|启用和禁用显示的对话框当调用的应用程序正忙。|  
|[COleMessageFilter::EnableNotRespondingDialog](../Topic/COleMessageFilter::EnableNotRespondingDialog.md)|启用和禁用显示的对话框当调用的应用程序不响应。|  
|[COleMessageFilter::EndBusyState](../Topic/COleMessageFilter::EndBusyState.md)|停止应用程序的忙状态。|  
|[COleMessageFilter::OnMessagePending](../Topic/COleMessageFilter::OnMessagePending.md)|调用由框架处理消息，当OLE调用时正在进行。|  
|[COleMessageFilter::Register](../Topic/COleMessageFilter::Register.md)|注册了OLE系统的DLL消息筛选器。|  
|[COleMessageFilter::Revoke](../Topic/COleMessageFilter::Revoke.md)|取消与OLE系统DLL的消息筛选器的注册。|  
|[COleMessageFilter::SetBusyReply](../Topic/COleMessageFilter::SetBusyReply.md)|确定对OLE的忙应用程序的答复调用。|  
|[COleMessageFilter::SetMessagePendingDelay](../Topic/COleMessageFilter::SetMessagePendingDelay.md)|确定应用程序需要等待对OLE的响应调用。|  
|[COleMessageFilter::SetRetryReply](../Topic/COleMessageFilter::SetRetryReply.md)|确定向忙应用程序的调用应用程序的答案。|  
  
## 备注  
 `COleMessageFilter` 选件类可用于可视化编辑服务器和容器应用程序，以及OLE自动化应用程序。  调用服务器应用程序，此选件类可用于使应用程序“忙”，以便从其他容器应用程序传入的调用之后撤消或重做试。  当调用应用程序正忙时，此选件类还可用于确定调用的应用程序将采用的事件。  
  
 常见用法是为了服务器应用程序可以调用 [BeginBusyState](../Topic/COleMessageFilter::BeginBusyState.md) 和 [EndBusyState](../Topic/COleMessageFilter::EndBusyState.md)，当很危险。对于要销毁的文档或其他OLE可访问对象。  在用户界面更新过程中，这些在 [CWinApp::OnIdle](../Topic/CWinApp::OnIdle.md) 调用。  
  
 默认情况下，`COleMessageFilter` 对象，同时初始化应用程序时，分配。  它可以检索与 [AfxOleGetMessageFilter](../Topic/AfxOleGetMessageFilter.md)。  
  
 这是高级选件类;您几乎不需要直接与它的人员。  
  
 有关更多信息，请参见文章 [服务器:实现服务器](../../mfc/servers-implementing-a-server.md)。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleMessageFilter`  
  
## 要求  
 **Header:** afxole.h  
  
## 请参阅  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)