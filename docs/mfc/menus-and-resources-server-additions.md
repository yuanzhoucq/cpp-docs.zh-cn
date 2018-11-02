---
title: 菜单和资源：服务器添加
ms.date: 11/04/2016
f1_keywords:
- IDP_OLE_INIT_FAILED
helpviewer_keywords:
- OLE visual editing servers [MFC]
- accelerator tables [MFC], server applications
- visual editing [MFC], application menus and resources
- server applications [MFC], accelerator table
- string tables [MFC], visual editing applications
- servers [MFC], menu additions
- resources [MFC], server applications
- OLE server applications [MFC], menus and resources
- string editing [MFC], visual editing applications
- IDP_OLE_INIT_FAILED macro [MFC]
- server applications [MFC], OLE menus and resources
- OLE initialization failure [MFC]
ms.assetid: 56ce9e8d-8f41-4db8-8dee-e8b0702d057c
ms.openlocfilehash: 8b4e7787029fc9401ece02860f09b8159f086afe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592580"
---
# <a name="menus-and-resources-server-additions"></a>菜单和资源：服务器添加

本文介绍了对菜单和可视化编辑服务器 （组件） 应用程序中的其他资源进行更改。 服务器应用程序需要许多新增功能的菜单结构和其他资源，因为它可以启动在三种模式之一： 独立、 嵌入，或在位置。 如中所述[菜单和资源 (OLE)](../mfc/menus-and-resources-ole.md)文章中，有最多四个集的菜单。 所有四个用于 MDI 完全服务器应用程序，而只有三个用于袖珍服务器。 应用程序向导将创建菜单布局所需的服务器所需的类型。 可能需要一些自定义。

如果不使用应用程序向导，您可能想要看一看 HIERSVR。RC 中，MFC 示例应用程序的资源脚本[HIERSVR](../visual-cpp-samples.md)，以查看如何实现这些更改。

在本文中涵盖的主题包括：

- [添加服务器菜单](#_core_server_menu_additions)

- [添加快捷键对应表](#_core_server_application_accelerator_table_additions)

- [添加字符串表](../mfc/menus-and-resources-container-additions.md)

- [添加袖珍服务器](#_core_mini.2d.server_additions)

##  <a name="_core_server_menu_additions"></a> 添加服务器菜单

服务器 （组件） 应用程序必须具有为支持 OLE 可视化编辑添加的菜单资源。 在独立模式下运行应用程序时使用的菜单而无需更改，但生成应用程序之前，必须添加两个新的菜单资源： 一种用于支持就地激活和一种用于支持服务器完全打开。 完整和袖珍服务器应用程序使用这两个菜单资源。

- 若要支持就地激活，必须创建一个菜单资源，可非常类似于在独立模式下运行时使用的菜单资源。 在此菜单中的差异是缺少的文件和窗口项 （和任何其他应用程序，并不是数据处理的菜单项）。 容器应用程序会提供这些菜单项。 有关详细信息，并举例说明此菜单合并技术，请参阅文章[菜单和资源： 菜单合并](../mfc/menus-and-resources-menu-merging.md)。

- 若要支持完全打开激活，必须创建菜单资源几乎等同于使用的菜单资源以独立模式运行时。 此菜单资源的唯一修改是某些项重述以反映在嵌入复合文档中的项上的服务器正在其中运行这一事实。

除了本文中列出的更改，需要包括 AFXOLESV 资源文件。RC 中，这是 Microsoft 基础类库实现所必需的。 此文件是 MFC\Include 子目录中。

##  <a name="_core_server_application_accelerator_table_additions"></a> 添加服务器应用程序快捷键对应表

两个新的快捷键对应表资源必须添加到服务器应用程序;它们直接对应于前面所述的新菜单资源。 在就地激活服务器应用程序时，使用第一个快捷键对应表。 除了这些绑定到的文件和窗口菜单包含该视图的快捷键对应表中的所有条目。

第二个表是几乎视图的快捷键对应表的一个精确副本。 任何差异并行中所述的完全打开菜单中所做的更改[服务器菜单添加](#_core_server_menu_additions)。

这些快捷键对应表更改的示例，进行比较与在 HIERSVR IDR_MAINFRAME IDR_HIERSVRTYPE_SRVR_IP 和 IDR_HIERSVRTYPE_SRVR_EMB 快捷键对应表。RC 文件包含在 MFC OLE 示例[HIERSVR](../visual-cpp-samples.md)。 文件和窗口加速器就地表中缺少，它们的确切副本位于嵌入的表。

##  <a name="_core_string_table_additions_for_server_applications"></a> 服务器应用程序的添加的字符串表

添加仅一个字符串表中是必需的服务器应用程序 — 一个字符串，表示 OLE 初始化失败。 例如，下面是应用程序向导生成的字符串表条目：

|Id|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|OLE 初始化失败。 请确保 OLE 库的正确版本。|

##  <a name="_core_mini.2d.server_additions"></a> 添加袖珍服务器

添加了相同的内容同样适用于袖珍上面所列的完整服务器。 袖珍服务器不能在独立模式下运行，因为其主菜单是要小得多。 应用程序向导创建主菜单有仅文件菜单，包含项退出和有关。 嵌入和就地菜单和快捷键的袖珍都与用于完整服务器相同。

## <a name="see-also"></a>请参阅

[菜单和资源 (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[菜单和资源：菜单合并](../mfc/menus-and-resources-menu-merging.md)

