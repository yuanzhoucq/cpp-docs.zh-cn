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
ms.openlocfilehash: a082a75ef0292e190e597f29be0cdc0bd0b497ef
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626230"
---
# <a name="menus-and-resources-container-additions"></a>菜单和资源：容器添加

本文说明了需要对可视编辑容器应用程序中的菜单和其他资源进行的更改。

在容器应用程序中，需要进行两种类型的更改：对现有资源进行修改以支持 OLE 可视化编辑，并添加了用于就地激活的新资源。 如果使用应用程序向导创建容器应用程序，则将为你执行这些步骤，但可能需要进行一些自定义。

如果不使用应用程序向导，可能需要查看 OCLIENT。RC，OCLIENT 示例应用程序的资源脚本，用于查看如何实现这些更改。 请参阅 MFC OLE 示例[OCLIENT](../overview/visual-cpp-samples.md)。

本文中涵盖的主题包括：

- [容器菜单添加项](#_core_container_menu_additions)

- [快捷键对应表添加项](#_core_container_application_accelerator_table_additions)

- [字符串表添加](#_core_string_table_additions_for_container_applications)

## <a name="container-menu-additions"></a><a name="_core_container_menu_additions"></a>容器菜单添加项

必须将以下项目添加到 "编辑" 菜单：

|项目|目的|
|----------|-------------|
|**插入新对象**|打开 OLE "插入对象" 对话框以在文档中插入链接或嵌入的项。|
|**粘贴链接**|将剪贴板上的项的链接粘贴到文档中。|
|**OLE 谓词**|调用选定项的主谓词。 此菜单项的文本将更改以反映所选项目的主谓词。|
|**链接**|打开 OLE "编辑链接" 对话框以更改现有链接项。|

除了本文中列出的更改之外，源文件还必须包含 AFXOLECL。RC，这是 Microsoft 基础类库实现所必需的。 插入新对象是唯一需要的菜单。 可以添加其他项，但此处列出的内容是最常见的。

如果要支持就地激活包含项，则必须为容器应用程序创建一个新菜单。 此菜单包含在打开文件时使用的相同的 "文件" 菜单和 "窗口" 弹出菜单，但在它们之间放置了两个分隔符。 这些分隔符用于指示服务器（组件）项目（应用程序）在就地激活时应放置其菜单的位置。 有关此菜单合并技术的详细信息，请参阅菜单[和资源：菜单合并](menus-and-resources-menu-merging.md)。

## <a name="container-application-accelerator-table-additions"></a><a name="_core_container_application_accelerator_table_additions"></a>容器应用程序加速器表添加

如果你支持就地激活，则需要对容器应用程序的快捷键对应表资源进行少量更改。 第一次更改后，用户可以按 esc 键来取消就地编辑模式。 将以下条目添加到主快捷键对应表中：

|ID|键|类型|
|--------|---------|----------|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

第二项更改是创建与为就地激活创建的新菜单资源相对应的新快捷键对应表。 除了上述 VK_ESCAPE 条目外，此表还包含 "文件" 和 "窗口" 菜单的条目。 下面的示例是为 MFC 示例[容器](../overview/visual-cpp-samples.md)中的就地激活创建的快捷键对应表：

|ID|键|类型|
|--------|---------|----------|
|ID_FILE_NEW|Ctrl+N|**VIRTKEY**|
|ID_FILE_OPEN|Ctrl+O|**VIRTKEY**|
|ID_FILE_SAVE|Ctrl+S|**VIRTKEY**|
|ID_FILE_PRINT|Ctrl+P|**VIRTKEY**|
|ID_NEXT_PANE|VK_F6|**VIRTKEY**|
|ID_PREV_PANE|SHIFT + VK_F6|**VIRTKEY**|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

## <a name="string-table-additions-for-container-applications"></a><a name="_core_string_table_additions_for_container_applications"></a>容器应用程序的字符串表添加

容器应用程序的字符串表的大部分更改都对应于[容器菜单添加](#_core_container_menu_additions)项中提到的其他菜单项。 它们提供显示每个菜单项时状态栏中显示的文本。 例如，以下是应用程序向导生成的字符串表项：

|ID|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|OLE 初始化失败。 请确保 OLE 库的版本正确。|
|IDP_FAILED_TO_CREATE|未能创建对象。 请确保在系统注册表中输入了该对象。|

## <a name="see-also"></a>另请参阅

[菜单和资源（OLE）](menus-and-resources-ole.md)<br/>
[菜单和资源：服务器添加](menus-and-resources-server-additions.md)
