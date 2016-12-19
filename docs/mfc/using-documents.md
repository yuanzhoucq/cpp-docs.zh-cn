---
title: "使用文档 | Microsoft Docs"
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
  - "数据 [MFC], 文档"
  - "数据 [MFC], 读取"
  - "文档/视图体系结构 [C++], 文档"
  - "文档 [C++]"
  - "文档 [C++], C++ 应用程序"
  - "文件 [C++]"
  - "文件 [C++], 写入"
  - "打印 [MFC], 文档"
  - "读取数据 [C++], 文档和视图"
  - "视图 [C++], C++ 应用程序"
  - "写入文件 [C++]"
ms.assetid: f390d6d8-d0e1-4497-9b6a-435f7ce0776c
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用文档
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文档和视图：  
  
-   包含，管理，并显示特定的 [数据](../mfc/managing-data-with-document-data-variables.md)。  
  
-   操作为数据提供一个接口中的 [文档数据变量](../mfc/managing-data-with-document-data-variables.md)。  
  
-   运行 [文本和读取文件](../mfc/serializing-data-to-and-from-files.md)。  
  
-   运行 [正在打印](../mfc/role-of-the-view-in-printing.md)。  
  
-   [句柄](../mfc/handling-commands-in-the-document.md) 大多数应用程序的命令和消息。  
  
 文档在管理更具体涉及到的数据。  存储数据，通常，文档中类成员变量。  视图使用这些变量访问数据的显示和更新。  文档的默认序列化机制进出文件管理读取和写入数据。  文档也可以处理命令 \(，但 **WM\_COMMAND**以外的不是窗口消息\)。  
  
## 您想进一步了解什么？  
  
-   [派生类从 CDocument 文档](../mfc/deriving-a-document-class-from-cdocument.md)  
  
-   [与文档数据变量的托管数据](../mfc/managing-data-with-document-data-variables.md)  
  
-   [序列化进出文件中的数据](../mfc/serializing-data-to-and-from-files.md)  
  
-   [对于序列化机制](../mfc/bypassing-the-serialization-mechanism.md)  
  
-   [处理文档中的命令](../mfc/handling-commands-in-the-document.md)  
  
-   [OnNewDocument 成员函数](../Topic/CDocument::OnNewDocument.md)  
  
-   [DeleteContents 成员函数](../Topic/CDocument::DeleteContents.md)  
  
## 请参阅  
 [文档\/视图体系结构](../mfc/document-view-architecture.md)