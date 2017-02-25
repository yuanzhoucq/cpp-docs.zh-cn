---
title: "ICommandSource Interface | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ICommandSource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ICommandSource interface"
ms.assetid: a4b1f698-c09f-4ba8-9b13-0e74a0a4967e
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# ICommandSource Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

管理从命令源对象发送的命令到用户控件。  
  
## 语法  
  
```  
interface class ICommandSource  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[ICommandSource::AddCommandHandler](../Topic/ICommandSource::AddCommandHandler.md)|添加一个命令处理程序添加到命令源对象。|  
|[ICommandSource::AddCommandRangeHandler](../Topic/ICommandSource::AddCommandRangeHandler.md)|添加命令处理程序的一组添加到命令源对象。|  
|[ICommandSource::AddCommandRangeUIHandler](../Topic/ICommandSource::AddCommandRangeUIHandler.md)|添加用户界面命令消息处理程序中的一组添加到命令源对象。|  
|[ICommandSource::AddCommandUIHandler](../Topic/ICommandSource::AddCommandUIHandler.md)|添加一个用户界面命令消息处理程序添加到命令源对象。|  
|[ICommandSource::PostCommand](../Topic/ICommandSource::PostCommand.md)|将消息发送，而不等待其处理。|  
|[ICommandSource::RemoveCommandHandler](../Topic/ICommandSource::RemoveCommandHandler.md)|从命令源对象的命令处理程序。|  
|[ICommandSource::RemoveCommandRangeHandler](../Topic/ICommandSource::RemoveCommandRangeHandler.md)|从命令源对象的命令处理程序的一组。|  
|[ICommandSource::RemoveCommandRangeUIHandler](../Topic/ICommandSource::RemoveCommandRangeUIHandler.md)|从命令源对象中移除用户界面命令消息处理程序中的一组。|  
|[ICommandSource::RemoveCommandUIHandler](../Topic/ICommandSource::RemoveCommandUIHandler.md)|从命令源对象中移除用户界面命令消息处理程序。|  
|[ICommandSource::SendCommand](../Topic/ICommandSource::SendCommand.md)|发送消息并等待其在返回之前处理。|  
  
## 备注  
 在承载在MFC视图时的用户控件，[CWinFormsView Class](../../mfc/reference/cwinformsview-class.md) 路由命令和更新命令UI消息传送到用户控件如何使其能够处理MFC命令\(例如，框架菜单项和工具栏按钮）。  通过实现 [ICommandTarget Interface](../../mfc/reference/icommandtarget-interface.md)，为用户控件引用 `ICommandSource` 对象。  
  
 有关如何使用 `ICommandTarget` 的示例，请参见 [如何：向 Windows 窗体控件添加命令传送](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)。  
  
 有关使用Windows窗体的更多信息，请参见 [在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
## 要求  
 **标头:** afxwinforms.h \(定义程序集中atlmfc \\ lib \\ mfcmifc80.dll\)  
  
## 请参阅  
 [如何：向 Windows 窗体控件添加命令传送](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)   
 [ICommandTarget Interface](../../mfc/reference/icommandtarget-interface.md)