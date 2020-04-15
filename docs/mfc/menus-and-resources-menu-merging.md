---
title: 菜单和资源：菜单合并
ms.date: 11/04/2016
helpviewer_keywords:
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- coordinating menu layouts [MFC]
- OLE containers [MFC], menus and resources
- toolbars [MFC], OLE document applications
- merging toolbar and status bar [MFC]
- menus [MFC], OLE document applications
ms.assetid: 80b6bb17-d830-4122-83f0-651fc112d4d1
ms.openlocfilehash: 149af83bd53b7a97fd264bd6b18701fc9f64ea1f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364760"
---
# <a name="menus-and-resources-menu-merging"></a>菜单和资源：菜单合并

本文详细介绍了 OLE 文档应用程序正确处理视觉编辑和就地激活所需的步骤。 就地激活对容器和服务器（组件）应用程序都构成挑战。 用户保留在同一帧窗口中（在容器文档的上下文中），但实际上正在运行另一个应用程序（服务器）。 这需要容器和服务器应用程序的资源之间的协调。

本文涵盖的主题包括：

- [菜单布局](#_core_menu_layouts)

- [工具栏和状态栏](#_core_toolbars_and_status_bars)

## <a name="menu-layouts"></a><a name="_core_menu_layouts"></a>菜单布局

第一步是协调菜单布局。 容器应用程序应创建一个新菜单，仅在嵌入项目就地激活时使用。 至少，此菜单应按列出的顺序包含以下内容：

1. 文件菜单与打开文件时使用的文件菜单相同。 （通常不会在下一个项之前放置其他菜单项。

1. 两个连续分隔符。

1. 窗口菜单与打开文件时使用的窗口菜单相同（仅当 MDI 应用程序中的容器应用程序时）。 某些应用程序可能具有属于此组中的其他菜单（如"选项"菜单），当嵌入项激活到位时，该菜单将保留在菜单上。

    > [!NOTE]
    >  可能还有其他影响容器文档视图的菜单，如"缩放"。 这些容器菜单出现在此菜单资源中的两个分隔符之间。

服务器（组件）应用程序还应创建一个新菜单，专门用于就地激活。 它应类似于打开文件时使用的菜单，但没有菜单项，如操作服务器文档而不是数据的文件和窗口。 通常，此菜单包括以下内容：

1. 编辑菜单与打开文件时使用的菜单相同。

1. 分隔符。

1. 对象编辑菜单，如"涂鸦"示例应用程序中的"笔"菜单。

1. 分隔符。

1. 帮助菜单。

例如，查看容器和服务器的一些示例就地菜单的布局。 已删除每个菜单项的详细信息，以使示例更清晰。 容器的就地菜单具有以下条目：

```
IDR_CONTAINERTYPE_CNTR_IP MENU PRELOAD DISCARDABLE
BEGIN
    POPUP "&File C1"
    MENUITEM SEPARATOR
    POPUP "&Zoom C2"
    MENUITEM SEPARATOR
    POPUP "&Options C3"
    POPUP "&Window C3"
END
```

连续分隔符指示服务器菜单的第一部分应转到何处。 现在查看服务器的就地菜单：

```
IDR_SERVERTYPE_SRVR_IP MENU PRELOAD DISCARDABLE
BEGIN
    POPUP "&Edit S1"
    MENUITEM SEPARATOR
    POPUP "&Format S2"
    MENUITEM SEPARATOR
    POPUP "&Help S3"
END
```

此处的分隔符指示第二组容器菜单项应转到何处。 当此服务器中的对象在此容器内就地激活时，生成的菜单结构如下所示：

```
BEGIN
    POPUP "&File C1"
    POPUP "&Edit S1"
    POPUP "&Zoom C2"
    POPUP "&Format S2"
    POPUP "&Options C3
    POPUP "&Window C3"
    POPUP "&Help S3"
END
```

如您所见，分隔符已替换为每个应用程序菜单的不同组。

与就地菜单关联的加速器表也应由服务器应用程序提供。 容器将将它们合并到自己的加速器表中。

当嵌入的项目就地激活时，框架将加载就地菜单。 然后，它要求服务器应用程序提供其菜单进行就地激活，并将其插入分离器的位置。 这是菜单的组合方式。 从容器获取用于在文件和窗口放置上操作的菜单，并从服务器获取用于对项目操作的菜单。

## <a name="toolbars-and-status-bars"></a><a name="_core_toolbars_and_status_bars"></a>工具栏和状态栏

服务器应用程序应创建新工具栏，并将其位图存储在单独的文件中。 应用程序向导生成的应用程序将此位图存储在名为 ITOOLBAR 的文件中。Bmp。 当服务器的项目就位激活时，新工具栏将替换容器应用程序的工具栏，并且应该包含与普通工具栏相同的项目，但删除表示"文件和窗口"菜单上项的图标。

此工具栏加载到派生`COleIPFrameWnd`类中，由应用程序向导为您创建。 状态栏由容器应用程序处理。 有关就地帧窗口实现的详细信息，请参阅[服务器：实现服务器](../mfc/servers-implementing-a-server.md)。

## <a name="see-also"></a>另请参阅

[菜单和资源 （OLE）](../mfc/menus-and-resources-ole.md)<br/>
[激活](../mfc/activation-cpp.md)<br/>
[服务器](../mfc/servers.md)<br/>
[容器](../mfc/containers.md)
