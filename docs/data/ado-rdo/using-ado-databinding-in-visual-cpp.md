---
title: "在 Visual C++ 中使用 ADO 数据绑定 | Microsoft Docs"
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
  - "ADO [C++], 数据绑定"
  - "绑定控件 [C++], ADO"
  - "绑定控件 [C++], RDO"
  - "数据绑定 [C++], ADO"
  - "数据绑定 [C++], RDO"
ms.assetid: ad193919-3437-41ee-b41c-9d353f6274e5
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在 Visual C++ 中使用 ADO 数据绑定
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 Visual C\+\+ 中使用 ADO 数据绑定需要下列步骤：  
  
-   添加 ADO 数据控件。  
  
-   指向数据源。  
  
-   指定记录源（SQL 查询或数据检索语言）。  
  
-   添加 ADO 数据绑定控件。  
  
-   将数据绑定控件连接到 ADO 数据控件。  
  
-   选择要绑定到 ADO 数据控件记录源的字段。  
  
### 在 Visual C\+\+ 中使用 ADO 数据绑定  
  
1.  使用“MFC 应用程序向导”创建 MFC 对话框应用程序或 MFC Formview 应用程序。  
  
2.  将 Microsoft ADO 数据控件添加到对话框；请参见[将控件插入 Visual C\+\+ 应用程序](../../data/ado-rdo/inserting-the-control-into-a-visual-cpp-application.md)。  
  
3.  将 ADO 数据控件指向 OLE DB 数据源。  
  
    1.  右击 ADO 数据控件，再单击**“属性”**。  
  
    2.  在“控件”选项卡上，单击“使用连接字符串”。  可以使用提供的提供程序也可以删除它。  
  
    3.  单击**“生成”**。  如果从“使用连接字符串”中删除了提供程序，现在可以定义一个。  定义提供程序后，再次访问 ADO 数据控件的属性，然后再次选择**“生成”**继续。  
  
         如果在选择**“生成”**之前在“使用连接字符串”中定义了提供程序，现在可以定义数据链接属性。  这将显示“DataLink 向导”。  
  
    4.  如有必要更改“提供程序”，并为提供程序定义适当的“位置”和**“数据源”**值。  例如，如果使用的是 SQL Server 提供程序，则“位置”指定数据库服务器，而**“数据源”**指定数据库。  如果使用的是 ODBC 提供程序，则**“数据源”**对应于 ODBC DSN。  
  
    5.  如果数据源需要，单击“身份验证”选项卡并设置“用户名”和**“密码”**的值。  
  
    6.  单击**“连接”**选项卡，再单击“测试连接”测试数据源。  滚动到“结果”窗口的最后，查看是否通过了测试。  如果测试失败，检查数据源的配置。  常见错误包括无效的密码以及“位置”和**“数据源”**字段的值不正确。  
  
    7.  退出“DataLink 向导”，返回到 ADO 数据控件的属性表。  
  
4.  在 `RecordSource` 选项卡中，将查询输入到“命令文本 \(SQL\)”中。  数据绑定控件可绑定到此查询的结果。  查询通常为 SQL。  但是，某些 OLE DB 提供程序不使用 SQL。  
  
5.  设置所需的任何其他 ADO 数据控件属性，然后关闭 ADO 数据控件的属性表。  
  
6.  添加数据绑定控件。  例如，添加 DataGrid 控件，它不同于 RDO DBGrid 控件。  
  
7.  设置 DataGrid 的属性。  
  
    1.  右击 DataGrid，再单击**“属性”**。  
  
    2.  单击**“所有”**选项卡，然后将 **DataSource** 属性设置为 ADO 数据控件。  单击“数据源”下拉列表，找到 ADO 数据控件的 ID。  默认的 ID 名称为 IDC\_ADODC1。  
  
8.  若要以测试模式运行，请按 Ctrl\+T。  将能够在数据中滚动。  按 Esc 键或关闭对话框以结束测试模式。  
  
 如果编译和运行程序，同样能够在数据中滚动。  
  
## 请参阅  
 [ADO 数据绑定](../../data/ado-rdo/ado-databinding.md)   
 [在 Visual C\+\+ 中使用 ActiveX 控件进行数据绑定](../../data/ado-rdo/databinding-with-activex-controls-in-visual-cpp.md)