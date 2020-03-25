---
title: MFC：不结合文档和视图使用数据库类
ms.date: 11/04/2016
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
ms.openlocfilehash: 57a7abd89bc9bfb465912a35c21f9780668f4466
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213351"
---
# <a name="mfc-using-database-classes-without-documents-and-views"></a>MFC：不结合文档和视图使用数据库类

有时，您可能不想在数据库应用程序中使用框架的文档/视图体系结构。 本主题介绍：

- [不需要使用](#_core_when_you_don.92.t_need_documents)文档序列化等文档时。

- [应用程序向导选项](#_core_appwizard_options_for_documents_and_views)，用于支持不进行序列化的应用程序，并且不包含文档相关的 "**文件**" 菜单命令（如**新**的、**打开**、**保存**和**另存为**）。

- [如何处理使用最小文档的应用程序](#_core_applications_with_minimal_documents)。

- [如何在不使用文档或视图的情况如何构造应用程序](#_core_applications_with_no_document)。

##  <a name="when-you-do-not-need-documents"></a><a name="_core_when_you_don.92.t_need_documents"></a>不需要文档时

某些应用程序具有不同的文档概念。 这些应用程序通常使用**文件打开**命令将文件中的全部或大部分文件从存储加载到内存中。 它们使用**文件 "保存**" 或 "**另存为**" 命令将更新后的文件一次性写入存储。 用户看到的是数据文件。

但某些类别的应用程序并不需要文档。 数据库应用程序在事务中运行。 应用程序从数据库中选择记录，并将其呈现给用户，通常一次一个。 用户看到的内容通常是单个当前记录，这可能是内存中唯一的一条记录。

如果你的应用程序不需要文档来存储数据，则可以使用框架的部分或全部文档/视图体系结构。 你使用的方法取决于你首选的方法。 你可能：

- 使用最小文档作为存储与数据源的连接，但使用普通文档功能（如序列化）进行分配。 如果需要多个数据视图，并希望同步所有视图，并同时更新所有视图，这会很有用。

- 使用直接绘制的框架窗口，而不是使用视图。 在这种情况下，将忽略文档，并在框架窗口对象中存储任何数据或数据连接。

##  <a name="application-wizard-options-for-documents-and-views"></a><a name="_core_appwizard_options_for_documents_and_views"></a>文档和视图的应用程序向导选项

MFC 应用程序向导在 "**选择数据库支持**" 中有几个选项，如下表中所列。 如果使用 MFC 应用程序向导创建应用程序，则所有这些选项都将生成具有文档和视图的应用程序。 某些选项提供忽略不需要的文档功能的文档和视图。 有关详细信息，请参阅[MFC 应用程序向导的数据库支持](../mfc/reference/database-support-mfc-application-wizard.md)。

|选项|查看|Document|
|------------|----------|--------------|
|无|从 `CView`派生。|不提供数据库支持。 这是默认选项。<br /><br /> 如果您在 "[应用程序类型"-"MFC 应用程序向导](../mfc/reference/application-type-mfc-application-wizard.md)" 页上选择 "**文档/视图体系结构支持**" 选项，则可以在 "**文件**" 菜单上获取完整文档支持，包括序列化和**新**的、**打开**、**保存**和**另存为**命令。 请参阅[不包含文档的应用程序](#_core_applications_with_no_document)。|
|**仅头文件**|从 `CView`派生。|为应用程序提供基本的数据库支持级别。<br /><br /> 包括 Afxdb。 添加链接库，但不创建任何特定于数据库的类。 稍后可以创建记录集，并使用它们来检查和更新记录。|
|**不支持文件的数据库视图**|派生自 `CRecordView`|提供文档支持，但不支持序列化。 文档可以存储记录集并协调多个视图;不支持序列化或 "**打开**"、"**保存**"**和 "** **另存为**" 命令。 请参阅[文档最少的应用程序](#_core_applications_with_minimal_documents)。 如果包含数据库视图，则必须指定数据源。<br /><br /> 包括数据库头文件、链接库、记录视图和记录集。 （仅适用于在[应用程序类型 "MFC 应用程序向导](../mfc/reference/application-type-mfc-application-wizard.md)" 页上选择了 "**文档/视图体系结构支持**" 选项的应用程序。）|
|**具有文件支持的数据库视图**|派生自 `CRecordView`|提供完整文档支持，包括序列化和与文档相关的**文件**菜单命令。 数据库应用程序通常基于每个记录运行，而不是基于每个文件运行，因此不需要序列化。 不过，您可能有一个用于序列化的特殊用途。 请参阅[文档最少的应用程序](#_core_applications_with_minimal_documents)。 如果包含数据库视图，则必须指定数据源。<br /><br /> 包括数据库头文件、链接库、记录视图和记录集。 （仅适用于在[应用程序类型 "MFC 应用程序向导](../mfc/reference/application-type-mfc-application-wizard.md)" 页上选择了 "**文档/视图体系结构支持**" 选项的应用程序。）|

有关序列化的替代项和序列化替代用法的讨论，请参阅[序列化：序列化与数据库输入/输出](../mfc/serialization-serialization-vs-database-input-output.md)。

##  <a name="applications-with-minimal-documents"></a><a name="_core_applications_with_minimal_documents"></a>文档数量最少的应用程序

MFC 应用程序向导有两个选项可支持基于窗体的数据访问应用程序。 每个选项都创建一个 `CRecordView`派生的视图类和一个文档。 它们在文档中遗留的内容有所不同。

###  <a name="document-without-file-support"></a><a name="_core_a_document_without_file_support"></a>无文件支持的文档

如果不需要文档序列化，请选择 "应用程序向导数据库"**数据库视图（不支持文件**）。 文档提供以下有用目的：

- 这是存储 `CRecordset` 对象的便利位置。

   此使用情况类似于普通文档概念：文档存储数据（在本例中为一组记录），视图为文档视图。

- 如果您的应用程序提供多个视图（例如多个记录视图），则文档支持协调视图。

   如果多个视图显示相同的数据，则可以使用 `CDocument::UpdateAllViews` 成员函数在任何视图更改数据时协调所有视图的更新。

对于简单的基于窗体的应用程序，通常使用此选项。 应用程序向导自动支持此类应用程序的简单结构。

###  <a name="document-with-file-support"></a><a name="_core_a_document_with_file_support"></a>文档支持文件

当你对文档相关的 "**文件**" 菜单命令和文档序列化有备用用途时，请选择 "应用程序向导数据库" 选项**数据库视图和文件支持**。 对于您的程序的数据访问部分，您可以使用文档中所述的相同方式使用文档，[而无需提供文件支持](#_core_a_document_without_file_support)。 例如，可以使用文档的序列化功能来读取和写入存储用户首选项或其他有用信息的序列化用户配置文件文档。 有关更多建议，请参阅[序列化：序列化与数据库输入/输出](../mfc/serialization-serialization-vs-database-input-output.md)。

应用程序向导支持此选项，但您必须编写序列化文档的代码。 将序列化信息存储在文档数据成员中。

##  <a name="applications-with-no-document"></a><a name="_core_applications_with_no_document"></a>不包含文档的应用程序

有时可能需要编写不使用文档或视图的应用程序。 如果没有文档，请在框架窗口类或应用程序类中存储数据（如 `CRecordset` 对象）。 任何其他要求取决于应用程序是否提供用户界面。

###  <a name="database-support-with-a-user-interface"></a><a name="_core_database_support_with_a_user_interface"></a>具有用户界面的数据库支持

如果你有一个用户界面（例如，控制台命令行界面），则应用程序将直接绘制到框架窗口的工作区而不是视图中。 此类应用程序不会将 `CRecordView`、`CFormView`或 `CDialog` 用于其主用户界面，但它通常会将 `CDialog` 用于普通对话框。

###  <a name="writing-applications-without-documents"></a><a name="_core_writing_applications_without_documents"></a>不带文档编写应用程序

由于应用程序向导不支持创建没有文档的应用程序，因此必须编写自己的 `CWinApp`派生类，并在需要时创建 `CFrameWnd` 或 `CMDIFrameWnd` 类。 重写 `CWinApp::InitInstance` 并将应用程序对象声明为：

```cpp
CYourNameApp theApp;
```

该框架仍提供消息映射机制以及许多其他功能。

###  <a name="database-support-separate-from-the-user-interface"></a><a name="_core_database_support_separate_from_the_user_interface"></a>独立于用户界面的数据库支持

某些应用程序不需要任何用户界面，或者只需要最少的一个。 例如，假设您正在编写：

- 一个中间数据访问对象，其他应用程序（客户端）在应用程序与数据源之间对数据的特殊处理调用。

- 在无需用户干预的情况下处理数据的应用程序，例如将数据从一个数据库格式移到另一个数据库格式的应用程序，或者用于执行计算和执行批处理更新的应用程序。

因为没有任何文档拥有 `CRecordset` 对象，所以你可能希望将其作为嵌入数据成员存储在 `CWinApp`派生的应用程序类中。 替代方案包括：

- 根本不会保留永久的 `CRecordset` 对象。 可以将 NULL 传递给记录集类构造函数。 在这种情况下，框架使用记录集 `GetDefaultConnect` 成员函数中的信息创建一个临时 `CDatabase` 对象。 这是最可能的替代方法。

- 使 `CRecordset` 对象成为全局变量。 此变量应为指向在 `CWinApp::InitInstance` 重写中动态创建的记录集对象的指针。 这避免了在初始化框架之前尝试构造对象。

- 使用记录集对象，在文档或视图上下文中使用。 在应用程序或框架窗口对象的成员函数中创建记录集。

## <a name="see-also"></a>另请参阅

[MFC 数据库类](../data/mfc-database-classes-odbc-and-dao.md)
