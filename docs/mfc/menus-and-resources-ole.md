---
title: 菜单和资源 (OLE)
ms.date: 11/04/2016
helpviewer_keywords:
- OLE visual editing servers [MFC]
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- string tables [MFC], visual editing applications
- OLE containers [MFC], menus and resources
- OLE applications [MFC], menus and resources
- OLE server applications [MFC], menus and resources
- toolbars [MFC], OLE document applications
- string editing [MFC], visual editing applications
- server applications [MFC], OLE menus and resources
- applications [OLE], menus and resources
- menus [MFC], OLE document applications
- in-place activation [MFC], OLE menus and resources
- containers [MFC], OLE container applications
- OLE menus and resources [MFC]
ms.assetid: 52bfa086-7d3d-466f-94c7-c7061f3bdb3a
ms.openlocfilehash: e705f28476df7b594f9648aee8317759211c66c9
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626214"
---
# <a name="menus-and-resources-ole"></a>菜单和资源 (OLE)

这一组文章介绍了 MFC OLE 文档应用程序中的菜单和资源的使用。

OLE 视觉对象编辑对 OLE 文档应用程序提供的菜单和其他资源施加了其他要求，因为有多种模式可以启动和使用容器和服务器（组件）应用程序。 例如，完全服务器应用程序可以使用以下三种模式之一运行：

- 独立。

- 就地，用于在容器的上下文中编辑项。

- 打开，用于在其容器的上下文之外编辑项，通常在单独的窗口中进行编辑。

这需要三个单独的菜单布局，每个适用于每种可能的应用程序模式。 每个新模式还需要快捷键对应表。 容器应用程序不一定支持就地激活;如果是这样，则需要新的菜单结构和关联的快捷键对应表。

就地激活要求容器和服务器应用程序必须协商菜单、工具栏和状态栏空间。 所有资源都必须在设计时考虑到这一点。 项目[菜单和资源：菜单合并](menus-and-resources-menu-merging.md)详细介绍了此主题。

由于这些问题，使用应用程序向导创建的 OLE 文档应用程序最多可以有四个单独的菜单和快捷键对应表资源。 这些原因如下：

|资源名称|用途|
|-------------------|---------|
|IDR_MAINFRAME|在未打开任何文件的情况下在 MDI 应用程序中使用，或在 SDI 应用程序中使用，而不考虑打开的文件。 这是在非 OLE 应用程序中使用的标准菜单。|
|IDR_ \<project> 类型|如果文件已打开，则在 MDI 应用程序中使用。 当应用程序独立运行时使用。 这是在非 OLE 应用程序中使用的标准菜单。|
|IDR_ \<project> TYPE_SRVR_IP|当对象处于打开状态时，由服务器或容器使用。|
|IDR_ \<project> TYPE_SRVR_EMB|如果在不使用就地激活的情况下打开对象，则由服务器应用程序使用。|

其中每个资源名称都表示一个菜单，通常是一个快捷键对应表。 应在不使用应用程序向导创建的 MFC 应用程序中使用类似的方案。

以下文章讨论了实现就地激活所需的容器、服务器和菜单合并的相关主题：

- [菜单和资源：容器添加](menus-and-resources-container-additions.md)

- [菜单和资源：服务器添加](menus-and-resources-server-additions.md)

- [菜单和资源：菜单合并](menus-and-resources-menu-merging.md)

## <a name="see-also"></a>另请参阅

[OLE](ole-in-mfc.md)
