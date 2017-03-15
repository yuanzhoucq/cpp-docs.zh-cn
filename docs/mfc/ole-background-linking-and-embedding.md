---
title: "OLE 后台：链接和嵌入 | Microsoft Docs"
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
  - "嵌入对象 [C++]"
  - "项类型"
  - "项类型, 已定义"
  - "链接项 (OLE) [C++]"
  - "OLE 嵌入项"
  - "OLE 项, 类型"
  - "OLE, 链接项"
ms.assetid: 11107711-eb96-4099-8f5c-7910bb3ecb75
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# OLE 后台：链接和嵌入
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通过将容器应用程序的粘贴命令可以创建嵌入的组件或嵌入项。  嵌入项的源数据存储包含 OLE 文档作为它的一部分。  这样一来，字处理器文档的文件包含文本并可以包含位图、图、公式，或者任何其他类型的数据。  
  
 OLE 提供了另一种方法合并其他应用程序中数据：创建链接的组件或链接的项或链接。  创建链接项的步骤类似于创建嵌入项，只不过您使用粘贴链接命令而不是粘贴命令。  与嵌入的组件不同，通常在单独的文件中，链接的组件存储路径到原始数据。  
  
 例如，如果在字处理器文档中工作，并创建一个链接项到某些电子表格单元格，链接项的数据存储在原始文档存储电子表格。  字处理器文档仅包含指定项的位置信息，也就是说，它包含一链接到原始电子表格文档。  当双击单元格时，电子表格应用程序启动，并且原始电子表格文档从存储它的位置加载。  
  
 每个 OLE 项，不论嵌入或链接，存在与创建基于该数据库的应用程序关联的类型。  例如，Microsoft Paintbrush 项是项的一种类型，因此，Microsoft Excel 项是其他类型。  然而，某些应用程序可以创建不止一种项目类型。  例如，Microsoft Excel 可以创建工作表项、图表项和 macrosheet 项。  通过使用类标识符或 **CLSID**，这些项中的每一个都可以由系统唯一标识。  
  
## 请参阅  
 [OLE 后台](../mfc/ole-background.md)   
 [OLE 后台：容器和服务器](../mfc/ole-background-containers-and-servers.md)   
 [容器：客户端项](../mfc/containers-client-items.md)   
 [服务器：服务器项](../mfc/servers-server-items.md)