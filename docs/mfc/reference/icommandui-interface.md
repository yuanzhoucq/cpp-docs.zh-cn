---
title: "ICommandUI Interface | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ICommandUI"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ICommandUI interface"
ms.assetid: 134afe8d-dcdf-47ca-857a-a166a6b665dd
caps.latest.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# ICommandUI Interface
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

管理用户界面命令。  
  
## 语法  
  
```  
interface class ICommandUI  
```  
  
## 成员  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[ICommandUI::Check](../Topic/ICommandUI::Check.md)|将此命令的用户界面项到相应的复选状态。|  
|[ICommandUI::ContinueRouting](../Topic/ICommandUI::ContinueRouting.md)|调用命令传送结构继续路由在处理程序中链的当前消息。|  
|[ICommandUI::Enabled](../Topic/ICommandUI::Enabled.md)|启用或禁用此命令的用户界面项。|  
|[ICommandUI::ID](../Topic/ICommandUI::ID.md)|获取 `ICommandUI` 对象表示的用户界面对象的ID。|  
|[ICommandUI::Index](../Topic/ICommandUI::Index.md)|获取 `ICommandUI` 对象表示的用户界面对象的索引。|  
|[ICommandUI::Radio](../Topic/ICommandUI::Radio.md)|将此命令的用户界面项到相应的复选状态。|  
|[ICommandUI::Text](../Topic/ICommandUI::Text.md)|设置用户界面项的文本此命令的。|  
  
## 备注  
 此接口提供管理用户界面命令的方法和属性。  `ICommandUI` 类似于 [CCmdUI Class](../../mfc/reference/ccmdui-class.md)，除此之外，`ICommandUI` 配合.NET组件交互操作的MFC应用程序。  
  
 `ICommandUI` 在 `ON_UPDATE_COMMAND_UI` 处理程序在 [ICommandTarget](../../mfc/reference/icommandtarget-interface.md)派生类中使用。  当应用程序的用户活动\(选择或单击时\)菜单，每个菜单项显示为启用或禁用。  每个菜单命令的目标通过实现 `ON_UPDATE_COMMAND_UI` 处理程序提供此信息。  对于每个在应用程序的命令用户界面对象，请使用"属性"窗口创建每个处理程序的消息映射项和函数原型。  
  
 有关 `ICommandUI` 接口方式的更多信息用于命令传送，请参见 [如何：向 Windows 窗体控件添加命令传送](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)。  
  
 有关使用Windows窗体的更多信息，请参见 [在 MFC 中使用 Windows 窗体用户控件](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
 有关用户界面命令方式的更多信息在MFC管理，请参见 [CCmdUI Class](../../mfc/reference/ccmdui-class.md)。  
  
## 要求  
 **标头:** afxwinforms.h \(定义程序集中atlmfc \\ lib \\ mfcmifc80.dll\)  
  
## 请参阅  
 [CCmdUI Class](../../mfc/reference/ccmdui-class.md)