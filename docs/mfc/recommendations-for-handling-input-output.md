---
title: 关于处理输入-输出的建议 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- I/O [MFC], about I/O
- file-based I/O options
- I/O [MFC]
- I/O [MFC], options
- I/O [MFC], file-based options
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e08ea95c9cfe4bd67c0904cc22e6db19dcfb52e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355677"
---
# <a name="recommendations-for-handling-inputoutput"></a>关于处理输入/输出的建议
您使用基于文件的 I/O 取决于如何响应以下决策树中的问题：  
  
 **你的应用程序中的主数据位于磁盘文件**  
  
-   是，主数据位于磁盘的文件：  
  
     **应用程序不整个文件读到上打开文件的内存，写入整个文件返回到磁盘上保存文件**  
  
    -   是： 这是默认 MFC 文档大小写。 使用**CDocument**序列化。  
  
    -   否： 这通常是基于事务的更新的文件的大小写。 在更新每个事务的基础上的文件并不需要**CDocument**序列化。  
  
-   否，主数据不驻留在磁盘中：  
  
     **数据位于 ODBC 数据源**  
  
    -   是，数据驻留在 ODBC 数据源：  
  
         使用 MFC 的数据库支持。 这种情况下的标准 MFC 实现包括`CDatabase`对象，如下文中讨论[MFC： 结合文档和视图使用数据库类](../data/mfc-using-database-classes-with-documents-and-views.md)。 应用程序还可能会读取和写入辅助文件-应用程序向导"的数据库视图和文件支持"选项的目的。 在这种情况下，你将序列化用于辅助文件。  
  
    -   否，数据不驻留在 ODBC 数据源。  
  
         这种情况下的示例： 数据驻留在非 ODBC DBMS;通过某种其他机制，例如 OLE 或 DDE 在读取数据。  
  
         在这种情况下，不会使用序列化，并且你的应用程序不会打开和保存菜单项。 你可能仍想要使用**CDocument**作为主页基础，就像一个 MFC ODBC 应用程序使用文档存储`CRecordset`对象。 但不会使用框架的默认文件打开/保存文档序列化。  
  
 若要支持打开、 保存，并将其作为命令保存在文件菜单上，该框架提供文档序列化。 序列化读取和写入数据，包括对象派生自类`CObject`，到永久存储，通常将一个磁盘文件。 序列化是易于使用并提供您的许多需求，但它可能在很多数据访问应用程序中不适当。 数据访问应用程序通常会更新每个事务的基础上的数据。 他们会更新受事务而不是读取和写入的整个数据文件一次的记录。  
  
 有关序列化的信息，请参阅[序列化](../mfc/serialization-in-mfc.md)。  
  
## <a name="see-also"></a>请参阅  
 [序列化：序列化与数据库输入/输出](../mfc/serialization-serialization-vs-database-input-output.md)
