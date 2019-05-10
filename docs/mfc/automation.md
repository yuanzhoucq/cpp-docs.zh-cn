---
title: 自动化
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers, about Automation servers
- clients, Automation
- programmatic control [MFC]
- properties [MFC], Automation
- MFC, COM support
- OLE Automation
- Automation
- servers [MFC], Automation
- Automation clients
- sample applications [MFC], Automation
- methods [MFC]
- passing parameters, Automation
- Automation method [MFC]
- Automation, passing parameters
- Automation property [MFC]
- MFC COM, Automation
- methods [MFC], Automation
ms.assetid: 329117f0-c1aa-4680-a901-bfb71277dfba
ms.openlocfilehash: 7818aa708a762f2a284be029a6c3f3facd971d9a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374150"
---
# <a name="automation"></a>自动化

自动化（以前称为“OLE 自动化”）使一个应用程序能够操作在其他应用程序中实现的对象，或公开对象以供其他应用程序进行操作。

[自动化服务器](../mfc/automation-servers.md) 是一个通过 COM 接口向其他应用程序（称为 [自动化客户端](../mfc/automation-clients.md)）公开其功能的应用程序（一种 COM 服务器）。 公开可以使自动化客户端通过直接访问对象并使用它们提供的服务来自动执行某些功能。

自动化服务器和客户端使用始终从 `IDispatch` 派生的 COM 接口，并采用和返回一组称为“自动化类型”的特定数据类型。 您可以自动化任何公开自动化接口的对象，提供可以从其他应用程序访问的方法和属性。 自动化可用于 OLE 和 COM 对象。 自动化的对象可能是本地或远程的（在网络中其他可访问的计算机上）；因此有两个类别的自动化：

- 自动化（本地）。

- 远程自动化 （通过网络，使用分布式的 COM，即 DCOM）。

当应用程序提供对其他应用程序有用的功能时，公开对象是有益的。 例如，ActiveX 控件是一种类型的自动化服务器；托管 ActiveX 控件的应用程序是该控件的自动化客户端。

另一个示例是，字处理器可能向其他程序公开其拼写检查功能。 对象的公开可使供应商通过使用其他应用程序的现成功能改善其应用程序。 通过这种方式，自动化将在应用程序级别应用面向对象编程的部分准则，例如，可重用性和封装。

更重要的是自动化提供给用户和解决方案提供商的支持。 自动化通过常用的定义完善的接口公开应用程序功能，使得可以使用单一的常规编程语言（如 Microsoft Visual Basic）而非不同的应用程序特定的宏语言来构建全面的解决方案。

许多商业应用程序，如 Microsoft Excel 和 Microsoft Visual C++，允许您自动化大部分功能。 例如，在视觉对象C++，您可以编写 VBScript 宏来自动执行生成、 代码编辑，或调试任务的方面。

##  <a name="_core_passing_parameters_in_automation"></a> 在自动化中传递参数

创建自动化方法的一个难点是帮助提供一个统一的“安全”机制，以便在自动化服务器和客户端之间传递数据。 自动化使用 **VARIANT** 类型传递数据。 **VARIANT** 类型是带标记的联合。 它有一个表示值的数据成员（这是一个匿名的 C++ 联合）和一个指示存储在该联合中的信息类型的数据成员。 **变体**类型支持很多标准数据类型：2 字节和 4 字节整数、 4 和 8 字节浮点数、 字符串和布尔值。 此外，它支持**HRESULT** （OLE 错误代码），**货币**（定点数值类型），并且**日期**（绝对日期和时间） 类型，以及指向`IUnknown`和`IDispatch`接口。

**VARIANT** 类型封装在 [COleVariant](../mfc/reference/colevariant-class.md) 类中。 支持的 **CURRENCY** 和 **DATE** 类封装在 [COleCurrency](../mfc/reference/colecurrency-class.md) 和 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) 类中。

## <a name="automation-samples"></a>自动化示例

- [AUTOCLIK](../overview/visual-cpp-samples.md) 使用此示例可了解自动化技术并作为学习远程自动化的基础。

- [ACDUAL](../overview/visual-cpp-samples.md) 将双重接口添加到自动化服务器应用程序中。

- [CALCDRIV](../overview/visual-cpp-samples.md) 驱动 MFCCALC 的自动化客户端应用程序。

- [INPROC](../overview/visual-cpp-samples.md) 演示进程内自动化服务器应用程序。

- [IPDRIVE](../overview/visual-cpp-samples.md) 驱动 INPROC 的自动化客户端应用程序。

- [MFCCALC](../overview/visual-cpp-samples.md) 演示自动化客户端应用程序。

## <a name="what-do-you-want-to-know-more-about"></a>你想要了解更多信息

- [自动化客户端](../mfc/automation-clients.md)

- [自动化服务器](../mfc/automation-servers.md)

- [OLE](../mfc/ole-in-mfc.md)

- [Active 技术](../mfc/mfc-com.md)

## <a name="what-do-you-want-to-do"></a>你想要做什么

- [添加自动化类](../mfc/automation-servers.md)

- [使用类型库](../mfc/automation-clients-using-type-libraries.md)

- [访问自动化服务器](../mfc/automation-servers.md)

- [采用 C++ 编写自动化客户端](../mfc/automation-clients.md)

## <a name="see-also"></a>请参阅

[MFC COM](../mfc/mfc-com.md)
