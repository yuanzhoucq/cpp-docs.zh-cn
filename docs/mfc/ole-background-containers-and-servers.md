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
ms.openlocfilehash: c154562e58cf8f37d77df61556fe25b19ca54c70
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346119"
---
# <a name="ole-background-containers-and-servers"></a>OLE 后台：容器和服务器

容器应用程序是可将嵌入项或者链接项并入自己的文档中的应用程序。 管理容器应用程序的文档必须能够存储和显示 OLE 文档组件，以及创建应用程序本身的数据。 容器应用程序还必须允许用户以插入新项或通过激活服务器应用程序在必要时编辑现有项。 一文中列出了的容器应用程序的用户界面要求[容器：用户界面问题](../mfc/containers-user-interface-issues.md)。

服务器应用程序或组件应用程序，可以创建供容器应用程序使用的 OLE 文档组件的应用程序。 服务器应用程序通常支持拖放或其数据复制到剪贴板，以便容器应用程序可以插入为嵌入或链接项的数据。 应用程序可以是一个容器和服务器。

大多数服务器都是独立的应用程序或完整服务器;它们既可以作为独立应用程序运行或可由容器应用程序启动。 袖珍服务器是一种特殊的服务器应用程序可以仅由容器启动。 它不能作为独立的应用程序运行。 Microsoft 绘图和 Microsoft Graph 服务器是袖珍的示例。

容器和服务器不直接通信。 相反，它们进行通信通过 OLE 系统动态链接库 (DLL)。 这些 Dll 提供功能的容器和服务器调用，但容器和服务器提供的 Dll 调用的回调函数。

使用此通信的方式，容器不需要知道服务器应用程序的实现细节。 它使容器能够接受任何服务器而无需定义类型的服务器可以使用自己创建的项目。 因此，容器应用程序的用户可以充分利用未来的应用程序和数据格式。 如果这些新的应用程序是 OLE 组件，复合文档将能够将这些应用程序创建的项。

## <a name="see-also"></a>请参阅

[OLE 后台](../mfc/ole-background.md)<br/>
[OLE 后台：MFC 实现](../mfc/ole-background-mfc-implementation.md)<br/>
[容器](../mfc/containers.md)<br/>
[服务器](../mfc/servers.md)<br/>
[容器：客户端项](../mfc/containers-client-items.md)<br/>
[服务器：服务器项](../mfc/servers-server-items.md)
