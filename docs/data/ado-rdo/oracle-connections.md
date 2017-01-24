---
title: "Oracle 连接 | Microsoft Docs"
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
  - "连接 [C++], 数据库"
  - "数据库连接 [C++], Oracle"
  - "数据库 [C++], 连接"
  - "Oracle [C++], 创建连接"
  - "Oracle 数据库 [C++]"
  - "Oracle 数据库 [C++], 连接"
ms.assetid: d317e763-44aa-47c9-abe8-261d513d894f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Oracle 连接
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在配置 Oracle ODBC DSN 或 OLE DB 连接时，必须安装 Oracle 的 SQL\*Net 客户端组件。  SQL\*Net 是 Oracle 网络传输层。  大部分 Oracle ODBC 驱动程序，包括 Microsoft 的驱动程序和 Microsoft OLE DB Oracle 提供程序映射，直接调用此 SQL\*Net 层。  
  
 配置 SQL\*Net 后，记住 SQL\*Net 连接字符串。  一般情况下，它由 Oracle 数据库服务器名称的说明符和网络协议类型（例如，TCP\/IP、命名管道）组成。  SQL\*Net 连接字符串通常映射到别名。  这种情况下，只需要记住别名。  有关如何配置 SQL\*Net 的信息，请联系 Oracle DBA，参考 SQL\*Net 文档，或者参考 Oracle ODBC 驱动程序帮助文件中的连接字符串示例。  
  
## 请参阅  
 [创建数据库连接](../../data/ado-rdo/creating-database-connections.md)