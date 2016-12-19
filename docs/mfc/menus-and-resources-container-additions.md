---
title: "菜单和资源：容器添加 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDP_OLE_INIT_FAILED"
  - "IDP_FAILED_TO_CREATE"
  - "VK_ESCAPE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "快捷键表 [C++], 容器应用程序"
  - "应用程序加速器表 [C++]"
  - "CONTAIN 教程"
  - "IDP_FAILED_TO_CREATE 宏"
  - "IDP_OLE_INIT_FAILED 宏"
  - "链接菜单项"
  - "OLE 容器, 菜单和资源"
  - "可视化编辑, 应用程序菜单和资源"
  - "VK_ESCAPE 键"
ms.assetid: 425448be-8ca0-412e-909a-a3a9ce845288
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 菜单和资源：容器添加
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明需要对菜单和在可视化编辑容器应用程序中其他资源的更改 。  
  
 在容器应用程序中，需要更改两种类型：修改现有资源为支持 OLE 可视化编辑和修改用于就地激活的新资源附加物。  如果使用应用程序向导创建容器应用程序，这些步骤用于将为您完成，但它们可能需要一些自定义。  
  
 如果不使用应用程序向导，您可能希望查看 OCLIENT.RC，示例应用程序 OCLIENT 的资源脚本，查看将如何实现这些更改。  参见 MFC OLE 示例 [OCLIENT](../top/visual-cpp-samples.md)。  
  
 本文涵盖的主题包括：  
  
-   [容器添加菜单](#_core_container_menu_additions)  
  
-   [快捷键表添置](#_core_container_application_accelerator_table_additions)  
  
-   [字符串表添置](#_core_string_table_additions_for_container_applications)  
  
##  <a name="_core_container_menu_additions"></a> 容器添加菜单  
 您必须为"编辑"菜单添加以下项：  
  
|项|用途|  
|-------|--------|  
|**插入新对象**|打开 OLE 插入对象对话框来在文档中插入链接或嵌入项。|  
|**粘贴链接**|将指向剪贴板上的项粘贴到文档。|  
|**OLE Verb — OLE 谓词**|调用选定项的主要谓词。  此菜单项文本更改反映选定项的主要谓词。|  
|**链接**|打开 OLE 编辑链接对话框更改现有链接的项。|  
  
 除了本文中列出的更改外，源文件需要包括 AFXOLECL.RC，它需要 Microsoft 基础类库的实现。  插入新对象是仅有的需要的菜单添加。  其他项可以添加，但在这里，列出最常用的某些。  
  
 如果想要所包含的项支持就地激活，必须创建容器应用程序的新菜单。  此菜单包括相同文件菜单和打开文件时使用的窗口弹出菜单，但是，它有两个分隔符放置在它们之间。  这些分隔符用于指示服务器 \(组件\) 项 \(应用程序\) 在当激活就地时应放置其菜单。  有关该菜单合并技术的更多信息，请参见 [菜单和资源：菜单合并](../mfc/menus-and-resources-menu-merging.md)。  
  
##  <a name="_core_container_application_accelerator_table_additions"></a> 容器应用程序快捷键对应表添置  
 如果支持就地激活，容器应用程序的快捷键表资源的小改变是必须的。  第一更改是允许用户按 ESCAPE 键 \(Esc 键\) 取消就地编辑模式。  将下面的项添加到母快捷键表：  
  
|ID|键|类型|  
|--------|-------|--------|  
|**ID\_CANCEL\_EDIT\_CNTR**|VK\_ESCAPE|**VIRTKEY**|  
  
 另一个更改是创建对应于为就地激活创建的新菜单资源的新快捷键对应表。  该表具有除上述 **VK\_ESCAPE** 输入以外的文件和 Windows 菜单的输入。  下面的示例为在 MFC 示例 [CONTAINER](../top/visual-cpp-samples.md) 中为就地激活创建的快捷键对应表的示例：  
  
|ID|键|类型|  
|--------|-------|--------|  
|`ID_FILE_NEW`|Ctrl\+N|**VIRTKEY**|  
|`ID_FILE_OPEN`|Ctrl\+O|**VIRTKEY**|  
|**ID\_FILE\_SAVE**|Ctrl\+S|**VIRTKEY**|  
|**ID\_FILE\_PRINT**|Ctrl\+P|**VIRTKEY**|  
|**ID\_NEXT\_PANE**|VK\_F6|**VIRTKEY**|  
|**ID\_PREV\_PANE**|SHIFT\+VK\_F6|**VIRTKEY**|  
|**ID\_CANCEL\_EDIT\_CNTR**|VK\_ESCAPE|**VIRTKEY**|  
  
##  <a name="_core_string_table_additions_for_container_applications"></a> 容器应用程序的字符串添加表  
 大多数到容器应用程序的字符串表的更改对应于 [容器添加菜单](#_core_container_menu_additions) 提到的附加菜单项。  当每个菜单项显示时，它们提供可在状态栏显示的文本。  例如，这是应用程序向导生成的字符串表项：  
  
|ID|String|  
|--------|------------|  
|**IDP\_OLE\_INIT\_FAILED**|OLE 初始化失败。  请确保 OLE 库是正确的版本。|  
|**IDP\_FAILED\_TO\_CREATE**|创建对象失败。  确保对象已输入系统注册表。|  
  
## 请参阅  
 [菜单和资源 \(OLE\)](../mfc/menus-and-resources-ole.md)   
 [菜单和资源：服务器添加](../mfc/menus-and-resources-server-additions.md)