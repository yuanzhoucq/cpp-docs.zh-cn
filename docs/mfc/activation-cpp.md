---
title: "Activation (C++) | Microsoft Docs"
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
  - "激活对象"
  - "激活 [C++]"
  - "激活 [C++], 嵌入的 OLE 项"
  - "文档, OLE"
  - "嵌入对象"
  - "就地激活"
  - "就地激活, 嵌入的和链接的项"
  - "OLE [C++], 激活"
  - "OLE [C++], 编辑"
  - "OLE [C++], 就地激活"
  - "OLE 激活"
  - "OLE 项, 可视化编辑"
  - "OLE 服务器应用程序, 激活"
  - "可视化编辑"
  - "可视化编辑, 激活"
ms.assetid: ed8357d9-e487-4aaa-aa6b-2edc4de25dfa
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Activation (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明激活影响可视编辑 OLE 项。  在用户将此容器文档后面的一个 OLE 项，则可能需要使用。  为此，该用户双击项，激活该项。  激活的最常见的激活编辑。  许多当前 OLE 项，那么，当激活的编辑，在当前框架窗口使菜单和工具栏对属于更改反映创建项的服务器应用的转换。  此行为，即就地激活，允许用户编辑受复合文档中嵌入的所有项，而无需使文档容器的窗口。  
  
 编辑可在单独窗口的嵌入的 OLE 项也是可能的。  则容器或服务器应用不支持就地激活，则会发生。  在这种情况下，那么，当用户双击嵌入的项时，服务器应用在单独窗口启动，并嵌入项显示为自己的文档。  用户编辑此窗口中的项。  完成编辑时，用户关闭并返回到服务器应用容器应用程序。  
  
 或者，用户可以选择打开“编辑”。在 **编辑** 菜单上的 **\<object Open\>**  命令。  这将在单独窗口的对象。  
  
> [!NOTE]
>  编辑可在单独窗口的嵌入项位于生成 OLE 1 的标准行为，并且，某些 OLE 应用程序可能只支持编辑此样式。  
  
 就地激活提升一个文档为中心创建文档的方法。  复合用户可以将文档作为单个实体，工作，还不在应用程序之间进行切换。  但是，仅用于激活就地嵌入项，而为链接的项：在单独的窗口必须编辑它们。  这是因为，为链接的项在不同的位置实际上存储。  也就是说，编辑的链接项。数据的上下文中实际出现的数据存储。  编辑可在单独窗口的链接项的提醒用户数据所属的其他文档。  
  
 MFC 不支持嵌套的就地激活。  如果生成服务器\/容器应用，该服务器\/容器，并在其他容器和激活就地嵌入，它无法激活就地嵌入对象内部。  
  
 发生到嵌入的项，当用户双击其依赖为项定义的谓词。  有关信息，请参见 [激活：谓词](../mfc/activation-verbs.md)。  
  
## 请参阅  
 [OLE](../mfc/ole-in-mfc.md)   
 [容器](../mfc/containers.md)   
 [服务器](../mfc/servers.md)