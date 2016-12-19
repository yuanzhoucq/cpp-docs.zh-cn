---
title: "关于处理输入/输出的建议 | Microsoft Docs"
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
  - "基于文件的 I/O 选项"
  - "I/O [C++]"
  - "I/O [C++], 基于文件的选项"
  - "I/O [C++], 选项"
  - "I/O [MFC], 关于 I/O"
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 关于处理输入/输出的建议
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

不论是否使用基于文件 I\/O 取决于您回答下决策树的问题：  
  
 **在应用程序的主数据驻留在磁盘文件？**  
  
-   是，主数据驻留在磁盘文件：  
  
     **应用程序如果读取整个文件在打开文件的内存并写入整个文件回在保存文件的磁盘？**  
  
    -   为：这是默认情况 MFC 文档。  序列化使用 **CDocument**。  
  
    -   否：这通常与用例基于事务中更新文件。  可更新基于每个事务进行文件，因此不需要序列化。**CDocument**  
  
-   不，主要数据不在磁盘文件：  
  
     **数据驻留在 ODBC 数据源？**  
  
    -   是，数据驻留在 ODBC 数据源：  
  
         使用 MFC 的数据库支持。  此情况的标准 MFC 实现中存储 `CDatabase` 对象的 **CDocument** 对象，如知识库文章 [什么是 MFC 数据库编程模型？](../data/what-is-the-mfc-database-programming-model-q.md)所述。  应用程序可以读取和来编写一个附属文件 \- 应用程序向导数据库视图“的用途和支持文件”选项。  在这种情况下，会为附属文件使用序列化。  
  
    -   不，数据不在 ODBC 数据源。  
  
         此情况的示例：非 DBMS 数据驻留在 ODBC;数据通过其他一些机制读取，如 OLE 或 DDE。  
  
         在这种情况下，不使用序列化，并且，应用程序不会自动打开并且不保存菜单项。  如同 MFC ODBC 应用程序存储文档使用 `CRecordset` 对象，您仍可能想要使用 **CDocument** 作为本垒。  但是，不使用框架的默认打开文件或保存文档序列化。  
  
 要支持开放，在"文件"菜单上，"另存为"命令保存和框架的文档序列化。  序列化读写数据，包括从类派生的对象 `CObject`，为永久性存储，通常磁盘文件。  序列化易于使用并为许多需要服务，但可能不合适的。许多数据访问应用程序。  访问应用程序通常更新基于每个事务基本类型的数据。  他们更新的事务会立即影响的记录而不是读取和写入整个数据文件。  
  
 有关序列化的信息，请参见 [序列化](../mfc/serialization-in-mfc.md)。  
  
## 请参阅  
 [序列化：序列化与数据库输入\/输出的对比](../mfc/serialization-serialization-vs-database-input-output.md)