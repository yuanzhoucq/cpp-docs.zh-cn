---
title: 容器：高级功能
ms.date: 11/04/2016
helpviewer_keywords:
- links [MFC], to embedded OLE objects
- containers [MFC], links to embedded OLE objects
- containers [MFC], advanced features
- container/server applications [MFC]
- embedded objects [MFC]
- OLE controls [MFC], containers
- OLE containers [MFC], advanced features
- server/container applications [MFC]
- containers [MFC], container applications
ms.assetid: 221fd99c-b138-40fa-ad6a-974e3b3ad1f8
ms.openlocfilehash: 1ef4ed9865d3a88a6ff85f777984b856d03cc48e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616364"
---
# <a name="containers-advanced-features"></a>容器：高级功能

本文介绍了将可选高级功能并入现有容器应用程序所需的步骤。 这些功能包括：

- [既是容器也是服务器的应用程序](#_core_creating_a_container_server_application)

- [指向嵌入对象的 OLE 链接](#_core_links_to_embedded_objects)

## <a name="creating-a-containerserver-application"></a><a name="_core_creating_a_container_server_application"></a>创建容器/服务器应用程序

容器/服务器应用程序是既充当容器又充当服务器的应用程序。 Microsoft Word for Windows 是此应用程序的一个示例。 您可将 Word for Windows 文档嵌入其他应用程序，也可将项目嵌入 Word for Windows 文档。 修改既是容器也是完全服务器的容器应用程序的过程（您无法创建组合容器/袖珍服务器应用程序）类似于创建完全服务器的过程。

文章[服务器：实现服务器](servers-implementing-a-server.md)列出了实现服务器应用程序所需的多个任务。 如果将容器应用程序转换为容器/服务器应用程序，则你需要执行一些相同的任务，将代码添加到容器。 下面列出了重要的注意事项：

- 由应用程序向导创建的容器代码已初始化 OLE 子系统。 您无需为此支持更改或添加任何内容。

- 无论文档类的基类是否是 `COleDocument`，请将基类更改为 `COleServerDoc`。

- 重写 `COleClientItem::CanActivate` 以避免在使用服务器自身进行就地编辑时就地编辑项目。

   例如，MFC OLE 示例[OCLIENT](../overview/visual-cpp-samples.md)已嵌入由容器/服务器应用程序创建的项目。 打开 OCLIENT 应用程序并就地编辑由容器/服务器应用程序创建的项目。 编辑应用程序项时，您决定要嵌入由 MFC OLE 示例[HIERSVR](../overview/visual-cpp-samples.md)创建的项。 为此，您无法使用就地激活。 您必须完全打开 HIERSVR 才能激活此项目。 由于 Microsoft 基础类库不支持此 OLE 功能，因此重写 `COleClientItem::CanActivate` 使您可检查此情况并防止应用程序中出现可能的运行时错误。

如果要创建新的应用程序并希望它充当容器/服务器应用程序，请在应用程序向导的“OLE 选项”对话框中选择此选项，将自动创建此支持。 有关详细信息，请参阅文章[概述：创建 ActiveX 控件容器](reference/creating-an-mfc-activex-control-container.md)。 有关 MFC 示例的信息，请参阅[Mfc 示例](../overview/visual-cpp-samples.md#mfc-samples)。

请注意，您无法将 MDI 应用程序插入其本身。 为容器/服务器的应用程序不能插入其本身，除非它是 SDI 应用程序。

## <a name="links-to-embedded-objects"></a><a name="_core_links_to_embedded_objects"></a>指向嵌入对象的链接

利用“链接到嵌入对象”功能，用户可在您的容器应用程序中创建包含指向嵌入对象的 OLE 链接的文档。 例如，在字处理器中创建一个包含嵌入电子表格的文档。 如果应用程序支持链接到嵌入对象，则可将链接粘贴到字处理器的文档中包含的电子表格。 利用此功能，您的应用程序可使用电子表格中包含的信息，而不必知道字处理器最初从何处获得此信息。

#### <a name="to-link-to-embedded-objects-in-your-application"></a>链接到应用程序中的嵌入对象

1. 从 `COleLinkingDoc` 而不是 `COleDocument` 派生您的文档类。

1. 使用 OLE 开发工具附带的类 ID 生成器为应用程序创建 OLE 类 ID （**CLSID**）。

1. 向 OLE 注册应用程序。

1. 创建一个 `COleTemplateServer` 对象作为应用程序类的成员。

1. 在应用程序类的 `InitInstance` 成员函数中，执行以下操作：

   - 通过调用对象的 `COleTemplateServer` 成员函数，将您的 `ConnectTemplate` 对象连接到文档模板。

   - 调用 `COleTemplateServer::RegisterAll` 成员函数以向 OLE 系统注册所有类对象。

   - 调用 `COleTemplateServer::UpdateRegistry`。 `UpdateRegistry`如果应用程序未通过 "/Embedded" 开关启动，则应*OAT_CONTAINER*唯一的参数。 这会将应用程序作为可支持链接到嵌入对象的容器注册。

      如果应用程序已使用“/Embedded”开关启动，则不应显示其主窗口，这与服务器应用程序类似。

MFC OLE 示例[OCLIENT](../overview/visual-cpp-samples.md)实现了此功能。 有关如何执行此操作的示例，请参阅 `InitInstance` OCLIENT 中的函数 *。* 此示例应用程序的 CPP 文件。

## <a name="see-also"></a>另请参阅

[容器](containers.md)<br/>
[服务器](servers.md)
