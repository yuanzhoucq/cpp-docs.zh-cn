---
title: "MFC ODBC 使用者向导 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.class.mfc.consumer.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC ODBC 使用者向导"
  - "向导 [MFC]"
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
caps.latest.revision: 7
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ODBC 使用者向导
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在此处插入“搜索结果”摘要。  
  
 该向导设置 ODBC 记录集类和访问指定的数据源所需的数据绑定。  
  
## UIElement 列表  
 **数据源**  
 **“数据源”**按钮使您可以使用指定的 ODBC 驱动程序设置指定的数据源。  有关数据源文件 \(DSN\) 的更多信息，请参见 ODBC SDK 中的[文件数据源](https://msdn.microsoft.com/en-us/library/ms715401.aspx)。  **“选择数据源”**对话框有两个选项卡：  
  
-   **“文件数据源”**选项卡：“查找范围”框指定从中选择要用作数据源的文件的目录。  默认为 \\Program Files\\Common Files\\ODBC\\Data Sources。  现有文件数据源（.dsn 文件）显示在主列表框中。  可以事先使用 [ODBC 数据源管理器](https://msdn.microsoft.com/en-us/library/ms714024.aspx)上的**“文件 DSN”**选项卡设置数据源，或者使用此对话框创建新的数据源。  
  
     若要从此对话框创建新的文件数据源，请单击“新建”\(`New`\) 指定 DSN 名称；“创建新数据源”对话框出现。  在“创建新数据源”对话框中，选择合适的驱动程序并单击“下一步”\(`Next`\)；单击“浏览”，并选择要用作数据源的文件名（必须选择“所有文件”查看非 DSN 文件，如 .xls 文件）；单击“下一步”\(`Next`\)，然后单击“完成”。（如果选择了非 DSN 文件，将获得驱动程序特定的对话框，如“ODBC Microsoft Excel 安装”，它将文件转换为 DSN）。  
  
    > [!NOTE]
    >  也可以事先使用 ODBC 数据源管理器创建新的文件数据源。  从**“开始”**菜单中，选择**“设置”**、**“控制面板”**、**“管理工具”**、“数据源 \(ODBC\)”，然后选择“ODBC 数据源管理器”。  
  
     “DSN 名称”框允许指定文件数据源的名称。  必须确保 DSN 名称以适当的文件扩展名结尾，如 Excel 文件的 .xls 或 Access 文件的 .mdb。  
  
     有关 DSN 的更多信息，请参见 ODBC SDK 中的[文件数据源](https://msdn.microsoft.com/en-us/library/ms715401.aspx)。  
  
-   **“计算机数据源”**选项卡：此选项卡列出系统数据源和用户数据源。  用户数据源特定于此计算机上的一个用户。  系统数据源可以被此计算机上或系统级服务上的所有用户使用。  请参见 ODBC SDK 中的[计算机数据源](https://msdn.microsoft.com/en-us/library/ms710952.aspx)。  
  
 有关 ODBC 数据源的更多信息，请参见 ODBC SDK 中的[数据源](https://msdn.microsoft.com/en-us/library/ms711688.aspx)。  
  
 单击**“确定”**完成操作。  出现“选择数据库对象”对话框。  从此对话框中选择使用者将使用的表或视图。  注意单击项时按住 Control 键可以选择多个视图和表。  
  
 **类**  
 使用者类的名称，默认情况下基于选定的文件或计算机数据源的名称。  
  
 **.h 文件**  
 使用者类头文件的名称，默认情况下基于选定的文件或计算机数据源的名称。  
  
 **.cpp 文件**  
 使用者类实现文件的名称，默认情况下基于选定的文件或计算机数据源的名称。  
  
 **类型**  
 指定记录集是动态集（默认）还是快照。  
  
-   **“动态集”**：指定记录集为动态集。  动态集是查询的结果，为查询数据库的数据提供索引视图。  动态集仅缓存原始数据的整数索引，因此比快照提供更好的性能。  索引直接指向作为查询结果找到的每个记录并指示记录是否被移除。  还可访问查询记录中的更新信息。  这是默认设置。  
  
-   **“快照”**：指定记录集为快照。  快照是查询的结果，并且是某一时间点数据库的概况。  作为查询结果找到的所有记录都被缓存，所以不会看到对原始记录所做的任何更改。  
  
 **绑定所有列**  
 指定是否绑定选定表中的所有列。  如果选中此框（默认），则绑定所有列；如果不选择此框，则不绑定任何列，必须在记录集类中手动绑定它们。  
  
## 请参阅  
 [MFC ODBC 使用](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)