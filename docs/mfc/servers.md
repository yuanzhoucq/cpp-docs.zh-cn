---
title: 服务器
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC]
- OLE server applications [MFC], activation
- full-server
- servers
- mini-server
- OLE server applications [MFC], server types
- server applications [MFC]
ms.assetid: e45172e8-eae3-400a-8139-0fa009a42fdc
ms.openlocfilehash: d1e0a8ca85055c289d1ef8e1c36fcd35eab61c91
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526493"
---
# <a name="servers"></a>服务器

服务器应用程序 （或组件应用程序） 创建供容器应用程序使用的 OLE 项 （或组件）。 可视化编辑服务器应用程序还支持可视编辑或就地激活。 OLE 服务器的另一种形式是[自动化服务器](../mfc/automation-servers.md)。 某些服务器应用程序支持嵌入项，则创建其他支持嵌入和链接项的创建。 一些只支持链接，尽管这并不常见。 当用户想要编辑某个项时，所有服务器应用程序必须由容器应用程序都支持激活。 应用程序可以是一个容器和服务器。 换而言之，它可以同时将数据合并到其文档，并创建可作为项合并到其他应用程序的文档的数据。

袖珍服务器是一种特殊的仅可以由容器启动的服务器应用程序。 Microsoft 绘图和 Microsoft Graph 是袖珍的示例。 袖珍服务器不会将文档存储为磁盘上的文件。 相反，它读取它的文档，并将其写入到属于容器的文档中的项。 因此，袖珍服务器支持仅嵌入未链接。

可以运行作为独立的应用程序或容器应用程序启动的整个服务器。 完整的服务器可以将文档存储为磁盘上的文件。 它可以支持仅嵌入这两个嵌入和链接，或仅链接。 容器应用程序的用户可以通过在服务器和容器中的粘贴命令选择剪切或复制命令创建嵌入的项。 通过在容器中选择服务器中的复制命令和粘贴链接命令将创建一个链接的项。 或者，用户可以创建使用插入对象对话框中的嵌入或链接项。

下表总结了不同类型的服务器的特征：

### <a name="server-characteristics"></a>服务器的特征

|服务器类型|支持多个实例|每个文档的项|每个实例的文档|
|--------------------|---------------------------------|------------------------|----------------------------|
|袖珍服务器|是|1|1|
|SDI 完全服务器|是|1 (如果支持链接，则一个或多个)|1|
|MDI 完全服务器|否 （不要求）|1 (如果支持链接，则一个或多个)|0 或更多|

服务器应用程序应同时支持多个容器，在的多个容器将用于编辑嵌入或链接项。 如果服务器是 SDI 应用程序 （或与对话框接口袖珍服务器），必须能够同时运行多个服务器实例。 这允许应用程序来处理每个容器请求的单独实例。

如果服务器是 MDI 应用程序，它可以创建新的 MDI 子窗口每次需要编辑一个项容器。 这样一来，应用程序的单个实例可以支持多个容器。

服务器应用程序必须告知 OLE 系统 Dll 要执行的操作的服务器的一个实例已在运行另一个容器请求其服务时如果： 它应在启动服务器的新实例或在所有容器的请求定向到的一个实例服务器。

在服务器上的更多详细信息，请参阅：

- [服务器：实现服务器](../mfc/servers-implementing-a-server.md)

- [服务器：实现服务器文档](../mfc/servers-implementing-server-documents.md)

- [服务器：实现就地框架窗口](../mfc/servers-implementing-in-place-frame-windows.md)

- [服务器：服务器项](../mfc/servers-server-items.md)

- [服务器：用户界面问题](../mfc/servers-user-interface-issues.md)

## <a name="see-also"></a>请参阅

[OLE](../mfc/ole-in-mfc.md)<br/>
[容器](../mfc/containers.md)<br/>
[容器：高级功能](../mfc/containers-advanced-features.md)<br/>
[菜单和资源 (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[注册](../mfc/registration.md)<br/>
[自动化服务器](../mfc/automation-servers.md)

