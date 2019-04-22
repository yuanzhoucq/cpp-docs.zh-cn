---
title: 菜单和资源：添加容器
ms.date: 11/04/2016
f1_keywords:
- IDP_OLE_INIT_FAILED
- IDP_FAILED_TO_CREATE
- VK_ESCAPE
helpviewer_keywords:
- application accelerator table [MFC]
- VK_ESCAPE key [MFC]
- IDP_FAILED_TO_CREATE macro [MFC]
- visual editing, application menus and resources
- OLE containers [MFC], menus and resources
- accelerator tables [MFC], container applications
- IDP_OLE_INIT_FAILED macro [MFC]
- CONTAIN tutorial [MFC]
- Links menu item [MFC]
ms.assetid: 425448be-8ca0-412e-909a-a3a9ce845288
ms.openlocfilehash: b1a74fef743592d3d052226dac926fc7ddc58578
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58770338"
---
# <a name="menus-and-resources-container-additions"></a>菜单和资源：添加容器

本文介绍了对菜单和可视化编辑容器应用程序中的其他资源进行更改。

需要在容器应用程序中的更改的两种类型： 对现有的资源以支持 OLE 可视化编辑和添加新的资源用于就地激活的修改。 如果你使用应用程序向导创建的容器应用程序，将完成这些步骤，但它们可能需要一些自定义。

如果不使用应用程序向导，您可能想要看一看 OCLIENT。RC 中，资源脚本中的 OCLIENT 示例应用程序，若要了解如何实现这些更改。 请参阅 MFC OLE 示例[OCLIENT](../overview/visual-cpp-samples.md)。

在本文中涵盖的主题包括：

- [菜单添加容器](#_core_container_menu_additions)

- [添加快捷键对应表](#_core_container_application_accelerator_table_additions)

- [添加字符串表](#_core_string_table_additions_for_container_applications)

##  <a name="_core_container_menu_additions"></a> 菜单添加容器

必须将以下各项添加到编辑菜单：

|项|用途|
|----------|-------------|
|**插入新对象**|将打开 OLE 插入对象对话框中要插入到文档的链接或嵌入的项。|
|**粘贴链接**|将剪贴板上的项的链接粘贴到文档中。|
|**OLE Verb**|调用选定的项的主谓词。 此菜单项发生更改以反映所选的项的主谓词的文本。|
|**Links**|将打开 OLE 编辑链接对话框中，若要更改现有链接的项。|

除了本文中列出的更改，源文件必须包括 AFXOLECL。RC 中，这是 Microsoft 基础类库实现所必需的。 插入新对象是唯一的所需的菜单添加。 可以添加其他项，但此处列出的内容是最常见的。

如果你想要支持就地激活的包含的项，必须为容器应用程序中创建一个新的菜单。 此菜单包含相同的文件菜单和窗口弹出菜单时文件处于打开状态，但它具有两个分隔符置于它们之间的使用。 这些分隔条用于指示服务器 （组件） 项 （应用程序） 应在其中放置时就地激活，其菜单。 此菜单合并技术的详细信息，请参阅[菜单和资源：菜单合并](../mfc/menus-and-resources-menu-merging.md)。

##  <a name="_core_container_application_accelerator_table_additions"></a> 添加容器应用程序快捷键对应表

如果支持就地激活必要容器应用程序的快捷键对应表资源的小改动。 第一次更改允许用户通过按 esc 键 (ESC)，以取消就地编辑模式。 将以下条目添加到主快捷键对应表：

|Id|键|类型|
|--------|---------|----------|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

第二项更改是创建新的快捷键对应表，对应于创建就地激活的新菜单资源。 此表具有除了上述 VK_ESCAPE 条目的文件和窗口菜单项。 下面的示例是就地激活 MFC 示例中为创建快捷键对应表[容器](../overview/visual-cpp-samples.md):

|Id|键|类型|
|--------|---------|----------|
|ID_FILE_NEW|Ctrl+N|**VIRTKEY**|
|ID_FILE_OPEN|Ctrl+O|**VIRTKEY**|
|ID_FILE_SAVE|Ctrl+S|**VIRTKEY**|
|ID_FILE_PRINT|Ctrl+P|**VIRTKEY**|
|ID_NEXT_PANE|VK_F6|**VIRTKEY**|
|ID_PREV_PANE|SHIFT+VK_F6|**VIRTKEY**|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

##  <a name="_core_string_table_additions_for_container_applications"></a> 添加容器应用程序的字符串表

大部分对容器应用程序的字符串表的更改中所述的额外的菜单项对应[容器菜单添加](#_core_container_menu_additions)。 它们提供时每个菜单项显示在状态栏中显示的文本。 例如，下面是应用程序向导生成的字符串表条目：

|Id|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|OLE 初始化失败。 请确保 OLE 库的正确版本。|
|IDP_FAILED_TO_CREATE|无法创建对象。 请确保在系统注册表中输入了该对象。|

## <a name="see-also"></a>请参阅

[菜单和资源 (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[菜单和资源：添加服务器](../mfc/menus-and-resources-server-additions.md)
