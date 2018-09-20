---
title: 菜单和资源： 菜单合并功能 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- coordinating menu layouts [MFC]
- OLE containers [MFC], menus and resources
- toolbars [MFC], OLE document applications
- merging toolbar and status bar [MFC]
- menus [MFC], OLE document applications
ms.assetid: 80b6bb17-d830-4122-83f0-651fc112d4d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f4e76902335477ba507e6f3e7a66c5f862b8543
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418666"
---
# <a name="menus-and-resources-menu-merging"></a>菜单和资源：菜单合并

本文详细介绍所需 OLE 文档应用程序可处理可视编辑，并在就地激活正确的步骤。 就地激活的一个挑战容器和服务器 （组件） 应用程序。 用户将保留在同一框架窗口 （在容器文档的上下文），但实际上正在运行另一个应用程序 （服务器）。 这需要的资源的容器和服务器应用程序之间进行协调。

在本文中涵盖的主题包括：

- [菜单布局](#_core_menu_layouts)

- [工具栏和状态栏](#_core_toolbars_and_status_bars)

##  <a name="_core_menu_layouts"></a> 菜单布局

第一步是协调菜单布局。 有关详细信息，请参阅**菜单上创建**主题中[菜单编程注意事项](https://msdn.microsoft.com/library/ms647557.aspx)Windows SDK 中。

容器应用程序应创建一个新的菜单仅在就地激活嵌入的项时要使用。 最小值，此菜单应包含以下内容，按所列顺序：

1. 文件菜单等同于打开文件时使用的代码。 （通常没有任何其他菜单项的放置在下一项之前。）

1. 两个连续的分隔符。

1. 等同于打开文件时使用的代码窗口菜单 (仅当 MDI 应用程序中的容器应用程序)。 某些应用程序可能属于此组中，后者在就地激活嵌入的项时仍然在菜单上的其他菜单，选项菜单中，例如。

    > [!NOTE]
    >  可能会影响容器文档，例如缩放视图的其他菜单。 此菜单资源中的两个分隔符之间出现这些容器菜单。

服务器 （组件） 应用程序还应创建专门用于就地激活的新菜单。 它应与菜单时文件处于打开状态，使用类似，但不具有菜单项，如文件和操作而不是数据服务器文档的窗口。 通常情况下，此菜单包含以下值：

1. 编辑菜单等同于打开文件时使用的代码。

1. 分隔符。

1. 编辑菜单，如 Scribble 示例应用程序中的笔菜单的对象。

1. 分隔符。

1. 帮助菜单。

有关示例，查看为容器和服务器的某些示例就地菜单布局。 已删除的每个菜单项的详细信息进行更清晰的示例。 容器的就地菜单还拥有以下项：

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

连续的分隔符指示服务器的菜单中的第一部分应发送到何处。 接下来，查看服务器的就地菜单：

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

此处的分隔符指示容器的菜单项的第二组应发送到何处。 在此容器内的位置中激活此服务器中的对象时生成的菜单结构如下所示：

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

如您所见，分隔符已替换为不同的每个应用程序的菜单组。

服务器应用程序还应提供与就地菜单相关联的快捷键对应表。 容器会将其合并到其自己的快捷键对应表中。

就地激活嵌入的项时，框架将加载的就地菜单。 然后请求其菜单的服务器应用程序的就地激活，并将其分隔符所在。 这是菜单的合并方式。 你的操作系统上的文件和窗口的位置，从容器获取菜单和菜单从服务器获取有关操作的项。

##  <a name="_core_toolbars_and_status_bars"></a> 工具栏和状态栏

服务器应用程序应创建一个新的工具栏并将其位图存储在一个单独的文件。 应用程序向导生成应用程序将此位图存储在名为 ITOOLBAR 的文件。BMP。 在你的服务器的项到位，请激活并应包含相同项作为正常的工具栏中，但删除代表文件和窗口菜单上的项的图标时，新工具栏替换容器应用程序的工具栏。

此工具栏中加载你`COleIPFrameWnd`-派生的类，为你创建的应用程序向导。 由容器应用程序处理状态栏。 有关就地框架窗口的实现的详细信息，请参阅[服务器： 实现服务器](../mfc/servers-implementing-a-server.md)。

## <a name="see-also"></a>请参阅

[菜单和资源 (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[激活](../mfc/activation-cpp.md)<br/>
[服务器](../mfc/servers.md)<br/>
[容器](../mfc/containers.md)

