---
title: 自动化客户端
ms.date: 11/04/2016
helpviewer_keywords:
- clients, Automation
- Automation clients
- type libraries, Automation clients
- clients
ms.assetid: 84e34a79-06f6-4752-a33b-ae0ede1d8ecf
ms.openlocfilehash: 098c41ea981d9d0069130d5439632aa7b0d6cbbd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62254357"
---
# <a name="automation-clients"></a>自动化客户端

利用自动化，您的应用程序可以操作在其他应用程序中实现的对象，或者公开对象以便操作它们。 自动化客户端是可以操作公开的对象属于另一个应用程序的应用程序。 显示对象的应用程序称为自动化服务器。 客户端操作服务器应用程序的对象，通过访问这些对象的属性和函数。

### <a name="types-of-automation-clients"></a>类型的自动化客户端

有两种类型的自动化客户端：

- 客户端的动态 （在运行时） 获取有关的属性和操作的服务器的信息。

- 拥有 （提供在编译时），指定的属性和操作的服务器的静态信息的客户端。

第一种客户端获取有关服务器的方法和属性的信息通过查询 OLE 系统`IDispatch`机制。 尽管它足以用于动态客户端，`IDispatch`很难驱动必须在已知的对象的编译时为静态客户端使用。 有关静态绑定客户端，Microsoft 基础类提供[COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)类。

静态绑定的客户端与客户端应用程序使用静态链接的代理类。 此类提供类型安全C++的服务器应用程序的属性和操作封装。

类`COleDispatchDriver`提供主体自动化客户端的支持。 使用**添加新项**对话框中，创建派生自的类`COleDispatchDriver`。

然后指定描述的属性和函数的服务器应用程序的对象的类型库文件。 添加项对话框中读取此文件并创建`COleDispatchDriver`的派生的类，与你的应用程序可以调用访问中的服务器应用程序的对象的成员函数C++以类型安全的方式。 其他功能继承自`COleDispatchDriver`简化了调用适当的自动化服务器的过程。

### <a name="handling-events-in-automation-clients"></a>在自动化客户端中处理事件

如果你想要在你的自动化客户端中处理事件，您需要添加接收器接口。 MFC 提供了向导支持添加接收器接口的 ActiveX 控件，但不支持对其他 COM 服务器。

## <a name="see-also"></a>请参阅

[自动化客户端：使用类型库](../mfc/automation-clients-using-type-libraries.md)<br/>
[自动化](../mfc/automation.md)<br/>
[MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)
