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
ms.openlocfilehash: 4e8f8c7fa8e24349a741b99822f13d5473373e17
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62225462"
---
# <a name="menus-and-resources-ole"></a>菜单和资源 (OLE)

此系列文章解释了如何使用 MFC OLE 文档应用程序中菜单和资源。

OLE 可视化编辑对其他要求菜单和其他资源，因为有多种模式的这两个容器中提供的 OLE 文档应用程序和服务器 （组件） 应用程序可以启动和使用。 例如，完全服务器应用程序可以在以下三种模式之一中运行：

- 单独存在。

- 在编辑上下文中的容器的项的位置。

- 打开，以进行编辑其容器，通常在单独的窗口的上下文以外的项。

这需要三个单独的菜单布局，一个用于应用程序的每个可能的模式。 快捷键对应表也是每种新模式必需的。 容器应用程序可能会或可能不支持就地激活;如果是这样，它需要新的菜单结构和关联的快捷键对应表。

在就地激活要求容器和服务器应用程序必须协商菜单、 工具栏和状态条空间。 记住，必须与此设计的所有资源。 文章[菜单和资源：菜单合并](../mfc/menus-and-resources-menu-merging.md)了解本主题的详细信息。

由于存在这些问题，通过应用程序向导创建 OLE 文档应用程序可以具有最多四个单独的菜单和快捷键对应表资源。 由于以下原因需要使用这些：

|资源名称|使用|
|-------------------|---------|
|IDR_MAINFRAME|在 MDI 应用程序是否没有文件处于打开状态，或在 SDI 应用程序而不考虑打开的文件中使用。 这是在非 OLE 应用程序中使用的标准菜单。|
|IDR_\<project>TYPE|如果已打开的文件在 MDI 应用程序中使用。 在应用程序以独立模式运行时使用。 这是在非 OLE 应用程序中使用的标准菜单。|
|IDR_\<project>TYPE_SRVR_IP|在位置中打开对象时使用的服务器或容器。|
|IDR_\<project>TYPE_SRVR_EMB|如果不使用就地激活的情况下打开对象服务器应用程序使用。|

每个这些资源名称代表一个菜单和快捷键对应表，通常情况下。 应在不使用应用程序向导创建的 MFC 应用程序中使用类似的方案。

以下文章介绍了与容器、 服务器和菜单合并有必要实现就地激活相关的主题：

- [菜单和资源：容器添加项](../mfc/menus-and-resources-container-additions.md)

- [菜单和资源：服务器添加项](../mfc/menus-and-resources-server-additions.md)

- [菜单和资源：菜单合并](../mfc/menus-and-resources-menu-merging.md)

## <a name="see-also"></a>请参阅

[OLE](../mfc/ole-in-mfc.md)
