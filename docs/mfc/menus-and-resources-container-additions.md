---
title: 菜单和资源：容器添加
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
ms.openlocfilehash: c8da58316f471f7b7d26e142cc1dd1ccaa6ad8b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364797"
---
# <a name="menus-and-resources-container-additions"></a>菜单和资源：容器添加

本文介绍了需要在可视化编辑容器应用程序中对菜单和其他资源进行更改。

在容器应用程序中，需要进行两种类型的更改：对现有资源进行修改以支持 OLE 可视化编辑和添加用于就地激活的新资源。 如果使用应用程序向导创建容器应用程序，这些步骤将为您完成，但它们可能需要一些自定义。

如果不使用应用程序向导，则可能需要查看 OCLIENT。RC，OCLIENT 示例应用程序的资源脚本，以查看这些更改是如何实现的。 请参阅 MFC OLE 示例[OCLIENT](../overview/visual-cpp-samples.md)。

本文涵盖的主题包括：

- [容器菜单添加](#_core_container_menu_additions)

- [加速器表添加](#_core_container_application_accelerator_table_additions)

- [字符串表添加](#_core_string_table_additions_for_container_applications)

## <a name="container-menu-additions"></a><a name="_core_container_menu_additions"></a>容器菜单添加

您必须将以下项目添加到"编辑"菜单：

|Item|目标|
|----------|-------------|
|**插入新对象**|打开"OLE 插入对象"对话框，将链接或嵌入的项目插入到文档中。|
|**粘贴链接**|将指向剪贴板上项目的链接粘贴到文档中。|
|**OLE 动词**|调用所选项的主谓词。 此菜单项的文本将更改以反映所选项的主谓词。|
|**链接**|打开"OLE 编辑链接"对话框以更改现有链接项目。|

除了本文中列出的更改之外，源文件还必须包含 AFXOLECL。RC，这是 Microsoft 基础类库实现所必需的。 插入新对象是唯一需要添加的菜单。 可以添加其他项目，但此处列出的项目是最常见的。

如果要支持包含项的就地激活，则必须为容器应用程序创建新菜单。 此菜单由相同的文件菜单和窗口弹出菜单组成，当文件打开时使用，但它有两个分隔符放置在它们之间。 这些分隔符用于指示服务器（组件）项（应用程序）在激活时应将其菜单放置的位置。 有关此菜单合并技术的详细信息，请参阅[菜单和资源：菜单合并](../mfc/menus-and-resources-menu-merging.md)。

## <a name="container-application-accelerator-table-additions"></a><a name="_core_container_application_accelerator_table_additions"></a>容器应用程序加速器表添加

如果支持就地激活，则需要对容器应用程序的加速器表资源进行少量更改。 第一个更改允许用户按转义键 （ESC） 取消就地编辑模式。 将以下条目添加到主加速器表：

|ID|密钥|类型|
|--------|---------|----------|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

第二个更改是创建一个新的快捷键表，该表对应于为就地激活而创建的新菜单资源。 除了上面VK_ESCAPE条目外，此表还包含"文件和窗口"菜单的条目。 下面的示例是为 MFC 示例[CONTAINER](../overview/visual-cpp-samples.md)中为就地激活而创建的加速器表：

|ID|密钥|类型|
|--------|---------|----------|
|ID_FILE_NEW|Ctrl+N|**VIRTKEY**|
|ID_FILE_OPEN|Ctrl+O|**VIRTKEY**|
|ID_FILE_SAVE|Ctrl+S|**VIRTKEY**|
|ID_FILE_PRINT|Ctrl+P|**VIRTKEY**|
|ID_NEXT_PANE|VK_F6|**VIRTKEY**|
|ID_PREV_PANE|SHIFT_VK_F6|**VIRTKEY**|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

## <a name="string-table-additions-for-container-applications"></a><a name="_core_string_table_additions_for_container_applications"></a>容器应用程序的字符串表添加

容器应用程序的字符串表的大部分更改都对应于[容器菜单添加](#_core_container_menu_additions)中提及的其他菜单项。 当显示每个菜单项时，它们提供状态栏中显示的文本。 例如，下面是应用程序向导生成的字符串表条目：

|ID|字符串|
|--------|------------|
|IDP_OLE_INIT_FAILED|OLE 初始化失败。 确保 OLE 库是正确的版本。|
|IDP_FAILED_TO_CREATE|无法创建对象。 确保对象是在系统注册表中输入的。|

## <a name="see-also"></a>另请参阅

[菜单和资源 （OLE）](../mfc/menus-and-resources-ole.md)<br/>
[菜单和资源：服务器添加](../mfc/menus-and-resources-server-additions.md)
