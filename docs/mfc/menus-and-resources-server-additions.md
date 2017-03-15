---
title: "菜单和资源：服务器添加 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDP_OLE_INIT_FAILED"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "快捷键表 [C++], 服务器应用程序"
  - "IDP_OLE_INIT_FAILED 宏"
  - "OLE 初始化失败"
  - "OLE 服务器应用程序, 菜单和资源"
  - "OLE 可视化编辑服务器"
  - "资源 [MFC], 服务器应用程序"
  - "服务器应用程序, 快捷键表"
  - "服务器应用程序, OLE 菜单和资源"
  - "服务器, 菜单添加"
  - "字符串编辑, 可视化编辑应用程序"
  - "字符串表, 可视化编辑应用程序"
  - "可视化编辑, 应用程序菜单和资源"
ms.assetid: 56ce9e8d-8f41-4db8-8dee-e8b0702d057c
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 菜单和资源：服务器添加
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明需要对菜单和在可视化编辑服务器\(组件\) 应用程序其他资源的更改 。  服务器应用程序要求很多额外的资源到菜单结构以及其他资源，因为它可以以三种模式之一启动：独立，嵌入或到位  正如 [菜单和资源 \(OLE\)](../mfc/menus-and-resources-ole.md) 文章所述，具有四组菜单中最大值。  对于MDI 全服务器应用使用所有这四个，而对于小型服务器只使用三个。  应用程序向导将为您服务器的类型创建需要的菜单布局。  一些自定义项可能是必需的。  
  
 如果不使用应用程序向导，您可能希望查看 HIERSVR.RC，MFC 示例应用程序 [HIERSVR](../top/visual-cpp-samples.md)的资源脚本，查看将如何实现这些更改。  
  
 本文涵盖的主题包括：  
  
-   [服务器菜单添置](#_core_server_menu_additions)  
  
-   [快捷键表添置](#_core_server_application_accelerator_table_additions)  
  
-   [字符串表添置](../mfc/menus-and-resources-container-additions.md)  
  
-   [Miniservert添置](#_core_mini.2d.server_additions)  
  
##  <a name="_core_server_menu_additions"></a> 服务器菜单添置  
 服务器\(组件\) 应用程序必须添加菜单资源以支持 OLE 可视化编辑。  在应用程序处于独立模式运行无需更改时使用菜单，但是，必须在建立应用程序之前添加两个新的菜单资源：一个支持就地激活的和一个支持服务器完全打开。  full\-和 miniserver 应用程序使用全部的菜单资源。  
  
-   若要支持就地激活，必须创建类似于当在独立模式下运行时使用的菜单资源。  此菜单差异在于窗口和文件项 \(及任何其他菜单项处理应用程序，而不是数据\) 丢失。  容器应用程序将提供这些菜单项。  有关此菜单合并的技术的更多信息和实例，请参阅文章 [菜单和资源：菜单合并](../mfc/menus-and-resources-menu-merging.md)。  
  
-   若要支持完全打开激活，必须创建菜单资源基本等效于独立模式使用的运行时使用的菜单资源。  该菜单资源的唯一更改是某些项时重说反映服务器在复合文档嵌入项运行的情况。  
  
 除了列出的更改外本文中，资源文件需要包括 AFXOLESV.RC，需要在 Microsoft 基础类库实现所必需的。  此文件在 MFC \\Include 子目录。  
  
##  <a name="_core_server_application_accelerator_table_additions"></a> 服务器应用程序快捷键对应表添置  
 必须将两个新的快捷键表资源到服务器应用；它们直接对应于前面描述的新菜单资源。  当服务器应用适当激活时，使用第一个快捷键表。  包括在视图中的快捷键对应表中所有输入除这些附加对文件及窗口菜单。  
  
 第二个表都接近视图中的快捷键对应表的准确副本。  进行的任何差异并行更改在 [服务器添加菜单](#_core_server_menu_additions)提到的完全打开菜单上。  
  
 对于这些快捷键表更改的示例中，比较与 **IDR\_MAINFRAME** 的 **IDR\_HIERSVRTYPE\_SRVR\_IP** 和 **IDR\_HIERSVRTYPE\_SRVR\_EMB** 在快捷键表 MFC OLE 示例包括文件的 HIERSVR.RC [HIERSVR](../top/visual-cpp-samples.md)。  文件和窗口快捷键从就地表消失和并将它们复制在嵌入的表中。  
  
##  <a name="_core_string_table_additions_for_server_applications"></a> 服务器应用的字符串表添置  
 在服务器应用只需要一个字符串添加的表 \- 表示的字符串初始化 OLE 失败。  例如，这是应用程序向导生成的字符串表项：  
  
|ID|String|  
|--------|------------|  
|**IDP\_OLE\_INIT\_FAILED**|OLE 初始化失败。  请确保 OLE 库是正确的版本。|  
  
##  <a name="_core_mini.2d.server_additions"></a> Miniservert添置  
 和以上所列的full\-servers添加同样适用于miniservers。  由于 miniserver 在独立模式无法运行，其主菜单更小。  通过应用程序向导创建的主菜单只有文件菜单，只包含项退出和关于项。  嵌入的资源和本地菜单和快捷键 miniservers 的与full\-servers相同。  
  
## 请参阅  
 [菜单和资源 \(OLE\)](../mfc/menus-and-resources-ole.md)   
 [菜单和资源：菜单合并](../mfc/menus-and-resources-menu-merging.md)