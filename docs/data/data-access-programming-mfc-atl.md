---
title: "数据访问编程 (MFC/ATL) | Microsoft Docs"
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
  - "数据 [C++], 数据访问技术"
  - "数据访问 [C++], 数据库的类库"
  - "数据库 [C++], MFC"
  - "MFC [C++], 数据访问应用程序"
  - "OLE DB [C++], 数据访问技术"
ms.assetid: def97b2c-b5a6-445f-afeb-308050fd4852
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# 数据访问编程 (MFC/ATL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 提供了好几种处理数据库的方法。  首选方法就是使用其中一个类库，例如活动模板库 \(ATL\) 或 Microsoft 基础类库 \(MFC\),这种方法可以简化数据库 API 的处理。  
  
> [!NOTE]
>  本主题包括可用于在 Visual C\+\+ 中进行数据库编程的旧技术。  有关使用 Visual C\+\+ 和 SQL Server 2005 进行数据访问编程的信息，请参阅 [数据访问](../dotnet/data-access-using-adonet-cpp-cli.md)、[在 Visual Studio 中访问数据](../Topic/Accessing%20data%20in%20Visual%20Studio.md) 和 [Creating SQL Server 2005 Objects In Managed Code](http://msdn.microsoft.com/zh-cn/5358a825-e19b-49aa-8214-674ce5fed1da)。  
  
 库类支持以下数据访问类型：  
  
-   ATL 提供 OLE DB 模板和数据库属性。  
  
-   MFC 提供开放式数据库连接 \(ODBC\)和 ODBC 驱动程序。  
  
 这些库提供简化数据库处理的抽象，包括 C\+\+ 的速度、功能和灵活性。  它们可以利用库的应用程序框架整合数据访问工作。  
  
 或者，你可以直接从 COM、ODBC 或 DAO 软件开发工具包 \(SDK\) 调用数据库 API 函数。  有关直接用 COM、DAO 或 ODBC API 函数编程的信息，请参阅 COM SDK、DAO SDK 或 ODBC SDK。  
  
 如果需要访问数据，无论该数据存储在哪个窗体，都可以使用 ATL OLE DB。  当你没有使用 Microsoft Jet \(.mdb\) 数据库并且想要使用 ODBC API 完成数据源独立性时，使用 MFC ODBC 类。  当希望使用 Microsoft Jet \(.mdb\) 数据库或外部数据库（例如 ODBC 数据源）时，请使用 MFC DAO 类。  
  
> [!NOTE]
>  Microsoft 建议使用 OLE DB 或 ODBC 处理新项目。  只有在维护现有应用程序时才能使用 DAO。  
  
 除了编写独立数据库应用程序外，通常还可以使用在其他程序类型中作为有效便利存储和检索媒体的数据库。  
  
|了解更多信息|请参阅|  
|------------|---------|  
|**选择数据库技术**||  
|ODBC 与  DAO|[使用 DAO 还是 ODBC？](../data/should-i-use-dao-or-odbc-q.md)|  
|使用 Microsoft 知识库查找由产品支持工程人员编写的数据库主题方面的其他文章。|[Microsoft 知识库](../data/where-can-i-find-microsoft-knowledge-base-articles-on-database-topics-q.md)|  
|**ATL 数据库支持 \(OLE DB\)**||  
|OLE DB 编程（概念性主题）|[OLE DB 编程概述](../data/oledb/ole-db-programming-overview.md)|  
|使用 OLE DB 使用者模板（概念性主题）|[OLE DB 使用者模板](../data/oledb/ole-db-consumer-templates-cpp.md)|  
|OLE DB 使用者特性|[OLE DB 使用者特性](../windows/ole-db-consumer-attributes.md)|  
|使用 OLE DB 提供程序模板（概念性主题）|[OLE DB 提供程序模板](../data/oledb/ole-db-provider-templates-cpp.md)|  
|将 OLE DB 使用者添加到 MFC 项目|[创建 OLE DB 使用者](../data/oledb/creating-an-ole-db-consumer.md)|  
|**MFC 数据库支持（ODBC 和 DAO）**||  
|DAO 和 ODBC 的概念|[什么是 DAO 和 ODBC？](../data/what-are-dao-and-odbc-q.md)|  
|MFC 数据库类的使用时间|[何时使用数据库类？](../data/when-should-i-use-the-database-classes-q.md)|  
|了解 MFC 数据库编程模型|[MFC 数据库编程模型是什么？](../data/what-is-the-mfc-database-programming-model-q.md)。|  
|在 MFC DAO 类和 MFC ODBC 类之间选择|[我是否应使用 DAO 或 ODBC？](../data/should-i-use-dao-or-odbc-q.md).|  
|你可以使用 DAO 和 ODBC 访问的数据源|[使用 DAO 和 ODBC 可以访问哪些数据源？](../data/what-data-sources-can-i-access-with-dao-and-odbc-q.md)|  
|开放式数据库连接 \(ODBC\)|[ODBC 和 MFC](../data/odbc/odbc-and-mfc.md)|  
|是否可以在使用类时直接调用 DAO 或 ODBC API|[是否可以直接调用 DAO 或 ODBC？](../data/can-i-call-dao-or-odbc-directly-q.md)|  
|提供了哪些 ODBC 驱动程序|[ODBC 驱动程序列表](../data/odbc/odbc-driver-list.md)|  
|数据库类如何处理 MFC 文档\/视图结构|[MFC：结合文档和视图使用数据库类](../data/mfc-using-database-classes-with-documents-and-views.md)|  
|安装 MFC 数据库支持；默认情况下，Visual C\+\+ 中安装了哪些 ODBC 驱动程序；安装了哪些 ODBC 和 DAO SDK 组件|[安装 MFC 数据库支持](../data/installing-mfc-database-support.md)|  
|**数据绑定控件（ADO 和 RDO）**||  
|编写可以使用数据绑定控件的程序|[数据绑定控件（ADO 和 RDO）](../data/ado-rdo/data-bound-controls-ado-and-rdo.md)|  
|使用 ActiveX 控件绑定的数据|[MFC ActiveX 控件：在 ActiveX 控件中使用数据绑定](../mfc/mfc-activex-controls-using-data-binding-in-an-activex-control.md)|  
|发行 ActiveX 控件|[MFC ActiveX 控件：发行 ActiveX 控件](../mfc/mfc-activex-controls-distributing-activex-controls.md)|  
  
## 请参阅  
 [数据访问](../Topic/Data%20Access%20in%20Visual%20C++.md)