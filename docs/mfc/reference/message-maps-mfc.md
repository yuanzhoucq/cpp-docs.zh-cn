---
title: "消息映射 (MFC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.messages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "消息映射 [C++], MFC"
  - "消息 [C++], Windows"
  - "MFC [C++], 消息"
  - "Windows 消息 [C++], 消息映射"
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# 消息映射 (MFC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

这个部分的饮用列出了所有的[message mapping macros](../../mfc/reference/message-map-macros-mfc.md)和所有的[CWnd](../../mfc/reference/cwnd-class.md)消息，映射的实例与函数实例一致。  
  
|类别|说明|  
|--------|--------|  
|[WM\_COMMAND消息处理程序](../../mfc/reference/wm-command-message-handler.md)|控件**WM\_COMMAND**信息由用户菜单选项或用户菜单访问键生成。|  
|[子窗口通知消息处理程序](../../mfc/reference/child-window-notification-message-handlers.md)|处理来自子窗口的通知消息。|  
|[WM\_消息处理程序](../../mfc/reference/handlers-for-wm-messages.md)|处理**WM\_**消息，例如`WM_PAINT`。|  
|[由用户定义的消息处理程序](../../mfc/reference/user-defined-handlers.md)|处理用户定义的消息。|  
  
 （在引用中使用的术语和公约的例子请参见[How to Use the Message Map Cross\-Reference](../../mfc/reference/how-to-use-the-message-map-cross-reference.md)。）  
  
 因为 windows 是面向消息操作系统，Windows环境下编程的一大部分参与消息处理。  每次使用诸如击键或鼠标单击时，信息会发送到应用程序，然后必须处理事件。  
  
 Microsoft 基础类库提供基于消息编程的编程模型优化。  在此模型中，“消息映射”用于指定哪些函数用于为特定的类处理多种消息。  消息映射包含一个或多个宏用于指定哪些函数处理哪些消息。  例如，一个消息映射包括一个`ON_COMMAND`宏，会像这样：  
  
 [!code-cpp[NVC_MFCMessageMaps#16](../../mfc/reference/codesnippet/CPP/message-maps-mfc_1.cpp)]  
  
 `ON_COMMAND`宏用于处理由菜单、按钮、和加速键生成的命令消息。  [Macros](../../mfc/reference/message-map-macros-mfc.md)可用于映射如下的：  
  
## Windows消息  
  
-   控件通知  
  
-   用户定义的消息  
  
## 命令消息  
  
-   注册用户定义消息  
  
-   用户界面更新消息  
  
## 消息的范围  
  
-   命令  
  
-   更新处理程序消息  
  
-   控件通知  
  
 虽然消息映射宏很重要，但您通常不会直接使用它们。  这是因为当你使用消息关联消息处理函数时，属性窗口在源文件自动创建消息映射项。  任何时候你需要编辑或添加消息映射项，可以使用属性窗口。  
  
> [!NOTE]
>  属性窗口不支持消息映射排序。  必须自己编写这些消息映射项。  
  
 但是，消息映射是Microsoft 基础类库的重要组成部分。  您应了解他们做了什么，并且文档是为他们提供的。  
  
## 请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)