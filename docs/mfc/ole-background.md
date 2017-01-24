---
title: "OLE 后台 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE, 关于 OLE"
ms.assetid: 5f654eb5-66b1-40c9-9215-bb85356a67f8
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE 后台
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

OLE 是允许用户创建和编辑用于包含项或“对象”文档创建的各种应用程序的机制。  
  
> [!NOTE]
>  OLE 最初是对象链接与嵌入的首字母缩写词。  但是，它现在指向 OLE。  OLE 的部分不相关链接和嵌入现在是 Active 技术的一部分。  
  
 OLE 文档，以前称为组合文档数据无缝集成，或组件的各种类型。  声音剪辑、电子表格和位图是在 OLE 文档中的组件的典型示例。  支持在应用程序的" OLE 允许用户使用 OLE 文档，而不用担心不同应用程序之间交换；OLE 执行您交换。  
  
 使用容器创建复合应用程序文档和服务器应用或组件应用程序文档创建容器中的项。  已编写的任何应用程序可以是容器，和\/或服务器。  
  
 OLE 将许多不同的概念所有若要实现无缝的交互目标应用程序之间的。  这些区域包括：  
  
 链接和嵌入  
 链接和嵌入是存储在其他应用程序创建的两个方法创建一项在 OLE 文档中。  关于二者之间的差异的常规信息，请参见 [OLE 背景：链接和嵌入](../mfc/ole-background-linking-and-embedding.md)文章。  有关详细信息，请参见和文章 [容器](../mfc/containers.md) [服务器](../mfc/servers.md)。  
  
 就地激活 \(可视化编辑对象\)  
 激活在文档中的嵌入项容器调用就地激活或可视化编辑。  容器应用程序的接口更改合并创建嵌入项组件应用程序的功能。  链接的项永远不激活就地，因为项的实际数据在一个单独的文件中，移出包含链接的应用程序的上下文之外。  有关就地激活的更多信息，请参见知识库文章 [激活](../mfc/activation-cpp.md)。  
  
> [!NOTE]
>  链接嵌入和就地激活和提供主要功能 OLE 可视化编辑。  
  
 自动化  
 自动化使一驱动应用程序其他应用程序。  驱动的应用程序称为的自动化客户端，并且，驱动的应用程序称为的自动化或自动化服务器组件。  有关自动化的更多信息，请参见和文章 [自动化客户](../mfc/automation-clients.md) [自动化服务器](../mfc/automation-servers.md)。  
  
> [!NOTE]
>  在 OLE 自动化和 Active 技术上下文工作。  可以自动基于 COM 的对象。  
  
 复合文件  
 复合文件提供简化结构化存储 OLE 应用程序成分文档标准的文件格式。  在复合文件中，存储目录有许多功能，然后流具有文件的许多功能。  该技术也称为结构化存储。  有关复合文件的更多信息，请参见知识库文章 [容器：复合文件](../mfc/containers-compound-files.md)。  
  
 统一传输数据  
 统一数据传输 \(UDT\) 是允许数据发送和接收的标准方式的一组接口，无论选择的实际方法传输数据。  UDT 由窗体中拖放数据传输的基础。  UDT 现在作为基础现有 Windows 数据传输，例如剪贴板和的动态数据交换 \(DDE\) \(DDE\)。  UDT 有关的更多信息，请参见知识库文章 [数据对象与数据源 \(OLE\)](../mfc/data-objects-and-data-sources-ole.md)。  
  
 拖放  
 拖放属于一种易用，技术直接处理在应用程序之间传输数据，包括在应用程序内的 Windows 中，甚至在应用程序中作为单一窗口中。  将要传输的数据选择并拖到所需目标。  拖放基于统一数据传输。  有关拖放的更多信息，请参见知识库文章 [拖放](../mfc/drag-and-drop-ole.md)。  
  
 组件对象模型  
 当 OLE 对象彼此通信时，组件对象模型 \(COM\) \(COM\) 提供使用的基础结构。  MFC OLE 类简化程序员的 COM。  因为基础 COM 对象，COM 和 OLE Active 技术是 Active 技术的一部分。  有关 COM 的更多信息，请参见 [活动模板库 \(ATL\) \(ATL\)](../atl/active-template-library-atl-concepts.md) 主题。  
  
 一些更重要的 OLE 主题。下列文章包括：  
  
-   [OLE 后台：链接和嵌入](../mfc/ole-background-linking-and-embedding.md)  
  
-   [OLE 后台：容器和服务器](../mfc/ole-background-containers-and-servers.md)  
  
-   [OLE 后台：实现策略](../mfc/ole-background-implementation-strategies.md)  
  
-   [OLE 后台：MFC 实现](../mfc/ole-background-mfc-implementation.md)  
  
 对于上述文章找不到的通用 OLE 信息，OLE 的搜索 MSDN。  
  
## 请参阅  
 [OLE](../mfc/ole-in-mfc.md)