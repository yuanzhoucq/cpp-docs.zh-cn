---
title: 自动化客户端
ms.date: 11/04/2016
helpviewer_keywords:
- clients, Automation
- Automation clients
- type libraries, Automation clients
- clients
ms.assetid: 84e34a79-06f6-4752-a33b-ae0ede1d8ecf
ms.openlocfilehash: 9c34f6fccd06635dfb686e6eb1f2cf895bb86989
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626084"
---
# <a name="automation-clients"></a>自动化客户端

利用自动化，您的应用程序可以操作在其他应用程序中实现的对象，或者公开对象以便让它们能够被操作。 自动化客户端是一种应用程序，它可以操作属于另一个应用程序的公开对象。 公开对象的应用程序称为自动化服务器。 客户端通过访问这些对象的属性和函数来操纵服务器应用程序的对象。

### <a name="types-of-automation-clients"></a>自动化客户端的类型

有两种类型的自动化客户端：

- 动态（在运行时）获取有关服务器的属性和操作的信息的客户端。

- 具有指定服务器属性和操作的静态信息（在编译时提供）的客户端。

第一种类型的客户端通过查询 OLE 系统的机制来获取有关服务器的方法和属性的信息 `IDispatch` 。 尽管它足以用于动态客户端，但 `IDispatch` 难以用于静态客户端，在这种情况下，要驱动的对象必须在编译时是已知的。 对于静态绑定的客户端，Microsoft 基础类提供了[COleDispatchDriver](reference/coledispatchdriver-class.md)类。

静态绑定的客户端使用与客户端应用程序静态链接的代理类。 此类提供服务器应用程序的属性和操作的类型安全 c + + 封装。

类 `COleDispatchDriver` 为自动化的客户端提供了主体支持。 使用 "**添加新项**" 对话框，可以创建派生自的类 `COleDispatchDriver` 。

然后指定用于说明服务器应用程序对象的属性和函数的类型库文件。 "添加项" 对话框读取此文件，并 `COleDispatchDriver` 使用成员函数创建派生类，应用程序可以调用此类以类型安全的方式访问服务器应用程序的对象。 从继承的其他功能 `COleDispatchDriver` 简化了调用正确自动化服务器的过程。

### <a name="handling-events-in-automation-clients"></a>处理自动化客户端中的事件

如果要处理自动化客户端中的事件，则需要添加接收器接口。 MFC 为 ActiveX 控件提供了向导支持以添加接收器接口，但不支持其他 COM 服务器。

## <a name="see-also"></a>另请参阅

[自动化客户端：使用类型库](automation-clients-using-type-libraries.md)<br/>
[自动化](automation.md)<br/>
[MFC 应用程序向导](reference/mfc-application-wizard.md)
