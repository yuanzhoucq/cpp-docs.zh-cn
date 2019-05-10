---
title: 服务器：实现服务器
ms.date: 11/04/2016
helpviewer_keywords:
- servers, implementing
- OLE server applications [MFC], implementing OLE servers
ms.assetid: 5bd57e8e-3b23-4f23-9597-496fac2d24b5
ms.openlocfilehash: 953d157f4bbad0b460947740a2622074dfc90f4f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308012"
---
# <a name="servers-implementing-a-server"></a>服务器：实现服务器

此文章介绍了 MFC 应用程序向导创建的可视化编辑服务器应用程序的代码。 如果不使用应用程序向导，本文列出了必须在其中编写代码来实现服务器应用程序的领域。

如果使用应用程序向导创建新的服务器应用程序，它为您提供大量的特定于服务器的代码。 如果要添加到现有应用程序的可视化编辑服务器功能，必须复制应用程序向导会添加必要的服务器代码的其余部分之前提供的代码。

应用程序向导提供的服务器代码划分为几个类别：

- 定义服务器资源：

  - 服务器在编辑嵌入的项在其自己的窗口中时使用的菜单资源。

  - 使用服务器处于就地活动状态时的菜单和工具栏资源。

  这些资源的详细信息，请参阅[菜单和资源：服务器添加](../mfc/menus-and-resources-server-additions.md)。

- 定义项类派生自`COleServerItem`。 服务器项的更多详细信息，请参阅[服务器：服务器项](../mfc/servers-server-items.md)。

- 更改到的文档类的基类`COleServerDoc`。 有关更多详细信息，请参阅[服务器：实现服务器文档](../mfc/servers-implementing-server-documents.md)。

- 定义框架窗口类派生自`COleIPFrameWnd`。 有关更多详细信息，请参阅[服务器：实现就地框架 Windows](../mfc/servers-implementing-in-place-frame-windows.md)。

- Windows 注册数据库中创建服务器应用程序的条目，并向 OLE 系统注册的服务器的新实例。 本主题的信息，请参阅[注册](../mfc/registration.md)。

- 初始化和启动服务器应用程序。 本主题的信息，请参阅[注册](../mfc/registration.md)。

有关详细信息，请参阅[COleServerItem](../mfc/reference/coleserveritem-class.md)， [COleServerDoc](../mfc/reference/coleserverdoc-class.md)，并[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)中*类库参考*。

## <a name="see-also"></a>请参阅

[服务器](../mfc/servers.md)<br/>
[容器](../mfc/containers.md)<br/>
[菜单和资源 (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[注册](../mfc/registration.md)
