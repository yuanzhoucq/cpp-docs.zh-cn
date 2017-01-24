---
title: "自动化客户端 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "自动化客户端"
  - "客户端"
  - "客户端, 自动化"
  - "类型库, 自动化客户端"
ms.assetid: 84e34a79-06f6-4752-a33b-ae0ede1d8ecf
caps.latest.revision: 14
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 自动化客户端
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

自动化使应用程序中操作应用程序中实施的对象，或者公开对象，所以它们可以进行操作。  自动化客户可操作属于另一个应用程序中的已公开对象的应用程序。  公开对象的应用程序称为自动化服务器。  客户端通过访问这些对象的属性和服务器应用函数操作的对象。  
  
### 自动化客户端的类型  
 自动客户端分为两种类型：  
  
-   客户端 \(在运行时\) 将动态获取有关服务器的属性和操作的信息。  
  
-   拥有静态信息的客户。\(提供在编译时\) 指定服务器的属性和操作。  
  
 第一个类型的客户通过 OLE 查询系统的 `IDispatch` 机制获取有关服务器的方法和属性的信息。  尽管其足以为动态客户端，使用 `IDispatch` 很难提供静态客户使用，必须在编译时知道驱动的对象。  对于静态绑定客户端，但是 Microsoft 基础类 \(MFC\) 提供类。[COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)  
  
 静态绑定客户端使用静态链接与客户端应用程序中的一个代理类。  此类提供的属性和服务器应用操作的类型安全 C\+\+ 来封装。  
  
 类 `COleDispatchDriver` 提供自动化客户端主要提供支持。  使用 `Add New Item` 对话框，可创建从 `COleDispatchDriver`派生的类。  
  
 您然后指定用于描述服务器应用对象的属性和函数的类型库文件。  "添加项"对话框读取此文件并创建 `COleDispatchDriver`派生类，使用成员函数在 C\+\+ 中调用应用程序可以访问服务器的应用对象一个以类型安全方法。  从 `COleDispatchDriver` 继承的其他功能简化调用适当的自动化服务器进程。  
  
### 自动化客户端的事件处理。  
 如果希望处理在自动化客户端的事件，则需要将接收接口。  MFC 提供向导的其他 COM 服务器不支持 ActiveX 控件添加的接收接口，但支持。  有关如何将客户了 MFC 的 COM 服务器接收接口的信息介绍的源的接口，请参见如何：创建基于 MFC 的 COM 客户 \(知识库 181845\) 的。[http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;181845](http://support.microsoft.com/default.aspx?scid=kb;en-us;181845)接收接口。  
  
## 请参阅  
 [自动化客户端：使用类型库](../mfc/automation-clients-using-type-libraries.md)   
 [自动化](../mfc/automation.md)   
 [MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)