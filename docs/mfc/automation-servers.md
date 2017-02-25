---
title: "自动化服务器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "自动化服务器"
  - "COM 组件, 自动化服务器"
  - "调度映射, 自动化服务器"
  - "服务器, 自动化"
ms.assetid: 523fd155-51ce-4f91-b986-b74bdbdd7d92
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 自动化服务器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

自动化使应用程序中操作应用程序中实施的对象，或者公开对象，所以它们可以进行操作。  自动化服务器。公开可编程对象的应用程序 \(称为自动化对象\) 与其他应用程序 \(称为\)。[自动化客户](../mfc/automation-clients.md) 自动化服务器有时调用自动化组件。  
  
 自动化公开对象使客户可以通过直接访问对象自动化某些过程，服务器提供的功能。  此对象公开方式是有利，则应用程序提供其他应用程序非常有用的功能。  例如，字处理器可能公开其拼写检查器功能，以使其他程序中使用它。  使用其他应用程序中选取的功能，该对象公开从而使提供商以改善其应用程序的功能。  
  
 这些自动化对象具有属性和方法作为它们的外部界面。  属性是自动化对象的命名属性。  属性就像 C\+\+ 友好类的数据成员。  方法对自动化对象的工作函数。  方法类似于 C.C\+\+ 类的公共成员函数。  
  
> [!NOTE]
>  虽然属性就像 C\+\+ 数据成员，它们不可直接访问。  若要提供透明的访问，请将在自动化对象的内部变量一个对的 get\/set 成员函数访问它们。  
  
 通过公开应用程序功能通过常用，显式定义的接口，自动化可以在单一泛型编程语言的应用程序 \(例如 Microsoft Visual Basic，而不是在其他应用程序特定的宏语言。  
  
##  <a name="_core_support_for_automation_servers"></a> 自动化服务器的支持  
 Visual C\+\+ 和 MFC 框架为自动化服务器提供了广泛的支持。  他们在处理进行自动化服务器所涉及的许多系统开销，因此，您可以集中精力于应用程序的功能。  
  
 支持的自动化框架的主要机制是计划映射扩展到，声明和调用需要公开方法和属性 OLE 的组宏。  典型的计划映射如下所示：  
  
 [!code-cpp[NVC_MFCAutomation#1](../mfc/codesnippet/CPP/automation-servers_1.cpp)]  
  
 在维护的计划映射的属性"窗口和"类视图帮助。  在添加新的方法或属性。类时，Visual C\+\+ 将相应的 `DISP_FUNCTION` 或 `DISP_PROPERTY` 宏与表示方法的类名和命名的外部、内部或属性参数和数据类型。  
  
 **添加类** 对话框还简化自动化类的声明及其属性和操作的管理。  当您使用将类对话框向项目添加类时，应指定其基类。  如果允许自动化基类，则可以使用指定类中添加对话框显示控制新类是否应支持自动化，则“创建 OLE”\(类的对象即是否在从 COM 客户端的请求\) 和名称。可以创建外部 COM 客户端使用。  
  
 **添加类** 对话框然后创建类声明，包括指定的 OLE 功能的相应宏。  它还添加类的成员函数的实现的主干代码。  
  
 MFC 应用程序向导来简化在获取自动化服务器应用程序所涉及的步骤地面。  如果选择从 **高级功能** 页的复选框 **自动化 \(U\)**，MFC 应用程序向导将应用到程序的 `InitInstance` 函数的调用要求注册自动化对象并运行该应用程序用作自动化服务器。  
  
### 你希望做什么？  
  
-   [了解自动化客户](../mfc/automation-clients.md)  
  
-   [详细了解 CCmdTarget 类](../mfc/reference/ccmdtarget-class.md)  
  
-   [详细了解 COleDispatchDriver 类](../mfc/reference/coledispatchdriver-class.md)  
  
## 请参阅  
 [自动化](../mfc/automation.md)   
 [MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)