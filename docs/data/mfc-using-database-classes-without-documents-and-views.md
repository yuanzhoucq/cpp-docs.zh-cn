---
title: "MFC： 使用数据库类不结合文档和视图 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC applications [C++], without views
- documents [C++], applications without
- ODBC applications [C++]
- document/view architecture [C++], in databases
- files [C++], MFC
- database classes [C++], MFC
- CRecordView class, using in database applications
- database applications [C++], without views
- database applications [C++], application wizard options
- application wizards [C++], creating database applications
- ODBC [C++], file support in database applications
- ODBC applications [C++], without documents
- database applications [C++], without documents
- user interface [C++], drawing information
ms.assetid: 15bf52d4-91cf-4b1d-8b37-87c3ae70123a
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 89c8c1d67a8273b542c088783e4b5121038c9fc2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC：不结合文档和视图使用数据库类
有时你不可能想要使用的框架的数据库应用程序中的文档/视图体系结构。 本主题说明：  
  
-   [不需要使用文档](#_core_when_you_don.92.t_need_documents)如文档序列化。  
  
-   [应用程序向导选项](#_core_appwizard_options_for_documents_and_views)来支持应用程序，序列化而无需与文档相关**文件**菜单命令如**新建**，**打开**，**保存**，和**将另存为**。  
  
-   [如何使用最少的文档的应用程序使用](#_core_applications_with_minimal_documents)。  
  
-   [如何构造不包含文档或视图的应用程序](#_core_applications_with_no_document)。  
  
##  <a name="_core_when_you_don.92.t_need_documents"></a>当你不需要的文档  
 某些应用程序具有不同的文档的概念。 这些应用程序通常从全部或加载文件中的大部分存储到内存中，**文件打开**命令。 它们写入更新的文件返回存储在一次与使用**文件保存**或**另存为**命令。 哪些用户将看到为数据文件。  
  
 但是，某些类别的应用程序，不需要的文档。 按照事务来运行数据库应用程序。 应用程序从数据库中选择记录，并将它们提供给用户，通常一次一个地。 哪些用户将看到通常是单个的当前记录，这可能是内存中的只能有一个。  
  
 如果你的应用程序不需要用于存储数据的文档，可完成部分或全部框架的文档/视图体系结构中进行分配。 摒弃的多少，取决于您喜欢的方法。 你可能会：  
  
-   使用最少文档作为的位置以存储到你的数据源的连接，但摒弃常规文档功能，如序列化。 当你想的数据的多个视图和想要同步所有视图中，在一次，依此类推对它们进行更新，这非常有用。  
  
-   使用在其中你描述直接，而不是使用视图的框架窗口。 在这种情况下，你中省略文档和框架窗口对象中存储任何数据或数据连接。  
  
##  <a name="_core_appwizard_options_for_documents_and_views"></a>文档和视图的应用程序向导选项  
 MFC 应用程序向导提供了若干选项**选择数据库支持**下, 表中列出的。 如果使用 MFC 应用程序向导创建应用程序，所有这些选项将产生结合文档和视图的应用程序。 某些选项提供文档和视图省略不需要的文档功能。 有关详细信息，请参阅[数据库支持，MFC 应用程序向导](../mfc/reference/database-support-mfc-application-wizard.md)。  
  
|选项|视图|Document|  
|------------|----------|--------------|  
|**无**|从 `CView` 派生。|未提供的数据库支持。 这是默认选项。<br /><br /> 如果你选择**文档/视图体系结构支持**选项[应用程序类型、 MFC 应用程序向导](../mfc/reference/application-type-mfc-application-wizard.md)页上，你获得完整的文档支持，包括序列化和`New`， **打开**，**保存**，和**另存为**上的命令**文件**菜单。 请参阅[没有文档的应用程序](#_core_applications_with_no_document)。|  
|**仅标头文件**|从 `CView` 派生。|你的应用程序提供基本级别的数据库支持。<br /><br /> 包括 Afxdb.h。 添加链接库，但不会创建任何数据库特定类。 你可以稍后创建记录集并使用它们来检查和更新记录。|  
|**不支持文件的数据库视图**|派生自`CRecordView`|提供文档支持，但不是序列化支持。 文档可以存储记录集和协调多个视图;不支持序列化或`New`，**打开**，**保存**，和**另存为**命令。 请参阅[带最小文档的应用程序](#_core_applications_with_minimal_documents)。 如果你包含的数据库视图，则必须指定数据源。<br /><br /> 包括数据库标头文件、 链接库、 记录视图和记录集。 (仅适用于应用程序与**文档/视图体系结构支持**上所选的选项[应用程序类型、 MFC 应用程序向导](../mfc/reference/application-type-mfc-application-wizard.md)页。)|  
|**文件支持的数据库视图**|派生自`CRecordView`|提供完整的文档支持，包括序列化以及与文档相关**文件**菜单命令。 数据库应用程序通常运行在每个记录基础上而不是对每个文件的基础，因此不需要序列化。 但是，您可能序列化的特殊的用途。 请参阅[带最小文档的应用程序](#_core_applications_with_minimal_documents)。 如果你包含的数据库视图，则必须指定数据源。<br /><br /> 包括数据库标头文件、 链接库、 记录视图和记录集。 (仅适用于应用程序与**文档/视图体系结构支持**上所选的选项[应用程序类型、 MFC 应用程序向导](../mfc/reference/application-type-mfc-application-wizard.md)页。)|  
  
 有关序列化和序列化的其他用途的替代项的讨论，请参阅[序列化： 序列化 vs。数据库输入/输出](../mfc/serialization-serialization-vs-database-input-output.md)。  
  
##  <a name="_core_applications_with_minimal_documents"></a>带最小文档的应用程序  
 MFC 应用程序向导的两个选项，支持基于窗体的数据访问应用程序。 每个选项创建`CRecordView`-派生视图类和一个文档。 它们的区别在于它们所排除的文档之外。  
  
###  <a name="_core_a_document_without_file_support"></a>不支持文件的文档  
 选择应用程序向导数据库选项**数据库不支持文件的视图**如果不需要文档序列化。 该文档具有下列用途：  
  
-   它是一个方便的位置来存储`CRecordset`对象。  
  
     这种用法类似普通文档概念： 将数据存储的文档 （或，在这种情况下，一组记录） 和视图是文档的视图。  
  
-   如果你的应用程序存在多个视图 （例如多个记录视图），则文档支持协调视图。  
  
     如果多个视图将显示相同的数据，则可以使用`CDocument::UpdateAllViews`成员函数时任何视图中更改数据协调到所有视图的更新。  
  
 通常情况下，为简单的基于窗体的应用程序需要使用此选项。 应用程序向导自动支持这种应用程序的方便的结构。  
  
###  <a name="_core_a_document_with_file_support"></a>支持文件的文档  
 选择应用程序向导数据库选项**数据库支持文件的视图**如果有其他用途与文档相关**文件**菜单命令和文档序列化。 对于你的程序的数据访问部分，你可以使用文档中的相同方式中所述[文档不带文件支持](#_core_a_document_without_file_support)。 可用于文档的序列化功能，例如，读取和写入存储用户的首选项或其他有用信息的序列化的用户配置文件文档。 有关更多概念，请参阅[序列化： 序列化 vs。数据库输入/输出](../mfc/serialization-serialization-vs-database-input-output.md)。  
  
 应用程序向导支持此选项，但你必须编写将文档序列化的代码。 在文档数据成员中存储的序列化的信息。  
  
##  <a name="_core_applications_with_no_document"></a>没有文档的应用程序  
 有时，你可能想要编写的应用程序不使用文档或视图。 无文档时，你将数据存储 (如`CRecordset`对象) 框架窗口类或你的应用程序类。 任何其他要求取决于应用程序是否提供用户界面。  
  
###  <a name="_core_database_support_with_a_user_interface"></a>使用用户界面的数据库支持  
 如果您有一个用户界面 （而非，例如，控制台命令行界面中），则应用程序直接在框架窗口的工作区而不是视图。 此类应用程序不使用`CRecordView`， `CFormView`，或`CDialog`主用户界面，但它通常使用`CDialog`普通的对话框。  
  
###  <a name="_core_writing_applications_without_documents"></a>编写应用程序没有文档  
 由于应用程序向导不支持无文档的创建应用程序，你必须编写你自己`CWinApp`-派生类，并且如果需要还创建`CFrameWnd`或`CMDIFrameWnd`类。 重写`CWinApp::InitInstance`和应用程序对象声明为：  
  
```  
CYourNameApp theApp;  
```  
  
 框架仍提供了消息映射机制和许多其他功能。  
  
###  <a name="_core_database_support_separate_from_the_user_interface"></a>数据库支持单独从用户界面  
 某些应用程序需要任何用户界面线程或仅需最小的密码。 例如，假设你正在编写：  
  
-   其他应用程序 （客户端） 调用的应用程序和数据源之间的数据的特殊处理的一个中间的数据访问对象。  
  
-   处理的应用程序无需用户干预，例如从一种数据库格式将数据转移到另一个或者是进行计算并执行批处理更新的应用程序的数据。  
  
 由于任何文档不拥有`CRecordset`对象，你可能想要将其存储中的嵌入的数据成员作为你`CWinApp`-派生应用程序类。 备选方法包括：  
  
-   不保留一个永久`CRecordset`根本对象。 你可以将传递**NULL**到记录集类构造函数。 在这种情况下，框架会创建一个临时`CDatabase`对象使用中的记录集的信息`GetDefaultConnect`成员函数。 这是最可能的另一种方法。  
  
-   使`CRecordset`对象全局变量。 此变量应指向创建动态在记录集对象的指针你`CWinApp::InitInstance`重写。 这样就避免了尝试初始化框架之前构造对象。  
  
-   使用记录集对象，就像在文档或视图的上下文中。 在成员中的应用程序或框架窗口对象的函数创建记录集。  
  
## <a name="see-also"></a>另请参阅  
 [MFC 数据库类](../data/mfc-database-classes-odbc-and-dao.md)