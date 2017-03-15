---
title: "ODBC：配置 ODBC 数据源 | Microsoft Docs"
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
  - "配置 ODBC 数据源"
  - "ODBC 连接, 配置"
  - "ODBC 数据源, 配置"
ms.assetid: 1cd03e6a-8d59-4eca-a8c6-1010582d5e67
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# ODBC：配置 ODBC 数据源
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要在已开发的应用程序中使用[数据源](../../data/odbc/data-source-odbc.md)，必须使用 ODBC 管理器配置您的应用程序。  ODBC 管理器可跟踪可用的数据源及其在 Windows 注册表中的连接信息。  使用 ODBC 管理器可以在**“数据源”**对话框中添加、修改和删除数据源以及添加和删除 ODBC 驱动程序。  
  
> [!NOTE]
>  当您将 MFC 数据访问对象 \(DAO\) 类用于 ODBC 访问和使用 MFC ODBC 类时，该信息适用。  
  
 ODBC 管理器自动随 Microsoft 基础类 \(MFC\) 库数据库支持一起安装。  有关 ODBC 管理器程序的更多信息，请参见 [ODBC 管理器](../../data/odbc/odbc-administrator.md)和“ODBC API 参考”联机帮助系统。  
  
 有关如何为 MFC 数据库应用程序编写 ODBC 安装和管理程序的信息，请参见[技术说明 48](../../mfc/tn048-writing-odbc-setup-and-administration-programs.md)。  
  
## 请参阅  
 [ODBC 基础](../../data/odbc/odbc-basics.md)   
 [ODBC：直接调用 ODBC API 函数](../../data/odbc/odbc-calling-odbc-api-functions-directly.md)