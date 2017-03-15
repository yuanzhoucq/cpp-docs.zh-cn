---
title: "剪贴板：使用 OLE 剪贴板机制 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "应用程序 [OLE], 剪贴板"
  - "剪贴板 [C++], OLE 格式"
  - "格式 [C++], OLE 剪贴板"
  - "OLE 剪贴板"
  - "OLE 剪贴板, 格式"
ms.assetid: 229cc610-5bb1-435e-bd20-2c8b9964d1af
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 剪贴板：使用 OLE 剪贴板机制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

OLE 对通过剪贴板传递数据使用标准格式和某些 OLE 特定格式。  
  
 当从应用程序中剪切或复制数据时，存储在剪贴板的数据将在之后的粘贴操作中使用。  此数据有多种格式。  当用户选择从剪贴板上粘贴数据时，应用程序可以选择使用的格式。  应编写应用程序选择提供的大部分信息的格式，除非用户明确要求特定的格式，使用特殊粘贴。  在继续之前，您可能需要阅读[数据对象与数据源 \(OLE\)](../mfc/data-objects-and-data-sources-ole.md) 主题。  描述数据传输如何工作的基本原理以及在应用程序如何实现它们。  
  
 窗口定义通过剪贴板传输数据的许多标准格式。  这些包含文件、文本、位图和其他。  OLE 也定义多种 OLE 特定格式。  对于比这些标准形式给出需要更多详细信息的应用程序中，最好注册它们的自定义格式剪贴板。  使用 Win32 API 函数 [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) 执行此操作。  
  
 例如，Microsoft Excel 电子表格注册自定义格式。  此格式比例如位图携带更多信息。  当此将数据粘贴到应用程序以支持电子表格格式时，如果需要，所有电子表格中的公式和值都将保留并更新。  Microsoft Excel 将数据以格式放入在剪贴板，以便粘贴为 OLE 项。  任何 OLE 文档容器可以粘贴此信息作为嵌入的项。  使用 Microsoft Excel，可更改此嵌入项。  剪贴板还包含在电子表格中选定范围的图像的简单位图。  还可以粘贴到 OLE 文档容器或到位图编辑器，如绘制。  至于位图，然而无法作为电子表格来操作数据。  
  
 若要从剪贴板检索最大消息量，应用程序应在剪贴板上粘贴数据之前检查这些自定义格式。  
  
 例如，启用剪切命令，您可能会编写处理程序类似于以下内容：  
  
 [!CODE [NVC_MFCListView#3](../CodeSnippet/VS_Snippets_Cpp/NVC_MFCListView#3)]  
  
## 您想进一步了解什么？  
  
-   [复制和粘贴数据](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [添加其他格式](../mfc/clipboard-adding-other-formats.md)  
  
-   [使用 Windows 剪贴板](../mfc/clipboard-using-the-windows-clipboard.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
-   [OLE 数据对象与数据源和统一传输数据](../mfc/data-objects-and-data-sources-ole.md)  
  
## 请参阅  
 [剪贴板](../mfc/clipboard.md)