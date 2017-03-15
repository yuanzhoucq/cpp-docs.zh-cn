---
title: "MFC：不结合文档和视图使用数据库类 | Microsoft Docs"
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
  - "应用程序向导 [C++], 创建数据库应用程序"
  - "CDaoRecordView 类, 在数据库应用程序中使用"
  - "CRecordView 类, 在数据库应用程序中使用"
  - "DAO [C++], 数据库应用程序中的文件支持"
  - "DAO [C++], 写应用程序"
  - "数据库应用程序 [C++], 应用程序向导选项"
  - "数据库应用程序 [C++], 没有文档"
  - "数据库应用程序 [C++], 没有视图"
  - "数据库类 [C++], MFC"
  - "文档/视图体系结构 [C++], 在数据库中"
  - "文档 [C++], 应用程序"
  - "文件 [C++], MFC"
  - "ODBC [C++], 数据库应用程序中的文件支持"
  - "ODBC 应用程序 [C++]"
  - "ODBC 应用程序 [C++], 没有文档"
  - "ODBC 应用程序 [C++], 没有视图"
  - "用户界面 [C++], 绘图信息"
ms.assetid: 15bf52d4-91cf-4b1d-8b37-87c3ae70123a
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# MFC：不结合文档和视图使用数据库类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

有时用户可能不希望在数据库应用程序中使用框架的文档\/视图结构。  本主题说明：  
  
-   [当不需要使用文档时](#_core_when_you_don.92.t_need_documents)，如文档序列化。  
  
-   [应用程序向导选项](#_core_appwizard_options_for_documents_and_views)，这些选项支持不带序列化和与文档相关的**“文件”**菜单命令（如 **“新建”**、**“打开”**、**“保存”**和**“另存为”**）的应用程序。  
  
-   [如何使用（使用了最少文档的）应用程序](#_core_applications_with_minimal_documents)。  
  
-   [如何构造不包含文档或视图的应用程序](#_core_applications_with_no_document)。  
  
##  <a name="_core_when_you_don.92.t_need_documents"></a> 当不需要文档时  
 有些应用程序对文档有不同的概念。  这些应用程序通常使用**“文件打开”**命令从存储中把一个文件的全部或大部分加载到内存中。  然后它们使用**“保存文件”**或者**“另存为”**命令把更新后的文件一齐写回到存储中。  用户所看到的是一个数据文件。  
  
 但是，有些类别的应用程序不需要文档。  数据库应用程序按照事务来运行。  应用程序从数据库中选择记录，然后将它们提供给用户，通常为一次一条记录。  用户所看到的通常是一条当前记录，该记录可能为内存中唯一的记录。  
  
 如果应用程序不需要用文档来存储数据，可以摒弃框架的部分或全部文档\/视图结构。  摒弃内容的多少取决于用户所喜欢的方法。  您可能：  
  
-   使用最小文档作为存储到数据源的连接的地方，但摒弃常规文档功能，例如序列化。  该方法的用途在于可以获得数据的多种视图并且同步处理所有视图，例如同时更新等。  
  
-   使用用户直接向其中描述的框架窗口，而不是视图。  此时，用户可省略文档并存储框架窗口对象中的所有数据或数据连接。  
  
##  <a name="_core_appwizard_options_for_documents_and_views"></a> 文档和视图的应用程序向导选项  
 MFC 应用程序向导包括下表中列出的多种**“选择数据库支持”**选项。  如若使用 MFC 应用程序向导创建应用程序，所有这些选项都生成带文档和视图的应用程序。  有些选项提供省略不需要的文档功能的文档和视图。  有关详细信息，请参阅[MFC 应用程序向导的数据库支持](../mfc/reference/database-support-mfc-application-wizard.md)。  
  
|选项|视图|Document|  
|--------|--------|--------------|  
|**无**|从 `CView` 派生。|不提供数据库支持。  这是默认选项。<br /><br /> 如果选择[MFC 应用程序向导的应用程序类型](../mfc/reference/application-type-mfc-application-wizard.md)页中的**“文档\/视图结构支持”**选项，可获得完全文档支持，包括序列化以及**“文件”**菜单中的 `New`、**“打开”**、**“保存”**和**“另存为”**命令。  请参见[无文档的应用程序](#_core_applications_with_no_document)。|  
|**仅支持头文件**|从 `CView` 派生。|为应用程序提供基本的数据库支持。<br /><br /> 包括 Afxdb.h。  添加链接库，但不创建任何数据库特定的类。  可在以后创建记录集来检验并更新记录。|  
|**不支持文件的数据库视图**|从 `CRecordView` 派生|提供文档支持但不提供序列化支持。  文档可以存储记录集并且协调多个视图，但不支持序列化或 `New`、**“打开”**、**“保存”**和**“另存为”**命令。  请参见[带最小文档的应用程序](#_core_applications_with_minimal_documents)。  如果包含数据库视图，则必须指定数据源。<br /><br /> 包含数据库头文件、链接库、记录视图和记录集。（仅对在[MFC 应用程序向导的应用程序类型](../mfc/reference/application-type-mfc-application-wizard.md)页中选择了**“文档\/视图结构支持”**选项的应用程序可用。）|  
|**支持文件的数据库视图**|从 `CRecordView` 派生|提供完全文档支持，包括序列化和与文档相关的“文件”菜单命令。  数据库应用程序通常以记录而非文件为基础进行操作，因此不需要序列化。  但是，序列化有一个特殊用处。  请参见[带最小文档的应用程序](#_core_applications_with_minimal_documents)。  如果包含数据库视图，则必须指定数据源。<br /><br /> 包含数据库头文件、链接库、记录视图和记录集。（仅对在[MFC 应用程序向导的应用程序类型](../mfc/reference/application-type-mfc-application-wizard.md)页中选择了**“文档\/视图结构支持”**选项的应用程序可用。）|  
  
 有关序列化的替代方法和序列化的其他用途的讨论，请参见[序列化：序列化与数据库输入\/输出的对比](../mfc/serialization-serialization-vs-database-input-output.md)。  
  
##  <a name="_core_applications_with_minimal_documents"></a> 带最小文档的应用程序  
 MFC 应用程序向导有两个支持基于窗体的数据访问应用程序的选项。  每个选项都创建一个 `CRecordView` 派生类和一个文档。  它们的区别在于文档不包含的功能。  
  
###  <a name="_core_a_document_without_file_support"></a> 不带文件支持的文档  
 不需要文档序列化的用户可选择应用程序向导数据库选项“不支持文件的数据库视图”。  该文档具有下列用途：  
  
-   它是存储 `CRecordset` 对象的很合适的地方。  
  
     该用法和普通文档概念相同：文档存储数据（在本文的情况中指一组记录），视图用于查看文档。  
  
-   如果应用程序提供多视图（例如多记录视图），则文档支持协调视图。  
  
     如果多视图显示相同的数据，则可使用 `CDocument::UpdateAllViews` 成员函数来协调任一视图改变数据时对所有视图的更新。  
  
 通常对基于简单窗体的应用程序使用此选项。  应用程序向导自动支持这些应用程序的便利结构。  
  
###  <a name="_core_a_document_with_file_support"></a> 带文件支持的文档  
 对与文档相关的“文件”菜单命令和文档序列化有其他用途的用户，可选择应用程序向导数据库选项“支持文件的数据库视图”。  对于程序的数据访问部分，用户可用[不带文件支持的文档](#_core_a_document_without_file_support)中描述的方式使用文档。  例如，使用文档的序列化功能读写存储用户首选项或其他有用信息的序列化用户配置文档。  有关更多概念，请参见[序列化：序列化与数据库输入\/输出的对比](../mfc/serialization-serialization-vs-database-input-output.md)。  
  
 应用程序向导支持该选项，但用户必须编写将文档序列化的代码。  在文档数据成员中存储序列化信息。  
  
##  <a name="_core_applications_with_no_document"></a> 无文档的应用程序  
 有时需要编写不使用文档或视图的应用程序。  无文档时，数据（例如 `CRecordset` 对象）存储在框架窗口类或应用程序类中。  其他附加要求取决于应用程序是否提供用户界面。  
  
###  <a name="_core_database_support_with_a_user_interface"></a> 有用户界面的数据库支持  
 如果您有一个用户界面（不包括某些界面，如控制台命令行界面），则应用程序直接在框架窗口的工作区内而不是视图内进行描述。  这种应用程序不使用 `CRecordView`、`CFormView` 或 `CDialog` 作为主用户界面，而通常使用 `CDialog` 作为普通对话框。  
  
###  <a name="_core_writing_applications_without_documents"></a> 编写无文档应用程序  
 因为应用程序向导不支持创建无文档应用程序，所以用户必须编写自己的 `CWinApp` 派生类，并且在需要时创建 `CFrameWnd` 或 `CMDIFrameWnd` 类。  重写 `CWinApp::InitInstance` 并且将应用程序对象声明为：  
  
```  
CYourNameApp theApp;  
```  
  
 框架还提供消息映射机制和许多其他功能。  
  
###  <a name="_core_database_support_separate_from_the_user_interface"></a> 独立于用户界面的数据库支持  
 有些应用程序要么不需要用户界面，要么只需要一个最小用户界面。  例如，假设编写：  
  
-   一个中间数据访问对象，其他应用程序（客户端）调用该对象在应用程序和数据源之间进行特殊的数据处理。  
  
-   一个没有用户干预的数据处理应用程序，例如一个把数据从一种数据库格式移到另一种数据库格式的应用程序，或者一个进行计算并执行批处理更新的应用程序。  
  
 因为任何文档都没有 `CRecordset` 或 `CDaoRecordset` 对象，所以可将其作为 `CWinApp` 派生应用程序类中一个嵌入的数据成员来存储。  其他方法包括：  
  
-   根本不保留一个永久 `CRecordset` 或 `CDaoRecordset` 对象。  用户可将 **NULL** 传递到记录集类构造函数。  那样，框架使用记录集的 `GetDefaultConnect` 成员函数中的信息创建一个临时 `CDatabase` 或 `CDaoDatabase` 对象。  此为最可能使用的替换方法。  
  
-   让 `CRecordset` 或 `CDaoRecordset` 对象成为全局变量。  该变量应是一个指向在 `CWinApp::InitInstance` 重写中动态创建的记录集对象的指针。  这样避免在初始化框架之前尝试构造对象。  
  
-   在文档或视图中随意使用记录集对象。  在应用程序或框架窗口对象的成员函数中创建记录集。  
  
## 请参阅  
 [MFC 数据库类（ODBC 和 DAO）](../data/mfc-database-classes-odbc-and-dao.md)