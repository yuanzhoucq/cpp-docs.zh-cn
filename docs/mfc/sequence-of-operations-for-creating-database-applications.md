---
title: "用于创建数据库应用程序的操作顺序 | Microsoft Docs"
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
  - "应用程序 [MFC], 数据库"
  - "数据库应用程序 [C++]"
  - "数据库应用程序 [C++], 创建"
  - "MFC [C++], 数据库应用程序"
ms.assetid: 9371da59-8536-43cd-8314-706ad320e2ec
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 用于创建数据库应用程序的操作顺序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表显示效果和框架的文本效果在数据库应用程序。  
  
> [!NOTE]
>  从 Visual C\+\+ .NET 起，Visual C\+\+ 环境和向导不再支持 DAO（不过提供了 DAO 类，仍可供您使用）。  Microsoft 建议对新项目使用 ODBC或 MFC。  DAO 只应用于维护现有的应用程序。  
  
### 创建数据库应用程序  
  
|任务|You do|框架|  
|--------|------------|--------|  
|决定是否使用 MFC ODBC 或 DAO 类。|对新MFC项目使用ODBC 。  使用 DAO 仅维护现有的应用程序。  [使用 DAO 还是 ODBC？](../data/should-i-use-dao-or-odbc-q.md) 有关一般信息，请参见知识库文章 [数据访问编程](../data/data-access-programming-mfc-atl.md)。|框架支持数据库访问的类。|  
|创建与数据库选项的主干应用程序。|运行神奇应用程序。  选择上数据库支持页的选项。  如果选择创建记录视图的选项，还要指定：<br /><br /> -   数据源和表名称或名称<br />-   查询名称或名称。|MFC 应用程序向导创建文件并指定所需中。  根据您指定的选项，文件可以包括记录集类都可以过度。|  
|设计数据库窗体或窗体。|使用 Visual C\+\+ 对话框编辑器编辑的记录将控件放置在对话框模板资源视图类。|MFC 应用程序向导为您创建空的对话框模板资源可以填充。|  
|创建过多记录视图和记录集类需要。|使用"类视图"创建类和对话框编辑器设计视图。|"类视图"创建新类的附加文件。|  
|创建记录集对象根据需要在代码。  每个记录使用记录集操作…|记录集基于用向导的 [CRecordset](../mfc/reference/crecordset-class.md) 派生的类。|ODBC 使用记录字段交换 \(RFX\) 到在数据库和记录集的字段数据成员之间交换数据。  如果使用记录视图，在记录集和控件之间的对话框数据交换 \(DDX\) 交换数据。记录视图。|  
|…或者创建在代码中显式打开 [CDatabase](../mfc/reference/cdatabase-class.md) 要的每个数据库中。|使记录集对象的数据库对象。|数据库对象提供一个接口为数据源。|  
|请参见记录集：动态绑定数据列 \(ODBC\)。|在 ODBC，请将代码添加到类派生的记录集管理绑定。  请参见文章[记录集：动态绑定数据列 \(ODBC\)](../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)。||  
  
## 请参阅  
 [基于框架生成](../mfc/building-on-the-framework.md)   
 [用于生成 MFC 应用程序的操作顺序](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [用于创建 OLE 应用程序的操作顺序](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [用于创建 ActiveX 控件的操作顺序](../mfc/sequence-of-operations-for-creating-activex-controls.md)