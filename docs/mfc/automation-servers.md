---
title: 自动化服务器 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Automation servers
- COM components, Automation servers
- dispatch maps [MFC], Automation servers
- servers, Automation
ms.assetid: 523fd155-51ce-4f91-b986-b74bdbdd7d92
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2cc163559b4946626e754b70a1b54d4fe20306c7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377613"
---
# <a name="automation-servers"></a>自动化服务器

利用自动化，您的应用程序可以操作在其他应用程序中实现的对象，或者公开对象以便操作它们。 自动化服务器是向其他应用程序公开可编程对象 （称为自动化对象） 的应用程序 (称为[自动化客户端](../mfc/automation-clients.md))。 自动化服务器有时称为自动化组件。

通过公开自动化对象，客户端可以通过直接访问对象和服务器提供的功能来自动执行某些过程。 当应用程序提供对其他应用程序有用的功能时，以这种方式公开对象有很大好处。 例如，字处理器可能公开其拼写检查器功能以便让其他程序使用它。 公开对象后，供应商便能使用其他应用程序的现成功能改进其应用程序的功能。

这些自动化对象将属性和方法作为其外部接口。 属性是自动化对象的命名特性。 属性与 C++ 类的数据成员类似。 方法是处理自动化对象的函数。 方法与 C++ 类的公共成员函数类似。

> [!NOTE]
>  尽管属性与 C++ 数据成员类似，但前者不可直接访问。 若要提供透明访问，请使用一对 get/set 成员函数在自动化对象中设置一个内部变量来访问这些属性。

通过定义完善的常用接口公开应用程序功能后，自动化实现了在单个通用编程语言（如 Microsoft Visual Basic）中（而不是在各种特定于应用程序的宏语言中）生成应用程序。

##  <a name="_core_support_for_automation_servers"></a> 对自动化服务器的支持

Visual C++ 和 MFC 框架为自动化服务器提供了广泛的支持。 它们处理了创建自动化服务器所涉及的大部分工作，从而让您将精力放在应用程序的功能上。

用于支持自动化的框架的主要机制是调度映射，即扩展到公开 OLE 的方法和属性所需的声明和调用中的一组宏。 典型的调度映射如下所示：

[!code-cpp[NVC_MFCAutomation#1](../mfc/codesnippet/cpp/automation-servers_1.cpp)]

“属性”窗口和类视图可帮助维护调度映射。 向某个类添加新方法或属性时，Visual C++ 将添加对应的 `DISP_FUNCTION` 或 `DISP_PROPERTY` 宏并使用指示类名、方法或属性的内部和外部名称以及数据类型的参数。

**添加类**对话框还简化了自动化类的声明和属性，操作管理。 当您使用“添加类”对话框向您的项目添加类时，应指定其基类。 如果基类允许自动化，则“添加类”对话框将显示一些控件，您可使用这些控件指定新类是否应支持自动化、新类是否是“OLE 可创建的”（即，类的对象是否可以应来自 COM 客户端的请求而创建）以及 COM 客户端要使用的外部名称。

**添加类**对话框然后创建一个类声明，包括相应的宏的 OLE 功能您已指定。 它还会为你的类的成员函数的实现添加主干代码。

MFC 应用程序向导简化了让自动化服务器应用程序起作用所涉及的步骤。 如果选择**自动化**复选框**高级功能**页上，MFC 应用程序向导将添加到应用程序的`InitInstance`函数注册您的自动化所需的调用对象，并运行应用程序作为自动化服务器。

### <a name="what-do-you-want-to-do"></a>你想要做什么

- [了解自动化客户端](../mfc/automation-clients.md)

- [详细了解类 CCmdTarget](../mfc/reference/ccmdtarget-class.md)

- [详细了解类 COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)

## <a name="see-also"></a>请参阅

[自动化](../mfc/automation.md)<br/>
[MFC 应用程序向导](../mfc/reference/mfc-application-wizard.md)

