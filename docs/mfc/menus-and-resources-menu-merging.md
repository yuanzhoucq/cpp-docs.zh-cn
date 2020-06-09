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
ms.openlocfilehash: 03d27443f90634b5d787eee25acc951d24178f42
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626220"
---
# <a name="menus-and-resources-menu-merging"></a>菜单和资源：菜单合并

本文详细介绍了 OLE 文档应用程序正确处理可视编辑和就地激活所需的步骤。 就地激活为容器和服务器（组件）应用程序带来了挑战。 用户仍将保留在同一框架窗口中（在容器文档的上下文中），但实际上是在运行其他应用程序（服务器）。 这需要在容器和服务器应用程序的资源之间进行协调。

本文中涵盖的主题包括：

- [菜单布局](#_core_menu_layouts)

- [工具栏和状态栏](#_core_toolbars_and_status_bars)

## <a name="menu-layouts"></a><a name="_core_menu_layouts"></a>菜单布局

第一步是协调菜单布局。 容器应用程序应创建一个新菜单，该菜单仅在就地激活嵌入项时使用。 此菜单至少应包含以下各项，顺序如下：

1. 文件菜单与打开文件时所用的相同。 （通常，不会在下一项之前放置其他菜单项。）

1. 两个连续的分隔符。

1. 窗口菜单与打开文件时使用的菜单相同（仅在 MDI 应用程序中的容器应用程序中）。 某些应用程序可能具有属于此组的其他菜单，如选项菜单，该菜单在就地激活嵌入项时仍保留在菜单上。

    > [!NOTE]
    >  可能会有其他影响容器文档的视图的菜单，例如缩放。 这些容器菜单显示在此菜单资源中的两个分隔符之间。

服务器（组件）应用程序还应创建专门用于就地激活的新菜单。 它应该与打开文件时使用的菜单相似，但不包含菜单项（例如操作服务器文档的文件和窗口，而不是数据）。 通常，此菜单由以下内容组成：

1. 编辑菜单与打开文件时所用的菜单完全相同。

1. 分隔符。

1. 对象编辑菜单，如自由曲线示例应用程序中的 "笔" 菜单。

1. 分隔符。

1. "帮助" 菜单。

例如，查看容器和服务器的一些就地菜单示例的布局。 为了使示例更清晰，已删除每个菜单项的详细信息。 容器的就地菜单包含以下项：

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

连续的分隔符指示服务器菜单的第一部分应到达的位置。 现在，查看服务器的就地菜单：

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

此处的分隔符指示第二组容器菜单项的位置。 在此容器内就地激活此服务器中的对象时生成的菜单结构如下所示：

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

与就地菜单关联的快捷键对应表还应由服务器应用程序提供。 容器将它们合并到其自己的快捷键对应表中。

就地激活嵌入项时，框架会加载就地菜单。 然后，它会向服务器应用程序请求就地激活菜单，并将其插入到分隔符所在位置。 这就是菜单合并的方式。 从容器中获取用于对文件和窗口位置进行操作的菜单，并从服务器获取用于对项进行操作的菜单。

## <a name="toolbars-and-status-bars"></a><a name="_core_toolbars_and_status_bars"></a>工具栏和状态栏

服务器应用程序应该创建一个新的工具栏，并将其位图存储在单独的文件中。 应用程序向导生成的应用程序将此位图存储在名为 ITOOLBAR 的文件中。.BMP. 就地激活服务器的项时，新工具栏将替换容器应用程序的工具栏，并应包含与普通工具栏相同的项，但会删除表示文件和窗口菜单上的项的图标。

此工具栏加载在 `COleIPFrameWnd` 派生类中，由应用程序向导为您创建。 状态栏由容器应用程序进行处理。 有关就地框架窗口实现的详细信息，请参阅[服务器：实现服务器](servers-implementing-a-server.md)。

## <a name="see-also"></a>另请参阅

[菜单和资源（OLE）](menus-and-resources-ole.md)<br/>
[激活](activation-cpp.md)<br/>
[服务器](servers.md)<br/>
[容器](containers.md)
