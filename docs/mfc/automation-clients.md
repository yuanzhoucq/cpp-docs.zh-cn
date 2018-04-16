---
title: 自动化客户端 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- clients, Automation
- Automation clients
- type libraries, Automation clients
- clients
ms.assetid: 84e34a79-06f6-4752-a33b-ae0ede1d8ecf
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9cfb6aae5c947d1f36019e548c72b22a3304aa12
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="automation-clients"></a>自动化客户端
利用自动化，您的应用程序可以操作在其他应用程序中实现的对象，或者公开对象以便操作它们。 自动化客户端是应用程序可以操作属于另一个应用程序公开的对象。 对象公开的应用程序称为自动化服务器。 客户端操作通过访问这些对象的属性和函数的服务器应用程序的对象。  
  
### <a name="types-of-automation-clients"></a>类型的自动化客户端  
 有两种类型的自动化客户端：  
  
-   动态 （在运行时） 的客户端获取有关属性和操作的服务器的信息。  
  
-   拥有 （在编译时提供），指定的属性和操作的服务器的静态信息的客户端。  
  
 第一种客户端获取有关服务器的方法和属性的信息通过查询 OLE 系统`IDispatch`机制。 虽然已足够用于动态客户端，`IDispatch`很难使用对于静态客户端，其中被驱动必须在已知的对象编译时间。 对于静态绑定客户端，提供 Microsoft 基础类[COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)类。  
  
 静态绑定的客户端在客户端应用程序中使用静态链接的代理类。 此类提供服务器应用程序的属性和操作的类型安全 c + + 的封装。  
  
 类`COleDispatchDriver`提供自动化客户端的主体的支持。 使用`Add New Item`对话框中，你创建一个派生自的类`COleDispatchDriver`。  
  
 然后指定描述的属性和函数的服务器应用程序的对象的类型库文件。 添加项对话框中读取此文件，并创建`COleDispatchDriver`-派生类，与你的应用程序可以调用以类型安全的方式访问 c + + 中的服务器应用程序的对象的成员函数。 其他功能继承自`COleDispatchDriver`简化了调用正确的自动化服务器的过程。  
  
### <a name="handling-events-in-automation-clients"></a>自动化客户端中处理事件  
 如果你想要在你的自动化客户端中处理事件，你需要添加接收器接口。 MFC 提供了向导支持将加载的 ActiveX 控件的接收器接口，但不是支持对其他 COM 服务器。 有关如何将接收器接口添加源接口通过 COM 服务器所述的 MFC 客户端中的信息，请参阅如何： 在创建 MFC-Based COM 客户端 (KB 181845) 中的接收器接口[http://support.microsoft.com/default.aspxscid=kb;en-us;181845](http://support.microsoft.com/default.aspxscid=kb;en-us;181845)。  
  
## <a name="see-also"></a>请参阅  
 [自动化客户端： 使用类型库](../mfc/automation-clients-using-type-libraries.md)   
 [自动化](../mfc/automation.md)   
 [MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)

