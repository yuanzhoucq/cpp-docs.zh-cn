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
ms.openlocfilehash: c1dfd059572c433e8fd7ccaf6e5c48e880f59cad
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445185"
---
# <a name="menus-and-resources-server-additions"></a>菜单和资源：服务器添加

本文说明了需要对可视编辑服务器（组件）应用程序中的菜单和其他资源进行的更改。 服务器应用程序需要很多添加到菜单结构和其他资源，因为它可以使用以下三种模式之一来启动：独立、嵌入或就地。 如[菜单和资源（OLE）](../mfc/menus-and-resources-ole.md)一文中所述，最多可以有四组菜单。 所有四个用于 MDI 完全服务器应用程序，而只有三个用于袖珍服务器。 应用程序向导将创建所需服务器类型的菜单布局。 某些自定义可能是必需的。

如果不使用应用程序向导，可能需要查看 HIERSVR。RC，MFC 示例应用程序[HIERSVR](../overview/visual-cpp-samples.md)的资源脚本，用于查看如何实现这些更改。

本文中涵盖的主题包括：

- [服务器菜单添加项](#_core_server_menu_additions)

- [快捷键对应表添加项](#_core_server_application_accelerator_table_additions)

- [字符串表添加](../mfc/menus-and-resources-container-additions.md)

- [添加袖珍](#_core_mini.2d.server_additions)

##  <a name="_core_server_menu_additions"></a>服务器菜单添加项

服务器（组件）应用程序必须添加菜单资源才能支持 OLE 可视化编辑。 当应用程序在独立模式下运行时使用的菜单无需更改，但必须在构建应用程序之前添加两个新的菜单资源：一个用于支持就地激活，另一个用于支持完全打开的服务器。 这两个菜单资源均由完全和袖珍应用程序使用。

- 若要支持就地激活，必须创建与以独立模式运行时所使用的菜单资源非常相似的菜单资源。 此菜单的区别在于缺少文件和窗口项（以及处理应用程序的任何其他菜单项，而不是数据）。 容器应用程序将提供这些菜单项。 有关此菜单合并技术的详细信息和示例，请参阅菜单[和资源：菜单合并](../mfc/menus-and-resources-menu-merging.md)一文。

- 若要支持完全打开的激活，必须创建与在独立模式下运行时使用的菜单资源几乎相同的菜单资源。 对此 menu 资源的唯一修改是，某些项改写，以反映服务器对嵌入到复合文档中的项的操作。

除了本文中列出的更改之外，资源文件还需要包含 AFXOLESV。RC，这是 Microsoft 基础类库实现所必需的。 此文件位于 MFC\Include 子目录中。

##  <a name="_core_server_application_accelerator_table_additions"></a>服务器应用程序加速器表添加

必须向服务器应用程序添加两个新的快捷键对应表资源;它们与前面所述的新菜单资源直接对应。 当就地激活服务器应用程序时，将使用第一个快捷键对应表。 它包含视图的快捷键对应表中的所有条目，但绑定到文件和窗口菜单的项除外。

第二个表几乎是视图快捷键对应表的精确副本。 [服务器菜单添加内容](#_core_server_menu_additions)中所述的完全打开菜单中进行的任何差异并行更改。

有关这些快捷键表更改的示例，请将 IDR_HIERSVRTYPE_SRVR_IP 和 IDR_HIERSVRTYPE_SRVR_EMB 快捷键对应表与 HIERSVR 中的 IDR_MAINFRAME 进行比较。MFC OLE 示例[HIERSVR](../overview/visual-cpp-samples.md)中包含的 RC 文件。 就地表中缺少文件和窗口加速器，并且嵌入表中存在这些快捷键的精确副本。

##  <a name="_core_string_table_additions_for_server_applications"></a>服务器应用程序的字符串表添加

在服务器应用程序中只需要添加一个字符串表，即表示 OLE 初始化失败的字符串。 例如，以下是应用程序向导生成的字符串表项：

|ID|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|OLE 初始化失败。 请确保 OLE 库的版本正确。|

##  <a name="_core_mini.2d.server_additions"></a>添加袖珍

与上面列出的用于完整服务器的 miniservers 一样，添加的内容也同样适用。 由于袖珍无法在独立模式下运行，因此它的主菜单要小得多。 应用程序向导创建的主菜单只有一个 "文件" 菜单，其中只包含 "退出" 和 "关于" 项。 适用于 miniservers 的嵌入和就地菜单和加速器与完全服务器的相同。

## <a name="see-also"></a>另请参阅

[菜单和资源 (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[菜单和资源：菜单合并](../mfc/menus-and-resources-menu-merging.md)
