---
title: "菜单和资源： 容器添加 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDP_OLE_INIT_FAILED
- IDP_FAILED_TO_CREATE
- VK_ESCAPE
dev_langs: C++
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
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 654efeaacd08e0d2c8c51cee012fd58dcbf071ab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="menus-and-resources-container-additions"></a>菜单和资源：容器添加
此文章介绍了需要的菜单和可视化编辑的容器应用程序中的其他资源进行的更改。  
  
 需要在容器应用程序中，两种类型的更改： 修改现有资源以支持 OLE 可视化编辑和添加新的资源用于在就地激活。 如果你使用应用程序向导创建容器应用程序，将为你完成这些步骤，但它们可能需要一些自定义项。  
  
 如果不使用应用程序向导，你可能想要查看 OCLIENT。RC，OCLIENT 示例应用程序，以查看如何实施这些更改的资源脚本。 请参阅 MFC OLE 示例[OCLIENT](../visual-cpp-samples.md)。  
  
 本文中涵盖的主题包括：  
  
-   [菜单添加容器](#_core_container_menu_additions)  
  
-   [添加快捷键对应表](#_core_container_application_accelerator_table_additions)  
  
-   [添加字符串表](#_core_string_table_additions_for_container_applications)  
  
##  <a name="_core_container_menu_additions"></a>菜单添加容器  
 必须将以下项添加到编辑菜单：  
  
|项|目标|  
|----------|-------------|  
|**插入新对象**|将打开 OLE 插入对象对话框中要插入到文档中的链接或嵌入项目。|  
|**粘贴链接**|将项链接到剪贴板上粘贴到文档中。|  
|**OLE 谓词**|调用选定的项的主谓词。 此菜单项发生更改以反映主谓词的选定项的文本。|  
|**Links**|将打开 OLE 编辑链接对话框中，若要更改现有链接的项。|  
  
 在本文中列出的更改，除了源文件必须包括 AFXOLECL。RC，即 Microsoft 基础类库实现所必需的。 插入新对象是唯一的必需的菜单添加。 可以添加其他项，但此处所列是最常见。  
  
 如果你想要支持包含的项的就地激活，必须为容器应用程序中创建一个新的菜单。 此菜单包含相同的文件菜单和窗口弹出菜单时文件处于打开状态，但它具有两个分隔符置于它们之间使用。 这些分隔条用于指示服务器 （组件） 项 （应用程序） 放置其菜单时就地激活的位置。 此菜单合并的方法的详细信息，请参阅[菜单和资源： 菜单合并](../mfc/menus-and-resources-menu-merging.md)。  
  
##  <a name="_core_container_application_accelerator_table_additions"></a>添加容器应用程序快捷键对应表  
 容器应用程序的快捷键对应表资源的小改动如果，则必须支持就地激活。 第一次更改允许用户按 esc 键 (ESC) 取消就地编辑模式。 将以下条目添加到主快捷键对应表中：  
  
|Id|键|类型|  
|--------|---------|----------|  
|**ID_CANCEL_EDIT_CNTR**|VK_ESCAPE|**VIRTKEY**|  
  
 第二项更改是创建新的快捷键对应表对应于为就地激活创建新的菜单资源。 此表具有除文件和窗口菜单项**VK_ESCAPE**上文条目中。 下面的示例是在就地激活 MFC 示例中创建的快捷键对应表[容器](../visual-cpp-samples.md):  
  
|Id|键|类型|  
|--------|---------|----------|  
|`ID_FILE_NEW`|Ctrl+N|**VIRTKEY**|  
|`ID_FILE_OPEN`|Ctrl+O|**VIRTKEY**|  
|**ID_FILE_SAVE**|Ctrl+S|**VIRTKEY**|  
|**ID_FILE_PRINT**|Ctrl+P|**VIRTKEY**|  
|**ID_NEXT_PANE**|VK_F6|**VIRTKEY**|  
|**ID_PREV_PANE**|SHIFT + VK_F6|**VIRTKEY**|  
|**ID_CANCEL_EDIT_CNTR**|VK_ESCAPE|**VIRTKEY**|  
  
##  <a name="_core_string_table_additions_for_container_applications"></a>容器应用程序的添加的字符串表  
 更改到容器应用程序的字符串表中的大多数对应中所述的额外的菜单项[容器菜单添加](#_core_container_menu_additions)。 提供显示每个菜单项时，状态栏中显示的文本。 例如，下面是应用程序向导生成的字符串表条目：  
  
|Id|String|  
|--------|------------|  
|**IDP_OLE_INIT_FAILED**|OLE 初始化失败。 请确保 OLE 库的正确版本。|  
|**IDP_FAILED_TO_CREATE**|无法创建对象。 请确保在系统注册表中，输入对象。|  
  
## <a name="see-also"></a>请参阅  
 [菜单和资源 (OLE)](../mfc/menus-and-resources-ole.md)   
 [菜单和资源：服务器添加](../mfc/menus-and-resources-server-additions.md)

