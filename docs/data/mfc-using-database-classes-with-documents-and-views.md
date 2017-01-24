---
title: "MFC：结合文档和视图使用数据库类 | Microsoft Docs"
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
  - "CDaoRecordView 类, 在数据库应用程序中使用"
  - "CDaoRecordView 类, 在数据库窗体中使用"
  - "CRecordView 类, 在数据库窗体中使用"
  - "DAO [C++], 数据库应用程序中的窗体"
  - "DAO 记录集 [C++]"
  - "DAO 记录集 [C++], 文档和视图"
  - "数据库应用程序 [C++], 窗体"
  - "数据库类 [C++], MFC"
  - "文档/视图体系结构 [C++], 在数据库中"
  - "文档 [C++], 数据库应用程序"
  - "窗体 [C++], 数据库应用程序"
  - "ODBC [C++], 窗体"
  - "ODBC 记录集 [C++], 文档和视图"
  - "记录视图 [C++], 基于窗体的应用程序"
  - "记录集 [C++], 文档和视图"
  - "视图 [C++], 数据库应用程序"
ms.assetid: 83979974-fc63-46ac-b162-e8403a572e2c
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC：结合文档和视图使用数据库类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

结合或不结合文档\/视图结构都可以使用 MFC 数据库类 DAO 或 ODBC。  本主题重点介绍结合文档和视图使用数据库类。  本文解释：  
  
-   使用 `CRecordView` 或 `CDaoRecordView` 对象作为文档主视图[编写基于窗体的应用程序的方法](#_core_writing_a_form.2d.based_application)。  
  
-   [在文档和视图中使用记录集对象的方式](#_core_using_recordsets_in_documents_and_views)。  
  
-   [其他考虑事项](#_core_other_factors)。  
  
 有关其他信息，请参见 [MFC：不结合文档和视图使用数据库类](../data/mfc-using-database-classes-without-documents-and-views.md)。  
  
##  <a name="_core_writing_a_form.2d.based_application"></a> 编写基于窗体的应用程序  
 很多数据访问应用程序都是基于窗体。  用户界面是一个包含控件的窗体，用户可在其中检查、输入或编辑数据。  使用 `CRecordView` 或 `CDaoRecordView` 类可使应用程序基于窗体。  在运行“MFC 应用程序向导”，并在**“数据库支持”**页中选择 **ODBC** 客户类型时，项目将 `CRecordView` 用于视图类。  由于向导不再支持 DAO，因此如需使用 `CDaoRecordView`，必须手动编写代码。  
  
 在基于窗体的应用程序中，每个记录视图对象都存储一个指向 `CRecordset` 或 `CDaoRecordset` 对象的指针。  框架的记录字段交换 \(RFX\) 机制在记录集和数据源之间交换数据。  对话框数据交换 \(DDX\) 机制在记录集对象的字段数据成员和窗体上的控件之间交换数据。  `CRecordView` 或 `CDaoRecordView` 也提供默认命令处理程序函数，用于在窗体上从一个记录定位到另一个记录。  
  
 有关使用应用程序向导创建基于窗体的应用程序的信息，请参见[创建基于窗体的 MFC 应用程序](../mfc/reference/creating-a-forms-based-mfc-application.md)和[数据库支持，MFC 应用程序向导](../mfc/reference/database-support-mfc-application-wizard.md)。  
  
 有关窗体的全面讨论，请参见[记录视图](../data/record-views-mfc-data-access.md)。  
  
##  <a name="_core_using_recordsets_in_documents_and_views"></a> 在文档和视图中使用记录集  
 许多简单的基于窗体的应用程序不需要文档。  如果应用程序比较复杂，可能希望使用文档作为数据库代理，存储连接到数据源的 `CDatabase` 或 `CDaoDatabase` 对象。  基于窗体的应用程序通常存储指向视图中记录集对象的指针。  其他类型的数据库应用程序存储文档中的记录集和 `CDatabase` 或 `CDaoDatabase` 对象。  以下是在数据库应用程序中使用文档的一些可能情况：  
  
-   如果要访问本地上下文中的记录集，请在本地根据需要在文档或视图的成员函数中创建 `CRecordset` 或 `CDaoRecordset` 对象。  
  
     在函数中将记录集对象声明为局部变量。  向构造函数传递 **NULL**，使框架创建并打开一个临时 `CDatabase` 或 `CDaoDatabase` 对象。  或者，向 `CDatabase` 或 `CDaoDatabase` 对象传递一个指针。  在函数内使用记录集，并让其在该函数退出时自动销毁。  
  
     当向记录集构造函数传递 **NULL** 时，框架使用记录集的 `GetDefaultConnect` 成员函数返回的信息来创建 `CDatabase` 或 `CDaoDatabase` 对象并打开它。  向导实现 `GetDefaultConnect`。  
  
-   在文档生存期间访问记录集时，在文档中嵌入一个或多个 `CRecordset` 或 `CDaoRecordset` 对象。  
  
     当初始化文档或需要时构造记录集对象。  如果记录集存在，则编写一个函数，返回指向该记录集的指针；否则，建立并打开新的记录集。  根据需要关闭、删除或重新创建记录集，或者调用其 **Requery** 成员函数以刷新记录。  
  
-   在文档生存期间访问数据源时，在文档中嵌入 `CDatabase` 或 `CDaoDatabase` 对象，或在其中存储一个指向 `CDatabase` 或 `CDaoDatabase` 对象的指针。  
  
     `CDatabase` 或 `CDaoDatabase` 对象管理到数据源的连接。  对象在文档构造期间自动构造，用户在初始化该文档时调用其 **Open** 成员函数。  在文档成员函数中构造记录集对象时，向该文档的 `CDatabase` 或 `CDaoDatabase` 对象传递一个指针。  这样就将每个记录集和其数据源关联一起。  文档关闭时，数据库对象通常被销毁。  记录集对象在退出函数范围时通常被销毁。  
  
##  <a name="_core_other_factors"></a> 其他因素  
 因为基于窗体的应用程序通常不需要框架的文档序列化机制，所以用户可能希望移除、禁用或替换“文件”菜单中的“新建”\(`New`\) 和“打开”命令。  请参见文章：[序列化：序列化与数据库输入\/输出的对比](../mfc/serialization-serialization-vs-database-input-output.md)。  
  
 用户也许还希望利用框架支持的众多用户界面可能性。  例如，您可以在一个拆分窗口中使用多个 `CRecordView` 或 `CDaoRecordView` 对象、在不同的多文档界面 \(MDI\) 子窗口中打开多个记录集等等。  
  
 用户可能希望实现打印视图中的所有内容，无论是使用 `CRecordView` 或 `CDaoRecordView` 实现的窗体还是其他内容。  作为 `CFormView` 派生类，`CRecordView` 和 `CDaoRecordView` 都不支持打印，但用户可以重写 `OnPrint` 成员函数使其支持打印。  有关更多信息，请参见类 [CFormView](../mfc/reference/cformview-class.md)。  
  
 用户也许根本不想使用文档和窗体。  如果这样，请参见 [MFC：不结合文档和视图使用数据库类](../data/mfc-using-database-classes-without-documents-and-views.md)。  
  
## 请参阅  
 [MFC 数据库类（ODBC 和 DAO）](../data/mfc-database-classes-odbc-and-dao.md)