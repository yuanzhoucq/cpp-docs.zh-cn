---
title: "MFC 数据库应用程序中的文件菜单 | Microsoft Docs"
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
  - "“文件”菜单"
  - "数据库应用程序 [C++]，“文件”菜单命令"
ms.assetid: 92dafb75-c1b3-4860-80a0-87a83bfc36f2
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# MFC 数据库应用程序中的文件菜单
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果在创建 MFC 数据库应用程序，不使用序列化，您应如何解释在"文件"菜单中打开，请关闭、保存和另存为命令？  在没有此问题时样式指南，这是个一些建议：  
  
-   完全消除"文件"菜单中打开命令。  
  
-   介绍打开为“命令打开”数据库并显示用户应用程序识别的数据源的列表。  
  
-   介绍打开，打开“命令，而配置文件”。保留已打开的一个序列化的文件，但是，文件使用包含用户存储“配置文件”的信息，例如用户首选项的序列化文档，包括用户的登录 ID \(可选\) 不包括密码和数据源及其新工作了。  
  
 MFC 应用程序向导创建应用程序支持无文档相关的"文件"菜单命令。  选择在 **数据库支持** 页中的 **不提供文件支持的数据库视图 \(V\)** 选项。  
  
 若要解释"文件"菜单命令。特定方法，您必须重写一个或多个命令处理程序，主 `CWinApp`的派生类。  例如，如果完全重写实现 \( `ID_FILE_OPEN` \) 命令的 `OnFileOpen` 指“打开的数据库：”  
  
-   因为您将完全替换命令框架的默认实现，则不要调用 `OnFileOpen`的基类版本。  
  
-   使用处理程序演示对话框列表数据源。  通过调用 `CDatabase::OpenEx` 或 `CDatabase::Open` 以显示这样对话框使用参数 **NULL**。  这就打开显示在用户计算机的所有可用数据源的 ODBC 对话框。  
  
-   由于数据库应用程序通常不保存整个文档，您可能希望移除、保存和另存为实现，除非使用的序列化文档存储信息。  否则，您可能会实现一保存命令，例如，提交“事务”。参见 [技术说明 22](../mfc/tn022-standard-commands-implementation.md) 有关重写这些命令的更多信息。  
  
## 请参阅  
 [序列化：序列化与数据库输入\/输出的对比](../mfc/serialization-serialization-vs-database-input-output.md)