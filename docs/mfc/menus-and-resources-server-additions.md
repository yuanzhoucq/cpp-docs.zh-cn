---
title: 菜单和资源： 服务器添加 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- IDP_OLE_INIT_FAILED
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 86b941820b439afc8b914142b412995df30f109c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351346"
---
# <a name="menus-and-resources-server-additions"></a>菜单和资源：服务器添加
此文章介绍了需要的菜单和可视化编辑服务器 （组件） 应用程序中的其他资源进行的更改。 服务器应用程序需要多个添加到菜单结构和其他资源，因为它可以启动在三种模式之一： 独立、 嵌入，或就地。 中所述[菜单和资源 (OLE)](../mfc/menus-and-resources-ole.md)文章，有最多四个集的菜单。 所有四个用于 MDI 完全服务器应用程序，而只有三用于 miniserver。 应用程序向导将创建菜单布局所需的服务器所需的类型。 自定义一些可能有必要。  
  
 如果不使用应用程序向导，你可能想要查看 HIERSVR。RC，MFC 示例应用程序的资源脚本[HIERSVR](../visual-cpp-samples.md)以查看如何实施这些更改。  
  
 本文中涵盖的主题包括：  
  
-   [服务器菜单添加](#_core_server_menu_additions)  
  
-   [添加快捷键对应表](#_core_server_application_accelerator_table_additions)  
  
-   [添加字符串表](../mfc/menus-and-resources-container-additions.md)  
  
-   [添加袖珍服务器](#_core_mini.2d.server_additions)  
  
##  <a name="_core_server_menu_additions"></a> 服务器菜单添加  
 服务器 （组件） 应用程序必须具有添加以支持 OLE 可视化编辑的菜单资源。 在独立模式下运行应用程序时使用的菜单无需更改，但生成应用程序前，必须添加两个新的菜单资源： 一种用于支持就地激活和一种用于支持服务器完全打开。 完整和袖珍服务器应用程序使用使用这两个菜单资源。  
  
-   若要支持就地激活，必须创建非常类似于在独立模式下运行时使用的菜单资源的菜单资源。 此菜单中的区别是缺少的文件和窗口的项 （和处理应用程序和不是数据的任何其他菜单项）。 容器应用程序将提供这些菜单项。 有关详细信息和此菜单合并的技术的示例，请参阅文章[菜单和资源： 菜单合并](../mfc/menus-and-resources-menu-merging.md)。  
  
-   若要支持完全打开激活，必须创建菜单资源使用的菜单资源几乎完全相同时在独立模式下运行。 与此菜单资源的唯一修改是重述某些项以反映在嵌入复合文档中的项上的服务器运行的事实。  
  
 除了本文中列出的更改，需要包括 AFXOLESV 资源文件。RC，即 Microsoft 基础类库实现所必需的。 此文件是在 MFC\Include 子目录中。  
  
##  <a name="_core_server_application_accelerator_table_additions"></a> 添加服务器应用程序快捷键对应表  
 必须将两个新的快捷键对应表资源添加到服务器应用程序;它们直接对应于前面所述的新菜单资源。 就地激活服务器应用程序时，将使用第一个快捷键对应表。 它包含视图的快捷键对应表中的所有条目除了那些绑定到的文件和窗口菜单。  
  
 第二个表是几乎视图的快捷键对应表的一个精确副本。 任何差异并行中所述完全打开菜单中所做的更改[服务器菜单添加](#_core_server_menu_additions)。  
  
 有关这些快捷键对应表更改的示例，比较**IDR_HIERSVRTYPE_SRVR_IP**和**IDR_HIERSVRTYPE_SRVR_EMB**快捷键对应表与**IDR_MAINFRAME**在 HIERSVR。RC 文件包含在 MFC OLE 示例[HIERSVR](../visual-cpp-samples.md)。 文件和窗口加速器是就地表中缺少且它们之间的精确副本以在嵌入式表。  
  
##  <a name="_core_string_table_additions_for_server_applications"></a> 针对服务器应用程序添加的字符串表  
 只有一个字符串表加法指的是需要在服务器应用程序-以表示 OLE 初始化失败的字符串。 例如，下面是应用程序向导生成的字符串表条目：  
  
|Id|String|  
|--------|------------|  
|**IDP_OLE_INIT_FAILED**|OLE 初始化失败。 请确保 OLE 库的正确版本。|  
  
##  <a name="_core_mini.2d.server_additions"></a> 添加袖珍服务器  
 相同的添加件同样适用于袖珍上面所列的完整服务器。 由于无法在独立模式下运行 miniserver，其主菜单是小得多。 应用程序向导创建的主菜单还拥有仅文件菜单上，仅包含的项退出和有关。 嵌入和就地菜单和快捷键的袖珍都与完整服务器相同。  
  
## <a name="see-also"></a>请参阅  
 [菜单和资源 (OLE)](../mfc/menus-and-resources-ole.md)   
 [菜单和资源：菜单合并](../mfc/menus-and-resources-menu-merging.md)

