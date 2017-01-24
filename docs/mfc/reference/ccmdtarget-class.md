---
title: "CCmdTarget Class | Microsoft Docs"
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
  - "CCmdTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCmdTarget class"
  - "命令传送, command targets"
  - "command targets"
  - "message maps, CCmdTarget base class"
  - "目标, 命令"
ms.assetid: 8883b132-2057-4ce0-a5f2-88979f8f2b13
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCmdTarget Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Microsoft基础类库选件消息映射体系结构的基类。  
  
## 语法  
  
```  
class CCmdTarget : public CObject  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CCmdTarget::CCmdTarget](../Topic/CCmdTarget::CCmdTarget.md)|构造 `CCmdTarget` 对象。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CCmdTarget::BeginWaitCursor](../Topic/CCmdTarget::BeginWaitCursor.md)|显示光标作为一个沙漏光标。|  
|[CCmdTarget::DoOleVerb](../Topic/CCmdTarget::DoOleVerb.md)|生成OLE谓词指定的事件将执行。|  
|[CCmdTarget::EnableAutomation](../Topic/CCmdTarget::EnableAutomation.md)|允许 `CCmdTarget` 对象的OLE自动化。|  
|[CCmdTarget::EnableConnections](../Topic/CCmdTarget::EnableConnections.md)|启用激发中的操作连接点。|  
|[CCmdTarget::EnableTypeLib](../Topic/CCmdTarget::EnableTypeLib.md)|启用目标类型库。|  
|[CCmdTarget::EndWaitCursor](../Topic/CCmdTarget::EndWaitCursor.md)|返回到以前的光标。|  
|[CCmdTarget::EnumOleVerbs](../Topic/CCmdTarget::EnumOleVerbs.md)|枚举对象的OLE谓词。|  
|[CCmdTarget::FromIDispatch](../Topic/CCmdTarget::FromIDispatch.md)|返回指向 `CCmdTarget` 对象与 `IDispatch` 指针。|  
|[CCmdTarget::GetDispatchIID](../Topic/CCmdTarget::GetDispatchIID.md)|获取主调度接口ID.|  
|[CCmdTarget::GetIDispatch](../Topic/CCmdTarget::GetIDispatch.md)|返回指向 `IDispatch` 对象与 `CCmdTarget` 对象。|  
|[CCmdTarget::GetTypeInfoCount](../Topic/CCmdTarget::GetTypeInfoCount.md)|检索对象提供类型信息接口的数字。|  
|[CCmdTarget::GetTypeInfoOfGuid](../Topic/CCmdTarget::GetTypeInfoOfGuid.md)|检索与指定的 GUID 相对应的类型说明。|  
|[CCmdTarget::GetTypeLib](../Topic/CCmdTarget::GetTypeLib.md)|具有指针类型库。|  
|[CCmdTarget::GetTypeLibCache](../Topic/CCmdTarget::GetTypeLibCache.md)|获取该类型库缓存。|  
|[CCmdTarget::IsInvokeAllowed](../Topic/CCmdTarget::IsInvokeAllowed.md)|启用自动化方法调用。|  
|[CCmdTarget::IsResultExpected](../Topic/CCmdTarget::IsResultExpected.md)|如果自动化功能应返回值，则返回非零。|  
|[CCmdTarget::OnCmdMsg](../Topic/CCmdTarget::OnCmdMsg.md)|方法与计划排列消息。|  
|[CCmdTarget::OnFinalRelease](../Topic/CCmdTarget::OnFinalRelease.md)|最后，在OLE引用被释放后，清理。|  
|[CCmdTarget::RestoreWaitCursor](../Topic/CCmdTarget::RestoreWaitCursor.md)|还原一个沙漏光标。|  
  
## 备注  
 消息映射路由命令或对该成员的消息您正常写入处理这些事件。  （命令是从菜单项、命令按钮或快捷键的消息。）  
  
 键从 `CCmdTarget` 派生的结构选件类包括 [CView](../../mfc/reference/cview-class.md)、 [CWinApp](../../mfc/reference/cwinapp-class.md)、 [CDocument](../../mfc/reference/cdocument-class.md)、 [CWnd](../../mfc/reference/cwnd-class.md)和 [CFrameWnd](../../mfc/reference/cframewnd-class.md)。  如果您在新选件类旨在处理消息，请从一种方式 `CCmdTarget`派生选件类的派生类。  您从 `CCmdTarget` 将直接很少派生选件类。  
  
 有关路由命令的目标和的 `OnCmdMsg` 概述，请参见 [命令目标](../../mfc/command-targets.md)、 [命令传送](../../mfc/command-routing.md)和 [将消息映射](../../mfc/mapping-messages.md)。  
  
 `CCmdTarget` 包括成员函数处理一个沙漏光标的显示。  当您需要一个命令带花费大量的时间间隔执行时，将显示一个沙漏光标。  
  
 计划映射，与消息映射，使用显示OLE自动化 `IDispatch` 功能。  通过公开此接口，其他应用程序\(例如Visual Basic\)可以对您的应用程序。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CCmdTarget`  
  
## 要求  
 **标头：**afxwin.h  
  
## 请参阅  
 [MFC示例ACDUAL](../../top/visual-cpp-samples.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)   
 [CCmdUI Class](../../mfc/reference/ccmdui-class.md)   
 [CDocument Class](../../mfc/reference/cdocument-class.md)   
 [CDocTemplate Class](../../mfc/reference/cdoctemplate-class.md)   
 [CWinApp Class](../../mfc/reference/cwinapp-class.md)   
 [CWnd 类](../../mfc/reference/cwnd-class.md)   
 [CView Class](../../mfc/reference/cview-class.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [COleDispatchDriver Class](../../mfc/reference/coledispatchdriver-class.md)