---
title: OLE 后台：容器和服务器
ms.date: 11/04/2016
helpviewer_keywords:
- OLE full-server applications [MFC]
- server applications [MFC], communication with containers
- full-server [MFC]
- server applications [MFC], requirements
- server applications [MFC], defined
- OLE server applications [MFC], about server applications
- server applications [MFC], full-server vs. mini-server
- OLE server applications [MFC], mini-server applications
- OLE containers [MFC], container applications
- containers [MFC], OLE container applications
- server applications [MFC]
ms.assetid: dafbb31d-096c-4654-b774-12900d832919
ms.openlocfilehash: 7c3130ab9d8dff6551ef0ecbec43e5422dbdc4c4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617913"
---
# <a name="ole-background-containers-and-servers"></a>OLE 后台：容器和服务器

容器应用程序是可将嵌入项或者链接项并入自己的文档中的应用程序。 容器应用程序管理的文档必须能够存储和显示 OLE 文档组件以及应用程序本身创建的数据。 容器应用程序还必须允许用户在必要时通过激活服务器应用程序来插入新项或编辑现有项。 容器应用程序的用户界面要求在 "[容器：用户界面问题](containers-user-interface-issues.md)" 一文中列出。

服务器应用程序或组件应用程序是一种应用程序，可以创建供容器应用程序使用的 OLE 文档组件。 服务器应用程序通常支持将数据拖放或复制到剪贴板，以便容器应用程序可以将数据作为嵌入项或链接项插入。 应用程序可以同时为容器和服务器。

大多数服务器都是独立的应用程序或完整的服务器;它们可以作为独立的应用程序运行，也可以由容器应用程序启动。 袖珍服务器是一种特殊类型的服务器应用程序，只能由容器启动。 它不能作为独立应用程序运行。 Microsoft 绘图和 Microsoft Graph 服务器是 miniservers 的示例。

容器和服务器不会直接通信。 相反，它们通过 OLE 系统动态链接库（DLL）进行通信。 这些 Dll 提供容器和服务器调用的函数，容器和服务器提供 Dll 调用的回调函数。

使用这种通信方式，容器无需知道服务器应用程序的实现细节。 它允许容器接受任何服务器创建的项目，而无需定义可供其使用的服务器类型。 因此，容器应用程序的用户可以利用未来的应用程序和数据格式。 如果这些新应用程序是 OLE 组件，则复合文档将能够合并由这些应用程序创建的项目。

## <a name="see-also"></a>另请参阅

[OLE 背景](ole-background.md)<br/>
[OLE 后台：MFC 实现](ole-background-mfc-implementation.md)<br/>
[容器](containers.md)<br/>
[服务器](servers.md)<br/>
[容器：客户端项](containers-client-items.md)<br/>
[服务器：服务器项](servers-server-items.md)
