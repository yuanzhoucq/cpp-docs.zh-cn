---
title: 菜单和资源：服务器添加
ms.date: 11/04/2016
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
ms.openlocfilehash: 8366cd8b0376766b7914c94a24cef6598761a805
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375980"
---
# <a name="menus-and-resources-server-additions"></a>菜单和资源：服务器添加

本文介绍了需要在可视化编辑服务器（组件）应用程序中对菜单和其他资源进行更改。 服务器应用程序需要对菜单结构和其他资源进行许多补充，因为它可以在以下三种模式之一启动：独立、嵌入或就地启动。 如[菜单和资源 （OLE）](../mfc/menus-and-resources-ole.md)文章中所述，最多有四组菜单。 这四个都用于 MDI 全服务器应用程序，而只有三个用于微型服务器。 应用程序向导将创建所需服务器类型所需的菜单布局。 可能需要进行一些自定义。

如果不使用应用程序向导，则可能需要查看 HIERSVR。RC，MFC 示例应用程序[HIERSVR](../overview/visual-cpp-samples.md)的资源脚本，用于查看这些更改是如何实现的。

本文涵盖的主题包括：

- [服务器菜单添加](#_core_server_menu_additions)

- [加速器表添加](#_core_server_application_accelerator_table_additions)

- [字符串表添加](../mfc/menus-and-resources-container-additions.md)

- [迷你服务器附加功能](#_core_mini.2d.server_additions)

## <a name="server-menu-additions"></a><a name="_core_server_menu_additions"></a>服务器菜单添加

服务器（组件）应用程序必须添加菜单资源以支持 OLE 可视化编辑。 在独立模式下运行应用程序时使用的菜单不必更改，但在构建应用程序之前必须添加两个新的菜单资源：一个支持就地激活，一个支持服务器完全打开。 两个菜单资源都由完整服务器和小型服务器应用程序使用。

- 要支持就地激活，必须创建与在独立模式下运行时使用的菜单资源非常相似的菜单资源。 此菜单的区别是缺少"文件和窗口"项（以及处理应用程序（而不是数据的任何其他菜单项）缺失。 容器应用程序将提供这些菜单项。 有关此菜单合并技术的详细信息和示例，请参阅文章["菜单和资源：菜单合并](../mfc/menus-and-resources-menu-merging.md)"。

- 要支持完全打开的激活，必须创建与在独立模式下运行时使用的菜单资源几乎相同的菜单资源。 对此菜单资源的唯一修改是，某些项被重新措辞，以反映服务器正在对嵌入在复合文档中的项运行的事实。

除了本文中列出的更改外，您的资源文件还需要包括 AFXOLESV。RC，这是 Microsoft 基础类库实现所必需的。 此文件位于 MFC_包括子目录中。

## <a name="server-application-accelerator-table-additions"></a><a name="_core_server_application_accelerator_table_additions"></a>服务器应用程序加速器表添加

必须向服务器应用程序添加两个新的加速器表资源;它们直接对应于前面描述的新菜单资源。 当服务器应用程序就地激活时，将使用第一个加速器表。 它由视图的快捷键表中的所有条目组成，但绑定到"文件和窗口"菜单的条目除外。

第二个表几乎是视图加速器表的精确副本。 [服务器菜单添加](#_core_server_menu_additions)中提及的完全打开菜单中所做的任何差异并行更改。

有关这些加速器表更改的示例，请将 IDR_HIERSVRTYPE_SRVR_IP和IDR_HIERSVRTYPE_SRVR_EMB加速器表与 HIERSVR 中的IDR_MAINFRAME进行比较。RC 文件包含在 MFC OLE 示例[HIERSVR](../overview/visual-cpp-samples.md)中。 原位表中缺少"文件和窗口"快捷键，并且它们的确切副本位于嵌入表中。

## <a name="string-table-additions-for-server-applications"></a><a name="_core_string_table_additions_for_server_applications"></a>服务器应用程序的字符串表添加

服务器应用程序中只需要添加一个字符串表 - 一个字符串表示 OLE 初始化失败。 例如，下面是应用程序向导生成的字符串表条目：

|ID|字符串|
|--------|------------|
|IDP_OLE_INIT_FAILED|OLE 初始化失败。 确保 OLE 库是正确的版本。|

## <a name="miniserver-additions"></a><a name="_core_mini.2d.server_additions"></a>迷你服务器附加功能

与上面列出的完整服务器相同的附加功能适用于小型服务器。 由于小型服务器无法以独立模式运行，因此其主菜单要小得多。 应用程序向导创建的主菜单只有一个文件菜单，仅包含"退出"和"左右"项。 小型服务器的嵌入式和就地菜单和加速器与完整服务器的菜单和加速器相同。

## <a name="see-also"></a>另请参阅

[菜单和资源 （OLE）](../mfc/menus-and-resources-ole.md)<br/>
[菜单和资源：菜单合并](../mfc/menus-and-resources-menu-merging.md)
