---
title: "ODBC 基础 | Microsoft Docs"
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
  - "ODBC 组件"
  - "ODBC 组件, 必需的组件"
  - "ODBC 游标库 [ODBC], ODBC 组件"
  - "ODBC, 关于 ODBC"
  - "ODBC, 组件"
ms.assetid: ec529702-0fb2-4754-b8de-d1efa8eca18f
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ODBC 基础
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主题提供了开放式数据库连接 \(ODBC\) 的基本知识：  
  
-   [ODBC 如何与数据库类一起工作](../../data/odbc/odbc-and-the-database-classes.md)  
  
-   [ODBC 驱动程序如何与动态集一起工作](../../data/odbc/odbc-driver-requirements-for-dynasets.md)  
  
-   [哪些 ODBC 组件需要与应用程序一起再发行](../../data/odbc/redistributing-odbc-components-to-your-customers.md)  
  
 您还需要阅读相关主题 [ODBC：ODBC 游标库](../../data/odbc/odbc-the-odbc-cursor-library.md)。  
  
> [!NOTE]
>  通过 MFC ODBC 类（如本主题所述）或通过 MFC 数据访问对象 \(DAO\) 类，都可以访问 ODBC 数据源。  
  
> [!NOTE]
>  MFC ODBC 类支持 Unicode 和多线程操作。  有关多线程操作支持的更多信息，请参见 [ODBC 类和线程](../../data/odbc/odbc-classes-and-threads.md)。  
  
 ODBC 是一个调用级接口，它使得应用程序得以访问任何具有 ODBC 驱动程序的数据库中的数据。  使用 ODBC 可以创建具有访问任何数据库（最终用户具有该数据库的 ODBC 驱动程序）的权限的数据库应用程序。  ODBC 提供了使您的应用程序独立于源数据库管理系统 \(DBMS\) 的 API。  
  
 ODBC 是 Microsoft Windows 开放式服务体系结构 \(WOSA\) 中的数据库部分。WOSA 是一种接口，允许基于 Windows 的桌面应用程序连接到多种计算环境，而不用为每个平台重写应用程序。  
  
 下面是 ODBC 的组件：  
  
-   ODBC API  
  
     函数调用库、错误代码集和用于访问 DBMS 上数据的标准的 [SQL](../../data/odbc/sql.md) 语法。  
  
-   ODBC 驱动程序管理器  
  
     代表应用程序加载 ODBC 数据库驱动程序的动态链接库 \(Odbc32.dll\)。  该 DLL 对您的应用程序是透明的。  
  
-   ODBC 数据库驱动程序  
  
     处理特定 DBMS 的 ODBC 函数调用的一个或多个 DLL。  有关所提供的驱动程序的列表，请参见 [ODBC 驱动程序列表](../../data/odbc/odbc-driver-list.md)。  
  
-   [ODBC 游标库](../../data/odbc/odbc-the-odbc-cursor-library.md)  
  
     驻留在 ODBC 驱动程序管理器和该驱动程序之间并处理数据滚动的动态链接库 \(Odbccr32.dll\)。  
  
-   [ODBC 管理器](../../data/odbc/odbc-administrator.md)  
  
     用于配置 DBMS 使之可用作应用程序的数据源的工具。  
  
 应用程序通过专为 DBMS 编写的 ODBC 驱动程序而不是直接使用 DBMS 的工作方式独立于 DBMS。  驱动程序将这些调用转换成 DBMS 可使用的命令，因而简化了开发人员的工作，使得广泛的数据源都可以使用它。  
  
 数据库类支持具有 ODBC 驱动程序的任何数据源。  例如，这可能包括关系数据库、索引顺序访问方法 \(ISAM\) 数据库、Microsoft Excel 电子表格或文本文件。  ODBC 驱动程序管理到数据源的连接，SQL 用于从数据库中选择记录。  
  
 有关 Visual C\+\+ 此版本中包括的 ODBC 驱动程序列表以及有关获取其他驱动程序的信息，请参见 [ODBC 驱动程序列表](../../data/odbc/odbc-driver-list.md)。  
  
## 请参阅  
 [开放式数据库连接 \(ODBC\)](../../data/odbc/open-database-connectivity-odbc.md)